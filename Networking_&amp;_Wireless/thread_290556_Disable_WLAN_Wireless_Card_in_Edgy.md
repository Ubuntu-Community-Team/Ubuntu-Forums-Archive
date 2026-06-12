---
title: "Disable WLAN Wireless Card in Edgy"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by coppertrail on 2006-11-01
I have Edgy running on a Laptop which has a wired and wireless interface.  Here's what I want to do:

Disable the WLAN card, as one would in Windows.  Even by unchecking the card in the networking applet, it's connecting to a public hotspot and overwriting my wired connection with the wireless DHCP info.  

I believe it's as simple as editing the /etc/network/interfaces file, but I'm not sure what I would replace the word auto with on the the WLAN interface line.  

Thanks!

---

### Post by trubblemaker on 2006-11-01
you might be using some sort of wireless connection package if your info is getting over written.  to stop you wireless from starting on boot remove it's name from the auto line or remove it's auto (marked in red)  **DO NOT REMOVE "auto lo" from you interfaces file**
```

auto lo [COLOR="Red"]wlan0[/COLOR]
iface lo inet loopback

iface wlan0 inet dhcp
        pre-up /home/meat/network_Startup_script

```

*NOTE* sometimes each interface will have an "auto" line in that case remove that auto line.

to stop it from over writing things don't use the gui and use "sudo dhclient wlan0" instead.  dhclient reads the current settings and starts wireless without writing to "/etc/network/interfaces"

---

### Post by RjBanker18 on 2006-11-01
Hey, I'm pretty sure the command

sudo iwconfig <interface> essid off

will do the trick, that command will prevent your wireless from associating to an ap.  if you want it to associate again...

sudo iwconfig <interface> essid on

will do the trick! :D

P.S. use the command "sudo dhclient" to get new dhcp info.

---

### Post by coppertrail on 2006-11-01
Thank you for your replies, great info. 

Trubb - 

I don't have any WLAN lines in my interfaces file, only eth(x).  So, I'd remove the word _**auto**_ in the line of the wireless interface? 

This would require me to do a **_sudo ifup ethx_** in order to bring the wireless interface up?

---

### Post by trubblemaker on 2006-11-01
> **coppertrail said:**
> Thank you for your replies, great info. 

Trubb - 

I don't have any WLAN lines in my interfaces file, only eth(x).  So, I'd remove the word _**auto**_ in the line of the wireless interface? 

typically it would be eth1 for your wirless.
> **coppertrail said:**
> 
This would require me to do a **_sudo ifup ethx_** in order to bring the wireless interface up?
yes that's correct, if you want to use the "/etc/network/interfaces" file to start your interface.  To use the current settings, (like if you changed the essid manually and want to use that setting) then use 
```
sudo dhclient eth1
```

---

