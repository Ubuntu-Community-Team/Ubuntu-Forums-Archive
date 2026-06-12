---
title: "WPA Fails but WEP works- Help with WPA"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by nimbuscott on 2006-09-06
I am able to connect to my wireless router using WEP but I cannot figure out how to connect using WPA. Following some suggestions on these boards I tried downloading NetworkManager but can't figure out how to use it to enter my WPA password.I want to connect using DHCP not static IP and a non-hidden ESSID so NetworkManager is supposed to work. I have tried some command line tweaks but no joy.

I purchased a Hawking Technology WC54D wireless PCMCIA card for my Thinkpad A31 because the Ubuntu [HardwareSupport Wiki]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") said it worked in Dapper Drake with no problems. The Wicki says it uses the rt2500 chipset. It connects fine with no encryption and with WEP encryption but WAP isn't working. I am trying to connect to a Linksys WRT54GX using WPA Pre-shared Key & TKIP Algorithm. I can connect fine using WPA from OSX laptop so I know the router side works.

thanks in advance

---

### Post by jbom on 2006-09-06
I'm not sure if this helps (I've just spent all day and finally got mine going) as I use an intel 2200 working into a netgear wireless router but it sounds the same.
The knetworkmanager started working ok when I uninstalled the wireless assistant, and the package dependent on it (ubantu desktop I think). Then restarted.
Someone on this thread said the k network manager had to work alone and it seems true.
I must say I'm stoked to get it going after wasting all day on wpa supplicants etc. It was quite simple in the end.:-D  
I hope it's as simple for you!

---

### Post by wieman01 on 2006-09-07
When using NetworkManager make sure this file only has 2 entries (if you don't use ethernet for the time being):

**_/etc/network/interfaces:_**
> auto lo
iface lo inet loopback

Then restart. If you are looking for a manual solution by editing that file, let us know.

---

### Post by nimbuscott on 2006-09-08
I got it to work! The secret was to replace the contents of the interfaces file with the code below.

```
sudo gedit /etc/network/interfaces
```

replace the contents with the following then save the file. You replace the text in [COLOR="Red"]red ***[/COLOR] with your own information. Part of the learning process for me with this involved setting my router to WPA2 which is AES algorithm not WPA1 which is TKIP algorithm.On my Linksys router the choice is Pre Shared Key & AES. The essid is the name you gave your network in your router settings and the WPAPSK is your password.


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

iface ra0 inet dhcp
pre-up iwconfig ra0 essid [COLOR="Red"]***[/COLOR]
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=1
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=AES
pre-up iwpriv ra0 set WPAPSK=[COLOR="Red"]***[/COLOR]
pre-up iwpriv ra0 set TxRate=0




auto ra0
```

---

