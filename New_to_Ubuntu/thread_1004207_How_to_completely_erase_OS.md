---
title: "How to completely erase OS"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by tegnoto89 on 2008-12-07
Okay, I'm going to switch to kubuntu, and I need to know how to completely erase ubuntu and start with a clean hard drive (I don't want to dual boot).  Also, does my hard drive need to be formatted somehow to boot the kubuntu cd?

---

### Post by OutOfReach on 2008-12-07
You can format the drive while installing Kubuntu, I am positive that there is an option for that.
No, the LiveCD doesn't need a formated drive to boot since it doesn't touch the hard drive at all.

---

### Post by cartisdm on 2008-12-07
When you run the liveCD for kubuntu it will start the partitioner once you get a little bit into the installation.  Choose "Guided: Use entire disk."  Be sure you pick the correct place of where you want to install.

It will erase the old OS completely and format everything for you.  Easy as cake.

---

### Post by jpmelos on 2008-12-07
You don't need to completely wipe Ubuntu out of your hard drive before installing Kubuntu.

All you have to do is insert the Kubuntu CD into your drive (if your BIOS is already configured to boot from CD) and then look for the Install Kubuntu option as the boot completes.

During the installation, you will be asked what kind of installation you want, then you choose the full hard drive option (may be the Assisted Install option, or something like that).

When you remove the CD from the drive and boot your computer, Kubuntu will be booted.

Hope it helps you somehow.

---

### Post by zvacet on 2008-12-07
@ **tegnoto89**

Before you do anything be sure that you have separate home partition.[Here]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") is good guide how to do it.If you don´t want to that just back up your home.

In second solution you don´t have to do anything described above.If you just want to switch desktops (from Ubuntu to Kubuntu) read [this]("http://psychocats.s465.sureserver.com/ubuntu/purekde") under Remove Ubuntu.

---

### Post by cartisdm on 2008-12-07
> **jpmelos said:**
> You don't need to completely wipe Ubuntu out of your hard drive before installing Kubuntu.

All you have to do is insert the Kubuntu CD into your drive (if your BIOS is already configured to boot from CD) and then look for the Install Kubuntu option as the boot completes.

During the installation, you will be asked what kind of installation you want, then you choose the full hard drive option (may be the Assisted Install option, or something like that).

When you remove the CD from the drive and boot your computer, Kubuntu will be booted.

Correct me if I'm wrong, but I believe this will erase the ubuntu OS off the harddrive, and install the kubuntu OS in it's place.  Either way, it still clears out the harddrive

---

### Post by tegnoto89 on 2008-12-07
Just went through - I chose to manually format the partition, and I didn't know how to create swap space so I came back here on my buddy's computer.  I chose use full- guided, and it seems to be installing alright.  Thanks!!

---

### Post by jbrown96 on 2008-12-07
As others have said you can use the "use entire drive" option. However, if you are dual booting or have a specific parition setup don't do that. Wherever your / is mounted just select edit and change it to the filesystem you want, then choose to mount it as / and format it.

---

### Post by jpmelos on 2008-12-07
> **cartisdm said:**
> Correct me if I'm wrong, but I believe this will erase the ubuntu OS off the harddrive, and install the kubuntu OS in it's place.  Either way, it still clears out the harddrive

That's right. That's why I said "**before installing Kubuntu**". I never said, though, it would never erase the old OS.

---

### Post by magnus0 on 2008-12-07
If you have Ubuntu, you could just install the kubuntu-desktop package and you get the exact same effect, when installing Kubuntu from a cd.

---

### Post by zvacet on 2008-12-08
You can not install kubuntu-desktop from live CD.You can install kubuntu-desktop via net or from alternate CD.I´ll be glad if I´m wrong.

---

