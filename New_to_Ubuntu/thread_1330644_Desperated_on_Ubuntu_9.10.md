---
title: "Desperated on Ubuntu 9.10"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by Daudjan on 2009-11-18
Hello folks,


I have just installed Ubuntu and i am already desperated in using it :D. Actually im feel very confortable with Computers but there's a error which i cant understand

My Error:

Whatever I am trying to install or remove it says on the Terminal : E: package not found , no installation candidate


Is it maybe , because I installed a dual boot system and gave Ubuntu a 60GB Workspace?

---

### Post by Cheesemill on 2009-11-18
What packages are you trying to install/remove?
 
Make sure your package lists are up to date, either by going to Synaptic and clicking reload or by typing the following into a terminal:
```
 
sudo aptitude update

```

---

### Post by sisco311 on 2009-11-18
Did you try to install packages via the GUI (Applications -> Ubuntu Software Center or System -> Administration -> Synaptic Package Manager)

You may also have to enable the universe and multiverse repositories (System -> Administration -> Software Sources)

Oh, and please post the command you are trying to use in the terminal.

---

### Post by lgiordano on 2009-11-18
can you give some examples of the commands you are trying in the terminal?

---

### Post by Daudjan on 2009-11-18
Ok 


1st Command I was using is the one suggested by Cheesemilli. The Output:

```
 W: GPG error: http://download.tuxfamily.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
```The command that made me post this Thread : 

```
sudo apt-get install compiz-bcop compiz-dev compizconfig-settings-manager build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool
```


-D

---

### Post by QIII on 2009-11-18
How did you get tuxfamily in your sources list?

You can add a key, but I'll save that for later if you really want it.

For now, try going to System | Administration | Software Sources and deselecting the tuxfamily entry.

Then, in the terminal

```
sudo apt-get update
``````
sudo apt-get upgrade
```That will clean up your sources and get you up to date.

Then try the command you posted again.

---

### Post by Daudjan on 2009-11-18
Uhm i was searching how to activate all the Ubuntu Effects , cause i actually only have the usual Effekts like shaky windows etc.


Thatswhy i googled for compiz and found this site [here]("http://forum.compiz.org/showthread.php?t=5303")

Thatswhy i think i have the tuxfamily in my recources.


Now everything works fine Thanks,

but is there a tutorial how to enable all the effects on ubuntu?

I cant imagine a search term.


[]("http://forum.compiz.org/showthread.php?t=5303")

---

### Post by sisco311 on 2009-11-18
You have followed an outdated guide. Remove the tuxfamily repo, you don't need it. compiz-fusion is installed by default. Make sure that your video card driver is installed (System -> Administration -> Hardware Driver), then You can enable the effects from System - Preferences -> Appearance -> Visual Effects tab. If you need more configuration option, install conpizconfig-settings-manager.

---

### Post by sisco311 on 2009-11-18
> **Daudjan said:**
> Uhm i was searching how to activate all the Ubuntu Effects , cause i actually only have the usual Effekts like shaky windows etc.


Thatswhy i googled for compiz and found this site [here]("http://forum.compiz.org/showthread.php?t=5303")

Thatswhy i think i have the tuxfamily in my recources.


Now everything works fine Thanks,

but is there a tutorial how to enable all the effects on ubuntu?

I cant imagine a search term.


[]("http://forum.compiz.org/showthread.php?t=5303")

Just install [compizconfig-settings-manager  and compiz-fusion-plugins-extra.]("apt://compiz-fusion-plugins-extra,compiz-fusion-plugins-extra") (<- click to install, apturl link)

Then go to System -> Preferences -> CompizConfig Settings Manager to configure the effects.

---

### Post by QIII on 2009-11-18
I would like to add this to sisco:

This forum exists to help others.  In the future, we would be more than happy to steer you in the right direction -- this is a community effort and most of us understand that.  (You'll occasionally run into the odd jerk here.  Ignore them!)

Welcome to Ubuntu!  Don't be afraid to ask here first...

---

### Post by Daudjan on 2009-11-18
Thank you soo much , i really appreciate it , cause i had never any experience in other OS than Windows , but now I think i can really start up with a better system :D

---

### Post by Tholley on 2009-11-18
If you are new to Ubuntu, I think this is one of the best places to check out first.
 
[http://sites.google.com/site/easylinuxtipsproject/Home](http://sites.google.com/site/easylinuxtipsproject/Home)
 
 
hope you find this as helpful as I did a while back!

---

### Post by Tholley on 2009-11-18
Also... if you want to find out more about Compiz, I have found one can learn alot from these sites.
 
[http://my.opera.com/ubuntunerd1/blog/how-to-install-compiz-fusion-in-ubuntu-hardy](http://my.opera.com/ubuntunerd1/blog/how-to-install-compiz-fusion-in-ubuntu-hardy)
 
and
 
[http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion)
 
have fun!

---

