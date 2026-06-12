---
title: "How to recover data in /home that's encrypted by 9.10 distribution?"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by Darth.Ming on 2010-01-09
Hi, I'm new here and this is my first thread. I'm a Chinse speaker and don't speak English well. There might be some problems understanding my description. I came here because no effective solution was found in the Chinese forum.
 
I chose the option of "encrypting the home category" when installing 9.10 using the UNR Flash drive. 
 
Things got wrong when one day I switched on my computer, waited until the step of login, and two message box appeared saying that it cannot read two files in /home. When I continued to the desktop, another one appeared saying that Nautilus cannot run. and after that, the only thing I could see is the background. 
 
Having rebooted the computer, I chose recovery in GRUB, disappointed that I was facing the command line which I cannot handle. The only command I know is cd, and I found two files under my home category, one is access-your-private-data.desktop, and the other is README.TXT.
 
Knowing nothing to do, I chose to reinstall the system because I must use my computer then. At that time the only image I have is 9.04, so I can only use this. And, when it came to the step of partitioning, I chose to format sda1 and mount as /, to mount sda5 as /home without formatting it, and to use sda6 as swap space, just like it was before the installation. Maybe I should describe my partitioning before the accident: sda1, /, 10GB, ext4; sda5, /home, 50GB, ext4; sda6, swap, 2GB; the rest of about 70GB was not used. 
 
When the installation was about to complete, a message box appeared saying that a package, "encrypt" or something like this, was damaged. I didn't know what that meant so I went on. I found that I couldn't use it! Everything was almost the same! Though no message box appeared, I can only see a black screen with a pointer on it. 
 
So I reinstalled again, this time creating a partition of 20GB as /home in the idle space in the end of the disk. OK, this time I can run the system, but when I was trying to mount sda5 and access the data, I found the two files are broken. Message boxes appeared saying that the path it leads to doesn't exist. 
 
I don't know what to do. How to recover my data? Thanks in advance!

---

### Post by bodhi.zazen on 2010-01-10
This blog details how to mount your encrupted partition with a live CD:

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

Once it is mounted you can copy the data you need and use it with your new install =)

---

