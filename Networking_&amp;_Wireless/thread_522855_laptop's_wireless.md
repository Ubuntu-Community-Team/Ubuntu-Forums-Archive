---
title: "laptop's wireless"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by Jaristr on 2007-08-11
Hi, 

I have HP nx7400 laptop and I tried to run kubuntu 7.04 from the CD but after the desktop loaded and started it did not connect to the wireless network. I tried setting manually the password and EESID but it didnt help, the network remained disables.
So I'm mainly posting to ask for help in finding out what went wrong/fails?

Thanks!

---

### Post by Jamie Jackson on 2007-08-12
If ```
lspci | egrep -i '(broad|wireless)'
``` doesn't turn up anything, please give the output of ```
lspci
```

---

### Post by Jaristr on 2007-08-17
Hi!

The lspci command shows this line for the wireless:

```
10:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
```

I had to type that from the output to here, so I hope it came out correctly. Thanks for helping me.

---

### Post by Jamie Jackson on 2007-08-17
> **Jaristr said:**
> Hi!

The lspci command shows this line for the wireless:

```
10:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
```

I had to type that from the output to here, so I hope it came out correctly. Thanks for helping me.

I was hoping that would be the output. Come on over [here]("http://ubuntuforums.org/showthread.php?t=475963").

---

### Post by Jaristr on 2007-08-20
Thank you! The wireless started working after installing the drivers according to those instructions.
However, I don't understand why the wireless doesn't work anymore. It's almost like the KNetwork manager had locked the settings to manual which doesnt work.
But it did work first, but not today anymore.
Is there some way to reset the KNetwork manager? It doesnt show the wireless networks anymore.
Thanks.

---

### Post by Jamie Jackson on 2007-08-20
Please report the output of the following:

sudo cat /etc/network/interfaces
sudo cat /etc/modules
modprobe -l | grep ndiswrapper

---

### Post by Jaristr on 2007-08-20
Ok here comes the output of those thee command lines:

$ sudo cat /etc/network/interfaces

```



auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth1 inet dhcp
wireless-essid HSMC



auto eth1




```

$ sudo cat /etc/modules

```


# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper


```

$ modprobe -l | grep ndiswrapper

```



/lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko


```

---

### Post by Jamie Jackson on 2007-08-20
> **Jaristr said:**
> Ok here comes the output of those thee command lines:

$ sudo cat /etc/network/interfaces

```



auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth1 inet dhcp
wireless-essid HSMC



auto eth1

```
Hmm, either you missed some steps, or something/someone else stomped on the configuration.

Run the following lines, one at a time:
```

sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo /etc/dbus-1/event.d/25NetworkManager restart

```

When you're done, you'll only have two lines in the /etc/network/interfaces file.

If that doesn't get you going again, post back.

---

### Post by Jaristr on 2007-08-21
Thank you, the wireless networks are visible again! But I am unable to connect to my network where I used to connect from winXP. It's strange because I have typed the password ten times and tested different protocols. Even it should be WPA, I tried WPA 2 as well.

---

### Post by Jaristr on 2007-08-21
In addition I can say that when it triest to connect the KNetwork manager first shows "Link up" then "IP configuration started" at 57% . This happens only with WPA2 , the WPA one and two are both supported by the router but only WPA2 gets that far.

---

### Post by Jamie Jackson on 2007-08-21
If you already have the following file, and it contains the following line, don't do the following. However, if you don't have that file, then do run it.

Edit: If, in the past, you did anything to try to enable wpa, please undo it, as this simple step is the only thing you need to enable it. Anything else might get in the way...

```

#create a file and add "ENABLED=0" to it
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
#restart networkmanager
sudo /etc/dbus-1/event.d/25NetworkManager restart
```

---

### Post by Jaristr on 2007-08-22
Ok thank you. I now have the file with the line "ENABLED=0".
Still it gets to the "link up" when I type the password in the prompt and select WPA2, but doesn't go futher from 57%, actually it asks the password again.
But its so simple and Im going to recheck it once more, and post back if that was the issue.

Edit: The password should be ok because I connected from windows to the same network.

---

### Post by Jamie Jackson on 2007-08-22
Well, if nobody else has any input, you could try [installing the backported native driver]("http://ubuntuforums.org/showpost.php?p=3230991&postcount=16"). You'd still be able to use NetworkManager.

---

### Post by Jaristr on 2007-08-22
Ok, thank you. But strange that it worked, twice. first when ran from CD and after installed, it was able to connect and I was able to use the net.
well maybe it helps to install the driver again and I try to delete/reset any KNetwork manager settings etc.

---

### Post by kevdog on 2007-08-22
I know Im jumping in the post late, but just for a summary for me can you post
lshw -C network
/etc/modprobe.d/blacklist
iwlist scan

Basically you are having a problem using bcm43xx drivers connecting to your router with WPA2 encryption??  Can you connect with no encryption of or WPA1?  Have you tried connecting manually -- not with knetworkmanager?

---

### Post by Jamie Jackson on 2007-08-22
> **Jaristr said:**
> Ok, thank you. But strange that it worked, twice. first when ran from CD and after installed, it was able to connect and I was able to use the net.
well maybe it helps to install the driver again and I try to delete/reset any KNetwork manager settings etc.

Wait, are you saying you were able to hit the 'net with an "out of the box installation" (without having to do any extra configuration whatsoever)?

Are you running Gutsy?

---

### Post by Jaristr on 2007-08-23
> **Jamie Jackson said:**
> Wait, are you saying you were able to hit the 'net with an "out of the box installation" (without having to do any extra configuration whatsoever)?

Are you running Gutsy?

No no. :) I followed the driver installation instructions while running from the CD and the wireless worked after reloading. Then I installed them permanetely after installing the kubuntu itself, to HD.
And I have kubuntu 7.04.

---

### Post by Jaristr on 2007-08-23
> **kevdog said:**
> I know Im jumping in the post late, but just for a summary for me can you post
lshw -C network
/etc/modprobe.d/blacklist
iwlist scan

Basically you are having a problem using bcm43xx drivers connecting to your router with WPA2 encryption??  Can you connect with no encryption of or WPA1?  Have you tried connecting manually -- not with knetworkmanager?

Hi, thanks for those three command, looks valid info from their output. the bcm43xx is in the blacklist however, but I suppose this is intent.

I tried connecting to unencrypted network but that didnt work.
How can I connect manually without KNetwork manager?

---

### Post by Jamie Jackson on 2007-08-23
Hi Jaristr,

Could you post the output from those commands? There might be something subtle lurking in the output.

---

### Post by Jaristr on 2007-08-23
Ok, here's the output of all three.


 lshw -C network


```



WARNING: you should run this program as super-user.
  *-network
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@10:00.0
       logical name: eth1
       version: 01
       serial: 00:14:a5:d8:74:a9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Broadcom,03/23/2006, 4.40.19.0 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:f4000000-f4003fff irq:17
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@02:0e.0
       logical name: eth0
       version: 02
       serial: 00:17:08:43:18:ea
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.2.101 latency=64 multicast=yes
       resources: iomemory:f4108000-f4109fff irq:16



```




iwlist scan



```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:02:CF:4E:E6:E6
                    ESSID:"ZyXEL"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:13:F7:4E:FA:01
                    ESSID:"HSMC"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-28 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:16:B6:C1:4F:F4
                    ESSID:"linksys_SES_60352"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:13:D3:7A:33:49
                    ESSID:"jr-ap"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

(HSMC is the network where I try to connect)



sudo cat /etc/modprobe.d/blacklist


```



# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
blacklist bcm43xx



```

---

### Post by Jaristr on 2007-08-25
Ok, I went through the driver installation again but it did not seem to make difference. 
The thing is that I can connect without encryption! But not to my own network that requires WPA2...

---

### Post by kevdog on 2007-08-25
Ok, dont give up hope yet.

Lets just check a few things before proceeding -- its good news that you can at least connect to an unencrypted network.


Make sure you have the wpa supplicant package installed:
```
sudo aptitude install wpasupplicant
```

And please post
lshw -C network
ndiswrapper -v
ndiswrapper -l
iwlist scan

Thanks

---

### Post by Jaristr on 2007-08-25
> **kevdog said:**
> Ok, dont give up hope yet.

Lets just check a few things before proceeding -- its good news that you can at least connect to an unencrypted network.


Make sure you have the wpa supplicant package installed:
```
sudo aptitude install wpasupplicant
```

And please post
lshw -C network
ndiswrapper -v
ndiswrapper -l
iwlist scan

Thanks

I just posted "lshw -C network" and "iwlist scan", they are on the previous page of the thread. 
I can post rest once I make sure wpasupplicant is installed. :)

---

### Post by bdoe on 2007-08-25
I don't know a whole lot about WPA, having been a WEP holdout for so long, but something seems fishy with your WPA encryption technique:
```
IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
```
particularly the CCMP part.  It seems to me that if you're using TKIP encryption, the pairwise ciphers should be TKIP as well...

---

### Post by kevdog on 2007-08-25
bdoe

Where did you get that information you posted ... is that quote contained in this thread??

---

### Post by Jaristr on 2007-08-26
> **bdoe said:**
> I don't know a whole lot about WPA, having been a WEP holdout for so long, but something seems fishy with your WPA encryption technique:

particularly the CCMP part.  It seems to me that if you're using TKIP encryption, the pairwise ciphers should be TKIP as well...

Hmm I dont know much about this either, but this is what I have selected in the wireless setup (for "Cipher suite"):
TKIP + AES (WPA/WPA2)

And "Pre-shared Key"

---

### Post by Jaristr on 2007-08-26
> **kevdog said:**
> bdoe

Where did you get that information you posted ... is that quote contained in this thread??

Yes in the page two, one of the output's I posted.

We may have different forum board settings though.

---

### Post by Jaristr on 2007-08-26
Ok I do have the wpasuplicant installed... 

And here's the output of the command's requested:


ndiswrapper -v


```
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload 586

```

 ndiswrapper -l

```

bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

```

---

### Post by bdoe on 2007-08-26
> **kevdog said:**
> bdoe

Where did you get that information you posted ... is that quote contained in this thread??
Ummm...  [Right here](http://ubuntuforums.org/showthread.php?p=3240004).

---

### Post by kevdog on 2007-08-26
Ok, this thread is moving on at a snails pace.

Few comments
1. You are using ndiswrapper v 1.38.  This probably will work, however its not the advised version.  If the rest of the suggestions dont work, then we will need to upgrade (current ver 1.48)

2. Lets just try to bring your network using wpa2 up by hand.  You wont have to do this everytime, Im just taking each step one and a time to generate some debugging output.

Here is what I want you to do:

Create a wpa_supplicant.conf file
```

gksu gedit /etc/wpa_supplicant.conf

```

Contents of the wpa_supplicant.conf file are the following:
This example is assuming WPA (or in some cases WPA2) with TKIP cipher
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
       ssid="<your networks essid in quotes>"
       scan_ssid=0
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk="<ASCII password in quotes>"
}

```

Find your wireless section, and then look for logical name -- this is your interface name (An example below)
```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **logical name: wlan0**
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```

The following is an example of what to type at the command line to bring up your network with wpa manually.
Assumptions:
1. Interface name is wlan0
2. Wireless driver is ndiswrapper (known as wext).  (See man wpa_supplicant for alternative choices)

A lot of debugging output will be given (the whole purpose of this exercise) 

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo dhclient -r wlan0
sudo killall dhclient wpa_supplicant dhclient3
sudo rm /var/run/dhclient.pid
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

---

### Post by Jaristr on 2007-08-27
Thank you for the instructions, bob. I followed replacing wlan0 with eth1. But it got stuck on this command, when the authentication fails:

sudo wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd    

Eventually , after many lines of debug info, resulted:

```

State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
Authentication with 00:13:f7:4e:fa:01 timed out.
Added BSSID 00:13:f7:4e:fa:01 into blacklist
State: GROUP_HANDSHAKE -> DISCONNECTED

```


I wonder why the connecting doesnt work on linux, and why it works on windows only. Could the router possibly have some setting that rejects linux for some reason? The adapters MAC address and everything should be same right? Not that I would have put any filtering or special security settings.

---

### Post by kevdog on 2007-08-27
Cant say that Ive seen that error either

Can you post your /etc/wpa_supplicant.conf file??

Do you have a working ethernet connection??

---

### Post by Jaristr on 2007-08-27
> **kevdog said:**
> Cant say that Ive seen that error either

Can you post your /etc/wpa_supplicant.conf file??

Do you have a working ethernet connection??

Well the wpa_supplicant.conf is otherwise the same as you posted except that I inserted my own EESID and password as you had quided in there. Or was there some other reason why you wanted to see the contents than making sure I didnt make a mistake? 

I have working ethernet on the eth0 interface.

Thanks for helping.

Please do tell me if there's anything else I can try?

---

### Post by Jaristr on 2007-09-02
Well I got it working using the WEP, but still not with WPA.
I'm glueless what to try next so I will leave this thing here unless some knows what to try.

Thanks for all the help so far though, I apreacite it.

PS. Only one thing, surely the linux cannot depend on 802.1X support?

---

