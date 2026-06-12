---
title: "Slow WiFi with Broadcom 14e4:4315 (rev 01) in 14.04"
date: 2016-01-28
forum: Networking &amp; Wireless
---

### Post by raequin on 2016-01-28
Note: some lingo might be misused in this post.  I've been working to improve WiFi performance on an Acer laptop that has Broadcom hardware.  It seems to need the b43 driver.  (The PC used firmware-b43-installer.)  Is the following output for ```
lsmod | grep b43
``` normal or should bcma etc. not be there?  Like, do I need to blacklist anything?  I can connect okay and sometimes WiFi is good but it often gets to where download speeds are minuscule.

```
Module	Size          Used	by
b43		396480	0
bcma		52320	1	b43
mac80211	652777	1	b43
cfg80211	498458	2	b43,mac80211
ssb		62352	1	b43
```

---

### Post by Hadaka on 2016-01-28
Hi, please go here...
[http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)
and then post the wireless-info.txt the script puts in your home directory,
your b43 looks correct... here is mine for comparison.
```
hadaka:~$ lsmod | grep b43
b43                   342801  0 
mac80211              436544  1 b43
cfg80211              178877  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43

```

---

### Post by raequin on 2016-01-31
Thanks, Hadaka.  Here is the script's output.

---

### Post by Hadaka on 2016-01-31
Hi, from a working wired connection open a terminal ctrl/alt/t
then copy and paste.
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
boot
your wireless connection is currently using CH#6 freq.2.447 with 11 other users.
access your router configuration and try CH#11 freq.2.462 with just 2 current users.
Once that is done,, then again from a working wired connection,please do
```
sudo apt-get remove --purge firmware-b43-installer
sudo apt-get install firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
sudo apt-get update
sudo apt-get dist-upgrade #This does NOT upgrade the os
sudo apt-get autoremove
sudo apt-get autoclean
```
Then edit your connection  and configure IPv4 and Iv6 like the attached
[ATTACH=CONFIG]267054[/ATTACH][ATTACH=CONFIG]267055[/ATTACH]
Then remove the wired connection,boot and test wireless

---

### Post by raequin on 2016-02-05
> access your router configuration and try CH#11 freq.2.462

I can get to the router settings but don't know how to change frequencies or even see a list of frequencies.  It seems like I'll need to be on WiFi to perform this step.  Is that correct?

---

### Post by Hadaka on 2016-02-05
Hi, the channel you select in your router settings.
I suggested CH#11 freq.2.462 ..that is Channel 11 
and channel 11 is 2.462. so dont worry about the freq.
just set it to CHANNEL 11....and no you do not have to
have an active wifi to do that...its how you get an active
wifi.
thanks.

---

### Post by raequin on 2016-02-05
> Hi, the channel you select in your router settings.

Are you instructing me to set the router to only use Channel 11 (this is, I think, the only thing I can find about channels on the router settings page) or are you saying I need to get my computer on Channel 11 of the router?  This surely reveals my ignorance about networking but it's fun to learn something new.  I guess if the instruction is to set the router to only use Channel 11 then that means some of the 11 others on Channel 6 are my neighbors?  In other words, there are eleven other devices in the vicinity using 2.447 MHz radio, not all of which are communicating with my router?

---

### Post by Hadaka on 2016-02-05
Hi, yes..in the router is where you change and set the channel.
if a frequency ..channel,becomes crowded then there can be interference
on that frequency,picture the clown car at the circus with 30 clowns crammed
in, not good. and no..no one else should be on your router unless you have given
them permission,that doesnt mean that a crowded frequency cant cause interference
with your router, hence my suggestion to move to a different less crowded frequency
channel.Take the time to read your wireless-info.txt file,the information including the
frequencies is there. In time you will figure all this out.

---

