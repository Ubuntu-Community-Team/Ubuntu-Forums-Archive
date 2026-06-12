---
title: "RT61 card working with Hardy, static IP, 54M and on reboot."
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by ushills on 2008-05-01
Finally I have got the RT61 wireless card working with a static IP, WPA, 54M and it automatically starts on boot up.

Using Roaming mode I could always used DHCP but not a static IP.

Here is the solution that worked for me.

Firstly, disable Roaming in network manager by selecting manual configuration from the network icon in the taskbar.

Then select edit wireless again from the network manager icon and delete and wireless networks listed.

Now do the following in a terminal.

Generate a hex WPA key with 

```
wpa_passphrase YOUR_SSID WPA_PASSPHRASE
```

and copy this code

```
sudo nano /etc/network/interfaces
```

remove any existing lines relating to wlan and use the following configuration, substituting for your network where applicable.

```

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
wpa-psk KeyGeneratedAfterRunning_wpa_passphrase_WithoutQuotes
wpa-key-mgmt WPA-PSK
wpa-proto WPA

#enter your SSID name below
wpa-ssid YOUR_SSID

# wait for 20 seconds to bring interface up
pre-up sleep 20

# make sure that you get full bit rate
iwconfig wlan0 rate 54M

# start interface
pre-up ifconfig wlan0 up
# make it start automatically
auto wlan0

```

Now restart the network, with

```

sudo /etc/init.d/networking restart

```

Your network should now work with a static IP using the native drivers in Hardy and restart on a reboot automatically.

Post if you have any problems.

---

### Post by khaji00 on 2008-05-11
ushills,

I still could not get it configured using this method.  One thing differnt on my set up, which i'm not sure makes a difference is the fact i dont have a locked/encrypted network.  I use MAC Address filtering, which is properly set up in my router and works when i switch to WinXP.

When i leave your WPA entries in your configuration empty the network restart fails.  When i delete all WPA entries from your config the network reset work.

I have entered the IP information for my system and still no luck.  I cannot connect to the network/internet.  I even did a system reboot.

When properly configured should the icon be of wireless bars or of 2 computers connected via ethernet?  My icon changes from wireless to a ethernet looking icon?  I'm not sure what i'm doing wrong.

thanks,
alex

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

### Post by n1ght28 on 2008-06-23
Amazing work my friend, worked an absolute treat for me. long live the linux,

---

### Post by n1ght28 on 2008-06-24
hey again if i wanted to put in both a primary and decondary DNS would it look like this or what would you recommend,


[CODE]

# set the static ip configuration, these will depend on your network
address 192.168.1.9 
gateway 192.168.1.1
**dns-nameservers 192.168.1.1 192.1.1.2**
netmask 255.255.255.0
broadcast 192.168.1.255

with the correct addresses in obviously, cheers,

---

### Post by chorltonian on 2008-10-18
This worked for me (thanks for your help!) as far as getting a static IP address and not having to use NetworkManager. However, I found I had to create an executable script in /etc/network/if-up.d to set the connection speed.

```

#!/bin/sh

# set the wireless bit rate
iwconfig wlan0 rate 54M
```

---

### Post by StephenG on 2008-10-24
Ushills --
I finally got my RT61 card working, but I'm more vanilla than you -- using WEP and DHCP.  Can you advise what file I need to modify to get it to come up with rebooting, rather than having to enter the control panel every time I turn the box on and enter the key and a new profile?  I'm using RutilT instead of Network Manager.  I'm still too new at Linux to understand it all, but I'm trying.

---

### Post by grwilmoth on 2010-01-22
Nice job man. This STILL worked for me on the karmic koala server edition. Thanks!

---

