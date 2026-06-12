---
title: "Firefox 3.5 RC2 Died"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by susanpenter on 2009-06-25
Alongside this older version of Firefox I also had FF 3.5 RC2 installed branded Shiretoko and yet it seems to have died.

It was suggested that I could override the extension manager to install an extension GTDinbox 3.0a8 which I did. When I rebooted Shiretoko though I just got a weird error box in the middle of the screen - it seemed to be searching through my Diigo bookmarks.  Out of desperation I went to the package manager and uninstalled Firefox 3.5 and then re-installed it.

I now have an icon for Shiretoko in my Internet menu which brings up the loading tab in the bottom tab briefly and then totally vanishes.

Although I have use of this FF 3.0.11 I would really like to get back to all the benefits of FF 3.5 so I would be grateful for any advice.

Many thanks,
Susan

---

### Post by 101011010010 on 2009-06-25
It looks as though Firefox 3.5 RC3 is out, you may want to try that.When you uninstall don't forget to check for config files and make sure that everything is gone. You could also start firefox from a terminal, the output may help isolate the problem. I hope this helps.

---

### Post by susanpenter on 2009-06-25
I have downloaded firefox-3.5rc3.tar.bz2 and I have extracted this as a firefox 3.5 folder in my home directory.  I now need to know how to use either the archive or the folder to compile the program.

I am hoping that in the same way as I had a working Shiretoko program before this will also set up a seperate program to my Firefox 3.0.11 so that i still have this as backup.

Thanks

---

### Post by Malta paul on 2009-06-25
Hi
This link may help you:
[http://ubuntuforums.org/showthread.php?t=1193223](http://ubuntuforums.org/showthread.php?t=1193223)

But I install 3.5 rc2 from 'Synaptic Package Manager' and its working great :D

---

### Post by lovinglinux on 2009-06-25
The solution to your problem is in the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

> **lovinglinux said:**
> 

**[size="5"][color=#CC0000]Troubleshooting[/color][/size]**

Several Firefox problems are related to corrupted profiles and can be easily fixed by restoring a profile backup (see Backup section), by deleting the corrupted profile or deleting specific files inside the profile. Usually, there is no need to re-install Firefox.

I don't know why everyone recommends moving, renaming or deleting ~/.mozilla folder to solve Firefox issues. The ~/.mozilla folder is also the place where other Mozilla applications might store their profiles (Sunbird, etc), so deleting this folder will delete their settings too. 

Firefox profiles are stored under ~/.mozilla/firefox folder. So if you need to remove a Firefox profile to fix a problem, then delete, rename or move ~/.mozilla/firefox not ~/.mozilla.

Profiles are stored in your home directory, under the hidden folder .mozilla. To see it, you need to hit CTRL+H when browsing home.

Firefox 3.5 profiles are stored inside ~/.mozilla/firefox-3.5/

Simple delete the profile folder and it should work again.

---

### Post by Footer on 2009-06-26
> **Malta paul said:**
> Hi
This link may help you:
[http://ubuntuforums.org/showthread.php?t=1193223](http://ubuntuforums.org/showthread.php?t=1193223)

But I install 3.5 rc2 from 'Synaptic Package Manager' and its working great :D

I can't seem to find 3.5 rc2 in Synaptic ... 3.5b4 is all I'm seeing.

---

### Post by lovinglinux on 2009-06-26
> **Footer said:**
> I can't seem to find 3.5 rc2 in Synaptic ... 3.5b4 is all I'm seeing.

It's because some users are confusing both releases and thinking they are the same thing. This is not the first comment I see with this misconception.

Firefox 3.5rc2 is not available in the repositories.

---

