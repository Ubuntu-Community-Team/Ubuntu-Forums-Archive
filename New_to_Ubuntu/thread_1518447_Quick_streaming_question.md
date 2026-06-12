---
title: "Quick streaming question"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by adobrakic on 2010-06-26
So I'm trying to see how Ghana's going to kick the US out of the world cup on [ESPN's website](http://espn.go.com/espn3/player), which all works fine until you click full-screen. The actual video is scrunched up into a 2 x 10-or-so box, causing me to see pretty much nothing. 

I'll post a picture if other's aren't experiencing the same issue. Any suggestions?

---

### Post by -kg- on 2010-06-26
I'm thinking that "2 X 10" is the actual size of the video.  I've had that same issue with some streaming videos that I've viewed.  You can increase the size of the display, but you can't always stretch the size of the video.

Try finding another source of the video and try it with that.  Of course, that might be hard to do, considering the source, the material, and the fact that it's probably live.

I'll try to view the video source and see what I come up with.

):P <waving at you from across the river!> :D

---

### Post by -kg- on 2010-06-26
OK, my apologies.  I pulled up the video and expanded it, and it expanded to near full screen for me, so you're having a legitimate problem.

May I assume that you have "ubuntu-restricted-extras" (with the Adobe Flash Player) installed, or do you have the swfdec/Gnash player?  I've found that swfdec and Gnash don't always work right with some of the current streaming video formats.  If you have that installed, I would suggest that you uninstall it and install "ubuntu-restricted-extras" for the Adobe player.

If it isn't that, hopefully someone else will come along with a better solution, because I wouldn't have any ideas.  "ubuntu-restricted-extras" have always worked perfectly once installed...well, except when some site or another requires the newest flash player and Adobe hasn't updated it for Linux yet!

---

### Post by adobrakic on 2010-06-26
> OK, my apologies. I pulled up the video and expanded it, and it expanded to near full screen for me, so you're having a legitimate problem.

Damnit, I was afraid of this being an only-me thing. :p

I took screens of normal vs full screen:
- [normal](http://img121.imageshack.us/img121/9357/screenshotbtt.png)
- [fullscreen](http://img52.imageshack.us/img52/1949/screenshot1rl.png)

> May I assume that you have "ubuntu-restricted-extras" 

```
ado@ado-laptop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ado@ado-laptop:~$ 

```

> with the Adobe Flash Player) installed,

Is this the flashplugin64-installer package? If so, then yes i do.

---

### Post by warfacegod on 2010-06-26
I have to disable Compiz before I can *any* video to go fullscreen. Either streaming or video that I have on my HDD, it doesn't matter, Compiz must be off.

If this turns out to be the case with you then google "Compiz Switch". A highly useful thing to have on ones panel. (Especially last month when I accidentally told CompizConfig to turn my entire desktop environment invisible. SHH! Don't tell anybody, I'll never live it down.)

---

### Post by adobrakic on 2010-06-26
In CCSM, under general, I have the setting to automagically turn off compiz in full-screen. However, I also have the "Compiz Fusion Icon" in my panel, and switched to Metacity. The problem in full-screen still occured. Should I still try Compiz Switch?

---

### Post by nhasian on 2010-06-26
you can check if a package is installed with the command *apt-cache policy*  for example

```
apt-cache policy flashplugin-nonfree
```

are you using ubuntu 32 or 64bit?

```
uname -a
```

if you are using ubuntu 64bit then i would uninstall the 32bit flash that comes with ubuntu-restricted-extras as well as the nspluginwrapper and grab the latest 64bit flash from adobe labs.

---

### Post by adobrakic on 2010-06-26
With apt-cache policy, it says:

```
ado@ado-laptop:~$ apt-cache policy flashplugin-nonfree
flashplugin-nonfree:
  Installed: (none)
  Candidate: 10.1.53.64ubuntu0.10.04.2
  Version table:
     10.1.53.64ubuntu0.10.04.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/multiverse Packages
     10.1.53.64ubuntu0.10.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Packages
        500 http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Packages
     10.0.45.2ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Packages
ado@ado-laptop:~$ 


```

Should I install flashplugin-nonfree? 

Also, I'm using 64-bit, but for reassurance:

```
ado@ado-laptop:~$ uname -a
Linux ado-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
ado@ado-laptop:~$ 

```

> if you are using ubuntu 64bit then i would uninstall the 32bit flash that comes with ubuntu-restricted-extras as well as the nspluginwrapper and grab the latest 64bit flash from adobe labs.

I'm not good at all with manually installing packages, so if I have to do that I'm afraid I most likely will run into more problems. :x

---

### Post by warfacegod on 2010-06-26
> **adobrakic said:**
> In CCSM, under general, I have the setting to automagically turn off compiz in full-screen. However, I also have the "Compiz Fusion Icon" in my panel, and switched to Metacity. The problem in full-screen still occured. Should I still try Compiz Switch?

If Compiz is the culprit, a one time way to find out is to set Visual Effects to None, under Appearances.

Don't discount flash-plugin being the problem though. It's probably much more likely to be the issue.

---

### Post by nhasian on 2010-06-27
actually installing flash is really simple.  you download file, extract it and move the contents (which is just one file libflashplayer.so) to /usr/lib/mozilla/plugins/libflashplayer.so

then restart firefox.  thats it.  oh make sure you remove the previous flash first.  dont want to have them conflicting...

> **adobrakic said:**
> I'm not good at all with manually installing packages, so if I have to do that I'm afraid I most likely will run into more problems. :x

---

### Post by adobrakic on 2010-06-27
> oh make sure you remove the previous flash first. dont want to have them conflicting...

You mind helping me with this? I'm not really sure what the previous flash player is. In about:plugins, it says the following:

> Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r45

Does that mean I'll just have to overwrite the current libflashplayer.so and I'll be fine?

---

### Post by nhasian on 2010-06-27
step by step instructions are here: [http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html](http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html)

---

### Post by adobrakic on 2010-06-27
is there a mirror for the "flashplayer10_install_linux_051508.tar.gz" download? the link in the tutorial is dead, and i couldn't find anything on google.

---

