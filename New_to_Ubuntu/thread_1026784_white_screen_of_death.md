---
title: "white screen of death"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by marcusesses on 2008-12-31
So a few days ago I ran 

```
sudo apt-get update
```

And shortly thereafter, I was presented with the WSOD upon logging in. I logged in using failsafe GNOME, and except for a few minor gui bugs, things seemed to be ok.

Yesterday, I went to the update manager, and made some more updates (there were quite a few packages to install). Now, I get the WSOD every time I log in. I'm currently using 8.04.

I've started a few threads of problems leading up to this (look at some of my recent posts for this), but they've all stagnated. Does anyone recognize this problem, or have any idea what's going on?

---

### Post by stoogiebuncho on 2008-12-31
I'm not very knowledgeable about this, but I'll ask a few questions to get things started.

Any idea what the updates were?

What sort of graphics card do you have and what driver are you using?

---

### Post by marcusesses on 2008-12-31
> **stoogiebuncho said:**
> I'm not very knowledgeable about this, but I'll ask a few questions to get things started.

Any idea what the updates were?
Not specifically....when I ran suod apt-get update, it said it looked in the multi-verse and universe packages, but it only took about 15 seconds to update (if it updated at all).

When I ran the update last night, it updated a lot of libraries, and some packages (I sort of just let it run and went to sleep, so I don't know specifically). 

After the update, I had the intrepid wallpaper on my desktop though. When I rebooted, that's when the trouble started.

> What sort of graphics card do you have and what driver are you using?

```
00:02.0 VGA compatible controller: Intel Corporation 
Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```

Intel Graphics Media Accelerator (GMA) X3100 - MB, Core: 500 MHz, 7.14.10.1329 (helpful?)

---

### Post by abn91c on 2008-12-31
turn off desktop effect should take care of WSOD, you may have to remove compiz altogether, it seems to have issues with the Intel video in 8.10

---

### Post by marcusesses on 2008-12-31
> **abn91c said:**
> turn off desktop effect should take care of WSOD, you may have to remove compiz altogether, it seems to have issues with the Intel video in 8.10



My compiz config file contains

```
[gnome_session]
profile = 
plugin_list_autosort = true
```


Is it a good idea to remove compiz altogether?  I wouldn't have any desktop effects then...

Also this may be related, but before the updates that ultimately destroyed my desktop, I could only access 2 desktops (I usually have 4)...

---

### Post by abn91c on 2008-12-31
look at the compiz forum, you may have to live without the cube, you can always get some other eye candy like cairo dock or screenlets

---

### Post by marcusesses on 2008-12-31
> **abn91c said:**
> look at the compiz forum, you may have to live without the cube, you can always get some other eye candy like cairo dock or screenlets

I don't use the cube though...I DO have multiple desktops, like I mentioned, but I just scroll through them if I need them. I really don't have much use for fancy desktop graphical features, so I could probably do without multiple desktops, if it will fix my problem....

But why would I have compiz then? I haven't installed it intentionally or anything, I scroll through my desktops using a simple 2d interface...wierd (this is probably tangent to my problem, but...)

If it helps, here are the contents of my .config directory

```

/compiz
/gtk-2.0
/totem
/tracker
Trolltech.conf
user-dirs.dirs
user-dirs.locale

```

---

### Post by markharding557 on 2008-12-31
compiz is installed and enabled by default in ubuntu so you have to turn it off or even remove it if you don't want it.
i regard it as pointless eye candy myself

---

### Post by marcusesses on 2008-12-31
> **markharding557 said:**
> compiz is installed and enabled by default in ubuntu so you have to turn it off or even remove it if you don't want it.
i regard it as pointless eye candy myself


I agree. But if I remove compiz, will that solve my WSOD problem, or will it potentially cause much graver problems in the future?

Also, will I still be able to scroll between virtual desktops?

---

### Post by abn91c on 2009-01-01
removing compiz will not do anything harmful, log out after you do and restart the X server. no sure about the scrolling part I only use 2 desktops

---

### Post by joshmuffin on 2009-01-01
I'm pretty sure if you uninstall compiz you will still have multiple desktops. And the reason you now have 2 is because that is the default in 8.10 intrepid ibex (which it appears you upgraded to). 

You can change it back to for by right clicking the workspace changer thing in the bottom right hand corner then click preferences.

P.S If you loose multiple desktops you could reinstall compiz (the problem might be compiz is corrupt)

I hope this helped, Joshmuffin :)

---

