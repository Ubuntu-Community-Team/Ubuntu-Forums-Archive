---
title: "Restricted Drivers problem"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by Anniku989 on 2008-03-12
First off, I searched, and found a few threads but they didn't help much...

Anyway, to sum up everything here. I'm on my laptop which was running ubuntu fine for about a week (Installed perfectly fine, and no problems since), but ended up having to reformat this partition (re-install ubuntu) on it for another problem. Everything installed fine this time, except for my wireless card drivers (broadcom, tell me about it...). I went to the restricted drivers manager, but it says 
The software source for the package

   bcm43xx-fwcutter

 is not enabled.

I tried ```
sudo apt-get install bcm43xx-fwcutter
``` , with that not working, and nothing else in the other threads with this problem working, I tried the codes in[ THIS ]("http://www.linuxforums.org/forum/ubuntu-help/110279-sof-tware-source-package-___-not-enabled.html")thread, but nothing happening but terminal errors.

Also, I'm connected via a wired Ethernet connection, but when I enter code ```
sudo apt-get install xchat
``` in the terminal, it says it cannot find 'xchat' for some reason ( I was going to ask this question on the ubuntu irc, but can't get it up)

Thanks in advance for any and all help!

---

### Post by Anniku989 on 2008-03-12
Seems to be a common problem, and I just found a solution for it, so I guess I'll post it.

1st
Goto System>Admin>Software Sources
CHECK boxes:  Lines with (Universe) AND (Multiverse) at the end
UNCHECK boxes: Source Code (for the time being) AND Cdrom with ubuntu
close

2nd
Goto System>Admin>SynapticPackageManager
Click Settings>Repositories
Check/uncheck the same boxes as in step one (If different)
Close the box (But not synaptic)
Hit Reload
Scroll down to *bcm43xx-fwcutter*, right click the box next, and click "install"
Accecpt changes

3rd
A install box for the above will pop up upon the clickage of 'install'
just hit 'forward' a few times

Now, go back to System>Admin>RestrictedDriversManager
Click Enable>Enable
Fill bubble "Download from internet location", hit apply/install/download or whatever it said. 

Cheers!

---

