---
title: "ndiswrapper: initialization failed ??"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by standingstill on 2007-02-27
God Please...someone help me!!!!

i've been trying to get my linksys card working on my laptop since i installed ubuntu. i downloaded ndisgtk and ndiswrapper...installed both. used ndisgtk to load the driver. but when i run 'ndiswrapper -l' ...it says the driver is invalid. and even worse...when i run 'dmesg'...it tells me that the ndiswrapper failed to initialize. 

here's part of what it tells me when i run 'dmesg' ...can someone help me? i'll be in your debt forever!

[17179599.616000] EXT3 FS on hda1, internal journal
[17179601.160000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179601.192000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179601.192000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179601.232000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179601.232000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179601.232000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179601.260000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179601.264000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179601.264000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179601.288000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179601.292000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179601.292000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed

---

### Post by Metaljaz on 2007-02-27
ok what is the chipset of your wireless card so that we can see if you have the right driver installed.
Assuming its a pci card run the below command from your terminal window and look for network controller. Output should look something like this:  

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN 

lspci

---

### Post by jasonbrisbane on 2007-02-27
Hi,

You definitely have th wrong driver loading in NDISWRAPPER.

I had two different INF files on my CD and was getting all sorts of errors and sporadic problems... until I tried the other driver and "BEHOLD!" everything worked perfectly!

:guitar: 

Regards,
Jason Brisbane
Ubuntu Newbie

---

### Post by standingstill on 2007-02-27
ok...i'll look for another driver. but i'm taking this directly off the cd that came with the card. and its only showing one 'inf' file. there are some 'autorun' dll files, but only one 'inf' file. 

whatcha think?

---

### Post by standingstill on 2007-02-27
how do i figure out which chipset is in my card? i see several numbers on the back of it: the MAC #, the serial #, IC #, FCC ID #, the model #..... do any of these tell me which chip set i have?

---

### Post by standingstill on 2007-02-27
actually, there is an "autorun.inf" file...but i wouldn't think that would be the one. is that a wrong assumption?

---

### Post by jasonbrisbane on 2007-02-28
Hi,

On my CD there were about 12 directories. I was looking in the Network directory and not having any luck gettign anything working....



Then I found the Directory WLAN and there were two inf files.

bcmwl5.inf and bcmwl5a.inf

The latter worked for me while the first only "seemed" to work.....

---

### Post by Metaljaz on 2007-02-28
ok...so you are up and running?

---

### Post by standingstill on 2007-03-01
that's exactly the chipset i have! but here's the first thing that's confusing me. 

one: i'm pretty sure, about 99% positive that this computer has a built-in wireless card. but it doesn't seem to work. i don't remember it working that well on this computer when it was a windows box. but my device manager tells me its there.  AND then when i pop in the linksys card in, it shows the same chipset TWICE. so it appears that whatever is IN the laptop and what i'm putting into the side of it...have the same chipset. is this just an error of the computer not recoginzing a bum wireless card and copying the same info on to the pci card? OR is it entirely possible they are infact the same ? 

ok, TWO: i don't have any other .inf files except one that says "autorun.inf" ...but that one just looks like it launches another .exe file. HOWEVER, i do see a "BCMwl5.SYS" file. that's not the same thing, right?

---

