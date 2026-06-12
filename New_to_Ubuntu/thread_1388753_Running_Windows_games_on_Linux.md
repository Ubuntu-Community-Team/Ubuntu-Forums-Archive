---
title: "Running Windows games on Linux"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by funkychild on 2010-01-23
I've been reading that there are ways to run Windows games on Linux.  Just looking for more info and necessary programs.  Also, does anyone experienced in running these games notice any performance issues?

---

### Post by JiuJitsu500 on 2010-01-23
I think you'll be directed to Wine more often than not.... Download this, use it to do nearly anything windows related. It is however hit and miss sometimes. PlayOnLinux is a good graphical front-end for Wine.

Performance issues though, given the computer power, is no and issue when you get it going generally. Most games (because of linux's need for less computing power) will be increased, mostly online games for one reason or another. I'm sure someone else can explain better than I can.

But, like I said, it's hit and miss sometimes and can be a REAL pain to get it on it's feet, but worth it to most. I'd say virtualize it, and share computing power with host/guest to play it right (though this is a decrease in performance). This is all what I've seen anyway :)

---

### Post by gradinaruvasile on 2010-01-23
Well games in virtualbox dont come near Wine in performance (if they work at all).
Wine (or its relatives PlayOn Linux, Cedega) are the only choices. More complex games (genarally newer 3d ones) are more likely to work slowly or dont work at all.

However i played Oblivion, Counterstrike (classic + source), Medieval Total War 2, Rome Total War on relatively low spec (AMD 3200+ single core/Nvidia 7600 GS/ Nvidia 8200 IGP) hardware - not stellar performance, but playable.

I hope you have Nvidia video card - for Wine, this is the best compatible brand because of their good drivers - the rest is hit and miss.
Also, PulseAudio dont mix well with Wine (and gaming on Ubuntu in general).

---

### Post by J V on 2010-01-23
Performance and chance to work are on a scale, where performance is highest at the wine end and goes down to VB, and chance to work is highest at the VB end, and goes down to wine... (Of course 3d in VB is practically non-existant)

Dont even think of just installing wine, simply the ability to use different wine versions and have seperate prefixes makes playonlinux far far better than a plain old wine client...

You should be able to get a lot of games to work on playonlinux, and if not, tinkering is something you will learn soon enough :P

Haven't tried a game on wine yet that is completly unplayable (but dual boot is definitley best... scratch that, 2 PCs is definitely best :))

---

### Post by funkychild on 2010-01-23
> **J V said:**
> Performance and chance to work are on a scale, where performance is highest at the wine end and goes down to VB, and chance to work is highest at the VB end, and goes down to wine... (Of course 3d in VB is practically non-existant)

Dont even think of just installing wine, simply the ability to use different wine versions and have seperate prefixes makes playonlinux far far better than a plain old wine client...

You should be able to get a lot of games to work on playonlinux, and if not, tinkering is something you will learn soon enough :P

Haven't tried a game on wine yet that is completly unplayable (but dual boot is definitley best... scratch that, 2 PCs is definitely best :))

Hahaha...  Two PCs would definitely be best.  Unfortunately, that isn't going to happen in the near future.

I'm actually running Linux on a VirtualBox right now.  I'm a CS student and I wanted the experience of developing in a Linux environment.  However, Ubuntu seems great, so I'm trying to figure out exactly what I'd lose if I went full-fledged into Linux.

Thanks for the info.  Does anyone know a good spot to find Linux games online?

---

### Post by funkychild on 2010-01-23
Another question for you mad geniuses:

What about other applications?  Like I said, I'm trying to remove any reason for me not to make a complete switch (after all, I can just run Windows on a VB).  What about the following applications (do they have a Linux version or is there another program that is almost identical):

1) Adobe CS3

2) Nero

3) DivX

4) Power ISO

5) Skype

Thanks a million for all the help.  You folks rock!

---

### Post by llawwehttam on 2010-01-23
> **funkychild said:**
> Another question for you mad geniuses:

What about other applications?  Like I said, I'm trying to remove any reason for me not to make a complete switch (after all, I can just run Windows on a VB).  What about the following applications (do they have a Linux version or is there another program that is almost identical):

1) Adobe CS3

2) Nero

3) DivX

4) Power ISO

5) Skype

Thanks a million for all the help.  You folks rock!


1) Adobe CS3 (if you mean photoshop) --> GIMP

2) Nero --> [http://news.softpedia.com/news/Linux-version-of-Nero-released-742.shtml](http://news.softpedia.com/news/Linux-version-of-Nero-released-742.shtml)

3) DivX ( if you mean the player) --> VLC

4) Power ISO -->you can do this in ubuntu anyway with the archive manager

5) Skype -->linux versions in the repos

---

### Post by marshmallow1304 on 2010-01-23
> **llawwehttam said:**
> 5) Skype -->linux versions in the repos

Not anymore actually.  But it is available at the [website]("http://www.skype.com/download/skype/linux/choose/").

---

### Post by funkychild on 2010-01-24
What about K3B?  Is that good?  I'd basically be looking to use something like Nero Vision which will recode video files and burn them to DVD (so you'll make an actual DVD video out of your home movie AVI files).

---

### Post by PenguinInside on 2010-01-24
If you're just trying to figure out what you'd miss, I'd say absolutely nothing, unless you're addicted to specific Windows games.

If you just want some games to while your time, you can check out:

TORCS [http://torcs.sourceforge.net/](http://torcs.sourceforge.net/) (Racing game)
Nexuiz [http://www.alientrap.org/nexuiz/](http://www.alientrap.org/nexuiz/) (FPS game)

Also: Alien Arena, OpenArena, Sauerbraten, Tremulous, Warsow, and World of Padman.

---

### Post by aktiwers on 2010-01-24
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)
[http://wddb.wine-doors.org/downloads](http://wddb.wine-doors.org/downloads)

---

### Post by anaconda on 2010-01-24
> **funkychild said:**
> Another question for you mad geniuses:

What about other applications?  Like I said, I'm trying to remove any reason for me not to make a complete switch (after all, I can just run Windows on a VB).  What about the following applications (do they have a Linux version or is there another program that is almost identical):

1) Adobe CS3

2) Nero

3) DivX

4) Power ISO

5) Skype

Thanks a million for all the help.  You folks rock!

1) Adobe CS3 doesnt work properly with wine, but CS2 works very well. with a new version of wine (version 1.1.35). I have also heard that someone has succeeded in getting CS4 to work also.
Another way to run photoshop is by installing it in virtualbox..

2) K3b is good. And for ripping DVD:s etc. k9copy

3.) k9copy

---

### Post by funkychild on 2010-01-24
> **anaconda said:**
> 1) Adobe CS3 doesnt work properly with wine, but CS2 works very well. with a new version of wine (version 1.1.35). I have also heard that someone has succeeded in getting CS4 to work also.
Another way to run photoshop is by installing it in virtualbox..

2) K3b is good. And for ripping DVD:s etc. k9copy

3.) k9copy


Thanks.  It's more burning DVDs that would be playable in a DVD player.  Right now I can use Nero Vision to burn my home movies and play them on my TV.  Another thing I'd still like to be able to do is convert those same AVI files to play on my iPod Touch.

---

