---
title: "Setting a static ip address 13.10"
date: 2014-03-25
forum: Networking &amp; Wireless
---

### Post by d.mayfair on 2014-03-25
Hi
I have various devices on my network,all but my main pc are connected via a powered ethernet switch which in turn is connected to the router via a powerline adaptor.
I wish to assign one of these devices....an ubuntu pc...a static ip address as I use xbmc on it with a tablet remote app.The app will only work if the ip address remains constant.

I've tried setting it using ubuntu's connections gui but it won't allow me to save the changes....the save box is greyed out.

Can someone talk me through the process please ?

cheers

---

### Post by chili555 on 2014-03-25
Will it allow you to save if you fill in the address, outside the range of the DHCP server in the switch or router, the netmask, gateway and the DNS nameservers? [http://www.liberiangeek.net/wp-content/uploads/2010/09/static_ip_mav_2.png](http://www.liberiangeek.net/wp-content/uploads/2010/09/static_ip_mav_2.png)

---

### Post by d.mayfair on 2014-03-25
I'm not sure what you mean.In that link it shows 2 numbers in the dns servers box.I have put the same as in the gateway,ie the ip address of my router.
I don't know what the range is

---

### Post by chili555 on 2014-03-25
Either the router or the switch is set to serve IP addresses by DHCP; probably the router. DHCP means that the router sets the address, netmask, gateway and DNS automatically so the most users needn't know or care about those details. There is usually a pool set aside for DHCP: [http://morscher.com/atcs/e1200_1a_setup.jpg](http://morscher.com/atcs/e1200_1a_setup.jpg) 

In the example I've linked, the router is set to assign DHCP addresses from 192.168.1.2 to 192.168.1.51. If you set a static IP address inside this range, you run the risk of a collision; both your XMBC and your desktop trying and failing to use the same address. In this setting, I'd use the static address of 192.168.1.100.

In order to know for sure, I suggest you log on to the administration pages of the router and then the switch and see who is the DHCP server and set your static IP outside the pool. 

The gateway address is usually sufficient for DNS.

---

### Post by d.mayfair on 2014-03-25
Ok,well I got it to accept the changes,I set the IP address outside of the range.

Now it won't connect to the internet.I can see from xbmc that Mac address comes up busy and Primary DNS is 127.0.1.1

---

### Post by chili555 on 2014-03-25
How do your settings compare to other computers on the network? You may need to reboot for the changes to take effect. Do you mind sharing the exact numbers? If you are behind a router, the addresses, typically 192.168.x.y, are private addresses and pose no security threat. > I can see from xbmc that Mac address comes up busy I don't understand this. Can you please elaborate?

---

### Post by d.mayfair on 2014-03-25
Main pc
[[IMG]http://img.photobucket.com/albums/v176/StokieDaz/IMG_20140325_202259_717_zps130a3055.jpg[/IMG]]("http://smg.photobucket.com/user/StokieDaz/media/IMG_20140325_202259_717_zps130a3055.jpg.html")

PC I'm setting static address on
[[IMG]http://img.photobucket.com/albums/v176/StokieDaz/IMG_20140325_202042_501_zps816ea4bb.jpg[/IMG]]("http://smg.photobucket.com/user/StokieDaz/media/IMG_20140325_202042_501_zps816ea4bb.jpg.html")

Xbmc settings
[[IMG]http://img.photobucket.com/albums/v176/StokieDaz/IMG_20140325_202158_732_zps9b6c5fe2.jpg[/IMG]]("http://smg.photobucket.com/user/StokieDaz/media/IMG_20140325_202158_732_zps9b6c5fe2.jpg.html")
[[IMG]http://img.photobucket.com/albums/v176/StokieDaz/IMG_20140325_202125_807_zps10e7b345.jpg[/IMG]]("http://smg.photobucket.com/user/StokieDaz/media/IMG_20140325_202125_807_zps10e7b345.jpg.html")

---

### Post by chili555 on 2014-03-25
I believe that x.255 is a reserved address. Please reset to x.200 and reboot.

---

### Post by Iowan on 2014-03-25
Looks like you selected the broadcast address as the IP address.

Out-typed by Master Chili555... again ;)

---

### Post by d.mayfair on 2014-03-25
I only used 255 because the range went up to 254. :)

---

### Post by Iowan on 2014-03-25
Perhaps you could set a smaller DHCP range?

---

### Post by chili555 on 2014-03-25
> **d.mayfair said:**
> I only used 255 because the range went up to 254. :)Unless you are expecting 253 guests at your home, you can certainly reduce the range to 50 or even less. If you set the range from 192.168.1.2 to 192.168.1.51; i.e. a pool of 50, you can then safely use, for example,192.168.1.100 for the static IP. 

Is this intended to run a graphical desktop, upon which Network Manager depends?

---

### Post by d.mayfair on 2014-03-25
I didn't realise the range was user configurable.

Anyway,I've reduced the range and set the ip address outside that and everything is working :)

Thank you

---

