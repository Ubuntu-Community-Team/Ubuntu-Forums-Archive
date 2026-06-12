---
title: "Belkin F5D7050 (Version 3000) in Feisty Fawn"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by lual3x on 2007-08-21
Hi,
I have a Belkin F5D7050 (Version 3000) wireless card and wanted to know how I could get it to work with Ubuntu Feisty Fawn (because I want to get rid of Windows). So I booted into the LiveCD and Ubuntu seems to recognize it. In the top left (I think it's called the notification area), It shows the network icon and it's able to find my router which is also a from Belkin (it's SSID is Belkin_Pre-N_533906 and I temporarily removed any encrption on it). However, when I tried to connect to it, the icon will change into to things going around in a circle for a while, and then revert back to the icon before it. Next, I went to my MacBook and created a network (I think it's an ad-hoc network) and Ubuntu recognized it as well, but it did the same thing as my Belkin router. Anyways I decided to take some screenshots of the problem.
Here's what happens when I first click on the network icon: [http://img224.imageshack.us/my.php?image=screenshot1pp3.png](http://img224.imageshack.us/my.php?image=screenshot1pp3.png)
Then after I choose the Belkin Router this happens: [http://img72.imageshack.us/my.php?image=screenshot2wm5.png](http://img72.imageshack.us/my.php?image=screenshot2wm5.png)
When I click on it while the stuff is spinning: [http://img103.imageshack.us/my.php?image=screenshot3xi7.png](http://img103.imageshack.us/my.php?image=screenshot3xi7.png)
And after a while, nothing happens and it goes back looking exactly the same as the first screenshot.
I read a few of the online tutorials, and they either were for a different version of Ubuntu, the Belkin wireless card, or required a working internet connection.
Any help will be appreciated!
Thanks

---

### Post by Darkhack on 2007-08-21
I personally have never had good luck with NetworkManager.  It's extremely buggy in this release of Ubuntu.  Try configuring it manually through the command line and do it unencrypted first to make sure you are able to connect before adding the security.  I'll assume the device is listed as wlan0 although it may be listed as eth1 or some other name.  Hopefully you know the proper IP addresses for the configuration of your router.

sudo iwconfig essid Belkin_Pre-N_533906
sudo nano /etc/network/interfaces
[QUOTE=/etc/network/interfaces]
auto wlan0
iface wlan0 inet dhcp
gateway 192.168.1.1
netmask 255.255.255.0  **OR** netmask 255.255.255.*255*
broadcast 192.168.1.255
network 192.168.1.0
essid Belkin_Pre-N_533906[/QUOTE]
sudo ifconfig wlan0 up
iwconfig wlan0  <-- check to see if your ESSID is set and if you have a signal
ping google.com  <-- test for a connection then Ctrl-C to exit

If it fails try...

sudo killall dhclient3
sudo killall dhclient
sudo dhclient  <-- restart DHCP client to fetch an IP from the router.

If this works, then here is a link for the guide to add WPA -->  [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by lual3x on 2007-08-22
Thanks for the help, however the first command didn't seem to work at all, and I am unsure whether or not to still edit /etc/network/interfaces (here's what it looks like: [http://img401.imageshack.us/my.php?image=screenshotre1.png](http://img401.imageshack.us/my.php?image=screenshotre1.png)). This is what my /etc/network/interfaces looks like 
```
  GNU nano 2.0.2         File: /etc/network/interfaces                          

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

``` 
So should I go ahead and add
```
auto wlan0
iface wlan0 inet dhcp
gateway 71.136.224.58
netmask 255.255.255.0 OR netmask 255.255.255.255
broadcast 192.168.1.255
network 192.168.2.1
essid Belkin_Pre-N_533906
```
to the bottom of my /etc/network/interfaces even though the first command didn't work?
sudo ifconfig wlan0 up and
iwconfig wlan0 seem to work fine. Here's the output of my iwconfig wlan0:
```
ubuntu@ubuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:50:2A:0E:8B   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
and btw, here's my router info: [http://img251.imageshack.us/my.php?image=picture1dj8.png](http://img251.imageshack.us/my.php?image=picture1dj8.png)

---

### Post by Darkhack on 2007-08-22
Yeah, do it anyway even if the first command didn't work.  You might need to reinitilize the network though so that it reads the new configuration file.

sudo ifconfig wlan0 down  <-- bring the interface down first or else the "up" command won't read the new interfaces file
sudo ifconfig wlan0 up   <-- bring it back up

---

