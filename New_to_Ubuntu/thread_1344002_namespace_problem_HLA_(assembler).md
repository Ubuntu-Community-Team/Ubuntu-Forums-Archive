---
title: "namespace problem HLA (assembler)"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by pratiks19 on 2009-12-02
Hi,

I tried compiling a hello world program using HLA.

The following error was produced:

    > $ hla -v hw
    Compiling 'hw.hla' to 'hw.o'
    using command line:
    [hlaparse -level=high  -v -sf -celf -test "hw.hla"]

    ----------------------
    HLA (High Level Assembler) Parser
    use '-license' to view license information
    Version Version 1.99 build 12922 (prototype)
    -t active
    File: hw.hla
    Output Path: ""
    Language Level: high

    [B]Compiling "hw.hla" to "hw.o"
    Error in file "/usr/hla/include/os.hhf" at line 5
    syntax error, unexpected namespaceTkn, expecting DoOneValStmt.
    Near: << namespace >>

    Compilation complete, 5 lines,   0.002 seconds,    2500 lines/second
    Using flat assembler version C1.66
    /usr/hla/include/os.hhf [4]:
    error: illegal instruction.[/B]

any suggestions? 

the os.hhf file:
> #if( ! @defined( os_hhf ))
?os_hhf := true;


namespace os;

	// Note: os.win32 and os.linux specify the operating system
	//		 in use.  This file must be manually edited as appropriate
	//		 for use under Windows or Linux so these constants contain
	//		 the appropriate values.
	
	const
		linux := @global:true;
		win32 := @global:false;
		freeBSD := @global:false;
		macOS := @global:false;

	procedure system( cmdLn:string ); @external( "OS_SYSTEM" );
	
	#macro exitProcess( rtnCode );
		
		mov( rtnCode, eax );
		xor( ebx, ebx );
		int( $80 );
		
	#endmacro	
		
end os;
	

#endif

any suggestions ?

---

