---
title: "nfsroot with local /boot"
date: 2018-09-01
forum: Networking &amp; Wireless
---

### Post by seb.r on 2018-09-01
I try to install Latest lubuntu on HP T5741 thin client with nfsroot and local /boot. For now /boot is on the internal 1GB flash memory and / on an external harddrive.
Then i tried to move / to nfs using these instructions: [http://www.vdr-wiki.de/wiki/index.php/Root_%C3%BCber_NFS_mounten](http://www.vdr-wiki.de/wiki/index.php/Root_%C3%BCber_NFS_mounten)
The system is booting but there are problems with the network. eth0 disappeared and there is a new interface and DNS settings not work.
Is there any tutorial out there to help?
This one if pretty much outdated: [https://help.ubuntu.com/community/Installation/OnNFSDriveWithLocalBoot](https://help.ubuntu.com/community/Installation/OnNFSDriveWithLocalBoot)

---

### Post by TheFu on 2018-09-02
I haven't tried to run Linux over NFS, ever.  Doubt I can help with that. Sorry.
The Linux file system hierarchy standards has specifics for what can and cannot be remote. Definitely worth a read.  In all my time here, you are the first who I've seen trying to run from NFS.  If you have a support contract with Canonical, now is the time to call them.

How network devices are named changed a few years ago when systemd took over the udev project. You can force the old behavior with some grub options, if you like.   [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/) explains the new method, but also has ways to force the older names. It works.

Networking has been changing with every major release since 12.04.  To get help, we need to know which exact release you are using. It changed again in 18.04, BTW.  ifupdown is replaced by netplan.

---

### Post by seb.r on 2018-09-02
Thanks for your answer. The nfsroot is working, the only problems I seem to have so far is DNS. I am using lubuntu 18.04 desktop i386.
In grub2 I set ```
ip=dhcp
``` and in /etc/network/interfaces I set ```
iface enp4s0 inet manual
``` like mentioned here: [https://help.ubuntu.com/community/DisklessUbuntuHowto#Creating_your_NFS_installation](https://help.ubuntu.com/community/DisklessUbuntuHowto#Creating_your_NFS_installation)
But DNS is not working. 
If i manually add my DNS with ```
systemd-resolve --set-dns=192.168.0.16 --interface=enp4s0

``` then it works until next reboot.
Where to start troubleshooting this problem? With grub options or within the system?

---

### Post by TheFu on 2018-09-02
/etc/network/interfaces isn't used.  You need to look at netplan.
I don't know anything about the other stuff.

---

