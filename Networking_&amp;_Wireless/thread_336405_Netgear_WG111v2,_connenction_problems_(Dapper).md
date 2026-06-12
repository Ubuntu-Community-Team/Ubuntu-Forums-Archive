---
title: "Netgear WG111v2, connenction problems (Dapper)"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by pbodin on 2007-01-11
Hi!
This is my first post here (only been using ubuntu for a week). I have some problems connection to my router using the usb-adapeter Netgear WG111v2. I have (to no avail) followed the recommendations available here: [http://www.ubuntuforums.org/showthread.php?t=212365&highlight=dapper+netgear+wg111v2](http://www.ubuntuforums.org/showthread.php?t=212365&highlight=dapper+netgear+wg111v2)

Some information that I thought might be relevant:

WPA or WEP is not activated on the router.
The installed version of ndiswrapper is 1.8-0ubuntu2 (dapper).

```

[FONT="Courier New"]peter@pb-ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
net111v2                
driver present, hardware present[/FONT]

``` 

Ok that seems to work, also if I scan for the available networks I find ~10 different networks including my own ("pb").

This is my configuration:
```

[FONT="Courier New"]peter@pb-ubuntu:~$ iwconfig wlan0
wlan0     802.11b/g linked  ESSID:"pb"
Mode:Managed  Channel=11  Access Point:  00:14:6C:23:01:FC
Bit Rate=54 Mb/s   Sensitivity=4/6
Retry:on   Fragment thr:off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/FONT]

```

This is my blacklist:
```

[FONT="Courier New"]peter@pb-ubuntu:~$ tail -3  /etc/modprobe.d/blacklist
# wlan WG111v2
blacklist rtl818x
blacklist r818x[/FONT]

```

Oh, and the little blue light on the adapter is not blinking.

Anyone have an idea on what might be wrong in my configuration? 

Best regards

pb

---

### Post by teaker1s on 2007-01-15
install 

[COLOR="Red"]network-manager-gnome[/COLOR]

make sure panel click [COLOR="Blue"]system administration networking [/COLOR]
interfaces are unconfigured
remove ethernet cable
reboot 
and you will find network-manager-gnome applet by volume control
left click on it and select network
if it still won't work
[COLOR="Red"]iwconfig[/COLOR] in terminal and post results

---

### Post by pbodin on 2007-01-15
Thanks for helping. 
I upgraded to edgy yesterday so I don't need the ndiswrapper anymore. Anyway, doing what you told me to really helped, I now have the wlan up and running. However, there is one thing that bothers me a bit. My connection is recognized as a cable connection, this means that I can't configure my WEP-settings (at least not using the GUI). This is the output from iwconfig:
```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g linked  ESSID:"pb"  
          Mode:Managed  Channel=11  Access Point: my access point MAC   
          Bit Rate=54 Mb/s   Sensitivity=4/6  
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

Any idea why it isn't recognized as wireless in sysadm networking?

/pbodin

---

### Post by Jose Catre-Vandis on 2007-01-15
well your iwconfig is definitely seeing your adapter as a wireless one - wlan0 (WirelessLan0)

You need to add the WEP seetings in your /etc/network/interfaces file

Plenty of threads on forum about how

---

### Post by pbodin on 2007-01-15
Hi!

It's up and running. It's a pleasure using ubuntuforums to solve ones problems.
Thank you all.

/pbodin

---

### Post by teaker1s on 2007-01-15
It's a pleasure, that's the  spirit of ubuntu :mrgreen:

---

