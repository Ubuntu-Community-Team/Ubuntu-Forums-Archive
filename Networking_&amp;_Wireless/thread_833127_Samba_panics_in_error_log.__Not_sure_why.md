---
title: "Samba panics in error log.  Not sure why"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by whatever69 on 2008-06-18
Hi,

I have a windows media centre pc connected to my Ubuntu machine via samba.  I keep getting this in my error log for my windowspc.  I would prefer if only my "roy" account is able to access this.  No need for guests.


> $ tail log.windowspc
[2008/06/17 23:37:40, 0] lib/util.c:smb_panic(1638)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 6433]
[2008/06/17 23:37:40, 0] lib/util.c:smb_panic(1646)
  smb_panic(): action returned status 0
[2008/06/17 23:37:40, 0] lib/fault.c:dump_core(181)
  dumping core in /var/log/samba/cores/smbd
[2008/06/17 23:37:44, 1] smbd/service.c:make_connection_snum(1033)
  windowspc (192.168.0.107) connect to service raid initially as user roy (uid=1000, gid=1000) (pid 6437)
[2008/06/17 23:40:29, 1] smbd/service.c:close_cnum(1230)
  windowspc (192.168.0.107) closed connection to service raid
roy@ubuntuserver:/var/log/samba$ tail -n40 log.windowspc
[2008/06/17 23:36:09, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/raid failed. Permission denied
[2008/06/17 23:37:40, 0] lib/substitute.c:alloc_sub_basic(463)
  alloc_sub_basic: NULL source string!  This should not happen
[2008/06/17 23:37:40, 0] lib/fault.c:fault_report(41)
  ===============================================================
[2008/06/17 23:37:40, 0] lib/fault.c:fault_report(42)
  INTERNAL ERROR: Signal 11 in pid 6433 (3.0.28a)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2008/06/17 23:37:40, 0] lib/fault.c:fault_report(44)

  From: [http://www.samba.org/samba/docs/Samba3-HOWTO.pdf](http://www.samba.org/samba/docs/Samba3-HOWTO.pdf)
[2008/06/17 23:37:40, 0] lib/fault.c:fault_report(45)
  ===============================================================
[2008/06/17 23:37:40, 0] lib/util.c:smb_panic(1633)
  PANIC (pid 6433): internal error
[2008/06/17 23:37:40, 0] lib/util.c:log_stack_trace(1737)
  BACKTRACE: 12 stack frames:
   #0 /usr/sbin/smbd(log_stack_trace+0x2d) [0x828ab6d]
   #1 /usr/sbin/smbd(smb_panic+0x5d) [0x828ac9d]
   #2 /usr/sbin/smbd [0x827551a]
   #3 [0xb7f67420]
   #4 /usr/sbin/smbd(volume_label+0x54) [0x809b314]
   #5 /usr/sbin/smbd(handle_trans2+0x25a) [0x80ecb8a]
   #6 /usr/sbin/smbd(reply_trans2+0x69c) [0x80f364c]
   #7 /usr/sbin/smbd [0x810f90e]
   #8 /usr/sbin/smbd(smbd_process+0x89b) [0x8110d6b]
   #9 /usr/sbin/smbd(main+0xa18) [0x835ec18]
   #10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b7b450]
   #11 /usr/sbin/smbd [0x8094331]
[2008/06/17 23:37:40, 0] lib/util.c:smb_panic(1638)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 6433]
[2008/06/17 23:37:40, 0] lib/util.c:smb_panic(1646)
  smb_panic(): action returned status 0
[2008/06/17 23:37:40, 0] lib/fault.c:dump_core(181)
  dumping core in /var/log/samba/cores/smbd
[2008/06/17 23:37:44, 1] smbd/service.c:make_connection_snum(1033)
  windowspc (192.168.0.107) connect to service raid initially as user roy (uid=1000, gid=1000) (pid 6437)
[2008/06/17 23:40:29, 1] smbd/service.c:close_cnum(1230)
  windowspc (192.168.0.107) closed connection to service raid


The share in question:

> $ la /var/lib/samba/usershares
total 12
drwxrwx--T 2 root sambashare 4096 2008-06-06 16:02 .
drwxr-xr-x 5 root root       4096 2008-05-09 13:25 ..
-rw-r--r-- 1 roy  roy          70 2008-06-06 16:02 raid


> $ more /var/lib/samba/usershares/raid
#VERSION 2
path=/mnt/raid
comment=
usershare_acl=S-1-1-0:F
guest_ok=y


And here's my smb.conf file.  Any tips/advice?

> $ sudo testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = PEANUTS
        server string = %h server (Samba, Ubuntu)
        interfaces = lo, eth0
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        load printers = No
        printcap name = /dev/null
        disable spoolss = Yes
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root
        printing = bsd
        print command = lpr -r -P'%p' %s
        lpq command = lpq -P'%p'
        lprm command = lprm -P'%p' %j

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers


---

### Post by adtrakmike on 2008-07-11
Same problem here, exactly the same issue, heres my log:

> [2008/07/11 15:21:05, 1] smbd/service.c:make_connection_snum(1033)
  mickwhitby (192.168.101.39) connect to service data initially as user administrator (uid=1001, gid=1001) (pid 19663)
[2008/07/11 15:21:08, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/data failed. Permission denied
[2008/07/11 15:21:08, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/data failed. Permission denied
[2008/07/11 15:21:08, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/data failed. Permission denied
[2008/07/11 15:21:08, 0] lib/substitute.c:alloc_sub_basic(463)
  alloc_sub_basic: NULL source string!  This should not happen
[2008/07/11 15:21:08, 0] lib/fault.c:fault_report(41)
  ===============================================================
[2008/07/11 15:21:08, 0] lib/fault.c:fault_report(42)
  INTERNAL ERROR: Signal 11 in pid 19663 (3.0.28a)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2008/07/11 15:21:08, 0] lib/fault.c:fault_report(44)
  
  From: [http://www.samba.org/samba/docs/Samba3-HOWTO.pdf](http://www.samba.org/samba/docs/Samba3-HOWTO.pdf)
[2008/07/11 15:21:08, 0] lib/fault.c:fault_report(45)
  ===============================================================
[2008/07/11 15:21:08, 0] lib/util.c:smb_panic(1633)
  PANIC (pid 19663): internal error
[2008/07/11 15:21:08, 0] lib/util.c:log_stack_trace(1737)
  BACKTRACE: 12 stack frames:
   #0 /usr/sbin/smbd(log_stack_trace+0x2d) [0x828ab6d]
   #1 /usr/sbin/smbd(smb_panic+0x5d) [0x828ac9d]
   #2 /usr/sbin/smbd [0x827551a]
   #3 [0xb7f3f420]
   #4 /usr/sbin/smbd(volume_label+0x54) [0x809b314]
   #5 /usr/sbin/smbd(handle_trans2+0x25a) [0x80ecb8a]
   #6 /usr/sbin/smbd(reply_trans2+0x69c) [0x80f364c]
   #7 /usr/sbin/smbd [0x810f90e]
   #8 /usr/sbin/smbd(smbd_process+0x89b) [0x8110d6b]
   #9 /usr/sbin/smbd(main+0xa18) [0x835ebf8]
   #10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b53450]
   #11 /usr/sbin/smbd [0x8094331]
[2008/07/11 15:21:08, 0] lib/util.c:smb_panic(1638)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 19663]
[2008/07/11 15:21:08, 0] lib/util.c:smb_panic(1646)
  smb_panic(): action returned status 0
[2008/07/11 15:21:08, 0] lib/fault.c:dump_core(181)
  dumping core in /var/log/samba/cores/smbd
[2008/07/11 15:21:08, 1] smbd/service.c:make_connection_snum(1033)

---

