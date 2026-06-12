---
title: "SSH to windowsXP fat32 filesystem hangs"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by fenifur on 2008-01-26
PC#1 = Ubuntu 7.10; filesystem=ext3; hardwired to router; 
PC#2 = Windows XP SP2; filesystem FAT32; CYGWIN installed; wireless card signal  strength excellent

I have cygwin installed on PC#2 and have configured ssh on it.  netstat -na | grep 22
reports listening on port 22.  PC#1 also reports listening on port 22.  

From PC#1 I can ping both PC#2 and PC#1.  
From PC#2  I can ping PC#2 and PC#1
From PC#2 I can ssh w/o password to PC#1.

However, I cannot ssh back to PC#2 from PC#1 ssh shell or ssh from PC#1 to PC#2.  After executing ssh command it just sits there.

I have had success with SSHing back and forth to another Dell Windows XP PC(#3) but that power supply died and I can no longer test on that machine.  Also PC#3 was wired to router.

Any suggestions would be greatly appreciated.

---

### Post by kevdog on 2008-01-26
try ssh -vvv to get more output

---

### Post by fenifur on 2008-01-27
I assume those were three "v"s and not a "v" and a "w".  Here is output and where it sits:

=>ssh -vvv PC#2
OpenSSH_4.6p1 Debian-5ubuntu0.1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to PC#2 [192.168.0.102] port 22.

---

### Post by kevdog on 2008-01-27
Thats it??

That wasn't very helpful (but neither was my response)

Looks like a connection was never established with the server -- firewall problem perhaps?

---

### Post by fenifur on 2008-01-28
Duhhh!  Windows firewall enabled with no exceptions.  Thanks for your help.    ](*,)

---

