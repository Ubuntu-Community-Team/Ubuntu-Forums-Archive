---
title: "how to play MP3, M4a and WMA files on Ubuntu"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by smiffy cg on 2009-05-06
hi, I'm completely new to Ubuntu.

Things was going great with my new net book till i found that i couldn't play my music. now I have looked at some other threads on loads of forums but they say something about vlc??? can someone tell me how to do that please???

People was also saying about downloading free media players but i can seem to find one that will work properly, so if anyone has any ideas they're welcome too.

please help....

---

### Post by buzzmandt on 2009-05-06
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
never fails for me, have fun

---

### Post by llemm on 2009-05-06
> **smiffy cg said:**
> hi, I'm completely new to Ubuntu.

Things was going great with my new net book till i found that i couldn't play my music. now I have looked at some other threads on loads of forums but they say something about vlc??? can someone tell me how to do that please???

People was also saying about downloading free media players but i can seem to find one that will work properly, so if anyone has any ideas they're welcome too.

please help....


Happens to me to too. I am new too this too. But I learned that the default installation of Ubuntu does not have codecs to play Multimedia.

so here what you gonna do. I assume you have an Internet.

go to Applications - Accessories - Terminal

type this

sudo apt-get install vlc

type your password 

thats it.

HTH

---

### Post by SunnyRabbiera on 2009-05-06
There is another method to get you started, go to applications and then to add/remove
with this app you can install the ubuntu retricted extras packages, here is a good package installation guide:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

VERY helpful for the beginner

---

### Post by rhcm123 on 2009-05-06
You don't need VLC unless the files are encrypted. Otherwise you need the legalese-drenched (you wont see any of it besides the sun java one) restricted packages, and you can grab them with this command in the terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by mick8985 on 2009-05-06
```
sudo apt-get install gstreamer0.10-plugins*
```
grabs pretty much everything
then follow everything on [this page]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by freeman2000 on 2009-05-07
Add Medibuntu to your repositories to download VLC and other media related packages.  To get the Medibuntu library, open a Terminal window and type:  

sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list   

Good luck.

---

### Post by sundar_ima on 2009-05-07
> **llemm said:**
> 

I assume you have an Internet.

HTH

if you do not have internet then download this debian package from here [http://rapidshare.com/files/229539080/ubuntu_restricted_extras_31.deb]("http://rapidshare.com/files/229539080/ubuntu_restricted_extras_31.deb") install it by just double clicking. this will install restricted packages need to most widely used music and movie files. if you want to install VLC with out internet connection then go to this page [http://hacktolive.org/wiki/VLC_offline_installer_(Ubuntu)]("http://hacktolive.org/wiki/VLC_offline_installer_(Ubuntu)") download vlc_offline_installer and extract it. installation instructions are given in the extracted folder.

---

### Post by smiffy cg on 2009-05-07
Thanks for all of the responses, unfortunatly after trying everything you have all said, just this message keeps coming up "Failed to connect stream: Invalid argument"

does anyone know what that means??? Is my net book knackered??? or is there anything else I can do?

---

### Post by logos34 on 2009-05-07
Check [this]("https://answers.launchpad.net/ubuntu/+source/totem/+question/37103") in sound prefs.

Or maybe it's an issue with pulseaudio and [libasound2]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/191027")

---

### Post by Don1500 on 2009-05-07
Everything about sound in one place 
Do what it says here and you will be able to sooth the savage beast.

[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

---

### Post by mhaight on 2009-05-07
> **llemm said:**
> Happens to me to too. I am new too this too. But I learned that the default installation of Ubuntu does not have codecs to play Multimedia.

so here what you gonna do. I assume you have an Internet.

go to Applications - Accessories - Terminal

type this

sudo apt-get install vlc

type your password 

thats it.

HTH

This is correct and will work, but in the future do not run code from people that you don't know, it could be _**[malicious]("http://ubuntuforums.org/announcement.php?f=326")**_.

---

### Post by Godly on 2009-05-07
I just press play.

---

### Post by thelegionsplayer on 2009-05-07
new to ubuntu--
ver:9.04 
   wen i try to install amarok,from applications add/remove programs it says failed to do er sumting..bcoz adp get (or sumting like that) is running ,please close that application and continue

well i just need sumtin to play mp3s and other sound formats..ny help?

and sum more doubts:-
1.how can i hide my WinXP protected system files(pagefile.sys etc)?
(my ubuntu is installled withhin windows)
2.do i lose any features of ubuntu if iv reduced the allocated space (iv currently set it to 7GB)
3.and where can i get the commands for python and terminal window

---

### Post by raymondh on 2009-05-07
> **buzzmandt said:**
> [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
never fails for me, have fun

LOL ... me too .... in fact, in each upgrade (if I do) that's the first thread I visit ...

Enjoy

---

### Post by photon_man62 on 2009-05-07
You have a file manager (or whatever it's called) running, like Add/Remove Programs etc.

You should try Songbird, it's a very good media player. Download it [here]("http://unter-hund.com/2008/12/03/songbird-1-final-linux-installer/").

Don't forget to update it!

---

### Post by thelegionsplayer on 2009-05-08
oh well,mp3s now work wid that rythmbox.. tried to open mp3s wid it..it searched for plugins..installed.done thnx for  ur help anyway..bt still--
1.)how can i hide Winxp protected system files(pagefile,autoexec.bat etc)
2.)how dus ubuntu show my winxp partition ..iv seen that its like mountig or sumting..like mounting iso files?
3.)and in Firefox there is no [Options] in the [Tools] menu..how do i make the [Options] option appear?
4.)how do i remove the animation wen i minimize a window?
5.)and dis home folder,videos etc..where are these located in my hdd?in the drive in wich in installed ubuntu?
ihav C: wich is named as 21.0gb media(??):shock: ,D drive ,E drive and F; where ubuntu is installed
6.)and in add/remove progs ..the reload button ..does it function like checking for updates?
7.)wats the difference between :[Movie player]and [Movie player (Gstreamer)]

---

### Post by Don1500 on 2009-05-08
"1. how can i hide Winxp protected system files(pagefile,autoexec.bat etc)"
Don't Mount your windows drive.

"2.)how dus ubuntu show my winxp partition ..iv seen that its like mountig or sumting..like mounting iso files?"
Mounting a drive is what allows you to use that drive in Ubuntu, If it is not mounted you can't use it. To mount a drive just go to PLACES - HOME (Or any) Folder. You will see all of the drives attached to your machine. Mounted drives will have an ICON next to them. Your "C:/" drive will not be called that unless you set that lable in Windows, otherwise it will show something like "21.0gb media" or whatever the size of your drive is. (I see you've figured this out.) To mount a drive , Right click on it and choose that option.

"3.)and in Firefox there is no [Options] in the [Tools] menu..how do i make the [Options] option appear?"
The "Options" in Firefox is in the EDIT Tab. Called "Preferences".

"4.)how do i remove the animation wen i minimize a window?"
What program?
The other stuff is too much work for me right now, my Break is over.:guitar:

---

