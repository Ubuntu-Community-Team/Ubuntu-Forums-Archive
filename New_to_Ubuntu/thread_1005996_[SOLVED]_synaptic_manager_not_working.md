---
title: "[SOLVED] synaptic manager not working"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by anirup on 2008-12-08
**i use ubuntu8.04**. **i installed edubuntu desktop on** it.however it didn't  install completely.but synaptic manager was still working.i then installed **mpg123-alsa** through a deb file that i had downloaded from the net with the help of **gdebi **installer and not from the software channel.gdebi got hanged during installation and i had to force quit.however mpg123-alsa installed all right.now when i try to open synaptic manager or try to install a deb file using gdebi the screen says checking for dependencies and then hangs.i waited for around 5 minutes but still no change.i again had to force quit.i tried dpkg --configure-a and sudo apt-get -f install but again faced the same problems.**plz help** i just migrated from kubuntu to ubuntu but never faced such kind of problem in kde.

---

### Post by anirup on 2008-12-08
i use **ubuntu 8.04**.i want to repair ubuntu installation by reinstalling it but **i don't want to lose any program**.i am having problems with **synaptic manager** and programs related with it.is there any other way out?

---

### Post by inobe on 2008-12-08
their a are few methods of repairing synaptic, what problems are you having ?

---

### Post by overdrank on 2008-12-08
Merged and Moved to ABT Absolute Beginner Talk
You may try and use the command in the terminal 
```
sudo apt-get install -f
``` and also
```
 sudo dpkg --configure -a
```

---

### Post by anirup on 2008-12-09
**i tried both but it didn't work**

---

### Post by Peter09 on 2008-12-09
You need to tell us what error messages you are getting. Why is it not working?

---

### Post by anirup on 2008-12-10
it says building dependencies proceeds till 50% and then stops responding.also i found out my cpu usage was at 100%.

---

### Post by Michael.Godawski on 2008-12-10
> **i use ubuntu8.04**. [B]i installed edubuntu desktop on;
[/B] i just migrated from kubuntu to ubuntu but never faced such kind of problem in kde. 	   	  	     		 	       	 		   

You are really travelling :p. Your voyages might produce some confusion in your sources.

Can you please post your sources.list here:

```
cat /etc/apt/sources.list
```

---

### Post by anirup on 2008-12-14
I got it allright by using **sudo apt-cache unmet**

---

