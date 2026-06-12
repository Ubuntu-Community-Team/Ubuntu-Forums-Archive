---
title: "Samba Speed Problems (again)"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by matt91 on 2007-04-15
i am still having problems with samba with ongoing speed problems which are unreliable between ubuntu and windows (XP+vista). sometimes they can be ok with around 10MB/s and sometimes they can be very slow with less than 1MB/s. i think that 10MB/s should be the minimum for my requirements. There have been lots of posts with various speed problems but not many seem to be resolved, here is a previous thread:

[http://ubuntuforums.org/showthread.php?t=342320](http://ubuntuforums.org/showthread.php?t=342320)

how many people are having the same issues as me and is this going to be resolved any time soon? is this problem the same throughout the other linux distributions?

Matt

---

### Post by dmizer on 2007-04-15
the most recent post in the thread you linked suggested that the fix could be done by changing the configuration of the network card in windows.  take a look here: [http://ubuntuforums.org/showpost.php?p=2434695&postcount=23](http://ubuntuforums.org/showpost.php?p=2434695&postcount=23)

this fixed the problem i was having.

could be lots of other things interfering with your samba file transfer speeds, and cause the exact same problem.  firewall issues, domain name issues.  remember ... just because the SYMPTOM is the same (speed problems), does not mean the cause is the same.  could be any of a number of things, including but not limited to:
> router problems
> network configuration in windows
> network configuration in ubuntu
> incorrect share settings in windows
> incorrect mount settings in ubuntu (are you mounting with nautilus? smbfs? cifs?)
> firewall blockage from windows (can you say "norton"?)
> firewall blockage from ubuntu (firestarter)

also ... try to remember that, just because you experience the problem in ubuntu does not mean that ubuntu is causing the problem.

---

### Post by matt91 on 2007-04-16
iv tried changing windows network settings (already auto-negotiation) and iv disabled firewall on windows and ubuntu. i have a spare 10/100 NIC so i will try that later.

---

### Post by matt91 on 2007-04-16
i have tried the network card and also an old switch. i dont know why im bothering with gigabit becouse even 100mb isnt being taken advantage of.

does feisty have an updated version of samba or does anybody know another distro with faultless samba?

i have lots of photos im working on and im having to keep them local on windows becouse the speed and unreliablity keep making windows crash. :( :(

---

### Post by chtse53 on 2007-04-24
My problem was fixed by using the r1000 driver for my NIC (with RLT8169 chipset).  Feisty doesn't have r1000 module in the kernel.  I have download the driver from RealTek and incorporate it into Feisty as well as removing the r8169 driver.  Otherwise, even with r1000 loaded, r8169 will still grab the NIC.  An interesting observation before the fix, I can boost up the speed of transferring files to  the Ubuntu server from WinXP PC by opening a VNC connection window to the Ubuntu server.  The VNC window must not be minimized.  The speed is now about 250-300 Mb/s (i.e. about (35MByte/s) transferring files to the Ubuntu server from an WinXP box.  The other way round has always been about 450 Mb/s (i.e. around 55Mbyte/s) before and after the fix.

---

### Post by teeks99 on 2007-04-27
> **chtse53 said:**
> I have download the driver from RealTek and incorporate it into Feisty as well as removing the r8169 driver.  Otherwise, even with r1000 loaded, r8169 will still grab the NIC. 

I've got this driver from RealTek (I have the same NIC) and installed it.  How do I go about removing the current driver?  
Thanks,
Tom

---

### Post by chtse53 on 2007-04-28
> **teeks99 said:**
> I've got this driver from RealTek (I have the same NIC) and installed it.  How do I go about removing the current driver?  
Thanks,
Tom

I followed the steps mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=143982](http://ubuntuforums.org/showthread.php?t=143982)  Basically, I backup the original driver: /lib/modules/2.6.20-15-generic/kernel/drivers/net/r8169.ko and delete it from that directory. Edit the /etc/modules file by adding a line: r1000 to ensure the r1000 driver is loaded a boot time. Backup the boot image file and remake a new one which does not contain the r8169.ko module. The r1000 will grab your NIC. 
Chris

---

### Post by matt91 on 2007-05-26
is there a step by step guide to installing the correct drivers. my ethernet is Realtek 8110S. there is lots mentioned and i dont know which will work for me. is there a package or what do i download?

Matt

---

### Post by matt91 on 2007-05-28
i used apache to download a file from my server and it was the same slow speed. can anybody help with installing the correct drivers if they are wrong? i am using belkin cat6 cables and a gigabit netgear switch with my network. my pc's can send files to each other at full speed so it isnt the other pc's.

I have been trying to sort this for a long time now. Would it be better buying a PCI gigabit card which has better compatability, if so which one?

Matthew

---

