---
title: "external Hotspot will piggy back until bucked off"
date: 2017-06-17
forum: Networking &amp; Wireless
---

### Post by rocky3 on 2017-06-17
hi

I am trying to connect to an external Hotspot (android tablet) called turtle connector.  I am trying to connect from 16.04 LTS ubuntu.  

My windows 7 computer connects to this turtle connector Hotspot no problem from anywhere, as it should be.  

The only way I can connect is if tethered to some WIFI, which defeats the purpose of Hotspot.  For example. if I connect through my home WIFI called "Eldridge" shown at line 267 below, I can disconnect from Eldridge WiFI and connect instead to "turtle connector" Hotspot just fine (line 266 below).  I can move out of the WIFI range and continue to serf the internet  using the Turtle connector hotspot.  

However, as soon as I reboot Ubuntu, I loose my turtle connector hotspot connection and cannot restore it regardless of where I move. 

[https://pastebin.ubuntu.com/24880348/](https://pastebin.ubuntu.com/24880348/)

The two lines below are extracted from my WIFI info report at the pastbin link above:
SSID                     BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
266 Turtle connector         <MAC 'Turtle connector' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA2       yes     * 
267 Eldridge                 <MAC 'Eldridge' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA1       no    

Anything you can do to assist would be greatly appreciated!!

Rocky3:mad:

---

### Post by Hadaka on 2017-06-17
Hi, from the wireless-info report...

CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   | MREF5
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   | turtle connector            <<-
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   | Kathleen Carr's Network
CONNECTIONS.AVAILABLE-CONNECTIONS[4]:   | Wi-Fi connection 1
CONNECTIONS.AVAILABLE-CONNECTIONS[5]:   | suite-x
CONNECTIONS.AVAILABLE-CONNECTIONS[6]:   | Turtle connector 2          <<-
CONNECTIONS.AVAILABLE-CONNECTIONS[7]:   | Turtle connector 1          <<-
CONNECTIONS.AVAILABLE-CONNECTIONS[8]:   | Eldridge
CONNECTIONS.AVAILABLE-CONNECTIONS[9]:   | Turtle connector            <<-
CONNECTIONS.AVAILABLE-CONNECTIONS[10]:  | FiOS-4LLPL_Ext
CONNECTIONS.AVAILABLE-CONNECTIONS[11]:  | Hotspot
CONNECTIONS.AVAILABLE-CONNECTIONS[12]:  | Turtle connector            <<-

Turtle connector <MAC 'Turtle connector' [AC1]> Infra 1 2412 MHz 54 Mbit/s 75 &#9602;&#9604;&#9606;_ WPA2 yes * 
Eldridge <MAC 'Eldridge' [AC6]> Infra 11 2462 MHz 54 Mbit/s 74 &#9602;&#9604;&#9606;_ WPA1 no 

The wireless report indicates several "Turtle" ENTRIES.   edit connections...delete them all
add back in ONE ssid Turtle_connector no spaces in the ssid name. Then UNCHECK "connect automatically"
in the ipV4 SETTINGS BOX. Uncheck also Eldrige.

Also noted is WPA1 for Eldrige..this needs to be WPA2  

Make these changes and test.

Thanks.

---

### Post by rocky3 on 2017-06-24
My HOTSPOT worked great all!  Thanks Hadaka!!!

How I solved my hotspot network connectivity problem:

- I went into settings and under the 1st tab on the left "general"  I unchecked the box that called for auto ID
- Under the WIFI on the  SSID tab, I changed turtle connector to one word "hillbilly"  and I selected "client" NOT "hotspot" .  . that was tricky . . .. I made the same adjustment on my android tablet which was serving as a hotspot.  MODE = client and MTU =auto
- Under security  -  WPA and WPA 2  personal
- Under IPV4  I selected AUTO (DCHP)
- for my WIFI network, I set it up the same way.  

Rocky3

---

### Post by Hadaka on 2017-06-24
Glad you were able to resolve the problem !
Thank you for marking your thread Solved.

---

### Post by rocky3 on 2017-06-24
Thanks to you!!

---

