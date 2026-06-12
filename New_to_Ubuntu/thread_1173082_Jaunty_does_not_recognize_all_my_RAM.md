---
title: "Jaunty does not recognize all my RAM"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by jlbr21 on 2009-05-29
Hi,
My machine came originally with 3 Gb of Ram, I got a 2 Gb card and installed it, under Intrepid the machine recognized all my RAM immediately the minute I installed it, no problem whatsoever.

I did a clean install of Jaunty and now it does not look like the machine is recognizing the 4 gbs. Under System Monitor, in the System specs, it says I've got only 3gb.

What's up with that??

---

### Post by yamagami on 2009-05-29
You'll need the 64bit (amd64) version of Jaunty (or any other OS including windows) to recognize RAM over 3GB.

---

### Post by LowSky on 2009-05-29
> **yamagami said:**
> You'll need the 64bit (amd64) version of Jaunty (or any other OS including windows) to recognize RAM over 3GB.

32 bit version of ubuntu will not see more than 3.2GB of RAM like Yamagami said.

install 64bit, sorry no other way.

---

### Post by lykwydchykyn on 2009-05-29
> **LowSky said:**
> 32 bit version of ubuntu will not see more than 3.2GB of RAM like Yamagami said.

install 64bit, sorry no other way.

Actually, there is another way.  Install the server kernel.  It has PAE (Physical Address Extension) enabled and will see up to 64 GB of RAM, even with a 32 bit system.

Now, I've heard people say they have had driver issues with the server kernel, but I'm currently using the server kernel on my Dell with the Nvidia driver and it's working fine, sees my full 4 GB of RAM.

Give it a shot, you've got nothing to lose.
```

sudo aptitude install linux-image-server

```

---

### Post by billgoldberg on 2009-05-29
See this article on 32bit ram limitations:
[http://www.interact-sw.co.uk/iangblog/2005/08/05/is3gbenough](http://www.interact-sw.co.uk/iangblog/2005/08/05/is3gbenough)

There are ways around it, but 32bit is getting obsolete pretty quickly on the computer market (the exception being netbooks).

---

### Post by lykwydchykyn on 2009-05-29
> **billgoldberg said:**
> That's a way, but installing the 64bit version is easier and won't cause issues.

See this article on 32bit ram limitations:
[http://www.interact-sw.co.uk/iangblog/2005/08/05/is3gbenough](http://www.interact-sw.co.uk/iangblog/2005/08/05/is3gbenough)

Reinstalling Ubuntu is easier than installing a new kernel?

I haven't had a single issue running the server kernel myself.

64 bit wasn't an option for me for a variety of reasons.

---

### Post by kevil99 on 2009-08-06
> **lykwydchykyn said:**
> Actually, there is another way.  Install the server kernel.  It has PAE (Physical Address Extension) enabled and will see up to 64 GB of RAM, even with a 32 bit system.

Now, I've heard people say they have had driver issues with the server kernel, but I'm currently using the server kernel on my Dell with the Nvidia driver and it's working fine, sees my full 4 GB of RAM.

Give it a shot, you've got nothing to lose.
```

sudo aptitude install linux-image-server

```

I HAD nothing to loose up untill a few days ago using the code. But now its not working for me anymore.  After using the code and restarting my pc it crashes the grapicalx blah blah..and i get a blue screen that isnt responsive.

My pc is only show like 2.7g of my 4g installed what can i do to resolve this with out the graphical issue?

---

### Post by kevil99 on 2009-08-06
linux-image-server??

This is a kernal just for the server edition and not a 32bit edition?

---

### Post by shae on 2009-08-06
The server version should work fine because the repositories are shared between types of Ubuntu (Server, Kubuntu, etc).

---

### Post by lykwydchykyn on 2009-08-06
> **kevil99 said:**
> linux-image-server??

This is a kernal just for the server edition and not a 32bit edition?

It is a kernel for the server edition which is 32 bit.  It's still a 32 bit kernel, but as I explained:
[quote=lykwydchykyn]
It has PAE (Physical Address Extension) enabled and will see up to 64 GB of RAM, even with a 32 bit system.
[/quote]

If it doesn't work for your graphics driver, I suppose you're just going to have to go 64 bit.

What is your graphics card?

---

### Post by LowSky on 2009-08-06
if you install a new kernel you might have to update your graphics driver by reinstalling them

---

### Post by kevil99 on 2009-08-07
__________________
EVGA nForce780i SLI, EVGA GeForce9800.GTX
1000w CoolerMaster PSU
Intel Q9550 OCd 3.4
4GB Patriot DDR2 1066 :D

---

### Post by kevil99 on 2009-09-08
RESOLVE:)

After changing over to the Server Kernel..DO NOT REBOOT until you remove the video driver first!! :P    (basically dont have a video driver installed while changing to the server kernel) then reboot. check to see if all the ram is showing then reinstall the video driver.

THX for all the help guys!

---

### Post by rkod420 on 2009-10-13
I have an Nvidia GT120 and when I install the amd64 version of Jaunty it doesn't recognize my card on the proprietary drivers. Also it doesn't even let me turn on Gnome desktop effects and limits my resolution to a tiny 1280x800.

I'm going to try to install the server kernel and report back.


Edit:

Thought I'd add I have 8GB ram and only 3.2 is showing up, so I really didn't want to miss out on 4.8.

---

