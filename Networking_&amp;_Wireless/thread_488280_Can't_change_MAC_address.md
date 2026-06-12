---
title: "Can't change MAC address"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by flyingkiwi on 2007-06-30
Using Feisty 7.04

I have tried two ways of changing the MAC address.  

The first was to modify /etc/network/interfaces to include the line **hw address ether 12:34:12:34:12:34** after restarting the networking the eth0 wasn't working at all anymore, it said something about being manually configured...

The second was to run the following from a terminal as sudo

[B]ifconfig eth0 down hw ether 12:34:12:34:12:34
ifconfig eth0 up[/B]

this seemed to work, using ifconfig showed the new MAC address, however the network manager icon in the ?system tray? still showed the old MAC address under connection info.

The reason I am trying to do this is to allow me to use a friends internet connection that seems to be tied to MAC address.  I am able to change the MAC address under windows and use the connection through windows...so I know it can be fooled!  However I don't seem to be able to fool it from Ubuntu.

Any ideas would be much appreciated!

Jon

---

### Post by arvevans on 2007-06-30
The MAC address is a hard coded unique manufacturer's number that is placed in the Ethernet hardware at manufacture time.  If is used for among other things, to determine which hardware drivers are needed for a particular set of hardware (the MAC address is unique, and each manufacturer "owns" their own block of assignable MAC addresses).  Routers use the hardware MAC address from your Ethernet hardware to route traffic to your particular computer and DHCP servers us it to assign your IP address.

Now, having said all that...you can possibly change the MAC address of your computer hardware, but it is not recommended.  You have to set the new MAC address, then stop and restart the inet demon (stop and start network interface handling) in order to fool the router into establishing a route to your new fake MAC address.
_._

---

### Post by kevdog on 2007-06-30
Ive heard this may work, but Ive never tried it.

Edit the /etc/iftab file and change the MAC address there that is listed with your interface name

May iftab file is the following:
wlan0 mac 00:12:17:35:17:10 arp 1


First backup this file or add a comment to the above line (just to make sure you can revert to the old settings if necessary), and then just change the MAC address to whatever you want

---

### Post by flyingkiwi on 2007-07-01
> **arvevans@earthlink.net said:**
> Now, having said all that...you can possibly change the MAC address of your computer hardware, but it is not recommended.  You have to set the new MAC address, then stop and restart the inet demon (stop and start network interface handling) in order to fool the router into establishing a route to your new fake MAC address.
_._

Isn't this what I have already described doing?  It didn't work.

---

### Post by flyingkiwi on 2007-07-01
> **kevdog said:**
> Ive heard this may work, but Ive never tried it.

Edit the /etc/iftab file and change the MAC address there that is listed with your interface name

May iftab file is the following:
wlan0 mac 00:12:17:35:17:10 arp 1


First backup this file or add a comment to the above line (just to make sure you can revert to the old settings if necessary), and then just change the MAC address to whatever you want

I don't have an /etc/iftab file, should I create one?

---

### Post by kevdog on 2007-07-01
Mine was produced automatically, but sure try it.  If anything goes wrong just delete the file.  Use root priv. to create file.  

Yours will read something like:
eth0 mac 00:12:17:35:17:10 arp 1

If would first try with the known MAC address just to make sure everything works.  After creating file, reboot.
If everything is peachy, then change the MAC address to whatever you want, save and reboot.

Good luck!

---

### Post by atonaldenim on 2007-09-18
I'm not sure if the above method works when using NetworkManager.

Another method I have verified on my wireless card using NetworkManager on Feisty Fawn is the simple program [GNU Mac Changer]("http://www.alobbs.com/macchanger/"). It was already installed on my system, but if not...
```
sudo apt-get install macchanger
```
To change the MAC address for an interface, you must leave Networking Enabled in NetworkManager, while disabling only the particular interface you wish to change. For my wireless card, I right-clicked the NM Applet, and unchecked Enable Wireless, while leaving Enable Networking checked.

Then the command is simply:
```
sudo macchanger eth1
```
which iterates the last bit of your real MAC. (of course you must change "eth1" in the above example to refer to your network interface.) The command accepts many other options as well, see **man macchanger**.

Finally, re-enable the interface in Network Manager, and your new MAC address should be listed in Connection Information.

(thanks to James Crocker's article [Anonymizing Network MAC Addresses]("https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses"))

---

