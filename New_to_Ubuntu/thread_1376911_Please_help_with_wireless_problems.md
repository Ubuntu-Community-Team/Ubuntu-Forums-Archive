---
title: "Please help with wireless problems"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by ARCI-Phase 4 on 2010-01-09
Please help! Im putting Ubuntu on a desktop that will need wireless access to the net. Im using AT&T DSL with a 2Wire 2701HG-B gateway broadcasting to a Linksys WUSB600N usb wireless connected to a Dell Inspiron 531 pc. Im connected by ethernet cable to that gateway right now, and the wireless works fine on all other windows pc's. I thought Ubuntu would detect the need for non-free proprietary drivers to get the wireless running (it did for my laptop,) but Ive recieved no notices of such this time. My wireless network is detected, but when I try connecting I just keep being asked for the security key over and over. Any help would be greatly appreciated, thanks!

---

### Post by marco123 on 2010-01-09
Sometimes changing the channel on the router helps.  I had a similar problem with Intrepid (8.10) on an old laptop, I changed the router to channel 1 and it worked perfectly.

You could also try resetting the network by turning everything off then back on again.

---

### Post by Old_Grey_Wolf on 2010-01-09
Try this. I hope it helps.

Using the Driver CD that came with the WUSB600N device.

Make sure that you have the "Windows Wireless Drivers" application installed on your system.

If not, you can install via menu bar...
Click Applications - Add/Remove (9.04) or Software Center (9.10).
On the search bar, type "Windows Wireless" (without the quotes).
Select it then "Apply Changes"

- With that one sorted out...
Go to System - Administration - Windows Wireless Drivers.
Enter your root password.
Click "Install New Driver"
Browse for the .inf file on the Driver CD that came with your device.
Click "Install" then "Close"

- You should now be able to see a wireless device on the network icon at the right side of your Applications Menu.

- Configure your wireless device and that's it!!!

NOTE: If by chance the wireless is not listed on your networks, try restarting your machine.

---

### Post by bkratz on 2010-01-09
I think it may be a little more difficult
See this thread for other doing the same thing

[http://ubuntuforums.org/showthread.php?t=972060&highlight=WUSB600N](http://ubuntuforums.org/showthread.php?t=972060&highlight=WUSB600N)

Start at the end (it is a long thread)

---

### Post by ARCI-Phase 4 on 2010-01-09
Thanks, a soft reset and a power off reset didnt help. As for the channel, Im not sure how to affect it. The network shows up under the wireless, its just not able to connect. Seems to be related to the key, but Im not sure. It wont even connect to any of the many unsecured networks that its detecting. I dont know much about Linux, Im in day one of windows rehab.

---

### Post by ARCI-Phase 4 on 2010-01-09
Thanks all. Gray Wolf, I tried what you suggested but it was a no go. Based on the link in your post bkratz I tried switching to Linksys WUSB100 V.2, but that think didnt even detect any wireless networks. I would try to do what that link says, but its kinda over my head as a newbie, Im not sure what theyre talking about. Thanks anyways though. Ill keep trying.

---

### Post by anewguy on 2010-01-09
Are you using any kind of encryption on the wireless?  I had AT&T DSL for a while a few years ago, using a 2Wire modem/wireless router. The 2Wire modem/router had problems with certain types of WPA encryption and Linux (yes, WPA supplicant was running and I set everything up correctly).  Basically, I had to forget WPA and just use WEP and MAC filtering to get it to work.

Also, do you by any chance have MAC address filtering on the router?  If so, you will need to include the MAC address of the new PC adapter in the router allowed MAC address list or you will not be able to connect.


When you try to connect, does it look like it tries to connect for a while and then times out?  This could be a difference in the encryption type, pass phrase versus passkey, etc..

Dave :)

EDIT:  Just thought of one more thing - is it asking for the network password or is it asking for the keyring password?

---

### Post by ARCI-Phase 4 on 2010-01-09
I am using WEP, I dont know anything about MAC. Yes, it does appear to try connecting for awhile and then times out and asks for the WEP key again. It isnt asking for keyring anymore, I thuink it did once in the beginning. However, it appears worse now,niether device is detecting any wireless networks at all now. This is a fresh Ubuntu 9.10 install so I may re-install to undo whatever caused that newest development (happened after trying to load inf files from CD)

---

### Post by ARCI-Phase 4 on 2010-01-09
Okay, I re-installed ubuntu and can now see wireless networks again. Ive entered my WEP key and MAC address into the wireless network editing page. Still same problem--I initiate a connection, enter inthe key when asked, it cycles for a few minutes then asks for key again, continuously. If I cancel the key entry, I get the black notification box that Im disconnected.

---

### Post by bkratz on 2010-01-09
> **ARCI-Phase 4 said:**
> Okay, I re-installed ubuntu and can now see wireless networks again. Ive entered my WEP key and MAC address into the wireless network editing page. Still same problem--I initiate a connection, enter inthe key when asked, it cycles for a few minutes then asks for key again, continuously. If I cancel the key entry, I get the black notification box that Im disconnected.

Now that you can see networks again, it might be nice to remove encryption from the router and just make sure that you can even connect or try WPA instead of wep. I was able to setup WPA2 and never did get wep to work. (Actually I gave up when I got WPA2 working since it is much more secure)

---

### Post by ARCI-Phase 4 on 2010-01-09
Okay, I tried WPA2-PSK and unsecured, neither actually connect. Also, the router wont accept changes from WEP-Open for some reason, so I couldnt actually implement the WPA2. It did take the unsecured, but it was still a no go. I also set it channel 1 as suggested earlier. No complaints though, at least Im learning new things as I sort through this.

---

### Post by bkratz on 2010-01-10
> **ARCI-Phase 4 said:**
> Okay, I tried WPA2-PSK and unsecured, neither actually connect. Also, the router wont accept changes from WEP-Open for some reason, so I couldnt actually implement the WPA2. It did take the unsecured, but it was still a no go. I also set it channel 1 as suggested earlier. No complaints though, at least Im learning new things as I sort through this.

If you can't even connect when no security is used; something more major is wrong. When you added your MAC address-was it to the router:  where did you obtain the mac address? Perhaps it is time to get even a little more learning accomplished!! The terminal.

If you go to Applications>>Accessories>>Terminal a small window will open--type in 

sudo iwlist scan 
(that is IWLIST in lowercase)
It will ask you for the password. Put it in even though it does not echo to the screen and press enter.  Copy/paste the output here. It should show all the networks you can "see" and the type of encryption.

Also type in
sudo lshw -C network
(LSHW in lowercase, C in upper case!)
And copy paste the output here
This will give all your network information

With these hopefully we can see where to go next.

(close the window)

---

### Post by ARCI-Phase 4 on 2010-01-10
Well, I remembered I had an old netgear pci nic laying around so I put that in and it connects right away. As for the MAC address I took that from the one listed under the wired connection properties. Ive since removed that as the nic doesnt seem to need it populated anyway. Iv included the scan reults you requested, but it is with the pci card, not thwe usb device. What was the scan for? Anyway, thank you so much for all your help. I guess the nic doesnt solve the problem with the usb, but it solves the problem with wireless access.


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:26:50:4E:7E:69
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"2WIRE744"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000086243c181
                    Extra: Last beacon: 800ms ago
                    IE: Unknown: 00083257495245373434
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C

 *-network               
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: wmaster0
       version: 01
       serial: 00:1e:2a:40:91:c5
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.69 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fdef0000-fdefffff

---

