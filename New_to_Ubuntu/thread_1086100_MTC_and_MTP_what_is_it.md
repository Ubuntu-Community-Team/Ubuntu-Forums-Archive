---
title: "MTC and MTP what is it?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by cptrohn on 2009-03-03
Hi, we are having a problem, my girlfriend bought a Sansa Fuse and we are having trouble loading music and video files on it...

I came across an article while googling this and it talks about MTC and MTP protcal for loading music and videos...  Which one should I be using with Ubuntu?

Isn't MTP the same thing that Zune uses?  I thought that Sansa was good with Linux?  We dragged and dropped 2 files from the computers music file into the Sansa's music file, and while it shows up on the player as being there, when you try to play the file nothing at all happens?

Also when I tried to get it to synch with Amarok on the device list nothing happened....  What in the world are we doing wrong?

---

### Post by smacattack on 2009-03-03
Hello,

I have had a couple of MP3 players that I have used in Ubuntu so I hope I can help.

Both MP3 players (Creative Zen V and Samsung P2) use MTP protocol and I was able to interact with both with AmaroK and gnomad2.

It's not the prettiest program, but gnomad2 works really well without having to configure anything. [You should be able to just install it with sudo apt-get install gnomad2 ] Once you go into gnomad2 it should 'just work' assuming the MP3 player is plugged in. Gnomad2 will, in my experience, transfer any type of data you want to transfer (pictures and videos included). 

For AmaroK, you should be able to just go to Settings--> Configure AmaroK --> Media Devices (at the bottom left). Then pick MTP in the drop down menu, and make up a name for it(ie. Sansa). Then, from the main AmaroK screen, pick 'Devices' at the bottom left, pick the device profile you just created (ie. Sansa) from the drop down menu at the top left and then click 'Connect' (right above the drop-down menu with the lightning bolt). You should be able to click and drag media files from your main box at the right to the device box at the left then you can 'start transfer'.

Best of luck.

---

### Post by cptrohn on 2009-03-03
> **smacattack said:**
> Hello,

I have had a couple of MP3 players that I have used in Ubuntu so I hope I can help.

Both MP3 players (Creative Zen V and Samsung P2) use MTP protocol and I was able to interact with both with AmaroK and gnomad2.

It's not the prettiest program, but gnomad2 works really well without having to configure anything. [You should be able to just install it with sudo apt-get install gnomad2 ] Once you go into gnomad2 it should 'just work' assuming the MP3 player is plugged in. Gnomad2 will, in my experience, transfer any type of data you want to transfer (pictures and videos included). 

For AmaroK, you should be able to just go to Settings--> Configure AmaroK --> Media Devices (at the bottom left). Then pick MTP in the drop down menu, and make up a name for it(ie. Sansa). Then, from the main AmaroK screen, pick 'Devices' at the bottom left, pick the device profile you just created (ie. Sansa) from the drop down menu at the top left and then click 'Connect' (right above the drop-down menu with the lightning bolt). You should be able to click and drag media files from your main box at the right to the device box at the left then you can 'start transfer'.

Best of luck.


Ahh thank you...

I will give both of these a try tonight to see if I can get them going!

thanks much!

---

