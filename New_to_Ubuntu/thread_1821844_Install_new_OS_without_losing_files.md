---
title: "Install new OS without losing files"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by thatguy93 on 2011-08-09
Hey guys,
Alright so I need some help.
It seems as though no operating systems (at least no ubuntu versions) want to run on my beater laptop.
Now I have some important files I need to recover off of it.
I tried to install ubuntu 11.04 again, I tried Ubuntu 10.04LTS, and I tried Linux Mint. None work. For ubuntu, I get a server error, and a gnome power manager error. I tried abunch of things to fix it, and nothing worked.
So since I have mint on another computer of mine, and like it, I though I would try and install it on the beater laptop, to recover my files.
Well I did, and I selected the option to upgrade from Ubuntu 10.04LTS to Mint 11. And the computer just loads a grub line. I tried typing boot in, and it told me a kernal image was missing.

So here is what I want to do. I want to either be able to access my files on my computer, while using a LiveUSB(but the files are all locked).
Or I want to try and install Mint again.
Now when I get to the "allocate drive space" step, I need to know what to do, in order to NOT lose any files(other than system files of course). 

Basically I want to install Mint, without losing my files.
So can someone please help me? Nicely defined steps would be very helpful.

thank you!

---

### Post by Basher101 on 2011-08-09
Boot from a live CD, run GParted and post a screenshot of it. Also write what you have on what partition (for example on /dev/sda1 mint on /dev/sda2 files)

---

### Post by thatguy93 on 2011-08-09
BTW, the error I get at startup is "There is a problem with the configuration server".

I will boot with LiveUSB, and do as you said.

---

### Post by amjjawad on 2011-08-09
[www.distrowatch.com]("http://www.distrowatch.com")

Pick any distro with a LiveCD feature, download it, check MD5SUM before you burn to a CD or create LiveUSB, when you burn it to a CD try to use 8x for example instead of the MAX speed and boot your machine from that LiveCD.

If you are trying to boot from Ubuntu LiveCD or Mint LiveCD and it doesn't work, then either your download iso is damaged (MD5SUM to be checked) OR the CD is damaged OR something wrong with your CD Drive. 

I'm not sure which OS do you have currently installed but if your files were so important, you should have backed them up. Anyway, just make sure to backup your files while you are booting from the LiveCD (better to an external HDD) and then, we can guide you through the other steps.

Please, list the hardware details of your Laptop.

---

### Post by elgordodude on 2011-08-09
Hopefully by "locked" you mean assigned to another user, usually "user 1000" in a ubuntu live cd. If you mean they're encrypted and you can't log in with your username and password then I don't know how much I can help.

Easy way:

1 locate the files you want to save

2 open a terminal

3 type sudo nautilus in terminal

4 drag folder / file from window into terminal

5 press enter twice

This should open a window where you can now see and copy the files that were in the folder to wherever you're copying them to. Depending on how much data you have and how you're transferring it this may take a very long time.

Not sure how bad a "beater" is, but if Mint gives you trouble you might want to consider, Lubuntu or Xubuntu, if you still have trouble I've used puppy to revive a couple of sytems that seemed destined for the dump.

---

### Post by Johnb0y on 2011-08-09
or asking around/buy an USB to hard drive adapter... take hard drive out and connect to the other machine... this should allow access to copy files over from hard drive to hard drive... Theoretically... :confused:

hope that helps in anyway... thats how i recovered my 29GB of music and vids from an old hard drive that the OS failed on...:D

---

### Post by thatguy93 on 2011-08-09
here's a screenshot. The HD is full because of foremost. It made and output file I cannot delete, which takes up all the space.

---

### Post by thatguy93 on 2011-08-09
> **amjjawad said:**
> [www.distrowatch.com]("http://www.distrowatch.com")

Pick any distro with a LiveCD feature, download it, check MD5SUM before you burn to a CD or create LiveUSB, when you burn it to a CD try to use 8x for example instead of the MAX speed and boot your machine from that LiveCD.

If you are trying to boot from Ubuntu LiveCD or Mint LiveCD and it doesn't work, then either your download iso is damaged (MD5SUM to be checked) OR the CD is damaged OR something wrong with your CD Drive. 

I'm not sure which OS do you have currently installed but if your files were so important, you should have backed them up. Anyway, just make sure to backup your files while you are booting from the LiveCD (better to an external HDD) and then, we can guide you through the other steps.

Please, list the hardware details of your Laptop.

Okay I will try that.
I was going to backup the files, but I had to research how to do that. By the time I had it figured out, poop had already hit the fan.

Hardware:
Intel R pentium M processor 1.73GHz
516mb DDR2 RAM
ATA HTS541040G9AT00 40GB hard drive

---

### Post by thatguy93 on 2011-08-09
I think I might just buy a HD to USB adapter, and trash the laptop. Then I can just transfer the files over to another computer. 
(Thanks Johnb0y!)

---

### Post by amjjawad on 2011-08-09
> **thatguy93 said:**
> 
Hardware:
Intel R pentium M processor 1.73GHz
516mb DDR2 RAM
ATA HTS541040G9AT00 40GB hard drive

With such Hardware, better to give Lubuntu or Xubuntu a try.

Ubuntu 10.04 and Mint 11 will work but definitely not as fast as Lubuntu on the same machine.

I recommend Lubuntu 11.04 and if you don't like LXDE then Xubuntu.

I have installed Ubuntu 11.04 on P4 with less than 512MB RAM. It's ok but whenever I open two browser, it gets so slow.

---

### Post by amjjawad on 2011-08-09
> **thatguy93 said:**
> I think I might just buy a HD to USB adapter, and trash the laptop. Then I can just transfer the files over to another computer. 
(Thanks Johnb0y!)

You do NOT need that, at least yet.

---

### Post by Johnb0y on 2011-08-09
> **thatguy93 said:**
> I think I might just buy a HD to USB adapter, and trash the laptop. Then I can just transfer the files over to another computer. 
(Thanks Johnb0y!)

> might just buy a HD to USB adapter, and trash the laptop Epic idea if you getting issue like these ones!

> Then I can just transfer the files over to another computer thats the idea... but also you get to do the same if any friends or family have the issue and look like a proper "geek!" lol!

> (Thanks Johnb0y!) your welcome! glad i could help! :)

---

### Post by dFlyer on 2011-08-09
Is there any reason you didn't backup your data before you tried to install another OS?

---

