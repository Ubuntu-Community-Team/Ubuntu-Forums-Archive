---
title: "make expect 5.43 issue"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by aichan on 2009-07-20
i have installed Tcl 8.57 on my ubuntu 9.04.
when i'm tryng to make expect 5.43, it always give me this error..
(i use "./configure --with-tcl=/home/onepiece/tcl8.5.7/unix/" to make make file )


```
root@server:/home/onepiece/expect-5.43# make
gcc -c  -I. -I. -I/home/onepiece/tcl8.5.7/generic   -DEXP_VERSION=\"5.43.0\" -DSCRIPTDIR=\"/usr/local/lib/expect5.43\" -DEXECSCRIPTDIR=\"/usr/local/lib/expect5.43\" -DTCL_DEBUGGER -DUSE_NON_CONST -DSTTY_BIN=\"/bin/stty\"  -DDFLT_STTY="\"sane\""  exp_command.c
In file included from /home/onepiece/tcl8.5.7/generic/tclInt.h:3886,
                 from exp_command.c:62:
/home/onepiece/tcl8.5.7/generic/tclPort.h:27:28: error: tclUnixPort.h: No such file or directory
In file included from /home/onepiece/tcl8.5.7/generic/tclInt.h:3888,
                 from exp_command.c:62:
/home/onepiece/tcl8.5.7/generic/tclIntPlatDecls.h:98: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/home/onepiece/tcl8.5.7/generic/tclIntPlatDecls.h:113: warning: ‘struct in_addr’ declared inside parameter list
/home/onepiece/tcl8.5.7/generic/tclIntPlatDecls.h:113: warning: its scope is only this definition or declaration, which is probably not what you want
/home/onepiece/tcl8.5.7/generic/tclIntPlatDecls.h:394: error: expected specifier-qualifier-list before ‘Tcl_DirEntry’
In file included from exp_command.c:72:
exp_command.h:117: error: expected specifier-qualifier-list before ‘WAIT_STATUS_TYPE’
exp_command.c: In function ‘exp_wait_zero’:
exp_command.c:244: error: expected declaration specifiers before ‘WAIT_STATUS_TYPE’
exp_command.c:248: error: ‘WAIT_STATUS_TYPE’ undeclared (first use in this function)
exp_command.c:248: error: (Each undeclared identifier is reported only once
exp_command.c:248: error: for each function it appears in.)
exp_command.c: In function ‘exp_state_prep_for_invalidation’:
exp_command.c:263: error: ‘ExpState’ has no member named ‘fg_armed’
exp_command.c: In function ‘expBusy’:
exp_command.c:314: error: ‘ExpState’ has no member named ‘fdBusy’
exp_command.c: In function ‘exp_close’:
exp_command.c:345: error: ‘ExpState’ has no member named ‘leaveopen’
exp_command.c: In function ‘exp_init_spawn_ids’:
exp_command.c:462: error: ‘ExpState’ has no member named ‘keepForever’
exp_command.c:465: error: ‘ExpState’ has no member named ‘keepForever’
exp_command.c:469: error: ‘ExpState’ has no member named ‘keepForever’
exp_command.c: In function ‘Exp_SpawnCmd’:
exp_command.c:849: error: ‘ExpState’ has no member named ‘leaveopen’
exp_command.c:856: error: ‘ExpState’ has no member named ‘wait’
exp_command.c:1234: error: ‘ExpState’ has no member named ‘wait’
exp_command.c: At top level:
exp_command.c:2465: error: expected specifier-qualifier-list before ‘WAIT_STATUS_TYPE’
exp_command.c: In function ‘fork_clear_all’:
exp_command.c:2475: error: ‘struct forked_proc’ has no member named ‘next’
exp_command.c:2476: error: ‘struct forked_proc’ has no member named ‘link_status’
exp_command.c:2476: error: ‘not_in_use’ undeclared (first use in this function)
exp_command.c: In function ‘fork_init’:
exp_command.c:2486: error: ‘struct forked_proc’ has no member named ‘link_status’
exp_command.c:2486: error: ‘wait_not_done’ undeclared (first use in this function)
exp_command.c: In function ‘fork_add’:
exp_command.c:2496: error: ‘struct forked_proc’ has no member named ‘next’
exp_command.c:2497: error: ‘struct forked_proc’ has no member named ‘link_status’
exp_command.c:2497: error: ‘not_in_use’ undeclared (first use in this function)
exp_command.c:2503: error: ‘struct forked_proc’ has no member named ‘next’
exp_command.c: In function ‘Exp_WaitCmd’:
exp_command.c:2577: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2585: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2616: error: ‘struct forked_proc’ has no member named ‘next’
exp_command.c:2617: error: ‘struct forked_proc’ has no member named ‘link_status’
exp_command.c:2617: error: ‘not_in_use’ undeclared (first use in this function)
exp_command.c:2619: error: ‘struct forked_proc’ has no member named ‘wait_status’
exp_command.c:2651: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2651: error: ‘struct forked_proc’ has no member named ‘wait_status’
exp_command.c:2665: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2665: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2666: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2666: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2668: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2668: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2669: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2669: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2670: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2670: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2672: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2672: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2673: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2673: error: ‘struct ExpState’ has no member named ‘wait’
exp_command.c:2678: error: ‘struct forked_proc’ has no member named ‘link_status’
exp_command.c: In function ‘Exp_DisconnectCmd’:
exp_command.c:2775: error: ‘ExpState’ has no member named ‘valid’
exp_command.c:2790: error: ‘ExpState’ has no member named ‘valid’
make: *** [exp_command.o] Error 1
```

please help me fix this issue..

thanks :)

---

### Post by aichan on 2009-07-20
up up...

:)

---

### Post by aichan on 2009-07-20
problem solved..

i've installed previous version of Tcl (8.4), and the expect installed with no problem :)

---

