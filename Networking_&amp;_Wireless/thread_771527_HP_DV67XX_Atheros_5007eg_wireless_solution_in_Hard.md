---
title: "HP DV67XX Atheros 5007eg wireless solution in Hardy!"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by Vegetarianrage on 2008-04-27
I FINALLY GOT THIS TRASH TO WORK! :KS:KS

I'm running Hardy Heron 8.04 LTS on a HP DV6700 series laptop with the Atheros 5007eg wireless card.

I, myself, am a complete noob, so I'm writing this for other noobs. This is EXACTLY what I did step by step. Change things at your own risk!

Download [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz ]("http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz") to the desktop.

Open a terminal and execute the following. I know you shouldn't blindly run terminal commands but seeing as I don't know what most of this means myself, I can assure you there is nothing intentionally malicious in it. :D

Make sure there are no current madwifi drivers running.
 
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop/
tar -xf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007
make
sudo unload
sudo make install

```

Now restart and pray! Make sure your hardware kill switch is in the on position.

NOTE: THE WIRELESS LIGHT WILL REMAIN RED EVEN IF THE DRIVER WORKS.
Make sure there are no current madwifi drivers running. (I think that's what the "unload" command does but I really don't know.)

---

### Post by Nitewalker on 2008-04-27
Thanks, don't know what you came up with but got me up and running for now.  I have an Acer 5100 with an Atheros AR2413 card, and I followed your post and it brought it up and running....thanks for the post

---

### Post by eddywashere on 2008-04-28
> **Vegetarianrage said:**
> I FINALLY GOT THIS TRASH TO WORK! :KS:KS

I'm running Hardy Heron 8.04 LTS on a HP DV6700 series laptop with the Atheros 5007eg wireless card.

I, myself, am a complete noob, so I'm writing this for other noobs. This is EXACTLY what I did step by step. Change things at your own risk!

Download [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz ]("http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz") to the desktop.

Open a terminal and execute the following. I know you shouldn't blindly run terminal commands but seeing as I don't know what most of this means myself, I can assure you there is nothing intentionally malicious in it. :D

Make sure there are no current madwifi drivers running.
 
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop/
tar -xf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007
make
sudo unload
sudo make install

```

Now restart and pray! Make sure your hardware kill switch is in the on position.

NOTE: THE WIRELESS LIGHT WILL REMAIN RED EVEN IF THE DRIVER WORKS.
Make sure there are no current madwifi drivers running. (I think that's what the "unload" command does but I really don't know.)

I had a problem with your code, but what worked the second time around was

```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop/
tar -xf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007
make
sudo make unload
sudo make install

```

---

### Post by Vegetarianrage on 2008-04-30
> **eddywashere said:**
> I had a problem with your code, but what worked the second time around was

```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop/
tar -xf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007
make
sudo make unload
sudo make install

```

Thanks for the fix. I must have written down what I did incorrectly. I'm still figuring out how this "make" concept works.

---

### Post by paraplegicpanda on 2008-05-01
If this doesn't work for you the first time around, try this:

```
sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop/
tar -xf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007
make
sudo make clean
sudo make unload
sudo make install
```

---

### Post by Skillachi on 2008-05-01
a slightly off-topic question, how did you end up with that kind of wireless card. I am running a 6700t and i have an intel wireless card. Or does that card come with the amd processor?

I had no install problems with my card though, it worked once hardy was installed

---

### Post by Vegetarianrage on 2008-05-03
HP seems to be pretty sketchy with their hardware choices these days. I get the feeling we're all "beta testers" for their vista-oriented laptops. They are swapping out a lot of different devices. For example, older dv67xx laptops have conexant sound, which is unfortunate for linux fans like myself. Newer ones are using realtek, I think. Interestingly enough, some of their choices for hardware don't even work right in windows!:lolflag: The built in webcam has serious driver issues that often prevent it from functioning what-so-ever. Works like a charm in Ubuntu :KS.... now if I could only find a program that works so that I can use it! :mad:

---

### Post by weirdfrog on 2008-05-04
Thanks Vegetarianrage- this worked on my asus a8dca1. Hardy, upgraded from Gutsy.

---

### Post by nicedude on 2008-05-16
There is more that should be done to remove the restricted madwifi drivers that are installed with hardy 32bit by default. I remove them completely as well as jockey the restricted driver manager since it is not needed and is pretty silly try at making linux as simple as windows. I would rather install my own drivers and have the best/newest ones for my equipment than let some half baked program run my important devices for me. Its not hard to install drivers for your graphics and for Wifi which is what jockey covers anyway.

I just made a complete guide to install ar5007 support in 32bit Hardy correctly with madwifi patched drivers step by step with links to everything needed.

I dont know if you have already solved your situation or not, but if not my method is 100% for 32bit Hardy 8.04

Here is the link to my guide
[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

---

