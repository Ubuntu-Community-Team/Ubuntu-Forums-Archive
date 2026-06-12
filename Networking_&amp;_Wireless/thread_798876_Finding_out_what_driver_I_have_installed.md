---
title: "Finding out what driver I have installed?"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by ConMan318 on 2008-05-18
I've been trying to connect to my home wireless network for a while now, and I think my last remaining problem is figuring out what driver I have installed.  I don't really know anything about wireless with Linux, so sorry if these questions seem stupid, and yes, I have searched these forums for answers but couldn't find any that helped me.

I have never manually installed a driver, since I assume mine is recognized by ubuntu, since **sudo iwlist eth1 scan** picks up wireless networks.

So I have been following the sticky and have gotten to this part in the WPA connection:

```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo wpa_supplicant -w -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf -dd 
sudo ifconfig <interface> up
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

It's that third command that gets me, as I don't know what driver to replace the <****see footer below***> part.  The footer says to do **man wpa_supplicant** but that just gives a long list of possible driver extensions that work with the -D tag.

So how do I know which one to put in there?  I have tried putting in a couple of the ones in the man page in after that tag but none of them worked: they either sent it into an endless loop, paused a very long time, or gave an error message.

Also, I know my wireless is WPA, but I don't know if I should use WPA(1) WPA(2).  I assumed WPA(1), so I am following those instructions.  Is there a way to figure out which one my wireless is broadcasting on?

Thanks in advance.

---

### Post by nicedude on 2008-05-18
None of that should be needed if your driver is installed for your wifi card and it is ready to work as the settings can be set in network-manager or if that doesn't work good enough for you then you can use WICD software to manage your wireless & wired network ( Although its not in the repositories by default so you will need to google "wicd ubuntu" to find a link to how to add it to your repository sources so you can install it. Either way one of the network managers should handle the configuration for you and all you need is to enter the settings.

As far as how to test what type of encryption your wireless uses it is quite easy if you own the router that is broadcasting the signal to just plug and ethenet cable into your PC and the router then open firefox or whatever web browser you use and enter the address to log on to the router for configuration ( I will list some common ones below ) but you will also need to know your admin password to log in. If you don't administrate your networks wifi router I would suggest you contact the admin as they can provide you with the proper settings to allow you to connect.

Common router administration log on IP addresses
192.168.0.1
192.168.1.1
192.168.15.1

It will probably be one of those ( If not look on the router and see if it is on it somewhere ) and if you have never changed your routers password ( Which is vital and the equivalent of leaving your front door unlocked ) then it will be either password or admin most likely.

Good luck and feel free to PM me if you can't make any progress on your situation.

---

### Post by ConMan318 on 2008-05-18
Well I installed WICD, and I tried to connect with it, so I entered in my password and hit connect under the correct network name, and it grayed out.  I had to force a quit and it hasn't started up since.  Trying to open the program elicits no reponse.

I have figured out the encryption part, all I really need now is how to figure out what to put after the -D tag, or a different command to connect to a network that my wireless card is picking up.

Any other suggestions in the command line route?  All the GUI ways seem to be failing me.

---

### Post by nicedude on 2008-05-18
No one here will be able to diagnose problems if they dont know what hardware in question is since wireless adapters and their respective drivers & problems vary greatly. So for starters try listing your brand of laptop and model number with series if possible i.e mine is a Acer Aspire 5520-5716 and with that I or others can figure out exactly what wifi chipset you have. Also run the commands below and post the results here as they will help me and others see what is installed hardware wise. 

Basically though it sounds to me like you may not have the correct driver installed for your card or it just isn't configured correctly. For 99% of people just wanting to connect to the internet via their ISP they never need the command line, this is really only needed for advanced topics like mac spoofing and changing wifi modes etc.

Please also try to say what version of Ubuntu you are using and what you have done so far. I will subscribe to this thread and check back in a little while to see what your situation is and try to help you solve it.
Command to list PCI devices post this commands output
lspci

and also this one - command to list wireless network adapters
iwconfig

Also be sure to post the other system info and what your using and have done.

nicedude

---

### Post by ConMan318 on 2008-05-18
Well I have a Dell XPS M1210, and I am using Hardy right now. And thank you very much for helping me with this.

```

connor@connor-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

```

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"LessWired"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=88/100  Signal level=-40 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
^"LessWired" is my home network.

I've looked at my parts on Dell's site, and it looks like my wireless card is:
CARD (CIRCUIT)..., WIRELESS..., MINICARD..., DW1390, BROADCOM CORPORATION...

So I guess it's a Broadcom DW1390.  I just assumed I didn't need to install anything since my wireless card is picking up networks without me having to do anything.

---

### Post by nicedude on 2008-05-20
Try the link below conman as it is related to exactly your car post #6 there gives some sensible commands to try and you might also heed their advice of starting off using no encryption then when that works turn on wep and try to use it.

[http://ubuntuforums.org/showthread.php?t=309653&highlight=Broadcom+DW1390](http://ubuntuforums.org/showthread.php?t=309653&highlight=Broadcom+DW1390)

I am sorry I didn't look here for a day so if that post doesn't get you going then PM me by clicking my name and selecting "send private message" as that way I wont miss that you still need help and I will try to help you further but from your lspci and iwconfig I see no problems for you as your wifi seems to be detected and in your iwconfig shows no dropped or lost packets so I think your problem could be solved via reading the above thread as the fella there solved his problem with the same card by following the advice he got there. If you don't solve yours though please dont hessitate to PM me and if you do please PM me that you did so I will know that you are good to go.


Later and good luck,
nicedude

---

### Post by Ayuthia on 2008-05-20
> **ConMan318 said:**
> Well I have a Dell XPS M1210, and I am using Hardy right now. And thank you very much for helping me with this.

```

connor@connor-laptop:~$ lspci
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

```

I've looked at my parts on Dell's site, and it looks like my wireless card is:
CARD (CIRCUIT)..., WIRELESS..., MINICARD..., DW1390, BROADCOM CORPORATION...

So I guess it's a Broadcom DW1390.  I just assumed I didn't need to install anything since my wireless card is picking up networks without me having to do anything.

You definitely have a Broadcom wireless card.  You will hear it as the 4311 rev 01 in this fourm.  Here is a snip from the man wpa_supplicant page:
[QUOTE]AVAILABLE DRIVERS
       The available drivers to specify with the -D option are:

       hostap (default) Host AP driver (Intersil Prism2/2.5/3).  (this can also be used with Linuxant DriverLoader).

       hermes Agere Systems Inc. driver (Hermes-I/Hermes-II).

       madwifi
              MADWIFI 802.11 support (Atheros, etc.).

       atmel  ATMEL AT76C5XXx (USB, PCMCIA).

       wext   Linux wireless extensions (generic).

       ndiswrapper
              Linux ndiswrapper.

       broadcom
              Broadcom wl.o driver.

       ipw    Intel ipw2100/2200 driver.

       wired  wpa_supplicant wired Ethernet driver

       bsd    BSD 802.11 support (Atheros, etc.).

       ndis   Windows NDIS driver.
[/CODE]
You will probably want to either try broadcom or wext.

You card normally does not want to work right out of the box because it is missing firmware.  However you are picking up signals which means something was already done.  If for some reason you cannot connect still, you might want to remove the encryption and test to see if you can connect.  Once you are able to connect you can then go with encryption.

---

