---
title: "I want to install Ubuntu, but keep Vista. I am having problems.."
date: 2009-01-06
forum: New to Ubuntu
---

### Post by hurst21uk on 2009-01-06
I am new to all this, so please be patient!

I have burned Ubuntu to a CD, and I am ready to install it.

My HDD is setup currently with a C:\ with 27gb free and a D:\ with 28gb free. The C:\ is where Vista is installed and the D:\ I currently just use for odds and ends. I originally thought it would be possible to install Ubuntu to the D:\ and have it boot from there, but I do not think that is possible after reading around. I come across this tutorial 

[http://forums.techarena.in/guides-tutorials/1028375.htm](http://forums.techarena.in/guides-tutorials/1028375.htm)

I am following the tutorial to partition my C:\ but when I click 'Shrink Volume', it says that the size of available shrink space is 0. I did it also on the D:\ just to test and it gave me around 30gb of shrink space.

So right now, I have no idea what to do. Is it in anyway possible to parition the D:\ and install it there? Also, why is my C:\ showing 0 available shrink space? It does mention something about Snapshots and Pagefiles, but this is all foreign to me!

If anyone can point me in the right direction, I will be extremely grateful!

Thanks,

Mark.

---

### Post by avtolle on 2009-01-06
To shrink the Vista install, you will need to use the Vista tool for that (on C). Sorry, I don't use Vista, so I've no idea where to find the tool. But first, before trying to shrink, defrag C; a couple of times.

You can install Ubuntu on D; you might want to search the forums for threads on how that is done. [http://psychocats.net/ubuntu/dualboot#partitioning](http://psychocats.net/ubuntu/dualboot#partitioning) may also be of assistance to you in this endeavor.

---

### Post by hurst21uk on 2009-01-06
> **avtolle said:**
> To shrink the Vista install, you will need to use the Vista tool for that (on C). Sorry, I don't use Vista, so I've no idea where to find the tool. But first, before trying to shrink, defrag C; a couple of times.

You can install Ubuntu on D; you might want to search the forums for threads on how that is done. [http://psychocats.net/ubuntu/dualboot#partitioning](http://psychocats.net/ubuntu/dualboot#partitioning) may also be of assistance to you in this endeavor.

Right, so installation is possible on the D:\, thats what I needed to hear.

I'll check the thread, thanks a lot!

---

### Post by Pessulus on 2009-01-06
You could also use "System Rescue CD" 
Home page: [http://www.sysresccd.org/Main_Page ]("http://www.sysresccd.org/Main_Page")

Great tool for partition

---

### Post by Nxion on 2009-01-06
This will make your life MUCH, MUCH easier. It is a awesome tool.

Wubi [http://wubi-installer.org/](http://wubi-installer.org/)

It installs in Vista just like an application. Asks a few questions(password harddrive size and what flavor of ubuntu) and that's it , it will start the install.The cool part is that there is no need to reformat or repartition. It just works.

The other nice part is that if you dont want it anymore, you can just remove it by going to "Programs and Featurs" and uninstalling the whole thing.

---

### Post by JoshuaRL on 2009-01-06
I have Vista that came installed on my new laptop, and had to shrink the partition through Vista.  [Here is a good explanation of how to do that.](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)  It's linked to from [the Community Wiki page here.](https://help.ubuntu.com/community/WindowsDualBoot)  It seems to work just fine, just make sure that you defrag first.  You know, just like any Windows involved dual boot.

---

### Post by dynathi on 2009-01-06
> **Nxion said:**
> This will make your life MUCH, MUCH easier. It is a awesome tool.

Wubi [http://wubi-installer.org/](http://wubi-installer.org/)

It installs in Vista just like an application. Asks a few questions(password harddrive size and what flavor of ubuntu) and that's it , it will start the install.The cool part is that there is no need to reformat or repartition. It just works.

The other nice part is that if you dont want it anymore, you can just remove it by going to "Programs and Featurs" and uninstalling the whole thing.

Seconded. If you have a somewhat "strange" partition setup (I.E., vista isn't on one partition occupying the entire disk), and you don't know **exactly** what you are doing, chances are you'll end up getting burned somehow. Wubi is the simplest option for installing, you have nothing to lose. I believe that it's even on the Intrepid installer disk now.

---

### Post by hurst21uk on 2009-01-06
Well, I installed Ubuntu!

It did have all the partioning options before I installed it, it handled it all.

And I am typing this from Vista, so I think so far so good. I just have to setup my wirelss networking thorugh Ubuntu now and that will be me sorted. 

If I have any problems, I will let you know..

---

### Post by hurst21uk on 2009-01-06
First problem!

Ubuntu does not seem to recognize my Wireless Network Adaptor.

Its an Atherons Wireless adaptor that came with my laptop when I bought it.

It just doesn't seem to show up in the wireless tab. Am I wrong in thinking that it should detect it automatically? I was also thinking that maybe my Wireless Network card is not turned on when ubuntu starts. Its permanently on in Vista.

Any ideas to the solution?

---

### Post by zvacet on 2009-01-06
@ **hurst21uk**

If you have problems it is good thing to start new thread.That way other people will know that you have some problem and when you solved it that will help others who have same problem because they can search and find your thread with solution how to fix.

---

