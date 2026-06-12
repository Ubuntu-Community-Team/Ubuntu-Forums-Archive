---
title: "ubuntu,kubuntu or xubuntu?"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by nitstorm on 2009-11-13
Wondering which I should opt for? Ubuntu, Kubuntu, or Xubuntu? And also which version is preferable for a total newbie. Basically looking to do some cool groovy desktop environment (would appreciate suggestions if any, like other than compiz or something), audio and video editing, plus a total newb so maybe learn how to do things with the terminal? oh yeah, also movies and music all the time, so..... 

My system config is:
Intel Core 2 Duo processor, 2.1 GHz, 
2GB of RAM
160 GB HDD
NO ADDITIONAL GRAPHICS CARD
and currently dual-booting with vista, but soon will be getting rid of the whole thing and be dual-booting with xp(jus so that i have something to go to wen i f@#$ up ubuntu, which happens all the time, lol)

---

### Post by kio_http on 2009-11-13
I'd say Kubuntu. it has the best interface and should run fine on your system. Also there are more issues with the latest Ubuntu karmic than Kubuntu karmic.

See screen shots at thecodingstudio.com

---

### Post by kio_http on 2009-11-13
Do you get aero with your graphic card on vista?

---

### Post by coldReactive on 2009-11-13
> **nitstorm said:**
> other than compiz or something)

Did you have a bad experience with it?

---

### Post by dragonboss on 2009-11-13
Ubuntu - General use and well balanced, Gnome desktop.
Kubuntu - More customisation and eyecandy, KDE desktop
Xubuntu - Less hardware requirements, XFCE desktop

---

### Post by coldReactive on 2009-11-13
> **dragonboss said:**
> Xubuntu - Less hardware requirements, XFCE desktop

It's been proven that Xubuntu takes up more RAM than Ubuntu.

---

### Post by Paqman on 2009-11-13
> **kio_http said:**
> Also there are more issues with the latest Ubuntu karmic than Kubuntu karmic.


I'm not sure there are. Most of the problems people seem to be having with Karmic are due to HAL dperecation, which is the same on both.

Just pick one and go for it Nitstorm. It's really easy to change later. Start with regular Ubuntu then try out the others:

[URL="http://www.psychocats.net/ubuntu/kde"]
How to install KDE[/URL]
[How to install XFCE]("http://www.psychocats.net/ubuntu/xfce")
[Comparison of Gnome/KDE]("http://www.psychocats.net/ubuntu/kdegnome")

---

### Post by jollysnowman on 2009-11-13
You can run any of those just fine on your system. Lots of ppl believe that KDE is the best for flashy things, but I can do lots of similar stuff with xfce+compiz on my laptop.

> **coldReactive said:**
> It's been proven that Xubuntu takes up more RAM than Ubuntu.

Furthermore, if you look at [http://xubuntu.org/about](http://xubuntu.org/about) it doesn't actually say Xubuntu is meant for slower/older computers (although I did choose it for my iMac G3). I do think that Xubuntu's a little easier to slim down than the others, though.

---

### Post by coldReactive on 2009-11-13
> **jollysnowman said:**
> Furthermore, if you look at [http://xubuntu.org/about](http://xubuntu.org/about) it doesn't actually say Xubuntu is meant for slower/older computers (although I did choose it for my iMac G3). I do think that Xubuntu's a little easier to slim down than the others, though.

Or you could just install the barebones xfce4 metapackage from the mini.iso.

Then build/remove stuff from there.

---

### Post by nitstorm on 2009-11-13
wow! thanks for the help, will tweak around with some stuff and get back to u soon.
not sure what the aero effect of vista is...
and compiz, i added the water effect and once i clicked something, there were black patches on all the toolbars and stuff and ubuntu jus crashed, so with the help of a user called durant here on the forums i cleared compiz outta the system using the terminal. had to uninstall everything using sudo aptitude something...

so is there any substitute for compiz or is compiz the only thing to go?
also can i display the kde apps on on toolbar and use another toolbar to display the gnome apps?? i mean like the drop-down menu... thanks in advance :)

---

### Post by dragonboss on 2009-11-13
You could simply edit the menus by right click in gnome and hide all the KDE apps from the menu. About a compiz altenative, not sure since it always worked for me.

There is an alternative called Xcompmgr

---

### Post by jrandolph on 2009-11-13
> **nitstorm said:**
> 
My system config is:
Intel Core 2 Duo processor, 2.1 GHz, 
2GB of RAM
160 GB HDD
NO ADDITIONAL GRAPHICS CARD


> **kio_http said:**
> Do you get aero with your graphic card on vista?

Have you got onboard graphics?
I think it will be hard going if your trying to do "flashy" or "groovy" things with out a video card - only speaking from experience

---

### Post by sandy8925 on 2009-11-13
What kind of video card do you have ? If it's Intel it might not work so well since Intel cards suck. You can use whichever you want(Ubuntu,Kubuntu or Xubuntu) it's your choice. Your system can handle any of them so need to worry about that. Using compiz however depends on what your onboard graphics card is. 

In my opinion Kubuntu is a great desktop environment. It has great eyecandy and some good ideas (such as having the desktop icons inside a folder widget,photo frames etc.) so probably the best one to use for making a great-looking desktop.

---

### Post by nitstorm on 2009-11-13
followed the link given by Paqman earlier, and downloading the kubuntu desktop thing using  the synaptic package manager,has appromixately 50 mins more to go.. yup i guess there is some onboard graphics card since i've played a few games like F.E.A.R. and all that on this comp earlier... so there should be something is my guess.. 
will keep u posted with how the kde installation goes once it gets downloaded, cheers!

---

### Post by jrandolph on 2009-11-13
> **nitstorm said:**
> followed the link given by Paqman earlier, and downloading the kubuntu desktop thing using  the synaptic package manager,has appromixately 50 mins more to go.. yup i guess there is some onboard graphics card since i've played a few games like F.E.A.R. and all that on this comp earlier... so there should be something is my guess.. 
will keep u posted with how the kde installation goes once it gets downloaded, cheers!

When you get it up and going...

```
lspci | grep VGA
```

this will give you the output of your graphics card 
Not a bad thing to know - especially if you are having problems

---

### Post by bwzz on 2009-11-13
I'm still new here, and I would like to ask about ubuntu studio [http://ubuntustudio.org/](http://ubuntustudio.org/)
is it an advanced desktop environment? or KDE? or is it only for multimedia editing?

---

### Post by nitstorm on 2009-11-13
> **jrandolph said:**
> When you get it up and going...

```
lspci | grep VGA
```

this will give you the output of your graphics card 
Not a bad thing to know - especially if you are having problems

jus got it up and running, seems ok, gotta tweak around more though, this is the output i got for that code :
```

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

```

so, everything's cool right? ill keep u posted if i encounter some problem. thanks a mil guys.

also curious to know answers regarding bwzz's question..

---

### Post by Sef on 2009-11-13
Ubuntu is the best way to start since most people here use it.

---

### Post by arnab_das on 2009-11-13
here's my take:

Ubuntu -  the easiest and the best.
Kubuntu - potentially far better than GNOME/Ubuntu but implementation is horrendous!
Xubuntu - Light weight.

I'm currently using Ubuntu but thanks to project timelord which promises loads of changes, i'll move to kubuntu after the 10.10 release.

---

### Post by nitstorm on 2009-11-13
ok i got the kde thing going on well, but how do i play with the compiz thing in it, was so much more easier on gnome, here i get to only either set it to none, standard, extra or custom, now i click on custom, but what do i do to customize it???

---

### Post by Merk42 on 2009-11-13
> **bwzz said:**
> I'm still new here, and I would like to ask about ubuntu studio [http://ubuntustudio.org/](http://ubuntustudio.org/)
is it an advanced desktop environment? or KDE? or is it only for multimedia editing?

It's GNOME. With a lot of preinstalled programs focusing on multimedia development.

---

### Post by arnab_das on 2009-11-13
> **nitstorm said:**
> ok i got the kde thing going on well, but how do i play with the compiz thing in it, was so much more easier on gnome, here i get to only either set it to none, standard, extra or custom, now i click on custom, but what do i do to customize it???

i personally dont think u require compiz if ur using kde. anyway the settings in compiz are pretty simple. activate the following:
desktop cube, rotate cube, 3D windows, cube deformation and ur all set! :)

---

### Post by nitstorm on 2009-11-13
> **nitstorm said:**
> ok i got the kde thing going on well, but how do i play with the compiz thing in it, was so much more easier on gnome, here i get to only either set it to none, standard, extra or custom, now i click on custom, but what do i do to customize it???

ofcourse, dumb me, had to install ccsm :P he he... but then i didnt like kde much, gnome is best for me :D love you gnome , u rock :D
Thanks all u guys for helping me out :D cheers :D

---

### Post by UbuntoJO on 2009-11-23
I prefer Xubuntu simply because I can make it look better than Ubuntu....it's not a featherweight anymore, but the Karmic x64 version flys on this little Vostro 1220.

---

### Post by XubuRoxMySox on 2009-11-23
> **coldReactive said:**
> It's been proven that Xubuntu takes up more RAM than Ubuntu.

I don't believe that is true any longer (yes, it used to be), but on the OP's 'puter it certainly wouldn't matter.

Linus is *supposed* to put the RAM to work and load a bunch of stuff into it. That's why it's so snappy and quick. 

It ain't the Xfce desktop environment that "uses more resources," it's the default *applications* that determine resource requirements. Xubuntu Karmic runs at near transwarp speed on my 5-year-old Dell with less that half of the resources of the OP's machine.

-Robin

---

### Post by garikaib on 2009-11-23
You can begin with Ubuntu. I just prefer it.

---

