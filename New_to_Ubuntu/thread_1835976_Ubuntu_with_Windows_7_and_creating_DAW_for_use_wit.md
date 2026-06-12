---
title: "Ubuntu with Windows 7 and creating DAW for use with Ubuntu"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by arlen_audio93 on 2011-08-30
Hello good forum, 

  I recently installed Ubuntu along with windows 7  on a laptop. I don't have to use my CD but I know it's not a full  version of Ubuntu that I installed. 

i burned the ISO from the home site to disk and installed. all is working well; however, i have a few questions: 

if this is a limited version, what things would i not be able to do? 
i'm having trouble gaining root (if i use the su, or sudo commands) i receive an error message after typing in my password. Should i be able to have root access with the a limited version/installation? 

i don't see how to mnt my C drive which has some windows files i'd like  access to from the command line-when i switch to the /mnt folder, i do  not see any drives listed after doing a ls command 
will it be much easier if i completely switch my laptop over to Ubuntu? 
I don't like  7 at all and i've lost my installation cd for XP
i was only using XP for my music.

Seeking and open to suggestions: 
I'd like to switch completely over to Ubuntu. I have a laptop with  Windows 7 on it, a desktop full of viruses with XP on it (without the  installation cd) dua processor decent desktop once i get the viruses  off) and a much older desktop. I was thinking of creating a home network  for the learning experience and maybe as a server for online gaming/one to back up files etc

i actually would love to have a linux system set up as a Digital  Recording Workstation. I have (hard ware-Mbox 2 pro) and Pro Tools LE 7  (older version) and Reason 4.0 
I read about WINE but haven't to use it yet. 
i'm looking at using Reason Record, Reason 5 and Recycle. i want to make sure that i can get ubuntu working with this setup. i forum had a driver uploaded for the mbox 2 pro i found. However, he can mention USB and the Mbox 2 Pro uses firewire. I will need to use fire wire also. 

so my main question is what would you suggest i do about my little situation.

---

### Post by decoherence on 2011-08-30
> **arlen_audio93 said:**
> i actually would love to have a linux system set up as a Digital  Recording Workstation. I have (hard ware-Mbox 2 pro) and Pro Tools LE 7  (older version) and Reason 4.0 
I read about WINE but haven't to use it yet. 
i'm looking at using Reason Record, Reason 5 and Recycle. i want to make sure that i can get ubuntu working with this setup. i forum had a driver uploaded for the mbox 2 pro i found. However, he can mention USB and the Mbox 2 Pro uses firewire. I will need to use fire wire also. 

so my main question is what would you suggest i do about my little situation.

Boot from a live CD and test, test, test! You can test your entire setup from the live cd -- install the programs you want, test drivers, etc.. The only drawback is that it'll be a bit slow and you'll have to do it again if you decide to do a full install or if your computer reboots (so take notes!)

While I can't address much of what you said directly, I can share my experience.

I recently moved away from Linux for my DAW. It's not that you can't do a good DAW in Linux -- it's just that if you're trying to do it with your general purpose computer, as I was, certain things can cause your DAW to break frequently. For instance, if you're using your computer to surf the web and decide you want to lay down a track, you may find JACK won't start because the browser or some plugin refuses to give up the sound card. I've also had my video drivers fail after an update -- not related to audio but still prevents me from recording. I've had my ethernet stuff fail preventing me from looking up music.

So while JACK is great and there is a solid collection of tools you can plug in to it, I've had many inspired moments spoiled by technical issues that prevent me from laying down a track when I want to.

So i got fed up, dual-booted Windows 7 and bought a copy of Reaper. Now I have to reboot to record but at least I know when the system comes up, it'll be ready to go.

I might try the Linux DAW thing again if I can devote a computer to it with open source video and network drivers. Funny how those things would be my major stumbling block but there you go.

---

### Post by CatKiller on 2011-08-30
"Alongside Windows" doesn't distinguish between a dual-boot installation and a Wubi installation. I haven't used Wubi so I don't know its particular limitations.

su and sudo are different things. Sudo should work out-of-the-box with just your normal password. su won't work because you'd need to put in root's password and it doesn't have one. Logging in as root is not possible with a default Ubuntu install and doing so is specifically discouraged.

You need to mount the partition before you can access the files on it. If you do this by clicking on the drive in the Computer section of the file manager it will turn up in /media. If you mount it by editing /etc/fstab you can put it wherever you want. Not being able to mount the partition that holds the Wubi subsystem file might be a limitation of Wubi, but I wouldn't know for sure.

If you want to use those particular programs for doing audio work, it's best to do so on their native platform. It's perfectly possible to do audio work in Ubuntu but you'll have most luck using native tools, which will be different than what you're used to. Some of the Linux audio tools are a bit rough around the edges.

---

### Post by arlen_audio93 on 2011-08-30
> **decoherence said:**
> 


I recently moved away from Linux for my DAW. It's not that you can't do a good DAW in Linux -- it's just that if you're trying to do it with your general purpose computer, as I was, certain things can cause your DAW to break frequently. For instance, if you're using your computer to surf the web and decide you want to lay down a track, you may find JACK won't start because the browser or some plugin refuses to give up the sound card. I've also had my video drivers fail after an update -- not related to audio but still prevents me from recording. I've had my ethernet stuff fail preventing me from looking up music.



I thank your for the advice. I think most of the problems you had are problems all of us have when trying to use a computer as a DAW while using it as a multi-purpose pc also regardless of the OS. That is, if you're using it for an all purpose workstation, it will cause problems. If you have automatic updates turned on windows, it may happen to update while you're tracking audio causing unwanted sounds and loss of system performance. I plan to use one computer as a DAW and not even use internet or anything else on it period. I hope anyhow. I've also read it' s a bad idea to have a dual OS when using a computer as a DAW. I know Linux used just from CD etc might not be the same. I have a buddy who's an engineer and he said to always have a external drive (fire wire) for your audio to keep it segregated from other files on your pc.

---

### Post by Enigmapond on 2011-08-30
I can save you some time here. Reason, ReCycle, Cubase, Pro-Tools, Adobe Auditions will NOT run properly through Wine and forget about any VST's like Waves...I know...It's the only reason I keep my Win7 partition. There are fairly good programmes available for audio for Ubuntu however, they fall short and it's a real chore to get things working...I feel your pain but for the time being, especially with those apps...I have them all...you are better off dual booting.

Good Luck!

---

### Post by arlen_audio93 on 2011-08-31
I think Engimapond's reply has answered my questions along with Catkiller. 
If anyone has any fun suggestions for using Ubuntu on two older desktops, please let me know. I thank you all.

---

