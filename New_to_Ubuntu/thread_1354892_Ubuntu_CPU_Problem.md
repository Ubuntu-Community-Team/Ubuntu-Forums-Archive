---
title: "Ubuntu CPU Problem"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by king_009 on 2009-12-14
Hey Guys.. i m a newbie in ubuntu..
n just installed ubuntu 9.04 on virtualbox and have Windows 7 as host.
i m getting a strange problem...
Ubuntu is working tooooo slow...
i mean like it is full of loads...it may be common in ubuntu as it is different from windows n i m not familiar with ubuntu environment. but this is not the strange thing.
i opened System Monitor in Ubuntu n found CPU working as 97%
but my windows 7 was showing CPU at only 71%
i have provided 512 MB of RAM to ubuntu but still it works too slow.. is it normal in ubuntu or i m getting any problem??
need your help dear techies!!!
Thanks in Advance..
Akshit

---

### Post by snowpine on 2009-12-14
Hi Akshit, it is normal for an operating system to be slower as a Virtualbox guest (as your computer is running two operating systems at the same time). You should install Ubuntu to your hard drive if you want the best performance.

---

### Post by muteXe on 2009-12-14
That doesnt sound normal to be honest. I have 9.10 running in VB (admittedly with 8.04 as the host), with 512Mb given to it as RAM and mine runs pretty fast.
How much RAM to you have in your windows?

---

### Post by ukripper on 2009-12-14
Can yor run ```
top
``` command in terminal and tell us what is taking the cpu most. Sometimes internal database is updated for locate search. you must have looked at cpu percent then.

---

### Post by spydeyrch on 2009-12-14
Another question should be, what are your hardware specs? Type of CPU, total amount of RAM, etc. Also, what seetings did you apply/not apply in your VM (virtual machine - your guest os - ubuntu) setting in VB (Virtual box). If you have a multi-core cpu, try to dedicate one of the cores to just teh VM. You can do that through the settings for your VM. The VM has to be shutdown, not just in a saved state. Also, if your CPU supports hardware virtualization, make sure that it marked in your settings.
 
Let us know if it works and what your specs are. I have several VMs on my machine, both ubuntu as host and win7 as host (dual boot system). I know that it works and that it shouldn't be that big of a system resource hog. Also make sure you have installed the VBox Guest Additions. That helps to some degree.
 
-Spydey

---

### Post by king_009 on 2009-12-15
My Hardware Specs are
Processor: Pentium4 3.0 GHz
RAM:2 GB DDR2
and i had applied 512 MB RAM to Ubuntu.
I work on Windows XP also but through virtual PC and it runs smoothly n fast!
may be thats a problem of my VIrtualBox.
I was facing problem in using Ubuntu through Virtual PC so just used it through VirtualBox.

---

### Post by 3rdalbum on 2009-12-15
1. Have you installed the Guest Additions within Ubuntu? It accelerates video rendering when you're using Virtualbox.

2. You say you have high CPU use in Ubuntu; well what program is using the high amounts of CPU? The system monitor can tell you. Kill whatever is causing the high CPU use and you'll kill the problem.

---

### Post by spydeyrch on 2009-12-15
Aright, so let me see if i understand your system setup(s). You have Win7 as host, and run XP as the guest in virtual pc, right? Is it "XP Mode" that you are running or is it just a copy of xp that you run in virtual pc (there is a difference)? What version of win7 and also is it a 32 bit or 64 bit version? You tried to run ubuntu through virtual pc and didn't get acceptable results, comparable to your experience with xp in virtual pc, therefore you switched to virtual box (VB) to see if ubuntu would run better, right?
 
You have two gigs of ram and have allocated 512megs to the guest os. P4s *CAN* use virtual box but, they don't support hardware virtualization and that is a ***BIG HELP***. (I am not "yelling" by using the capitalized letters, just placing emphasis on the words. Some peopel get offened by "yelling" in the forum :)) Due to not supporting hardware virtualization, it is software virtualized. Virtual box does a good job of software virtualization, but you need to optimize your vm (virutal machine) as much as possible. Also, you really do need to install the guest additions, this will help drastically!!
 
So I suspect that your machine is bogging down due to a couple issues:

[LIST]
[*]P4 not supporting hardware virtualization, therefore it is taxed more because of extensive software virtualization techniques
[*]optimization of your vm (needs to be done)
[*]guest additions not installed
[/LIST]Also, make sure that you follow ukripper's advice and run this command in terminal while in the vm:
 
Code:
top 
Take a look at what is using the msot cpu cycles and see if you really need it or if you can shut it down.
 
If you would like some help optimizting your VM, just ask. :D
 
-Spydey

---

### Post by king_009 on 2009-12-15
Thanks Spydey for help...
i have installed guest additions in virtualbox n while i used the top command, i found Xorg is taking the highest %of CPU. so should i really kill Xorg?

one more thing... i had given even 700MB to ubuntu but speed is still the same!!!!
n i m using Win7 32bit edition.
my processor is of 64bit.

n one more qstn please....
i feel much better using virtual machines through virtual pc. but the main problem was i was unable to install Virtual Machines Additions through Virtual PC.. So i opted for VirtualBox. Tell me guys.. what to do????

i know i m in a foolish trouble... but guys.. plz get me out of it...

---

### Post by spydeyrch on 2009-12-15
King_009, do you have any crucial files in your ubuntu system, i.e. music, documents, photos, work projects, etc.? What version of ubuntu are you trying to run? 9.04 or 9.10?
 
Are you using ubuntu for liesure or for business? To be honest, I personally don't like virtual pc, not as customizable as I would like it to be. Also, what are your gpu specs (graphics card)?
 
With a little patience, we will get you there.  :D
 
-Spydey

---

### Post by king_009 on 2009-12-15
hey guys!!!!
we all know that to solve the problem when we are struck somewhere, we have two ways...
1. Bang your heads to get the solution
2. Go back n start again...
I banged my head n found nothing. so just deleted my earlier virtual disk and machine..
and made a new and fresh install... n guys... suess what.... it really helped me out!!!
yes guys!!! my ubuntu started working faster now!!

@Spydey: no dude it hardly contained any of my projects but i was to make a project in it.. anyways.. its working fine now. now its too late here... 1:45 AM so i m going for a sleep.. tomorrow i'll see all those build-essentials, guest additions and all formalities... ;)

hey can u plz answer my last qstn dude??? i m a student of software engineering... so should i really use this ubuntu stuff?? i tried c++ in ubuntu n found it intresting... so should i use ubuntu for my development of projects or not? i hope u got my point... i m just asking for my practice purpose.. not for commercially.... :D it may be an off-topic qstn but... please!!! 

thanks 4 all your help dear members!!!
love u all
Yours Forever
Akshit

---

### Post by ibuclaw on 2009-12-15
> **king_009 said:**
> yes guys!!! my ubuntu started working faster now!!

Being run in a VM is not the swiftest of things to do for any OS. So I don't see why speed would matter so much anyway.

> **king_009 said:**
> 
hey can u plz answer my last qstn dude??? i m a student of software engineering... so should i really use this ubuntu stuff?? i tried c++ in ubuntu n found it intresting... so should i use ubuntu for my development of projects or not? i hope u got my point... i m just asking for my practice purpose.. not for commercially.... :D it may be an off-topic qstn but... please!!! 

It has been said that Linux is the Developers platform - and I don't doubt that a bit when I have C, C++, D, Perl, Sed/Awk, Bourne Shell and Haskell under my belt.

In Windows Development I used VB6 and Pascal whilst at college. That relationship didn't last long, and I quickly forgot how to program in both languages. (dim foo as Integer; -- Tell me if I'm right, because I honestly can't remember ;))

Regards
Iain

---

### Post by spydeyrch on 2009-12-15
Great news dude!! i ran home during my lunch break and wrote down the steps to create a new ubuntu vm. I didn't have a copy of vb here to work with and wanted to make sure tha tI got it write. i was going to tell you to delete your old vm and start over. i was going to give you the steps needed to get it all setup properly but it looks like everything is going well for you so far. AWESOME!!!
 
Make sure that the following settings are set in your ubuntu vm.
 
don't start the vm. select it with a single click and then select settings above where the vms are shown.
 
under system -> motherboard -> you should have a few options: boot order, memory allocation, & features. Make sure that you have allocated enough memory to your vm, I usually would do just under half of your total system memory. VB usually tells you if you have allocated more than half, pretty sweet. :)
 
Choose the boot order that you want.
 
for the features, make sure that at least ACPI is enabled. You can enable IO APIC if you want but it might slow down your vm.
 
under system -> proccesor -> if you can enable PAE/NX, do it.
 
under system -> Acceleration -> you will probably not be able to check/uncheck the vt-x/AMD-V because your CPU might not support hardware virtualization. If ou can select Nested Page, do it, but most likely you won't be able to because I believe that your cpu doensn't support it.
 
under display -> video -> you should see a setting to increase/decrease your video memory and also select/de-select 3d acceleration. If you are going to be using compiz fusion on your ubuntu vm, then you will want to enable the 3d acceleration and also give your vm sufficient video ram. the effectiveness of this will be determined on how much video ram your video card has and also your system membory allocated to your vm. you decide. if i were you, i wouldn't do it just yet, you can always change it later.
 
under CD/DVD -> make sure you have "mount cd/dvd drive" bubbled (it is a little radio button). Also, select your appropriate cd/dvd drive that you want to use for the vm. Make sure that you mark enable passthrough. if you have an iso that you want to use instead of a physical disk, this is where you would select that too.
 
Under usb -> make sure that both boxes are marked
 
under shared folders -> we can get this set up later if needs be. :)
 
I would do all that BEFORE installing the vm os, just to make sure that it all works together well.
 
--------
 
As far as your other question(s):
 
Well, for programming, I really don't have too much experience in it. sorry. I would love to give you my opinions/theories/hypotheys, but I am afraid it wouldn't do you any good. Sorry man. What I would suggest is to open a new thread with just that discussion subject as the topic and see if you can get people to help. Hope everything goes well. Enjoy your new system and if you have any questions, post them in the forum so we can all pitch in and help. And you are always welcome to PM me if you would like. Take care! :o
 
-Spydey

---

