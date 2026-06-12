---
title: "Another noob question about dual-boot."
date: 2010-02-26
forum: New to Ubuntu
---

### Post by lockalidiot on 2010-02-26
Again, hello you all wonderful people!

Simply put: I have pure Ubuntu 9.10 install on my 'top. Is it possible to install Vista to dual-boot without loosing data stored on ubuntu partition? I have a lot of empty HD space, about 800 GB(1 TB HD, 6 GB RAM, 17 GB SWAP) Please ask further questions if I was unclear.

Cheers!

---

### Post by skymera on 2010-02-26
You can install Vista without affecting Ubuntu.

I suggest you resize the Ubuntu partition from the Ubuntu LiveCD BEFORE installing Vista.
If you have free space, you can install Vista.

Also note that Vista will bomb your bootloader and you will have to reinstall GRUB

---

### Post by lockalidiot on 2010-02-26
Thanks for quick answer!

I'm figuring out my options here. So, when/if I resize my ubuntu partition to about 500 GB, I won't loose any data IF everything goes well?
Is there any HOW-TO guides for idiots on doing this?

---

### Post by skymera on 2010-02-26
You can resize your paritition in Ubuntu fine and if everything goes well (Which it should!) no harm will be done.

One you have your desired free space, install vista.

But keep the live CD to reinstall GRUB after

This link: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Is a great start to learning Ubuntu and has some common questions answere on there

---

### Post by Silent Warrior on 2010-02-26
Also, feel free to reduce the size of your swap-partition. I doubt you need more than 4 Gb, if that! Myself, I've been using between 2 and 3 Gb, and so far I haven't even noticed any swap-usage in Ubuntu unless a process had got stuck in some kind of number-crunchy loop, with 3 Gb system RAM. Besides that, do as skymera says.

---

### Post by zeroseven0183 on 2010-02-26
Remember to backup your data first before doing something just to be sure.
Follow the instructions on [Installing Windows after Ubuntu]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu") and everything will be fine.

---

### Post by lockalidiot on 2010-02-26
Again, thank you all for your answer. This forum and its members with their collective knowledge of infinite proportions is one of the reasons it is so easy to love Ubuntu.

[QUOTE=Silent Warrior]Also, feel free to reduce the size of your swap-partition. I doubt you need more than 4 Gb, if that! Myself, I've been using between 2 and 3 Gb, and so far I haven't even noticed any swap-usage in Ubuntu unless a process had got stuck in some kind of number-crunchy loop, with 3 Gb system RAM. Besides that, do as skymera says.[/QUOTE]

I thought of this, but lazy as I am, I feel no reason to do reduce my swap size, as I have plenty of space to spare.

---

