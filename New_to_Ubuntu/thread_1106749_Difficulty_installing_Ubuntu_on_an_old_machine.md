---
title: "Difficulty installing Ubuntu on an old machine"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-26
Hi there, I am having a bit of difficulty getting the Ubuntu installer to work on an old machine. I have already installed the 64 bit version successfully on my brand new laptop with no problems and now I just burnt a disk of the 32 bit version to install on this machine:

Dell
Pentium III 733mhz
128mb SDRAM
CD-ROM Drive
10GB IDE HDD
Onboard Sound
Network Port

DSE 19" Widescreen LCD (connected via VGA)
Keyboard and Mouse


Basically I boot into the CD, choose English, then choose "install Ubuntu" and it will show the splash screen and load for quite a while. Once it has loaded the mouse will appear and the Ubuntu default background shows up, but then it stops. Nothing happens from then on... the CD keeps spinning but no menus pop up like they should do. I left it for 15mins like this and came back to find it exactly the same except the mouse and keyboard were frozen.

I tried the Live CD mode and encountered something similar. Help please?

I am using a Ubuntu 8.10 i386 CD.

---

### Post by kerry_s on 2009-03-26
128mb ram is not enough, you need to go lighter.

---

### Post by humphreybc on 2009-03-26
I was planning on sticking 1GB in it (memory is so cheap nowadays) so would that be sufficient?

---

### Post by Ptero-4 on 2009-03-26
1GB is more than enough to get it going.

---

### Post by humphreybc on 2009-03-26
Sweet. Am I looking at DDR or DDR2 SDRAM?

---

### Post by cjv8888 on 2009-03-26
> **humphreybc said:**
> Hi there, I am having a bit of difficulty getting the Ubuntu installer to work on an old machine. I have already installed the 64 bit version successfully on my brand new laptop with no problems and now I just burnt a disk of the 32 bit version to install on this machine:

Dell
Pentium III 733mhz
128mb SDRAM
CD-ROM Drive
10GB IDE HDD
Onboard Sound
Network Port

DSE 19" Widescreen LCD (connected via VGA)
Keyboard and Mouse


Basically I boot into the CD, choose English, then choose "install Ubuntu" and it will show the splash screen and load for quite a while. Once it has loaded the mouse will appear and the Ubuntu default background shows up, but then it stops. Nothing happens from then on... the CD keeps spinning but no menus pop up like they should do. I left it for 15mins like this and came back to find it exactly the same except the mouse and keyboard were frozen.

I tried the Live CD mode and encountered something similar. Help please?

I am using a Ubuntu 8.10 i386 CD.

Hi, I have a machine with 170 MB ram.  I can get Xubuntu to run on it but very painfully. (also needed the alternate CD to install -again painfully ) 
Finally got Puppy linux to run and it worked like a breeze on it.  Even 2 different USB wifi adapters works out of the box.
However, if you can add 1 GB to the RAM, it will be ok.:)

---

### Post by humphreybc on 2009-03-26
Cheers I will get 1GB for it. Just makes it simpler if I have Ubuntu on all of my machines rather than playing around with other distros. Also Ubuntu is the most supported.

---

### Post by linux_tech on 2009-03-26
> **humphreybc said:**
> Sweet. Am I looking at DDR or DDR2 SDRAM?

Its most likely DDR but best to remove the RAM and check to make sure

---

### Post by balaknair on 2009-03-26
> **humphreybc said:**
> Sweet. Am I looking at DDR or DDR2 SDRAM?

Most older mobos and processors do not support DDR/DDR2, you'll need to check your mobo documentation to be sure(or the manufacturer's website). Since your processor is an older P3, I'm guessing the mobo is old too, approximately 8 years old, and back then most mobos were SDRAM(I think DDR1 was just being introduced back then).

You'll probably need plain old SDRAM(DDR1 if you're lucky), and I'm not even sure you can get new modules. You might need to hunt around a bit for used modules, and it might not be as cheap as a brand new DDR2 module. 256-512 MB would be enough to get Ubuntu running pretty decently, but again, it depends on being able to find compatible SDRAM memory modules.

---

### Post by humphreybc on 2009-03-26
I just ordered 512mb of PC100 SDRAM which is what it says on the currunt modules. I'm going to install Xubuntu on the machine I think anyway.. mainly because I can do it now while I wait for the RAM to arrive by courier. And besides I think Xubuntu should run better with the old processor, no?

---

### Post by balaknair on 2009-03-26
> **humphreybc said:**
> And besides I think Xubuntu should run better with the old processor, no?

Yep. XFCE on Xubuntu may not be as pretty or feature-loaded as Gnome(Ubuntu), but it definitely feels snappier on old hardware. With 512MB RAM, plain Ubuntu without desktop effects runs quite decently too. It's stuff like Open Office that tends to slow the system down.

And if you want to switch to Gnome/Ubuntu later on, you don't have to reinstall the whole thing, just install the Gnome desktop packages(sudo apt-get install ubuntu-desktop).

---

### Post by tarps87 on 2009-03-26
It will install on you current spec (I have Intrepid running on 128MB ram, 300MHzcpu. Slow but works), you will need to use the alternative installer though. This is available from here:
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by Mze on 2009-03-26
PIII processor at 733 MHz - supported memory modules will be SDRAM 100/133. I'd go for 133 SDRAM if you can find it.

Your motherboard will most probably support a max of 512 RAM no more than that.

Look for your motherboard id number, since you already opened the case and google it for more info.

---

