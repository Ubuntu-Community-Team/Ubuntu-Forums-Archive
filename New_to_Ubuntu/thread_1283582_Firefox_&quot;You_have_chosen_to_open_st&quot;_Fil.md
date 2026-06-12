---
title: "Firefox &quot;You have chosen to open st&quot; File Error"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by Nightstrike2009 on 2009-10-05
Hiya everyone I have noticed an annoying bug in firefox with ubuntu and Windows xp, I know how to fix the windows xp one by editing the "Hosts" file, how do I stop ubuntu from displaying same annoying error message?

I Get a window saying

> Opening st

You have chosen to open
st
Which is a: BIN File
from: [http://ad.yieldmanager.com](http://ad.yieldmanager.com)

Would you like to save this file?
(Buttons)
CANCEL     SAVE FILE

It mainly occurs with yahoo email page, i selected no such file and seems to be linked to an advert of some type.

Can anyone help with this?

---

### Post by halitech on 2009-10-05
you can do the same in Ubuntu by editing /etc/hosts

---

### Post by Nightstrike2009 on 2009-10-05
How would i do that in Windows Xp the fix is:

> You can add a line to your HOSTS file to stop it trying to load the ads.

The Hosts file is found in C:\WINDOWS\SYSTEM32\DRIVERS\ETC\ - Open the Hosts file with Notepad. the line to add is:

127.0.0.1    ad.yieldmanager.com

right click the Hosts file and uncheck Read Only (If required wasn't neccessary with mine) and save the file.

I've found the location in ubuntu (from menu bar)

Places/computer/filesystem/etc/hosts

It looks different to Windows XP and unsure how to proceed, also get neccessary permissions error blocking me when save is attempted can anyone help?

---

### Post by halitech on 2009-10-05
same idea but the file location is /etc/hosts

to edit the file, press ALT + F2 and enter
```
gksudo gedit /etc/hosts
```
then add 
```
127.0.0.1    ad.yieldmanager.com
```
under where the other 127.0.0.1 entries are. Then save the file (file - save) and close. Might want to reboot to ensure it is taking effect after saving the file.

here is what mine looks like
```
127.0.0.1	localhost
127.0.1.1	debian.eastlink.ca	debian

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by Nightstrike2009 on 2009-10-05
cheers halitech that error annoys the hell outta me :-)

---

### Post by halitech on 2009-10-05
did that work for you? If it did, edit your first post to change the title to include (solved)

---

### Post by lavinog on 2009-10-05
Have you tried adblock plus plugin for firefox?  I would wonder if that file is a malacious attack from an advertisement.

---

### Post by Nightstrike2009 on 2009-10-05
Yeah been a while halitech took time out for a while was figuring out how to mark my thread as solved, i've done it now LOL

> For new users or confused ones like me to mark thread as solved:

either go to first post then click edit, then edit again and mark first thread title as [SOLVED] 
or
go to thread tools at the top in red and select "mark as solved" from pull down menu.

Nah, lavinog the techs on windows xp side say its a advert but firefox has a problem with it and displays that error, thats what they say anyhow. You guys probably know better as your the real experts after all :-)

---

