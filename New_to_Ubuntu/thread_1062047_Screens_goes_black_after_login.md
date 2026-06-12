---
title: "Screens goes black after login"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by gnt64a on 2009-02-06
Hi there, firstly i wanna say that i love Ubuntu so far but i've got a problem.

Somehow I have changed something in the appearance settings and when i login to ubuntu it boots up ok but then the screen goes black, if i hover above or select "applications, places, system" or anything else i get a strange pattern then the screen goes black.
So i cant do anything at all.

How could i switch back to my original settings from the "command line", i have just bought a book "begining ubuntu linux" and cant seem to find anything in there to help.

Is there a better book i could buy as i am quite new to Linux?

Any info would be much appreciated.

Thanks for looking

Graham.

---

### Post by jbrown96 on 2009-02-06
It's usually a problem with Compiz that causes this, which is in the appearance section. Usually, you can toggle it on and off and then everything works fine. That doesn't do you a whole lot of good because you can toggle it. 

What I'm going to recommend is reseting the the graphics driver to something that doesn't support Compiz, so it can't load. This should get you to an ugly but functional desktop. Then, we can load the proper driver and try Compiz again. 

Just a couple of things first.
1) What type of graphics card do you have? You can get to a shell login by pressing Crtl+Alt+F1 at your black screen. and try ```
lspci | grep VGA
``` the manufacturer and model number are important. 
2) What drivers are you currently runnging? Did you install them manually, or use the Hardware drivers application?

Number 2 is important because we may need to try different drivers depending on your card.

Remove the proprietary drivers
1) get to a shell login and login (mentioned above).
2) kill the x-server. ```
sudo /etc/init.d/gdm stop
```
3) reconfigure the x-server. I can never seem to remember the exact command, but it's something like ```
sudo dpkg-reconfigure xserver-xorg
``` but there may be one or two hyphens before the xserver bit. Just accept the defaults. 
4) start the xserver. ```
startx
``` You should now have a desktop. 

Write back with the answers to the two questions and we can figure what should be next.

---

### Post by gnt64a on 2009-02-06
Hi jbrown,
thanks for the reply.
Here is the reply to your question.

"VGA compatible controller Intel Corp 945GM/GMS, 943/940 GML express inergrated graphics controller(rev 03)"

i hope this correct and look forward to your reply.

i haven't installed any drivers the only ones are the ones from installation cd.

cheers Graham

---

### Post by jbrown96 on 2009-02-07
I've never done much with Intel graphics, but they are open-source friendly, so it should be automatic to fix if it is a driver problem. 

Go ahead and do the four steps from my last post and see where you get, but do some extra steps for backups. 

Before step 3, run the following
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```
This saves a backup of your display settings, so if the situation somehow gets worse, it can be restored by running the same commands but changing the files so xorg.conf is second and xorg.conf.back is first.

---

