---
title: "My PC is now unable to boot from CD, Please help"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by nimdave24 on 2010-06-01
Dear Team

I am a new joinee for Linux. I am not a computer graduate or studied anything about computers, but with time I ve learnt a bit about it. Well I was a routin windows user and just 1-2 months back i have came to know much about Linux OS and I was shocked, amazed, surprised, and excited to try linux. Since its a free OS i thought that nothing is wrong to try it at least. 

Then I have came to know abt Ubuntu and i heard that they are also sending free CDs, I have applied for one free CD and surprisingly It came to my home as well. I have 3 computers at my home, all were run on win-xp previously. all 3 are ancient PC with old low configuration. but my normal pc use is surf internet and to see normal word / excel files om my mail ID, so even i dont need a high configuration PCs.

Now I am a very much new to linux and do not know much about it so I need an OS which is easy to install and has a great community, so I ve finalized my choice on ubuntu. Now I have installed Ubuntu 10.04 in one of my ancient PC (Celeron 465 Mhz, 256 Ram, 20GB HDD), I have install it without making any partition on my HDD (So only one partition of 20GB). it runs ok but when it comes to speed its damn slow, and when i m opening Open office its hell slow, i have to wait for atlest a minute to open OO file. and it is the same story with almost all applications, 
In short i found ubuntu 10.04 very slow on my that PC. The reasons behind it may be Ubuntu 10.04 has so many unnecessary programs. whatever but i have make my mind to change the OS from Ubuntu. 
Now I had 2 Option one is back to WIn-xp or
another linux os which is fast on my PC
I have done lots of research and decided to try small linux OS which may be faster and easy to use, I have made the CDs for Puppy-5, Slitaz-3.0 and DSL4.4.10, Since all of them runs on RAM, I have decided to atleast try all of them and whichever is more suitable to me I will install it on my Hard disk. and i would have a small fast OS!! 

Now comes the twist in the tale!!!
The CDs of Puppy, DSL, Slitaz are ok ,working nicely, i have tried it on my another PC (Which has XP on it ), puppy & DSL working nicely on it, but my Ubuntu system is not taking anything.  Its not getting booted from those CDs, I have tried every physical means & ways to get it booted but got failure every time. I have change CD Drives, CD Cables, Changed Jumpers as many times as possible, changed CDs and bios changes o many time, but my system is not gettinf booted from the CD, even I have tried Win-XP CD also but my system is not taking that as well. 

Even I select First Boot from CD, normal Ubuntu starts and when normal desktop comes it shows me CD drive with its CD name (Like Puppy, DSL XP Etc), means my PC takes CD drive but not getting booted from it.

Any suggestion? friends

N.B. My Hard disk and CD ROM drives works on the same cable, because only one slot on the mother board is working and please dont ask me to change the jumper or put a jumper on mother board as well because dont forget i have already install ubuntu on the same system with the same circumstances (With one cable only and with jumper put at the right place)

---

### Post by Iowan on 2010-06-01
I upgraded this machine to 512M RAM before I upgraded to Hardy (8.04). 
Have you tried unplugging the HD to see if machine would boot from CD?

I presume you're using CD-R's instead of CD-RW's - some machines/players won't boot from CD-RW.

---

### Post by Cathhsmom on 2010-06-01
Is your cd drive a dvd drive or purely a cd drive.  If you have a purely cd drive, it will not read the installation dvd.

---

### Post by acrazyplayer on 2010-06-01
I understand what you're saying but I don't think any of us can help. It sounds like you tried just about everything. The best way to make 100% sure is to disconnect your hard drive and any usb drives or other accessories and then try to boot from your CD drive. Make sure the jumper is set on cable select - its usually always the best choice - and try then to run a CD to boot from. 

edit: also get rid of openoffice and try abiword or something much smaller instead. To get rid of openoffice the best way is to "sudo apt-get purge openoffice*"

---

### Post by formaldehyde_spoon on 2010-06-01
I had a similar problem recently:

a computer that would boot DSL or a Gparted liveCD, but refused  boot an Ubuntu LiveCD, no matter what version, no matter what type of disk, no matter how slow I burnt them, no matter what computer burnt them.

In the end I had to download and burn the Ubuntu Minimal CD [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
install that (without adding any extra packages during installation, because that caused errors) and once it had installed and booted to a command prompt I finished the installation with 'sudo apt-get install ubuntu-desktop' which downloaded and installed the rest of Ubuntu.

I don't know if that's a suitable solution for you, but your problem sounds identical to mine, and that worked for me.

---

### Post by nimdave24 on 2010-06-02
> **Iowan said:**
> I upgraded this machine to 512M RAM before I upgraded to Hardy (8.04). 
Have you tried unplugging the HD to see if machine would boot from CD?

I presume you're using CD-R's instead of CD-RW's - some machines/players won't boot from CD-RW.


Its a DVD Combo Drive (DVD ROM + CD Writer), I have write puppy with the same DVD Combo drive, but that puppy is not booted from the CD, now this puppy CD runs excellent on another system (Which has Win-XP installed)

I have tried to bood CDs like Win-XP also in this system but no cd get boted in this system ,which runs excellent on other system, secondly the DVD combo is also in working condition because that i must already have checked it in other system, so, DVD combo is also in working

---

### Post by nimdave24 on 2010-06-02
Its a DVD Combo Drive (DVD ROM + CD Writer), I have write puppy with the same DVD Combo drive, but that puppy is not booted from the CD, now this puppy CD runs excellent on another system (Which has Win-XP installed)

I have tried to bood CDs like Win-XP also in this system but no cd get boted in this system ,which runs excellent on other system, secondly the DVD combo is also in working condition because that i must already have checked it in other system, so, DVD combo is also in working

---

### Post by fooman on 2010-06-02
double check your bios settings and make sure you have it set to boot from cd.

some systems may require you to press any key as it starts to get the cd to boot....watch for such a message as it is booting.

---

### Post by nimdave24 on 2010-06-02
> **acrazyplayer said:**
> I understand what you're saying but I don't think any of us can help. It sounds like you tried just about everything. The best way to make 100% sure is to disconnect your hard drive and any usb drives or other accessories and then try to boot from your CD drive. Make sure the jumper is set on cable select - its usually always the best choice - and try then to run a CD to boot from. 

edit: also get rid of openoffice and try abiword or something much smaller instead. To get rid of openoffice the best way is to "sudo apt-get purge openoffice*"


Yes Ok
When I have removed hard disk from my system, it has worked, i have used puppy on RAM, 
but again u must be agree with me thats not the final solution, I am happy that when we remove hard disk my system boots from CD but when again i have attached hard disk, same problem, it was not getting booted from CD.

Please my pros help me,

I have even thought of install win-xp again, but then I remembered that my system is not booting from CD!!!!

Anyway I wish somebody may have the solution 

Thanks again to show me atleast my system is booting but without HDD
Have fun same as i m havin with my system

---

### Post by nimdave24 on 2010-06-02
> **Iowan said:**
> I upgraded this machine to 512M RAM before I upgraded to Hardy (8.04). 
Have you tried unplugging the HD to see if machine would boot from CD?

I presume you're using CD-R's instead of CD-RW's - some machines/players won't boot from CD-RW.


Ok

When I have removed hard disk from my system, it has worked, i have used  puppy on RAM, 
but again u must be agree with me thats not the final solution, I am  happy that when we remove hard disk my system boots from CD but when  again i have attached hard disk, same problem, it was not getting booted  from CD.

Please my pros help me,

I have even thought of install win-xp again, but then I remembered that  my system is not booting from CD!!!!

Anyway I wish somebody may have the solution 

Thanks again to show me atleast my system is booting but without HDD
Have fun same as i m havin with my system

---

### Post by nimdave24 on 2010-06-02
> **formaldehyde_spoon said:**
> I had a similar problem recently:

a computer that would boot DSL or a Gparted liveCD, but refused  boot an Ubuntu LiveCD, no matter what version, no matter what type of disk, no matter how slow I burnt them, no matter what computer burnt them.

In the end I had to download and burn the Ubuntu Minimal CD [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
install that (without adding any extra packages during installation, because that caused errors) and once it had installed and booted to a command prompt I finished the installation with 'sudo apt-get install ubuntu-desktop' which downloaded and installed the rest of Ubuntu.

I don't know if that's a suitable solution for you, but your problem sounds identical to mine, and that worked for me.

Dear Sir, 
Ubuntu 10.04 full version is already installed. My problem is my system now not booting for CD, whatever OS i try its never boots from CD drive when HDD is attached with my system, when i remove HDD from my system its get booted , i have already run puppy on my RAM , but again when i attached HDD and booted again Ubuntu 10.04 started .

If my system is ready to boot then i would rather boot Puppy or may be win-xp instead of Ubuntu minimal install!!

Anyways your suggestion would be very helpful to me before i had installed Ubuntu 10.04, but now its already too late, 
Even I had made blunders in terms of not made partitions in my HDD during Ubuntu installation. its only one part of entire 20GB HDD.
Anyways thanks again

---

### Post by eriktheblu on 2010-06-02
Your system specs are a bit low for a full Ubuntu experience.

Open Office is a notorious resource hog; Abiword and Gnumeric are lighter. You might also replace the Gnome desktop with LXDE or another light environment.

---

### Post by nimdave24 on 2010-06-03
> **eriktheblu said:**
> Your system specs are a bit low for a full Ubuntu experience.

Open Office is a notorious resource hog; Abiword and Gnumeric are lighter. You might also replace the Gnome desktop with LXDE or another light environment.

Dear sir 

Ubuntu 10.04 is already installed and running OK (not so fast but fairly ok, as i am agreed with you that OO is taking too lomg time to open but still the rest application and internet going at a decent speed)

My problem is now my system is booting any other CD, i want to remove ubuntu from my system, but anyhow its not booting fro any CD (Neither any linux not win-xp)

I want to remove ubuntu 10.04 and want to install puppy instead, but whatever CD i put in CD drive, my system is not booting form CD thats my problem.

Hope you may have any solution

---

### Post by eriktheblu on 2010-06-03
Given that you have successfully used the disk to boot on other machines, we can probably rule out the disk as the problem.

The problem must be with your hardware. Most likely it is in your BIOS configuration. My recommendation is to play around with your boot order. You should be able to identify the optical disk, and your HDD.

---

