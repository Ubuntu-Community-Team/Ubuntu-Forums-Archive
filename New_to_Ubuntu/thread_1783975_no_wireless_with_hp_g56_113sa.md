---
title: "no wireless with hp g56 113sa"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by bh89 on 2011-06-16
Hi everyone,

I'm new to ubuntu and have recently installed the os on a hp g56 laptop. The problem is that i cant get wireless to work on it. when i click on the network applet and select 'edit wireless networks' no networks appear. any suggestions would be really appreciated.

Thanks.

---

### Post by seawolf167 on 2011-06-16
Please connect the laptop to your internet source (gateway) via an ethernet cable, then open the Additional Drivers system configuration and see if you have any drivers for your device that you can install.

In 11.04, click the power icon in the upper-right, select system settings, then additional drivers
For previous version, it is System -> Administration -> Hardware Drivers

---

### Post by bh89 on 2011-06-16
Hi,
i opened the 'hardware drivers' box and it says "no propriety drivers are in use on this system". is there another way of downloading the necessary drivers?

---

### Post by seawolf167 on 2011-06-16
Can you please open a terminal (the default keyboard shortcut is [CTRL][ALT][T]), and type in the following command, then post the output here inside CODE tags when you reply (not quick reply)

```
sudo lshw -class network
```

---

### Post by bh89 on 2011-06-16
*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 78:ac:c0:56:77:94
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.39 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
ben@ubuntu:~$

---

### Post by seawolf167 on 2011-06-16
It looks like since your network is unclaimed, there no kernel modules or drivers contained in your installation that support the device. If there are no entries that you can select and active in the Additional Drivers section, you will have to find and install the drivers manually. Can you get a model number of the wireless RealTek card from any of your spec sheets?

The drivers for your ethernet card by comparison are already installed, and RealTek has the drivers listed [here]("http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false").

---

### Post by bh89 on 2011-06-16
no, i'm sorry mate i cant find the drivers listed anywhere in the specs...

---

### Post by wildmanne39 on 2011-06-16
> **bh89 said:**
> no, i'm sorry mate i cant find the drivers listed anywhere in the specs...Hi, your card did not show up as being installed when your ran the commands that you were ask to run, I have seen this recently, is your card an usb card? I figure you need to see how you can turn your card on it looks like it is off, some people use a fn key or a button to turn theres on, if you turn it on and it still does not work run those cammands again that way we can see what card you have and probably be able to help you get it working. You can also run these three commands and see if it show your card.

lspci
lsmod
ifconfig

post the outcome back here by clicking on new reply and click # and paste the information between the brackets.

---

