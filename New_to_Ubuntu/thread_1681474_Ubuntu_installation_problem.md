---
title: "Ubuntu installation problem"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by Miladeen on 2011-02-04
Hi everybody!

I need some help for my ubuntu installation. 
I made three partitions on my hard and installed winXP on first. Second is just formated (NTFS), and the last partition is left unformatted. I want to install ubuntu on the last partition.
When I insert live cd (downloaded from [www.ubuntu.com](www.ubuntu.com), 10.10, x86) all I get is screen where I should choose to run live ubuntu, install ubuntu...
When I choose to install it looks like installation starts but everything I see is standard ubuntu wallpaper with mouse cursor over it (loading something) and nothing else. I tried several times, same happens everytime i try.

Does someone have any suggestions?

---

### Post by wicxity on 2011-02-04
How long did you leave it to load? I found I had to wait several minutes in order for the next stage in installation to commence.

---

### Post by Miladeen on 2011-02-04
I don't know exactly. About 10 minutes.
Do you think it takes longer to start installation?

Thanks for reply ;)

---

### Post by abnordude on 2011-02-04
Did you burn the disk properly?
If no, then try to burn another one.
But, if you think, that you burned it okay.
Then, [I think] that you should be patient for some time for the installation to progress.
Ubuntu takes a bit time to start the installation.

---

### Post by wicxity on 2011-02-04
Wait a little longer and see how that goes, if nothing advances then I'd suggest listening to abnordude and burning another disk.
Hey, it's what we're on here for, god knows how many times I've needed this forum :mrgreen:

---

### Post by Miladeen on 2011-02-04
Thanks!!
I'll try to burn another disk and leave the installation much longer. Hope this works.

---

### Post by Yougo on 2011-02-04
what are the specs of your computer? processor, RAM, (if it's very old, speed of cd-rom player), graphics card

is it very busy loading lots of stuff? if you have a very old computer, with a slow cd-drive, it might take a while. 
in that case, maybe you might be better off using the alternate install cd, which does it all with low graphics and a simple shell.
i don't know how clear the partitioning is spelled out in the Alternate Install, so be carefull

if you have a modern computer, it should not take 10 minutes or longer.

---

### Post by Miladeen on 2011-02-04
> **Yougo said:**
> what are the specs of your computer? processor, RAM, (if it's very old, speed of cd-rom player), graphics card

is it very busy loading lots of stuff? if you have a very old computer, with a slow cd-drive, it might take a while. 
in that case, maybe you might be better off using the alternate install cd, which does it all with low graphics and a simple shell.
i don't know how clear the partitioning is spelled out in the Alternate Install, so be carefull

if you have a modern computer, it should not take 10 minutes or longer.

It's old computer, but not too old. I have AMD Sempron 2800+, 1512MB RAM on 400MHz(DDR1), New cd/dvd rom, 250GB sata hard.

Thanks for reply.

---

### Post by oldfred on 2011-02-04
Did you burn it at the slowest speed you can? That often helps.

Did you verify ISO downloaded correctly? 

Not sure if your system is 64bit or 32bit. Are you installing 64bit or 32 version?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Have you tried running the LiveCd as a livecd to make sure everything works ok? Also have you backed up everything just incase?

---

### Post by Miladeen on 2011-02-04
Tried to run live ubuntu and same thing happens.
I found something on [this]("https://help.ubuntu.com/community/BootParameters") page. It's the same problem, but I still can't get it to start the installation.

I did manage to install ubuntu from windows, using wubi, but I want two separate, independent systems.

Downloaded ISO two times (x86 - 32 version) and burned both ISOs at speed x7.

Thanks everybody for your help!

---

### Post by oldfred on 2011-02-04
As the CD first starts do you get the small symbols at the bottom. It is supposed to be a human & a keyboard or telling you to hit a key so you can add boot parameters. Then use f6.

Most times now it is video issues. I had to use nomodeset to get my nVidia to work.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by Miladeen on 2011-02-04
> **oldfred said:**
> As the CD first starts do you get the small symbols at the bottom. It is supposed to be a human & a keyboard or telling you to hit a key so you can add boot parameters. Then use f6.

Most times now it is video issues. I had to use nomodeset to get my nVidia to work.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

Saw the symbols. At that point I click enter and then I see all those options (run live, instal...). 
I didn't try anything from this page that you gave me, so hope this works. 
Thank you

---

### Post by Miladeen on 2011-02-05
> **oldfred said:**
> As the CD first starts do you get the small symbols at the bottom. It is supposed to be a human & a keyboard or telling you to hit a key so you can add boot parameters. Then use f6.

Most times now it is video issues. I had to use nomodeset to get my nVidia to work.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

Same thing happens. I guess I will have to install with wubi.

---

