---
title: "Can't get network to work with Asus A8V-E motherboard"
date: 2005-08-28
forum: Networking &amp; Wireless
---

### Post by Antithesis on 2005-08-28
Hey there,

I recently installed the 64bit hoary on my machine, asus a8v-e, which uses a marvell chipset for ethernet.
After having alot of "fun" with a freeze on every login (fixed courtesy of changing X11 to vesa from ati radeon drive), I'm now able to login, but can't seem to get my networking to get detected. At this point, neither wired nor wireless networking is working, but I'm willing to settle for getting wired working first, then focus on the wireless to work.

I've tried "modprobe sk98lin" with any type of flag I could think of that could help, but this doesn't seem to help - even after restart, I'm not showing any network adapters (lsmod shows nothing is using sk98lin, but it is loaded, as far as I can tell).
I am knowledgble user, but realtive newbie in ubuntu/linux, so maybe I'm missing something obvious.

Also tried installing the Asus original driver, but the installer is asking me for all these things I dont have (e.g., linux srouce code, and a whole bunch of librariers), but since I don't have networking, its kinda annoying, and I'm not even sure if this will really help.

There is no problem hardware wise - I know for a fact that network adapter is working and its set as on in the bios, etc. I also know some others have had problems with this board, but I can't see any solution that I can understand (the ones I've tried go along the lines of what I've written above, and haven't worked)

Any help, advice or tips for troubleshooting would be appreciated.

Thanks in advance,
Antithesis

---

### Post by pmjdebruijn on 2005-08-28
Hi,

Well first post a 'lspci' (execute this in the terminal) in here, so we can be sure it's Marvall chip.

Also please use this [http://www.syskonnect.com/syskonnect/support/driver/d0102_driver.html](http://www.syskonnect.com/syskonnect/support/driver/d0102_driver.html)  site for the most up to date driver for the Marvall chips, as they are based on the original SysKonnect design. ASUS generally lags behind pretty terribly regarding driver versions.

Also to compile the more up to date sk98lin driver, you should be able to do fine with only the linux-kernel-headers, though I'm not entirely sure about this.

Anyway, if the headers aren't suffient, use synaptic to download 'linux-source-2.6.10'.

Regards,
Pascal de Bruijn

---

### Post by Antithesis on 2005-08-28
Thx for the help pmjdebruijn.

I've tried what you suggested, but there is one detail that is slowing everything down - since my internet is obviously not working on my ubuntu install, I have to do stuff there and then use the internet on another computer.

From lspci, the last line and the only one that relates to networking that I can see is:
0000.05:00.0 Ethernet Controller: Marvell Technology group Ltd: Unknown Device 4362 (rev 15)

If you think more lines would help, I'll do it again and copy the output to a floppy, but from briefing through it, most other things are unrelated (a few AMD Stuff), ATI stuff or unknown devices, so I'm not sure what other information can be salvadged from there.

I also downloaded the new driver from the website you recommended. It is a much newer version, but it also requires the linux headers. Again, since I don't have, I can't use synaptic to download it easily, but if you think that will work better than the complied driver that came on the hoary cd, I'm willing to give it a try. Do you know a web link where I can download them from?

Thanks again for your help!

---

### Post by Antithesis on 2005-08-28
Thanks for your help....

I figured out my stupidity (The linux headers were on the ubuntu CD), got those, made a symbolic link, and ran the driver install script.
After a restart, the network adapter is showing, and I could easily configure it.

Cheers

---

### Post by pmjdebruijn on 2005-08-28
Hi,

You might want to report this in the ubuntu bugzilla that your chip doesn't work out of the box.

The sk98lin driver in the normal kernel is quite outdated.

Regards,
Pascal de Bruijn

---

