---
title: "Intermittent issues with Samba"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by whatever69 on 2008-06-06
Hi, 

I have a windows media centre pc that connects to my ubuntu 8.04 server through Samba.  I keep getting these permission denied errors, and sometimes it just dies but then reconnects to windows eventually.  Any help is appreciated!  Here's the log file:

> [2008/06/06 17:11:11, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/raid failed. Permission denied
[2008/06/06 17:11:17, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/raid failed. Permission denied
[2008/06/06 17:11:17, 1] smbd/service.c:make_connection_snum(1033)
  windowspc (192.168.0.107) connect to service raid initially as user roy (uid=1000, gid=1000) (pid 5859)
[2008/06/06 17:13:20, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/raid failed. Permission denied
[2008/06/06 17:14:51, 0] lib/substitute.c:alloc_sub_basic(463)
  alloc_sub_basic: NULL source string!  This should not happen
[2008/06/06 17:14:51, 0] lib/fault.c:fault_report(41)
  ===============================================================
[2008/06/06 17:14:51, 0] lib/fault.c:fault_report(42)
  INTERNAL ERROR: Signal 11 in pid 5859 (3.0.28a)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2008/06/06 17:14:51, 0] lib/fault.c:fault_report(44)
  
  From: [http://www.samba.org/samba/docs/Samba3-HOWTO.pdf](http://www.samba.org/samba/docs/Samba3-HOWTO.pdf)
[2008/06/06 17:14:51, 0] lib/fault.c:fault_report(45)
  ===============================================================
[2008/06/06 17:14:51, 0] lib/util.c:smb_panic(1633)
  PANIC (pid 5859): internal error
[2008/06/06 17:14:51, 0] lib/util.c:log_stack_trace(1737)
  BACKTRACE: 12 stack frames:
   #0 /usr/sbin/smbd(log_stack_trace+0x2d) [0x828a92d]
   #1 /usr/sbin/smbd(smb_panic+0x5d) [0x828aa5d]
   #2 /usr/sbin/smbd [0x82752da]
   #3 [0xb7f22420]
   #4 /usr/sbin/smbd(volume_label+0x54) [0x809b2a4]
   #5 /usr/sbin/smbd(handle_trans2+0x25a) [0x80ecb1a]
   #6 /usr/sbin/smbd(reply_trans2+0x69c) [0x80f35dc]
   #7 /usr/sbin/smbd [0x810f89e]
   #8 /usr/sbin/smbd(smbd_process+0x89b) [0x8110cfb]
   #9 /usr/sbin/smbd(main+0xa18) [0x835e8f8]
   #10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b36450]
   #11 /usr/sbin/smbd [0x80942c1]
[2008/06/06 17:14:51, 0] lib/util.c:smb_panic(1638)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 5859]
[2008/06/06 17:14:51, 0] lib/util.c:smb_panic(1646)
  smb_panic(): action returned status 0
[2008/06/06 17:14:51, 0] lib/fault.c:dump_core(181)
  dumping core in /var/log/samba/cores/smbd
[2008/06/06 17:14:51, 0] lib/util_sock.c:write_data(562)
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2008/06/06 17:14:51, 0] lib/util_sock.c:send_smb(769)
  Error writing 4 bytes to client. -1. (Connection reset by peer)
[2008/06/06 17:14:51, 1] smbd/service.c:make_connection_snum(1033)
  windowspc (192.168.0.107) connect to service raid initially as user roy (uid=1000, gid=1000) (pid 5879)

Any help would be appreciated.  Here are some of my files:

> roy@ubuntuserver:/var/lib/samba/usershares$ more /var/lib/samba/usershares/raid 
#VERSION 2
path=/mnt/raid
comment=
usershare_acl=S-1-1-0:F
guest_ok=y


/etc/smb.conf

> #======================= Global Settings =======================

[global]

workgroup = PEANUTS 
remote announce = 192.168.0.255/PEANUTS
server string = %h server (Samba, Ubuntu)
dns proxy = no
interfaces = eth0 lo 
bind interfaces only = true
log file = /var/log/samba/log.%m
max log size = 1000
panic action = /usr/share/samba/panic-action %d
security = user 

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how nsuccessful authentication attempts are mapped 
# to anonymous connections
map to guest = bad user

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = no 

# lpr(ng) printing. You may wish to override the location of the
# printcap file
   printing = bsd
   printcap name = /dev/null
   disable spoolss = yes
   socket options = TCP_NODELAY
   usershare allow guests = yes 

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

---

