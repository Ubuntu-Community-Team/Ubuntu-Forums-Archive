---
title: "Is it samba? How do I configure samba on ubuntu to work well?"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by IFailAtLinux on 2008-06-17
I'm trying to get samba working with my home network, but for now I'm failing... And completely clueless.

You see, I've managed to get it working totally strange way - the windows can't access shares on my linux, but mu linux easily can access shares on my windows... Too easily. It can actually see not only shares, but whole disks C and D(all of them, in other words), while they are not shared.

I was playing around with samba configuration trough webmin, restarting server every time and... nothing changed. Ever.

So I went evil and purged samba. And what? The thing is that I still can use
smb://windowsUser@windowsComputerIPAdress/
on my kububtu and it still does show everything on my windows computer! That's... crazy. I mean, isn't smb from samba? And I uninstalled samba? And why does it see C$ and D$? And it accepts write/read permissions on my shares, but has full power over everything in C$ and D$(in other words my all files).

I've configured samba few times before on fedora and it always worked well... But I completely can't do it on ubuntu. And I don't know why ubuntu does so much problems about swat?

Anyway, how do I configure samba to get normal filesharing between my windows machine and kubuntu machine? (I.E. works both ways and shows only shared files)

---

### Post by Iowan on 2008-06-17
Samba is a collection - most Ubuntu versions come with the client installed,   the client lets Ubuntu access Windows shares. The Server lets Ubuntu share files, but samba-server must be installed.
Samba client *should* have no more access to Windows files than the shares allow.

---

### Post by infinitezero on 2008-06-17
Following this link and download the Samba Install on Kubuntu 7.04 - rev1.3.pdf.tar.gz .

It works the same for 8.04.


[http://ubuntuforums.org/showthread.php?t=575214](http://ubuntuforums.org/showthread.php?t=575214)


Hope it helps,
iz
_________

 If samba is not automaticlly starting after you reboot do the following:

Just enter (without quotes), "/etc/init.d/samba start", into /etc/rc.local to have it executed during boot.

Make sure you enter it before, and leave intact, the "exit 0" line!


The reboot and check the status:

sudo /etc/init.d/samba status


One other thing, if Kubuntu's firewall is running you may have to disable it. I am behind a router, so I don't about it.

Disable Kubuntu Firewall:
sudo ufw disable && sudo ufw status

If Samba is still not starting at boot edit the smb.conf file to comment out the following:

;   interfaces = 127.0.0.0/8 eth0
;    bind interfaces only = true

Samba does not play well with DHCP.

iz

---

