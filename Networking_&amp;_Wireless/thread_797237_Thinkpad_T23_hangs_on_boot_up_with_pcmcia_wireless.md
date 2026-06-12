---
title: "Thinkpad T23 hangs on boot up with pcmcia wireless card"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by michaeljking on 2008-05-17
If I twitch my Thinkpad T23 on with the pcmcia wireless card in it boots to a point then hangs.  If I pull out the card before it then boots up with no problems.  Once the gnome login screen comes up I push the card back in and it connects to my wireless as usual.

This happens not only with Ubuntu 8.04 but the new Kubuntu,  and Crunchbang Linux
(openbox)


I am hoping there is a simple solution,  I have tried 2 other wireless card but they have had the same problem.

any idea?


Thanks!!!

---

### Post by michaeljking on 2008-05-18
any ideas anyone?  I have had to install PCLINUXOS 2007 instead of Ubuntu on two Thinkpads because of this problem(thinkpad T22 and T21)   I was hoping it was something simple unlike the Dodgy Kernal in the last release

---

### Post by chili555 on 2008-05-18
What chipset is the wireless card?

I would interrupt the boot process with the Esc key to get into the GRUB menu, edit the line like that should look like this:```
/boot/vmlinuz-2.6.24-16-generic root=UUID=4b70eff7-c255-4e38-9af6-1a9d9af90fe3 ro quiet splash
```Edit the line to remove the words 'quiet' and 'splash.' Then press Enter and 'b' to boot the amended line. You will see lines of text flash by until it hangs. Make a note of the last four or five lines and let's see if we can troubleshoot it.

I had a similar issue with my T40 which hung with every distribution I tried that used the 2.6.24 kernel. Unfortunatly, the wireless card is built-in and could not be yanked prior to start-up.

---

