---
title: "Banshee ipod error: Cannot open /media/.hal-mtab"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by efx5452 on 2010-01-20
Hi!

Well- I need help please :)

I'm running ubuntu 9.10 32bit and Banshee 1.6 Beta 2 (1.5.1).
Now, I'm trying to sync my ipod and for some reason any library changes I make in banshee won't take.

I did the killall -9 nautilus command to connect my ipod and it worked: banshee recognized that an ipod was connected. 

When I tried to sync the ipod everything seemed fine too.  Banshee showed me progress bars where it seemed to be adding and converting songs for my ipod.  

However, after it was finished, I tried to eject the ipod, I got this error:
Could not eject Media Player: org.freedesktop.Hal.Device.Volume.UnknownFailure: Cannot open /media/.hal-mtab

I then tried ejecting it directly from my desktop, and that worked, but ipod shows no music.  I also noticed that the whole time it was "syncing" the display only said "connected" not "syncing."

I tried everything, even completely restoring my ipod before connecting it to banshee, but nothing I've tried works. Please help!  I need my music  :( 

Thank you!

---

### Post by LuisGMarine on 2010-01-25
Try the new fix in my signature to get Banshee to recognize your iPod in Karmic Koala.

As for the error you are getting it is a known bug, and I'm not sure what release it suppose to be fixed it.  One thing that you can do is after you are done transferring songs to your iPod.  Right click the iPod icon on your desktop and hit Eject.

Try that and see if it works.

---

