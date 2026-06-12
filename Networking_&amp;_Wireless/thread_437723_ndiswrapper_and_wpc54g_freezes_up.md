---
title: "ndiswrapper and wpc54g freezes up"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by aZn137 on 2007-05-09
hi guys,

iam a new guy in the linux community, so sorry if i dont know what iam talking about or dont use the right terms.

i have ubuntu 7.04, ndiswrapper 1.43rc and wpc54g, trying to make everything work with wireless internet.

got it working, yay! but, sometimes when i plug in my card, it totally freezes up my comp, dont know why. if i plug it in before ubuntu starts, it will freeze up when it gets to the "running bar" screen, somewhere around half of the bar (this happens all the time, not sometimes).

if i had it plugged in when its hibernated and then wake the comp up, it will show "bug: BUG: soft lockup detected on CPU#0!" and then freezes everything after that.

i can only use the card when i really need the internet now because it might freeze up as it will --> no good. please help.

oh, i have the latest driver from dell inspiron 1501 (i heard this worked on a lot of laptop so i got it, and ndiswrapper actually installed the driver) (some say it has something do to with the stack memory too)??

much appreciate.

azn137.

---

### Post by Davesp on 2007-05-09
I have the same problems on different hardware. ( a compaq evo n610) with a netgear wireless card.

My experience was that the card worked when I did a boot from the ubutu cd; I was able to get online via the wireless network in my house but when I did the install on ubuntu onto the hard disk the machine would not boot into ubutu with the card in place. 

It will boot with the card out. I'll keep an eye on this thread....

---

### Post by aZn137 on 2007-05-10
well, theres no point using the CD with the card. what we actually need is a working card with ubuntu on HDD. i guess theres no solution until the next ubuntu comes out with new ndiswrapper.

---

### Post by ozooha on 2007-05-16
It used to happen to me before with ndiswrapper-1.43 but yesterday it went away as I used the ndiswrapper-1.44rc1. They fixed it for Ubuntu.
I was using the netgear wpn511 with the net5211.inf/sys files on compaq presario 701.
OZooHA

---

### Post by aZn137 on 2007-05-16
still, no good. now that it doesnt freeze up when i plug it in since i upgraded to 1.44rc1, but when i have my console up and i unplug it, man, bad business... it gives me a whole bunch of error messages and doesnt let me do anything, cant even shut it down, just have to hold on to the power button for 3-4 seconds. anybody else is having the same problem with linksys WPC54G???

oh, one more thing: i cant have the card plugged in when i start or shut down my ubuntu, it will freeze up also. please, help...

---

