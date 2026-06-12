---
title: "Net setup script on SystemRescueCD"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by dhopley on 2008-01-20
Dear Forum , 
Hi , I have had a series of problems with sc92031 . My set up is a dual boot Pentium III under Windows 98SE and Ubuntu 7.10 , which I have just upgraded from Ubuntu 7.04 , and my PC is fitted with an ethernet card , an SC92031 10/100 PCI . Originally although I was able to compile the drivers on my supplied CD for both the 98SE and Ubuntu 7.04 systems for use by the network card , unfortunately there are compile problems under Ubuntu 7.10 , specifically a missing module 'PCI_Module_INIT' . I installed ndiswrapper-1.45 under linux-headers-2.6.22-14-generic and that was working fine with my Windows 98SE driver file netslnt.inf , but after the recent Ubuntu 7.10 upgrade of linux-headers-2.6.22.14 and linux-headers-2.6.22-14-generic from version 46 to 47 my wired connection was lost . 
I have succeeded in getting it working again as follows :
derek@ubuntu:~$ gksudo gedit /etc/modprobe.d/blacklist
and adding the line below :
blacklist sc92031
The reason seems that sc92031.ko has been included in the 18/12/07 upgrade set of drivers , but in my case isn't working . What is intriguing is that in using the SystemRescueCD for backups of the 98SE and Ubuntu 7.10 I am able to have the network card recognised immediately via a simple script called net-setup  eth0 which seems to work quickly and perfectly . Is there any way I can import that script into Ubuntu 7.10 ?
Derek

---

