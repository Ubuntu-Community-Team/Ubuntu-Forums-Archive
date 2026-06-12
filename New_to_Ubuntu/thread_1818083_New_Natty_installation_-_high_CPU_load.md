---
title: "New Natty installation - high CPU load"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by setspeed on 2011-08-04
I have just installed Natty Narwhal on a HP NC4010 (1.6ghz, 768mb RAM/32mb shared with video card), dual boot configuration.
When booting into Ubuntu my CPU usage is sky-high - never below 60% when the computer is idling, and it shoots up to 100% if I open Firefox. The system is disappointingly unresponsive, compared to the XP installation.

I've looked at System Monitor and there are no processes which look excessive, in fact the processes listed don't add up to the CPU usage displayed in the resources tab.

"top" shows PID/623 - USER/root - COMMAND/Xorg is chewing up about 30-45% of my CPU.

I'm a complete beginner, this is my first time on Linux, what I have done so far has been by searching the forums. Can someone explain to me what Xorg is, why it's using loads of CPU time, and how to stop it from doing so?

Thanks.

---

### Post by amjjawad on 2011-08-04
Hello and Welcome :)

Not a direct answer to your question but hope this will help a little bit:

[http://www.x.org/wiki/](http://www.x.org/wiki/)

[http://en.wikipedia.org/wiki/X.Org_Server](http://en.wikipedia.org/wiki/X.Org_Server)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Xorg+high+CPU+usage&as_qdr=all&sa=Google+Search&lang=en#1095](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Xorg+high+CPU+usage&as_qdr=all&sa=Google+Search&lang=en#1095)

For Ubuntu related search: [www.googlubuntu.com](www.googlubuntu.com)

---

### Post by setspeed on 2011-08-04
After playing around a bit I think I might have solved my own problem!
I went into the BIOS of the machine, where there is the option to choose between using 32mb or 64mb of your system memory for the integrated ATI 350M graphics card.
It seems to have had the effect of dropping my CPU usage right down. Xorg is now only using 5-15% of my CPU when idle.
gnome-system-mo is hovering around 16-17%.
At least the system (and Firefox) seems a lot more responsive now.

I would call myself an intermediate Windows user, and I know how to tweak Windows installations for best performance. Can anyone offer me tips to do the same for this Ubuntu install? I just want the best performance I can get out of this thing :-)

---

### Post by setspeed on 2011-08-04
> **amjjawad said:**
> Hello and Welcome :)

Not a direct answer to your question but hope this will help a little bit:

[http://www.x.org/wiki/](http://www.x.org/wiki/)

[http://en.wikipedia.org/wiki/X.Org_Server](http://en.wikipedia.org/wiki/X.Org_Server)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Xorg+high+CPU+usage&as_qdr=all&sa=Google+Search&lang=en#1095](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Xorg+high+CPU+usage&as_qdr=all&sa=Google+Search&lang=en#1095)

For Ubuntu related search: [www.googlubuntu.com]("http://www.googlubuntu.com")

Thanks for the links, I'll be sure and take a look. Currently trying to wrap my head around Linux!

---

### Post by tdrusk on 2011-08-04
> **setspeed said:**
> After playing around a bit I think I might have solved my own problem!
I went into the BIOS of the machine, where there is the option to choose between using 32mb or 64mb of your system memory for the integrated ATI 350M graphics card.
It seems to have had the effect of dropping my CPU usage right down. Xorg is now only using 5-15% of my CPU when idle.
gnome-system-mo is hovering around 16-17%.
At least the system (and Firefox) seems a lot more responsive now.

I would call myself an intermediate Windows user, and I know how to tweak Windows installations for best performance. Can anyone offer me tips to do the same for this Ubuntu install? I just want the best performance I can get out of this thing :-)
You must realize that Ubuntu, the Unity version, is not going to run as fast as Windows XP. You are comparing operating systems with over a a ten year difference.

---

### Post by setspeed on 2011-08-04
Yeah, I'm not running Unity I don't think - when I installed it told me my machine didn't have the hardware required. Tbh this machine is to take travelling with me as a safe alternative to me taking my main machine.
I'll be staying in hostels so there's a high chance of theft I suppose, so being able to easily encrypt my home folder was an added bonus, in addition to the fact that I'll be using wifi networks with god knows what sortof machines attached to them. So Linux offers me a safe way to access my online banking etc.

I don't intend on spending any money on this machine (not that I could anyway, it would only take a max 1GB of ram, compared to the 768MB it currently has), so some tips on reducing any crap running in the background would be appreciated. Perhaps even a suggestion for an older distro would be acceptable to me, if it's significantly lighter on resources? I don't know, as I said, I'm a complete Linux noob and have heard Ubuntu is the place to start since it's user-friendly. I'm getting on ok with it so far, although I have to admit even trying to install some software is daunting. I downloaded Utorrent, and it came down as a tar.gz file. A quick search on the net gives instructions that I don't fully understand, so it's gonna have to wait until I have a bit more time before that gets installed!
I basically just want the machine running nicely with the basics first, then I'll worry about adding on other software!

---

### Post by setspeed on 2011-08-04
Also, another reason i wanted to try Linux out is becuase it has this rep for being so much lighter on system resources than Windows is. Although i guess if that's my goal then perhaps a diffferent distro would be better suited?

---

### Post by amjjawad on 2011-08-04
> **tdrusk said:**
> You must realize that Ubuntu, the Unity version, is not going to run as fast as Windows XP. **You are comparing operating systems with over a a ten year difference**.

Despite that fast, Ubuntu still runs **"faster"** than XP but perhaps not a fresh installed XP.

Linux Mint 9 LXDE runs MUCH faster than XP installed on Pentium 2 with 64MB of RAM on an antique broken HP Laptop. Yes, I have that laptop.

Microsoft Windows WILL never be faster than Linux as long as they keep doing the same over and over again.
Who knows? maybe one day they will use Linux Kernel ;)

---

### Post by verymadpip on 2011-08-04
I'd suggest Lubuntu as a lightweight distro.
I think as long as you aren't going to be doing anything crazily technical or weird it should be ideal for your machine.

[http://lubuntu.net/](http://lubuntu.net/)

I've run Lubuntu successfully on a 1.3GHz Celeron M CPU with 256mb RAM.  It gave that box a whole new lease of life. (I've upgraded the RAM in it now, & still use Lubuntu as it does all I need lightning quick).

Excellent help is available for Lubuntu if it's needed on the IRC at Freenode #lubuntu.

---

### Post by setspeed on 2011-08-04
Presumably if I want to try out Lubuntu or Mint, then I could just download a live cd and give it a go? Although it doesn't run as well as if you actually install it on the hard drive? Presumably I could install on the hard drive and make the computer a triple boot following the same procedure I used to dual boot.

All I need the computer for really is internet access (Facebook, Youtube, banking), and a bit of multimedia such as watching movies and some light photo-editing then uploading.
If either one of those suggested distros is more complicated than Ubuntu, I reckon I'll probably just stick with what I've got for now. Decisions, decisions!!

---

### Post by amjjawad on 2011-08-04
> **setspeed said:**
> Presumably if I want to try out Lubuntu or Mint, then I could just download a live cd and give it a go? 

Preciously :)

> Although it doesn't run as well as if you actually install it on the hard drive? 

Speed wise. Trying it from CD will be very slow. If you want, you can create LiveUSB. There is some instructions on HOWTO Create a LiveUSB on Ubuntu Website, same page where you download Ubuntu.
Also, you won't be installing programs, you'll just have a look. Windows doesn't have that feature as you have to install it to see what's going on but after all, Windows is Windows and nothing much is different with newer versions.

> Presumably I could install on the hard drive and make the computer a triple boot following the same procedure I used to dual boot.

Yes, why not? you can do that. I had 9 OS's installed on one machine.

> All I need the computer for really is internet access (Facebook, Youtube, banking), and a bit of multimedia such as watching movies and some light photo-editing then uploading.

Your needs are basic so ANY Distro could do that job, even SliTaz ;)
SliTaz is 30MB OS but you may have some hard time with the Wireless Drivers so better to stick with Ubuntu, Xubuntu or Lubuntu.

> 
If either one of those suggested distros is more complicated than Ubuntu, I reckon I'll probably just stick with what I've got for now. Decisions, decisions!!

Ubuntu, Kubuntu, Xubuntu and Lubuntu ... all have the same core but it's the Desktop Environment which is different.

I'm using 11.04 on less than 512MB of RAM.
It becomes slow when I run two browsers at the same time.

How light you want to go?
I can suggest at least 10 light distros for you but if you really want something so light and so nice, definitely Lubuntu.

Some may suggest Xubuntu but I just don't like XFCE.

[www.distrowatch.com](www.distrowatch.com) << is all what you need to have a look but be careful, you'll be dizzy because there are tons of choices :)

---

