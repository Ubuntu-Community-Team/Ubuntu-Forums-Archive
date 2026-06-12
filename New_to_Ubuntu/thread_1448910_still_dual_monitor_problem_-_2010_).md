---
title: "still dual monitor problem - 2010 :)"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by duruttye on 2010-04-07
Hey there!

I know, I know, this question has been asked a lot of times, but still, after a while of browsing I can't get my xubuntu working with dual monitors...

So, I use Xubuntu 9.10 and Xfce 4 Desktop Environment version 4.6.1 (Xfce 4.6), and when I start my dell vostro a680 laptop I can't even log in to xfce when the second monitor is plugged in. With gnome it works perfectly.

I plug it out, log in to xfce, and plug it in, then it doesn't show up in the Display, it only shows my native monitor, which is the laptop's monitor.

Video card:
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

uname -r command:
2.6.31-21-generic


And hey, I can't find my xorg.conf file... here are the files in

/etc/X11$ ls
app-defaults             fonts    xinit       Xsession          XvMCConfig
cursors                  rgb.txt  xkb         Xsession.d        Xwrapper.config
default-display-manager  X        Xresources  Xsession.options


So, any ideas out there??

I'm pretty lost here, and it's 2010... it shouldn't be that complicated... :)

---

### Post by IndyGunFreak on 2010-04-07
Intel seems fairly crappy w/ Dual screens... I've never been able to get it to work either(same device)

My PC w/ Nvidia works great.

IGF

---

### Post by duruttye on 2010-04-07
> **IndyGUnFreak said:**
> Intel seems fairly crappy w/ Dual screens... I've never been able to get it to work either(same device)

My PC w/ Nvidia works great.

IGF


I already read that on several forums, but with Gnome it works perfectly... different resolution, inverted, etc, what ever you want...

Why doesn't it work on xfce??
Or better yet: why isn't there a simple way to make it work, just like on gnome... (i'm confident it works...)

---

### Post by duruttye on 2010-04-26
Any ideas on this?

I'm still switching between xfce and gnome wherever I need to work on two screens... :)

---

