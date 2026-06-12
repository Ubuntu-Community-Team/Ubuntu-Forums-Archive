---
title: "Too much memory usage without starting an application"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by ZuLuuuuuu on 2009-01-01
Hello,

Since Ubuntu runs slow on my machine, I started using Xubuntu but the slowness didn't disappear much. So I checked the memory usage and find out that after booting to the desktop -without starting any application- it uses about 250 MB memory which is half of my entire memory. It is fast when no application running (exploring menus, opening Thunar etc.). But when I start Firefox and music player it grows to 400 MB after a while and starts slowing down.

My question is, is 250 MB usage normal? It does not show what is taking this memory on System Monitor (I can see Firefox and Listen Music Player but others are just a few programs with kilobytes). I have Apache and MySQL server installed I guess they are one of the reason but it still looks like so much.

My system is: 512MB ram, Celeron 2.66 GHz, 1GB swap partition, 20GB Linux partition (%16 of it occupied), 128MB on board graphics card.

---

### Post by bwang on 2009-01-01
I don't think so, because GNOME uses around that much memory on an empty desktop, and XFCE should be significantly lighter.

---

### Post by Sprut1 on 2009-01-01
Ubuntu uses memory in a whole other way than Windows - no need to worry.

---

### Post by Joeb454 on 2009-01-01
MySQL will eat any RAM it finds along it's way in my experience, so you might want to rethink if and when you run that. Apache shouldn't make a big difference though.

As for Firefox, it's quite well known that FF RAM usage is relatively high, especially if you use tabbed browsing a lot.

I'd say 250MB is normal, I can run a couple of apps and still sit around 300-310MB (this doesn't include Firefox). But when you think Vista uses ~700MB idle, that's nothing ;)

---

### Post by mwanstall on 2009-01-01
I've run Xubuntu on a lower specced machine than yours and all general applications ran fine, but FF is a resource hog and will run older machines to the ground (esp if you leave it open for long periods of time and are using many tabs). I'd try a more scaled back browser if I were you.

---

### Post by lloyd_b on 2009-01-01
First step:
Xubuntu Menu -> System -> System Monitor

Select the "Processes" tab, then click twice on the "Memory" header.  This will sort processes by descending memory usage (memory hogs at the top).

Does anything jump out at you there?

I have a system with similar specs, but it has a crappy Intel video system, which uses system RAM instead of having it's own dedicated video memory.  With Firefox, Deluge (bit-torrent), and my music player open, I'm currently using about 350Mb of 512mb...

Another question: How are you determining memory used?  For an *accurate* picture of memory, open a terminal window, and type "free".  Look at the line that starts "-/+ buffers/cache".  What does it show for used/free?  It's perfectly normal for Linux to use *all* of your RAM, but most of it is used to cache/buffer files, and this memory will be made available to programs if it is needed.

---

### Post by ZuLuuuuuu on 2009-01-01
Unfortunately, I use the extensions of Firefox a lot which is crucial for me :( I will try to close library feature of Listen player which is taking almost 50~100MB of memory...

---

### Post by ZuLuuuuuu on 2009-01-01
> **lloyd_b said:**
> First step:
Xubuntu Menu -> System -> System Monitor

Select the "Processes" tab, then click twice on the "Memory" header.  This will sort processes by descending memory usage (memory hogs at the top).

Does anything jump out at you there?


Of course I did this before writing here :) Firefox and Listen Music Player is the ones eating memory.

> **lloyd_b said:**
> I have a system with similar specs, but it has a crappy Intel video system, which uses system RAM instead of having it's own dedicated video memory.  With Firefox, Deluge (bit-torrent), and my music player open, I'm currently using about 350Mb of 512mb...


I think the difference is because of the MySQL, tabs and music library size. When I first open Firefox it is about 320MB which quickly grows to 340MB after opening two tabs.

> **lloyd_b said:**
> Another question: How are you determining memory used?  For an *accurate* picture of memory, open a terminal window, and type "free".  Look at the line that starts "-/+ buffers/cache".  What does it show for used/free?  It's perfectly normal for Linux to use *all* of your RAM, but most of it is used to cache/buffer files, and this memory will be made available to programs if it is needed.

It shows:

```
             total       used       free
-/+ buffers/cache:     407512      98284
```

---

### Post by ZuLuuuuuu on 2009-04-05
By the way, I upgraded to 1 GB ram recently and find out that the slowness is not because of the memory. Speed didn't even slightly improved. And the more I use Ubuntu for my day to day needs, the more I find dealing with this slowness painful.

Tried different programs, different drivers, no result... After opening 2-3 programs (a browser, a multimedia player and a file manager etc.) it begans to slow significantly. The cause is either CPU, Celeron 2.66 GHz, or the onboard graphics card which is relatively new along with the mainboard (ASUS P5GZ-MX).

---

### Post by enri2 on 2009-04-05
my linux mint uses 450-700 mb without any open programs

---

### Post by chessnerd on 2009-04-05
I'm using Xubuntu 8.04 on a $50 boat anchor (1.7Ghz Pentium 4 with 256MB RAM and an Elixir graphics card from 2001) and I am able to run Firefox perfectly even with OpenOffice, and a couple Thunars open or minimized. My system idles at around 128MB of RAM usage so I don't know why your system is idling so high...

I'd use the system monitor to see what is eating up your RAM and CPU. Either put "gnome-system-monitor" in a terminal or go to Applications>System>System Monitor.

---

### Post by bertolo on 2009-04-05
> **enri2 said:**
> my linux mint uses 450-700 mb without any open programs

 ?
 lol my ubuntu takes 500mb with:
 amarok, pidgin, btnext, conky and firefox.using 0% swap.
 how can mint uses that much memory and so inacurate values ?

---

### Post by enri2 on 2009-04-05
> **bertolo said:**
> ?
 lol my ubuntu takes 500mb with:
 amarok, pidgin, btnext, conky and firefox.using 0% swap.
 how can mint uses that much memory and so inacurate values ?

maybe because i have all the desktop effects on

---

### Post by egalvan on 2009-04-05
> **ZuLuuuuuu said:**
> , I upgraded to 1 GB ram  and find that the slowness is not because of the memory. Speed didn't even slightly improved.

 After opening 2-3 programs (a browser, a multimedia player and a file manager etc.) it begans to slow significantly. The cause is either CPU, **Celeron** 2.66 GHz, or  onboard graphics  which is relatively new along with the mainboard (ASUS P5GZ-MX).

Celeron is a very inefficient (but inexpensive) chip.
If possible, upgrade to a full Pentium 4.

Depending on the socket and chip-set, you can get a much improved CPU.

P-IV came in

Socket mPGA478

Willamette  (oldest, limited to 256K cache, 130-die size)
Northwood   (512k-1meg cache 130-90 die-size)
Prescott    (512k-2meg cache 90-die size)

Socket L:GA775
Prescott (90 die-size)

Better, larger cache,
more efficient memory handling
better pipe-line support
possible Dual-Core (at least Hyper-Threading)

(These are from memory, so I may have some errors.)


ErnestG

---

### Post by khelben1979 on 2009-04-05
> **Sprut1 said:**
> Ubuntu uses memory in a whole other way than Windows - no need to worry.

I have had discussions regarding this with my younger brother last year. Can some Linux expert on this forum explain exactly how the RAM management in Linux works? And why it is better than what comes from Windows XP or Vista? (I find this very interesting)

And regarding memory usage: I have been running Debian myself on the Amiga with only 64MB of RAM with working graphics 10 years ago and I'm surprised to read how much RAM some Linux distributions just "eats up" from the start without that even a desktop enviroment has been up and running. It doesn't sound good to me.

---

### Post by Peter09 on 2009-04-05
Install HTOP and keep an eye on the stats, are you really using a lot of CPU, are you using SWAP etc. What is the major resource task in the system?

---

### Post by corpsehacker on 2009-04-05
my computer uses 220mb idle, but thats not a huge problem for me because I have over 2 gigs of overall ram.

---

### Post by oldos2er on 2009-04-05
[http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm](http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm) is one explanation. If you google "linux memory management" you'll get much technical information.

---

### Post by khelben1979 on 2009-04-05
> **oldos2er said:**
> [http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm](http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm) is one explanation. If you google "linux memory management" you'll get much technical information.

Thanks for the link! I found it useful.

---

