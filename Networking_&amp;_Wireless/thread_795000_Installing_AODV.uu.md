---
title: "Installing AODV.uu"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by digitalspy99 on 2008-05-15
I'm trying to install AODV-Uu in Ubuntu Fiesty Fawn
I've already installed kernel-source-2.6.8 & kernel-headers-2.6-386 as directed in the link [http://my.opera.com/subjam/blog/show.dml/472834](http://my.opera.com/subjam/blog/show.dml/472834).
Is there a problem of conflict between my current kernel version and installed one ie 2.6.8
I dont know how to know my current version of kernel. I tried 'uname -r -s' which gives 'Linux 2.6.20-15-server'
But i'm still not sure what kernel it is.
Then I installed GCC and 'make' commands
But when i type 'make' after going into the aodv-uu-0.9.5 folder i get the following list of errors

gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o main.o main.c
main.c:22:19: error: stdio.h: No such file or directory
main.c:23:20: error: stdlib.h: No such file or directory
main.c:24:20: error: unistd.h: No such file or directory
main.c:25:19: error: errno.h: No such file or directory
main.c:26:23: error: sys/types.h: No such file or directory
main.c:27:24: error: sys/socket.h: No such file or directory
main.c:28:22: error: sys/stat.h: No such file or directory
In file included from /usr/include/linux/posix_types.h:47,
                 from /usr/include/linux/types.h:5,
                 from /usr/include/linux/if.h:22,
                 from main.c:30:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/asm/posix_types.h:13:22: error: features.h: No such file or directory
main.c:32:20: error: getopt.h: No such file or directory
main.c:33:19: error: ctype.h: No such file or directory
In file included from main.c:35:
defs.h:28:22: error: sys/time.h: No such file or directory
defs.h:32:24: error: sys/signal.h: No such file or directory
defs.h:33:24: error: netinet/in.h: No such file or directory
defs.h:34:23: error: arpa/inet.h: No such file or directory
defs.h:35:24: error: netinet/ip.h: No such file or directory
defs.h:36:23: error: sys/ioctl.h: No such file or directory
defs.h:39:20: error: syslog.h: No such file or directory
defs.h:41:20: error: string.h: No such file or directory
defs.h:42:19: error: fcntl.h: No such file or directory
In file included from defs.h:45,
                 from main.c:35:
timer_queue.h:40: error: field âtimeoutâ has incomplete type
timer_queue.h: In function âtimeval_diffâ:
timer_queue.h:53: error: dereferencing pointer to incomplete type
timer_queue.h:54: error: dereferencing pointer to incomplete type
timer_queue.h:54: error: dereferencing pointer to incomplete type
timer_queue.h:54: error: dereferencing pointer to incomplete type
timer_queue.h: In function âtimeval_add_msecâ:
timer_queue.h:66: error: dereferencing pointer to incomplete type
timer_queue.h:67: error: dereferencing pointer to incomplete type
timer_queue.h:68: error: dereferencing pointer to incomplete type
In file included from main.c:35:
defs.h: At top level:
defs.h:96: error: field âipaddrâ has incomplete type
defs.h:97: error: field ânetmaskâ has incomplete type
defs.h:98: error: field âbroadcastâ has incomplete type
defs.h:103: error: field âbcast_timeâ has incomplete type
defs.h:104: error: field âfwd_timeâ has incomplete type
defs.h: In function âname2indexâ:
defs.h:157: warning: implicit declaration of function âstrcmpâ
In file included from aodv_socket.h:30,
                 from main.c:39:
aodv_rerr.h:27:20: error: endian.h: No such file or directory
In file included from aodv_rerr.h:30,
                 from aodv_socket.h:30,
                 from main.c:39:
routing_table.h: At top level:
routing_table.h:35: error: field âneighborâ has incomplete type
routing_table.h:47: error: field âdest_addrâ has incomplete type
routing_table.h:50: error: field ânext_hopâ has incomplete type
routing_table.h:57: error: field âlast_hello_timeâ has incomplete type
aodv_rerr.h:44:2: error: #error "Adjust your <bits/endian.h> defines"
In file included from main.c:39:
aodv_socket.h:45: error: array type has incomplete element type
aodv_socket.h:45: error: array type has incomplete element type
In file included from aodv_hello.h:28,
                 from main.c:42:
aodv_rrep.h:52:2: error: #error "Adjust your <bits/endian.h> defines"
main.c:75: error: array type has incomplete element type
main.c:76: error: ârequired_argumentâ undeclared here (not in a function)
main.c:77: error: âno_argumentâ undeclared here (not in a function)
main.c: In function âusageâ:
main.c:100: warning: implicit declaration of function âfprintfâ
main.c:100: warning: incompatible implicit declaration of built-in function âfprintfâ
main.c:100: error: âstderrâ undeclared (first use in this function)
main.c:100: error: (Each undeclared identifier is reported only once
main.c:100: error: for each function it appears in.)
main.c:101: warning: implicit declaration of function âexitâ
main.c:101: warning: incompatible implicit declaration of built-in function âexitâ
main.c:105: warning: implicit declaration of function âprintfâ
main.c:105: warning: incompatible implicit declaration of built-in function âprintfâ
main.c:128: warning: incompatible implicit declaration of built-in function âexitâ
main.c: In function âset_kernel_optionsâ:
main.c:138: warning: implicit declaration of function âopenâ
main.c:138: error: âO_WRONLYâ undeclared (first use in this function)
main.c:140: warning: implicit declaration of function âwriteâ
main.c:142: warning: implicit declaration of function âcloseâ
main.c:162: warning: implicit declaration of function âmemsetâ
main.c:162: warning: incompatible implicit declaration of built-in function âmemsetâ
main.c:163: warning: implicit declaration of function âsprintfâ
main.c:163: warning: incompatible implicit declaration of built-in function âsprintfâ
main.c:179: warning: incompatible implicit declaration of built-in function âmemsetâ
main.c:180: warning: incompatible implicit declaration of built-in function âsprintfâ
main.c: In function âfind_default_gwâ:
main.c:201: error: âFILEâ undeclared (first use in this function)
main.c:201: error: ârouteâ undeclared (first use in this function)
main.c:204: warning: implicit declaration of function âfopenâ
main.c:207: warning: implicit declaration of function âperrorâ
main.c:208: warning: incompatible implicit declaration of built-in function âexitâ
main.c:211: warning: implicit declaration of function âfgetsâ
main.c:212: warning: implicit declaration of function âstrtokâ
main.c:212: warning: assignment makes pointer from integer without a cast
main.c:213: warning: assignment makes pointer from integer without a cast
main.c:216: warning: assignment makes pointer from integer without a cast
main.c:217: warning: assignment makes pointer from integer without a cast
main.c:219: warning: implicit declaration of function âfcloseâ
main.c: In function âget_if_infoâ:
main.c:239: warning: implicit declaration of function âsocketâ
main.c:239: error: âSOCK_DGRAMâ undeclared (first use in this function)
main.c:241: warning: implicit declaration of function âstrcpyâ
main.c:241: warning: incompatible implicit declaration of built-in function âstrcpyâ
main.c:242: warning: implicit declaration of function âioctlâ
main.c:243: error: âLOG_ERRâ undeclared (first use in this function)
main.c:243: error: âerrnoâ undeclared (first use in this function)
main.c:248: warning: type-punning to incomplete type might break strict-aliasing rules
main.c: In function âattach_callback_funcâ:
main.c:267: warning: incompatible implicit declaration of built-in function âfprintfâ
main.c:267: error: âstderrâ undeclared (first use in this function)
main.c:268: warning: incompatible implicit declaration of built-in function âexitâ
main.c: In function âload_modulesâ:
main.c:282: error: storage size of âstâ isnât known
main.c:285: error: âFILEâ undeclared (first use in this function)
main.c:285: error: âmâ undeclared (first use in this function)
main.c:287: warning: incompatible implicit declaration of built-in function âmemsetâ
main.c:289: warning: implicit declaration of function âstatâ
main.c:290: warning: incompatible implicit declaration of built-in function âsprintfâ
main.c:296: warning: implicit declaration of function âsystemâ
main.c:298: warning: implicit declaration of function âusleepâ
main.c:303: warning: assignment makes pointer from integer without a cast
main.c:307: warning: incompatible implicit declaration of built-in function âfprintfâ
main.c:307: error: âstderrâ undeclared (first use in this function)
main.c:309: warning: incompatible implicit declaration of built-in function âexitâ
main.c:315: warning: incompatible implicit declaration of built-in function âfprintfâ
main.c:318: warning: incompatible implicit declaration of built-in function âexitâ
main.c:282: warning: unused variable âstâ
main.c: In function âremove_modulesâ:
main.c:329: warning: incompatible implicit declaration of built-in function âfprintfâ
main.c:329: error: âstderrâ undeclared (first use in this function)
main.c: In function âhost_initâ:
main.c:342: warning: incompatible implicit declaration of built-in function âmemsetâ
main.c:347: error: âSOCK_DGRAMâ undeclared (first use in this function)
main.c:351: warning: incompatible implicit declaration of built-in function âfprintfâ
main.c:351: error: âstderrâ undeclared (first use in this function)
main.c:352: warning: incompatible implicit declaration of built-in function âexitâ
main.c:358: warning: incompatible implicit declaration of built-in function âstrcpyâ
main.c:365: warning: implicit declaration of function âstrlenâ
main.c:365: warning: incompatible implicit declaration of built-in function âstrlenâ
main.c:366: warning: incompatible implicit declaration of built-in function âfprintfâ
main.c:368: warning: incompatible implicit declaration of built-in function âexitâ
main.c:370: warning: incompatible implicit declaration of built-in function âstrcpyâ
main.c:372: error: âLOG_ERRâ undeclared (first use in this function)
main.c:372: error: âerrnoâ undeclared (first use in this function)
main.c:375: warning: incompatible implicit declaration of built-in function âexitâ
main.c:381: error: âLOG_NOTICEâ undeclared (first use in this function)
main.c:385: warning: incompatible implicit declaration of built-in function âstrcpyâ
main.c:394: warning: implicit declaration of function âgettimeofdayâ
main.c:399: warning: assignment makes pointer from integer without a cast
main.c:408: warning: incompatible implicit declaration of built-in function âexitâ
main.c:419: warning: incompatible implicit declaration of built-in function âexitâ
main.c:421: error: dereferencing pointer to incomplete type
main.c:428: error: dereferencing pointer to incomplete type
main.c:434: error: dereferencing pointer to incomplete type
main.c:441: warning: assignment makes pointer from integer without a cast
main.c:450: warning: incompatible implicit declaration of built-in function âfprintfâ
main.c:451: warning: incompatible implicit declaration of built-in function âexitâ
main.c: In function âsignal_handlerâ:
main.c:460: error: âSIGSEGVâ undeclared (first use in this function)
main.c:461: error: âLOG_ERRâ undeclared (first use in this function)
main.c:463: error: âSIGINTâ undeclared (first use in this function)
main.c:464: error: âSIGHUPâ undeclared (first use in this function)
main.c:465: error: âSIGTERMâ undeclared (first use in this function)
main.c:467: warning: incompatible implicit declaration of built-in function âexitâ
main.c: In function âmainâ:
main.c:480: warning: implicit declaration of function âstrrchrâ
main.c:480: warning: incompatible implicit declaration of built-in function âstrrchrâ
main.c:495: warning: implicit declaration of function âgetopt_longâ
main.c:497: error: âEOFâ undeclared (first use in this function)
main.c:515: error: âoptargâ undeclared (first use in this function)
main.c:524: warning: implicit declaration of function âisdigitâ
main.c:525: warning: implicit declaration of function âatoiâ
main.c:527: warning: incompatible implicit declaration of built-in function âfprintfâ
main.c:527: error: âstderrâ undeclared (first use in this function)
main.c:528: warning: incompatible implicit declaration of built-in function âexitâ
main.c:541: warning: implicit declaration of function âatofâ
main.c:563: warning: incompatible implicit declaration of built-in function âprintfâ
main.c:565: warning: incompatible implicit declaration of built-in function âexitâ
main.c:575: warning: implicit declaration of function âgeteuidâ
main.c:576: warning: incompatible implicit declaration of built-in function âfprintfâ
main.c:577: warning: incompatible implicit declaration of built-in function âexitâ
main.c:582: warning: implicit declaration of function âforkâ
main.c:583: warning: incompatible implicit declaration of built-in function âexitâ
main.c:588: warning: implicit declaration of function âsetsidâ
main.c:591: warning: implicit declaration of function âatexitâ
main.c:609: warning: implicit declaration of function âsignalâ
main.c:609: error: âSIGHUPâ undeclared (first use in this function)
main.c:610: error: âSIGINTâ undeclared (first use in this function)
main.c:611: error: âSIGTERMâ undeclared (first use in this function)
main.c:618: warning: implicit declaration of function âFD_ZEROâ
main.c:620: warning: implicit declaration of function âFD_SETâ
main.c:629: error: âLOG_NOTICEâ undeclared (first use in this function)
main.c:642: warning: implicit declaration of function âmemcpyâ
main.c:642: warning: incompatible implicit declaration of built-in function âmemcpyâ
main.c:646: warning: implicit declaration of function âselectâ
main.c:647: error: âerrnoâ undeclared (first use in this function)
main.c:647: error: âEINTRâ undeclared (first use in this function)
main.c:648: error: âLOG_WARNINGâ undeclared (first use in this function)
main.c:655: warning: implicit declaration of function âFD_ISSETâ
main.c: In function âcleanupâ:
main.c:668: error: âLOG_DEBUGâ undeclared (first use in this function)
make: *** [main.o] Error 


PLZZZ HELP ME OUT...........WAITING ANXIOUSLY

---

### Post by chili555 on 2008-05-15
When you run 'uname -r' it gives you the version number of your running kernel, in your case, 2.6.20-15. That's the problem we have here, the source and maybe the headers, do not match the running kernel. Also, I believe you need more tools than GCC to get the compile done. Please try:```
sudo apt-get install build-essential
sudo apt-get install linux-source
sudo apt-get install linux-headers-generic
```These generic package will pull in the source and headers needed by your running kernel. Then try 'make' again.

---

### Post by digitalspy99 on 2008-05-16
Hey chilli... thankxx a lot for helping me out... i did what you said... and it worked a little.... after doing what you said... i got following errors when i again typed make in the adov-uu folder... ther are not complete errors but some of them...

kaodv-mod.c:38:22: error: linux/in.h: No such file or directory
kaodv-mod.c:39:22: error: linux/ip.h: No such file or directory
kaodv-mod.c:40:23: error: linux/udp.h: No such file or directory
kaodv-mod.c:41:23: error: linux/tcp.h: No such file or directory
kaodv-mod.c:42:21: error: net/tcp.h: No such file or directory
kaodv-mod.c:43:23: error: net/route.h: No such file or directory
In file included from kaodv-mod.c:45:
kaodv-mod.h:6:24: error: linux/list.h: No such file or directory
kaodv-mod.h:7:28: error: linux/spinlock.h: No such file or directory
In file included from kaodv-mod.c:45:
kaodv-mod.h:11: error: field âlâ has incomplete type
kaodv-mod.h:12: error: field âif_addrâ has incomplete type
kaodv-mod.h:13: error: field âbc_addrâ has incomplete type
kaodv-mod.h:17: warning: type defaults to âintâ in declaration of âLIST_HEADâ
kaodv-mod.h:17: warning: parameter names (without types) in function declaration
kaodv-mod.h:18: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âifilockâ
kaodv-mod.h: In function âif_info_addâ:
kaodv-mod.h:27: warning: implicit declaration of function âkmallocâ
kaodv-mod.h:27: error: âGFP_ATOMICâ undeclared (first use in this function)
kaodv-mod.h:27: error: (Each undeclared identifier is reported only once
kaodv-mod.h:27: error: for each function it appears in.)
kaodv-mod.h:34: warning: implicit declaration of function âdev_holdâ
kaodv-mod.h:36: warning: implicit declaration of function âin_dev_getâ
kaodv-mod.h:36: warning: assignment makes pointer from integer without a cast
kaodv-mod.h:42: error: dereferencing pointer to incomplete type
kaodv-mod.h:42: error: âNULLâ undeclared (first use in this function)
kaodv-mod.h:43: error: dereferencing pointer to incomplete type
kaodv-mod.h:44: warning: implicit declaration of function âstrcmpâ
kaodv-mod.h:44: error: dereferencing pointer to incomplete type
kaodv-mod.h:44: error: dereferencing pointer to incomplete type
kaodv-mod.h:48: error: dereferencing pointer to incomplete type
kaodv-mod.h:49: error: dereferencing pointer to incomplete type
kaodv-mod.h:51: warning: implicit declaration of function âin_dev_putâ
kaodv-mod.h:54: warning: implicit declaration of function âwrite_lockâ
kaodv-mod.h:54: error: âifilockâ undeclared (first use in this function)
kaodv-mod.h:55: warning: implicit declaration of function âlist_addâ
kaodv-mod.h:55: error: âifiheadâ undeclared (first use in this function)
kaodv-mod.h:56: warning: implicit declaration of function âwrite_unlockâ
kaodv-mod.h: In function âif_info_purgeâ:
kaodv-mod.h:65: error: âifilockâ undeclared (first use in this function)
kaodv-mod.h:66: warning: implicit declaration of function âlist_for_each_safeâ
kaodv-mod.h:66: error: âifiheadâ undeclared (first use in this function)
kaodv-mod.h:66: error: expected â;â before â{â token
kaodv-mod.h: In function âif_info_from_ifindexâ:
kaodv-mod.h:81: warning: implicit declaration of function âread_lockâ
kaodv-mod.h:81: error: âifilockâ undeclared (first use in this function)
kaodv-mod.h:82: warning: implicit declaration of function âlist_for_eachâ
kaodv-mod.h:82: error: âifiheadâ undeclared (first use in this function)
kaodv-mod.h:82: error: expected â;â before â{â token
kaodv-mod.h: At top level:
kaodv-mod.h:100: warning: âstruct iphdrâ declared inside parameter list
kaodv-mod.h:100: warning: its scope is only this definition or declaration, which is probably not what you want
In file included from kaodv-mod.c:46:
kaodv-expl.h:30: error: field âlâ has incomplete type
kaodv-expl.h:33: error: expected specifier-qualifier-list before â__u32â
kaodv-expl.h:40: error: expected â)â before âdaddrâ
kaodv-expl.h:41: error: expected â)â before âdaddrâ
kaodv-expl.h:43: error: expected â)â before âdaddrâ
kaodv-expl.h:46: error: expected â)â before âdaddrâ
In file included from kaodv-mod.c:47:
kaodv-netlink.h:27:25: error: linux/types.h: No such file or directory
kaodv-netlink.h:28:27: error: linux/netlink.h: No such file or directory
kaodv-netlink.h:29:29: error: linux/rtnetlink.h: No such file or directory
In file included from kaodv-mod.c:47:
kaodv-netlink.h:102: error: expected specifier-qualifier-list before âu_int8_tâ
kaodv-netlink.h:133: error: expected declaration specifiers or â...â before â__u32â
kaodv-netlink.h:133: error: expected declaration specifiers or â...â before â__u32â
kaodv-netlink.h:134: error: expected declaration specifiers or â...â before â__u32â
kaodv-netlink.h:135: error: expected declaration specifiers or â...â before â__u32â
kaodv-netlink.h:136: error: expected declaration specifiers or â...â before â__u32â
kaodv-netlink.h:136: error: expected declaration specifiers or â...â before â__u32â
In file included from kaodv-mod.c:48:
kaodv-queue.h:28: error: expected â)â before âdaddrâ
kaodv-queue.h:30: warning: âstruct sk_buffâ declared inside parameter list
kaodv-queue.h:31: error: expected declaration specifiers or â...â before â__u32â
In file included from kaodv-mod.c:49:
kaodv-ipenc.h:29:27: error: asm/byteorder.h: No such file or directory
In file included from kaodv-mod.c:49:
kaodv-ipenc.h:34: error: expected specifier-qualifier-list before âu_int8_tâ
kaodv-ipenc.h:42:2: error: #error "Adjust your <asm/byteorder.h> defines"
kaodv-ipenc.h:48: error: expected declaration specifiers or â...â before â__u32â
In file included from kaodv-mod.c:50:
kaodv-debug.h:35: error: expected â)â before âaddrâ
kaodv-debug.h: In function âprint_ethâ:
kaodv-debug.h:57: warning: implicit declaration of function âsprintfâ
kaodv-debug.h:57: warning: incompatible implicit declaration of built-in function âsprintfâ
kaodv-mod.c: At top level:
kaodv-mod.c:65: error: expected declaration specifiers or â...â before string constant
kaodv-mod.c:65: warning: data definition has no type or storage class
kaodv-mod.c:65: warning: type defaults to âintâ in declaration of âMODULE_DESCRIPTIONâ
kaodv-mod.c:66: error: expected declaration specifiers or â...â before string constant
kaodv-mod.c:66: warning: data definition has no type or storage class
kaodv-mod.c:66: warning: type defaults to âintâ in declaration of âMODULE_AUTHORâ
kaodv-mod.c:75: warning: âstruct iphdrâ declared inside parameter list
kaodv-mod.c:76: error: conflicting types for âkaodv_update_route_timeoutsâ
kaodv-mod.h:100: error: previous declaration of âkaodv_update_route_timeoutsâ was here
kaodv-mod.c: In function âkaodv_update_route_timeoutsâ:
kaodv-mod.c:78: error: storage size of âbcaddrâ isnât known
kaodv-mod.c:84: error: âNULLâ undeclared (first use in this function)
kaodv-mod.c:84: error: dereferencing pointer to incomplete type
kaodv-mod.c:89: error: âNF_IP_PRE_ROUTINGâ undeclared (first use in this function)
kaodv-mod.c:90: error: dereferencing pointer to incomplete type
kaodv-mod.c:91: error: dereferencing pointer to incomplete type
kaodv-mod.c:91: error: dereferencing pointer to incomplete type
kaodv-mod.c:91: error: too many arguments to function âkaodv_netlink_send_rt_update_msgâ
kaodv-mod.c:92: error: dereferencing pointer to incomplete type
kaodv-mod.c:92: error: âINADDR_BROADCASTâ undeclared (first use in this function)
kaodv-mod.c:92: error: dereferencing pointer to incomplete type
kaodv-mod.c:93: error: dereferencing pointer to incomplete type
kaodv-mod.c:94: error: dereferencing pointer to incomplete type
kaodv-mod.c:94: error: dereferencing pointer to incomplete type
kaodv-mod.c:94: error: too many arguments to function âkaodv_netlink_send_rt_update_msgâ
kaodv-mod.c:97: warning: implicit declaration of function âkaodv_expl_getâ
kaodv-mod.c:97: error: dereferencing pointer to incomplete type
kaodv-mod.c:99: warning: implicit declaration of function âkaodv_expl_updateâ
kaodv-mod.c:99: error: âstruct expl_entryâ has no member named âdaddrâ
kaodv-mod.c:99: error: âstruct expl_entryâ has no member named ânhopâ
kaodv-mod.c:100: error: dereferencing pointer to incomplete type
kaodv-mod.c:102: error: âstruct expl_entryâ has no member named ânhopâ
kaodv-mod.c:102: error: âstruct expl_entryâ has no member named âdaddrâ
kaodv-mod.c:102: error: âstruct expl_entryâ has no member named ânhopâ
kaodv-mod.c:103: error: âstruct expl_entryâ has no member named âdaddrâ
kaodv-mod.c:103: error: âstruct expl_entryâ has no member named ânhopâ
kaodv-mod.c:104: error: dereferencing pointer to incomplete type
kaodv-mod.c:107: error: dereferencing pointer to incomplete type
kaodv-mod.c:109: error: âstruct expl_entryâ has no member named âdaddrâ
kaodv-mod.c:109: error: âstruct expl_entryâ has no member named ânhopâ
kaodv-mod.c:110: error: dereferencing pointer to incomplete type
kaodv-mod.c:112: error: âstruct expl_entryâ has no member named ânhopâ
kaodv-mod.c:112: error: âstruct expl_entryâ has no member named âdaddrâ
kaodv-mod.c:112: error: âstruct expl_entryâ has no member named ânhopâ
kaodv-mod.c:113: error: âstruct expl_entryâ has no member named âdaddrâ
kaodv-mod.c:113: error: âstruct expl_entryâ has no member named ânhopâ
kaodv-mod.c:114: error: dereferencing pointer to incomplete type
kaodv-mod.c:78: warning: unused variable âbcaddrâ
kaodv-mod.c:124:41: error: missing binary operator before token "("
kaodv-mod.c: In function âkaodv_hookâ:
kaodv-mod.c:127: error: dereferencing pointer to incomplete type
kaodv-mod.c:130: error: storage size of âifaddrâ isnât known
kaodv-mod.c:130: error: storage size of âbcaddrâ isnât known
kaodv-mod.c:133: warning: implicit declaration of function âmemsetâ
kaodv-mod.c:133: warning: incompatible implicit declaration of built-in function âmemsetâ
kaodv-mod.c:133: error: invalid application of âsizeofâ to incomplete type âstruct in_addrâ
kaodv-mod.c:134: error: invalid application of âsizeofâ to incomplete type âstruct in_addrâ
kaodv-mod.c:137: error: âNULLâ undeclared (first use in this function)
kaodv-mod.c:138: error: âNF_ACCEPTâ undeclared (first use in this function)
kaodv-mod.c:142: error: dereferencing pointer to incomplete type
kaodv-mod.c:142: error: âIPPROTO_UDPâ undeclared (first use in this function)
kaodv-mod.c:145: error: dereferencing pointer to incomplete type
kaodv-mod.c:147: warning: implicit declaration of function ântohsâ
kaodv-mod.c:147: error: dereferencing pointer to incomplete type
kaodv-mod.c:148: error: dereferencing pointer to incomplete type
kaodv-mod.c:164: error: âNF_IP_PRE_ROUTINGâ undeclared (first use in this function)
kaodv-mod.c:165: warning: passing argument 3 of âkaodv_update_route_timeoutsâ from incompatible pointer type
kaodv-mod.c:172: error: dereferencing pointer to incomplete type
kaodv-mod.c:174: error: dereferencing pointer to incomplete type
kaodv-mod.c:181: error: dereferencing pointer to incomplete type
kaodv-mod.c:181: error: âINADDR_BROADCASTâ undeclared (first use in this function)
kaodv-mod.c:182: warning: implicit declaration of function âIN_MULTICASTâ
kaodv-mod.c:182: warning: implicit declaration of function ântohlâ
kaodv-mod.c:182: error: dereferencing pointer to incomplete type
kaodv-mod.c:183: error: dereferencing pointer to incomplete type
kaodv-mod.c:190: warning: passing argument 3 of âkaodv_update_route_timeoutsâ from incompatible pointer type
kaodv-mod.c:193: error: dereferencing pointer to incomplete type
kaodv-mod.c:194: error: dereferencing pointer to incomplete type
kaodv-mod.c:196:41: error: missing binary operator before token "("
kaodv-mod.c:199: error: dereferencing pointer to incomplete type
kaodv-mod.c:205: error: dereferencing pointer to incomplete type
kaodv-mod.c:206: error: dereferencing pointer to incomplete type
kaodv-mod.c:210: error: dereferencing pointer to incomplete type
kaodv-mod.c:211: error: dereferencing pointer to incomplete type
kaodv-mod.c:212: error: dereferencing pointer to incomplete type
kaodv-mod.c:212: error: dereferencing pointer to incomplete type
kaodv-mod.c:212: error: too many arguments to function âkaodv_netlink_send_rerr_msgâ
kaodv-mod.c:213: error: âNF_DROPâ undeclared (first use in this function)
kaodv-mod.c:219: error: dereferencing pointer to incomplete type
kaodv-mod.c:220: error: dereferencing pointer to incomplete type
kaodv-mod.c:220: error: too many arguments to function âkaodv_netlink_send_rt_msgâ
kaodv-mod.c:222: warning: passing argument 1 of âkaodv_queue_enqueue_packetâ from incompatible pointer type
kaodv-mod.c:222: warning: passing argument 2 of âkaodv_queue_enqueue_packetâ from incompatible pointer type
kaodv-mod.c:224: error: âNF_STOLENâ undeclared (first use in this function)
kaodv-mod.c:227: error: âNF_IP_LOCAL_OUTâ undeclared (first use in this function)
kaodv-mod.c:229: error: dereferencing pointer to incomplete type
kaodv-mod.c:232: warning: implicit declaration of function âkaodv_queue_findâ
kaodv-mod.c:232: error: dereferencing pointer to incomplete type
kaodv-mod.c:235: error: dereferencing pointer to incomplete type
kaodv-mod.c:235: error: too many arguments to function âkaodv_netlink_send_rt_msgâ
kaodv-mod.c:237: warning: passing argument 1 of âkaodv_queue_enqueue_packetâ from incompatible pointer type
kaodv-mod.c:237: warning: passing argument 2 of âkaodv_queue_enqueue_packetâ from incompatible pointer type
kaodv-mod.c:263: warning: passing argument 3 of âkaodv_update_route_timeoutsâ from incompatible pointer type
kaodv-mod.c:265: error: âstruct expl_entryâ has no member named ânhopâ
kaodv-mod.c:265: error: too many arguments to function âip_pkt_encapsulateâ
kaodv-mod.c:270:41: error: missing binary operator before token "("
kaodv-mod.c:273: warning: implicit declaration of function âip_route_me_harderâ
kaodv-mod.c:273: error: âRTN_LOCALâ undeclared (first use in this function)
kaodv-mod.c:277: error: âNF_IP_POST_ROUTINGâ undeclared (first use in this function)
kaodv-mod.c:278: warning: passing argument 3 of âkaodv_update_route_timeoutsâ from incompatible pointer type
kaodv-mod.c:130: warning: unused variable âbcaddrâ
kaodv-mod.c:130: warning: unused variable âifaddrâ
kaodv-mod.c: At top level:
kaodv-mod.c:283: error: expected declaration specifiers or â...â before âoff_tâ
kaodv-mod.c: In function âkaodv_proc_infoâ:
kaodv-mod.c:288: warning: incompatible implicit declaration of built-in function âsprintfâ
kaodv-mod.c:292: error: âoffsetâ undeclared (first use in this function)
kaodv-mod.c: At top level:
kaodv-mod.c:315: error: expected â)â before string constant
kaodv-mod.c:316: error: expected â)â before string constant
kaodv-mod.c:319: error: array type has incomplete element type
kaodv-mod.c:321: error: field name not in record or union initializer
kaodv-mod.c:321: error: (near initialization for âkaodv_opsâ)
kaodv-mod.c:325: error: field name not in record or union initializer
kaodv-mod.c:325: error: (near initialization for âkaodv_opsâ)
kaodv-mod.c:325: error: âPF_INETâ undeclared here (not in a function)
kaodv-mod.c:326: error: field name not in record or union initializer
kaodv-mod.c:326: error: (near initialization for âkaodv_opsâ)
kaodv-mod.c:326: error: âNF_IP_PRE_ROUTINGâ undeclared here (not in a function)
kaodv-mod.c:327: error: field name not in record or union initializer
kaodv-mod.c:327: error: (near initialization for âkaodv_opsâ)
kaodv-mod.c:327: error: âNF_IP_PRI_FIRSTâ undeclared here (not in a function)
kaodv-mod.c:330: error: field name not in record or union initializer
kaodv-mod.c:330: error: (near initialization for âkaodv_opsâ)
kaodv-mod.c:334: error: field name not in record or union initializer
kaodv-mod.c:334: error: (near initialization for âkaodv_opsâ)
kaodv-mod.c:335: error: field name not in record or union initializer
kaodv-mod.c:335: error: (near initialization for âkaodv_opsâ)
kaodv-mod.c:335: error: âNF_IP_LOCAL_OUTâ undeclared here (not in a function)
kaodv-mod.c:336: error: field name not in record or union initializer
kaodv-mod.c:336: error: (near initialization for âkaodv_opsâ)
kaodv-mod.c:336: error: âNF_IP_PRI_FILTERâ undeclared here (not in a function)
kaodv-mod.c:339: error: field name not in record or union initializer
kaodv-mod.c:339: error: (near initialization for âkaodv_opsâ)
kaodv-mod.c:343: error: field name not in record or union initializer
kaodv-mod.c:343: error: (near initialization for âkaodv_opsâ)
kaodv-mod.c:344: error: field name not in record or union initializer
kaodv-mod.c:344: error: (near initialization for âkaodv_opsâ)
kaodv-mod.c:344: error: âNF_IP_POST_ROUTINGâ undeclared here (not in a function)
kaodv-mod.c:345: error: field name not in record or union initializer
kaodv-mod.c:345: error: (near initialization for âkaodv_opsâ)
kaodv-mod.c:349: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âkaodv_initâ
kaodv-mod.c:423: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âkaodv_exitâ
kaodv-mod.c:439: warning: data definition has no type or storage class
kaodv-mod.c:439: warning: type defaults to âintâ in declaration of âmodule_initâ
kaodv-mod.c:439: warning: parameter names (without types) in function declaration
kaodv-mod.c:440: warning: data definition has no type or storage class
kaodv-mod.c:440: warning: type defaults to âintâ in declaration of âmodule_exitâ
kaodv-mod.c:440: warning: parameter names (without types) in function declaration
make[1]: *** [kaodv-mod.o] Error 1
make[1]: Leaving directory `/root/test/aodv-uu-0.9.5/lnx'
make: *** [kaodv] Error 2

now you must have noted that the errors that were coming earlier were all concerned with main.c file but now they are all in k-aodv-mod.c file.... i hopw and wish that you can help me more... i ll be really thankfull to you....

---

### Post by chili555 on 2008-05-16
I got it to compile on kernel version 2.6.20-16-generic with warnings, but no errors with:```
 make KCC=gcc33
```This is suggested in the README for users of Fedora Core 1!!! That suggests just how old this thing is.

I checked in Synaptic and the oldest version of gcc I can find to install, which I already had, was gcc-3.3. I suppose the differences in 3.2 versus 3.3 throw up the warnings. I also believe if you update your kernel, you will not be able to get this old-timer to compile. If 2.6.20 works well for you and you need AODV.UU, do *not* install a new kernel.

---

### Post by digitalspy99 on 2008-05-19
I'm still having a problem...Would u do me a favor by telling what exactly were your kernel and gcc versions.What was your environment? what version of AODV-uu were u using? I'm currently using Ubuntu 7.04 feisty fawn. If needed, I'm ready to change the version of the operating system....My netfilter is not getting enabled, which i think, is because of the version conflicts. I'm using
OS = Ubuntu 7.04 Feisty Fawn
kernel = 2.6.20-16
gcc = 4.12 (but I've changed it to 3.3)
AODV-uu = 0.9.5 (but i do have other versions as well)

---

### Post by chili555 on 2008-05-19
I am running Hardy, but I have booted to kernel version 2.6.20-16-generic. My gcc version is 4.2.3, however, like you, I have 3.3, also. The AODV version I downloaded seems to be 0.9.6. I just did a 'make clean' followed by 'make KCC=gcc33' and, again, I got a few warnings, but no errors.

Please understand; I do not use AODV.uu or even know what it is or does. I just responded because you asked for help in compiling and I can sometimes help figure out how to compile. If you are getting compile errors, I will be glad to help. Beyond that, I am out of talent.

---

