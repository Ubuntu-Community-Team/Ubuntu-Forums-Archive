---
title: "Cannot load.Not enough RAM"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by Kenc3 on 2011-05-28
I have an old Acer desktop that is supposed to have 256MB of RAM. The computer only sends the message that I have 253MB. Ubuntu will not load because it says I need 256MB.
Is there a dist that uses less than 256MB?:popcorn:

---

### Post by akand074 on 2011-05-28
I've never used or even looked at any, but I know people have often recommended [PuppyLinux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm") for low resource machines, I think I've heard of something called "Damn small Linux" there are likely another few that people could mention. Maybe Lubuntu (Ubuntu with LXDE Desktop Environment).

---

### Post by Macskeeball on 2011-05-28
[www.lubuntu.net](www.lubuntu.net)

The reason for the discrepancy may be a GPU that is integrated rather than dedicated. That means it shares some RAM with the CPU instead of having its own VRAM.

---

### Post by The Real Dave on 2011-05-28
Try PuppyLinx, Slitaz, DamnSmallLinux, TinyCore etc, all distros which are designed specifically for old/under-powered machines.

In fact, you can install Ubuntu, starting with a clean command line, and build up, even adding a Gnome desktop (or preferably something lighter, like Openbox) and still have RAM to spare, so long as you do so correctly. Ubuntu Docs [here ]("https://help.ubuntu.com/community/Installation/LowMemorySystems")should help.

---

### Post by Dustin2128 on 2011-05-28
SliTaz is what I'd go for personally. Though you might go for something like debian or arch which you could "build from the ground up" so to speak. Usually critical ram mass for me to install a non lightweight distro is 384Mb though.

---

### Post by Kenc3 on 2011-05-28
Thanks everyone. I will look into these.

---

### Post by NormanFLinux on 2011-05-29
AntiX will work on old machines. With a GUI desktop environment.

---

### Post by jerenept on 2011-05-29
Try [FreeNAS.]("http://freenas.org/") It's unlikely any distro will be useful on such low resources.

---

### Post by Allavona on 2011-05-29
> AntiX will work on old machines. With a GUI desktop environment.

Agreed. AntiXs' minimum is 128GB. Read more here:

[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

---

### Post by Dustin2128 on 2011-05-29
> **Allavona said:**
> Agreed. AntiXs' minimum is 128GB. Read more here:

[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)
128GB of RAM? you'd need at least 3 motherboards for that much!

---

### Post by aysiu on 2011-05-29
Ubuntu will actually load just fine. You just can't use the Desktop CD to load it. You can use the Alternate CD or mini.iso.

---

### Post by Macskeeball on 2011-05-29
> **Dustin2128 said:**
> 128GB of RAM? you'd need at least 3 motherboards for that much!

Heh, yeah. It reminds me of Weird Al's song ["It's All About the Pentiums."](http://www.youtube.com/watch?v=qpMvS1Q1sos)

I got me a hundred gigabytes of RAM
I never feed trolls and I don't read spam
Installed a T1 line in my house
Always at my PC, double-clickin' on my mizouse

---

### Post by BigSilly on 2011-05-29
Definitely try [Peppermint Ice from here]("http://peppermintos.com/"). It's great. Based on Ubuntu but very light. Uses OpenBox, so it still looks brilliant. We're using it on our Eee 701 4G Surf. :)

---

### Post by NormanFLinux on 2011-05-29
LOL... He meant 128 MB RAM. That means if an old Pentium that ran Windows 95 for which the upper memory limit was 1 GB, it should be blazing fast. There's no need to throw out an old computer that can't run the latest version of Windows.

---

### Post by uRock on 2011-05-29
Moved to ABT.

---

### Post by SEisch on 2011-05-29
I have an old Compaq that also has 256 megabytes of memory and I used the mini ISO.  It worked much better that the larger live CD ISO.  It does require that the computer be connected to the internet to fully install though.  It was a pretty easy installation from what I remember.  It just took a while for everything to download and install.

---

