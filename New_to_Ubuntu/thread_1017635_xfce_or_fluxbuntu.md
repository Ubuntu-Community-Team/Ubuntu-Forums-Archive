---
title: "xfce or fluxbuntu?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-12-21
im looking to boos the efficiency of my laptop. im trying to figure which to use. which would be better? more visually appealing? etc

---

### Post by w4ett on 2008-12-21
If you have been using Gnome, Xfce will be easier for you.  I Like Flux, but it takes a lot of tweaking to get it like you want it.....My question is though,, Why not install both and...Flux on top of Xubuntu...then you can select at login, play with both, then decide which to be your default GUI. :)

---

### Post by PatrickMoore on 2008-12-21
> **w4ett said:**
> If you have been using Gnome, Xfce will be easier for you.  I Like Flux, but it takes a lot of tweaking to get it like you want it.....My question is though,, Why not install both and...Flux on top of Xubuntu...then you can select at login, play with both, then decide which to be your default GUI. :)

i could do that. i love gnome i just want to see if i can enhance my performance. fluxbox seems prettier one i play with it. is it as easy to configure as say conky?

---

### Post by snowpine on 2008-12-21
> **PatrickMoore said:**
> im looking to boos the efficiency of my laptop. im trying to figure which to use. which would be better? more visually appealing? etc

Hi Patrick, 
Is your goal to install a new windows manager on top of your existing install, or to do a new install from scratch?

You can add Xfce as a windows manager to any existing install with the command 'sudo apt-get install xubuntu-desktop' or 'sudo apt-get install xfce4' (depending on whether you want the pre-configured Xubuntu experience or just the core packages to tweak to your liking). Then, log out, and select the Xfce session from the login screen. In my experience, switching from Ubuntu to Xubuntu is about a 10% boost in performance. You can also install an Xfce distro from scratch, Xubuntu is the Ubuntu version, but there are others, for example Debian Xfce is a very fast and stable distro.

You can't add Fluxbuntu over an existing install, as it is a complete (and obsolete) distro. You can however add Fluxbox (the windows manager used by Fluxbuntu) to your existing install with 'sudo apt-get install fluxbox'. Fluxbox is very fast, geeky, and tweakable. It's really easy to configure by editing text configuration files; if you like to configure your system with point and click graphical interface, Fluxbox is not for you.

I would also recommend giving Openbox a try. It is similar to Fluxbox but I just like its "vibe" a bit more. You can install it over Ubuntu with 'sudo apt-get install openbox' or try an Openbox distro (if you're doing a fresh install) like my personal favorite distro, Crunchbang. Highly recommended.

Honorable mention goes to LXDE. 'sudo apt-get install lxde' gives you a desktop environment that's basically pre-configured Openbox with menu, panels, icons, etc. It's probably the easiest way to go if you like Fluxbox/Openbox but don't want any configuration hassles and don't want to do a fresh install.

Good luck!

---

### Post by PatrickMoore on 2008-12-21
> **snowpine said:**
> Hi Patrick, 
Is your goal to install a new windows manager on top of your existing install, or to do a new install from scratch?

You can add Xfce as a windows manager to any existing install with the command 'sudo apt-get install xubuntu-desktop' or 'sudo apt-get install xfce4' (depending on whether you want the pre-configured Xubuntu experience or just the core packages to tweak to your liking). Then, log out, and select the Xfce session from the login screen. In my experience, switching from Ubuntu to Xubuntu is about a 10% boost in performance. You can also install an Xfce distro from scratch, Xubuntu is the Ubuntu version, but there are others, for example Debian Xfce is a very fast and stable distro.

You can't add Fluxbuntu over an existing install, as it is a complete (and obsolete) distro. You can however add Fluxbox (the windows manager used by Fluxbuntu) to your existing install with 'sudo apt-get install fluxbox'. Fluxbox is very fast, geeky, and tweakable. It's really easy to configure by editing text configuration files; if you like to configure your system with point and click graphical interface, Fluxbox is not for you.

I would also recommend giving Openbox a try. It is similar to Fluxbox but I just like its "vibe" a bit more. You can install it over Ubuntu with 'sudo apt-get install openbox' or try an Openbox distro (if you're doing a fresh install) like my personal favorite distro, Crunchbang. Highly recommended.

Honorable mention goes to LXDE. 'sudo apt-get install lxde' gives you a desktop environment that's basically pre-configured Openbox with menu, panels, icons, etc. It's probably the easiest way to go if you like Fluxbox/Openbox but don't want any configuration hassles and don't want to do a fresh install.

Good luck!

i want a completely fresh install. i went to the flxbuntu site and was disapointed to see the latest stable was 7.10 which was a disaster of an install i want 8.10 if possible since it was brutally easy to get running

---

### Post by PatrickMoore on 2008-12-21
> **snowpine said:**
> Hi Patrick, 
Is your goal to install a new windows manager on top of your existing install, or to do a new install from scratch?

You can add Xfce as a windows manager to any existing install with the command 'sudo apt-get install xubuntu-desktop' or 'sudo apt-get install xfce4' (depending on whether you want the pre-configured Xubuntu experience or just the core packages to tweak to your liking). Then, log out, and select the Xfce session from the login screen. In my experience, switching from Ubuntu to Xubuntu is about a 10% boost in performance. You can also install an Xfce distro from scratch, Xubuntu is the Ubuntu version, but there are others, for example Debian Xfce is a very fast and stable distro.

You can't add Fluxbuntu over an existing install, as it is a complete (and obsolete) distro. You can however add Fluxbox (the windows manager used by Fluxbuntu) to your existing install with 'sudo apt-get install fluxbox'. Fluxbox is very fast, geeky, and tweakable. It's really easy to configure by editing text configuration files; if you like to configure your system with point and click graphical interface, Fluxbox is not for you.

I would also recommend giving Openbox a try. It is similar to Fluxbox but I just like its "vibe" a bit more. You can install it over Ubuntu with 'sudo apt-get install openbox' or try an Openbox distro (if you're doing a fresh install) like my personal favorite distro, Crunchbang. Highly recommended.

Honorable mention goes to LXDE. 'sudo apt-get install lxde' gives you a desktop environment that's basically pre-configured Openbox with menu, panels, icons, etc. It's probably the easiest way to go if you like Fluxbox/Openbox but don't want any configuration hassles and don't want to do a fresh install.

Good luck!

i want a completely fresh install. i went to the flxbuntu site and was disapointed to see the latest stable was 7.10 which was a disaster of an install i want 8.10 if possible since it was brutally easy to get running

---

### Post by snowpine on 2008-12-21
> **PatrickMoore said:**
> i want a completely fresh install. i went to the flxbuntu site and was disapointed to see the latest stable was 7.10 which was a disaster of an install i want 8.10 if possible since it was brutally easy to get running

Yes, that's why I said Fluxbuntu is obsolete, or at least it will be in April when Gutsy reaches end-of-life. :) And 7.10 isn't "stable" but rather a buggy "release candidate." Too bad, because I really liked Fluxbuntu when I discovered it. 

If you are doing a fresh install, I can't recommend Crunchbang highly enough: [http://www.crunchbanglinux.org](http://www.crunchbanglinux.org)

It is based on 8.10 (there is also an 8.04 version). The regular version is very fast, and the lite version ([http://crunchbanglinux.org/forums/topic/219/crunchbang-linux-81001rc1-lite-edition/](http://crunchbanglinux.org/forums/topic/219/crunchbang-linux-81001rc1-lite-edition/)) is super fast. 

Try it as a live CD, see if you like it...

---

### Post by w4ett on 2008-12-21
Do an 8.10 Xubuntu install, then:

```
sudo apt-get install fluxbox
```

---

### Post by PatrickMoore on 2008-12-21
how is puppy linux? does it have a good community? one of the things that has made the transistion to linux simple and painless was the ubuntu forums (thanks guys) i dont want to lose that as every once in a while i get some ridiculous situation in which another brain is needed

---

### Post by snowpine on 2008-12-21
> **PatrickMoore said:**
> how is puppy linux? does it have a good community? one of the things that has made the transistion to linux simple and painless was the ubuntu forums (thanks guys) i dont want to lose that as every once in a while i get some ridiculous situation in which another brain is needed

I am typing this message in Puppy right now, by coincidence. :) It is incredibly fast compared to anything in the Ubuntu family (including Crunchbang and Fluxbuntu). It also has the advantage of not needing a traditional "full" install, since it is small enough to run equally well from CD, live USB, or frugal install. Finally, it will run on a lot of old computers that don't have a prayer of handling even a minimalistic Ubuntu installation. The biggest downsides in my opinion are 1) doesn't have nearly the application selection of an Ubuntu or Debian system; 2) you're always root.

I've not had opportunity to post on their forums, but I have found some good advice using the search function (such as how to get it running on my eee).

Another favorite distro of mine, that's even lighter than Puppy, is the openbox-based SliTaz. But the OP seems like an Ubuntu user, which is why my previous suggestion (Crunchbang) is Ubuntu-based.

---

### Post by PatrickMoore on 2008-12-21
> **snowpine said:**
> I am typing this message in Puppy right now, by coincidence. :) It is incredibly fast compared to anything in the Ubuntu family (including Crunchbang and Fluxbuntu). It also has the advantage of not needing a traditional "full" install, since it is small enough to run equally well from CD, live USB, or frugal install. Finally, it will run on a lot of old computers that don't have a prayer of handling even a minimalistic Ubuntu installation. The biggest downsides in my opinion are 1) doesn't have nearly the application selection of an Ubuntu or Debian system; 2) you're always root.

I've not had opportunity to post on their forums, but I have found some good advice using the search function (such as how to get it running on my eee).


Another favorite distro of mine, that's even lighter than Puppy, is the openbox-based SliTaz. But the OP seems like an Ubuntu user, which is why my previous suggestion (Crunchbang) is Ubuntu-based.

puppy linux is under 100mbs!!! which is ridiculous, ridiculously awesome that is. i may try that was wireless a poor experience? ubuntu 8.10 was so easy to set up.

---

### Post by snowpine on 2008-12-21
Puppy has excellent wireless detection (better than Ubuntu, in my opinion). Wireless did not work on my eee at first, but I found a post on their forums with an updated driver that only took 1 click to install.

Puppy is great for old or slow hardware, I would definitely recommend it over anything in the Ubuntu family if you have, for example, less than a pentium 3 with 256mb of ram. I do not personally run it as an everyday os for the reasons mentioned above (lack of applications, always the root user), but it is a fun diversion. Best part as I mentioned is you don't have to get rid of your ubuntu install to use it; you can just run it from CD or do a frugal install.

---

### Post by snowpine on 2008-12-21
I just noticed your sig (2gb ram, 64bit); is that the computer you're thinking of switching to puppy on??? You should be able to run Ubuntu easily on those specs... if it's slow, there must be some sort of problem. :)

---

### Post by PatrickMoore on 2008-12-21
> **snowpine said:**
> I just noticed your sig (2gb ram, 64bit); is that the computer you're thinking of switching to puppy on??? You should be able to run Ubuntu easily on those specs... if it's slow, there must be some sort of problem. :)

ubuntu runs fine, i just wanted a change of enviroment. maybe something faster. i made the mistake of trying fedora 10 which aggravated me as community support sucked and i did not have to patience this weekend to play with the wireless to get it working. so i figured while im going to have to re do that i might as well test the water.

---

