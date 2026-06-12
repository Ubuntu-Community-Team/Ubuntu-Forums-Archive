---
title: "hp dv1411se broadcom 4318!!! HELP"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by gdg2k5 on 2007-07-14
ok so i went through ndiswrapper, i got the proper driver... all that ****.... when i goto settings>admin>network the wlan doesnt show up!!! help:confused::confused::confused::confused::confused::confused::confused::confused:

there is a button on my laptop that enables/disables the card and it is stuck on disabled... could this be a problem?

---

### Post by johnnydough69 on 2007-07-14
Hi gdg2K5,

If you really want to use the ndiswrapper I can't help you much. The approach I found that worked well for my broadcom 4318 in Fiesty was:

see this thread and use it wih the below caveats
[http://ubuntuforums.org/showthread.php?t=391961]("http://ubuntuforums.org/showthread.php?t=391961")

1. Got the firmware file (BCMWL5.SYS) from my windows xp install which in my case was c:/windows/system32/drivers/BCMWL5.SYS  (alternately you can rip them from the drivers on your HP install disk or whatever source you have. Put the file in /etc/lib/firmware  I had trouble using drivers from other sources on my broadcom 4318.  Actual cause may have been my ignorance, but it's what worked for me

2. Install using synaptic (or what you will) the "bcm43xx-fwcutter" package. Following it's instructions, use it to install the microcode into the /etc/lib/firmware directory. (you will see a bunch of new files)

3. In my Fiesty install "network-manager" and "network-manager-gnome" were part of the default install.

4. My broadcom 4318 showed up as "eth1", I didn't need to change it's name.

5. when you are ready for wpa use this site:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html")
Absolutely the best way to go. You will note the duplication of the /etc/network/interfaces editing.  I believe this allows the "network-manager" to do its job.

For my install I was looking for a way to keep extra layers minimized.  Intuitively, I felt I would be better off without the ndiswrapper to achieve that end.  Again, this perspective may be due to my ignorance associated with linux.

Good Luck

James

---

