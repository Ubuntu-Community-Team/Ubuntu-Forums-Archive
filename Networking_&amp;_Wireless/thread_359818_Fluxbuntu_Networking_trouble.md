---
title: "Fluxbuntu Networking trouble"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by Beastmouth on 2007-02-12
I'm using Fluxbuntu, but I know how helpful y'all are here so I figured I mise well ask.  
I'm having copious hardware trouble with a Compaq TC1000 and a BenQ external optical drive. 
First, my onboard HD completely quit being recognized.  Then, when I tried re-installing Fluxbuntu, it'd hang up when it got to 'Linux kernel booting...'. 
Finally, I got it to load, log in onto the liveCD, then install to my external HD.  After minor trouble, I got it booting on this drive.  However, the internet connection doesn't work, so I've rebooted to my CD drive to find any help. 
I appreciate any help.  Thanks, A. M.

---

### Post by Paerez on 2007-02-12
can you print the output of "lspci" so we can see what card you have?

---

### Post by Beastmouth on 2007-02-12
> **Paerez said:**
> can you print the output of "lspci" so we can see what card you have?
(Why can't I copy in Fluxbox?  :-(  Computers are so depressing sometimes.)

Uh, okay, LSPCI gives network as
```
0000:00:08.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller

0000:00:0a.0 Ethernet controller: Atmel Corporation at76c506 802.11b Wireless Network Adaptor
```


Atm, I can't boot into my USB HD, not sure why, but I'm not sure why I ever could.  It's awful; I finally had a distro installed that my machine got along with (the WiFi even works out of the box!) but then it had to go and die, seemingly because windows had to hibernate and then skipped GRUB or something and my internal HD isn't recognized any more and, oh, the horror, the horror.  

Anyway, the light on the machine for the Wifi adaptor is blinking, but I'm nowhere near wifi access.  The lights on the ethernet plug were on (the orange for a cable inserted, the green for connection up), but no internet applications work.  Firefox has a problem loading every page, sudo apt-get update just tells me to go, well, you know.  I'd give more details, but I have no idea how I ever was able to boot into the installed one in the first place.  

Tomorrow, I'll see if I can intall the USB drive into the internal HD slot, see if that is recognized.  Otherwise, what?  Please help!

---

### Post by Paerez on 2007-02-12
so you have an ethernet and a wireless... and they both don't work?

Can I see the output of "iwconfig" and "ifconfig"?

EDIT: try selecting text and then middle clicking (the scroll wheel) or clicking with both buttons at the same time. This will copy/paste in flux.

---

