---
title: "Please help. 100% (before upgrade) to frustration afterwardsRealtek 8185(Ndiswrapper)"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by PreviousN on 2007-10-21
Hi guys/gals,

I just upgraded from feisty to gutsy and have a problem. In feisty I was using NDISwrapper to use my wireless card on my laptop (Realtek 8185). Everything worked EXCELLENT. I could connect to encrypted networks and even see signal strength (gasp :-/). 

After upgrading to gutsy I cannot connect to encrypted networks (it never prompts me for my key) or see signal strength. The drop down gnome applet shows networks, but signal strength for all is 0%. This is of course not the case because I'm sitting right by the router. 

Anyways, so it allows me to connect to a network without encryption (and with an apparent 0% wireless signal) to send this message. That woudln't be too bad, but I travel and need to know which networks are the strongest (and connect to mine at home that has encryption).

Please help!

---

### Post by kevdog on 2007-10-21
Do a few things on the command line to see if Network Manager is telling you the truth

iwlist scan

This should show you the networks around you and the relative signal strengths

If strengths are above zero, then try establishing a link manually on the command line.  There is a link in my signature to help you.

Just try to determine right now if your driver and everything works after the upgrade.  Then if it is a problem with Network Manager then you can deal with this later.

---

### Post by PreviousN on 2007-10-21
Hey, thanks a bunch. Didn't see the reply. Ok...So on command line, strength says "0%". 

But..I can connect to it and browse the net/post this using the gnome applet to connect. 

Basically it thinks everything is 0% (even in Bash) even though its' not. Hopefully that makes sense.

---

### Post by PreviousN on 2007-10-23
I fixed it. I did this:

"lsmod | grep 8180"
"modprobe -r *name of module from above*
It was loading the wrong module for my card...

---

### Post by KenMac on 2008-02-14
Hi PreviousN,
I am experiencing similar problems with my RT8185 after an upgrade to Gutsy. 
When I type:

lsmod | grep 8180

I see:
r8180                  89868  0 
ieee80211_rtl          80648  1 r8180

Is it the r8180 module that I should remove with modprobe?
Thanks,
Ken

---

### Post by KenMac on 2008-02-23
Hi again,
I am really hesitant to modprobe -r anything until someone that knows a lot more about it than me tells me its OK!  Can someone help me out?
Thanks very much.

---

### Post by KenMac on 2008-03-05
*BUMP*
Hi all.  Could anyone give me a hand getting my Realtek 8185 wireless card working again after an update to Gutsy seemed to mess-up NDISwrapper?
Thanks,
Ken

---

### Post by KenMac on 2008-03-11
I tried modprobe -r but received the following error:

```
ken@Max:~$ modprobe -rv r8180
rmmod /lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl8180/r8180.ko
FATAL: Error removing r8180 (/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl8180/r8180.ko): Operation not permitted

```

does modprobe have to be run with sudo?
Thanks.

---

### Post by Anacranom on 2008-03-16
Could someone please help me with same/similar problem with rt8185 card, I have never made it work, I just yesterday put in a new hard drive (removed others) and fresh installed WinXPP and all drivers, partitioned the hdd and installed 7.10 amd64. Installed envy, cedega, and COH, but still cant get the wireless rt8185 card working. This is a problem because we've moved into my in'law's home and not practical to string cat5 all over the place. The card works fine in winXP, since i've started fresh i was hoping someone could help me Start Fresh with this, before I muck it all up, Thank you for any help.
i think i did something stupid, now it doesn't show up in ifconfig (i think i removed the drivers) oh well, please help.

---

