---
title: "Would Xubuntu provide better results?"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by Dreakon on 2010-02-13
I tried Ubuntu and honestly, I love it.  It's just the UI is pretty sluggish (probably due to a lack of sufficient Intel graphic drivers in 9.10) and things like opening and closing windows and menu's and the sort all seem to struggle a bit, taking a few seconds even, as compared to the instantaneous feel I get from using Windows.  Not to mention flash videos are almost impossible to run at a decent speed without burning out my CPU.

That said, I guess Xubuntu uses Xfce (I think), which I guess is supposed to be quite lightweight compared to KDE and Gnome, and probably better suited to a laptop like mine.  Plus I enjoy how it's UI is similar to Gnome.

Do you think I would see a significant improvement to desktop (and overall) performance if I switched to Xubuntu instead of Ubuntu?

Here's my laptop specs, just for kicks:
Intel Core2Duo 2.0Ghz (I usually limit it to about half speed or else it gets uncomfortably hot)
2gb RAM
Intel GMA 4500HD
250gb Hard Drive Space

---

### Post by chaanakya_chiraag on 2010-02-13
The problems is that, if it *is* sluggish because of lack of proper intel drivers, that is not going yo change whether you use ubuntu, kubuntu, or xubuntu. I would try Linux Mint or another distro.

---

### Post by nhasian on 2010-02-13
Based on your system specs, you have more than enough hardware to run Ubuntu.  I dont think you need to drop down to a lighter weight Windows Manager like xfce.  That being said, if you still want to try it you can install it with this one terminal command:

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

Now when you reboot you can choose between Gnome and Xfce at the login screen.

As far as speeding things up in Gnome, try disabling he visual effects from System->Preferences->Appearance.

Also you mentioned your system getting very hot?  How hot does your CPU, GPU, and HD get while idle?

right now my Nvidia GPU is 58C (yeah i know its rather hot) and my CPus in my laptop are 37 and 44C.  I have an Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz.

> **Dreakon said:**
> 
Here's my laptop specs, just for kicks:
Intel Core2Duo 2.0Ghz (I usually limit it to about half speed or else it gets uncomfortably hot)
2gb RAM
Intel GMA 4500HD
250gb Hard Drive Space

---

### Post by mkvnmtr on 2010-02-13
Xubuntu is not a light distro. Doing a minimal install with xfce4 is a light distro. With the specs of your machine you should not be having trouble with Ubuntu.If a specific solution does not present itself I would try other distros to see if they fit your machine better. Such as Kubuntu or Xubuntu. When 10.04 comes I understand we will have Lubuntu. I like the LXDE desktop.Some completely different distros are good also.

---

### Post by Sir Jasper on 2010-02-13
Hi,

I have an ancient computer with specs way below yours. I have Ubuntu with the Xubuntu desktop. I have 640 MB RAM (but my Swap partition is never needed or activated as I never hibernate) and all programs that I use regularly I leave minimised on my panel so they open instantaneously rather than taking typically 10 to 12 seconds opening from scratch.

I now use Xubuntu because I like it though I originally used it because I thought (possibly mistakenly) that it would be faster.

If you try the Xubuntu desktop you can easily remove it if don´t like it, but I also doubt it will improve your speed.

My regards

---

### Post by Dreakon on 2010-02-13
> **chaanakya_chiraag said:**
> The problems is that, if it *is* sluggish because of lack of proper intel drivers, that is not going yo change whether you use ubuntu, kubuntu, or xubuntu. I would try Linux Mint or another distro.

Well, the idea of course is that a lighter weight Windows Manager would be less hardware intensive in general, in which case the effects of the poor drivers would be somewhat alleviated.  Maybe that's not how it works, but that's what I am asking lol.

I understand Ubuntu *should* work fine with these specs, but it doesn't.  I'm fairly new to Linux still, so Ubuntu is definately the way I want to go though.  Other distro's don't have the community, the support or the overall ease of use as Ubuntu.  The closest I've found is Fedora, which seems to have the Intel drivers working better than Ubuntu, but it has other major problems with my setup (namely the wireless internet).  Plus, again, it's not half as user friendly as Ubuntu.  Fixing anything in it literally took hours of research and a lot of time spent on their IRC getting help...

> **nhasian said:**
> Based on your system specs, you have more than enough hardware to run Ubuntu.  I dont think you need to drop down to a lighter weight Windows Manager like xfce.  That being said, if you still want to try it you can install it with this one terminal command:

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

Now when you reboot you can choose between Gnome and Xfce at the login screen.

As far as speeding things up in Gnome, try disabling he visual effects from System->Preferences->Appearance.

Also you mentioned your system getting very hot?  How hot does your CPU, GPU, and HD get while idle?

right now my Nvidia GPU is 58C (yeah i know its rather hot) and my CPus in my laptop are 37 and 44C.  I have an Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz.

Temperature-wise, if I set it OnDemand in Ubuntu, the CPU cores can get anywhere from 60 to 80 degrees C when I'm opening Firefox, surfing the web, opening and closing folders, playing music, etc.  Idle, it's usually high 40's, low 50's.  This is pretty much the same for the Hard Drive temps.  Limiting my CPU to roughly half speed (setting each core to 800MHz), keeps the temperature around 50 to low 60 at all times, no matter what I do.  Of course, that's at the cost of system performance... but Windows for example, still functions perfectly fine when I limit it, games are the only thing effected.  I've cleaned dust out, I've gone as far as opening up the laptop.  It's clean, its just a naturally hot running computer.  It's only about a half a year old.

I don't want to get a laptop cooling pad or anything either, I don't like them.  Most of them seem shoddy, fans stop working, it's too big for my laptop or it's too small for my laptop.  Plus it's another thing to carry around with me if I go anywhere and want to run a game or something.  If I wanted to carry piles of crap with me, I would've kept my desktop lol.  My GPU doesn't have a temperature sensor, or at least, I've never actually seem a temperature for it in the several programs I have tried to read temperature.

I'm guessing switching to Xubuntu wouldn't really help performance at all though?  I'm pretty much SOL on getting Ubuntu running decently on this darn laptop...  I'm on Windows at the moment (grudgingly) or I'd try that terminal command nhasian.

---

### Post by bruno9779 on 2010-02-13
I had xubuntu 9.10 running on a P4 in a very satisfactory way.
Long boot time, but decent fluidity on the desktop

Ubuntu on the same machine was completely unusable (mouse moving 1-2 fps, windows never opening completely, etc.)

I have tried xubuntu only on that machine, and it DID make quite a lot of difference

---

### Post by Dreakon on 2010-02-13
> **bruno9779 said:**
> I had xubuntu 9.10 running on a P4 in a very satisfactory way.
Long boot time, but decent fluidity on the desktop

Ubuntu on the same machine was completely unusable (mouse moving 1-2 fps, windows never opening completely, etc.)

I have tried xubuntu only on that machine, and it DID make quite a lot of difference
Well, mine isn't quite that bad.  Ubuntu in general is usable, just sluggish to the point of annoyance after a little while.

---

### Post by bruno9779 on 2010-02-14
You should give it a try by installing both:

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

to remove xubuntu

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

and to remove gnome

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

