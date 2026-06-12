---
title: "[SOLVED] Corega WLUSB Stick-11 V2 for Gutsy with WEP"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by Jose Catre-Vandis on 2008-04-18
Corega WLUSB Stick-11 V2  (wireless USB stick interface)
Ubuntu 7.10 Gutsy

OK, this is for the V2 model, which has an atmel chipset.
I am on Gutsy, can't test on any other Ubuntu I am afraid.
```
lsusb
``` gives back this device info ```
Bus 002 Device 004: ID 07aa:7613 Corega K.K. Stick-11 V2 802.11b Adapter
```
It works out of the box - kind of. Anyway the most important thing is to get your wlan interface right.
Before starting, ensure wireless is enabled on your router, that your router is serving up IP addresses via DHCP, and that you have all security turned off. I also have Network Manager turned off in Start > System > Preferences > Sessions > Startup  

1. Insert your stick
2. Open a terminal
3. Type ```
sudo lshw -C network
``` and enter password
4. Towards the end of the listing you should see something like this:

##############################################################
*-network
description: Wireless interface
physical id: 1
logical name: wlan1
serial: XX:XX:XX:XX:XX:XX
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=1.101.0-86 ip=10.10.10.18 wireless=IEEE 802.11b
##############################################################

Although yours might at this stage say something about the network being disabled.

5. Make a note of the logical name, in my case here; wlan1
6. You also need your essid from your router. If you haven't got one, set one up.
7. Back to your terminal
8. Type ```
sudo gedit /etc/network/interfaces
```
9. This will open up gedit with your interfaces file
10.Add the following information to the bottom of the file:

########################
#the wireless interface
auto wlan1
iface wlan1 inet dhcp
wireless-essid youressid
wireless_mode managed # (might not be needed now)
########################

Note I have use my logical name (so use yours) and replace "youressid" with your essid

11. Save the file
12. Reboot

Is it working? ( see if you can get google in firefox or something similar )

If not:

13. Start > System > Administration > Network
14. You should have a Wireless entry. Click on it, and then select properties
15. Tick the activate/enable box top left
16. Enter your Essid and select DHCP and click OK
17. Tick the box for the Wireless interface
18. Things should start happening and a dialog will show the interface being activated
19. You should now be connected.
20. Reboot to ensure it all works OK on start up.


Try to leave the stick in situ, as it seems to do funny things if you take it out and reinsert.

Your other useful command is:

```
sudo etc/init.d/networking restart
```

which reloads your interfaces file.

#################################################################################

OK that is the basic setup, now we need to add some security. The corega stick-11 only offers WEP, but if your router does MAC address control we can improve things by using both. Routers do this in different ways, and do not affect the settings on your PC, so just access your router interface, find the settings page and lock your router down to approved MAC addresses only, and of course add the MAC address of your Corega Stick to the approved list. Now for WEP.

Whilst still in your router interface, go to the security settings part of wireless configuration

On my router I selected WEP, Open System, 128 bit

```
passphrase example     =  bananas

generated key example  =  0C10A2DF969AA5066D96E0360F
```

Don't use these, use your own passphrase, the stronger the better. Write these down somewhere!

Click apply and leave your router interface.

Open up a terminal and type as follows:
```
sudo gedit /etc/network/interfaces
```
add this line to the bottom of your wireless config section
```
wireless-key 0C10A2DF969AA5066D96E0360F
```

so it all looks like this now:

#######################################
#the wireless interface
auto wlan1
iface wlan1 inet dhcp
wireless-essid youressid
wireless_mode managed
wireless-key 0C10A2DF969AA5066D96E0360F
#######################################

Save the file

Note: if you have entries for wlan0 and wlan1,(I do) add the wireless-key line to both

Try restarting the network with
```
sudo etc/init.d/networking restart
```

If that doesn't bring the network back up, you may need to reboot

Check your settings at the terminal with ```
iwconfig
```

You can check your security is on by typing ```
sudo iwlist scan
```
This is fun, because if you are in a heavily populated area, you will see all the other wireless networks about!
You will find your setup , probably by looking for your ESSID and you should see a line Encryption key : on 

So now you have a working wireless connection, secured with MAC address and WEP. Enjoy :)

---

