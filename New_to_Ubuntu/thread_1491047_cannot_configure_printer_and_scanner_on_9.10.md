---
title: "cannot configure printer and scanner on 9.10"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by guyholmes on 2010-05-23
Hi,

I have just upgraded from 9.10 to 10.04 LTS. My Epson Stylus Office BX300F printer and scanner don't work. Can you help me configure them? Here is the troublshooting readout for the printer (I then show what the terminal readout is when I add the command: sudo dpkg -i --force-architecture pipslite_1.4.0-5_i386.deb):

 	 	 	 	 	  sudo dpkg -i --force-architecture pipslite_1.4.0-5_i386.deb
 
guy@linuxpc:~$ sudo dpkg -i --force-architecture pipslite_1.4.0-5_i386.deb
[sudo] password for guy: 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 248412 files and directories currently installed.)
Preparing to replace pipslite 1.4.0-5 (using pipslite_1.4.0-5_i386.deb) ...
failed to uninstall PPD file: "/eklite.ppd
/eklite.ppd
/eklite.ppd
/eklite.ppd
/eklite.ppd
/eklite.ppd
/eklite.ppd" not found
Unpacking replacement pipslite ...
Setting up pipslite (1.4.0-5) ...
Install Message > Described entry of LITE in services.
Install Message > Backup file is /etc/services.bak.
install: target `' is not a directory: No such file or directory
Install Message > Start /usr/lib/pipslite/setup to change setup.
Install Message > Start /usr/bin/pipslite-install to make ppd file.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by guyholmes on 2010-05-25
i have just solved both the printer and the scanner.

---

### Post by dneary on 2010-10-19
Hi,

> **guyholmes said:**
> i have just solved both the printer and the scanner.

It'd be really nice if you said how you fixed it. This is also my office printer/scanner, and once again, it is not working after an upgrade. I documented my issues after upgrading to 9.04 for posterity: [http://blogs.gnome.org/bolsh/2009/05/26/trial-by-fire-distro-upgrade/](http://blogs.gnome.org/bolsh/2009/05/26/trial-by-fire-distro-upgrade/) - could you do the same, please (it seems the libsane-backends-extra package doesn't exist any more, and the epkowa driver isn't shipped in libsane or libsane-extras).

Thanks,
Dave.

---

### Post by mbfortuna on 2012-01-17
Hello guys,
I'm using ubuntu 10.04 too and I have an epson office bx300f and I can't use the scanner. The printer goes good but the scanner is not recognized. When I use lsusb I have this message:
root@mbfortuna-laptop:/home/mbfortuna# lsusb
Bus 002 Device 004: ID 04b8:0848 Seiko Epson Corp. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5094 IMC Networks 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 and no matter what I do nothing works.
Can you be so nice and help me?
I'm not really so good on Linux but I learn fast so if you can help me please be very... how can I say... basic LOL :D
Thank you in advance
Mauricio

---

