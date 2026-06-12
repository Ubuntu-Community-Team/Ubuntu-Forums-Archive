---
title: "Marvell Yukon ethernet on Edgy"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by Rocks on 2006-11-11
Hi all,

I'm trying to get the network to work with Edgy on my laptop. It's a Sony with a Marvell Yukon ethernet card. The original sky2 module seemed to cause problems and after reading a few topics on this forum, I decided to use the Marvel sk98lin driver. I went to download the driver (linux 2.14.13 and later kernel), bunzipped it, modified the #!/bin/sh to #!/bin/bash in install.sh, did "ln -s /usr/src/linux-headers-2.6.17-10-generic /usr/src/linux" and ran install.sh which promptly failed :evil: 

Here's the end of the install.log :
```
+++ Compile the driver
+++ ====================================
make: entrant dans le répertoire « /usr/src/linux-headers-2.6.17-10-generic »
Makefile:450: .config: Aucun fichier ou répertoire de ce type
  Building modules, stage 2.
/usr/src/linux-headers-2.6.17-10-generic/scripts/Makefile.modpost:38: .config: Aucun fichier ou répertoire de ce type
make[1]: *** Pas de règle pour fabriquer la cible « .config ». Arrêt.
make: *** [modules] Erreur 2
make: quittant le répertoire « /usr/src/linux-headers-2.6.17-10-generic »
+++ Compiler error
```

Although it's obvious the .config is missing, I can't see what I can do to solve this (I'm a bit of a newbie ...). Can anyone suggest any ways to solve this please? Thanks. :) 

Cheers,

---

### Post by FrodoB on 2006-11-11
From a terminal window type

$ sudo apt-get install linux-source-2.6.17

That should get you what you need.

---

### Post by redsax on 2006-11-11
U don't have "libc-dev" in ur Edgy.
You may install it from your Edgy CD.

Actually you may already have it,
try "sudo modprobe sk98lin"
and "lsmod | grep sk98"

I am struggling with compiling sk98lin, downloaded
from Marvell.com. Whenver the script install.sh reaches
the step "checking the driver", my computer dies.

Anyone has an idea about this? Thanks in advance for any help!
Even though now I suspect that I may not need a new sk98lin driver, I want to make sure that the sk98lin I am using is 
a right one, which is freshly compiled.

---

### Post by Rocks on 2006-11-12
Hi,

> **FrodoB said:**
> From a terminal window type

$ sudo apt-get install linux-source-2.6.17

That should get you what you need.

Yes, but linux-source is not on the Edgy CD is it?
As I'm trying to get networking to work, I can't apt-get anything else thant what's on the CD for the moment...

---

### Post by Rocks on 2006-11-12
Hi,

> **redsax said:**
> U don't have "libc-dev" in ur Edgy.
You may install it from your Edgy CD.
Thanks for the suggestion. Done that but it's no better. Compile still fails with the same error...

> **redsax said:**
> Actually you may already have it,
try "sudo modprobe sk98lin"
and "lsmod | grep sk98"
Yep, indeed, it's already there. Unfortunately, the network card still does not function. Dhcpdiscovers go out into the open space and never come back... fixing the network in /etc/network/interfaces works no better... :( 

> **redsax said:**
> I am struggling with compiling sk98lin, downloaded
from Marvell.com. Whenver the script install.sh reaches
the step "checking the driver", my computer dies.

Anyone has an idea about this? Thanks in advance for any help!
Even though now I suspect that I may not need a new sk98lin driver, I want to make sure that the sk98lin I am using is 
a right one, which is freshly compiled.

That's odd, I do exactly the same thing and all I get is a "Compile the kernel (error)" failure...
However, I suspect the same as you, neither the existing sk98lin in Ubuntu nor the Marvell flavor are likely to function...

Has anyone ever tried to get the card to work with ndiswrapper?

Cheers

---

### Post by Rocks on 2006-11-12
Ooops... I should have done apt-get install build-essential before compiling the driver :oops:  Thanks to the excellent contribution from [kleeman]("http://www.ubuntuforums.org/showthread.php?t=47615") for this =D> 
Nonetheless, once the driver compiled (succesfully) and modprobed, the kernel patched, the card brought up and all... I still get no network ](*,)  dhcpdiscovers still go out into nowhere :(  
The card works fine under windows but I'd really prefer to use Ubuntu...

Any further help gladly welcome ;) 

P.S. I tried using the windows driver with ndiswrapper : all I got was a fatal error :neutral:

---

### Post by redsax on 2006-11-12
I still cannot install the sk98lin.

I checked sky2.c code, which was dated 2005/07 or so.
This could be the key since it's old? the recent
one at marvell's website is Nov/2006.

When you compiled, did you set cc=gcc.3-4, as said in
Keelman's post? 

Maybe I should just give up on ubuntu and try another linux](*,)

---

### Post by Rocks on 2006-11-13
\\:D/  Victory is mine :mrgreen:  For some odd reason, using static ip on the network @work is functional. Maybe it was dhcp on my home network that has an issue with this driver, but that seems odd. However, I've got the network up and running, which is really great :cool: 

P.S. redsax : using the Marvell driver, did you compile/install the driver + the patch? or only the driver? I did both and although it didn't work straight away, it's functional now.  And I didn't need to set cc=gcc.3-4. If you need any further info, let me know ;)

---

### Post by redsax on 2006-11-13
I still havenot got the luck. ](*,) ](*,) 

The problem with my machine, I think, is it uses a Yukon
88E8056 (device id 4364), which was not supported by sk98lin in edgy.

I should either 
1. install the new driver or 
2. change sky2.c by adding one line.

For 1., when I run install.sh, choosing installation, my computer freezes.

For 2. or choosing patch in 1., I need to compile my kernel?
Then I have the following problem, which I posted in general help
[http://ubuntuforums.org/showthread.php?t=298428](http://ubuntuforums.org/showthread.php?t=298428), but
nobody gave me a help yet.

Could you post your very detailed steps about running sk98lin install.sh?
I greatly appreciate it.

---

### Post by Rocks on 2006-11-14
Hi,

Here is, to my best recollection, the steps I took to succesfully compile the driver :
1) modified #!/bin/sh to #!/bin/bash in install.sh (I presume running sudo sh ./install.sh would have been just as good).
2) sudo apt-get install build-essential
3) sudo ./install.sh -> 1. installation
4) sudo modprobe sk98lin
5) sudo ./install.sh -> 2. generate patch
6) cd /usr/src/linux -> cat "the_patch" where "the-patch" is the info given at the end of the patch creation
and that was it (no kernel re-compile required afterwards).

Note that I have not managed to get DHCP to work yet, I have to use static ip with this card, but at least that works.

Cheers and good luck

---

### Post by Levander on 2006-12-10
.

---

