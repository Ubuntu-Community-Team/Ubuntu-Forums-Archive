---
title: "Missing /etc/iftab"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by John The Bad on 2008-05-19
Hi,

I am presently following the article on "Broadcom BCM4311 802.11g mini-PCIe (14E4:4324) Wireless Adapter using ndiswrapper Installation (Plus NetworkManager and WPA)" - see [here]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)#head-ea76065f30b99d3b8472289cd049e2b141856b55").

However, for some reason, I can't continue past Step 2:

[I]Check the contents of the /etc/iftab file and make sure that no other device has the wlan0 driver name reserved for it:

user@ubuntu:~$ cat /etc/iftab

If there are any lines assigning the name wlan0 to a MAC identifier then either remove that line or comment it out with the "#" character. 

[/I]When I try this, I get this error:

*cat: /etc/iftab: No such file or directory*

What does this mean?  I am VERY new to Ubuntu.

---

### Post by jtrindle on 2008-05-19
Don't worry about it.  If you don't have iftab it means you don't have ifrename, which is normal for a recent distribution.  You can skip that step in your directions (though it does imply that the directions may be old).

---

### Post by jtrindle on 2008-05-19
OK, I looked at the doc, and it seems it contains info for a lot of different distributions.  The chart is still being maintained, though, so it might not be too out of date.  You might see some lines which don't apply, but overall it looks good.

(I haven't personally used ndiswrapper, however.)

---

### Post by John The Bad on 2008-05-19
Thanks Jtrindle.  I'm very new to all this.  Do I have to use ndiswrapper?  Is there another way to get my wireless working?  I thought it would simply be the case of getting the driver for the wireless card and installing it.

---

### Post by jtrindle on 2008-05-19
I don't know about "have to" but Broadcom is apparently kind of tricky with Ubuntu.  Since you have a complete set of instructions I'd stick with it unless you have difficulty.

I don't have a Broadcom card myself, so I can't help you in great detail.  If it didn't work with the default Ubuntu kernel drivers I would definitely follow the doc you found.

---

### Post by John The Bad on 2008-05-21
I got it.  My flavour is Hardy Heron and 'iftab' is not part of this release.

The correct guide (and the one that worked for me) is here - [Broadcom Wireless Setup for Hardy (Step by step)]("http://ubuntuforums.org/showthread.php?t=766560").

My wireless is now working like a treat.

---

