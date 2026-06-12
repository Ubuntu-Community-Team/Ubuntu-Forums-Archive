---
title: "eth1 instead of wlan0"
date: 2005-05-18
forum: Networking &amp; Wireless
---

### Post by deorca on 2005-05-18
I'm using a 3Com 3CRSHPW196 wireless PCMCIA card on my Dell Inspiron 8500.

I'm pretty sure the Ubuntu installation has assigned the wrong driver for my card as it's assigned the name eth1 to the device. The HW compatibility list says this card is supported OK, using the atmel driver, tho iwconfig shows no atmel device (seems to be some sort of generic 802.11 driver).

I got the atmel package via synaptic, but not sure what to do now .. how do I reassign the card to the atmel driver?

Would appreciate any help very very much.

---

### Post by philipacamaniac on 2005-05-18
If it is an atmel based card, you might try compiling the latest CVS snapshot. That's how I got my WUSB11 to work (which is also an atmel based card).

See this thread: [http://www.ubuntuforums.org/showthread.php?t=29554&page=2&pp=10](http://www.ubuntuforums.org/showthread.php?t=29554&page=2&pp=10) and follow peejay's instructions.

Oh, and a network card, whether wireless or wired, can be given any alias. Sometimes cards will just default to eth1 instead wlan0.

---

### Post by deorca on 2005-05-19
Nope, followed the steps and all appeared to go OK. But still nothing doing.

I noticed the LED on the card goes out completely when I activate the wireless interface but comes on again when I deactivate it. I don't know if I should remove the atmel package with synaptic, I don't completely understand what the steps Peejay gave did. All I know is, it didn't work and my wireless card still can't connect to my router in Ubuntu. 

This is the sort of thing that will prevent me from using any flavour of Linux and I so want to move over from XP.

---

### Post by philipacamaniac on 2005-05-20
What you did by following peejay's steps was install the latest greatest driver for your card. With iwconfig, do you see you card now?

You probably need to manually set the essid: 
(assumed that your card is still eth1 and your essid is "linksys")
```
sudo iwconfig eth1 essid "linksys"
```
If you have WEP encryption enabled on the router, manually set the WEP key:
128bit keys:
```
sudo iwconfig eth1 key xxxx-xxxx-xxxx-xxxx
```
64/40bit keys:
```
sudo iwconfig eth1 key xxxxxxxxxx
```
Make sure the wireless card has an interface entry:
```
sudo nano /etc/network/interfaces
```
In this file, you need an entry that looks something like this:
(assumed your using DHCP and not a static IP address)
```
auto eth1
iface eth1 inet dhcp
```
Then restart your network:
```
sudo /etc/init.d/networking restart
```

(This solution involves a lot of command line, mostly because I'm not very familiar with the GNOME interface (I use KDE), and this is how I got mine working).

---

### Post by deorca on 2005-05-22
Thanks v. much for your suggestions.

OK, checked /etc/network/interfaces and there was a correct entry for the interface. I re-entered the card parameters with iwconfig again, and restarted the network anyway, but to no avail.

I'm convinced that for some reason Ubuntu isn't recognising the device correctly as it doesn't list the MAC address and says the device is an IEEE 802.11-DS (see below) rather than a 3Com CRSHPW_96 as it says in /etc/pcmcia/config

Is there anyway I can force Ubuntu to bind to the correct card spec?

This is what iwconfig gives -

```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"BLAH-BLAH"
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: 02:00:2C:A6:D5:27
          Bit Rate:11 Mb/s
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:BLAH-BLAH-BL   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by deorca on 2005-05-22
..I've also just noticed that my laptop makes a loud beep on startup and shutdown, and I think it's when it starts the PCMCIA services. 

If this were a desktop I'd have no problems, I'd just use the wired connection, but I use a laptop cos I need to move around.

I know I'm far from being the only one with wireless problems, but I'd really, really like to get this working.

---

### Post by Kyral on 2005-05-22
Have you tried using NDiswrapper to use the Windows Drivers? That may work

---

### Post by deorca on 2005-05-22
I haven't tried the NDIS wrapper, no. All reports say that the atmel driver works well, and I've had it working before (same hardware, different distro, long time ago, long story). Also the card isn't listed as being supported on the Ndiswrapper list ([http://ndiswrapper.sourceforge.net/phpwiki/index.php/List](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List) ) so I'm not keen to start faffing around with that.

I've just found that it does find my MAC address too, iwconfig just wasn't displaying for some reason. ifup gives the following -

```
# ifup eth1
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:04:75:d2:71:58
Sending on   LPF/eth1/00:04:75:d2:71:58
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

And I've been through iwlist to check, again. So now I'm *really* confused. Everything seems to be in place - device MAC address, router MAC address, all parameters are set correctly as far as I can tell. There's something missing .. but what?

---

### Post by rusi_pathan on 2005-05-22
Try to play with your wifi router settings. Disable encryption and any MAC filtering and see if it works.

---

### Post by deorca on 2005-05-24
OK, disabled MAC filters, WEP encryption, everything, and still nothing. I made sure once again that the device was properly configured (using iwconfig) but not a sausage. I'm convinced the wrong atmel module is being loaded (or something) everytime I unplug the card and unload atmel and atmel-cs using modprobe, they get reloaded. There seems to be no evidence of what was compiled from the at503* stuff (CVS package from sourceforge).

Don't know what to try now, but will keep fiddling till I get the damn thing working. Gates & Ballmer wouldn't understand.

---

### Post by sukhu on 2005-08-12
philipacamaniac, thanks for your help.


My 3Com 3crshpw196 is now working.

I didn't have to add any drivers.  5.04 already has the drivers.

---

### Post by MetalMusicAddict on 2005-10-16
[QUOTE=deorca]..I've also just noticed that my laptop makes a loud beep on startup and shutdown, and I think it's when it starts the PCMCIA services. 

If this were a desktop I'd have no problems, I'd just use the wired connection, but I use a laptop cos I need to move around.

I know I'm far from being the only one with wireless problems, but I'd really, really like to get this working.[/QUOTE]
Im getting the same "beeping" sounds with my A21m Thinkpad and WPC11 v?.

---

