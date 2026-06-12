---
title: "nvidia drivers, dvd burning..."
date: 2010-02-10
forum: New to Ubuntu
---

### Post by redhuxley on 2010-02-10
Probably a stupid question, but while trying to burn a dvd (avi. files with devede or dvdstyler) my system freezes.  I'm looking at the log file and wondering if it has something to do with a proprietary nividia driver.  Does this make sense, or is the issue likely somewhere else??

---

### Post by mwcrowley on 2010-02-10
I had issues under karmic with dvd burning.  I suspect it has nothing to do with the nvidia drivers.  If I remember correctly it's a bug related to a Uli chipset on the motherboard.   One workaround is to enter 
sudo  echo 1 > /sys/module/pata_ali/parameters/atapi_dma

here's more: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/328053](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/328053)

if the command above works, then try this from the above link.

1) "options pata_ali atapi_dma=1" in /etc/modprobe.d/options (new file for me!)
2) "echo 1 > /sys/module/pata_ali/parameters/atapi_dma" in /etc/rc.local

Post back if this works.  I'm guessing you have an asrock dual sata board.

---

### Post by Temposs on 2010-02-10
The graphics driver deals with displaying things on your screen, not with burning dvd's. So, it is likely not a problem with your graphics driver.

Have you tried burning with Brasero? Does that have the same outcome?

---

### Post by redhuxley on 2010-02-10
> **Temposs said:**
> The graphics driver deals with displaying things on your screen, not with burning dvd's. So, it is likely not a problem with your graphics driver.

Have you tried burning with Brasero? Does that have the same outcome?

That's of course what I thought, but looking at the log it looks like the trouble starts w/ something with nvidia.   I'll try Brasero, but immediately after switching to ubuntu and trying to burn a CD, Brasero would not work for me at all-it would just hang there.  That was on jaunty, though and I've since upgraded to karmic.

---

### Post by halitech on 2010-02-10
try k3b. yes I know its a kde app but its always been foolproof for me

---

### Post by redhuxley on 2010-02-11
OK, same issue with k3b. 

Brasero says I'm missing a plugin(going to explore that now), tho the program itself does seem to work now that I'm in karmic.

I tried converting the .avi to mpeg and computer froze then also.

re:  mwcrowley, I'm a recent convert from m$ vista, I'm not that familiar/experienced/comfortable w/ CL....yet?

---

### Post by 3rdalbum on 2010-02-11
I had system freezes and kernel panics (blinking keyboard lights) when ripping DVDs, and I think I once had it happen when my DVD drive was spinning up to burn a disc. It also used to freeze during video encoding. In the end, the problem was the RAM.

Try removing each RAM stick individually until you have a problem-free system. Test all your RAM in this way - yes, all of it.

If your system only has one RAM stick, try running the RAM benchmarks from Phoronix Test Suite ([www.phoronix.com](www.phoronix.com)) and see if they trigger a crash - in my scenario, they did. If you get a crash, then try buying some new memory.

---

### Post by redhuxley on 2010-02-11
I have brand new memory and I've recently run tests on it, but I'm wondering then if the issue is mb or writing from the hd.  But burning cds and data dvds has been no problemo.

---

