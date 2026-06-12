---
title: "I cant get my wireless G network adapter to work?"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by Adam.W on 2008-02-23
Hello
I am using xubuntu on my laptop and have a Belkin wireless G USB network adapter modal number F5D7050. When I plug it in to xubuntu it seems to find the adapter (I think) and seems to find wireless routers in my range but I just can´t get it to connect? I am only a Linux baby so I am not sure if there are some setting I need to change or not?

I typed  sudo lshw -c network in to the terminal and this is what I got:
 
adam@laptopB2131:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 08
       serial: 00:00:0e:d2:f8:d0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.254.50 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: PRISM ISL37101P-SSF Adapter
       product: ISL37101P-10
       vendor: Intersil
       physical id: 0
       version: A3
       slot: Socket 0
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:50:77:31:73
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


I got this code from one of the other threads. Don't know if it helps?
dose anybody know what I can do or what I am doing wrong?

Thanks

Adam

---

### Post by Beowulf.1000 on 2008-02-23
From my experience atheros chipset wifi works best, best supported because of madwifi drivers that are made to work with atheros chipsets. Not sure if Belkin is atheros chipset.

---

### Post by Adam.W on 2008-02-24
Can anyone help I am really stuck or can anybody tell me of a wifi adapter I can buy that will work.

also I have just got a bluetooth doggle and had a quick go at getting thet to work with no joy, any advice?

Thanks

---

### Post by james_vanb on 2008-02-26
If you have the install cd or can download it from Belkin site, try this:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (My default is mousepad) as follows:

sudo mousepad /etc/modprobe.d/blacklist

add rt2500usb and rt73usb to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo mousepad /etc/modules

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

You should now have a connection. Roaming mode works sporadically, so I manually configure. Left click on the network manager at the upper right corner and enter manual configuration. Open wifi properties. Untick "enable roaming". Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours. Set Password type to WPA personal. Set Configuration to Automatic configuration (DHCP). I don't use WEP yet, but if you do, you may have to enter your password in Network password.

---

