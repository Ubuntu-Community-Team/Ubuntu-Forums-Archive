---
title: "Wireless timeout problems"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by petehall on 2007-01-11
I am having a problem with wireless in Edgy Eft. Sometimes, when I leave the computer for a while, when I come back I'll see that the icon in the system tray is showing that I am still connected to the network but I won't be able to see anything on the network. Trying to connect to a website will cause it to freeze on "Looking up foo.com..." for a while, and pinging my router will give me "Destination host unreachable." Here's an extract from syslog leading up to this (see part1.txt)

I came back to the computer a few minutes after 19:22. When I realised that it was broken, I tried reconnecting to my network by left clicking on the icon in the system tray and reselecting my network (see part2.txt)

I've tried disabling then reenabling networking, and I've tried logging out and back in again. Ultimately, the only thing that can fix this is to restart the computer.

At the very least, I'd like to be able to avoid having to restart my computer each time this thing goes belly up.

Thanks,

Pete

---

### Post by chili555 on 2007-01-11
First, this may or may not have anything to do with the problem, but I noticed this:

> kernel: [17183647.084000] irq 193: nobody cared (try booting with the "irqpoll" option)

I would suggest adding irqpoll to your boot options as you boot up. You will have the option to edit the options. Edit the line that reads someting like this:

> /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash to add the word irqpoll and see if it helps...or not.

Next, I see this: > Roamed from BSSID 00:18:39:1E:B2:88 to 00:0F:B5:29:5D:88 on wireless network 'dinnerNet'  and so it looks like your card is trying to jump from one nextwork to another. The other may not be WPA encrytped and certainly not with the key you use. You can fix the ESSID you want in System -> Administration -> Networking. Highlight the wireless interface and click Properties. You can set the ESSID you want to connect to.

You can restart your network without rebooting your machine by doing sudo /etc/init.d/networking restart

Good luck and have fun!

---

### Post by petehall on 2007-01-12
> **chili555 said:**
> I would suggest adding irqpoll to your boot options as you boot up. You will have the option to edit the options. Edit the line that reads someting like this:

 to add the word irqpoll and see if it helps...or not.

I'm booting with irqpoll now. If the problem comes back, I'll post here.

UPDATE: The problem didn't come back, but I did get a new one - the keyboard would stop working after a while, forcing me to restart the computer. I'm not booting with irqpoll any more.

> **chili555 said:**
> Next, I see this:  and so it looks like your card is trying to jump from one nextwork to another. The other may not be WPA encrytped and certainly not with the key you use. You can fix the ESSID you want in System -> Administration -> Networking. Highlight the wireless interface and click Properties. You can set the ESSID you want to connect to.

When I tried to open Networking, I got an error message: "The configuration could not be loaded - You are not allowed to access the system configuration". I can still get into Synaptic, so clearly I haven't accidentally removed my account from the list of sudoers. I get the same error when I try to access "Time and Date" in the same menu.

UPDATE: This seems to be working now. My wireless card isn't configured through Networking - if I enter an ESSID in there, will it break everything?

> **chili555 said:**
> You can restart your network without rebooting your machine by doing sudo /etc/init.d/networking restart

I believe that I've tried this before, and it hasn't worked. I'll try it again next time my problem crops up.

Thanks very much for all your help.

Pete

---

