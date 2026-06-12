---
title: "[SOLVED] awus036h (rtl8187l) with wpa natively hardy"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by matjaz on 2008-10-18
( a note before you read this:
 the configuration described below works for me pretty well (on kernel 2.6.24-21, ubuntu - on previous kernel it didn't work at all ), but i have noticed in the past that it got pretty unresponsive - google ping ~ 3000ms. The ping problem might had been caused by heavy downloading of somebody else on that also connects to the internet through my router, so i can't say it is the driver's fault. If it works for you, please post below.
I also can't change my mac address with this driver on current kernel, which is something i could do on 24-19 )
CONFIGURING AWUS036H (rtl8187l) FOR USE WITH WPA
About this post:
There seems to be a lot of people having trouble with getting this adapter to work with ubuntu, kernel 2.6.24-21.
I got my  awus036h (the famous Alfa) wrking and in this post I will try to explain how I did it. The part marked with STRANGE puzzles me a bit, so if you can improve that or explain it, please do so.
At the moment, I am using the alfa card with native driver (r8187, patched from aircrack-ng site), and I am connected to a wpa protected AP. I also haven't uninstalled my network manager, just when i am not using it, i stop it.

The &#8220;howto&#8221; :
Assumptions:
-you have read the (excellent) tutorial [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495) and you still cant get it to work
-wlan2 is your network interface that uses the alfa card

Important: If you have a bad connection with your current settings, download everything from 3. (wget [http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip](http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip), wget [http://patches.aircrack-ng.org/rtl8187_2.6.24v3.patch](http://patches.aircrack-ng.org/rtl8187_2.6.24v3.patch) - you will have to move the patch to rtl8187_linux_26.1010.0622.2006/ afterwards
-  and make a copy of [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495) before you disable your driver.

first of all, stop your NetworkManager:
```
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
```
(It will still start when you log into gnome next time.
You can start it manually too, just replace stop with start.)
1.if you are using awus036h with ndiswrapper or any other driver, do your best to remove that driver from the kernel. If you are using ndiswrapper,  ```
sudo modprobe -r ndiswrapper
``` should do it.
2.blacklist rtl8187: append the line
```
blacklist rtl8187
```
to the /etc/modprobe.d/blacklist.
If you have rtl8187 loaded in kernel, remove it (sudo modprobe -r rtl8187) or for safety restart your computer
3.execute the following ( the instructions how to install and patch the driver from [http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187) ):
```
ifconfig wlan2 down	 
wget http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip
unzip rtl8187_linux_26.1010.zip
cd rtl8187_linux_26.1010.0622.2006/
wget http://patches.aircrack-ng.org/rtl8187_2.6.24v3.patch
tar xzf drv.tar.gz
tar xzf stack.tar.gz
patch -Np1 -i rtl8187_2.6.24v3.patch
make
sudo make install
```
then restart your cpu
4.write your wpa_supplicant.conf (and install wpasupplicant, if you haven't done that already), as described in [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495) in section WPA Connection - WPA-PSK or WPA2-PSK.
Follow that guide up to the point where it says "2. Connect via command line"
5. open a terminal and execute:
```
sudo ifconfig wlan2 down
sudo dhclient -r wlan2
sudo wpa_supplicant -w -dd -iwlan2 -c/etc/wpa_supplicant.conf
```

6. open another terminal and when the first terminal gets to ```
EAPOL: startWhen --> 0
```
or stops for a while, execute:
```
sudo ifconfig wlan2 up
sudo iwconfig wlan2 mode Managed
sudo dhclient wlan2
```

If everything went well, you now have a working connection.
The STRANGE bit is that the first terminal will remain open, for as long as your connection will be up (i don't know if that is wrong, i just find it strange).
For some reason, when i boot i have to DO ALL THAT TWICE before it works
(by all that i mean everything in 5. and 6.- before you do it again, quit the terminal from the first attempt - ctrl+c ).

If all that works, you can use the following script the next time:
```
#!/bin/bash

# this is a script that connects me to my home wpa network

# check if NetworkManager is running
foo=`pgrep NetworkManager`

sudo echo "$foo"

if [ -n "$foo" ]
then
	echo shutting down network manager and dispatcher
	sudo /etc/dbus-1/event.d/25NetworkManager stop
	sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
	sleep 10
fi

# start the connection
sudo ifconfig wlan2 down
sleep 2
sudo dhclient -r wlan2
sleep 2
# run wpa_supplicant in another terminal:
gnome-terminal -x sudo wpa_supplicant -w -dd -iwlan2 -c/etc/wpa_supplicant.conf
# wait for wpa_supplicant: (increase the time if it takes longer to get ready)
sleep 15
sudo ifconfig wlan2 up
sleep 2
sudo iwconfig wlan2 mode Managed
sleep 2
sudo dhclient wlan2
```

Note 1: sometimes you must run it twice. (When the first terminal stops, you can exit it with ctrl+c, and after that run the script again if it didn't work the first time)
Note 2: for me at least, everything works a whole lot better if i don't have my adapter plugged in when i boot or i plug it out after boot and than plug it in again.
Note 3: the sleep 2 inside the script also seems to help...
Note 4: sometimes i have to run the script twice, becouse my connection drops after a minute or so.

But in general, the connection is reliable (or at least it was up to this moment).
I have downloaded 800MB from a torrent to test it and it held for that time ~ 1,5h at least.

Hope this helps someone.
Matjaz

---

