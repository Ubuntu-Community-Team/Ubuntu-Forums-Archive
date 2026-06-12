---
title: "Ubuntu 9.10 install"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by danman06 on 2010-02-25
Hey all, 

I'm switching over to Ubuntu from windows, and I'm really liking 9.10. My question is I downloaded the ISO and installed from a CD. Once I ran the updates it prompted to run, I checked my disk utilization and it's around 19GB. Is that normal, I see in other forums where people are talking like 8GB, etc.. 

I did just a standard install.

thanks in advance.

---

### Post by johngreth on 2010-02-25
I'm not sure what the expected size should be, but the excess might be old versions of updated packages. You could try running
```
sudo apt-get autoremove
```and
```
sudo apt-get clean
```This will delete any unused packages on the computer.

---

### Post by theozzlives on 2010-02-25
> **danman06 said:**
> Hey all, 

I'm switching over to Ubuntu from windows, and I'm really liking 9.10. My question is I downloaded the ISO and installed from a CD. Once I ran the updates it prompted to run, I checked my disk utilization and it's around 19GB. Is that normal, I see in other forums where people are talking like 8GB, etc.. 

I did just a standard install.

thanks in advance.

I have Karmic installed on a 10 GB partition and have 5.7 GB free. Although I have a seperate /home partition. It has 243.2 GB free on a 320 GB drive. I might also add that I have a 4 GB swap.

---

### Post by danman06 on 2010-02-25
sigh... I hate being a noob.. It's all the junk I let it import from the windows partition into /home/<accountname>

---

### Post by thecliff on 2010-02-26
> **danman06 said:**
> sigh... I hate being a noob.. It's all the junk I let it import from the windows partition into /home/<accountname>

I have never had anyone use the option to import data from Windows -- good to know it works though.

---

### Post by mailprashant07 on 2010-02-26
hi i dont know where to put this. but plzz help me out. i have installed ubuntu 9.10-->working well so far..but not able to connect to the internet...i have [EMAIL="ADSL@+Router"]ADSL2+Router[/EMAIL] modem. when i connect it's wire--> it shows auto eth0 connected-->i donno what it means since i cant surf internet...i also tried various tutorials of ubuntu on connection but i cant find networking in system administration...i mean we have on ubuntu 9.10-->system-->administration-->network tools....i know i am in mess...hence ask for an easy step by step help.....well internet works well on my other computer with windows....ask if you need more info..its urgent..thanks

---

### Post by mailprashant07 on 2010-02-26
> **mailprashant07 said:**
> hi i dont know where to put this. but plzz help me out. i have installed ubuntu 9.10-->working well so far..but not able to connect to the internet...i have ADSL2+Router modem. when i connect it's wire--> it shows auto eth0 connected-->i donno what it means since i cant surf internet...i also tried various tutorials of ubuntu on connection but i cant find networking in system administration...i mean we have on ubuntu 9.10-->system-->administration-->network tools....i know i am in mess...hence ask for an easy step by step help.....well internet works well on my other computer with windows....ask if you need more info..its urgent..thanks
 
by the way how long does it takes to get answered....help me out guys

---

### Post by norbert26 on 2010-02-26
> **mailprashant07 said:**
> by the way how long does it takes to get answered....help me out guys

Start a new thread with your problem in the title so the good folks can see it and respond they don't know its here.

---

