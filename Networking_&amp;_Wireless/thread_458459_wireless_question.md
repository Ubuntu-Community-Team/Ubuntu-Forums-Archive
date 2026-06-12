---
title: "wireless question"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by joereith on 2007-05-29
i just installed xubuntu on laptop and wondering if i can just go to my friends house and click firefox and be able to use the internet. my friend has wireless router in his house probably without wep encryption enabled.the laptop has a netgear wireless card in it

---

### Post by SamsLembas on 2007-05-29
As long as your wireless card is being recognized (If you can connect to your home network, the answer is yes), you should be fine.

---

### Post by joereith on 2007-05-29
what do u mean home network? I don't have wireless at my house just dsl

---

### Post by ugm6hr on 2007-05-29
If you have Xubuntu - I would recommend you use Network Manager if you are going to "roam" with wireless - otherwise it will not be as simple as clicking go.

Try this:
[http://ubuntuforums.org/showthread.php?t=448952](http://ubuntuforums.org/showthread.php?t=448952)

This assumes that your wireless card works "out-of-the-box" with Ubuntu (i.e. has Ubuntu drivers that work).  If not, then it may require more work.

Try typing "lspci" in Terminal - and look for your "Network Controller".  Then search these forums (or paste here) to see what is required to get it to work with Feisty (assuming you have Feisty).

---

### Post by kilroy423 on 2007-05-29
See if your wireless card is recognized by using ```
ifconfig
```if it is then you can use ```
iwconfig 
``` to list info about just your wireless card...from there you would need to know the BSSID of your friends nework and what encryption he uses or lack thereof...then you can enter the information in the system adminstration>networking panel or use the command line ```
iwconfig [your wireless card ex:eth1] essid my neighbors network name ap your neighbors wifi router mac address
``` to scan for all available wireless networks you can use the ```
iwlist scan[your card ex:eth1]
``` this will print out the stats for all wifi netorks in range of your card....if you have anymore questions RTFM at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wireless%29](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wireless%29)


dan

---

