---
title: "Cant conect to WIFI's that are using special characters in its name (ÆØÅ)"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by Sn3ipen on 2008-04-21
I am having some Issues with connecting to the Wifi network at my job and i think it is because the network is named with an "Ø" in its name. This is a common character in Norway. The problem is that i cant change the name on the router cause i am not the one responsible for the network at my job. This network works great in Windows though. I don't want to use Windows!

When i am clicking on the Network Manager Icon the network i want to connect to isn't there.

I tried using the Terminal to search for networks and try to figure it out. Then this network is on the list but the "ø" is now changed to an "?" so i am no sure what to type as essid. I tried alots of different variants of the name names but nothing worked.

Is there any workarounds for this?

---

### Post by thevoidreturns on 2008-04-21
Dont know if this will work, but have a look at the following tutorial I found. Basically, try and put a "\" infront of the special character first and see if that works.

[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

Hope this helps
Adam

---

### Post by Sn3ipen on 2008-04-22
Thanks for trying to help me. That tutorial said you should have an "/" in front of the special characters in your pasword. I tried to do the same thing in the essid(name of network) but it didnt work. :(

---

### Post by chili555 on 2008-04-22
You might also try putting the name in quotes:```
sudo iwconfig essid "ÆØÅ"  
```Please let us know for the benefit of future searchers.

---

### Post by Sn3ipen on 2008-04-22
I already tried that ofcorse.

I also tried it in PcLinuxOS on a Live cd i had laying around and then the Ø wasn't in the name so i could connect fine. But i want to use my Ubuntu installation.

---

### Post by chili555 on 2008-04-22
You could also try disabling ESSID checking with:```
sudo iwconfig eth1 essid any
```Or whatever your wireless interface is, if it's not eth1. If that is a security issue, you can specify the MAC address you want with:```
sudo iwconfig eth1 ap 99:0C:41:19:58:79
```You can verify the MAC address with:```
sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 99:0C:41:19:58:79
                    ESSID:"mylittlerouter"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
etc., etc.
```Let us know.

---

