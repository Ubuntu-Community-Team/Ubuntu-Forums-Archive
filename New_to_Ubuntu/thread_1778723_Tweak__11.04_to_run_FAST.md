---
title: "Tweak  11.04 to run FAST?"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by mamaj on 2011-06-09
I just installed ubuntu 11 on my 512mg Ram AMD Athlon XP PC, and it seem to be a bit slow...even slower then XP which i had before this. After I ran all the updates, it seems a bit faster though( i also added Unity 2D, since got no harware for 3D..). 
  The question is how do I tweak it to run optimally fast on my machine? ( I also installed Ubuntu Tweaks for further customisation)
 P.S. Of topic, when I try to play a video through build in player/VLC, it logs me out of the OS after the first 2-3 seconds of playing it.. whats the deal here?

---

### Post by astrobob.tk on 2011-06-09
> **mamaj said:**
> I just installed ubuntu 11 on my 512mg Ram AMD Athlon XP PC, and it seem to be a bit slow...even slower then XP which i had before this. After I ran all the updates, it seems a bit faster though( i also added Unity 2D, since got no harware for 3D..). 
  The question is how do I tweak it to run optimally fast on my machine? ( I also installed Ubuntu Tweaks for further customisation)

I recommend installing fluxbox or xfce4 along with gnome. The system loads & operates fast on 10.04. When i don't need all the stuff on gnome i log ing to fluxbox or xfce4 (the latter i installed yesterday). I think i will do a similar thing with my old desktop (256 MB RAM)

---

### Post by fabricator4 on 2011-06-09
> **mamaj said:**
> I just installed ubuntu 11 on my 512mg Ram AMD Athlon XP PC, and it seem to be a bit slow...even slower then XP which i had before this. After I ran all the updates, it seems a bit faster though( i also added Unity 2D, since got no harware for 3D..). 
  The question is how do I tweak it to run optimally fast on my machine? ( I also installed Ubuntu Tweaks for further customisation)
 P.S. Of topic, when I try to play a video through build in player/VLC, it logs me out of the OS after the first 2-3 seconds of playing it.. whats the deal here?

Check your memory usage.  Unity 2D is not as well developed and still has a few problems.  Check the memory usage of the module Unity2d-places in particular.  A memory leak in this module was supposed to be fixed however I haven't checked it recently.  If the module memory usage grows too much you can safely kill it to get the memory back.  The module gets re-spawned when you open the application searcher.

Generally, I think Ubuntu is moving away from lower spec and older machines.  It's unclear if the code is going to get more efficient and compatible with older hardware in the near future.

+1 for Xfce and Xubuntu.

Chris

---

### Post by mamaj on 2011-06-09
any advice on [B]Tweaking  ext3 filesystem for a performance boost:

[http://ubuntuforums.org/showthread.php?t=107856](http://ubuntuforums.org/showthread.php?t=107856)

or [/B][B]Picking the Kernel thats Right for processor (Possible Speed Increase)?

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

By the way, I switched to Classic environment, 2D Unity was eating too much memory.
[/B]

---

### Post by astrobob.tk on 2011-06-09
> **mamaj said:**
> any advice on [B]Tweaking  ext3 filesystem for a performance boost:

[http://ubuntuforums.org/showthread.php?t=107856](http://ubuntuforums.org/showthread.php?t=107856)

or [/B][B]Picking the Kernel thats Right for processor (Possible Speed Increase)?

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

By the way, I switched to Classic environment, 2D Unity was eating too much memory.
[/B]

I believe its best that you try xfce4 before attempting to follow the above threads. I wouldn't recommend the above threads for a newbie (me among them; in my case, as I stated, I wanted a faster boot into my system, so I tried flux & xfce & they seem great).

Give it a try, its really simple; just run in a terminal

> sudo apt-get install xfce4

the same goes for fluxbox, replacing xfce4 with fluxbox.

Or ou could try LUbuntu, though the above are faster according to my testing.

Also check these:

[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

For other options: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

good luck

---

### Post by mamaj on 2011-06-10
Im looking more to tweak the Ubuntu itself, then install any other light alternatives, since i would rather just get XP then

---

### Post by mamaj on 2011-06-10
any advice on that?

---

### Post by kerry_s on 2011-06-10
So use xp then.

Different distros are made a certain way, ubuntu is not made to be lite or fast, it's made to cover more users. 

Lubuntu is the lite & fast version of ubuntu. [http://lubuntu.net/](http://lubuntu.net/)

---

### Post by walt.smith1960 on 2011-06-10
Lubuntu 11.04 works pretty well on this machine with lesser specs than the O.P.'s machine.  P3 1.1 ghz./512 RAM

---

### Post by kerry_s on 2011-06-10
> **walt.smith1960 said:**
> Lubuntu 11.04 works pretty well on this machine with lesser specs than the O.P.'s machine.  P3 1.1 ghz./512 RAM

exactly, all the hard work is done. all you have to do is tweak it to your tastes. add what ever else you want/need.

i'm using lubuntu 11.04, xcompmgr+docky for launchers & taskbar, even added the ambiance themes to give it more of the standard ubuntu look.

(i put the menu out cause i'm hiding what i have on the desktop :) )

---

### Post by nzjethro on 2011-06-10
You could install Xubuntu Desktop (xubuntu-desktop or similar in the Ubuntu Software Centre). It's an Ubuntu shell that uses xfce instead of gnome. You can install it with Ubuntu, and then when you login, select Xubuntu desktop session rather than Ubuntu desktop session. Sure, it involves installing stuff, but it's still your same OS (same programmes and everything) just with the lightweight xfce GUI. I'm not sure, but I imagine the effect is the same as installing Xfce as stated by the above posters.

---

### Post by kerry_s on 2011-06-10
> **nzjethro said:**
> You could install Xubuntu Desktop (xubuntu-desktop or similar in the Ubuntu Software Centre). It's an Ubuntu shell that uses xfce instead of gnome. You can install it with Ubuntu, and then when you login, select Xubuntu desktop session rather than Ubuntu desktop session. Sure, it involves installing stuff, but it's still your same OS (same programmes and everything) just with the lightweight xfce GUI. I'm not sure, but I imagine the effect is the same as installing Xfce as stated by the above posters.

xfce has been very buggy lately, leading to bad user experiences.
lxde on the other hand has gotten there stuff together. pcmanfm was usually the buggiest app, but i haven't had any problems with it so far.

---

### Post by nzjethro on 2011-06-10
> **kerry_s said:**
> xfce has been very buggy lately, leading to bad user experiences.
lxde on the other hand has gotten there stuff together. pcmanfm was usually the buggiest app, but i haven't had any problems with it so far.

I have Xubuntu Desktop installed with Ubuntu, and haven't had issues yet. Mind you I've only played around with it for a couple of days, I prefer the feel of GNOME.

---

### Post by kerry_s on 2011-06-10
> **nzjethro said:**
> I have Xubuntu Desktop installed with Ubuntu, and haven't had issues yet. Mind you I've only played around with it for a couple of days, I prefer the feel of GNOME.

I had a straight xubuntu install. Lubuntu is much faster.

---

### Post by jtarin on 2011-06-10
> **mamaj said:**
> Im looking more to tweak the Ubuntu itself, then install any other light alternatives, since i would rather just get XP thenLets see XP is about 11/12 years old.....just great for a box with your specs. Full-blown Ubuntu needs a machine more up to Win7 specs. There are other distros that will fit your ram budget.:p

---

### Post by fabricator4 on 2011-06-10
> **mamaj said:**
> any advice on that?

Your problem may be Unity 2D.  It's slooow.  Use the classic interface until Unity 2D is a bit more mature and bug free.

Another 512Mb of RAM would also make a difference.

To change to the classic interface (Gnome 2), in the login screen click on your username.  The bottom bar will then appear.  Change to classic interface then complete the login.

Chris.

---

### Post by mamaj on 2011-06-10
> **fabricator4 said:**
> Your problem may be Unity 2D.  It's slooow.  Use the classic interface until Unity 2D is a bit more mature and bug free.

Another 512Mb of RAM would also make a difference.

To change to the classic interface (Gnome 2), in the login screen click on your username.  The bottom bar will then appear.  Change to classic interface then complete the login.

Chris.

i figured. but classic is slow as well. im gonna give another go to Lubuntu. see what happens. Although with a little research it seems you can run W7 on 512mb ram quite well as it uses only 200...

---

### Post by jtarin on 2011-06-10
> **mamaj said:**
> i figured. but classic is slow as well. im gonna give another go to Lubuntu. see what happens. Although with a little research it seems you can run W7 on 512mb ram quite well as it uses only 200...Maybe a strpped down version but Professional is not usable with 512.

---

### Post by fabricator4 on 2011-06-10
> **jtarin said:**
> Maybe a strpped down version but Professional is not usable with 512.


There's a lot that's subjective here.  "Useable" for one person can simply mean that it runs at all, not how fast it is.  Likewise for the definition of a fast machine.  I've always found that Ubuntu outperforms XP on any hardware I've tried it on however.  I have an XP machine that I use for work with much higher specs (dual core, 2GB), that runs slower than this celeron with 1Gb RAM with Ubuntu on it.  Neither run what I would call particularly fast, though it's my wish to convert the dual core machine over to Ubuntu if I can get everything working that I need.

I would say, that if Ubuntu runs significantly slower than XP on the same hardware then something is broken. There's also the case where you do forget how slow Windows can be.  I have to change frequently and I'm amazed at how bad it can be sometimes, on much more powerful boxes.

Chris.

---

### Post by jtarin on 2011-06-10
> **fabricator4 said:**
> There's a lot that's subjective here.  "Useable" for one person can simply mean that it runs at all, not how fast it is.  Not subjective at all.....in plain english....not usable. As a paper weight...yes.

---

### Post by astrobob.tk on 2011-06-11
> **mamaj said:**
> Im looking more to tweak the Ubuntu itself, then install any other light alternatives, since i would rather just get XP then

This is not "another" alternative "OS". It is the same OS but with different covers ;) like books, there are the paperback & the hardcover & cloth. hehe

Windows doesn't have this (up to my knowledge).

Ubuntu will still be the same, it won't change; just its cover.

Personally, I recommend you keep your Windows, just for the sake of comparison. I have been an XP user myself since 2003 & only this year did I keep the Win7 on my new laptop, for trying's sake only.)

At least Linux (in all its distro's) gives you the option (& will, speaking of free will & freedom) to choose the software & options that suit you contrary to Windows which only gives you products they want to give you. Not just this, they want money from you too.

P.S. These are called GUI (graphical user interfaces).

It's your choice, but we are here, always, if you wana come back ;P

---

