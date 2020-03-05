# Pro-C
This is for Demo connection between C/C++ and Oracle 

Links for Refrence :
http://infolab.stanford.edu/~ullman/fcdb/oracle/or-proc.html
https://docs.oracle.com/cd/A91202_01/901_doc/appdev.901/a89861/toc.htm
https://docs.oracle.com/cd/A57673_01/DOC/api/doc/PC_22/ch03a.htm
https://download.oracle.com/otn_hosted_doc/timesten/1122/quickstart/html/developer/proc/proc.html

Processing / Compiling Pro*C  program 
------------------------------------------
Pro*<C/C++> souce code with embabed SQLs  ===>>    Parsing OR precompiling via Pro*C precompiler or parser    ==> genrate  modfied source code in C/C++  with system lavel implementation of embdaed SQLs
*.pc (INPUT) ==> {pro*C compiler} ==> C/C++ code with embaded sql system level implementation (OUTPUT)

for Example :
     proc simpleCompileC.pc 
               * To check proc is installed or not :proc <ENTER>, it should return options that can be used along with proc 
     by default it will genrate <name>.pc ==> <name>.c file 
     Some options are :
     CODE          => it will indiacate output file type 
     CPP_SUFFIX     => it will ask to set extension of output file (ignore default cpp extention ) 
     proc CODE=cpp 
     
     examle :  proc CODE=cpp CPP_SUFFIX=XX simpleCompileC.pc 
     This will genrate cpp code 
     
     Compiling c++ code : as generated source code having low level implementation of sql and uses oracle headerfile so we need to provide oracle include file path for compiling and ssql lib for linking
     
     
     g++ simpleCompileC.cpp -I$ORACLE_HOME/precomp/public -l $ORACLE_HOME/lib -lclntsh -o a.out
     -I for include path , -l for compile time binding(early binding) 

Rules for Pro*C
---------------------------------------------
1) You can write sql execution block anywhere in c/c++ program, but it should be valid sql block i.e. its start from "EXEC" and end with ";" semicolon 
2) As proc source first parse then compile so all preprocessing and its components are not supported.
3) you can use c/c++ "GOTO" statement inside SQL block 


