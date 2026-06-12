---
title: "Low Resolution after login?"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by Beanmonster on 2010-05-28
Hey guys :)

The last thing I want to do is start another thread going on about the display problems in Lucid after installing nvidia drivers...

After a lot of trouble and three re-installs I got things semi-working.

Plymouth and gdm login work nicely, but _after I log in resolution drops to 800x600_.
Any suggestions on a fix? i will post xorg.conf if needed.

Thanks for your time :)

---

### Post by cariboo on 2010-05-29
Open a terminal (Applications->Accessories->Terminal) and type:

```
sudo nvidia-xconfig
```

The above command will create a new /etc/X11/xorg.conf file, once the file has been created, reboot, your desktop should be the proper resolutions. If you want to adjust the resolution and have it stick, press Alt-F2 and type:

```
gksu nvidia-settings
```

choose the resolution you want and click save.

---

### Post by Beanmonster on 2010-05-31
haha, sorry cariboo, i should have been more specific. 

The problem is a bit more complicated.

Now, plymouth splash is at the correct resolution (1280x1024) but the screen goes black after that...

I CTRL+ALT+F1, login and run ```
sudo service gdm stop
``` which provides me with a black X cursor, then CTRL+ALT+F1 again and start the service to get the login screen, which is now 1024x768 btw.

After logging in, my desktop resolution changes to 800x600.

Any suggestions would greatly be appreciated, otherwise I'll have to revert back to Karmic.

Thank you

---

### Post by Bob Bertrands on 2010-05-31
This site solved my problem, give it a try:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

Good luck

B

---

### Post by Beanmonster on 2010-05-31
Thanks for your quick response bob, but unfortunately that doesn't solve my problem.

I think it has something to do with xserver. grub and plymouth are at high resolution then black screen... after service restart, gdm login is at 1024x768 and my desktop itself 800x600.

---

### Post by genis200 on 2010-05-31
I had this same problem with NVIDA drivers, what I did to fix this problem is to install an earlier version of the drivers.

---

### Post by Beanmonster on 2010-05-31
Tried older drivers and also tried older xorg versions... Still no luck.

I am stumped as to what could be causing this.

---

### Post by Chipshot on 2010-05-31
> **Beanmonster said:**
> Hey guys :)

The last thing I want to do is start another thread going on about the display problems in Lucid after installing nvidia drivers...

After a lot of trouble and three re-installs I got things semi-working.

Plymouth and gdm login work nicely, but _after I log in resolution drops to 800x600_.
Any suggestions on a fix? i will post xorg.conf if needed.

Thanks for your time :)
   	 	 	 	 	 	  My system had a similar problem. It got corrected by going to System, Administration and clicking Hardware drivers. It installed a Nvidia Proprietary driver. Then a copy of xorg was saved and the original was overwritten using the changes below that reflect the Acer monitor specs connected.

Section "Monitor"  	Identifier	"Configured Monitor" 
         HorizSync        30-82 
         VertRefresh      60  
 EndSection 
  
 Section "Screen" 
 	Identifier	"Default Screen" 
 	Monitor		"Configured Monitor" 
 	Device		"Configured Video Device" 
        	DefaultDepth	24 
         SubSection      "Display" 
         Depth           24 
         Modes           "1440x900_60 
         EndSubsection  
 	Option	"AddARGBGLXVisuals"	"True" 
 EndSection 
  
 Section "Module" 
 	Load	"glx" 
 	Disable	"dri2" 
 EndSection 
  
 Section "Device" 
 	Identifier	"Configured Video Device" 
 	Driver	"nvidia" 
 	Option	"NoLogo"	"True" 
 EndSection
 

 This is what is being used now and the resolution now “sticks” when booting from “User” to the “Desktop.”

---

### Post by Beanmonster on 2010-06-01
I got my system working, not the way i intended to do it, but hey.

So i resorted to ANOTHER fresh install of lucid. 
Manually installed the latest nvidia drivers off their site (NOT REPOSITORY)
Used the guide [Bob posted]("http://ubuntuforums.org/showpost.php?p=9387812&postcount=4").

Only issue I'm having is a white desktop for 30 seconds after login... ah well.

Thanks everybody who offered their support!

---

