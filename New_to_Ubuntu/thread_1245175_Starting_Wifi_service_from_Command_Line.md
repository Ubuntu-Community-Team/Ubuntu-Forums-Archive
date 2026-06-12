---
title: "Starting Wifi service from Command Line?"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by mapes12 on 2009-08-20
My home network has the machines connected to the router via ethernet cables into the router. The router is wifi enabled. I have another machine that I'm working on that is too far away to be hard wired but has a fully functional PCI wifi card. The wifi card is fully Linux compatable and works fine when the machine is running Ubu when booted normally from the HDD.

However, the work I'm doing on the machine means that I need to boot it from a CD to load Linux into memory and get me to a command prompt. From the command prompt I need to enter commands to instruct the wifi adapter to connect to the wifi router and get itself assigned an IP address via DHCP. I have the routers SSID and password but I don't know the commands to enter to do this. 

Anybody?

TIA

Mark

---

### Post by Bachstelze on 2009-08-20
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant)

(You didn't mention which encryption scheme you're using, so I assumed it's WPA.)

---

### Post by mapes12 on 2009-08-20
> **HymnToLife said:**
> [https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant)

(You didn't mention which encryption scheme you're using, so I assumed it's WPA.)Thank you.

I'm not sure if it's WEP or WPA the passphrase is a series of 10 letters and digits. The router is a BTHomeHub supplied by........BT

At the moment the machine isn't connected to any kind of network so apt-get install is a problem.

---

### Post by Bachstelze on 2009-08-20
> **mapes12 said:**
> Thank you.

I'm not sure if it's WEP or WPA the passphrase is a series of 10 letters and digits. The router is a BTHomeHub supplied by........BT

At the moment the machine isn't connected to any kind of network so apt-get install is a problem.

It's probably WPA then. Using  a WEP passphrase that shourt would be foolish. And you can install packages from your Ubuntu CD, everything you need should be there.

---

### Post by mapes12 on 2009-08-20
The machine I'm working on will not load Ubu live CD. So the only CD I have with a bootable Linux kernel is the Systemrescue cd I use with partimage and GParted. I'm sure it's a Gentoo distro kernel and it's got me to a Terminal.

Using iwconfig and associated man pages I have found out that my wifi adapter has been identifed as wlan0. Using iwconfig I have configured it with the router SSID and passphrase. I tried iwlist but I couldn't see anything in the results that looked like my router.

So I guess what I need now is the CL to scan the airwaves to find the router and connect to it? 

Done lots of Googling but drawn a blank so far.

---

