---
title: "Wireless disabled/ wireless issues"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by Jun392 on 2011-07-14
Okay so now after doing a clean install and vga=772, I'm into ubuntu, but I can't seem to get wireless on the laptop. I looked at a couple of threads and i inputted the code 

sudo lshw -C network
The output of this was

*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:51:d9:24
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:7000(size=256) memory:b1804000-b1804fff memory:b1800000-b1803fff
  *-network DISABLED
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 10
       serial: 1c:65:9d:08:7b:b9
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=0 latency=0 link=no multicast=yes wireless=802.11bg
       resources: irq:17 ioport:5000(size=256) memory:b5a00000-b5a03fff

I see the *network DISABLED thingy, so I'm guessing that's where my problem is, but since I'm a nub, this is how far I got. Anyways, thanks for the help!

---

### Post by terrykiwi83 on 2011-07-14
Would you post the output of iwconfig

---

### Post by Jun392 on 2011-07-14
```
 lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by linuxman94 on 2011-07-14
Download the linux drivers from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") and install them.  There should be instructions included.

---

### Post by Jun392 on 2011-07-14
Hi so i downloaded the  RTL8191SE-VA2 driver and I'm looking at the directions which states.

You can enter top-level directory of driver and execute follwing command to
Compile, Installation, or uninstall the driver:

```
        1. Change to Super User
       sudo su

    2. Compile driver from the source code 
       make

    3. Install the driver to the kernel
           make install
           reboot

    4. uninstall driver
       make uninstall

========================================================================================
                III. Start Up Wireless
========================================================================================
You can use two methord to start up wireless:

    1. Install driver like II. and reboot OS, Wireless will be brought 
       up by GUI, such as NetworkManager

    2. If Wireless is not brought up by GUI, you can use: 
       ifconfig wlan0 up 
```

 And so my question would be, how do you install the driver to the kernel? it says sudo su, which I did, what should be the appropriate step after that? I apologize for my lack of knowledge.

---

### Post by gandaran on 2011-07-14
just use sudo only on the commands (like "sudo make install")  it'll work.
which release of ubuntu do you have? the rtl8191 chip should work out of the box on ubuntu 11.04.

simple install instructions
first you need to install compiling tools
```
sudo apt-get install build-essential
```
then open terminal and cd to the path of extracted drivers folder
```
user@PC:~$ cd "to drivers path" 
```
then
```
make
```
and last
```
sudo make install
```
that's all, you will need to reboot to load the driver.

---

### Post by Jun392 on 2011-07-14
Okay I did that and rebooted. Wireless Network is still grayed out even though I can enable wireless now. And even when I click connect to hidden wireless network and fill out all the info, it just never fully connects. It just looks like its loading and the wireless network authentication required windows pops up repeatedly even though I already entered the password. It still doesn't detect wireless though.

---

### Post by Jun392 on 2011-07-14
Hey thanks guys. I downloaded that driver, plugged it into a lan connection and used update manager. Once I did that and rebooted the wireless seemed to work. Thanks for the help.

---

