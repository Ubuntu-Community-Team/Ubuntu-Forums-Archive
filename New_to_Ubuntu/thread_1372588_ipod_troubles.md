---
title: "ipod troubles"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by Falc7 on 2010-01-04
Hi
I've got a new ipod, and i am having some trouble getting it to work well with ubuntu. While looking around i found gtkpod, and heard it was the best program to do this with. But I couldn't get it to work correctly, so i reset the ipod to factory defaults using itunes, so i'd have a clean slate to start this from. Tried gtkpod again, i press load ipod. Nothing happened for a long while, but then it asks me to select the model, i do, and i get the message: ipod database import failed, illegal seek to offset 0 (length4) in the file: media/ipod/ipod_control/itunes/itunesDB

I heard Amarok works, but when i put the ipod in and start amarok, nothing happened for a long while, then it said, please select your model, i did, then it said ipod initialised. But nothing more, i am still unable to put songs on.

Ubuntu recognises it as an ipod, which is a good, but i just cant get the damn thing to work.  Its a 5th gen ipod nano if it helps.

---

### Post by Max_Mackie on 2010-01-04
This may be redundant, but try using Rhythmbox and let me know if you can do it or not.

---

### Post by Falc7 on 2010-01-04
Would the ipod normally appear on the left pane? There seems to be nothing to say rhhythem box knows its there unfortunately.

I've noticed that after logging out gtkpod now gives me this error problem creating ipod directory or file /media/ipod/ipod_control

---

### Post by Max_Mackie on 2010-01-04
I'm beginning to wonder if your system is even mounting the iPod.
What kind of iPod is it?
Can you see it in the "Computer" window or in media/ipod ?

---

### Post by Falc7 on 2010-01-04
It definately recognises the ipod, it says devices plugged in: IPOD, in the notification area (i'm using kubuntu atm). And i can browse to where the ipod is mounted at /media/IPOD. I will make a series of screenshots showing what happens in gtkpod in just a minute

---

### Post by Falc7 on 2010-01-04
1.
[www.ubuntu-pics.de/bild/36605/screenshot_002_x7FTjV.png](www.ubuntu-pics.de/bild/36605/screenshot_002_x7FTjV.png)

2.
[www.ubuntu-pics.de/bild/36606/screenshot_003_VS63Pv.png](www.ubuntu-pics.de/bild/36606/screenshot_003_VS63Pv.png)

3.
[www.ubuntu-pics.de/bild/36607/screenshot_004_5p24to.png](www.ubuntu-pics.de/bild/36607/screenshot_004_5p24to.png)

4.
[www.ubuntu-pics.de/bild/36608/screenshot_006_u3Q7On.png](www.ubuntu-pics.de/bild/36608/screenshot_006_u3Q7On.png)
The last pic shows that the system recognises the ipod

---

### Post by Max_Mackie on 2010-01-04
Hmmm this MIGHT be a permission thing. 
Try the same thing, but start up gtkpod form the terminal by typing:

sudo gtkpod

---

### Post by LuisGMarine on 2010-01-04
see the "Fix Ipod detection" in my signature and let me knwo if that works!

---

### Post by Max_Mackie on 2010-01-04
Just read something else. Supposedly, gtkpod is looking in the wrong directory. The ipod is actually mounted in /media/ADMINISTRAT_/

See if you can tell gtkpod to look in that folder instead of the default media/ipod by going to Edit -> Edit Repository/Ipod-Options and browse to the proper directory.

---

### Post by Falc7 on 2010-01-04
> **LuisGMarine said:**
> see the "Fix Ipod detection" in my signature and let me knwo if that works!

I'll try this out on my ubuntu side tomorrow (going to sleep now), as i am using kubuntu atm and so don't have nautilus. I'll also try songbird then as well, i believe that supports ipods


Regarding sudo gtkpod
When i run sudo, it dosen't even see the ipod, but when i don't run sudo, it does. So strange

> **Max_Mackie said:**
> Just read something else. Supposedly, gtkpod is looking in the wrong directory. The ipod is actually mounted in /media/ADMINISTRAT_/

See if you can tell gtkpod to look in that folder instead of the default media/ipod by going to Edit -> Edit Repository/Ipod-Options and browse to the proper directory.

Get this error:
[www.ubuntu-pics.de/bild/36611/screenshot_007_1Fpekt.png](www.ubuntu-pics.de/bild/36611/screenshot_007_1Fpekt.png)

---

### Post by LuisGMarine on 2010-01-04
> **Falc7 said:**
> I'll try this out on my ubuntu side tomorrow (going to sleep now), as i am using kubuntu atm and so don't have nautilus. I'll also try songbird then as well, i believe that supports ipods


Regarding sudo gtkpod
When i run sudo, it dosen't even see the ipod, but when i don't run sudo, it does. So strange

Leave songbird alone, its ipod support is beyond repair right now.  Try something else, like [Banshee]("http://banshee-project.org/")

---

### Post by Max_Mackie on 2010-01-04
I'm stumped man :S
Maybe Luis is right and Banshee will work for you.

---

### Post by k3lt01 on 2010-01-04
Banshee is the best option atm.

Songbird is very hit and miss lately. My Jaunty desktop with Songbird supports my iPod Classic but my Karmic laptop with Songbird doesn't. The only real difference between the two PCs is the version of Songbird installed.

---

### Post by Falc7 on 2010-01-04
> **LuisGMarine said:**
> Leave songbird alone, its ipod support is beyond repair right now.  Try something else, like [Banshee]("http://banshee-project.org/")

Ah this looks promising:
[www.ubuntu-pics.de/bild/36613/screenshot_010_2u0gFT.png](www.ubuntu-pics.de/bild/36613/screenshot_010_2u0gFT.png)

But i get an error message when i try to unmount it:
[www.ubuntu-pics.de/bild/36615/screenshot_011_14EZ1Q.png](www.ubuntu-pics.de/bild/36615/screenshot_011_14EZ1Q.png)

---

### Post by LuisGMarine on 2010-01-04
lmao! I just got that error too.  Well I knew that ejecting the ipod through banshee doesn't work, but I never was able to see the error until now.

Yes if you right click your iPod through banshee and try to eject it, it will spit out that error.  Best thing to do is close down banshee, and manually right click the ipod icon on your desktop and then hit eject.

---

### Post by Falc7 on 2010-01-05
Ok i'll remember that. One problem is that the ipod dosen't seem to recognise the music that banshee puts onto it. I put a standard mp3 file onto the ipod. Banshee says synchronising. Then i eject, however the ipod says it has no music, but when i reconnect the ipod to the computer, banshee can see the song i've put on there before

---

### Post by LuisGMarine on 2010-01-05
Make sure you close out banshee and click on Eject from the desktop.  Or try doing the same thing with safely remove.

I had this in the past where if I clicked "Safely Remove" my ipod would display 0 songs.  So I then went and tried with "Eject" and everything was back to normal.

---

### Post by onecrustybaker on 2010-01-06
great help thankyou

---

### Post by LuisGMarine on 2010-01-06
I was informed of another workaround, that replaces having to do the whole "kill nautilus" thing.

First open up gconf-editor by hitting Alt + F2 and typing in "gconf-editor". Then navigate to apps > nautilus > preferences, and un-checking the "media_automount" option.

Close out of gconf-editor and plug in your iPod. Then open up banshee. Once banshee is open, mount your iPod by going to your desktop and clicking on Places > "your_ipod_name" and banshee should now recognize it.

I'm not sure you have to follow the steps in the second part exactly, but you are free to experiment. This I'm gussing might only work with the default ubuntu (gnome) install.

---

### Post by Falc7 on 2010-01-10
> **LuisGMarine said:**
> Make sure you close out banshee and click on Eject from the desktop.  Or try doing the same thing with safely remove.

I had this in the past where if I clicked "Safely Remove" my ipod would display 0 songs.  So I then went and tried with "Eject" and everything was back to normal.

oops sorry missed your post, i'll try this out

---

