---
title: "winbind crashes every sunday"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by warriorelric on 2008-10-14
Hi

I have a problem with a ubuntu 8.04 box and wondering if anyone can help.

Basically the box is configured with ubuntu server and has shorewall, webmin and winbind running on it. This also doubles up as router between different subnets in our environment and every sunday completly falls over. After disabling any weekly cron jobs this is still happening and the only thing I can find in the logs is with reference to samba and winbind:


Oct  5 07:53:55 router01 squid[10521]: logfileRotate: /var/log/squid/store.log
Oct  5 07:53:55 router01 squid[10521]: logfileRotate: /var/log/squid/access.log
Oct  5 07:53:55 router01 squid[10521]: helperStatefulOpenServers: Starting 10 'fakeauth_auth' processes
Oct  5 07:53:57 router01 kernel: [581299.761998] host 172.28.40.22/if2 ignores redirects for 172.28.32.31 to 160.100.10.63.
Oct  5 07:53:58 router01 winbindd[10166]: [2008/10/05 07:53:58, 0] lib/fault.c:fault_report(41)
Oct  5 07:53:58 router01 winbindd[10166]:   ===============================================================
Oct  5 07:53:58 router01 winbindd[10166]: [2008/10/05 07:53:58, 0] lib/fault.c:fault_report(42)
Oct  5 07:53:58 router01 winbindd[10166]:   INTERNAL ERROR: Signal 11 in pid 10166 (3.0.28a)
Oct  5 07:53:58 router01 winbindd[10166]:   Please read the Trouble-Shooting section of the Samba3-HOWTO
Oct  5 07:53:58 router01 winbindd[10166]: [2008/10/05 07:53:58, 0] lib/fault.c:fault_report(44)
Oct  5 07:53:58 router01 winbindd[10166]:
Oct  5 07:53:58 router01 winbindd[10166]:   From: [http://www.samba.org/samba/docs/Samba3-HOWTO.pdf](http://www.samba.org/samba/docs/Samba3-HOWTO.pdf)
Oct  5 07:53:58 router01 winbindd[10166]: [2008/10/05 07:53:58, 0] lib/fault.c:fault_report(45)
Oct  5 07:53:58 router01 winbindd[10166]:   ===============================================================
Oct  5 07:53:58 router01 winbindd[10166]: [2008/10/05 07:53:58, 0] lib/util.c:smb_panic(1633)
Oct  5 07:53:58 router01 winbindd[10166]:   PANIC (pid 10166): internal error
Oct  5 07:53:58 router01 winbindd[10166]: [2008/10/05 07:53:58, 0] lib/util.c:log_stack_trace(1737)
Oct  5 07:53:58 router01 winbindd[10166]:   BACKTRACE: 14 stack frames:
Oct  5 07:53:58 router01 winbindd[10166]:    #0 /usr/sbin/winbindd(log_stack_trace+0x2d) [0x8122fbd]
Oct  5 07:53:58 router01 winbindd[10166]:    #1 /usr/sbin/winbindd(smb_panic+0x5d) [0x81230ed]
Oct  5 07:53:58 router01 winbindd[10166]:    #2 /usr/sbin/winbindd [0x810d96a]
Oct  5 07:53:58 router01 winbindd[10166]:    #3 [0xb7f4d420]
Oct  5 07:53:58 router01 winbindd[10166]:    #4 /usr/sbin/winbindd [0x8118464]
Oct  5 07:53:58 router01 winbindd[10166]:    #5 /usr/sbin/winbindd(lp_do_parameter+0x44e) [0x81018de]
Oct  5 07:53:58 router01 winbindd[10166]:    #6 /usr/sbin/winbindd [0x8102ea5]
Oct  5 07:53:58 router01 winbindd[10166]:    #7 /usr/sbin/winbindd [0x810456a]
Oct  5 07:53:58 router01 winbindd[10166]:    #8 /usr/sbin/winbindd(pm_process+0x167) [0x81048b7]
Oct  5 07:53:58 router01 winbindd[10166]:    #9 /usr/sbin/winbindd(lp_load+0x158) [0x8101d58]
Oct  5 07:53:58 router01 winbindd[10166]:    #10 /usr/sbin/winbindd [0x808ac04]
Oct  5 07:53:58 router01 winbindd[10166]:    #11 /usr/sbin/winbindd(main+0xbaf) [0x808c60f]
Oct  5 07:53:58 router01 winbindd[10166]:    #12 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c6c450]
Oct  5 07:53:58 router01 winbindd[10166]:    #13 /usr/sbin/winbindd [0x808a6c1]
Oct  5 07:53:58 router01 winbindd[10166]: [2008/10/05 07:53:58, 0] lib/util.c:smb_panic(1638)
Oct  5 07:53:58 router01 winbindd[10166]:   smb_panic(): calling panic action [/usr/share/samba/panic-action 10166]
Oct  5 07:53:58 router01 winbindd[10166]: [2008/10/05 07:53:58, 0] lib/util.c:smb_panic(1646)
Oct  5 07:53:58 router01 winbindd[10166]:   smb_panic(): action returned status 0
Oct  5 07:53:58 router01 winbindd[10166]: [2008/10/05 07:53:58, 0] lib/fault.c:dump_core(181)
Oct  5 07:53:58 router01 winbindd[10166]:   dumping core in /var/log/samba/cores/winbindd


Any suggestions?

---

