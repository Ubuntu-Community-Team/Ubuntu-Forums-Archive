---
title: "Standard ZIP utility"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Neural Nut@work on 2010-02-09
**Summary**: Ubuntu doesnt come packaged with a ZIP/UNZIP utility to unzip windows files
[COLOR=DarkGreen][What I'm looking for is a good reason, and also answers to some other related questions marked Qx) ..thanks!][/COLOR]

**I Tried**:

[LIST]
[*]apt-get install ([COLOR=Red]FAILED [/COLOR]because what Im trying to unzip is MY WIRELESS CARD driver)
[*]GUNZIP, TAR, JAR (none worked)
[/LIST]
**What Finally worked**:
I searched the net, and on some vague random site found 7Zip (7z command).
[Get it here]("http://packages.debian.org/unstable/utils/p7zip")

[COLOR=Blue]As a result of the discussion, [/COLOR][mechro]("http://ubuntuforums.org/member.php?u=922703") [COLOR=Blue]supplied this link: [/COLOR][http://packages.ubuntu.com/karmic/allpackages](http://packages.ubuntu.com/karmic/allpackages) 
[COLOR=Blue]from where one can download stuff incase you cant use the network and hence apt-get directly. (More useful to know)
[/COLOR] 
**Description** (Problem Flow):
_Story _(YAWN) : I recently decided to junk my old XP box (with a fedora) partition and install it with [COLOR=Indigo]Ubuntu "[/COLOR][COLOR=Indigo]Karmic Koala"[/COLOR] server edition. As a newbee, you want to install the drivers etc and have yourself setup. I need to setup my Wireless card for starters. A NetGear wg311v3.

 By default it is not detected, but the [Ubuntu Doc]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3") is impressive. It requires you to use "ndiswrapper" and unzip the Windows NetGear Driver (my original driver was an exe, from Netgear I was able to download the ZIP version)

[COLOR=Red]Here is where things get interesting[/COLOR]:
So far, am in control feeling all good. Suddenly, I try to unzip and nothing works.
The Ununtu forms, all talk of ```
apt-get install zip
``` etc. 
Well, If I dont have internet, apt-get will get nothing (see /etc/apt source list)

I found out about [COLOR=Indigo]**Ubuntu Repositories**[/COLOR] from there; but the repos seem to be archived files and you manually cant get anything out straight away.
[COLOR=Red]Q1)[/COLOR] Can you ? How? Please assume the use has to use a non-ubuntu box to get the files in the first place

So I downloaded, 7-Zip put it on a CD and used that. I still have to configure my wirelss completely but it installed the driver and using modprobe I've set it.

..Appreciate, reasoning and answers.

---

### Post by Bachstelze on 2010-02-09
Cool story, bro.

---

### Post by lijcam on 2010-02-09
One of the first things you should do with a fresh install is install ubuntu-restricted-extras package.

This package installs various video/audio codes windows fonts unrar unzip flash java etc.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Neural Nut@work on 2010-02-09
**lijcam **: thanks. Though, does apt-get get the stuff from the installation CD or always the NET? 

If the thing im trying to install is thew Driver (zipped) then its a chikend n Egg situation right? And nevertheless from a different machine which has access to [COLOR=Red]Q2) [/COLOR]**internet I should be able to download stuff to unlock the chicken and egg situation right**?

Appreciate the answers guys!

---

### Post by lijcam on 2010-02-09
Can you plug into your network to install the package first?

---

### Post by mechro on 2010-02-09
If you know the package you need you can download the .deb file from here...

[http://packages.ubuntu.com/karmic/allpackages](http://packages.ubuntu.com/karmic/allpackages)

You can then transfer the .deb file to your unconnected computer and install by right-clicking and use Gdebi Package Installer.

Example... if you do a page search(on that link) for "7zip" it comes up with the "p7zip" package

---

### Post by Neural Nut@work on 2010-02-09
**mechro **: Thanks, that [link ]("http://packages.ubuntu.com/karmic/allpackages")is what I was looking for. (and answers Q1)
**lijcam **: In short **No**; because the box has a single wireless card to connect to the network and this entire process is to get that card to work.

Hope the thread helps others also. (I can imagine how it is when its something basic yet illusive to a beginner :D )

---

### Post by warfacegod on 2010-02-09
> lijcam : thanks. Though, does apt-get get the stuff from the installation CD or always the NET?

You can go to: System> Admin.> Software Sources> and enable "Installable From CD"

You'll need to put the disc in (obviously), open Synaptic, and click "Reload".

---

### Post by Neural Nut@work on 2010-02-09
Useful to know; though am on server (non-GUI) version. I bet that translates to some commands then (I guess involves modifying the source list or something since that files contains links to the WEB ?!?). If you could translate that into unix commands, I'd be obliged. (Already am from all the help)

I plan to add GUI at some point if I require it.

thanks man.

---

### Post by warfacegod on 2010-02-09
> **Neural Nut@work said:**
> Useful to know; though am on server (non-GUI) version. I bet that translates to some commands then (I guess involves modifying the source list or something since that files contains links to the WEB ?!?). If you could translate that into unix commands, I'd be obliged. (Already am from all the help)

I plan to add GUI at some point if I require it.

thanks man.

I can't help you with commands. I don't know the Terminal well enough.

---

### Post by warfacegod on 2010-02-09
Another package you may need in the future is "unrar".

---

