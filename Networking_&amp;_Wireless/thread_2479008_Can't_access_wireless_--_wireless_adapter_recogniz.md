---
title: "Can't access wireless -- wireless adapter recognized but won't run with driver"
date: 2022-09-11
forum: Networking &amp; Wireless
---

### Post by judahwolf on 2022-09-11
[COLOR=#232629][FONT=-apple-system][FONT=inherit][FONT=inherit][FONT=inherit]I upgraded to Ubuntu 22.04 recently. My system is also a dual-boot with Windows. Everything had been going well until recently the computer crashed due to running out of batteries. Now, there is no longer a networking option.

[/FONT][/FONT][/FONT][/FONT][/COLOR]```
~$ sudo lshw -C network  *-network UNCLAIMED       
       description: Network controller
       product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:80500000-8050ffff
  *-network
       description: Ethernet interface
       physical id: b
       bus info: usb@2:2
       logical name: enx00e04c6809e9
       serial: 00:e0:4c:68:09:e9
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.12.12 duplex=full firmware=rtl8153a-4 v2 02/07/20 ip=10.0.0.66 link=yes multicast=yes port=MII speed=1Gbit/s



```

So you can see my adapter is RTL8821CE, but it's marked as "unclaimed". The correct driver is RTL8821CE-dkms. Well, I have installed that, but it hasn't changed anything. It seems to be inactive. I have tried reinstalling it, rebooting, but no luck.

I was directed to try the information gathering script here:

[https://askubuntu.com/questions/425155/my-wireless-wifi-connection-does-not-work-what-information-is-needed-to-diagnos](https://askubuntu.com/questions/425155/my-wireless-wifi-connection-does-not-work-what-information-is-needed-to-diagnos)

The output of that is here:

[https://pastebin.ubuntu.com/p/Rg48qgZMzd/](https://pastebin.ubuntu.com/p/Rg48qgZMzd/)

---

### Post by chili555 on 2022-09-12
Please see your question here: [https://askubuntu.com/questions/1428833/no-option-to-connect-wifi-in-22-04?noredirect=1#comment2488718_1428833](https://askubuntu.com/questions/1428833/no-option-to-connect-wifi-in-22-04?noredirect=1#comment2488718_1428833)

You said: >  I attempted the fixes from here, but to no effect. Where 'here' are instructions to install the driver iwlwifi which is for Intel wireless devices. It will be, as you've found, ineffective for your Realtek device. Please uninstall it:

```
cd backport-iwlwifi && sudo make uninstall
```Reboot. You should be all set.

Thanks, Jeremy!

---

### Post by judahwolf on 2022-09-12
Yup, that worked! Thanks very much to both of you.

---

