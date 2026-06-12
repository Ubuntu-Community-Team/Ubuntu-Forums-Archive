---
title: "Linux not registering NICs"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by spiwaterwing on 2007-03-16
I've been trying for some time to get my Ubuntu 6.10 box, an HP Pavilion a250n, working with a Sony Clie.  As I was syncing, I attempted to cancel the HotSync operation through the Clie, which stopped- but, for some reason, locked up my computer.  I held the power button until the computer powered down, and turned it on again shortly after.

However, when I booted up, I received an error that I'm still getting each time on boot:
"PCI: device 000:02:0b.0 has unknown header type 4e, ignoring"
I can find it in the /var/log/kern.log right after boot.  (Booted using the latest kernel available through automatic updates in recovery mode)
It no longer registers my internal network interface (on the mobo)- it appears in the Device Manager as an unknown PCI device.

This error occurs right after the OS begins booting (after selection in GRUB).  It occurs not only in Ubuntu 6.10, but also using a 6.06 live CD and a D*** Small Linux live CD.  Also, my installation of Edgy does not register another NIC that I plugged into a PCI slot, instead giving a similar error, but I haven't tested with that NIC extensively.


I've only been using Linux for a few months, and this is the first major problem I've had.  (Well, the first that's been severly debilitating!)  Thanks very much for any help you can give!

---

### Post by garlicsalt2 on 2007-03-17
Just a hunch, but check for damage to the file structure on the Hard Drive. Go to a command line by pressing ctrl+alt+f1. Type your username and password. Then type "sudo shutdown -rF now". This will reboot your computer and force a disk check.

It's odd though, this should not be happening in other OSs, unless there is damage to the motherboard. Don't fret yet, however. Try booting from Knoppix, and see if it still has this same problem. If so, check the computer's BIOS to make certain that everything looks okay (unless this is something you've never done before - in that case, don't mess with it!!).

In any event, try doing a "lspci" from Knoppix, your native Ubuntu install and from the Ubuntu Boot CD and compare the results. (lspci is a command line tool, so you won't find it in the Gnome or KDE Menus). If still no luck, you can try posting the results of lspci to this forum topic, and maybe someone will be able help you.

---

### Post by spiwaterwing on 2007-03-24
No go.  That shutdown command just did a reboot, but fsck yielded nothing unusual afer reboot.  I d/led, burned, and booted from Knoppix 5.1.1 today, but it didn't register a network card either.

The BIOS (which I have messed with before :) has the "Onboard LAN: [Enabled]" and "Onboard LAN Boot ROM: [Enabled]".  I'm not sure what the Boot ROM is for; I've tried with it enabled and disabled, but neither works.

The Dapper live CD gives a slightly different lscpi result, but it's just formatting ("0000" instead of "00", for instance).  Knoppix and my native install of Edgy are the same, and attached below.  Any help, again, is much appreciated!

---

### Post by garlicsalt2 on 2007-03-25
Hmm, I don't see your Network adapter listed. Do you mind if I ask what brand and model of adapter you are using?

Also, please post the results of the "lsmod" command and "ifconfig -a". You can also try doing a lshw (this won't work in Knoppix, the program isn't included). If you could, please, just paste the results of these commands into your response. Use a terminal or console program to run the commands, and then copy 'n' paste the output.

Oh, yeah. FYI: The "Boot ROM" option is for booting over the network. You need a special server setup on another computer in order to do this, however. The Knoppix DVD edition has such a server, for example. Don't worry about this right now, though.

Normally, I wouldn't encourage running Windows on a Linux forum (heck, I wouldn't encourage running Windows period), but in this case, it can be useful if only to rule out Linux specific problem. I don't think that that is likely, however. Anyway, I'm off on a tangent again. If you have access to a Computer running Windows and have a Windows XP Install CD, you can try to make "The Ultimate Boot CD for Windows" [http://www.ubcd4win.com/]("http://www.ubcd4win.com/")

Otherwise, I don't know what to tell you. Maybe try a USB Ethernet adapter?

---

