---
title: "How to speed up Ubuntu boot-up time?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Ben Page on 2009-01-19
Me again with the Ubuntu questions.
I was using Windows7 and ubuntu 8.1 dual boot cofig. for about 2 weeks, and I noticed that boot-up time of Ubuntu is pretty sluggish comparing to Win7. Win7 boots up completely (past the login screen) in 20 secs, sometimes even faster, while Ubuntu needs more time, like 45 secs. ~30 to boot to login screen + ~15 to finish HDD activity and load apps after login.
Are there some unnecessary services to turn them off, or some tricks and tweaks to speed it up? I already turned of bluetooth app-service, but that doesn't seep to help (in terms of speed). Also, I have noticed that Nvidia proprietary drivers seem to slow the boot on Ubuntu, too. Are there some tweaks?

---

### Post by linux_tech on 2009-01-19
To help identify the bottlenecks, give bootchart a try 
```
sudo apt-get install bootchart
```

---

### Post by hyper_ch on 2009-01-19
unfortunately Win 7 will "load" certain stuff after the login page when you already see the desktop... it is not really faster, it just appears to be ;)

Besides, Win 7 is a minimum system this far - it means it lacks a lot of things that will still be added.

---

### Post by kaibob on 2009-01-19
There was a very long thread a ways back on boot-up times, and your's is a bit slow but not bad. You can do a search of this forum for tips on disabling unneeded services and other advice to reduce the boot-up time. Windows boot-up time is not relevant.

---

### Post by billgoldberg on 2009-01-19
Something you can do quickly, is go to system, preferences, session and disable some unneeded stuff.

There are some guides online, google them.

---

### Post by hyper_ch on 2009-01-19
you could also reprofile your boot up sequence. Jdong has written a howto on that.

---

### Post by flOOi!ghenTM on 2009-01-19
You could give this a try:

[http://www.polishubuntu.piczo.com/optimizeubuntu8.04forspeed/?cr=2](http://www.polishubuntu.piczo.com/optimizeubuntu8.04forspeed/?cr=2)

It worked just fine for me

---

### Post by Ben Page on 2009-01-19
Just don't get me wrong, im not bashing Ubuntu, just want to improve it to be better than Windows. Its true that windows loads certain stuff later (when its needed) and that can make it slower later, but some stuff I never load, or load them just once a week etc. While Ubuntu loads everything at startup and so appears to be sluggish in terms of booting, but I dont really benefit from that. This is important to me because I frequently boot between systems. As I said, Im a windows power user and can even make Vista boot in ~25 secs. but with Ubuntu i don't really know what each service is, and is it really necessary for my usage habits and needs. For example, I know its safe to turn off crypting services witch is used to communicate in corporate networks in Windows networks (witch loads at startup-but I never even think of using it), but I don't know is there such thing in Ubuntu, and where it is. Is there app like Tune up utilities to turn on off services, and maintain Ubuntu easier - through GUI not terminal.
As much I hate Gates/Microsoft and hes anti piracy protections, pay for full version or enterprise package, I must admit that 7 is a very solid, stable, fast and practical OS. It will suffer some change and addons during the devel, but I doubt it will slow it down, build 7000 is very close to the final product (in terms of built in kernel, services and registry) there will be only "external apps" further development.

---

### Post by kaibob on 2009-01-19
> **hyper_ch said:**
> you could also reprofile your boot up sequence. Jdong has written a howto on that.
I believe this is what hyper_ch is referring to. I do this but have never noticed much difference. Still, it's probably worth a try. 

[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

---

### Post by Ben Page on 2009-01-19
> **flOOi!ghenTM said:**
> You could give this a try:

[http://www.polishubuntu.piczo.com/optimizeubuntu8.04forspeed/?cr=2](http://www.polishubuntu.piczo.com/optimizeubuntu8.04forspeed/?cr=2)

It worked just fine for me


Ah..this is what I was looking for! Thnx!

---

### Post by Ben Page on 2009-01-19
> **kaibob said:**
> I believe this is what hyper_ch is referring to. I do this but have never noticed much difference. Still, it's probably worth a try. 

[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

I saw this one, but I thought its too old, considering its for dapper 6.06, but hey, maybe it'll squeeze a couple of secs from interpid

---

### Post by hyper_ch on 2009-01-19
I have my doubts that you can boot a VISTA in 25 seconds...

---

### Post by Ben Page on 2009-01-19
> **hyper_ch said:**
> I have my doubts that you can boot a VISTA in 25 seconds...

Yes I can! But to prove it now, I have to install it and tweak it, and that is not what I had in mind for the rest of my life :)
Off course, it will be missing many default services (witch I never use). All I want to say, its possible.

---

### Post by hyper_ch on 2009-01-19
and you are positive that it won't just keep loading things after showing the desktop?

---

### Post by Ben Page on 2009-01-19
> **hyper_ch said:**
> and you are positive that it won't just keep loading things after showing the desktop?

It will load anti virus app (Avira-witch is very light 1sec) plus explorer and maybe some other minor stuff like those security apps, but they all load within ~2-3 secs. Off course, indexing, defender, UAC, that network crypting etc. are disabled at startup.

---

### Post by oldos2er on 2009-01-19
I like to use sysv-rc-conf to turn off unneeded services. It's CLI but very easy to use. There are several other things you can do; google "speed up ubuntu boot time" and you'll find a ton of articles. Just be sure to make backup copies of any file you change.

---

### Post by billgoldberg on 2009-01-19
Also keep in mind that when you install a default Ubuntu install, it's not tweaked for speed.

If you want speed, go Arch or install a cli install.

---

### Post by Chiapo on 2010-01-16
My Acer Aspire One ZG5 (intel Atom 1.6Ghz, 1GB RAM, 160GB hdd) boots into xubuntu 9.10 in around 23 seconds. (with Compiz-fusion/Emerald window manager)

I used the Applications >> Settings >> Session and Startup utility to disable unnecessary services.

---

