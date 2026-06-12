---
title: "Setting up Wifi?"
date: 2015-06-13
forum: Networking &amp; Wireless
---

### Post by mlvmhn on 2015-06-13
I have finally installed Ubuntu on my HP 550 laptop. the only problem left now is that the system does not find any Wifi connections at all. Only a cable connection. 

how do i set up Wifi and connect to my wireless router?

---

### Post by grahammechanical on 2015-06-13
Go to System Settings>Software & Updates>Additional Drivers tab and see if you get offered a driver for WiFi.

If the Network Manager is not showing any wireless access points in range it could be that we do not have a WiFi adapter driver installed, or we have not enable WiFi in Network Manager, or as it is a laptop the WiFi adapter is turned off and we need to press a keyboard combination to switch the WiFi adapter back on.

A command we can run

```
rfkill list
```

This is what I see on my machine

> ~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no


I am using an ethernet connection and I have not enabled WiFi. If you see "Hard blocked: yes" then the WiFi adapter is switched off in hardware.

Regards.

---

### Post by UltimateCat on 2015-06-14
Hi:

Another thing you can try is find out what wifi card you have and go online and find the linux driver for your network interface card and install it.
This command will tell you what card you have:

```
lspci | grep -i network 

```

HTH

---

### Post by Bucky Ball on 2015-06-14
*Thread moved to **Networking & Wireless**.*

Do this:

```
sudo lshw -C network
```

Post the output here. That will give us the card, which driver you are currently using, if any, and other details.

---

### Post by mlvmhn on 2015-06-14
I have successfully managed to install WiFi, but now i am facing another problem. 

When i have connected my laptop to my LCD screen using VGA, i can not use the keyboard or mouse. 

Could the problem be that the case to the laptop is nearly closed when i put my laptop under my furniture in the livingroom?

I also want to remove my password for my admin account, but it seems to be impossible. 

How do i remove that?

---

### Post by Bucky Ball on 2015-06-14
Neither question is related to your original support request. Please post new threads for each of your issues, one support question a thread. Use descriptive titles and include all relevant information. This will improve you chances of help as this thread has a title which is in no way related to your new issues. See the third link in my signature for other tips.

Glad you got the wifi sorted. Please mark this thread as solved (see second link in my signature) and share with the community how you got your wifi up to wrap it up. Thanks.

---

