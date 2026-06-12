---
title: "What to do with the I-touch and I-tunes library?"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by dan1973 on 2009-04-18
At the moment I am running a dual boot system while I get my bearings in Ubuntu.

My question relates to the managament of my music. At present i have a large I-tunes library and an i-touch. 

What is the most painless way of moving the device and library into ubuntu?

PS, my linux knowledge is minimal.

---

### Post by juancarlospaco on 2009-04-18
Floola, Banshee, Amarok, GTKPod

---

### Post by clive littlewood on 2009-04-18
Hi

Unfortunatly the ipod touch and iphone are not supported in Linux and I have to dual boot with XP just to sync my ipod.

I believe that many of the players in Ubuntu are actively trying to find a solution (mainly Amarok) but no joy as yet.  :(

It is posible to SSH to your Ubuntu machine but this requires "jailbreaking" your ipod touch.

This of course is typical of Apple and other major OS's

Clive

---

### Post by dan1973 on 2009-04-19
I guess i'll just have to stick with my dual-boot for the time being.

Since I am running out of space on this laptop, mainly due to large music and photo stores, is it possible to purchase an external storage device, export both of these libraries, and have them accessible by both both Ubuntu based software and windows based?

If so, how is this likely to work - ie what formats are needed, and what are the potential difficulties for a novice?

---

### Post by Garrovick on 2009-04-19
iPods and iTunes are strictly Windows/OSX only.  Not for Ubuntu.

---

### Post by ShinHadoken on 2009-04-19
Well, like Clive said, you'd have to jailbreak to get the job done, but if you're willing to do that, here's how to do it.

First of all, jailbreak your iPod. There are many easy-to-follow guides out there on how to do it. If you have an iPod Touch 2G (like me) download the program QuickFreedom. If you are even REMOTELY computer literate (which you obviously are) then this program will show you how to jailbreak your iPod.

Next, install OpenSSH and Terminal via Cydia (I don't like installer, runs to choppy and has a very small and unreliable selection of apps, Cydia is heavily based upon Linux Aptitude tools, and works very well)

Now, to move your library over, you need to ensure that everything in your library is an MP3 (you may get .m4a's from iTunes to work, never tried myself) but definitely anything that is copy-protected from the iTunes store must be burnt to a disc and re-imported. Then you should be able to move everything over to your Ubuntu partition.

The rest depends on your firmware version and preferred approach. (eg, do you want wireless syncing, or to use a cable?) The rest is explained pretty well at this [Ubuntu Help page]("https://help.ubuntu.com/community/PortableDevices/iPhone"). I personally can tell you that I have firmware 2.2.1, and I sync wirelessly out of convinience. 

Hope this helps!

---

### Post by clive littlewood on 2009-04-19
Hi

As for your external drive it should be formatted as Ntfs as Ubuntu as well as Windoze can read this.

Windoze cannot read any of the Linux formats without extra software.

Clive

---

### Post by dan1973 on 2009-04-19
I think what i'll do is export the photos out to a new external hard disk - no problems of access in ubuntu. 

This should clear up plenty of space for itunes library expansion on the windows partition side. By the time the music fills up the partition, who knows, the problem may be cracked!

Thanks for the suggestions.

---

### Post by dan1973 on 2009-04-19
As far as 'windoze' (i like it:P) having access to the photos once on the new hard disk - am I bothered? I think not - plenty of good photo management software out there for linux.

---

### Post by dan1973 on 2009-04-19
By the way - Clive, where is the sun,sun,sun? I only ask because here in Finland it's snow,snow,snow!

---

