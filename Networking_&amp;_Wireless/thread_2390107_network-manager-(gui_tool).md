---
title: "network-manager-(gui tool)"
date: 2018-04-25
forum: Networking &amp; Wireless
---

### Post by ken35 on 2018-04-25
CentOS 7 with the Mate desktop has a package called network-manager-applet-1.8.0-3.el7.x86_64 which provides the gui interface to network-manager. Right click on the network icon in the notification area...

Ubuntu Mate 16.04 has a similar package which I believe is called network-manager-gnome. Or, it may be part of the Control Center as it can be accessed there as well.

Here is the question... Using either program I can select a wired connection and "Edit" the properties for that connection. On the Ethernet tab is a drop down list or combo box with the "Device".  Below that on Ubuntu is a text box "Cloned MAC address:"  On CentOS the second line is a drop down list which contains the values Preserve; Permanent; Random; Stable.  Here is my dilemma...

I recently replaced a CentOS 7 server which was serving as my router, gateway, firewall, dhcp, vpn sharing box etc. with a Raspberry Pi 3B+ running Ubuntu Mate 16.04. Works great and only uses a tiny bit of electricity :)

My ISP, on the other hand, does not work so well. Recently the did something to their dhcp server so I can no longer "release" the IP address on my server and get a different one. After spending (wasting) a couple of hours on the phone with their "support" persons... Their dhcp server still refuses to accept a release command.  So... I noticed the Random choice and set the Cloned MAC Address to that value. Then when I released the address and cycled the interface I obtained a different address from the ISP. I do not like the idea of doing this but...

Now that I have the Pi on-line in place of the CentOS server I do not have the Random option. I guess I could make up a MAC address and enter it in the box but that is rather a pain.  I am looking for suggestions.

TIA,

Ken

---

### Post by TheFu on 2018-04-26
MAC is used for DHCP.  ISPs are trying to be nice by providing an effectively static IP based on MAC. It can be very convenient if you want remote access.  There are MAC changing tools available. **macchanger** is one.  I have no idea if it works on any PI.

---

### Post by ken35 on 2018-04-26
Thanks TheFu,

I tried macchanger. It installs and runs. Unfortunately it tells me "insufficient permissions or device busy" when I try to change the MAC on the Internet side NIC. I am running sudo and have disconnected the interface.  I will have to look further into it.

ISP trying to me nice? NO. They will provide a static IP address for a fee. Some years back when I had a Netgear router picking up my IP address (DSL modem in bridging mode) a simple release/renew via the router web interface would do the trick. Then they changed something with their DHCP server (they claimed they didn't of course) and I had to release and reboot the router to make the change take effect. 

When I put a CentOS server in place of the router a simple script ```
#!/bin/bash
sudo dhclient -v -r p1p2
sudo ifdown p1p2
sudo ifup p1p2
``` would do the trick. A month or so back this quit working. Again they changed something in the configuration (but their support folks have no clue).

Ken

---

### Post by TheFu on 2018-04-26
Not all NICs allow changing the MAC. Firmware thing.
BTW, ifupdown is deprecated in 17.10+ for netplan.

Different ISPs have different techniques. I have static IPs, but 15 yrs ago, I had DHCP IPs that were tied to the MAC during the lease period.

It is next to impossible for customers to talk to anyone knowledgeable at an ISP.  I worked at an ISP. Never spoke to customers. That wasn't my role.

---

### Post by ken35 on 2018-04-26
Thanks again TheFu,

It seems that the Pi will not allow the MAC to be changed with macchanger. However, I was able to change it withing the network-manager-gnome utility. I guess I need to keep digging.

"RELEASE" is supposed to break the lease. Need to get after the ISP again :(

ifdown/up was from my CentOS script. I think about 3/4 of all networking commands out there have been depreciated.

Ken

---

### Post by TheFu on 2018-04-27
[https://obrienlabs.net/raspberry-pi-spoof-mac-address/](https://obrienlabs.net/raspberry-pi-spoof-mac-address/) might help.

---

### Post by ken35 on 2018-04-27
Thanks again AND AGAIN TheFu,

You beat me to searching for Pi and spoofing. I have found a couple of other "solutions" involving the /boot/cmdline.txt file. However, I have also been investigating another phenomenon.

As I mentioned earlier - some time back the ISP made a change to their DHCP server which required me to reboot my ancient Netgear router after issuing the RELEASE request to the dhcp server. I decided to try the "new" combination modem/router box which the ISP provided to me. It is such a security disaster I will only use it as a bridging mode modem - but for testing...

I reset the thing to factory default - router mode
It picked up a different IP address from what I had on the Pi - as expected
From the web interface I issued the RELEASE command - no longer had an address - as expected
From the web interface I issued the RENEW command - should ask for an available address - not the one I released - but I got the same address back
From the web interface I again issued the RELEASE command - no longer had an address - as expected
I then rebooted the modem/router box
Presto a new IP address :D
I set the thing back to bridging mode

I obtained an address on my Pi 
I issued "sudo dhclient - r (jibberish name of the interface)"
I no longer had an address on the Internet facing NIC.
I REBOOTED the Pi
I now had a different IP address on the Internet facing NiC.

I suspect that the local device (modem/router or Pi) may be remembering the leased IP address. I will do some investigation into this. Perhaps some sort of local flush is required.

Ken

---

