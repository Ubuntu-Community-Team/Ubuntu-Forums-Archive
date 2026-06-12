---
title: "Anyone got D-link DWA-140 to work?"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by ftornell on 2007-10-17
Hi,
is there anyway to get this card to work under linux?
I know its not listed as any ubuntu or linux compatible wireless card but think many ppl got it?

---

### Post by geirhoe on 2007-10-19
I have a partial success using the DWA-140 on gutsy. I am able to connect and use a wlan, but the connections dies after a few minutes.

here is what I did:

1) install ndisgtk and ndiswrapper with the package manager

2) start ndisgtk (sudo ndisgtk)

3) Select install driver

4) select the inf file from the cd-rom (on my cd the path was setup/Drivers/Drivers/WinXP_2K/rt2870.inf)

And that's it.

---

### Post by ugnomes on 2007-11-04
Hi, excuse me for my English but i am Italian...
Use ndiswrapper 1.47 but not 1.48 or 1.49.With ver.1.47 dwa-140 it's go very well.....You can get ver.1.47 from [www.sourceforge.net.....Ciao](www.sourceforge.net.....Ciao) Ciao:)

---

### Post by tennisfreakco07 on 2008-06-09
> **geirhoe said:**
> I have a partial success using the DWA-140 on gutsy. I am able to connect and use a wlan, but the connections dies after a few minutes.

here is what I did:

1) install ndisgtk and ndiswrapper with the package manager

2) start ndisgtk (sudo ndisgtk)

3) Select install driver

4) select the inf file from the cd-rom (on my cd the path was setup/Drivers/Drivers/WinXP_2K/rt2870.inf)

And that's it.



I'm relatively new, and have been having the same problems as not finding a easy tutorial or an english one to help me but i ran across some random website, and it said to use ndisgtk and diswrapper and use the old xp driver (for xp sp2 found on my cd). So far it's working and even the light on the dwa 140 is working. I've been on for about 10 minutes as of now, so hopefully none of the above problems occur.

---

### Post by bioshake on 2008-07-14
What did you guys do after you set up ndiswrapper?

Did you use the network-manager to configure your wireless settings or otherwise?

Anyone using WPA with this?

---

### Post by habicht on 2008-07-16
This is how I got the DWA-140 working with WPA on 2.6.24:
(you might need to 'sudo apt-get install build-essential' to make compilation possible)

1. Download driver archive for RT2870 from [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
   (for me it was [http://www.ralinktech.com.tw/data/drivers/2008_0528_RT2870_Linux_STA_v1.3.0.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0528_RT2870_Linux_STA_v1.3.0.0.tar.bz2))

2. extract and enter folder

3. edit Makefile, set
   TARGET = LINUX

4. edit os/linux/config.mk, set

   HAS_WPA_SUPPLICANT=y
   HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

5. make

6. make install

7. insmod os/linux/rt2870sta.ko
     (-> make sure you use .KO not .O !!!)

   ifconfig ra0 up


Connecition configuration:

8. open Network Manager (e.g. System > Administration > Network, or use applet > Manual configuration...)
   - Unlock
   - choose "Wireless Connection" > Properties
   - disable "Roaming Mode"
   - set ESSID
   - set Password Type "WPA Personal"
   - type Network Password
   - set configuration "Automatic Configuration (DHCP)"
   - OK

9. to get the interface up on startup I added the following line to "/etc/rc.local":
   ifconfig ra0 up

That's it!

More information can be found in the README_STA which is in the downloaded archive.

I don't know if it's really necessary to copy RT2870STA.dat to /etc/Wireless/RT2870STA as they way... Worked for me without.

The only problem that's still left is that I need to disable and re-enable networking in the Network Manager applet (right-click) to get it working. Moreover, after removing and re-inserting the the USB stick, I need to "ifconfig ra0 up" again before I do the disable/enable trick again.

"/etc/init.d/networking restart" does not work as replacement for disabling/enabling via the nm-applet.

Any solution to automatize that?

---

### Post by Epiphany on 2008-07-24
> **habicht said:**
> The only problem that's still left is that I need to disable and re-enable networking in the Network Manager applet (right-click) to get it working. Moreover, after removing and re-inserting the the USB stick, I need to "ifconfig ra0 up" again before I do the disable/enable trick again.

"/etc/init.d/networking restart" does not work as replacement for disabling/enabling via the nm-applet.

Any solution to automatize that?

Thanks for your tutorial, worked awesome! However, I am having the same issue. Anyone have a solution?

---

### Post by sirgogo on 2008-07-24
Hey all,

I also gave this a shot. I followed the instructions and the installation went fine, but I still can't get any internet/real wifi connection. Hows this? ([http://ubuntuforums.org/showthread.php?t=766850&page=1](http://ubuntuforums.org/showthread.php?t=766850&page=1))

---

