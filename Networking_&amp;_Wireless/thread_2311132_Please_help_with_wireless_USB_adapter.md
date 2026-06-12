---
title: "Please help with wireless USB adapter"
date: 2016-01-24
forum: Networking &amp; Wireless
---

### Post by alex496 on 2016-01-24
I have a wireless USB adapter that I've been using with a Windows computer and now would like to use with Ubuntu. I looked through a few threads and was able to install the driver using ndiswrapper.
Im at the point where the wireless network shows up in the network tab but it just keeps saying "connecting" and the passkey popup window keeps opening up but never connects.
I would greatly appreciate some help with this as Im a new Ubuntu user but quite persistent to get this to work. Thanks.

**Output code "lsusb"**
   Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 001 Device 002: ID 13b1:003a Linksys AE2500 802.11abgn Wireless Adapter [Broadcom BCM43236]

 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**Output code "ndiswrapper -l"**
   

cmwlhigh5 : driver installed
 	device (13B1:003A) present

---

### Post by sandyd on 2016-01-24
Moved to Networking & Wireless

---

### Post by Dreamer Fithp Apprentice on 2016-01-27
> **alex496 said:**
> the passkey popup window keeps opening upDid you enter a password?

---

### Post by alex496 on 2016-01-28
Yes, password entered. As the window keeps popping up it has the password autosaved. The wireless network Im trying to connect to is recognized in the network window at the top right corner. Not sure whats preventing the connection. Any thoughts?

---

### Post by Dreamer Fithp Apprentice on 2016-01-28
A few, none I'm afraid, are dazzling strokes of genius:

1-If the password is obscured, open a text editor, enter the password so you can see it. Copy it. Paste it on the next line. Make sure you didn't get the line feed also. Easiest way is to paste it twice. It should appear twice on the same line with nothing in between. Now delete whatever it has saved and paste that in, being careful to do it just once. I know that sounds real OCDish but it is easy to misenter an obscured password and with it saving it you only have to make the mistake once.

2-Could be a weak signal. To test move right up next to the router. If it still doesn't work, that isn't the problem. If it IS the problem, we can consider what to do about it.

3-Use a search engine (I like startpage.com) and search on the model name and number of your device along with "linux OR ubuntu". It is surprising how often answers are found at the Arch forum.

4-Hope somebody smarter than me wanders into your thread. At least I bumped it for you.

Good luck.

---

### Post by alex496 on 2016-01-28
Thanks for your help. I tried what you suggested but having the same issue. I read some other threads and think the problem might be blacklisting the old drivers. I dont know how to check if that is the issue. Anyone else have ideas? Appreciate it.

---

### Post by Dreamer Fithp Apprentice on 2016-01-28
No guarantee, and a bit more work, but if you don't come up with an easier approach soon, another idea:

BACKGROUND & BASIS:
I have 3 systems on a external USB that work fine with the machine it was attached to when they were installed, but despite determined tinkering, and a lot of advice, can't reach the internet when I boot a different machine from them. They work fine in all other respects - they just can't reach the internet.

But in other partitions of the same drive, I have installed the same distro (Trusty) with the hardware in place at the time of installation and it works fine. Evidently, there is some magic in the live disk I haven't figured out yet.

It seems to me your situation is in many ways similar.

=========================================

So:

In all cases, I'm assuming your data is backed up, preferably on removable media that has been removed.

1-
Back up your system. I like fsarchiver for the purpose but I keep things simple by putting my data on a separate partition rather than in ~/. You can do this while booted from another system, either on another partition or a live disk/stick.

You can follow the general approach I'm outlining here if you keep your data in ~/ but it gets a little hairier and you'll have to adjust the details. The general idea is to back up your system and data separately, so that restoring the system becomes a trivial exercise, and be careful in step 2 not to overwrite your data. But you DO want to replace all your old config files and so on in ~/. You CAN do this, but it is a bloody complex nightmare with lots of oops-traps if you keep your data there as well. If it were me if you don't have a data partition, I'd make one and move the data first. It makes a lot of things, especially backups, simpler. 

2-
Reinstall with a normal live disk/stick installer, with the device in place.

3-
Test it.

4-
If it works, backup the pristine ~/ and copy over any config files you've tweaked. If everything still works fine, you're shiny. If not, restore the backed up pristine ~/ and copy your old configs over a few at time, etc. to isolate the problem.

Or, alternately, just re-tweak by hand. This might be easier if you haven't done much tweaking.

5-
In the event the above doesn't work you're no worse off, and you can always restore your backed up system if you want to.

---

### Post by alex496 on 2016-01-31
Cool, thanks [**[COLOR=#000000]Dreamer Fithp Apprentice[/COLOR]**]("http://ubuntuforums.org/member.php?u=1435975").
I tried the reinstall that you recommended but the device still does not work. I thought maybe I should try installing Ubuntu 14.04 instead of 15.10 which is what I have now. Any ideas if this may help. I dont think there is much difference in the versions and again I wouldnt be any worse off since Im still on a fresh install.

---

