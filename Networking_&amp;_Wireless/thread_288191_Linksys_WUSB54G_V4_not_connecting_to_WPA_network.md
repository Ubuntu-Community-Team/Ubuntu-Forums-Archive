---
title: "Linksys WUSB54G V4 not connecting to WPA network"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by Yourname on 2006-10-29
Hello,

My Linksys WUSB54G v4 seems to be recognized, and it shows up as rausb0 in System-Admin-Networking. 

I try to configure it, and try connecting to my WPA2 network.. and it shows the dialogue that I need to enter the key, but the "Security" tab shows only WEP and two other WEP variations in the dropdown, no WPA.

What do I do to make Network Manager let me connect to a WPA network, and show me the WPA key options as well?

I'm using a Gateway 5300 Solo laptop with Edgy Eft.
I also have wpa_supplicant installed.

Summary: Just need to be able to connect to WPA network.

---

### Post by wieman01 on 2006-10-30
The standard "networking tool" that comes with Gnome cannot handle WPA, only WEP. You need to install a tool called "gnome-network-manager" which is the GUI for another package called "network-manager". 

The tool is fairly reliable but has a number of drawbacks:

1. No support for hidden ESSID.
2. No static IP leases, only DHCP.

The other option is configuring WPA manually using the "interfaces" file, however, I never got it working with the native Linux driver "RT2570" which you are using at the moment ("rausb0"). So if you want to take manual approach I recommend you to use "ndiswrapper" in connection with the latest "Windows" driver for your USB device. WPA2 is definitely no problem there:

Reference: [http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn")

If you need help with "ndiswrapper" and WUSB54G, drop me a line. The "RT2570" driver has been a frustrating experience if you ask me.

---

### Post by Yourname on 2006-10-31
> **wieman01 said:**
> The standard "networking tool" that comes with Gnome cannot handle WPA, only WEP. You need to install a tool called "gnome-network-manager" which is the GUI for another package called "network-manager". 

The tool is fairly reliable but has a number of drawbacks:

1. No support for hidden ESSID.
2. No static IP leases, only DHCP.

The other option is configuring WPA manually using the "interfaces" file, however, I never got it working with the native Linux driver "RT2570" which you are using at the moment ("rausb0"). So if you want to take manual approach I recommend you to use "ndiswrapper" in connection with the latest "Windows" driver for your USB device. WPA2 is definitely no problem there:

Reference: [http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn")

If you need help with "ndiswrapper" and WUSB54G, drop me a line. The "RT2570" driver has been a frustrating experience if you ask me.

Thanks for the reply.
I figured the same about RT2570, and got RT2500 using Ndiswrapper.
Also, I had network-manager-gnome.. and not relied on Networking too much.

I will follow the other thread and let you know of the progress.

---

### Post by Yourname on 2006-11-01
Sorry, halloween festivities.
Will do it soon.

---

