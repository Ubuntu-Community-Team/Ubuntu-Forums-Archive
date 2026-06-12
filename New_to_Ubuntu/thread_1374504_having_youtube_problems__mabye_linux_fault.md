---
title: "having youtube problems  mabye linux fault?"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2010-01-06
when i try clicking on the youtube links i get the video but it just shows a black screen  and thats pretty much it    is it linuxs fault or youtubes  im not sure anyone got any suggestion

---

### Post by firefly2442 on 2010-01-06
If you're using Firefox, it should pop up with a message on the top bar saying something is missing.  Then just click on this and install the Adobe Flash player (I'm guessing you don't have it installed).

Try going to the terminal and running:

```
sudo apt-get install flashplugin-installer
```

This will manually install the Adobe Flash player if it isn't already installed.

---

### Post by steveneddy on 2010-01-06
Have you been able to view YouTube videos in the past on Ubuntu?

If so, what have you done differently?

Have you installed any new software?

---

### Post by ubudog on 2010-01-06
This is a problem on some 64bit installs of Ubuntu. Maybe have to install a 32bit version.

---

### Post by pyrofreak99 on 2010-01-06
um i viewed a couple of videos in the past and i havent installed any new software  im installing the newest flash plugin to see if that helps   like the guy mentioned above

---

### Post by Ownager on 2010-01-06
> **pyrofreak99 said:**
> when i try clicking on the youtube links i get the video but it just shows a black screen  and thats pretty much it    is it linuxs fault or youtubes  im not sure anyone got any suggestion

Hi there, I think you forgot to do one thing. When you choose APT +9.04 version from adobe.com and prepare to install flash player, you must close Mozilla Firefox first. After you install flash player, you can open Mozilla Firefox and visit youtube. You will be able to watch a movie without seeing a blank box. Let me know how's it going on with your flash player. 

Good luck

---

### Post by pyrofreak99 on 2010-01-07
ok honestly that didnt help either  and am i going to have to update my linux to the newest one 9.10   or am i going to have to uninstall it down to a 32 bit version

---

### Post by tom.swartz07 on 2010-01-07
> **pyrofreak99 said:**
> ok honestly that didnt help either  and am i going to have to update my linux to the newest one 9.10   or am i going to have to uninstall it down to a 32 bit version

No need to worry- I had the same problem. heres my post on how to fix it:

[http://ubuntuforums.org/showpost.php?p=8573604&postcount=2](http://ubuntuforums.org/showpost.php?p=8573604&postcount=2)

---

### Post by ubudog on 2010-01-07
> **pyrofreak99 said:**
> ok honestly that didnt help either  and am i going to have to update my linux to the newest one 9.10   or am i going to have to uninstall it down to a 32 bit version

Yeah, might have to go to 32bit.  You won't be able to use more than 3.5 gbs of ram though....

---

### Post by ubudog on 2010-01-07
Try this: Open a terminal: Applications>Accessories>Terminal and type ```
sudo apt-get install flashplugin-nonfree
```

---

### Post by oldos2er on 2010-01-07
> **ubudog said:**
> Try this: Open a terminal: Applications>Accessories>Terminal and type ```
sudo apt-get install flashplugin-nonfree
```

A much better solution is to install 64-bit flash, as tom.swartz07 suggested.

If the OP has any other versions of flash installed, they should be removed.

---

### Post by steveneddy on 2010-01-07
I've been using 64 bit Ubuntu since Edgy or Feisty and have always been able to run Flash with no issues.

Uninstall any Flash you already have installed and install the version from the repos like the previous poster suggested.

If you are running 64 bit then here is the defact standard thread on UF to get you up and running:

[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

Read the ENTIRE first post including links before you start and hose your system.

Hopefully this will get you going - post back here with results and issues.

---

