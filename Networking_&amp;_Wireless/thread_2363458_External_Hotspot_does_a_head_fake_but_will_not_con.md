---
title: "External Hotspot does a head fake but will not connect me to the internet"
date: 2017-06-10
forum: Networking &amp; Wireless
---

### Post by rocky3 on 2017-06-10
Hi,

I am trying to connect my ubuntu laptop to the internet via an external hotspot (android tablet) called turtle connector.  When I activate my hotspot on my android and check the network ICON on my ubuntu, I find that it says that my hotspot "turtle connector" is connected, but I am unable to reach the internet via firefox or chrome.  The same hotspot work fine when I connect my window 7 laptop. Please see line 239 and 256 of the wifi info link below.  It features my turtle connector hotspot.  

Anything you can do to help would be much appreciated. 

Rocky:confused:



[https://paste.ubuntu.com/24819766/](https://paste.ubuntu.com/24819766/)

---

### Post by jeremy31 on 2017-06-10
Change your IPv4 settings for turtle connector in Network Manager from shared to auto

---

### Post by rocky3 on 2017-06-10
Thanks Jeremy31!!  Thanks for helping  me solve this.   This is how I solved it.

1. I activated my external android hotspot
 2.  I went to my network fan ICON on the top right-hand corner of my LAPTOP
3. I didn't see my hotspot "turtle connector"  so I selected "other networks" and Turtle connector was one of the choices
4. After selecting turtle connector - it asked me to authenticate.with my password
5. After authenticating, I WAS IN!!!!
.  
Now, for the first time!!  If you look at line 273 in my WIFI info pastebin, you will see the following statics on my HOTSPOT 

[https://paste.ubuntu.com/24828533/](https://paste.ubuntu.com/24828533/)
SSID                     BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Turtle connector         <MAC 'Turtle connector' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 

When I reviewed my pastebin before, it register turtle connector, but did not register, SIGNAL speed, security, signal strength, or WPA2

thanks again!!

---

