---
title: "Lost Splash after Update"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by Desert Sailor on 2009-04-16
This is very low priority, but I would like to learn from the experts.  I run my update weekly and after last weeks update I lost the startup splash  the screen with UBUNTU and the progress bar.  Now I get a black screen starting with "reading files needed to boot" and then a scroll of procedures and start ups.  The system comes up and runs fine, but I became used to the start up splash.  

I also lost the sutdown splash, but now all I get is something like "Acpic exiting" (I don't remember exactly).  The system shuts down and turns off without problems so it isn't really a big deal....but. 

I checked the swap ID and it matches, but that is the extent of my knowledge.  If anyone else has had this problem and knows how to get the splash back, let me know, if not, then don't worry because Ubuntu works fine and I'm loving being free from the Evil Empire of Redmond.

---

### Post by LostMagix on 2009-04-16
I would start by down downloading startup-manger from add/remove and tweaking around with it for a bit, see if you cant get it back that way.

---

### Post by Desert Sailor on 2009-04-16
That's an interesting suggestion.  I have downloaded Startup Manager and when I click on it, it flashes on the screen and then dies.  I think maybe I'll remove it and then try to download and install again.  Perhaps that is the problem since these updates haven't affected anyone else that I can tell.

---

### Post by LostMagix on 2009-04-16
There are quite a few programs that will do it, just search around add/remove and synaptic

---

### Post by nvteighen on 2009-04-16
The default splash is installed from the **usplash** package. Try reinstalling it using the following command at the Terminal:

```

sudo apt-get install usplash --reinstall

```

The splash won't be available till the next boot up. If any error occurs, please post the output.

If it reinstalls without error but doesn't work, then please post the content from /boot/grub/menu.lst (for God's sake [b]
don't[/b] use sudo... you don't need it to open the file in read-only mode!).

---

### Post by zvacet on 2009-04-16
Backup your manu list 

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Open menu list with 

```
gksudo gedit /boot/grub/menu.lst
```

and see in lines 

root=UUID=xxxxxxxxxxxxxxxxxxxxx ro quiet splash

**quiet** is word you need

---

### Post by Desert Sailor on 2009-04-16
Wanted to post that the problem is solved.  

This is what I did, based on some information I found in another string.  Thanks to Jakey_TheSnake for his answer. 

```
sudo gedit /etc/usplash.conf
```

I made sure my resolution was correct for my video settings and monitor. 

```
sudo update-usplash-theme usplash-theme-ubuntu
```

Made sure I had usplash set. 

Then Finally.... 

```
sudo update-initramfs -v -u -k all 
```

After that I rebooted and voila, the splash was back both log-on and log-off.  

The tragedy is I don't know what I did.  But that will come with time and fooling around with the commands and getting to know everything.  

THANKS to the Family...you guys are great!!!

---

### Post by Desert Sailor on 2009-04-16
One last thing...  It appears that STARTUPMANAGER was failing because it couldn't find the usplash file.  Once the system was repaird and working properly, then Startup Manager started working also.

---

