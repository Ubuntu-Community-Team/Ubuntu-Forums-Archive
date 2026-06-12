---
title: "Which Version Of Ubuntu Should i Use?"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by lenswipe on 2007-12-17
Hi there

i have ubuntu 7.1 gutsy gibbon but i want to upgrade my desktop PC to ubuntu 7.1 Gutsy SERVER. Im not sure though whether this would have any benefits.

Any ideas?

i have 2 laptops and a desktop (this is to become the server)

im getting another computer soon too.....

what version of ubuntu should i have?

---

### Post by Chachee on 2007-12-17
Well..
  It depends.  What are you doing to use the desktop for?  Most of the packages you can get through the normal ubuntu install anyway.

  I've played around with server a little at home and didn't really feel like I needed it for home networking.

JT

---

### Post by Junglizer on 2007-12-17
It doesn't really matter but I would say the server edition just b/c you can actually change the installation a bit more for your needs. However, if you're of the "no gui? wtf? thats gay." persuasion just stick with the desktop version, no need to try and figure out fdisk if you don't plan on taking advantage of the CLI opts durring the install.

---

### Post by lenswipe on 2007-12-17
> **Junglizer said:**
> It doesn't really matter but I would say the server edition just b/c you can actually change the installation a bit more for your needs. However, if you're of the "no gui? wtf? thats gay." persuasion just stick with the desktop version, no need to try and figure out fdisk if you don't plan on taking advantage of the CLI opts durring the install.

so is there no GUI with the ubuntu server edition??

also can i get things like samba and a domain controlled thru synaptic in desktop edition?

---

### Post by lvleph on 2007-12-17
There is no GUI but it can be installed.
```
apt-get install gnome-desktop
```
And then you will have a GUI.

Oh and it is 7.10.

---

### Post by lenswipe on 2007-12-17
> **lvleph said:**
> There is no GUI but it can be installed.
```
apt-get install gnome-desktop
```
And then you will have a GUI.

Oh and it is 7.10.

kk cool ill think about it :)

---

### Post by aysiu on 2007-12-17
Isn't it ```
sudo apt-get install gnome-desktop-environment
``` or ```
sudo apt-get install gnome-core
``` or ```
sudo apt-get install ubuntu-desktop
```?

---

### Post by Lostincyberspace on 2007-12-17
The third of Ayisu's is the correct to type in. or you could make a bash script and have it install without having to remember what to type in. This is what I do when I need to do some thing where i can't just copy and paste.

---

### Post by Junglizer on 2007-12-18
> **aysiu said:**
> Isn't it ```
sudo apt-get install gnome-desktop-environment
``` or ```
sudo apt-get install gnome-core
``` or ```
sudo apt-get install ubuntu-desktop
```?

What if you're root? Then you don't need sudo at all. And if it is going to be a server, running without X.org is nice. Saves resources.

---

### Post by lswest on 2007-12-18
just so you guys know, GNOME isn't the only WM you can install, and i know for a fact most servers usually stick with lower-end WMs (of 6 of the people i know who own Linux servers only 1 uses GNOME on his server).  My server (runs on some ancient compaq with Ubuntu Feisty server edition) actually runs with fluxbox&enlightenment...all the other ones i feel comfortable with were just too slow.  Generally you can install any WM, just for enlightenment you need another repository, and fluxbox is in the repos too.  Might help if your PC is a little slower.  and about the server or desktop thing...might be best to do a fresh install, as you might have packages you don't necessarily need in the desktop thing, and so a fresh install would let you just stick to the few things you need.

---

### Post by aysiu on 2007-12-18
> **Junglizer said:**
> What if you're root? Then you don't need sudo at all. And if it is going to be a server, running without X.org is nice. Saves resources.
Why would you be root?

Of course running without Xorg would be nice, but I was just correcting someone who said to install *gnome-desktop*--a non-existent metapackage, as far as I know.

Personally, I think if you're going to put a graphical frontend on a server, IceWM is a better choice than Gnome.

---

### Post by Lostincyberspace on 2007-12-18
> **lswest said:**
> just so you guys know, GNOME isn't the only WM you can install, and i know for a fact most servers usually stick with lower-end WMs (of 6 of the people i know who own Linux servers only 1 uses GNOME on his server).  My server (runs on some ancient compaq with Ubuntu Feisty server edition) actually runs with fluxbox&enlightenment...all the other ones i feel comfortable with were just too slow.  Generally you can install any WM, just for enlightenment you need another repository, and fluxbox is in the repos too.  Might help if your PC is a little slower.  and about the server or desktop thing...might be best to do a fresh install, as you might have packages you don't necessarily need in the desktop thing, and so a fresh install would let you just stick to the few things you need.
I also use gnome on my servers. nice to use some thing familiar in area that can be problematic at times.

---

### Post by lswest on 2007-12-18
true, but fluxbox and enlightenment wasnt really new for me when i installed them, so i wasnt that worried about it.  Also, how else to become accustomed to it other than using it? i was just suggesting

---

### Post by Junglizer on 2007-12-19
> **aysiu said:**
> Why would you be root?

Of course running without Xorg would be nice, but I was just correcting someone who said to install *gnome-desktop*--a non-existent metapackage, as far as I know.

Personally, I think if you're going to put a graphical frontend on a server, IceWM is a better choice than Gnome.

Why wouldn't you be root? at least for the install, granted, not everyone can do the "ideal" server install, as in have offline networked repos, as to not compromise the system before it has time to patch. Ice is nice *rhymes, heh* but even TWM would suffice in most cases.

The problem with full desktop GUIs is that the built-in apps, to say, configure DNS, don't write to the same files that you would access to do it from the command line, or ncurses based app. This is a huge problem, and why the best thing to do is to not run a gui at all, or if you do, don't actually log into it.

```
 root@box~# vi /etc/inittab
```
Set default run-level to 3, save, restart if you feel like it.

---

### Post by aysiu on 2007-12-19
> **Junglizer said:**
> Why wouldn't you be root? There are a lot of reasons. You can read about them here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> 
The problem with full desktop GUIs is that the built-in apps, to say, configure DNS, don't write to the same files that you would access to do it from the command line, or ncurses based app. This is a huge problem, and why the best thing to do is to not run a gui at all, or if you do, don't actually log into it.

```
 root@box~# vi /etc/inittab
```
Set default run-level to 3, save, restart if you feel like it. Of course you can write the same files. How is ```
sudo vi /etc/inittab
``` different from ```
gksudo gedit /etc/inittab
``` anyway?

---

### Post by Junglizer on 2007-12-19
> **aysiu said:**
> There are a lot of reasons. You can read about them here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

 Of course you can write the same files. How is ```
sudo vi /etc/inittab
``` different from ```
gksudo gedit /etc/inittab
``` anyway?

Yes, I am fully aware of the uses of Sudo, however that was supposed to be a light remark and for the record, I usually write my **root@box~#** as root so that other readers will hopefully make the connection that the command needs to be done with root permissions, how they do it is up to them. Likewise, aside from the server aspect, running as root is perfectly fine, assuming you're the only one that has access to your system.

---

### Post by lswest on 2007-12-19
well quick comment from me, i find vim a bit better than vi (i know, not much difference) but for me vi always seems to not respond to 50% of the commands i give in...

---

### Post by Junglizer on 2007-12-19
So do I, but most newer systems auto-alias vim to vi, but I can use either.

---

### Post by Junglizer on 2007-12-19
As long as its not emacs, good lord *"you can even use it to brows the web!"*, oh please, I don't want to browse the @#$! web, I just want to edit a freakin' text file.

---

### Post by lenswipe on 2007-12-20
> **aysiu said:**
> Why would you be root?

Of course running without Xorg would be nice, but I was just correcting someone who said to install *gnome-desktop*--a non-existent metapackage, as far as I know.

Personally, I think if you're going to put a graphical frontend on a server, IceWM is a better choice than Gnome.

so whats the command to install IceWM???


*interested*

also will it work with ubuntu desktop as i switched  back to that after using server for a whole 24 Hours and not finding any real difference....


also is it possible to have ubuntu as a domain controller??

if so i would be very interested to know how this is done.....

---

### Post by aysiu on 2007-12-20
> **lenswipe said:**
> so whats the command to install IceWM???


*interested* This link will help you:
[http://www.psychocats.net/ubuntu/icewm](http://www.psychocats.net/ubuntu/icewm)

> also will it work with ubuntu desktop as i switched  back to that after using server for a whole 24 Hours and not finding any real difference.... Yes. See the above link.

> also is it possible to have ubuntu as a domain controller??

if so i would be very interested to know how this is done..... I don't know what a domain controller is.

---

