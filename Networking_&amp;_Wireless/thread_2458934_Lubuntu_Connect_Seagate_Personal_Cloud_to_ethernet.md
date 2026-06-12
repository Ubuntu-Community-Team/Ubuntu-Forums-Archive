---
title: "Lubuntu: Connect Seagate Personal Cloud to ethernet card on PC"
date: 2021-03-06
forum: Networking &amp; Wireless
---

### Post by hatebloat on 2021-03-06
Hi you all. I just installed Lubuntu 20.10 on my old Emachine desktop. I love the speed and simple user interface! Windows 10 just became a bloated nightmare (hence my username).

Lubuntu is handling *most* of my needs out of the box. But I need your all's help on this one task:

I own a Seagate 3TB Personal Cloud NAS Device. I use it primarily for movies, and stream them to my TV. Well it was giving me a blinking red led error, so I did a reset on it and formatted it's drive. It's working again.

With the my Personal Cloud connected to my wireless router, in Lubuntu I was able to access the web interface where I did the initial web based setup wizard. And I can access the NAS in Lubuntu's file manager, drag/drop and delete files :).

However, I have about 600 movies that I need to transfer to the NAS. It would take forever to do this through the wireless connection. I need a one time physical connection to my PC's network card (the cat 5 jack). I used to be able to do this in Windows with no configuration. But in Lubuntu, nothing is showing up when I connect the NAS to the ethernet card.

What would be the simplest way to accomplish this in Lubuntu? I know I'll have to run a few scripts probably, unless there is a GUI package I can install. I'll learn about scripting later but right now I just need to get my movies on the drive.

And then when it's all done I'll reconnect the NAS to my wireless router, where I occasionally add a movie to my library.

Thank you all,

Matt

---

### Post by hatebloat on 2021-03-07
I might have found something useful. There is an icon called Network on my desktop. It looks like a file browser window. In the top menu there is "Go". I Click on it to get a drop down menu and there is "Connect to Server" at the bottom". My Seagate Personal Cloud is essentially a server right? You have to choose a connection method:

SSH, FTP, WebDav, Secure Webdav, HTTP, HTTPS

You also have to choose a host path and port.

Do you think this might work?

---

### Post by hatebloat on 2021-03-07
I found an easy fix. I brought my desktop computer into the room where my router is, and plugged it in directly. I can assess my NAS and have quicker upload speeds than wireless. I'm only doing this once anyway just to get all my movies on the NAS.

---

