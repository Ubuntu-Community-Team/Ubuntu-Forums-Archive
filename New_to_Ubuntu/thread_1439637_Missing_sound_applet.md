---
title: "Missing sound applet"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by clive littlewood on 2010-03-26
Hi All

I am wondering if anybody running Lucid Beta has lost their sound applet from the top panel.

Any Ideas how I can get it back !!!!

Clive

---

### Post by NightwishFan on 2010-03-26
You will need to add the indicator applets I believe. I am not running lucid now so I do not know what to say.

---

### Post by dnairb on 2010-03-26
Possibly the notification area has been lost from the panel and needs to be added.

---

### Post by clive littlewood on 2010-03-26
Hi

No all the other notification apps are there.



See screenshot.


/home/clive/Desktop/Screenshot.png



Clive

---

### Post by NightwishFan on 2010-03-26
Check if Gnome Volume Control applet is included in the System -> Preferences -> Startup Applications. It is called "Volume Control" If not add it:

Name: Volume Control
Command: gnome-volume-control-applet

After that, in either case, press alt+f2 type:
```
gnome-volume-control-applet
```
Then push enter, does volume control return to panel?

---

### Post by clive littlewood on 2010-03-27
Hi

Thanks nightwishfan that did the trick (although i still do not know how it disapeared ????)

I will mark as solved

Clive

---

### Post by markackerman8@gmail.com on 2010-04-12
This has happened to me quite afew time with my tinkering and just lived with it ... but this thread solved the ongoing problem though I would sure like to know why it disappears?

Thanks for your help! :)

---

### Post by davmax on 2010-04-13
I have just installed Ubuntu 9.1 and noticed two volume control applets. I removed to non functional applet, but this also removed the functional one.

I have not been able to return the applet to the panel.
I have made sure there is a Volume Control entry in the Startup Programs list, even Removed it and then used Add.

How is it possible to get the applet back into the panel? It is not listed in the ADD to Panel listing.

All updated have been installed.

---

### Post by markackerman8@gmail.com on 2010-04-13
Did you try ....
# gnome-volume-control-applet
in terminal, like suggested above?  It worked for me and I put the exact command line in the startup program and it stays after reboot.  

I hope that helps.  Ubuntu and sound are often finicky, arghhhh.   But getting better, and with 10.04 even better functionality still! (so I hear reported)

---

### Post by btermeli on 2010-04-30
Hey all,

> gnome-volume-control-applet

That works but volume control appears with different icon than choosen icon set. Do somebody know how to change volume control's icon?

---

### Post by Ryders on 2010-08-04
```
gnome-volume-control-applet &
```

is the old volume indicator and has a different layout. What you are looking for is the Indicator Applet

see: [http://newyork.ubuntuforums.org/showthread.php?p=9015573#post9010295](http://newyork.ubuntuforums.org/showthread.php?p=9015573#post9010295)

hth

---

### Post by agarciamog on 2010-08-14
> **btermeli said:**
> Hey all,

That works but volume control appears with different icon than choosen icon set. Do somebody know how to change volume control's icon?


I had a similar issue. All you have to do to restore Lucid's icon is install indicator-sound by doing the following:

```
sudo aptitude install indicator-sound
```

It'll probably give you a warning telling you it is reverting to an older version. Simply enter 'y' for yes and you'll be on your way. The last step is to log out and log back in. If you have any questions feel free to contact me.

---

### Post by azitizz on 2010-09-29
This was the simplest and best solution I have found. Thank you! it worked for me too. Some other solutions I looked up forced you to have to also include the icon for the mail client which I dont use.

---

### Post by azitizz on 2010-09-30
Actually since rebooting my computer its dissapeared again. I type "gnome-volume-control-applet" in terminal and it appears right away. 

However as soon as I try and close terminal it gives me a warning that a process is running and shutting down will kill it, which in fact it does. 

I have to keep terminal open and it seems to run indefinately in order to keep the control icon on the task bar. 
Any Ideas?.

---

### Post by dandy76 on 2011-02-03
[LEFT]Well I find it too clumsy to run "gnome-volume-control-applet" manually.
I've just added it into "System -> Preferences -> Startup Applications" so it gets launched automatically whenever I log in

[/LEFT]

---

