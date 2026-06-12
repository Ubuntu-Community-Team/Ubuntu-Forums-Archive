---
title: "Extremely slow WiFi With Ubuntu 16.04, And driver=iwlwifi"
date: 2017-04-05
forum: Networking &amp; Wireless
---

### Post by sajerner on 2017-04-05
Hello!
I have an Asus N53 laptop. 
I had some troubles with wifi 2 or 3 years ago, and I changed my wireless adapter that time and everything was good until I upgrade my ubuntu to 16.04, after that my wifi connection is extremely slow on SOME networks ( like few minutes to load a simple web page! ) for example I am good in university but it is awful on my home network! 
Also, everything is good with the ethernet cable or in windows 7!
The problem only occurs in ubuntu and on SOME wireless networks! and It is very bad because my home network is one of those! : (


I tried almost all solution I could find on the net, but nothing helps!


I have a TP-Link ( TP-W8901N ) modem router, and this is the information relevant to my network wireless interface.
```
[COLOR=#000000][FONT=verdana]sudo lshw -C network[/FONT][/COLOR]
```

```
*-network 
description: Wireless interface
product: Centrino Wireless-N 1000 [Condor Peak]
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlp3s0
version: 00
serial: 8c:a9:82:81:db:8e
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-72-generic firmware=39.31.5.1 build 35138 ip=192.168.1.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
resources: irq:34 memory:ddc00000-ddc01fff
*-network
description: Ethernet interface
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:05:00.0
logical name: enp5s0
version: 06
serial: 14:da:e9:2c:9e:62
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.109 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
resources: irq:29 ioport:9000(size=256) memory:d2104000-d2104fff memory:d2100000-d2103fff


```
[SIZE=4][COLOR=#333333][FONT=georgia]I really appreciate any help you can provide.[/FONT][/COLOR][/SIZE]

---

### Post by wildmanne39 on 2017-04-05
Click on the wireless script in my signature and follow the directions for running it and posting the link created to pastebin here, which is where the file will be posted.

Make sure to run it from the network you are having an issue with.
Thanks

---

### Post by sajerner on 2017-04-05
> **wildmanne39 said:**
> Click on the wireless script in my signature and follow the directions for running it and posting the link created to pastebin here, which is where the file will be posted.

Make sure to run it from the network you are having an issue with.
Thanks

Thank you for your help :)

I tried to do that 4 times, the first 3 times get timed out because of very slow connection and the 4th posted finally !
Here you are:
[http://paste.ubuntu.com/24321710/](http://paste.ubuntu.com/24321710/)

---

### Post by wildmanne39 on 2017-04-05
Always make sure your ethernet connection is unplugged because it will always be used instead of your wifi connection if it is plugged in and your ethernet connection has the wrong driver so it will be very slow.

Let's turn power management off by just coping and pasting the command into the terminal then hit enter:
> sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
Please set your wireless settings in network manager to match the settings in the screenshots.

Now, change the settings in the router to WPA2-AES not WPA and WPA2 mixed mode and definitely not TKIP. Second, if your router is capable of N speeds, you will probably have a better connection with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz.

Change your channel to a set channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router and your computer.

If you live in Tehran we need to change the Country Code for your router by doing:
```
sudo iw reg set IR
```
To make it permanent:
```
sudo sed -i 's/^REG.*=$/&IR/' /etc/default/crda
```

---

### Post by sajerner on 2017-04-06
> **wildmanne39 said:**
> Always make sure your ethernet connection is unplugged because it will always be used instead of your wifi connection if it is plugged in and your ethernet connection has the wrong driver so it will be very slow.

Let's turn power management off by just coping and pasting the command into the terminal then hit enter:

Please set your wireless settings in network manager to match the settings in the screenshots.

Now, change the settings in the router to WPA2-AES not WPA and WPA2 mixed mode and definitely not TKIP. Second, if your router is capable of N speeds, you will probably have a better connection with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz.

Change your channel to a set channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router and your computer.

If you live in Tehran we need to change the Country Code for your router by doing:
```
sudo iw reg set IR
```
To make it permanent:
```
sudo sed -i 's/^REG.*=$/&IR/' /etc/default/crda
```

Thank you very much, I did what you said :
 
I turned off the power management.
I changed wireless setting to what you said ( changed method, adding DNS servers and ignore IPV6 )
My router was on WPA-PSK and I changed to WPA2-PSK.
I changed the channel width to 20 MHz instead of auto.
And I changed the channel to IRAN 06

and now, things may be better but highly unstable!
for example, it is ok ( still slower than ethernet cable ) in one connection but if I disconnect and connect again it got back to what it was!
here is the wireless script when it was ok:
[http://paste.ubuntu.com/24326731/](http://paste.ubuntu.com/24326731/)
and here is the wireless script when it was just like before: ( it took me 100 try to get this because of the slow connection! )
[https://paste.ubuntu.com/24326890/](https://paste.ubuntu.com/24326890/)

They sound similar but they have some differences

or 2 or 3 times, suddenly the wifi icon turned off ( like the screenshot ) and no connection after that!
and the other screenshot is the error I got when things are not ok!
[ATTACH=CONFIG]274454[/ATTACH][ATTACH=CONFIG]274455[/ATTACH]


ps : always everything is good with the ethernet cable or in windows 7 and I unplugged it when I was testing wireless connections

---

### Post by sajerner on 2017-04-17
any help?  :(

---

