---
title: "Netgaer wireless instalation"
date: 2013-11-17
forum: Networking &amp; Wireless
---

### Post by car_care_man2 on 2013-11-17
I am new to Ubuntu, and dont know how to set up my USB wireless adapter. When i try to install the driver, i get an error? Can someone help me out? Do i have to connect wired first?

What is

BSSID

Device MAC address

cloned MAC address

MTU

I need help.

---

### Post by varunendra on 2013-11-20
Welcome to the forums !

We need to see your adapter's chip to be able to suggest you a suitable driver. Please open a terminal (Ctrl-Alt-T), run the following command and post back its output here -
```
lsusb
```
While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

Answers to your "what is" questions -

**BSSID :** The MAC address of any Access Point. By defining this value in Network Manager, you can tell NM to 'Only' associate that particular connection with that particular access point, not any others (useful when there are many access points with the same name (SSID), thus confusing NM).

**Device MAC address :** The MAC address of your network card. Is usually picked up automatically by Network Manager.

**cloned MAC address :** A fake or different MAC address that you want your network card to advertise on the network instead of advertising its real one. Not used normally.

**MTU :** Maximum Transmission Unit. The maximum size of data packets that can be sent on the network. Default is 1500, should not be changed manually unless you really need a different value.

[COLOR="#800000"]**_TIP_:**[/COLOR] Just hover and hold the mouse pointer over these fields in Network Manager settings to see a short description of what they mean and do.

---

