---
title: "Im really REALLY stuck.. Please Help!"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by RayZombie on 2009-07-27
Alright, last night, i screwed my brand new windows vista laptop up, so I decided to us my friends computer and burn a copy of Ubuntu 9.0 something.. 
Today, when I tried to get onto Youtube, It said I need to install Adobe Flash Player.. Since I have a 64bit computer, it didn't work.. After finding out what to download, I came to a problem.. I can't move the proper plug in into the firefox plug in folder because I don't own that folder..
I looked everywhere, and everyone is saying to type in some command to claim ownership.. The thing is, I have no idea how to type in commands..
Can someone help me, please!

---

### Post by philcamlin on 2009-07-27
try installing this instead 

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by RayZombie on 2009-07-27
> **philcamlin said:**
> try installing this instead 

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Thats what I have, I just dont have permission to move the .SO into the /usr/lib/mozilla/plugins

---

### Post by theozzlives on 2009-07-27
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by jose158 on 2009-07-27
To gain access to the folder: Go to Applications -> Accessories -> Terminal and type  ```
gksudo nautilus
``` to open up the file browser with full privileges and do what you have to do. You do know what folder to go to right?

**EDIT: The command above opens up the file browser only, the people above have better replies!**

---

### Post by izizzle on 2009-07-27
Go into synaptic package manager and look for "flashplugin-installer" and "flashplugin-nonfree" and install them. Now, restart firefox and youtube/flash should be working.

---

### Post by RayZombie on 2009-07-27
Alright, thanks you guys, I got it working

---

### Post by philcamlin on 2009-07-27
good to see 

sorry my post want helpful :(

---

### Post by TDurden1937 on 2009-07-27
PS man you guys are fast . . . there was no reply to this post three minutes ago and now there are five. Glad you all got it solved! You all are pretty nice too . . . some forums I've been on wouldn't have given such a sketchy post the time of day.

Wait . . . slow up slick. Explain a little more. You burned a 9.0.4 version of Ubuntu onto a DVD then installed it on your screwed up labtop?

If you want help on a forum ya got to give a step by step description of what you did.

If it was "9.0 something . . ." then its probably Ubuntu 9.0.4 (Jaunty) and the 64bit thing has to do with the Operating System. Did you download a 64bit version of Ubuntu or the x86 version? That's what determines whether your computer is 64 or 32 bit. If you have a processor that will handle a 64 bit O/S then it will work with a 32 bit O/S.

Come up with a detailed description of your laptop or no one will be able to help you let alone pay any attention to your post . . . got it. I can see how ya screwed up your Vista O/S (Windows sucks anyway so no loss) 'cause ya don't no what you are doing. Post that description of your computer hardware and then describe in DETAIL what you did . . . as in "I installed Ubuntu 9.04 Jaunty 64 bit version and the installation went okay. Then when I ran the Ubuntu version of Firefox and went to Youtube the site said I needed to install the Flash Player plug in." Something like that. BTW, ya don't just move the plugin to the Firefox plug in folder . . . ya download Flashplayer from Adobe for linux. At Adobe they will have you select which O/S ya want to download the plugin for . . . pick *.deb because Ubuntu uses those type of packages for the software. *.deb means the files that end with deb.

If ya don't give more information no one can help you.

TDurden1937



> **RayZombie said:**
> Alright, last night, i screwed my brand new windows vista laptop up, so I decided to us my friends computer and burn a copy of Ubuntu 9.0 something.. 
Today, when I tried to get onto Youtube, It said I need to install Adobe Flash Player.. Since I have a 64bit computer, it didn't work.. After finding out what to download, I came to a problem.. I can't move the proper plug in into the firefox plug in folder because I don't own that folder..
I looked everywhere, and everyone is saying to type in some command to claim ownership.. The thing is, I have no idea how to type in commands..
Can someone help me, please!

---

### Post by philcamlin on 2009-07-27
> **TDurden1937 said:**
> Wait . . . slow up slick. Explain a little more. You burned a 9.0.4 version of Ubuntu onto a DVD then installed it on your screwed up labtop?

If you want help on a forum ya got to give a step by step description of what you did.

If it was "9.0 something . . ." then its probably Ubuntu 9.0.4 (Jaunty) and the 64bit thing has to do with the Operating System. Did you download a 64bit version of Ubuntu or the x86 version? That's what determines whether your computer is 64 or 32 bit. If you have a processor that will handle a 64 bit O/S then it will work with a 32 bit O/S.

Come up with a detailed description of your laptop or no one will be able to help you let alone pay any attention to your post . . . got it. I can see how ya screwed up your Vista O/S (Windows sucks anyway so no loss) 'cause ya don't no what you are doing. Post that description of your computer hardware and then describe in DETAIL what you did . . . as in "I installed Ubuntu 9.04 Jaunty 64 bit version and the installation went okay. Then when I ran the Ubuntu version of Firefox and went to Youtube the site said I needed to install the Flash Player plug in." Something like that. BTW, ya don't just move the plugin to the Firefox plug in folder . . . ya download Flashplayer from Adobe for linux. At Adobe they will have you select which O/S ya want to download the plugin for . . . pick *.deb because Ubuntu uses those type of packages for the software. *.deb means the files that end with deb.

If ya don't give more information no one can help you.

TDurden1937

he already got it fixed :popcorn:

---

