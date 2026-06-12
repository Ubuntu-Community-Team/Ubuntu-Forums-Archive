---
title: "VMware WS eth0 won't come up"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by brargh on 2005-11-22
Hi all,

After a couple of (disappointing) trials to get a server running on freeBSD, I got Ubuntu server CD and Kubuntu DVD downloaded to make a fresh new start...

Learning curve made me try it in VMware Workstation 5.00 (b.13124) with XP as host OS.
Unfortunately it will not bring up the eth0 interface, not in the server install (took me some time to figure out what was going wrong though ;) - it comes up but only gets a IP6 address despite entering IP4 details during installer) nor in the live Kubuntu DVD - there it comes up and immediately dies on me :???: 

Anybody with similar experiences? or - even better - possible solutions?

if any more info needed, I'll reinstall (only takes 30 minutes or so -- GOOD WORK for the Ubuntu team!!! :D )

---

### Post by mlomker on 2005-11-23
I've never had a problem running Ubuntu under VMware...it uses an emulated AMD network card that is recognized out of the box.  After you install the VMWare tools you get a little better performance using their driver, but the Ubuntu driver works.

Are you using DHCP and not getting an address or what?  I should clarify by saying that I only run VMWare in bridged networking mode.  I'm not sure how you're doing it.

---

### Post by amccollough on 2005-11-23
I am installing ubuntu for the first time ever as a VMWare instance, and just went through this problem.

The solution in my case is that the file **/etc/network/interfaces** needed to be modified. Edit **/etc/network/interfaces** and add in **auto eth0** above the stuff for eth0. After a reboot, eth0 should come up automatically.

Mind you, when I go to reboot, it just sits there and I have to manually restart the vm, but that's a topic for another post!

---

### Post by brargh on 2005-11-25
[QUOTE=mlomker]I've never had a problem running Ubuntu under VMware...it uses an emulated AMD network card that is recognized out of the box.  After you install the VMWare tools you get a little better performance using their driver, but the Ubuntu driver works.

Are you using DHCP and not getting an address or what?  I should clarify by saying that I only run VMWare in bridged networking mode.  I'm not sure how you're doing it.[/QUOTE]

Bridged networking as well, it is really weird...tried both server CD install 5.10 and live DVD - both with the same result...

---

### Post by mlomker on 2005-11-25
[QUOTE=brargh]Bridged networking as well, it is really weird...tried both server CD install 5.10 and live DVD - both with the same result...[/QUOTE]

What is the contents of /etc/network/interfaces?

Have you seen my [sticky]("http://www.ubuntuforums.org/showthread.php?t=87643") for troubleshooting?

---

### Post by brargh on 2005-11-25
[QUOTE=mlomker]What is the contents of /etc/network/interfaces? Have you seen my [sticky]("http://www.ubuntuforums.org/showthread.php?t=87643") for troubleshooting?[/QUOTE] Took out an old Pentium Pro 64MB SCSI box w/3COM....works like a charm with the same settings (though I have to admit the earlier "eth0 auto" came in handy ;) ) I'll just go from here on, this actually 'feels' faster than VMware :) Thanks!!!!!!
Odd enough, did a full install within the same virtual machine, and all works like a charm (fast too, even within a VM on a Pentium M)

---

