---
title: "Connecting to wireless Network  ???"
date: 2014-10-03
forum: Networking &amp; Wireless
---

### Post by mx695 on 2014-10-03
Hello everyone I have just started using Ubuntu 14.04 trusty based off of xbmcbuntu. I have a Netgear wnda3100v2 which i searched the forums and learned how to install the broadcom driver . The adapter shows up in iwconfig also when i run command (sudo iwlist scan) the device scans for wireless networks and I see them , Here is where the problem lies for me Is i dont know how to connect to them I do not have a Network manager on the system and honestly dont know the proper way of installing it if this is what im even looking for , on another note if i go into network connections and type in the ssid login and password nothing happens , Im using the same settings for the connection as my laptop which has lubuntu and connects fine with its built in wifi adapter . If someone has a link to a similar situation as mine that would greatly be appreciated , ive searched and searched and felt its time to post onto the forums . and feedback is great help anything . I know my usb netgear adapter is a pain but i have seen where people get them to work .

An help please thanks everyone.

---

### Post by praseodym on 2014-10-03
Hi,

XBMCubuntu is based on Lubuntu. There was a bug with the network-manager in the first release of that. Check here:

[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

---

### Post by mx695 on 2014-10-03
alright great got that going I can connect to the networks now thank you. so simple i over looked that . (I do have a question is how do i determine the network band the adapter is using . currently its using 2.4ghz how would i access the options for (N) 5ghz .) also in my attempt to try to connect to the networks I was trying to load (wicd network manager ) which I thought never installed and I thought I cleared out anything to do with it .so that being said I believe that's conflicting with the built network manager which is separate I believe because on my laptop running lubuntu it just has the network connection box and the windows that show up in status bar. I think I'm saying all this correctly . I've tried removing Wicd or disabling it without any success . my wireless adapter just won't connect even on unsecured network 90% of the time and the other percent it connects through the oem interface . but no commands work from wicd. Any help would be greatly appreciated . 
I appreciate all the help everyone provides .Ubuntu/linux is all new to me and with these forums and the feedback you guys give have helped me tremendously and I have learned alot.  Thank you

---

### Post by praseodym on 2014-10-04
Check:
```

iwconfig
iwlist chan
sudo iwlist scan
```
You need to change the band in the router interface, check the manual. Start wicd like this:
```

sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```

---

