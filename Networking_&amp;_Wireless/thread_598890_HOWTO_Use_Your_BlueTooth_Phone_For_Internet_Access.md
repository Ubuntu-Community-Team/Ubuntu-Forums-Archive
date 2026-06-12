---
title: "HOWTO: Use Your BlueTooth Phone For Internet Access"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by InfoSec812 on 2007-10-31
So you, or your boss, has got one of those nice new BlueTooth enabled PDA phones. Did you know that you can use it to connect to the Internet wirelessly from anywhere you have cellular service? Here's how.

OK, first off, let's install the appropriate packages. You can use Synaptic, aptitude, or apt-get; as long as you install all of the listed programs:

[LIST]
[*]bluez-utils
[*]bluetooth
[*]bluez-gnome
[*]bluez-hcidump
[/LIST]

Now that all of that is done, let's get down to business. First, you will need to enable the BlueTooth applet in GNOME. Do this by going to "System->Preferences->BlueTooth Preferences". Set the mode of operation on the "Devices" tab to "Other devices can connect". On the "General" tab, set the program to always show the BlueTooth systray applet (personal preference).

Now we need to bind your BlueTooth phone and your computer. From your phone, add a new device and choose the entry for your computer from the list. The look of this will vary from phone to phone, but it should be somewhat simple. You will be asked for a passcode and when you enter it on your phone, the bluetooth applet on GNOME should pop up saying that something is trying to connect. Click on the notice and enter the same passcode on your computer. There, now we have a binding between the devices. If you ever change out your bluetooth adapter on the PC, you will have to do this over.

The last step is a little more difficult, but not too bad. Open a terminal. On the command line, enter the following commands and taking note of the information where asked to.

```
sudo bash

hcitool scan   (Make a note of the hardware address of your phone as listed).
vim /etc/default/bluetooth
```

Find the line which has something like:

```
PAND_ENABLED=0
```

and change it to:

```
PAND_ENABLED=1
```

Next, find the line which looks like:

```
PAND_OPTIONS=""
```

and change that to:

```
PAND_OPTIONS="--listen --role=PANU --devup /etc/bluetooth/pan/dev-up --devdown /etc/bluetooth/pan/dev-down"

```

Save the file.

Now, create a directory called "/etc/bluetooth/pan". Use an editor to create a file called "/etc/bluetooth/pan/dev-up" and put the following lines into that file:

```
#!/bin/bash
ifup bnep0
```

Save that file. Now, use a text editor to create another file called "/etc/bluetooth/pan/dev-down" and put the following lines into it:

```
#!/bin/bash
ifdown bnep0
```

Save that file as well. Finally, we need to add a line to /etc/network/interfaces. Open that file with a text editor (as root) and add the following line to it near the end:

```
iface bnep0 inet dhcp
```

Almost done. The last thing to do is start up the Internet Sharing on your phone and connect from your PC. The Internet Sharing on your phone is going to be different depending on the phone, but on the Linux client, use the following command:

```
pand --connect <Phone Hardware Address>.
```

That's it. You should see the bnep0 interface come up and get a DHCP address from your phone. After you have the address, you can freely browse the Internet.

To disconnect, simply run:

```
sudo pand -K
```

Remember, any time you want to connect or disconnect, you must run the "pand" commands as root. Just so you know, I'm using my HTC 8525 Windows Mobile 5 phone from AT&T right now to post this to the forum. I hope you find this useful and please feel free to leave your comments!!!

---

### Post by tech0007 on 2007-11-17
Great HOWTO!  This 'just works' on my laptop!

Do you know how to make a bluetooth-enabled phone access the internet through Gutsy?  That would be nice!

---

### Post by jeckman on 2007-11-29
This is no longer working for me under Kubuntu Gutsy. Used to work fine under Feisty. 

Any ideas what to check?

I can see the phone (cingular blackjack) and pair with it. It seems that the pand --connect fails, since the phone is stuck in "Device setup finished. On the PC, connect Bluetooth PAN"

hcitool scan shows the phone and the correct address.

When I'm working on trying this, I get this stuff in /var/log/syslog:

Nov 29 11:08:23 jeckman-ubuntu pand[7164]: Bluetooth PAN daemon version 3.19
Nov 29 11:08:23 jeckman-ubuntu pand[7164]: Connecting to 00:18:AF:A2:30:B5
Nov 29 11:08:23 jeckman-ubuntu NetworkManager: <debug> [1196352503.361318] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_2101_0002720221E1_if0_bluetooth_hci_bluetooth_hci').
Nov 29 11:08:27 jeckman-ubuntu kernel: [  434.348000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 12
Nov 29 11:08:27 jeckman-ubuntu kernel: [  434.504000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 12
Nov 29 11:08:27 jeckman-ubuntu hcid[6306]: link_key_request (sba=00:02:72:02:21:E1, dba=00:18:AF:A2:30:B5)
Nov 29 11:08:27 jeckman-ubuntu pand[7164]: Connect to 00:18:AF:A2:30:B5 failed. Success(0)


Any ideas to try to troubleshoot what's happening here?

---

### Post by jeckman on 2007-11-29
Actually looks to me like this may be a problem with Network Manager detecting the USB bluetooth dongle Im using:

From syslog:

Nov 29 11:06:22 jeckman-ubuntu NetworkManager: <debug> [1196352382.597068] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_2101_0002720221E1_if
0_bluetooth_hci_bluetooth_hci').


Lots of nm_hal_device_added() and nm_hal_device_removed() entries in debug and syslog. 

According to lsusb:

Bus 003 Device 005: ID 0a5c:2101 Broadcom Corp.

---

### Post by transformania on 2007-12-15
Hmm, yes, seems to work in Feisty, but a no-go in Gutsy.

From what I can tell it connects just fine, but does not attempt to get an ipv4 address under Gutsy...

```
Dec 15 19:25:17 Starscream pand[7065]: Bluetooth PAN daemon version 3.19
Dec 15 19:25:17 Starscream pand[7065]: Connecting to 00:17:83:0D:4F:3D
Dec 15 19:25:17 Starscream NetworkManager: <debug> [1197764717.472631] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if0_bluetooth_hci_bluetooth_hci'). 
Dec 15 19:25:17 Starscream hcid[5651]: link_key_request (sba=00:1C:26:E0:2E:3F, dba=00:17:83:0D:4F:3D)
Dec 15 19:25:17 Starscream pand[7065]: bnep0 connected
Dec 15 19:25:17 Starscream NetworkManager: <debug> [1197764717.942097] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1c_26_e0_2e_3f'). 
Dec 15 19:25:19 Starscream avahi-daemon[5612]: Registering new address record for fe80::21c:26ff:fee0:2e3f on bnep0.*.
```

/etc/network/interfaces contains very little in gutsy compared to feisty.  Actually, it only contains the loopback interface.  So...where is wlan0 and the like now kept?

---

### Post by jeckman on 2007-12-16
I don't think that's the same problem I am having. 

Critically, I never get this line:

Dec 15 19:25:17 Starscream pand[7065]: bnep0 connected

I never get a pand[#] bnep0 connected 

When this used to work under Fiesty, after getting pand connected I was manually issuing the dchpclient bnep0 stuff.

---

### Post by Strider on 2008-01-16
> **InfoSec812 said:**
>  I hope you find this useful and please feel free to leave your comments!!!

Hi,
This worked great on my AT&T Tilt.  Tutorial is very clear and easy to follow.  Thanks! :)

---

### Post by lcohen999 on 2008-04-13
Has anyone gotten this to work with 8.04?

---

### Post by trondhuso on 2008-04-16
It would be great if someone wrote a Python GUI-script so that we got an easy way to connect and disconnect to the phone(s) using this method. 
That would be awesome. 

I'm trying to look into it now, but I am not at all any Python-guy nor do I know how to make a GUI in Linux.

I'm eager to learn C# and so I am looking forward to 8.04 where MonoDevelop 1.0 is being shiped.
-trond-

---

### Post by wilbur.harvey on 2008-06-08
I am using Ubuntu Hardy 8.04 on my MacBook Pro, connecting to a TMobile Dash.

I got it to work following this tutorial, but with a few modifications.

The part about the /etc/bluetood/pan/dev-up and dev-down didn't work for me.

So in /etc/bluetooth I did this
PAND_ENABLED=1
PAND_OPTIONS="--role=PANU"

I created a script (made executable) called "panup" which had this in it:
#!/bin/bash
sudo pand --connect 00:12:D2:02:E7:F7 -n
sleep 1
sudo ifup bnep0

Of course use your own phones address instead of mine.

You can use the command "sudo hcitool scan" to get your phone's address.

I created another (executable) script to shut it down called "pandown":
#!/bin/bash
sudo ifdown bnep0
sudo pand -K

Allways shut it down with the pandown sript.

This is still not right, the network manager should be handling this, but I don't know how to make that work yet. In the mean time, I can browse the net with this while I am on the bus.

Wilbur

---

### Post by wkv2101 on 2008-06-08
Hey thats great that you got it working in hardy! I've got the sprint touch and am able to get this to work in that it says that I'm connected

sudo pand --connect 00:122:02:E7:F7 -n
sleep 1
sudo ifup bnep0

this is the output:
There is already a pid file /var/run/dhclient.bnep0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/bnep0/00:1e:4c:da:db:29
Sending on   LPF/bnep0/00:1e:4c:da:db:29
Sending on   Socket/fallback
DHCPDISCOVER on bnep0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.0.238 from 192.168.0.1
DHCPREQUEST of 192.168.0.238 on bnep0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.238 from 192.168.0.1
bound to 192.168.0.238 -- renewal in 122476 seconds.


But although it says that I'm connected firefox doesn't load any sites. I tried to kill it with 

sudo ifdown bnep0
sudo pand -K 

and try it again but no luck.
Any suggestions?
Thanks

---

### Post by wilbur.harvey on 2008-06-09
I had the same problem.

I went to the "File" tab on firefox, and unchecked he "Work Offline" tab, then it worked from firefox as well.

Wilbur

---

### Post by wkv2101 on 2008-06-09
Yep that work! Awesome, thx so much! I would have never thought the problem was with firefox.

---

### Post by dishguy123 on 2008-06-12
Has anyone got this to work using Moto Q on AT & T Cingular network?

---

### Post by dishguy123 on 2008-06-12
In my case, I get nothing when I type "hcitool scan".....

please help!

---

### Post by wilbur.harvey on 2008-06-13
Maybe you don't have some of the bluetooth tools installed like

sudo apt-get install

bluetooth
bluez-gnome
bluez-utils
gnome-bluetooth

---

### Post by tzalay on 2008-06-13
Dear Wilbur, thanks a lot, I was desperately searching for a solution since Hardy came out. You helped me more than you can imagine.

THX-THX-THX

---

### Post by xbshang on 2008-07-08
I guess this is probably an old topic. don't know if it's still fine to bring up the topic.

I am using Ubuntu Hardy, and has been trying to connect my O2 atom life to Hardy with BlueeZ PAN as described in this post. 

following the procedure, I got connected to my bluetooth and the PAN working fine, but the network manager just can't configure that DCHP connection. once I use manual connection, nothing happened and I just stay off line, even though my PDA is fine surfing online with GPRS. 

In Vista, I encountered the similar problem before, which the network center can't identify the IP address of PAN connection. After I change my Bluetooth PAN IP into static at XDA, I can surf internet properly. I tried the same thing here in hardy, but it doesn't work.

Anyone can help to identify this problem? :(

BTW, I modified a bit as described by wilbur.harvey since using hardy, don't know if that affect.

---

### Post by maks_zbogar on 2008-07-16
hm...

I did all what is written in this thread but have this problem: [COLOR="Red"]Connection refused(111)[/COLOR]

```

maks@Maks-MSI:~$ sudo pand --connect 00:12:D1:EB:40:F9 -n
pand[7172]: Bluetooth PAN daemon version 3.26
pand[7172]: Connecting to 00:12:D1:EB:40:F9
pand[7172]: Connect to 00:12:D1:EB:40:F9 failed. Connection refused(111)
maks@Maks-MSI:~$ 

```

hcitool scan is ok:
```

maks@Maks-MSI:~$ hcitool scan
Scanning ...
	00:12:D1:EB:40:F9	HPHW6915
maks@Maks-MSI:~$ 

```


I have tried that with 2 different cell phones and it is the same.
Is it something simple i am missing?

---

### Post by vasilis34 on 2008-07-17
Hi. I followed wilbur.harvey 's suggestions but I can't connect to internet. My laptop gets an ip and as far as I can tell DNS is working but firefox stops at the Connecting to ... phase. Anyone any suggestions on what to recheck or change?

---

### Post by fraser-08 on 2008-07-22
Thank you, Works well on Ubuntu 8.04 - Hardy 

Didn't work the first time but after a wee bit of playing about (unpairing, pairing, restarting Ubuntu, etc.) it seemed to work ok.

> **wilbur.harvey said:**
> I went to the "File" tab on firefox, and unchecked he "Work Offline" tab, then it worked from firefox as well.

Yes this is correct. I am using FF 3.0

---

