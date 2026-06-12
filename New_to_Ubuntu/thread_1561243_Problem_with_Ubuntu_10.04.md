---
title: "Problem with Ubuntu 10.04"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by skayplakes on 2010-08-26
Hey guys,

I just started using Ubuntu about 3 weeks ago. I'm still fairly new with Linux as I am a longtime Windows user. So anyway , I decided to try it first by installing it with Wubi as I'm still afraid of partitioning my hard drive lol. Everything boots fine until there's a blinking cursor for about 10 seconds and it displays and error: nforce2_smbus: Error probing SMB2 but that's still not my major problem lol. So basically the installation was fine after that error. But now the problem is that a few minutes doing stuff in Ubuntu 10.04, my desktop suddenly shutdowns. I searched Google for the answer but almost all of it suggested that it was a power supply problem. I know it's not a power supply problem as when I'm booting with my original OS (Windows Vista), it doesn't shutdown. Any ideas what's causing this? 

Oh here are the specs of my desktop which is a Acer Aspire M3710:

Processor: Pentium(R) Dual-Core Cpu E5200 2.50GHz
Ram: 2 gb
Os: Windows Vista 
Video Card: Nvidia GeForce 9200

---

### Post by mastablasta on 2010-08-26
It could be the way you installed it. With Wubi you sort of running Ubuntu within windows.
 
Have you tried booting it in Live session? boot from CD? Does it work there?
 
Partitioning is easy and can be done for you. all you need to do is prepare your computer for it.
1. back up data
2. defragment the drive (well actually computer does this for you)
3. star with instalation and during instalation you will be asked how much space you want to give to Ubuntu. then you just move the slider until you are satisfied with the amount of disk space. then continue the instal until finish. all partitioning is done for you automaticly (but you can always choose manual).
 
Read more here in the manual:
[[COLOR=#444444]http://ubuntu-manual.org/[/COLOR]]("http://ubuntu-manual.org/")

Or this book for a bit older vesion but still valid i believe:
[[COLOR=#444444]http://www.ubuntupocketguide.com/index_main.html[/COLOR]]("http://www.ubuntupocketguide.com/index_main.html")

---

### Post by Col.Krumpet on 2010-08-26
I've heard of this happening before and from what I've seen its usually problem with Wubi, which runs within Windows and for some reason it can cause an error. I would try booting from the Live CD and see if it runs alright, it'll be much slower but that will give you a good idea if its Wubi causing the problem.
If you have an external USB HDD you can also try loading Ubuntu on there and see if that works which would really be an even more reliable way to tell if its Wubi or not.
This is not to say that there may not be something wrong with your install disk but I would say its more than likely a Windows/Wubi problem.
Also as mentioned before the partitioning process is really painless and super easy, just follow the instructions while running the install CD and you'll be all set with a Windows/Ubuntu box in no time. It really is way easier than you think, just either choose automatic partitioning or manually set the partition size and Ubuntu does the rest.
Hope you get it solved and get back to smooth Linux sailing :D

---

### Post by skayplakes on 2010-08-26
> **mastablasta said:**
> It could be the way you installed it. With Wubi you sort of running Ubuntu within windows.
 
Have you tried booting it in Live session? boot from CD? Does it work there?
 
Partitioning is easy and can be done for you. all you need to do is prepare your computer for it.
1. back up data
2. defragment the drive (well actually computer does this for you)
3. star with instalation and during instalation you will be asked how much space you want to give to Ubuntu. then you just move the slider until you are satisfied with the amount of disk space. then continue the instal until finish. all partitioning is done for you automaticly (but you can always choose manual).
 
Read more here in the manual:
[[COLOR=#444444]http://ubuntu-manual.org/[/COLOR]]("http://ubuntu-manual.org/")

Or this book for a bit older vesion but still valid i believe:
[[COLOR=#444444]http://www.ubuntupocketguide.com/index_main.html[/COLOR]]("http://www.ubuntupocketguide.com/index_main.html")

My apologies as I didn't say it correctly. It's not that I'm scared to partition my hard drive. I just heard that in order to uninstall Ubuntu (not gonna happen anytime soon), I need a Windows Vista Recovery Disc and I don't have one of those. Thanks btw :)

> **Col.Krumpet said:**
> I've heard of this happening before and from what I've seen its usually problem with Wubi, which runs within Windows and for some reason it can cause an error. I would try booting from the Live CD and see if it runs alright, it'll be much slower but that will give you a good idea if its Wubi causing the problem.
If you have an external USB HDD you can also try loading Ubuntu on there and see if that works which would really be an even more reliable way to tell if its Wubi or not.
This is not to say that there may not be something wrong with your install disk but I would say its more than likely a Windows/Wubi problem.
Also as mentioned before the partitioning process is really painless and super easy, just follow the instructions while running the install CD and you'll be all set with a Windows/Ubuntu box in no time. It really is way easier than you think, just either choose automatic partitioning or manually set the partition size and Ubuntu does the rest.
Hope you get it solved and get back to smooth Linux sailing :D

I can try booting from a Live CD but I recently run out of CD's so I can't burn Ubuntu just yet. Will try to get some tomorrow :)

---

