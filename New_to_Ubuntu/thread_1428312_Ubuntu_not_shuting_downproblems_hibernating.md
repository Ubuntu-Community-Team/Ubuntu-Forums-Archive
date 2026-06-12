---
title: "Ubuntu not shuting down/problems hibernating"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by aloprot on 2010-03-12
I tried to shutdown my laptop and it didn't worked. So i manually(from the button)shut it down. Also if I hibernate i get to errors one irq_sata and one starting with E i didn't get that error. Finally it turns down in hibernate but when resuming ohh man do i get a color show.. blank screen with red lines /green lines for endless time but finally i see the login screen and i get into ubuntu. Also in my taskbar a wierd tray icon appears and when my mouse cursor is on it it says something like"session active, not inhibited screen idle.If you can see this text, your display server is broken and you should notify your distributor. Please see.....blogs.gone.org/......
What is this and how can i get my laptop to shut down properly every time and to hibernet or suspend with no problems?

---

### Post by aloprot on 2010-03-12
bump*

---

### Post by ubunterooster on 2010-03-12
try 
```

sudo shutdown -h 0

```
in the terminal to shut down. Does that work? Also hibernation is a weak spot in Linux. :(

---

### Post by aloprot on 2010-03-12
That command works but what can i do to hibernate aswell and what's with that server display bug? How do i fix it?

---

### Post by aloprot on 2010-03-12
bump?

---

### Post by ubunterooster on 2010-03-12
I know hibernate to be very slow and have stopped using it because of that. Oh, and that light show I've gotten on mine, but on yours it may be related to the server display bug.
 [guess:
1 display bug is a screensaver related problem.
2 a hardware problem causing difficulty stopping your video card]
 Does the screensaver come on when it's supposed to?

---

### Post by ubunterooster on 2010-03-12
Oh, and by the way, both times you bumped, you did it while I was typing a response. So unless it is extremely urgent, try going a little easier on bumping. No insult taken here, hopefully none received by you.

---

### Post by aloprot on 2010-03-12
Excuse me for bumping so much is just that I want to get that issue fixed. Well my screen saver is set every1 minute when the laptop is idle. I get that lightshow and slowness too. And sometimes now has appeard that tray icon saying display server is broken...it s a hardware issue or  a software one? what do i do then?

---

### Post by ubunterooster on 2010-03-12
Not sure, actually. Right now I'll search forums for solved threads about broken display servers.

 from what you are saying, it appears that hibernate is working properly as it has been slow on all four computers with Ubuntu that I touched.

My first thought is to reinstall, but that will do nothing if the problem is hardware. I hope you are using either 8.04 LTS or 9.10.

You could do some searching too if you are inclined to do so, or just go to the community cafe to kill time.
 I'll write when I find more info, but am not promising it will be today....

---

### Post by aloprot on 2010-03-12
I use 9.10 amd 64 with a brand new laptop. If this helps as I said above, I have problems seeing my screen saver, I set it to start after 1minute when computer is idle and it starts after 3 -4 minutes. I tired to search this problem and only come up with this if it helps:
[http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/](http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/)

But I don't know what I should do next. There is some code(updates..) that I honestly don't know were to put it.
Thanks so much!

---

### Post by ubunterooster on 2010-03-12
Ugh! It is likely a hardware/driver issue. The link is likely to be useful, I'll go read through it.............

---

### Post by ubunterooster on 2010-03-12
Not likely a related link. Try setting the screensaver for 5 min.

---

### Post by aloprot on 2010-03-12
Ok, I'll do that.

---

### Post by ubunterooster on 2010-03-13
Any difference?

---

### Post by aloprot on 2010-03-13
No, sadly no, and now my weather raport doesn't work too.....it sais --       "Forecast not currently available for this location."

---

### Post by sfordin on 2010-04-24
Hibernation works great for me with 9.10 Karmic on my Toshiba A205 laptop. The trick I discovered is that you need to unmount any SD cards or USB drives before hibernation. For example, I always keep an SD card mounted for incremental backups of my work, but if I forget to unmount the SD card before hibernation, my machine will hang with a black screen when I try to hibernate it.

Also, if you are running a MythTV backend on the machine, you need to shut down that backend before hibernation. Forgetting to do so will similarly prevent the machine going into hibernation.

I added two alias statements to my ~/.bash_aliases file to make this process more convenient:

```
alias hiberprep='sudo umount /media/LAZARETTE;sudo service mythtv-backend stop'
alias mythstart='sudo service mythtv-backend start'
```

For the "hiberprep" alias, replace "/media/LAZARETTE" with the name of the mount point for your SD/USB card. "/media/LAZARETTE" just happens to be where my SD card is mounted.

So, before hibernating, I issue the command "hiberprep", wait a few moments, and then choose Hibernate from the Gnome shutdown menu. Note that I do not have to actually physically remove the SD card from the card slot on the machine. Note also that I wait for the machine to finish hibernating before closing the lid.

When I wake up the machine, the SD card, still sitting happily in the card slot, is automatically remounted. To restart the MythTV backend, I use the "mythstart" alias I created in ~/.bash_aliases.

Hope this helps,

Scott

---

