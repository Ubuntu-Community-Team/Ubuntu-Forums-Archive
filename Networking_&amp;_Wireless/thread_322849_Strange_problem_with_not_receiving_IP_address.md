---
title: "Strange problem with not receiving IP address"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by fatal_boot on 2006-12-21
Hey guys,

I have a Compaq Presario V2000 series notebook.  I have tried to install Ubuntu, and in the installation it finds both my onboard Gigabit network card AND a Minitar Wireless cardbus, however once it goes off to try and get an IP via DHCP (I have an IPCop box as my DHCP server for the moment) it says it cant get one.

Now the strange thing is I have tried Suse10,10.1,10.2; Ubuntu (latest, downloaded 2 days ago..); Mandriva 2006; FedoraCore 6; and they all DETECT the two devices, however cant get an IP.

I have played around in Suse the longest on the laptop, and even with the wireless it can find my wireless network with full strength and everything, however when I tell it to connect it gets to "Configuring IP" (or something) and just closes and doesnt give me an IP.  This happens on both devices.  If I assign a static IP, it still doesnt work.

The problem isnt with the cable or DHCP server (guessing) as I am at the moment dualbooting with Windows XP Home and both wireless and cable work.  I just want to get rid of this damn Windows on the notebook.

(I do release this is an Ubuntu forum, but I thought the other distro info might be of some use).

Cheers all!

*Edit

Oh, by the way, my IP range has more then enough IPs left. :)

---

### Post by Elisei on 2006-12-21
try to boot ubuntu with additional parameter: when grub starts press Esc then sellect kernel from the list (if you have more than one) and press 'e', at the end of the boot string that shows up type in 'acpi=off' with space in front, then press enter and 'b' to boot using it; once booted try to get an ip again for example using : sudo dhclient; it should give you one;

---

