---
title: "Wireless Driver..??"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by motermouth on 2007-10-31
Hey,
   I've been trying to almost a week now non stop to get my latptop's internal wireless card to work. I have a Dell Latitude D510 and it has a Broadcom BCM4318 internall wireless card. I can't seem to get it to work and i finally came to the conclusion that i don't have the right driver. Could someone please help me in finally getting it to work. Thanks for you help and the sooner the better!

---

### Post by motermouth on 2007-11-01
Anyone? Please i would like to get this laptop working sometime soon!! And i dont wanna install windows just to get it to work.

---

### Post by srt4play on 2007-11-01
What version of Ubuntu are you using?

I would use ndiswrapper to get it working.  If you can, connect the laptop to the internet with a hard-wired connection and install ndiswrapper-utils-1.9.  

In a terminal, navigate to the directory that holds the windows driver for the wireless card and do:

```
sudo ndiswrapper -i name-of-file.inf
```

Replace name-of-file.inf with the real name of the file.  On my laptop, it's bcmwl5.inf.  I can't check right now but I think it's also a 4318. 

Still in the terminal, do:

```
sudo nano /etc/modules
```

and place the word ndiswrapper at the end of the file on it's own line, ctrl-o to save and then ctrl-x to exit.

Still in the terminal, do:

```
sudo nano /etc/modprobe.d/blacklist
```

and place the word bcm43xx at the end of the file on it's own line, ctrl-o to save and then ctrl-x to exit.

Reboot and see if it works.

---

### Post by motermouth on 2007-11-01
Thanks but i got this message...

couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.

---

### Post by kevdog on 2007-11-01
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

---

### Post by motermouth on 2007-11-02
Hey thanks...i got all the way down that list until the second to last step on the page and i put the command into the command promt...it comes to a point where it asks you if you want to continue. I type Y and push enter because thats what it says to do but no matter what i do it aborts. What am i doing wrong? And more importantly HOW DO I GET MY WIRELESS TO WORK?????

---

### Post by kevdog on 2007-11-02
Can you be more specific about where you are getting stuck -- Im confused.

---

### Post by motermouth on 2007-11-03
yea...before i did all of that last stuff my wireless card showed up in my network configurations. I also had it enabled to roam but when i clicked on the network thing it said wireless networks but nothing ever showed up underneath it. Now after i did all of that stuff my card doesn't show up in the network configurations at all.

---

### Post by motermouth on 2007-11-04
Hey kevdog...i tried to use your guide on ndiswapper but i kept getting errors while downloading the 43xx driver...and it said there was no such command as make install. So could maybe i get help with that too...if its going to help me w/ my wireless?

---

