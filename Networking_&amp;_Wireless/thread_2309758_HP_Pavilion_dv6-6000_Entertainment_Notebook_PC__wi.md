---
title: "HP Pavilion dv6-6000 Entertainment Notebook PC  wifi not working"
date: 2016-01-13
forum: Networking &amp; Wireless
---

### Post by gaetano6 on 2016-01-13
Hello everyone! Just installed Ubuntu 14.04 on my laptop and the f12 key led it's constantly with the red light on, also when I go to the top right in the networking the wi-fi commands are grey and cannot be clicked. I'm posting a new thread because after trying to follow the instructions that were given to other users with similar problems I didn't managed to solve anything... It's my first time using this OS so please be patient with this desperate noob.

---

### Post by Bucky Ball on 2016-01-13
Welcome. How old is this machine and was it running ok with whatever OS you were running on it prior to install Ubuntu?

Please open a terminal and paste this in:

> sudo lshw -C network

Copy/paste the output here between code tags, please (see last link in my signature for how).

---

### Post by gaetano6 on 2016-01-13
```
 *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 08:2e:5f:84:46:78
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:34 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network DISABLED
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 01
       serial: 20:10:7a:23:ad:c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.19.0-43-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:3000(size=256) memory:c4500000-c4503fff 
```
I bought this machine in november 2012, it came with windows 7, I installed windows 8.1 last year and it was performing better (but the wifi stopped working). Then I updated to windows 10 (problem persisted) and finally I installed Ubuntu because I'm starting to program and it was recommended by some friends in college. Now I hope Ubuntu is more helpful solving this problem since the terminal it's a real terminal unlike window&#8217;s.

---

### Post by Bucky Ball on 2016-01-13
If you were having issues with wifi dropping out for some time prior to this I doubt installing a different OS is going to make much difference, but you never know. Plug in an ethernet cable, do an update, reboot. If nothing, then try this in a terminal, one line at a time:

```

echo 'options rtl8192ce swenc=1' | sudo tee /etc/modprobe.d/rtl8192ce.conf  
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```

From Wild Man's suggestion at [the bottom of this page]("http://askubuntu.com/questions/342076/step-by-step-ubuntu-12-04-install-of-realtek-rtl8188ce-driver"). From what I can dig up that appears to be the correct driver you have but it can be problematic. Thought it may have been fixed considering the kernel you're using. Having said that, there is every possibility this is a hardware issue and your setup in Ubuntu is perfectly fine, considering your wifi history with Win .

---

### Post by gaetano6 on 2016-01-13
Ok thanks I'm gonna try the inputs you suggested. What do you mean by doing an update? What should I update? If none of those inputs or the update works could it be that my wifi adapter is damaged? one more thing, I used a usb adapter before to get wifi signal in my computer but now with Ubuntu when I plug it in it doesn't even notice it is plugged in,,,

---

### Post by Bucky Ball on 2016-01-13
Let's stick to the device you started with for now. :)

If you want support with that, perhaps start a new thread. Gets confusing trying to deal with more than one problem on one thread.

An update is just something we do in Ubuntu, normal, and if you haven't done one since you installed, good idea. Open 'Software Updater' and update. Reboot. Any wifi? Make sure the USB dongle is out of the machine when working on the internal card and posting info about your internal card here, thanks.

Seems obvious if your card has been problematic for some time in Windows that it is quite possible it's a hardware issue. Changing OSs is not going to change that.

---

