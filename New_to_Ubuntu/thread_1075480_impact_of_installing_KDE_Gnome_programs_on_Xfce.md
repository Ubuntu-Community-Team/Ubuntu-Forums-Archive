---
title: "impact of installing KDE/ Gnome programs on Xfce"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by rich_wookey on 2009-02-20
Hi

I've dabbled with Unix/ Linux/ Ubuntu and now Xubuntu over the years, and can even compile a program not available in Ubuntu repositories for use on Xubuntu, so I'm not a complete beginner....

FYI - following the demise of my 1 year old fast laptop, when I droppped it, I am now using Xubuntu on a 10 year of Dell Inspiron 3800 - P3 700MHz processor with 500MB Ram and 20GB hardrive - until the insurance company pay out...

I chose Xunubtu, because the Dell can cope with the lightweight Xfce desktop and other apps... 

However, what happens if I install another program, say Gnome Gparted or KDE  kbtobexclient for example, will they compromise my choice of Xfce, by installing bloatware (ie parts of the Gnome or KDE desktop) in order that GParted or Kbtobexclient can run? 

or to put it another way, if I install such apps, will it make any difference to the overall performance of the old laptop?

(BTW Gparted and other apps seem to install and run fine)

Thanks

Rich

---

### Post by LowSky on 2009-02-20
runnign gnome or KDE apps in XFCE will work. The only issue is that you need to have the libraries for those applications installed and running, so if you are low on RAM (under 512MB) then it may cause a small performance drop.

---

### Post by sdennie on 2009-02-20
The only real difference it will make is on disk space.  Gparted is a gtk app and XFCE uses a lot gtk apps so, the impact of installing that is very minimal.  KDE apps run some services and have their own GUI library so, installing KDE may be a bit more heavyweight than installing gtk/gnome apps.  Also, KDE apps might start some daemons so, it's possible (I don't know how likely (probably not very)) that performance will suffer if you are actively running KDE apps on a XFCE install on a very old machine.

---

