---
title: "Ubuntu 14.04 is causing random PIA-VPN crashes (crash message here)"
date: 2017-05-02
forum: Networking &amp; Wireless
---

### Post by Wadcutter on 2017-05-02
My PIA VPN continually loses connection with servers at random times ranging from 10 minutes to an hour. Occasionally it is accompanied by an error message, but that is only about 1 out of 15 crashes. The other times, it just loses connection with the VPN server and the internet goes dead. It can happen if my browser (I’ve tried Firefox, Chrome, Brave and Midori) is idle and it can happen if I am in the middle of doing something with it or playing music. If I then shut down the VPN connection, my regular ISP is running. This is affecting one desktop computer running Ubuntu 14.04. I have other computers on the same ISP/VPN that do not lose their VPN connection. So it is definitely an Ubuntu 14.04 issue, not a PIA or ISP problem, although they may be interrelated.
 

I’ve tried switching router connections (a wired router), router cables,different gateway ports, and changing from UDP to TCP but nothing has fixed it. Also  I un-installed openvpn and re-installed to no avail. This has been broken for over a month. Prior to then, it had worked almost perfectly for 2.5 years. PIA had no answers but they don’t really know my system. Everything I’ve searched online and in this forum relates to users being unable to establish a connection; no one seems to have this problem of being able to establish a perfectly good server connection and then having it suddenly go dead 20 or 30 minutes down the road. I’ve sent at least 20 automatic error problem reports to Ubuntu—they are probably tired of getting them and wonder, “why doesn’t this guy fix this?” I would if I knew how.

It's a homemade AMD64 desktop about 8 years old with 4 GB of memory. I'm not using wi-fi.


I found an error message at var/crash/_usra-sbin_openvpn.0.crash but it’s too advanced for me to interpret. It is also very, very long.Here’s the first part if that has any hints in it:


```
ProblemType:Crash
Architecture:amd64
CrashCounter:1
Date:Mon May  1 12:34:34 2017
DistroRelease:Ubuntu 14.04
ExecutablePath:/usr/sbin/openvpn
ExecutableTimestamp:1417473095
ProcCmdline:/usr/sbin/openvpn --remote us-california.privateinternetaccess.com--comp-lzo --nobind --dev tun --proto udp --port 1197 --cipherAES-256-CBC --auth SHA256 --auth-nocache --syslog nm-openvpn--script-security 2 --up/usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper--up-restart --persist-key --persist-tun --management 127.0.0.1 1194--management-query-passwords --route-noexec --ifconfig-noexec--client --auth-user-pass --ca /etc/openvpn/pia-ca.rsa.4096.crt
ProcCwd:/
ProcEnviron:
TERM=linux
PATH=(custom, no user)
LANG=en_US.UTF-8
ProcMaps:
559c047c9000-559c04868000 r-xp 00000000 08:05 296648                    /usr/sbin/openvpn
559c04a67000-559c04a69000 r--p 0009e000 08:05 296648                    /usr/sbin/openvpn
559c04a69000-559c04a6a000 rw-p 000a0000 08:05 296648                    /usr/sbin/openvpn
559c04a6a000-559c04a70000 rw-p 00000000 00:00 0 
559c051c4000-559c05295000 rw-p 00000000 00:00 0                         [heap]
7f5d4634a000-7f5d46361000 r-xp 00000000 08:05 291                       /lib/x86_64-linux-gnu/libresolv-2.19.so
7f5d46361000-7f5d46561000 ---p 00017000 08:05 291                       /lib/x86_64-linux-gnu/libresolv-2.19.so
7f5d46561000-7f5d46562000 r--p 00017000 08:05 291                       /lib/x86_64-linux-gnu/libresolv-2.19.so
7f5d46562000-7f5d46563000 rw-p 00018000 08:05 291                       /lib/x86_64-linux-gnu/libresolv-2.19.so
7f5d46563000-7f5d46565000 rw-p 00000000 00:00 0 
7f5d46565000-7f5d4656a000 r-xp 00000000 08:05 7162                      /lib/x86_64-linux-gnu/libnss_dns-2.19.so
7f5d4656a000-7f5d46769000 ---p 00005000 08:05 7162                      /lib/x86_64-linux-gnu/libnss_dns-2.19.so
7f5d46769000-7f5d4676a000 r--p 00004000 08:05 7162                      /lib/x86_64-linux-gnu/libnss_dns-2.19.so
7f5d4676a000-7f5d4676b000 rw-p 00005000 08:05 7162                      /lib/x86_64-linux-gnu/libnss_dns-2.19.so
7f5d4676b000-7f5d4676d000 r-xp 00000000 08:05 10803                     /lib/x86_64-linux-gnu/libnss_mdns4_minimal.so.2
7f5d4676d000-7f5d4696c000 ---p 00002000 08:05 10803                     /lib/x86_64-linux-gnu/libnss_mdns4_minimal.so.2
7f5d4696c000-7f5d4696d000 r--p 00001000 08:05 10803                     /lib/x86_64-linux-gnu/libnss_mdns4_minimal.so.2
7f5d4696d000-7f5d4696e000 rw-p 00002000 08:05 10803                     /lib/x86_64-linux-gnu/libnss_mdns4_minimal.so.2
7f5d4696e000-7f5d46978000 r-xp 00000000 08:05 7169                      /lib/x86_64-linux-gnu/libnss_files-2.19.so
7f5d46978000-7f5d46b77000 ---p 0000a000 08:05 7169                      /lib/x86_64-linux-gnu/libnss_files-2.19.so
7f5d46b77000-7f5d46b78000 r--p 00009000 08:05 7169                      /lib/x86_64-linux-gnu/libnss_files-2.19.so
7f5d46b78000-7f5d46b79000 rw-p 0000a000 08:05 7169                      /lib/x86_64-linux-gnu/libnss_files-2.19.so
7f5d46b79000-7f5d46d37000 r-xp 00000000 08:05 7160                      /lib/x86_64-linux-gnu/libc-2.19.so
7f5d46d37000-7f5d46f36000 ---p 001be000 08:05 7160                      /lib/x86_64-linux-gnu/libc-2.19.so
7f5d46f36000-7f5d46f3a000 r--p 001bd000 08:05 7160                      /lib/x86_64-linux-gnu/libc-2.19.so
7f5d46f3a000-7f5d46f3c000 rw-p 001c1000 08:05 7160                      /lib/x86_64-linux-gnu/libc-2.19.so
7f5d46f3c000-7f5d46f41000 rw-p 00000000 00:00 0 
7f5d46f41000-7f5d46f44000 r-xp 00000000 08:05 7170                      /lib/x86_64-linux-gnu/libdl-2.19.so
7f5d46f44000-7f5d47143000 ---p 00003000 08:05 7170                      /lib/x86_64-linux-gnu/libdl-2.19.so
7f5d47143000-7f5d47144000 r--p 00002000 08:05 7170                      /lib/x86_64-linux-gnu/libdl-2.19.so
7f5d47144000-7f5d47145000 rw-p 00003000 08:05 7170                      /lib/x86_64-linux-gnu/libdl-2.19.so
7f5d47145000-7f5d472f8000 r-xp 00000000 08:05 1273                      /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7f5d472f8000-7f5d474f7000 ---p 001b3000 08:05 1273                      /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7f5d474f7000-7f5d47512000 r--p 001b2000 08:05 1273                      /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7f5d47512000-7f5d4751d000 rw-p 001cd000 08:05 1273                      /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7f5d4751d000-7f5d47521000 rw-p 00000000 00:00 0 
7f5d47521000-7f5d47576000 r-xp 00000000 08:05 8087                      /lib/x86_64-linux-gnu/libssl.so.1.0.0
7f5d47576000-7f5d47776000 ---p 00055000 08:05 8087                      /lib/x86_64-linux-gnu/libssl.so.1.0.0
7f5d47776000-7f5d47779000 r--p 00055000 08:05 8087                      /lib/x86_64-linux-gnu/libssl.so.1.0.0
7f5d47779000-7f5d47780000 rw-p 00058000 08:05 8087                      /lib/x86_64-linux-gnu/libssl.so.1.0.0
7f5d47780000-7f5d47799000 r-xp 00000000 08:05 296646                    /usr/lib/x86_64-linux-gnu/libpkcs11-helper.so.1.0.0
7f5d47799000-7f5d47998000 ---p 00019000 08:05 296646                    /usr/lib/x86_64-linux-gnu/libpkcs11-helper.so.1.0.0
7f5d47998000-7f5d47999000 r--p 00018000 08:05 296646                    /usr/lib/x86_64-linux-gnu/libpkcs11-helper.so.1.0.0
7f5d47999000-7f5d4799a000 rw-p 00019000 08:05 296646                    /usr/lib/x86_64-linux-gnu/libpkcs11-helper.so.1.0.0
7f5d4799a000-7f5d479b3000 r-xp 00000000 08:05 7171                      /lib/x86_64-linux-gnu/libpthread-2.19.so
7f5d479b3000-7f5d47bb2000 ---p 00019000 08:05 7171                      /lib/x86_64-linux-gnu/libpthread-2.19.so
7f5d47bb2000-7f5d47bb3000 r--p 00018000 08:05 7171                      /lib/x86_64-linux-gnu/libpthread-2.19.so
7f5d47bb3000-7f5d47bb4000 rw-p 00019000 08:05 7171                      /lib/x86_64-linux-gnu/libpthread-2.19.so
7f5d47bb4000-7f5d47bb8000 rw-p 00000000 00:00 0 
7f5d47bb8000-7f5d47bd8000 r-xp 00000000 08:05 10771                     /lib/x86_64-linux-gnu/liblzo2.so.2.0.0
7f5d47bd8000-7f5d47dd7000 ---p 00020000 08:05 10771                     /lib/x86_64-linux-gnu/liblzo2.so.2.0.0
7f5d47dd7000-7f5d47dd8000 r--p 0001f000 08:05 10771                     /lib/x86_64-linux-gnu/liblzo2.so.2.0.0
7f5d47dd8000-7f5d47dd9000 rw-p 00020000 08:05 10771                     /lib/x86_64-linux-gnu/liblzo2.so.2.0.0
7f5d47dd9000-7f5d47dfc000 r-xp 00000000 08:05 7168                      /lib/x86_64-linux-gnu/ld-2.19.so
7f5d47fd1000-7f5d47fd6000 rw-p 00000000 00:00 0 
7f5d47ff9000-7f5d47ffb000 rw-p 00000000 00:00 0 
7f5d47ffb000-7f5d47ffc000 r--p 00022000 08:05 7168                      /lib/x86_64-linux-gnu/ld-2.19.so
7f5d47ffc000-7f5d47ffd000 rw-p 00023000 08:05 7168                      /lib/x86_64-linux-gnu/ld-2.19.so
7f5d47ffd000-7f5d47ffe000 rw-p 00000000 00:00 0 
7ffc8802c000-7ffc8804d000 rw-p 00000000 00:00 0                         [stack]
7ffc88167000-7ffc88169000 r--p 00000000 00:00 0                         [vvar]
7ffc88169000-7ffc8816b000 r-xp 00000000 00:00 0                         [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                 [vsyscall]
ProcStatus:
Name:    openvpn
State:    S (sleeping)
Tgid:    2706
Ngid:    0
Pid:    2706
PPid:    2686
TracerPid:    0
Uid:    0    0    0    0
Gid:    0    0    0    0
FDSize:    64
Groups:    0 
NStgid:    2706
NSpid:    2706
NSpgid:    2686
NSsid:    1104
VmPeak:       29040 kB
VmSize:       29036 kB
VmLck:           0 kB
VmPin:           0 kB
VmHWM:        5272 kB
VmRSS:        5272 kB
VmData:         968 kB
VmStk:         136 kB
VmExe:         636 kB
VmLib:        4504 kB
VmPTE:          84 kB
VmPMD:          12 kB
VmSwap:           0 kB
HugetlbPages:           0 kB
Threads:    1
SigQ:    0/15406
SigPnd:    0000000000000000
ShdPnd:    0000000000000000
SigBlk:    0000000000000000
SigIgn:    0000000000001a01
SigCgt:    0000000180004002
CapInh:    0000000000000000
CapPrm:    0000003fffffffff
CapEff:    0000003fffffffff
CapBnd:    0000003fffffffff
CapAmb:    0000000000000000
Seccomp:    0
Cpus_allowed:    3
Cpus_allowed_list:    0-1
Mems_allowed:    00000000,00000001
Mems_allowed_list:    0
voluntary_ctxt_switches:    22963
nonvoluntary_ctxt_switches:    1007
Signal:11
Uname:Linux 4.4.0-75-generic x86_64
UserGroups:
CoreDump:base64
H4sICAAAAAAC/0NvcmVEdW1wAA==
```

---

### Post by TheFu on 2017-05-03
I though PIA only allowed 3 devices to be connected?  If you stop the others, does the same issue happen?
Why have more than 1 system on the same LAN running PIA?  Can't you make 1 the gateway for all the others?

---

### Post by Wadcutter on 2017-05-04
I believe PIA allows 5 at one time, but that is never an issue as I only run this one computer on it about 98% of the time and two, at the most. I thought it a PIA server or ISP problem, until I used one of my other computers for about 5 hours straight with no interruption. I later asked my wife to implement PIA on her computer at the same time that I was running this one in question. We both went to streaming music as a test. After about 45 minutes, my PIA went dead, but hers continued merrily on it way playing the music. Those two incidents gave me the notion that the fault was inside my system, not outside at the ISP or VPN servers. Add to that the crash messages I get occasionally with "openvpn" listed when PIA goes down, makes me think the problem lies entirely within this one computer. Un-installing/re-installing openvpn didn't fix it.

---

### Post by TheFu on 2017-05-04
I do not use network manager on any of my systems. 

Using the stock openvpn install with PIA settings on 14.04 desktop, 16.04 laptop and android devices. Use multiple different exit locations. Have not seen the issues you have.  Different exit locations use different ports and settings. Have you verified those are all current?

If you find the stack at the time of the crash, look for the lowest level to know where the crash was caused. Usually the lowest 20 lines of the stack explain everything - er ... at least which library where the crash happened.

---

### Post by Wadcutter on 2017-05-04
You last paragraph underscores how little I know. Although I included an error message, I have no idea what it means, where to find the stack you mention or what it even is, where the lowest level is, etc. I'm not a beginner, but this aspect of how things work is over my head. 

I'm also not exactly sure what "exit locations" are. I did try using different port settings per PIA tech support and in combo with TCP vs UDP, but none worked any better than port 1197 on UDP. Although 1194 seems to be the default port and works with my wife's desktop running Ubuntu 12.04, I cannot connect on it with my desktop. 

The frustrating part of this is the intermittent failure with nothing I can identify as a causative action and the fact that it just seemed to start on its own without any major changes to my system other than regular kernal browser upgrades. It's as if a component such as a resistor or capacitor overheats and kicks off. Yet, the minute I lose my server connection, I can re-connect and it will run reliably for another 20 min to an hour. Overheated devices usually don't permit an immediate re-connection.

---

### Post by TheFu on 2017-05-04
Support for 12.04 ended a few weeks ago. You need to move to a newer release ASAP!!! No more patches for 12.04 and the longer you wait, the harder it will be to move to a new release.

You can't just pick ports to use with PIA. Each exit location has specific ports and settings enabled. You must use those.
PIA has exit location all over the world. It is one of the reasons I pay them instead of just using my own.

---

### Post by Wadcutter on 2017-05-05
Both of our desktops need to go to 16.04 and it needs to be done as a clean install, but I just don't have time for that now. She mostly uses her Ipad for important stuff and only plays solitaire games on 12.04 with no Internet connection, so I am not too concerned. Possibly moving to 16.04 will solve my VPN problem. 14.04 has just been a series of troubles involving the upgrade from 12.04 last year. Docs went missing and cryptswap has never worked. Using suspend raises the odds of a crash later.

As for PIA, this link says that one can change ports and UDP/TCP if you have trouble with your connection dropping.  [https://helpdesk.privateinternetaccess.com/hc/en-us/articles/226851548](https://helpdesk.privateinternetaccess.com/hc/en-us/articles/226851548) However it did not work for me.

---

### Post by TheFu on 2017-05-06
There are many different port options in that link.  It isn't just 1. Have you tried them all?
Are you running the stock openvpn (apt install openvpn) or are you using the PIA installer stuff?
Is your system using any power management stuff?  Something that could disable the network after 45 min? Spins down a HDD?
Is it wifi or wired ethernet connected?
Inside the crash log, there should be a **stack trace**. Did you find that? 
You are using a California exit location. PIA has many different exit locations around the world. Try using some others. Does that help?

---

### Post by Wadcutter on 2017-05-07
Thanks for spending all this time with me on this tricky and frustrating issue.
I've tried all the different port and connection types listed.  I've been running the openvpn recommended by PIA. It was the only option available when I first set up PIA 2+ years ago. It's worked fine for a long time. Yesterday, I un-installed it and tried their proprietary application, but I couldn't get it to work at all (couldn't connect to any server) so I re-installed openvpn (using terminal and following their instructions) and I now can connect to any server, but can't keep it connected for more than an hour.

I've looked for any power or screen timeout, but didn't find any. Everything is set to never shut off when inactive. I also looked at var/spool/cron/crontabs but didn't find anything other than a daily backup for 'Back In Time'.

I'm on a wired router--no wifi. And I have tried many different exits--all over the US, Denmark and Turkey. No difference.

Here's where I was wrong in my initial post. It does not shut down at 10 minute run times. It is shutting down pretty regularly at 1 hour times. That's 1 hour from the time I connect to an exit point, not 2:15, 3:15 etc I apologize for incorrect info, but I wasn't carefully timing and documenting its failure increments. Today, I've kept a written paper log and it has dropped pretty close to one hour after connecting every time.
I did find a 'stacktrace' listed in the last crash report. I don't know how long it's supposed to be, but I copied from first mention of it to the end of the crash report. At the end they mention 'passwd" being out of date, so I went to Synaptic mgr and updated it. I don't think it affects this issue since nothing has changed.

```
Stacktrace:
 #0 0x00007f168ff2dc37 in __GI_raise (sig=sig@entry=6) at../nptl/sysdeps/unix/sysv/linux/raise.c:56
        resultvar = 0
        pid = 2696
        selftid = 2696
 #1 0x00007f168ff31028 in __GI_abort () at abort.c:89
        save_stage = 2
        act = {__sigaction_handler = {sa_handler = 0x14, sa_sigaction =0x14}, sa_mask = {__val = {139734881855929, 94645972454064, 55, 92,1494106749, 94648194301951, 140736634697752, 1, 139734884773856,94645972454064, 0, 4222451713, 94645972685768, 167503724553,25769803790, 502511173636}}, sa_flags = 6, sa_restorer =0x561400000001}
        sigs = {__val = {32, 0 <repeats 15 times>}}
 #2 0x00007f168ff6a2a4 in __libc_message (do_abort=do_abort@entry=1,fmt=fmt@entry=0x7f169007bef0 "*** Error in `%s': %s: 0x%s***\n") at ../sysdeps/posix/libc_fatal.c:175
        ap = {{gp_offset = 40, fp_offset = 0, overflow_arg_area =0x7fffcd1e38f0, reg_save_area = 0x7fffcd1e3880}}
        fd = 2
        on_2 = <optimized out>
        list = <optimized out>
        nlist = <optimized out>
        cp = <optimized out>
        written = <optimized out>
 #3 0x00007f168ff7656e in malloc_printerr (ptr=<optimized out>,str=0x7f169007bfd8 "double free or corruption (!prev)",action=1) at malloc.c:4996
        buf = "000056147b94d5a0"
        cp = <optimized out>
 #4 _int_free (av=<optimized out>, p=<optimized out>,have_lock=0) at malloc.c:3840
        size = <optimized out>
        fb = <optimized out>
        nextchunk = <optimized out>
        nextsize = <optimized out>
        nextinuse = <optimized out>
        prevsize = <optimized out>
        bck = <optimized out>
        fwd = <optimized out>
        errstr = <optimized out>
        locked = <optimized out>
 #5 0x00007f168ffcb0c8 in __GI_freeaddrinfo (ai=0x56147b94d5f0) at../sysdeps/posix/getaddrinfo.c:2681
        p = 0x56147b94d5a0
 #6 0x000056147a3bb882 in ?? ()
 Nosymbol table info available.
 #7 0x000056147a3bc475 in ?? ()
 Nosymbol table info available.
 #8 0x000056147a37db1e in ?? ()
 Nosymbol table info available.
 #9 0x000056147a37e250 in ?? ()
 Nosymbol table info available.
 #100x000056147a396638 in ?? ()
 Nosymbol table info available.
 #110x00007f168ff18f45 in __libc_start_main (main=0x56147a3691e0,argc=35, argv=0x7fffcd1e4ae8, init=<optimized out>,fini=<optimized out>, rtld_fini=<optimized out>,stack_end=0x7fffcd1e4ad8) at libc-start.c:287
        result = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {0,-1823634624519948726, 94645949731301, 140736634702560, 0, 0,1823605747687274058, 1773356243207370314}, mask_was_saved = 0}}, priv= {pad = {0x0, 0x0, 0x7fffcd1e4c08, 0x7f169137b1c8}, data = {prev =0x0, cleanup = 0x0, canceltype = -853652472}}}
        not_first_call = <optimized out>
 #120x000056147a36920e in ?? ()
 Nosymbol table info available.
StacktraceAddressSignature:/usr/sbin/openvpn:6:x86_64:/lib/x86_64-linux-gnu/libc-2.19.so+36c37:/lib/x86_64-linux-gnu/libc-2.19.so+3a028:/lib/x86_64-linux-gnu/libc-2.19.so+732a4:/lib/x86_64-linux-gnu/libc-2.19.so+7f56e:/lib/x86_64-linux-gnu/libc-2.19.so+d40c8:/usr/sbin/openvpn+5d882:/usr/sbin/openvpn+5e475:/usr/sbin/openvpn+1fb1e:/usr/sbin/openvpn+20250:/usr/sbin/openvpn+38638:/lib/x86_64-linux-gnu/libc-2.19.so+21f45:/usr/sbin/openvpn+b20e
StacktraceTop:
__libc_message (do_abort=do_abort@entry=1,fmt=fmt@entry=0x7f169007bef0 "*** Error in `%s': %s: 0x%s***\n") at ../sysdeps/posix/libc_fatal.c:175
malloc_printerr (ptr=<optimized out>, str=0x7f169007bfd8"double free or corruption (!prev)", action=1) atmalloc.c:4996
_int_free (av=<optimized out>, p=<optimized out>,have_lock=0) at malloc.c:3840
__GI_freeaddrinfo (ai=0x56147b94d5f0) at../sysdeps/posix/getaddrinfo.c:2681
 ??()
Tags: trusty
ThreadStacktrace:
 .
Thread 1 (Thread 0x7f169134f740 (LWP 2696)):
 #0 0x00007f168ff2dc37 in __GI_raise (sig=sig@entry=6) at../nptl/sysdeps/unix/sysv/linux/raise.c:56
        resultvar = 0
        pid = 2696
        selftid = 2696
 #1 0x00007f168ff31028 in __GI_abort () at abort.c:89
        save_stage = 2
        act = {__sigaction_handler = {sa_handler = 0x14, sa_sigaction =0x14}, sa_mask = {__val = {139734881855929, 94645972454064, 55, 92,1494106749, 94648194301951, 140736634697752, 1, 139734884773856,94645972454064, 0, 4222451713, 94645972685768, 167503724553,25769803790, 502511173636}}, sa_flags = 6, sa_restorer =0x561400000001}
        sigs = {__val = {32, 0 <repeats 15 times>}}
 #2 0x00007f168ff6a2a4 in __libc_message (do_abort=do_abort@entry=1,fmt=fmt@entry=0x7f169007bef0 "*** Error in `%s': %s: 0x%s***\n") at ../sysdeps/posix/libc_fatal.c:175
        ap = {{gp_offset = 40, fp_offset = 0, overflow_arg_area =0x7fffcd1e38f0, reg_save_area = 0x7fffcd1e3880}}
        fd = 2
        on_2 = <optimized out>
        list = <optimized out>
        nlist = <optimized out>
        cp = <optimized out>
        written = <optimized out>
 #3 0x00007f168ff7656e in malloc_printerr (ptr=<optimized out>,str=0x7f169007bfd8 "double free or corruption (!prev)",action=1) at malloc.c:4996
        buf = "000056147b94d5a0"
        cp = <optimized out>
 #4 _int_free (av=<optimized out>, p=<optimized out>,have_lock=0) at malloc.c:3840
        size = <optimized out>
        fb = <optimized out>
        nextchunk = <optimized out>
        nextsize = <optimized out>
        nextinuse = <optimized out>
        prevsize = <optimized out>
        bck = <optimized out>
        fwd = <optimized out>
        errstr = <optimized out>
        locked = <optimized out>
 #5 0x00007f168ffcb0c8 in __GI_freeaddrinfo (ai=0x56147b94d5f0) at../sysdeps/posix/getaddrinfo.c:2681
        p = 0x56147b94d5a0
 #6 0x000056147a3bb882 in ?? ()
 Nosymbol table info available.
 #7 0x000056147a3bc475 in ?? ()
 Nosymbol table info available.
 #8 0x000056147a37db1e in ?? ()
 Nosymbol table info available.
 #9 0x000056147a37e250 in ?? ()
 Nosymbol table info available.
 #100x000056147a396638 in ?? ()
 Nosymbol table info available.
 #110x00007f168ff18f45 in __libc_start_main (main=0x56147a3691e0,argc=35, argv=0x7fffcd1e4ae8, init=<optimized out>,fini=<optimized out>, rtld_fini=<optimized out>,stack_end=0x7fffcd1e4ad8) at libc-start.c:287
        result = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {0,-1823634624519948726, 94645949731301, 140736634702560, 0, 0,1823605747687274058, 1773356243207370314}, mask_was_saved = 0}}, priv= {pad = {0x0, 0x0, 0x7fffcd1e4c08, 0x7f169137b1c8}, data = {prev =0x0, cleanup = 0x0, canceltype = -853652472}}}
        not_first_call = <optimized out>
 #120x000056147a36920e in ?? ()
 Nosymbol table info available.
Title:openvpn assert failure: *** Error in `/usr/sbin/openvpn': double freeor corruption (!prev): 0x000056147b94d5a0 ***
UnreportableReason:
 Youhave some obsolete package versions installed. Please upgrade thefollowing packages and check if the problem still occurs:
 
passwd
UpgradeStatus:No upgrade log present (probably fresh install)
_MarkForUpload:True
```

---

### Post by wildmanne39 on 2017-05-07
*Thread moved to **Networking & Wireless**.*

---

### Post by TheFu on 2017-05-07
Check the way that your password authentication is stored for VPN use. There is a setting that keeps it in RAM. This is less secure, but will let openvpn automatically re-authenticate.  I spent 5 min look for it in the manpage and didn't find it. Sorry.

---

### Post by Wadcutter on 2017-05-07
i apologize for not using the code tags. I neglected to take the time to learn how to do it. It didn't take any time at all--my bad. I don't throw my socks on the floor for my wife to pick up and I'm sorry I made anyone else have to edit my post(s).

As for the problem: I've DEFINITELY pinned it down to something in my computer disrupting my PIA connection at exactly 60 minutes from the time I connect.

I'm wondering about 'Suspend'. I know that Suspending drops the VPN because when I awake from Suspend, my regular ISP connection is running, but the VPN is not--the same situation that happens here every 60 min. Could my computer be going partially into a suspend mode every one hour and only cutting off the VPN, but not actually suspending the rest of the computer? I've set the 'Power Down' graphic setting to "Never", but that doesn't mean that it isn't somehow corrupted to think I want it to power down every hour. Of course, that is supposed to apply if idle, but in this case the VPN is being disrupted every hour even if I'm using it.

Could it be an acpi or apm problem? My computer is old--I don't know if it even has acpi.

---

### Post by wildmanne39 on 2017-05-07
> i apologize for not using the code tags. I neglected to take the time to learn how to do it. It didn't take any time at all--my bad. I don't throw my socks on the floor for my wife to pick up and I'm sorry I made anyone else have to edit my post(s).

No problem, we all were new once and this is how most of us learn.:)

---

### Post by TheFu on 2017-05-07
The error ... 
```
UnreportableReason:
 Youhave some obsolete package versions installed. Please upgrade thefollowing packages and check if the problem still occurs:
```

Run this to patch the system. This assumes that openvpn is installed through the package manager, not directly from some PIA-provided tool.
```
sudo apt update
sudo apt upgrade
```

I still think it is related to openvpn config settings that aren't keeping the PIA credentials in RAM. Remember reading about it somewhere. Research that. I googled - [https://serverfault.com/questions/436333/getting-disconnected-from-openvpn-server-each-hour](https://serverfault.com/questions/436333/getting-disconnected-from-openvpn-server-each-hour)  reneg-sec

Suspend does bring down the networking, but I doubt that is really happening if this happens while you are actively using the system.  I've never heard of any VPN coming back up automatically post-suspend.  **Anything** can be scripted, if desired.

---

### Post by Wadcutter on 2017-05-09
Thank you very much, TheFu. You nailed it with your link involving the renegotiation interval. The first problem was that I didn't use my stopwatch and clipboard to correctly identify the connection loss as occurring every 60 minutes. I was using subjective evaluations and thought it was occurring at random times, It was not. My mistake. If you don't correctly describe a problem, you probably won't fix it. Then, although I spent a month googling for something akin to my issue, I was never able to find someone with the right problem since I didn't understand the problem. The third barrier to finding a solution was that before now, I was completely ignorant of VPN renegotiation functions. I still am a bit uncertain about all the variances, but I think I now know enough to stay on top of it while learning more.

To fix it in my PIA system, I had to go into the network manager, to the VPN tab for an individual server or exit point, to the advanced setting and manually click on the box for "Use Custom Renegotiation Interval" making sure it was set to "0". The default setting shown for all servers is "0", but if the box isn't checked, the value is greyed out and it apparently defaults to 3600 seconds (1 hour). This is all because I am apparently using PIA's Openvpn configurations settings and their installation instructions rather than doing it through the package manager. Since I am paying them and am not as knowledgeable about my OS as I would like to be, I followed their instructions rather than trying to learn all the intricacies of Openvpn. Apparently I will have to manually set the renegotiation interval for each exit point that I use.

I still don't know why this problem popped up. Something changed with PIA's system that apparently affected some computers, but not others. I have 6 different devices running PIA (usually only one at a time): running multiple operating systems (Ubuntu, Point Linux, IOS, Windows) and Ubuntu 14.04 was the only one that suddenly started misbehaving. Several other people complained to PIA on their forum that they suddenly started having this problem of the connection dropping in early April. The PIA spokesperson pretty much denied any causation from their end and the  discussions got heated. I wouldn't point an accusing finger at anyone, but I do know that my system had run for 2 1/2 years on this same computer under Ubuntu 12.04 and then 14.04 with zero problems until the first of this April. The worst part is that I recommended PIA to a friend who has much less experience with computers than I do. I hope her laptop wasn't affected.

Thanks again for all the time you spent getting me squared away. I hope this thread may help someone else down the road.

---

