---
title: "[SOLVED] Problem with Broadcom 43xx WLAN not working -- not the usual problems, thoug"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by commonplace on 2008-01-12
This is on a Compaq Presario V6305NR with a Broadcom 43xx WLAN built-in. Everything was great in Feisty (7.04) and Gutsy (7.10). Then, I started having problems where upon bootup, my wireless indicator on the front of the laptop wouldn't turn blue (indicating that wireless was on). And when that happened, of course, my wireless wouldn't work in Ubuntu. Usually a reboot would fix it, but as it kept happening, I started having to do more and more reboots, and even complete shutdowns, in order to get the wireless to initialise upon bootup.

I decided to reinstall, and ran into myriad problems for whatever reason. Trying to get my wireless working, I tried Fedora 8, PCLOS, Mint 4, and maybe one or two others. :-)  With several of them, the wireless worked on the live CD, but when I installed it to my hard drive, no go.

I've completely formatted and gone back to Gutsy (7.10). But I'm still having my original problem -- no blue wireless indicator, no wireless. lspci's output doesn't show my Broadcom card at all when this happens. Repeated reboots eventually gives me wireless back.

Wireless works 100% of the time in Vista (which I abhor), so I'm fairly certain this is not a hardware issue.

I just want my wireless working. Any suggestions? It seems to either initialise, or not, during the bootup sequence. I've tried a few kernel boot parametres, e.g. noapic, etc., but none seem to have an effect on the wireless problem.

Anyone?

/Kevin

---

### Post by csat on 2008-01-13
This tutorial [==>HERE<==](http://ubuntuforums.org/showthread.php?t=297092) is indicated to solve problems with such hardware.  Hope this can help you out.

---

### Post by commonplace on 2008-01-13
> **csat said:**
> This tutorial [==>HERE<==](http://ubuntuforums.org/showthread.php?t=297092) is indicated to solve problems with such hardware.  Hope this can help you out.

Okay, thanks! I'm going to check this out later today. I'd checked a tonne of other threads, but not that particular one. I'll give it a go and see what happens. :)  I just wish I knew what the heck happened. I was thrilled with Gutsy out of the box and my wireless was fantastically easy to setup using just the restricted drivers... and then it all blew up!

Thanks again,
Kevin

---

### Post by templa edhel on 2008-01-13
um...thiis may be really stupid but i did it. is there a ¨fn¨ key (blue maybe) on your keyboard? if there is is there a key (maybe f2) with a wireless tower or symbol of some sort? if there is press [COLOR="Blue"]fn[/COLOR] then press the key with the wireless symbol on it (the symbol will be blue too.

hope that helps

---

### Post by csat on 2008-01-13
> **commonplace said:**
> Okay, thanks! I'm going to check this out later today. I'd checked a tonne of other threads, but not that particular one. I'll give it a go and see what happens. :)  I just wish I knew what the heck happened. I was thrilled with Gutsy out of the box and my wireless was fantastically easy to setup using just the restricted drivers... and then it all blew up!

Thanks again,
Kevin

I've seen different sites saying to unload restricted drivers for this purpose.

---

### Post by commonplace on 2008-01-13
> **templa edhel said:**
> um...thiis may be really stupid but i did it. is there a ¨fn¨ key (blue maybe) on your keyboard? if there is is there a key (maybe f2) with a wireless tower or symbol of some sort? if there is press [COLOR="Blue"]fn[/COLOR] then press the key with the wireless symbol on it (the symbol will be blue too.

hope that helps

Mine has a hardware switch in front, and I've made sure it's on. Thanks, though!

---

### Post by commonplace on 2008-01-13
Okay, I tried the tutorial referenced by **csat**, and it worked like the other solutions have worked. It works... until I reboot, and then it doesn't work. Repeated reboots eventually makes it work... until the next reboot. Usually, though, I can reboot 10+ times, shutdown, etc., and it may not work for many hours later.

The hardware just isn't even detected in Gutsy anymore. It's like the hardware isn't present, even though it is (since it's a laptop with built-in wireless, I can't even remove it anyway). Very frustrating. :(

---

### Post by csat on 2008-01-14
I am deeply sorry hear this.  Yesterday I got some issues with my notebook and had to re-install new OS so I decided on Mint 4.0.  This morning I've followed the same tutorial and now I am typing this short message using wireless.  My notebook is Dell 131-L with Broadcom 43xx wifi board.  I have turned off notebook and turned on and everything remains the same so I really don't know what might be wrong with your hardware.  Maybe the guy who wrote the tutorial could help you more.  Anyway it was a good try.

Cheers,

---

### Post by commonplace on 2008-01-25
Oh well, thanks for trying, **csat**. I haven't given up yet, but it's still not working and I'm definitely losing hope.

---

### Post by commonplace on 2008-05-12
Just wanted to follow-up on this (for anyone who stumbles across this in the future). It turned out to be a hardware problem -- the internal wireless NIC was bad. HP Compaq replaced it and it's been fine ever since.

/Kevin

---

