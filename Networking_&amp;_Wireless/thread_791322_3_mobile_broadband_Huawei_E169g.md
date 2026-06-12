---
title: "3 mobile broadband Huawei E169g"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by seansims on 2008-05-12
Hoping somebody can help me here, i have a dell laptop running Ubuntu 8.04, and i am trying to get 3 mobile broadband running on it. i am relatively new to Linux so you will need to keep it simple! my problems are that i have followed various threads to try and get it running, currently i have vodafone mobile connect card driver for linux 2.0.beta2 installed, it sees a signal but i am unable to connect, settings i have are :-
Authentication mode = CHAP
APN host = 3internet

Thanks in advance!

Sean

---

### Post by Sub101 on 2008-05-12
These threads all give a lot of advice about mobile broadband. Hope they help

[http://ubuntuforums.org/showthread.php?t=609534](http://ubuntuforums.org/showthread.php?t=609534)
[http://ubuntuforums.org/showthread.php?t=639330](http://ubuntuforums.org/showthread.php?t=639330)
[http://ubuntuforums.org/showthread.php?t=656431](http://ubuntuforums.org/showthread.php?t=656431)
[http://ubuntuforums.org/showthread.php?t=639362](http://ubuntuforums.org/showthread.php?t=639362)

---

### Post by mikeocaiside on 2008-06-13
Hi Seansims
Maybe I am a little late with the reply but I have this setup working on my laptop.

Here is my setup on a i386 machine:

Download Vodafone mobile driver for linux version 1.99.17 (DO NOT USE BETA 3 AS IT CAUSES A FATAL ERORR) from [http://www.betavine.net]("http://www.betavine.net")
Install driver with it own package installer (just double click)
it will ask you a couple of questions just accept defaults.
It will also ask you for depencies, you just need a working internet connection to download these and install them. The package will tellyou what you need.
When you have these installed just plug in your USB modem (Mine was a E169G) 
It should connect straight away but when you try to get to a web site it will give you a message that APN is not correct.
Just open tools- edit profile and tick STATIC DNS AND ADD THESE TWO SERVER ADDRESSES 172.31.140.69 AND 172.30.140.69 Thats it.

Hope this helps
Mike

---

### Post by lkuttner on 2008-06-17
Hi Mike,

Please help - I have much the same configuration all round but as a brand new linux user I am a bit stumped on some of your steps.

I surfed for ages trying to figure out how to download something from betavine but eventually downloaded the tar and when I got nowhere, the deb file for that driver [vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb]. I double-clicked the deb file and the Package Installer did its thing but bombed out on *Failed to fetch [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) etc etc*. Obviously because I don't have an internet connection yet. (I had downloaded the deb from another Windows machine).

Have I downloaded the wrong file for the driver? Should I be somehow downloading the missing dependancies from the Windows machine onto a USB stick and getting them across to the Linux machine? If so, how do you get the installer to know where to look?

Thanks in anticipation of assistance.

Lance

---

### Post by mikeocaiside on 2008-06-18
Hi Lance 

Sorry not on line to the forums for a little while I have all the depenencies and the driver in a zip I will send to your email. When you install the deb file it should tellyou what you need but it is a little bit labourious as it tells you one file at a time then you have to go back and load that one just for it to tell you about another one. I am new to linux as well and I do not know if i can upload to here.
Good luck Hope it helps

Mike

---

### Post by lkuttner on 2008-06-20
Well, I have finally got it working - took me ages! I have discovered how important an internet connection is to Ubuntu. Fortunately I had a mate nearby with a router into which I could plug an ethernet cable and that was pretty seamless.

So let me fill in the gaps...

When Mike mentioned tools > edit profile, he was talking about from within Applications > Internet > Vodafone Mobile Connect Card driver for linux. It is now very obvious from hindsight!

I did not have mine just working like that, so back to seansims at the beginning and to Mike's helpful numbers, I have the following config (see attached png file):


A further problem I had was with the driver not saving changes to the profile, so with every change, I had to create a new profile from scratch and then delete the old.

Thanks very much to Mike especially - does anyone know of a application to send someone a virtual beer?

Lance

---

### Post by shr2004 on 2008-08-04
Hi guys
I have E169G model from 3 Uk network. I am trying to use it with Hardy. I have installed the vodafone driver 1.99.17. But I can't make it work. Here is my situation:
1. when I insert the dongle and start the driver program it shows bar at the bottom, that means the dongle is working.
2. I have created a profile as shown in the pics by lkuttner. My question is as I am using 3 network, what would be the user name and password, will it be same as shown in pics, which is vodafone?
3. If I leave user name and pass field empty, the driver cant connect. If I enter vodafone for both fields, it connects, but cant open any webpage, also the network icon in panel shows I am not connected. I tick static DNS and entered the numbered mentioned. Forgot to mention that usb dongle light is blue when connected.

I have tried with windows in the same place where I am trying in ubuntu and it works.

I am novice in Linux and have not tried any other method. The ways shown here seem very handy for people like me. Can anyone tell me what can I do now to make it work? Another point, do I need to unmount the CD that appears on Desktop when the usb is connected before using the driver?

---

### Post by Sealbhach on 2008-08-04
Here's a very good how-to.

[http://ubuntuforums.org/showthread.php?t=843973&highlight=e220](http://ubuntuforums.org/showthread.php?t=843973&highlight=e220)

I got my Huawei E220 working using Gnome-PPP, I didn't need the Vodafone driver at all.


.

---

### Post by shr2004 on 2008-08-04
> **Sealbhach said:**
> Here's a very good how-to.

[http://ubuntuforums.org/showthread.php?t=843973&highlight=e220](http://ubuntuforums.org/showthread.php?t=843973&highlight=e220)

I got my Huawei E220 working using Gnome-PPP, I didn't need the Vodafone driver at all.


.

Thanks for the link. Finally I managed to make it work. There was proxy setting problem. I set to no proxy and can connect easily.

---

### Post by yadhav on 2008-10-31
Hi, following all these steps and many more, I had been able to connect my Huawei e169G Modem in Ubuntu. I made a blog where all the steps from A to Z have been mentioned. I'm 100 % sure that if you follow it properly, yours will be connected to. Here it is:
[http://crazyaboutubuntu.wordpress.com/huawei-e169g-hsdpa-usb-stick-on-ubuntu/](http://crazyaboutubuntu.wordpress.com/huawei-e169g-hsdpa-usb-stick-on-ubuntu/)

---

