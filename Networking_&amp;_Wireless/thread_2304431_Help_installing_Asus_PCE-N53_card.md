---
title: "Help installing Asus PCE-N53 card"
date: 2015-11-26
forum: Networking &amp; Wireless
---

### Post by kyle62 on 2015-11-26
I am in the process of making a dual boot on my desktop, and have very little experience on Ubuntuu.  I have tried to follow the instructions to install the drivers on Ubuntuu 14.04.03 and keep getting errors, and failing.  After reading the information on this site, I am still lost.  can someone please help me with this.  I hate to say it, but explain it to me in the simplest terms you can, with all the instructions, cant make any assumptions.  I have done some coding and such, but this is not working for me and i need to know linux for my job.  Thanks for the help!

---

### Post by chili555 on 2015-11-26
Let's start with all the facts, please: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by Spency on 2015-11-27
\Chili, I'm surprised you did not referece me in your post. 

@OP:
If you're trying to install drivers for an ASUS PCE-N53 PCI card, instruction can be found [here]("https://bbs.archlinux.org/viewtopic.php?id=152960&p=3") - read the 5th post from the top of the page.

---

### Post by Spency on 2015-11-27
Sorry there are 2 additional steps... I'll make it easy. This is the complete list of steps:

What you need to do to get your asus PCE-N53 card to work with ubuntu... I like to enter SU early on.
Open Terminal (ctrl+alt+t) and copy + paste + enter each step.  
```

1. cd Downloads
2. wget [http://dlcdnet.asus.com/pub/ASUS/wireless/PCE-N53/Linux_PCE_N53_1008.zip](http://dlcdnet.asus.com/pub/ASUS/wireless/PCE-N53/Linux_PCE_N53_1008.zip)
3. sudo apt-get install unzip
4. unzip Linux_PCE_N53_1008.zip2
5. cd Linux
6. sudo su
7. tar -xvjpf DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326.tar.bz2
8. cd DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326
9. wget [http://gridlox.net/diff/rt5592sta_fix_64bit_3.15.patch](http://gridlox.net/diff/rt5592sta_fix_64bit_3.15.patch)
10. patch -p1 < rt5592sta_fix_64bit_3.15.patch11. make 
11. make
12. make install 
13. modprobe rt5592sta

```

---

### Post by kyle62 on 2015-11-27
> **Spency said:**
> Sorry there are 2 additional steps... I'll make it easy. This is the complete list of steps:

What you need to do to get your asus PCE-N53 card to work with ubuntu... I like to enter SU early on.
Open Terminal (ctrl+alt+t) and copy + paste + enter each step.  
```

1. cd Downloads
2. wget [http://dlcdnet.asus.com/pub/ASUS/wireless/PCE-N53/Linux_PCE_N53_1008.zip](http://dlcdnet.asus.com/pub/ASUS/wireless/PCE-N53/Linux_PCE_N53_1008.zip)
3. sudo apt-get install unzip
4. unzip Linux_PCE_N53_1008.zip2
5. cd Linux
6. sudo su
7. tar -xvjpf DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326.tar.bz2
8. cd DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326
9. wget [http://gridlox.net/diff/rt5592sta_fix_64bit_3.15.patch](http://gridlox.net/diff/rt5592sta_fix_64bit_3.15.patch)
10. patch -p1 < rt5592sta_fix_64bit_3.15.patch11. make 
11. make
12. make install 
13. modprobe rt5592sta

```

Thank you for the reply, I can not attempt it right now, but once i get home I definitely will do this.  My next problem will be installing the graphics card however i feel that wont be quite as hard.

---

### Post by chili555 on 2015-11-29
> **Spency said:**
> \Chili, I'm surprised you did not referece me in your post. 

@OP:
If you're trying to install drivers for an ASUS PCE-N53 PCI card, instruction can be found [here]("https://bbs.archlinux.org/viewtopic.php?id=152960&p=3") - read the 5th post from the top of the page.Are all the PCE-N53s using the exact same chipset? I usually like to verify the pci.id before I proceed.

---

### Post by kyle62 on 2015-11-29
Ok so that did work but it doesnt see 5ghz signals how do i changr that

---

