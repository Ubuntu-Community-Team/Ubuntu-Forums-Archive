---
title: "NetworkManager crashes/freezes when try to connect to wireless network"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by trab_irl on 2007-02-18
hi all...

first... i am brand new to ubuntu and this is my first post here after days of searching the web and forums for an solution...
i try to setup ubuntu on my notebook HP Pavilion dv6190 with a AMD Turion 64 X2, 2 GB ram,  bcm4311, working wireless router, working network connection...

i installed all the right drivers(latest) as written in many manuals and the adapter is wirking fine, i can pick up all the wireless networks in my area and i can connect to the internet via network cable...  as seen in the pic [CLICK]("http://img19.imageshack.us/my.php?image=screenshotgi6.png")

i got the latest Networkmanager working and see alle the aviable networks in it...

BUT : ... every time i try to connect to one of the networks, the whole system freezes / crashes..   on a network that has WEP it freezes after entering the key and on a open network it freezes after 2-3 sec..  i can see the little indicator on the top right is trying to do something... but after 2-3 sec everything freezes...

i realy like to get this to work.... i am realy amazed about ubuntu...

Thanks for any help..

TRAB

---

### Post by teaker1s on 2007-02-18
I've had some router issues, there is also mention of altering speed boost in the link in my signature

---

### Post by trab_irl on 2007-02-18
... my router is working fine aswell as the one next house(the one thats not secured;) 
i can connect fine with the networkcable to the router and my mac and other laptop works fine on wireless on both networks...

and i was not able to find a thing about "speedboost"...

thx

edit: i might should add, i just installed "wifi Radar" and it froze whet it was "Acquiring IP Address" ....

---

### Post by teaker1s on 2007-02-18
*

user@ubuntu:~/bcm4311$ sudo gedit /etc/ndiswrapper/bcmwl5/.conf

> Change the .conf file and change the ninth line from "Afterburner|1" to "Afterburner|0"

NdisVersion|0x50001
Environment|1
class_guid|4d36e972-e325-11ce-bfc1-08002be10318
NetworkAddress|XX:XX:XX:XX:XX:XX
driver_version|Broadcom,03/23/2006, 4.40.19.0
BusType|5

11HNetworks|1
Afterburner|0

This turns off a Broadcom extention to the 802.11x standards that improves throughput when you are using all Broadcom devices. It also will not let this device work with my Linksys Access Point unless it is turned off. Perhaps this would not be necessary with some Broadcom Access Points? 

---

### Post by trab_irl on 2007-02-18
i did that of course as it is part of most manuals...

any other ideas welcome ...

---

### Post by VorDesigns on 2007-02-18
Consider skirting the Ubuntu Networking GUI which never worked for my wireless card and
work with /etc/network/interfaces file.
Post your interfaces.
What are you using to interrogate the Wireless NIC?
-
When I went to manual manipulation, this is what I did.
[DWL-G650 Wifi]("http://www.ubuntuforums.org/showthread.php?p=2060387&highlight=DWL-G650#post2060387")

---

### Post by trab_irl on 2007-02-19
first of all \\:D/ =D>  i am up and running...

How did i fixe it:

1. installed a fresh copie of ubuntu (amd64 vers. as i got one)
1.1 I DID NOT UPDATE THE LINUX KERNEL!
2. i installed my wireless driver as written [HERE]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29")
    (i used the 1.28 driver(same as in manual) and i did not install the networkmanager and WPA)
3.  i testet it with configuring it to my preffered wifi spot  (WORKED :biggrin: )
4. to search and connect for networks i installed and use Wifi Radar


info: it seams that the latest update killed the wireless, ... so if you got a similar problem, DONT UPDATE or if than USE The OLDER KERNEL IN THE BOOT MENU

THX
TRAB

---

