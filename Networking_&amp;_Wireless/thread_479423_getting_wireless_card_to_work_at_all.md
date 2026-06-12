---
title: "getting wireless card to work at all"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by redfinder on 2007-06-20
I have a dell latitude cpi a pII machine with 128 megs of ram, I was hoping to install xubuntu or debian on it, but i can't for the life of me figure out how to get my airlink101 awlc3025 pcmcia card  to work. I checked the supported cards list in the sticky and its not there so I know its going to be tough. The chipset is some kind of TI chip. Anyone have any suggestions? Windows is getting slow and annoying so im switching it over to linux, Like my other pc of course.

Adam

---

### Post by S15_88 on 2007-06-20
use [ndiswrapper]("http://ndiswrapper.sourceforge.net/") and the windows driver.

---

### Post by redfinder on 2007-06-24
thanks! i will try that. I'm also looking for a way to install linux with one of the net install cd's as my laptop doesn't seem to wanna boot the live cd's, the only one it'd boot is dsl linux. anyone?

thanks, i'll read up on how this ndiswrapper works

---

### Post by kevdog on 2007-06-24
Try the alternate CD.  Its non-GUI, however if my brother can install using this method, anyone can!

---

### Post by tturrisi on 2007-06-24
It appears that that card has a Texa Instruments chipset and in Linux will use the ACX driver.  9determined by reading the contents of the .INF files packages with the airlink driver downloads zip files)

To install the ACX Linux driver see this:
[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

---

### Post by redfinder on 2007-06-26
thanks, but heres a stupid and quick question, will xubuntu even run on this pos?

---

### Post by ironyCurtain on 2007-06-26
Absolutely, I've seen it run on worse.

---

### Post by redfinder on 2007-06-29
sweet, im getting a new laptop soon so this will be my linux experiment one, thanks all!

---

