---
title: "A little wifi help, please!"
date: 2005-08-07
forum: Networking &amp; Wireless
---

### Post by c-m on 2005-08-07
I'm trying to set up my linux box with a Netgear MA101 USB wireless adapter.

I have found out that this particular card uses the atmel chipset and a little search found this [http://atmelwlandriver.sourceforge.net/downloads.html](http://atmelwlandriver.sourceforge.net/downloads.html)

It is crucial that i get wireless working since that is the only connection this PC will use.

Can anyone guide me through what exactly i need to do here in order to install this, and have the card up and running?

Thank You,

---

### Post by PeP on 2005-08-07
[QUOTE=c-m]I'm trying to set up my linux box with a Netgear MA101 USB wireless adapter.

I have found out that this particular card uses the atmel chipset and a little search found this [http://atmelwlandriver.sourceforge.net/downloads.html](http://atmelwlandriver.sourceforge.net/downloads.html)

It is crucial that i get wireless working since that is the only connection this PC will use.

Can anyone guide me through what exactly i need to do here in order to install this, and have the card up and running?

Thank You,[/QUOTE]
 yes follow the instructions here:

[http://atmelwlandriver.sourceforge.net/howto/howto.html](http://atmelwlandriver.sourceforge.net/howto/howto.html)

---

### Post by c-m on 2005-08-07
[QUOTE=PeP]yes follow the instructions here:

[http://atmelwlandriver.sourceforge.net/howto/howto.html](http://atmelwlandriver.sourceforge.net/howto/howto.html)[/QUOTE]
 cheers i'll give that a whirl, no doubt i'll be back for help though. ;-P

Does ubuntu follow linux standards in the same way as red hat, or am i likely to run into differences in terms of directories, filenames and where things are stored?

---

### Post by PeP on 2005-08-08
they are som little differences in directories, filename ... 
you will face it when it comes to network configuration: once the driver is installed and loaded (/sbin/ifconfig shows the network interface) be sure to follow a debian or ubuntu howto

---

### Post by c-m on 2005-08-15
i've now come to do this and have run into trouble. I am following this guide here:
[http://at76c503a.berlios.de/support.html](http://at76c503a.berlios.de/support.html)

I have downloaded the CVS snapshot (since its the only one that works with 2.6 kernels), i have the kernel headers and build essentials and have compiled the driver and ran "make install"

but i didn't understand the part of the guide where it says Installing the Driver and just says "find /lib/modules/`uname -r`/ -name "usbvnet[5r]*" -exec rm {} \;"  what does this mean i have to do?

i also have no understanding of the second part.....
> Starting the device

Plugin your USB device and watch the syslog. If the hotplug package is installed and your USB device's ids are known to the driver, hotplug should load the correct driver. You'll see some lines like

         usbdfu.c: USB Device Firmware Upgrade (DFU) handler v0.11beta4-ac1
         at76c503.c: Generic Atmel at76c503/at76c505 routines v0.11beta4-ac1
         at76c503-rfmd.c: Atmel at76c503 (RFMD) Wireless LAN Driver v0.11beta4-ac1
         ...
         at76c503.c: $Id: at76c503.c,v 1.35 2003/07/30 06:31:51 jal2 Exp $ compiled Sep  2 2003 12:42:49
         at76c503.c: firmware version 1.101.5 #84 (fcs_len 4)
         at76c503.c: device's MAC 00:08:a1:42:9c:d9, regulatory domain ETSI (Europe - (Spain+France) (id 48)
         at76c503.c: registered wlan0

If all you get is something like

         usb.c: USB device ... (vend/prod xxx/yyy) is not claimed by any active driver.
    

grep for the USB ids (xxx,yyy) in the source C files. If you find the pair, manually load the corresponding driver (at76c503-rfmd, at76c503-rmfd-acc, at76c503-i3861, at76c503-i3863, at76c505-rfmd,at76c505-rfmd2958), e.g. by

modprobe -v at76c503-rfmd
       

what is it talking about with hotplug, syslog and grep.


I know there are people on these boards who have successfully installed this adaptor, some even from this very guide. Can someone please help me on this?

---

### Post by c-m on 2005-08-16
this is getting absolutely ridiculous now. its been over a week since i installed Ubuntu and i still have absolutley no wireless networking capeabilities.

I have installed everything to do with atmel that i could find in the repository.

ifconfig produces the following:

> 
wlan0     Link encap:Ethernet  HWaddr 00:09:5B:0C:86:ED
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe0c:86ed/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



iwconfig produces:

> 
wlan0     IEEE 802.11-DS  ESSID:"belkin"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




lsusb produces:

> 
Bus 001 Device 004: ID 0864:4102 NetGear, Inc. MA101 802.11b Adapter



Now can anyone at all help me? also can anyone recommend any usb wireless cards that play nice with linux?

---

### Post by varunus on 2005-08-16
From that output, it looks like your card is working...but not finding access points...Can you try typing in:
```
sudo iwconfig wlan0 essid <SSID of router>"
sudo dhclient wlan0
```

and see if that gets you net access?  Or does dhclient time out?

---

### Post by c-m on 2005-08-16
[QUOTE=varunus]From that output, it looks like your card is working...but not finding access points...Can you try typing in:
```
sudo iwconfig wlan0 essid <SSID of router>"
sudo dhclient wlan0
```

and see if that gets you net access?  Or does dhclient time out?[/QUOTE]
 what is SSID is the that the name i gave to the router?

it should be able to find a signal. Right now i have a windows box sitting on top of my linux box. the windows box is running the exact same usb wireless card and that finds the rounter fine. the linux box is currently connecting to the internet through the windows box untill i can get this wireless sorted.

sudo dhclient wlan0:

> 
carl@carl:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:09:5b:0c:86:ed
Sending on   LPF/wlan0/00:09:5b:0c:86:ed
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11


that list just kept going on and on untill i pressed CTL+C to stop it.

---

### Post by crispingatiesa on 2005-08-16
If U haven't modify Ur router the essid of the router yould be "Default"

---

### Post by c-m on 2005-08-16
[QUOTE=crispingatiesa]If U haven't modify Ur router the essid of the router yould be "Default"[/QUOTE]
 nah just checked the ESSID is "belkin"  I should mention that the router currently is using 64bit WEP, so that will need to be set on this connection too for it to work i imagine. I don't know how to do thisin linux though.

---

### Post by crispingatiesa on 2005-08-16
Ok, seems to be a problem of configuration.

I'm not in my Ubuntu box now, so, I cannot give you detailed instrucctions.

But, you should go to the network manager and configure the adaptor with that essid. (Don't stop the router from broadcasting the essid because I don't know way (even entering manually the ssid) if you do that you have problems with Ubuntu)

You should be able to configure wep as well. I cannot help you with this because I'm not certain if the wep in use in Ububtu is 64 or 128bit. I tried with a linksys router and I got into problems.

I'll also advice you if possible to tell your router to assign a fixed IP based on the mac address of the adaptor and to enter the assigned IP in the adaptor configuration in UBuntu (using the network configuration tool); this way you'll avoid any headache associated with DHCP

If you cannot fixed, when I get home I'll be able to be more specific. So, I'll be back to you

---

### Post by c-m on 2005-08-16
wooohooo its finally working, i've had to turn off WEP though, which i initially turned on because i noticed a device call Acer on our client list, we don't have any acer equiment in the house.

Cheers for all the help, i can now finally turn off this damn windows machine next to me, which incidentally crashed when i changed the router/network settings.

I notcied though that it says signal strength is 0% and there is no mesurement of singal quality. Is there any program that shows these? the reason i ask is that its important for me know the if i lose conectivity whether its because the signal is weak etc.. due to weather. My pc is based in the garage which is a fat distance from the router.

---

### Post by c-m on 2005-08-17
[QUOTE=c-m]wooohooo its finally working, i've had to turn off WEP though, which i initially turned on because i noticed a device call Acer on our client list, we don't have any acer equiment in the house.

Cheers for all the help, i can now finally turn off this damn windows machine next to me, which incidentally crashed when i changed the router/network settings.

I notcied though that it says signal strength is 0% and there is no mesurement of singal quality. Is there any program that shows these? the reason i ask is that its important for me know the if i lose conectivity whether its because the signal is weak etc.. due to weather. My pc is based in the garage which is a fat distance from the router.[/QUOTE]
 ah It seems i jumped the gun celebrating yesterday. While i can access the internet from the wifi card in ubuntu, I have a strange problem.

At first the card worked flawlessly, however when i next came to use the computer i could not connect to any websites. amule was still connected and downloading and i could ping the router and other computers on the network but nothing else could connect, not even that weather module in gnome.

Now i plugged the card (without moving it) back into the windows machine and used that as gateway for the linux box. This then gave me internet access again. All is fine i though, so i plugged the card back into my linux box and it worked just as it did the first time. After a while though, the problem happened again. I had connection but absolutly no internet access. I have just had to plug it back into the windows machine to write this message.

Has anyone else experienced this and/or know how to solve it?

---

### Post by EpiLePTiC FaiRY on 2005-08-17
[QUOTE=c-m]ah It seems i jumped the gun celebrating yesterday. While i can access the internet from the wifi card in ubuntu, I have a strange problem.

At first the card worked flawlessly, however when i next came to use the computer i could not connect to any websites. amule was still connected and downloading and i could ping the router and other computers on the network but nothing else could connect, not even that weather module in gnome.

Now i plugged the card (without moving it) back into the windows machine and used that as gateway for the linux box. This then gave me internet access again. All is fine i though, so i plugged the card back into my linux box and it worked just as it did the first time. After a while though, the problem happened again. I had connection but absolutly no internet access. I have just had to plug it back into the windows machine to write this message.

Has anyone else experienced this and/or know how to solve it?[/QUOTE]

It could be the DHCP lease expiring with the router and your Linux not retrieving a new one until you force the wireless to reconnect. Next time it happens try:
/etc/init.d/networking restart
or the dhclient wlan0 command someone else mentioned here. See if that fixes it for us.

---

### Post by c-m on 2005-08-18
[QUOTE=EpiLePTiC FaiRY]It could be the DHCP lease expiring with the router and your Linux not retrieving a new one until you force the wireless to reconnect. Next time it happens try:
/etc/init.d/networking restart
or the dhclient wlan0 command someone else mentioned here. See if that fixes it for us.[/QUOTE]
 sorted now, it was nothing to do with the lease. I maunually entered my ISP (blueyonder) DNS servers in and its working fine now. Problem is its not retaining the DNS server address and i have re-type it in every so often.

Still its strange how the XP machine doesn't need me to do this.

---

