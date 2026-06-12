---
title: "Ubuntu 20.04.3 LTS vs Windows 10 - Ethernet Half the Network speed"
date: 2022-02-08
forum: Networking &amp; Wireless
---

### Post by re8el on 2022-02-08
Hi eveyone,

Been strowgling with ethernet speed. i have my HP ZBook Ubuntu 20.04 lts full updated, and on a lan network that its at 1/Gbps Ubuntu only can make 500/Mbps compared to the dualboot Windows 10 on the same laptop/hardware, i can make 950/Mbps.

Im using a smb fileshare to a NAS and transfer big files 60gb to the NAS, and the diference of speed it huge.

Any ideas?

Down below some info of my ZBook.

[COLOR=#181A1B]My hardware:[/COLOR]


[COLOR=#181A1B]Laptop - HP [/COLOR][COLOR=#3E7396]Zbook[/COLOR][COLOR=#181A1B] Power G7[/COLOR]
[COLOR=#181A1B]i9-10885H[/COLOR]
[COLOR=#181A1B]64 GB DDR4-3200[/COLOR]
[COLOR=#181A1B]Intel UHD Graphics && NVIDIA Quadro T1000 with Max-Q Design (4 GB GDDR6 dedicated)[/COLOR]
[COLOR=#181A1B]2x 1 TB PCIe NVMe M.2 SSD[/COLOR]
[COLOR=#181A1B]Intel Wi-Fi 6 AX201 (2x2) and Bluetooth 5 combo, vPro[/COLOR]
[COLOR=#181A1B]Intel I219-LM GbE, vPro[/COLOR]
[https://support.hp.com/lt-en/document/c06931915](https://support.hp.com/lt-en/document/c06931915)


[COLOR=#181A1B]DockStatio - HP Thunderbolt Dock 230W G2 w/ Combo Cable[/COLOR]
[COLOR=#181A1B]Front: 1 USB-C™ port with data and power out (15W); 1 USB-C™ cable to connect to host system (0.7 meter cable length); Side: 1 powered USB 3.0 port; 1 combo Audio Jack; 1 Kensington lock slot; Back: 1 Thunderbolt™ port; 1 USB-C™ DisplayPort™ data and power out (15W) port; 2 DisplayPort™ ports; 1 VGA port; 2 USB 3.0 ports; 1 RJ45 port; 1 AC Adapter connector[/COLOR]
[https://www.hp.com/us-en/shop/pdp/hp...th-combo-cable]("https://www.hp.com/us-en/shop/pdp/hp-thunderbolt-dock-g2-with-combo-cable")


# lspci -knn | grep Eth -A2
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (10) I219-LM [8086:0d4e]
	Subsystem: Hewlett-Packard Company Ethernet Connection (10) I219-LM [103c:87ec]
	Kernel driver in use: e1000e
	Kernel modules: e1000e

---

### Post by re8el on 2022-02-17
bump

> **re8el said:**
> Hi eveyone,

Been strowgling with ethernet speed. i have my HP ZBook Ubuntu 20.04 lts full updated, and on a lan network that its at 1/Gbps Ubuntu only can make 500/Mbps compared to the dualboot Windows 10 on the same laptop/hardware, i can make 950/Mbps.

Im using a smb fileshare to a NAS and transfer big files 60gb to the NAS, and the diference of speed it huge.

Any ideas?

Down below some info of my ZBook.

[COLOR=#181A1B]My hardware:[/COLOR]


[COLOR=#181A1B]Laptop - HP [/COLOR][COLOR=#3E7396]Zbook[/COLOR][COLOR=#181A1B] Power G7[/COLOR]
[COLOR=#181A1B]i9-10885H[/COLOR]
[COLOR=#181A1B]64 GB DDR4-3200[/COLOR]
[COLOR=#181A1B]Intel UHD Graphics && NVIDIA Quadro T1000 with Max-Q Design (4 GB GDDR6 dedicated)[/COLOR]
[COLOR=#181A1B]2x 1 TB PCIe NVMe M.2 SSD[/COLOR]
[COLOR=#181A1B]Intel Wi-Fi 6 AX201 (2x2) and Bluetooth 5 combo, vPro[/COLOR]
[COLOR=#181A1B]Intel I219-LM GbE, vPro[/COLOR]
[https://support.hp.com/lt-en/document/c06931915](https://support.hp.com/lt-en/document/c06931915)


[COLOR=#181A1B]DockStatio - HP Thunderbolt Dock 230W G2 w/ Combo Cable[/COLOR]
[COLOR=#181A1B]Front: 1 USB-C™ port with data and power out (15W); 1 USB-C™ cable to connect to host system (0.7 meter cable length); Side: 1 powered USB 3.0 port; 1 combo Audio Jack; 1 Kensington lock slot; Back: 1 Thunderbolt™ port; 1 USB-C™ DisplayPort™ data and power out (15W) port; 2 DisplayPort™ ports; 1 VGA port; 2 USB 3.0 ports; 1 RJ45 port; 1 AC Adapter connector[/COLOR]
[https://www.hp.com/us-en/shop/pdp/hp...th-combo-cable]("https://www.hp.com/us-en/shop/pdp/hp-thunderbolt-dock-g2-with-combo-cable")


# lspci -knn | grep Eth -A2
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (10) I219-LM [8086:0d4e]
    Subsystem: Hewlett-Packard Company Ethernet Connection (10) I219-LM [103c:87ec]
    Kernel driver in use: e1000e
    Kernel modules: e1000e

---

### Post by kurt18947 on 2022-02-18
I recently had an experience which may or may not be relevant to your problem. I was checking speed on a wired ethernet home network using an app called iperf3. There are 2 networking protocols (if that's the correct word). TCP/IP and UDP. Using TCP/IP I was getting about 650 mb./sec. Using UDP I was getting 1 gb./sec. I wonder if you have something similar, Windows using one protocol, Ubuntu something else.  I am not an expert in these things.

---

### Post by him610 on 2022-02-18
> Ubuntu only can make 500/Mbps compared to the dualboot Windows 10 on the same laptop/hardware, i can make 950/Mbps.

Either on of those is pretty good speed. Are you connected to a fiber network? Don't know how you check your speed or your location or your server destination.

Perform a series of internet speed tests with Ubuntu and Windows by going to [https://www.speedtest.net/]("https://www.speedtest.net/")
and going to several nearby server destinations which you can choose in the speedtest web interface. 
For instance I just ran several iterations of speedtest from Hanover, PA through my internet provider, Comcast.
```

Destination Server             Ping (ms)  Download (Mbps )   Upload (Mbps)
Washington, DC -Cloudfire      23         93.59              0.00 (not tested)
Harrisburg, PA - Elevated MSP  10         93.84              17.87
Baltimore, MD - Comcast        20         93.93              17.85
Ashburn, VA - Whitesky         22         93.99              17.80

```

---

### Post by re8el on 2022-02-20
Hi!

Thks for the reply but im having this speeds on my Local Lan using protocol SMB for file share that uses TCP/ip. So not from there...

But thks for the input! ;-)

---

### Post by re8el on 2022-02-20
Hi!

thks for the reply, but im having these speeds on my Local Lan bettwen my laptop and my Local NAs, i have a Local Lan of 1GB using CAT6 cabelling.

So it does not mater for the situation what is the speed on the internet.

It realy weird the diference in Speed that i get from Windows 10 to Ubuntu 20.04 Lts...!

I think this is realy a bug! 

thks for the input!

---

### Post by re8el on 2022-03-02
up

---

### Post by re8el on 2022-03-07
up

---

### Post by re8el on 2022-03-10
Hi,

Any ideia how can i report this as a bug from Ubuntu?

Thks for the help in advanced.

V.

---

