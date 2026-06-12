---
title: "Windows XP and Ubuntu 6.0.6"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by fred_scotland on 2006-09-21
I am running Ununtu 6.0.6 as a Guest virtual machine on a Windows XP PRO Host. I want to print to the HP 1100 laserjet connected to the parallel port (LPT1) of the Windows machine. I have tried all of the suggestions made and none of them work the only way to print is to connect it as a local printer but this is not what I want, as it disables the printer in windows then. 

This is the sort of area that points up the inherrent weakness in Linux, it cannot drive hardware as well as Windows, I have tried all I am going to try with this one, so I am not looking for suggestions, however if anyone has a tried and tested set up procedure for a Windows XP Pro box and a Ubuntu guestI would be really grateful to have it. 


Thanks 


fred_scotland

---

### Post by mssever on 2006-09-21
Generally, HP printers work perfectly under Linux (HP provides open source drivers for all but a few of their printers), so I think that your problem is with the virtual machine, not Linux.

I've never used a virtual machine, but what would happen if you tried to set up the printer as a network printer and connect to it in Linux via the network?

---

### Post by Dr. C on 2006-09-21
I have tried it the other way around and it works great. Running Windows XP, NT4 and Vista RC1 in a VM under Ubuntu using VMWare. Printing works great from all of these version of Windows on a printer connected to the Ubuntu host. I have an HP 3015 and I have found that support for HP printers in Ubuntu is very good.  Setting up an HP 3015 printer in Windows XP is very tricky though. 

As far as the guest (Ubuntu) is concerned the printer on the host (Windows XP) is a network printer shared by the host. The first step is to share the printer on the Windows host. Then I suggest research the forums on connecting from Ubuntu to a shared Windows printer.

---

### Post by fred_scotland on 2006-09-22
Thanks for your answers, Yes normally I don't thave any trouble with HP printers, as I say if I connect it directly as a local printer it works fine from Ubuntu. 

If I was just setting up a Linux machine it would be OK, unforunately this is for a particular project where the computer boots Linux directly after Windows. The operator then has both systems available and can move from one to the other seamlessly, only the printing doesn't work. I am sharing the printer alright and can ping the Windows machine from Linux.I think it is definately on the Linux side that the problem lies as printer works from Windows with and without the VMware Workstation running, its only when the Linux boots in that the problem arises. I am going to try a few more things tonight I will get back on here and let you know what happens.



Fred.

---

### Post by ed_d on 2006-10-02
Have you tried using a network attached printer to print? That should really take all the hardware out of the picture, plus would make it easier for other things to use the same printer....

---

