---
title: "Belkin Wireless G router"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by dentree4 on 2008-01-28
Hi All,

I am trying to install 3 belkin usb 802.11g adapters on my ubuntu box. It's quite old, so it only runs a terminal.

I need to install the F5D7050 drivers, but I can't get ndiswrapper-utils anywhere. I've tried looking for instructions on this and other forums 

I have everything else configured. The adapters show up under lsusb, and lshw -C network | less

Can anyone help?

---

### Post by trehoffman on 2008-02-01
dentree4,

1) [Download the debian package for ndiswrapper-utils-1.9 via this link. ]("archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb")

2) Then go to the terminal and do the following:

[INDENT]"cd [location where debian package is]"[/INDENT]
[INDENT]"sudo dpkg -i ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb "[/INDENT]
[INDENT]"sudo apt-get install ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb "[/INDENT]

3) Show me an output of what happens (if it does not work).

---

### Post by dannyboy79 on 2008-02-01
there's native linux drivers that work for this adapter. see here: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
(i have that same belkin adapter and I used an older tar ball of the rt73_daily. the tarball I used is here:
 [http://ubuntuforums.org/showthread.php?t=400236&page=75](http://ubuntuforums.org/showthread.php?t=400236&page=75)
then just follow the instructions and you'll be golden.

---

