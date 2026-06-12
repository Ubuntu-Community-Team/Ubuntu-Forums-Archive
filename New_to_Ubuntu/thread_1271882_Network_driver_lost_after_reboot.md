---
title: "Network driver lost after reboot"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by Pwierenga on 2009-09-21
I am a brand nooby with linux. I have installed ubuntu 9.04 desktop on a new built computer. The motherboard is a GA31M-ES2L with Pentium E3200 Wolfdale 2.5Ghz dual core. This motherboard has a 1gig built in nic. I found a AR8131 linux-Family driver for it v1.0.0.10 and have installed it using 
 
make
insmod atl1e.ko
 
When I install, it loads and works fine until I reboot the computer. Then I lose the connection until I do the install process over again. How can I get the driver to stick?

---

### Post by norm7446 on 2009-09-21
Did UBUNTU not setup your LAN driver during the install as unlike Windows you normally shouldnt need to go hunting about for drivers.

---

### Post by Pwierenga on 2009-09-21
It did not seem to notice that there was a lan connection available during install.

---

### Post by sandyd on 2009-09-21
```

sudo modprobe atl1e

```

if that restores your internet, add that to the end of /etc/modules
using
```

sudo pico /etc/modules

```

---

### Post by Pwierenga on 2009-09-21
Carlee,  That did not work. What does work is this.  When I unpacked the driver, I created a root directory called /ar81 where all the files extracted to. It also created a sub directory called /ar81/src.  If I go into that directory and type "insmod atl1e.ko" in a couple of seconds I see the network indicator change to active and it works till I reboot again.  I just want to make this automatic on startup.

---

### Post by norm7446 on 2009-09-22
I anit no Command line Commando but is there no way you could put a line into your boot.ini file to load this driver up on startup.

---

### Post by jrev on 2009-09-22
Or put a script in the   folder /etc/rcS.d 
like the one I used to share my internet connection at the start of the computer : 
name it S91.sh so that it runs after the other scripts already there

---

