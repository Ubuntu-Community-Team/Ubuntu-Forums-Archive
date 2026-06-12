---
title: "How to setup wireless in ubuntu?"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by nbitting on 2007-02-01
I just installed ubuntu and completely got rid of WINDOWS!!!!  I am very very new to linux and am trying to configure the wireless on my laptop which has integrated wireless.  What do I need to do to set up my wireless connection to surf the net?  Any help would be greatly appreciated.

---

### Post by Floppyjoe on 2007-02-01
We need to know your wireless card to begin with then proceed from there.
What is the output of the following when entered into a terminal?
Click on Applications/Accessories/Terminal and enter the following:
```
lspci
```

Welcome and good luck!

---

### Post by nbitting on 2007-02-01
I'm using integrated wireless and it says Atheros Communications, Inc. AR5212 802.11abg NIC

---

### Post by Floppyjoe on 2007-02-01
Good now could you post the output of:
```
iwconfig
```
If your wireless card is recognized it will show here although the driver may need to be changed.

---

### Post by nbitting on 2007-02-01
Okay, Now it is picking up my wireless signal under ath0... what now?  It does have a WPA encryption... FYI

---

### Post by Floppyjoe on 2007-02-01
> **nbitting said:**
> Okay, Now it is picking up my wireless signal under ath0... what now?  It does have a WPA encryption... FYI
Okay do you have WPA Supplicant installed? You will need that for Wpa encryption to work. Also for wireless to work you need to disable your ethernet network adapters in system/administration/networking. If you plan to do roaming with your laptop i would also install Network-manager and network-manager-gnome. hopefully that will work with your wireless adapter.

---

### Post by nbitting on 2007-02-01
Should I just hook it up directly to my router and download those applications???

---

### Post by Floppyjoe on 2007-02-01
You could do that or use your install CD by clicking on System/Administration/Synaptic Package Manager. Then click on Edit/Add CD-ROM then click on reload then search for the required apps.

---

### Post by nbitting on 2007-02-01
I now installed the two things you told me to... Network-manager and network-manager-gnome... Now what?

---

### Post by Floppyjoe on 2007-02-01
If your router is using WPA encryption you will need to install WPA Supplicant as well to be able to connect with it.

---

### Post by nbitting on 2007-02-02
I'm not sure how to install WPA Supplicant... any chance you could give me some help?

---

### Post by Floppyjoe on 2007-02-02
System/Administration/Synaptic Package Manager

Search for wpasupplicant

Edit: You will not see this program in your applications menu. It is run from the terminal
Then to use network manager you need to disable all your network interfaces in System /Admininstration/Networking and then reboot your computer.

---

### Post by icalderus on 2007-02-19
I am in the same boat as the original posted. Just wiped out my windows install and put ubuntu in. 

Have no probs bringing up and using eth0 with is my ethernet connection. 

However using my wireless card isnt as easy. Currenty I read up on the previous posts and made sure network manager is installed, check that , done. I also made sure that wpa supplicant is installed that is done.

However the funny thing is I cant even access the damn network manager application. Looking on the internet seems ,like people are saying to 'click on icon named Network Manager'..however my desktop icons are bare , this is a new install. And there is no Network manager application. 

How do I access this Network Manager application?

TX

---

