---
title: "I need to ignore neighbors router"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by SumoJim on 2007-09-15
I need to find a way to stop my wireless router from automatically connecting to my one of my neighbors routers, On boot up my laptop attempts to connect to a router in range and about 50% of the time it connects to my neighbors, and if it attempts to connect to that router Ubuntu will freeze about 50% of the time (Shutdown won't even work and I have to force it off by holding power button 3 seconds, then restart again).

So, I guess I need to find a way to block his router. (I think it is a peer to peer connection b/c of the icon that shows up next to his ESSID on my list.)

This is the router I need to block:
iwlist eth1 scanning

Cell 02 - Address: CA:23:70:C1:5A:91
                    ESSID:"UCF"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Channel:10
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=91/100  Signal level=-55 dBm  Noise level=-69 dBm

Here's the thing though, I will need to block by Address and not ESSID because the wireless routers for school also have the ESSID: "UCF".

If it isn't possible to ignore a specific router is it at least possible to keep my wireless card from automatically connecting at boot up and wait for me to manually click "Enable Wireless"?

(I am using ndiswrapper with a Broadcom 4306 wireless card... If that matters)

Any advice would be greatly appreciated.

Jim

---

### Post by Kralizec on 2007-09-16
What might work is if you took network manager out of your startup applications, then started it manually after you log in.

System->Preferences->Sessions and uncheck Network Manager. To start, hit alt-f2 and type 'nm-applet'.

---

### Post by SumoJim on 2007-09-16
Thank you for the suggestion. I will do that as a last resort. I was hoping though to at least let the application start at boot up but not connect automatically. And I really want to put the other router on a black list somehow.

I checked the man pages and there wasn't much there. I checked [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/) and again nothing to be found. (Except of course the option to modify the code, But I wouldn't know where to begin with that.) I'm still doing digging of my own and haven't found anyone else who needs to ignore a router. I am probably out of luck, but thought I'd ask anyway.

---

### Post by panda726 on 2007-09-16
I am quite new to linux, but I believe it is easy to create network locations.  You may be able to create a "home" location and a "school" location, and block the ESSIED for the "home" location.  When you switch to the "school" location the ESSID should still be available.  If this doesn't help, then I probably cannot help you, as I have rather limited experience with wireless.

---

### Post by Kralizec on 2007-09-16
Another thing I just thought of is that if you set network manager to manual configuration, you can specify what network it will connect to. Just select manual configuration, then go into properties for your wireless and disable roaming. Then you'll have to specify the ESSID and encryption key; you can keep the connection settings set to DHCP so you only have to specify network settings.

---

### Post by SumoJim on 2007-09-16
Another problem is that sometimes my connection is interrupted and my wireless automatically switches to a different ESSID namely my neighbors which again sometimes forces me to reboot my computer. Which is why I really need to somehow make that router not an option for my wireless driver.

A side note:
I know the problem with freezing is that my Broadcom wireless driver in combination with ndiswrapper, has trouble with some routers depending on their security settings. (I will never buy another laptop w/ a Broadcom wireless card again!)

Hmm... I just found an interesting bit.

fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

This was in my network settings under the "Hosts" tab.
Does anyone know if I can change ip6-allrouters to something else? Maybe something specific rather than all? Just a shot in the dark.

---

