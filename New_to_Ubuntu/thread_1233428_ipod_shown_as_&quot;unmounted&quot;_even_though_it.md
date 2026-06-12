---
title: "ipod shown as &quot;unmounted&quot; even though it's mounted"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-08-06
hi all,

i've been connecting my ipod without any problems at all for the past 2 weeks. now, when i plug it in, a message in cairo-dock says "ipod is now unmounted". 

this is contradicting though, because the ipod folder appears under /media/IPOD

i can access all my songs through this folder. everything in my ipod is listed in here. 

however, i cannot access the ipod in the "places" menu. It's simply listed as a "USB Drive" and when i click on it, it says "unable to mount location"

this means i cannot put any music on my 'pod since it doesnt show up in rhythmbox :(

can someone please help me? i've been trying for an hour now to simply put REM's Greatest Hits album on my ipod. didn't think it could ever take this long to do such a simple thing. 

thanks

---

### Post by fennec_fox on 2009-08-06
I'm not really that familiar with ipods but, I have this problem with some other devices occasionally. It works for me if I take it to windows or mac, let it mount, then safely remove it. You might want to try it. I have the same problem with my mp3 player (not ipod). 

Do Ipods have a function to change mount options such as like mount as "mass storage device" or anything? 

Mine does and when I changed it to mass storage device instead of mp3 player I stopped having this problem.

---

### Post by LowSky on 2009-08-06
have your tried resetting your ipod.. don't wry it doesn't remove any songs just rests the ipod OS

simple switch the hold key on then off, then hold menu and select (middle of the circle button) at the same time for about 5 seconds, you will see the screen reset and show a white apple logo. then try to connect to your PC

---

### Post by asuastrophysics on 2009-08-06
> **fennec_fox said:**
> I'm not really that familiar with ipods but, I have this problem with some other devices occasionally. It works for me if I take it to windows or mac, let it mount, then safely remove it. You might want to try it. I have the same problem with my mp3 player (not ipod). 

Do Ipods have a function to change mount options such as like mount as "mass storage device" or anything? 

Mine does and when I changed it to mass storage device instead of mp3 player I stopped having this problem.

fennoc fox, you are correct! :popcorn: 

thank you! i have no idea why the ipod would need a windows machine but after connecting it and then ejecting it, i went over to ubuntu and it mounted right up! 
thanks again! :guitar:

does anyone know the technical reason why it must mount to windows every so often?

EDIT: my ipod only had ~ 100 MB of free space on it out of 30 GB. iTunes told me it was full and i deleted 500 MB of music.

---

### Post by fennec_fox on 2009-08-06
Windows has "suspend" and active?? (I forget what it's called when it's mounted) modes. 

If it doesn't get removed correctly or doesn't write correctly it doesn't appear suspended then when you try to mount it in linux it doesn't want to mount. I think the device still thinks it's mounted or active.

That answer is only like 50% correct. I can't remember the specifics but, that's kind of the idea.

---

