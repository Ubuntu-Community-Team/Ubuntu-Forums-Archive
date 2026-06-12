---
title: "[SOLVED] WG311v3 finally working, but not quite right"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by redmonster13 on 2007-08-16
I got everything working with my wireless (wg311v3) after 2 days of headaches and install/uninstall woes. I am using wicd becuase network-manager wouldnt work at all. My only problem now is that wicd doesnt connect automaticly on startup, this is going to cause me a small headache as well.

I am using the system this is on for record keeping and such as well as for folding@home. The folding program requires a good connection unless I want to babysit and reconnect when it needs to send results.

Does anyone know of a way to get wicd to automatically connect on system start?

---

### Post by imdano on 2007-08-16
Does wicd start normally and just fail to connect, or does wicd not start properly at all?  Did you make sure you checked the "Automatically connect to this network" box?

---

### Post by dannyboy79 on 2007-08-16
well, does wicd change your interfaces file located within /etc/network? if it does, then you can just add pre-up info within your interfaces file because when networking starts, it runs the ifup command which then parses your interfaces file. here's an example of how an interfaces file should look (details might be different like WPA versus WEP etc etc) I have also added the link to where I got the interfaces example which may help also.

auto wlan0
iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
    pre-up iwpriv wlan0 set SSID="YOUR_SSID"
    pre-up iwpriv wlan0 set NetworkType=Infra

OR

auto wlan0
iface wlan0 inet static
address STATIC_IP_ADDRESS
netmask 255.255.255.0
network ROUTER_IP
gateway ROUTER_IP
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 essid YOUR_ESSID
        pre-up iwconfig wlan0 mode Managed

here's the link to the guide: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
I hope this helps otherwise I am not sure how wicd works. have you gogled it?

---

### Post by imdano on 2007-08-16
Wicd doesn't change your interfaces file.  It stores the network info in it's own .conf file, and when it detects a network set to autoconnect in range, it uses the stored settings to connect to it.

---

### Post by kevdog on 2007-08-16
All valid points above, but I was interpreting you question a little different.  To make wicd start on startup, go to System->Preferences->Sessions

Create a new session called WICD.  The command should be /opt/wicd/tray.py  
This will give you the gui.

The actual WICD daemon should run at startup.  The startup file is located at /etc/init.d/wicd
This actually just calls the binary to execute = /opt/wicd/daemon.py

Thats it!

---

### Post by redmonster13 on 2007-08-16
I guess I should have been a bit more specific, WICD starts up but it does not automatically connect. I have the box checked but it just isnt happening.

I am simply right clicking the try icon and selecting connect to get it to connect to the network and then everything is all good.

I was just hooping to be able to hit the on button, login and walk away. It isnt really that big a deal, just a bit annoying after the time spent setting the drivers up for the POS wireless card.

---

### Post by imdano on 2007-08-16
What version are you using?

---

### Post by redmonster13 on 2007-08-17
1.3.1 

and my ubuntu is fiesty

---

### Post by imdano on 2007-08-17
Upgrade to 1.3.3 and see if it works any better.  If not there's a newer version on our SVN repository you can try as well.

---

