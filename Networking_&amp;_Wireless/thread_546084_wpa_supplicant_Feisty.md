---
title: "wpa_supplicant: Feisty"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by Paris Heng on 2007-09-08
Dear,

I have installed the wpa_supplicant in Ubuntu Feisty. But I only see **WEP** for password setting. But dont have **WPA/WPA2**. Please assist. How to set to use WPA?


Thank.

---

### Post by kevdog on 2007-09-08
Are you trying to use network manager to complete the connection, or doing the connection manually at the command line?

---

### Post by Paris Heng on 2007-09-08
Thanks reply.

I want to perform **both** on Command Line and also the Network Manager (NM). But in NM, i only can see **WEP HEX** and **ASCii**. No WPA to select.Why my WPA missing?

Any How-to?

---

### Post by kevdog on 2007-09-08
Try this with NM.  If it doesnt work we will go to command line version:

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by Paris Heng on 2007-09-10
Dear,

I am unable to use the WPA as i followed the setting of website you shown me. 
Can you show me how to use the WPA through the TERMINAL? 

thanks you.

---

### Post by kevdog on 2007-09-10
This is for testing purposes only, this script can be better defined than this.

This example assumes ndiswrapper as the wireless driver, which i dont know if you are using.  If you are using a different driver, do a 
man wpasupplicant

Read it, it will give you other options other than wext as the driver -- example intel = ipw.

I borrowed this, 

Create wpa_supplicant configuration somewhere, say, /etc/wpa_supplicant.conf. A simple configuration such as

ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="myssid"
   psk="mysecret"
   key_mgmt=WPA-PSK
   proto=WPA
 }

should suffice. Note that psk given above can be plain text ASCII pass phrase that is used on the AP or hex digits (without quotes) that can be generated with wpa_passphrase from the same ASCII pass phrase. For simplicity, go with ASCII pass phrase.

Above configuration causes wpa_supplicant to negotiate which encryption scheme to use. Certain AP’s might not work with this negotiation procedure. So it can help to limit the scheme to the most basic WPA one: TKIP. Add this line to your config to do so: pairwise=TKIP

Now start the interface and then wpa_supplicant. For example, as

ifconfig wlan0 up
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

Note: With ndiswrapper version 1.12 and older, use -Dndiswrapper instead of -Dwext.

Now configure the network interface; e.g., if you are using a DHCP you may need to run
dhclient wlan0

The option -dd to wpa_supplicant gives lot of output so you can see if there is a problem. If everything works, you can drop -dd option. You may also want to leave wpa_supplicant running in the background with the option -Bw so you don’t need to start it everytime. Once wpa_supplicant authenticates, you can use DHCP to configure the network interface.

---

### Post by Paris Heng on 2007-09-10
Ok, i will try it. Thanx

---

### Post by peterv6 on 2007-09-10
Paris,
Would you please tell me how you installed the WPA supplicant in Fiesty?  I'm a newbie at Linux, so if you wouldn't mind posting the step-by-step directions, like where I can get the package I need and how to install it, I'd be very grateful!
PETERV

---

### Post by Paris Heng on 2007-09-11
> **peterv6 said:**
> Paris,
Would you please tell me how you installed the WPA supplicant in Fiesty?  I'm a newbie at Linux, so if you wouldn't mind posting the step-by-step directions, like where I can get the package I need and how to install it, I'd be very grateful!
PETERV

Method 1:
In Feisty, the wpa_supplicant is installed by default by the Kernel. You can try to install by:

> sudo apt-get update
sudo apt-get install wpa_supplicant

It will show you  0 installed, if it already installed. 

Method 2:
Another way to check is goto** Package Manager**, type WPA in search to look weather the wpa_supplicant installed or not. IF not installed, just right click and select install. Then click on the "**Apply"** on the panel. It will installed for it and you must have a Internet connection in order to download the package.

Regards

---

