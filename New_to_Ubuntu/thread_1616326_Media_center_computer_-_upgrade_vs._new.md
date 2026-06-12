---
title: "Media center computer - upgrade vs. new"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by anigodin on 2010-11-08
Hello,

My media center computer is a Pentium 4 1.7 GH with 768 Mb of ram. I have 3 HD on this computer:
40 GB - system HD with ubuntu 10.10 installed (two weeks ago)
60 GB & 250 GB - data HD.

My current Video card is Nvidia MX 440 with 128 Mb.

Before the current OS I had on this computer Mythbuntu 8.04 for over 2 years. I destroyed the system by trying to upgrade the OS from 8.04 to 8.10 and then to 9.04. after the 9.04 upgrade, the computer started but the X session failed.

After consulting a friend with much more experience with ubuntu I installed unbuntu 10.10 from scratch. the X session starts but with half the max resolution of my TV (samsung 40" LCD). the Nvidia driver is not installed and I understood there is a reported bug about the Nvidia driver and Ubuntu 10.10.

Since I don't have Mythbuntu any more, my friend recommended I'll use XBMC instead. however, since my video card have only 128 MB, the XBMC is very heavy and the system barely move. I read about is a bit and decided to try Moovida. but it's even worse..

So now I watch movies using SMPlayer and wondering what to do:
1. Find a new AGP video card with at least 512 MB and install it (in Israel where I live they sell AGP cards for about 70-150$).
2. Buy a new media computer, either HTPC of just a new comp with a good card. the prices starts for about 250$ and up.

I know this is not a regular question for this forum, but I'd appreciate any insight.

Many thanks.

---

### Post by mastablasta on 2010-11-08
why not put a 10.04 version on it? maybe drivers work there?!
 
also why not try again with 10.04 mythbuntu?
 
graphics card should be strong enough to play movies and such.
 
how about only upgrading processor and RAM?

---

### Post by cascade9 on 2010-11-08
> **mastablasta said:**
> graphics card should be strong enough to play movies and such.
 
how about only upgrading processor and RAM?

For video cards with no VAAPI, VDPAU or XvBA, as far as video goes everything is done on the CPU. You'd need to get a nVidia 8XXX card or higher to support VDPAU, and there is no AGP version of any of the 8XX cards. 

CPU is pretty much unupgradable. P4 1.7 GHz is socket 423 only (AFAIK anyway), and the fastest socket 423 CPU is 2.0GHz..not worth it compard to a 1.7GHz. 

RAM should be upgradable, but if its a SDRAM P4, you'll pay way to much for not much RAM. If its RDRAM, you'd pay more for RAM than a new system...DDR is about the only upgrade thats not going to cost far, far more than any benefits. But more RAM wont make your movies play well.....

I'd probably go for a new computer, depending on what you can get for how much $ (OK, shekels)

---

### Post by anigodin on 2010-11-08
> **cascade9 said:**
> For video cards with no VAAPI, VDPAU or XvBA, as far as video goes everything is done on the CPU. You'd need to get a nVidia 8XXX card or higher to support VDPAU, and there is no AGP version of any of the 8XX cards. 

CPU is pretty much unupgradable. P4 1.7 GHz is socket 423 only (AFAIK anyway), and the fastest socket 423 CPU is 2.0GHz..not worth it compard to a 1.7GHz. 

RAM should be upgradable, but if its a SDRAM P4, you'll pay way to much for not much RAM. If its RDRAM, you'd pay more for RAM than a new system...DDR is about the only upgrade thats not going to cost far, far more than any benefits. But more RAM wont make your movies play well.....

I'd probably go for a new computer, depending on what you can get for how much $ (OK, shekels)

Thank you.
I I dont think I'll be able to find a new cpu for this computer in Israel. its a small market here and out-dated stuff is hard to come by. 

Your andwer only made it clearer to me that a new computer is the most logical solution.

Thanks again.

---

### Post by aeiah on 2010-11-08
if you install the nvidia drivers (probably easiest just to install ubuntu 10.04) you shouldnt have a problem playing none-hd content on xbmc.

perhaps you could check out one of the xbmc live installs. they're built on ubuntu.

---

### Post by anigodin on 2010-11-08
> **mastablasta said:**
> why not put a 10.04 version on it? maybe drivers work there?!
 
also why not try again with 10.04 mythbuntu?
 
graphics card should be strong enough to play movies and such.
 
how about only upgrading processor and RAM?

I installed ubuntu 10.10 and not mythbubtu 10.04 because the instalation of the 8.04 version was pretty annoying and took hours. and I needed a lot of help because my knowledge in installing systems like that is not great (dragged my friend 100 km to my home to help me :-)).
If the instalation process is shorter and easier I'll go back to mythbuntu. it worked fine with my elderly computer (that is of course if there is no problem with Nvidia drivers in this version).

---

### Post by anigodin on 2010-11-10
Well,

I installed Mythbuntu on the computer from scratch. everything works fine. the system is not using the Nvidia driver so there's no problem and I even get the full resolution of the TV.

However, I have a strange problem (which I'm not sure this is the right place to ask about). I have a Seagate 1TB External hard drive which hold all my movies. when I plug it in it appear on the desktop as 'Expansion Drive' and I can access it and write on it with no problem. but when I configure it as the movie storage in MythTV there are no movies in the list.

I suspect that the problem is the space in the name of the drive. I tried to change it but with no success. the owner user of the drive is me (my user name), the group is root with no permissions.

I read somewhere that I can plug the drive into a computer with windows installed on it and change the name there and then ubuntu will read the new name with no problem.

Is that a permission problem? if so, how do I change the permissions? 
If not and it a name problem, how do I change the name?
Will the windows rename be effective?

---

