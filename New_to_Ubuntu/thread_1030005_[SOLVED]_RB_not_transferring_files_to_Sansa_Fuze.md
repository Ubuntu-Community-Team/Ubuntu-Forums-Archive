---
title: "[SOLVED] RB not transferring files to Sansa Fuze"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by jalehtor on 2009-01-04
I just bought a 4gb Sansa Fuze, my first mp3 ever. No extra memory installed. I charged it for three hours--it shows up on the screen when you plug it in. I switched the system setting to msc. I installed the restricted stuff the Ubuntu help site told me to install. I installed Amarok. I have RB installed. 

Since this is my first player, I don't have a library to save.
I downloaded a single mp3 as trial onto my music folder, and tried it out. It plays--Totem comes on, very pretty etc. RB will allow me to download it, but I don't know how to download from RB to Sansa folder. Amarok says the file could not be played. 

I'm really confused. Part of the problem is that not only am I an Ubuntu noob, I'm an mp3 noob as well...terrible combination. Help?

---

### Post by adult swim on 2009-01-04
is RB rhythmbox?  if so if you have your music in your library, you can highlight it all with ctrl+a and drag it to your sansa fuze in the box on the left side of rhythmbox.

---

### Post by jalehtor on 2009-01-04
> **adult swim said:**
> is RB rhythmbox?  if so if you have your music in your library, you can highlight it all with ctrl+a and drag it to your sansa fuze in the box on the left side of rhythmbox.

Yes, I meant Rhythmbox by RB sorry! The problem is that there's no "sansa fuze" on the left side of rhythmbox. I dragged it to the folder I get when I click on the Fuze on desktop, and there it is. But it won't transfer to the player.

Btw, when I plug in the Sansa, the folder that appears on the desktop is not called Sansa, but 4.1 GB Media. When I open it, I get a "disk-file browser" screen with 4.1 GB media on the left, with folders for music, podcasts etc. 

I found the manual for Sansa online, but there're no instructions for Linux :confused: Under normal circumstances, how does the music transfer from the folder to the player? When my player is plugged in, the only screen I can access is the one showing the thing's being charged.

The instructions which came with the player are for windows, and with windows, I'd click "my computer," double click on the sansa player, and then click on "internal memory." Then I'm supposed to drag and drop files to the music folder. 

I can't find anything resembling internal memory here.

I did click on a number of other symbols--MTable.sys, Res_Info.sys, Sys_Conf.sys, and when I do that, I get a "There is no application installed for this file type."

---

### Post by adult swim on 2009-01-04
whenever you double click the desktop icon, can you drag some mp3s into the music folder that you see?  try ejecting the device after that and see if the music is on it.

---

### Post by jalehtor on 2009-01-04
> **adult swim said:**
> whenever you double click the desktop icon, can you drag some mp3s into the music folder that you see?  try ejecting the device after that and see if the music is on it.

Yes, I can drag the mp3 from rhythmbox to the music folder. The music's not on the device after it's been unplugged. The windows instructions say to click on internal memory for the device; is there something like that here that I'm missing?

---

### Post by adult swim on 2009-01-04
you might want to check out this thread, [http://ubuntuforums.org/archive/index.php/t-910063.html](http://ubuntuforums.org/archive/index.php/t-910063.html) , a few guys got it working with rhythmbox.  unfortunately i dont have one here to fiddle with.

---

### Post by jalehtor on 2009-01-04
> **adult swim said:**
> you might want to check out this thread, [http://ubuntuforums.org/archive/index.php/t-910063.html](http://ubuntuforums.org/archive/index.php/t-910063.html) , a few guys got it working with rhythmbox.  unfortunately i dont have one here to fiddle with.

Thank you! Is there something better out there than rhythmbox for mp3s?

---

### Post by ArgentSilver on 2009-01-06
> **jalehtor said:**
> Thank you! Is there something better out there than rhythmbox for mp3s?

If you are wanting to use the Fuze in MSC mode, you would be better off to just use the Nautilus file manager to locate the Fuze's mount point (probably /media/SANSA FUZE/) and then drag and drop mp3s from your music directory (maybe something like /home/your_username/music?) to the Fuze's music folder, which should be /media/SANSA FUZE/MUSIC.

In MSC mode, the Fuze is just like a USB stick, so you don't need a 'music player' application to manage moving mp3s to it. If you really want to use Rhythmbox for this, you probably would be better off changing to MTP mode on the Fuze, then make sure the 'Portable Players - MTP' plugin is enabled in Rhythmbox under Edit-> Plugins. You have to stick to one mode or the other though; files you transfer in one mode won't be visible under the other.

Personally, I find MSC to be the most simple way to go!

---

### Post by jalehtor on 2009-01-08
> **ArgentSilver said:**
> If you are wanting to use the Fuze in MSC mode, you would be better off to just use the Nautilus file manager to locate the Fuze's mount point (probably /media/SANSA FUZE/) and then drag and drop mp3s from your music directory (maybe something like /home/your_username/music?) to the Fuze's music folder, which should be /media/SANSA FUZE/MUSIC.

In MSC mode, the Fuze is just like a USB stick, so you don't need a 'music player' application to manage moving mp3s to it. If you really want to use Rhythmbox for this, you probably would be better off changing to MTP mode on the Fuze, then make sure the 'Portable Players - MTP' plugin is enabled in Rhythmbox under Edit-> Plugins. You have to stick to one mode or the other though; files you transfer in one mode won't be visible under the other.

Personally, I find MSC to be the most simple way to go!

Thank you so very much for your help. I was on a Sansa Fuze site, and a nice poster there figured it out. I can at least upload my Cds onto the Fuze now. 

Anyhow, I posted his solution here: [http://ubuntuforums.org/showthread.php?t=1030479&page=3&highlight=sansa--post](http://ubuntuforums.org/showthread.php?t=1030479&page=3&highlight=sansa--post) #25. Hope that helps someone else who's having the same problem...marking this thread as solved :D

---

### Post by hazza96 on 2009-01-16
Just to let people know, the version 2 of the Fuze has a different ID when you do a lsusb.

To get Rhythmbox to recognise the v2 Fuze as a "music device" you need to edit */usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi*

Add the ID 0x74c3 to the line for the Fuze. Connect your v2 Fuze, it will mount and it's icon on the Desktop will be look like a music device.

Open Rhythmbox and you will see your Fuze as a device on the left hand side.

---

