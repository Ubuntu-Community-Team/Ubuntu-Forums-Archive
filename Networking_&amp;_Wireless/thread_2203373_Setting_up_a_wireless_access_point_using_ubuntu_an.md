---
title: "Setting up a wireless access point using ubuntu and Edimax EW-7711USn"
date: 2014-02-03
forum: Networking &amp; Wireless
---

### Post by michael103 on 2014-02-03
Hi all this is my first post, and although im not a complete idiot i am close to it so forgive my ignorance. 

The task: To create a wireless acess point using ubuntu server and the Edimax EW-7711USn, on the device Acer Veriton N281G.

Though i have seen a similar thread on the site i was unable to fully understand the process. 
This is how i understand it...

1) install the Edimax drivers to run the device, is that as simple as a wget command?

2) When the drivers are downloaded i need to install them. is that the unzip command?

3) then need to black list the original network interface card? rfkill command?

Then im a bit lost as to what to do next, if its possible could please point out anything im missing and what other steps might be need doing?

Im not sure what to post in regards to system output but this is what ive checked so far

_**iwconfig**_

wlan   IEE 802.11bgn ESSID:off/any   
         Mode: Managed  Access Point: Not Associated   Tx-Power=0 dBm
         Retry Long limit:7 RTS thr:off  Fragment thr:off
         Power Management:off

lo      no wiresless extensions

eth0  no wiresless extensions[U][B]

lsusb[/B][/U]

Bus 002 Device 002: ID 0461:0010 Primax Electronics, LTD
Bus 003 Device 003: ID 046d:c077 logitech, INC
Bus 001 Device 001: ID 1d6b:0002 linux foundation 2.0 root hub ( same for Bus 002, Bus 003, Bus 004, Bus 005)

Any advise and or tips would be greatly welcome.

Kind Regards Mike

---

### Post by howefield on 2014-02-03
Hello and welcome to the forums.

Thread moved to the "Networking and Wireless" forum, where you'll have more likelihood of getting help.

---

### Post by michael103 on 2014-02-03
Thank you, i wasnt sure if this was a complete beginners question or a network one....not a great start :S

---

### Post by westie457 on 2014-02-03
Welcome to UF.

> [COLOR=#000000]1) install the Edimax drivers to run the device, is that as simple as a wget command?[/COLOR]

[COLOR=#000000]2) When the drivers are downloaded i need to install them. is that the unzip command?[/COLOR]

Just plug it in, should work out of the box. I have a similar dongle that is supported since 10.10 (Maverick Meercat).

> [COLOR=#000000]3) then need to black list the original network interface card? rfkill command?[/COLOR]


If the original NIC is ethernet via cable - disconnect the cable. If it is a Wi-fi chip we need to know which one it is.
Not 100% percent sure the 'rfkill' command will turn off the on board chip.

Open a terminal (Ctrl+Alt+T) is the quick way and run this command.

```
sudo lshw -C network
``` should show us something about all your NIC's. Post the output of the above command in 'code' tags.
Highlight the text in the terminal and in 'Advanced Reply' click on the # symbol at the top of the message window, paste between the brackets that look like this
[code]

This is a start.

---

### Post by michael103 on 2014-02-03
Thanks for your responses, im currently trying to get this working in  ubuntu server and im asking question via my mac so im having to write  out the output to these commands. 

So after running the command i got the following output.

```

*- network DISABLED
        desription: wireless interace
        production: RT3090 Wireless 802.11n 1T/1r PCIe
        vendor: Ralink corp
        physical id: 0
        bus info: pci@0000:02:00:0
        logical name: wlan0
        version: 00
        Serial: 9c:b7:0d:89:e2:e9
        width: 32bits
        clock: 33mhz
        capabilities: pm msi pciexpress bus master cap_list ethernet physical wireless
        configuration: broadcast=yes driverrt2800pci driverversion=3.8.0-35-generic firmware=N/A latency=0 link=no multicast=yes
wireless=IEE 802.11bgn
        resources: irq:18 memory:feaf0000-feafffff
*- network 
        desription: ethernet interace
        production: RTL8111/8168B PCI express gigabit Ethernet controller
        vendor: Realtech Semiconductor Co., LTD
        physical id: 0
        bus info: pci@0000:03:00:0
        logical name: eth0
        version: 06
        Serial: d0:27:88:bb:90:7f
        size: 100Mbit/s
        capacity: 1Gbit/s
        width: 64 bits
        clock: 33mhz
         capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet  physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
        configuration: autonegotiation= on  broadcast=yes driver=r8169 driver version=2.3lk-NAPI duplex=full  firmware=rtl_nic/rtl816 8e-2.fw ip=10.0.4.29 latency=0 link=yes  multicast=yes port=MII speed=100Mbit/s
        resources: irq:43 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff

```

---

### Post by nothingspecial on 2014-02-03
> **michael103 said:**
> Thanks for your responses, im currently trying to get this working in  ubuntu server and im asking question via my mac so im having to write  out the output to these commands. 



If you have a wired coonection to your server you can browse the forums and ask questions with a text browser eg elinks

If you have no networking at all you can  redirect the output to a file and copy it to a usb stick, much easier

eg ```
sudo lshw -C network > lshw.txt
```

The output is then in a file called lshw.txt because > puts it there instead of printing it on the screen

---

### Post by westie457 on 2014-02-03
@ nothingspecial
Thanks for joining in with hints and tips.
This might get beyond me quickly as I am not very good with the command line and have no clue about servers.

@ michael103
Carrying on with info gathering.
With the dongle plugged in the output of ```
rfkill list all > rfkill.txt
nm-tool > nm-tool.txt
```
A quick reboot of the server might be needed just to kick the dongle into life if the wifi is listed as unavailable in the nm-tool command.

Thank you for allowing me to learn some new stuff.

---

### Post by 3rdalbum on 2014-02-03
Hi Michael,

If you're new to Linux, you are REALLY jumping in the deep end by starting with Ubuntu Server. You may be under the impression that only Ubuntu Server can run server software or that it is more "tailor-made" for it. That's not really true. Ubuntu Server is just Ubuntu Desktop, minus the GUI. Ubuntu Desktop is Ubuntu Server, plus a GUI.

You can install the desktop GUI by running:

```
sudo apt-get install ubuntu-desktop
```

With the desktop running, you can set up an AP with a couple of mouseclicks in Network Manager. No need for the terminal at all.

---

### Post by michael103 on 2014-02-03
Thanks again people, i bricked my installation on my box so i had to flattern it and start fresh. 
Im using Ubuntu server as i believe that with server i have a more stable platform. Also not having a gui will improve the system performance.

I did think i was jumping the gun but im fairly computer literate so i thought id be fine lol!

all attempts to install the drivers failed not sure why but im now  asking you guys n girls for some step by step instructions in creating a wireless access  point or maybe point be some helpfull reading material.

So I was using 12.04 server, now im using 13.10 server on my new installation. Could i in theory install the GUI setup on the 13.10 server and then setup a Wireless access point through the GUI then remove the gui and have it work like that?

Sorry for the stupid question/s

---

### Post by westie457 on 2014-02-03
Plug in the dongle, run the command posted by 3rdalbum. Reboot the system and see if the dongle is working.

Working or not come back here for more help.

---

### Post by chili555 on 2014-02-03
Why do you think you need to install drivers? Doesn't your device spring to life if you just insert it? You may have to unload the driver for the internal device:```
sudo modprobe -r rt2800pci
```In order to use a wireless device as an access point, it must be able to go into Master mode. Sometimes, you can coax it using ad-hoc. The first step is to see if your card and driver combination can do so:```
sudo iwconfig wlan0 mode master  [COLOR="#FF0000"]<--or wlan1, whatever the USB uses[/COLOR]
iwconfig
```Or try:```
sudo iwconfig wlan0 mode ad-hoc
iwconfig
```If the card and driver combination won't go, then you should look for a driver that does. We'll help you install it. Failing that, then you simply have the wrong tool for the job. You can hardly ever drive a nail with a screwdriver.

Then I suggest you check here: [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)  Bear in mind, you are using the ethernet for incoming and wireless for outgoing. Adjust these instructions accordingly.

I have never done such a thing, so you are just about at the end of my knowledge. Frankly, if I wanted a wireless access point, I'd check Ebay. I see them for $5-10. Slap some DD-WRT on it and be all set.

---

### Post by michael103 on 2014-02-04
So after much fiddling i have found out that it doesnt support master mode so thats particular aspect is out the question. Thanks for your respones though

So i still want to create a wireless access point but now through a router connected to my ubuntu server.  I want the router to load all my images
from my EyeFi card through the wireless router onto my ubuntu server

This is my goal step by step 

1) Using a Acer veriton or someting like that, create a ubuntu server that will save and send images from an EyeFi card to the server (i have installed 13.10 server on my device)

2) The ubuntu server (acer veriton) will be connected to a Buffalo Air station that will be used for its WiFi capabilities which will send the images to my ubuntu server for storing

To me this sounds simple but as im not well versed in ubuntu and not sure on its implementation

Sorry if this is a repeat but i just seems like this kind of thing should be easy, any help would be greatly appriecated!

Kind regards Mike

---

