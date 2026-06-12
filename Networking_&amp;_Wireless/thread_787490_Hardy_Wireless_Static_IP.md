---
title: "Hardy Wireless Static IP"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by khaji00 on 2008-05-08
Hello,

I'm trying to assign a internal static IP to my pc for my wireless card and i seem to be doing something wrong.

When i use the gui and go to the System>Administration>Network menu and manually configure my IP, it accepts the settings but i have no internet connection.

I came across this site in the forums: [http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319) and went through those settings but it seems to have only changed my ethernet port to the correct settings, but i'm not using a wired connection.

I'm use a 32bit version of hardy with a Linksys PCI card (Ralink RT61 chip)

Any help would be appreciated.

---

### Post by helgman on 2008-05-09
There are three things in your set up that you must look through:

A) You need to get the network settings right (IP address, subnet mask, default gateway etc).

B) You need to get basic services set right (DNS).

C) For wireless, you also need to associate with an access point.

As for the guide you used, you have to change eth0 to the interface "name" of your wireless card (different depending on ... chipset I guess).

Does this help you pin down the reason?

Regards,
Helgman

---

### Post by superprash2003 on 2008-05-09
after you have configured static ip.. type ifconfig in your terminal and ensure that it has been set.. Also try pinging your router and try pinging say google.com

---

### Post by ushills on 2008-05-09
This will get it working

[http://ubuntuforums.org/showthread.php?t=777036](http://ubuntuforums.org/showthread.php?t=777036)

---

### Post by khaji00 on 2008-05-11
still no luck, this time i was referencing the thread by ushills

Is it not working because i do not have any encryption on my network?  I use MAC address filtering which is properly set up.

I checked with ifconfig and my wireless card is wlan0, which is in any config file i edit.

Not sure what i'm doing wrong.  As i mentioned to ushills, my icon on the top changes from a wireless icon to an ethernet connected looking icon every time i manaually edit my wireless settings?

---

### Post by ushills on 2008-05-13
In that case try

```
Code:
# wireless configuration, change wlan0 where applicable
iface wlan0 inet static

# set the static ip configuration, these will depend on your network
address 192.168.1.9 
gateway 192.168.1.1
dns-nameservers 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255

# bring the interface down, this makes it start correctly
pre-up ifconfig wlan0 down 

# enter correct key below

#enter your SSID name below
iwconfig wlan0 essid YOUR_SSID
iwconfig wlan0 mode Managed

# wait for 20 seconds to bring interface up
pre-up sleep 20

# make sure that you get full bit rate
iwconfig wlan0 rate 54M

# start interface
pre-up ifconfig wlan0 up
# make it start automatically
auto wlan0
```

The change to ethernet icon is correct for a manually configured network.

---

