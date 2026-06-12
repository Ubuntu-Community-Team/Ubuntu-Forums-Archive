---
title: "WEP Wireless"
date: 2005-05-05
forum: Networking &amp; Wireless
---

### Post by joplass on 2005-05-05
My wireless is working fine without WEP but once I enable the wireless security it stops working.  I know some people here have there WEP working.  Can someone help me make mine work?
Once I turne it on Hoary while booting hangs at Network configuration for awhile and shows failed.
I will appreciate some help.
thanks

---

### Post by dave9191 on 2005-05-05
After booting with wep when it fails copy the output of 'iwconfig' here. Also note that passphrases are currently not supported, so when entering the wep key make sure that you give the hex key.

---

### Post by radhaz on 2005-05-05
how do you get the hexkey translation for the passphrase?

---

### Post by joplass on 2005-05-05
Below is the result of "iwconfig" with the hex key not the passphrase:

job@ubuntunotebook:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:8 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:98   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

job@ubuntunotebook:~$

---

### Post by joplass on 2005-05-05
Here is "iwconfig" with WEP disable even my ESSID is present.

job@ubuntunotebook:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:A2:CD:72
          Bit Rate:54 Mb/s   Tx-Power:8 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-34 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:212   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

job@ubuntunotebook:~$

---

### Post by poofyhairguy on 2005-05-05
[QUOTE=joplass]My wireless is working fine without WEP but once I enable the wireless security it stops working.  I know some people here have there WEP working.  Can someone help me make mine work?
[/QUOTE]

First of all, make sure you replace the ESSID and the TYPED OUT 128bit key in the network tool....

---

### Post by joplass on 2005-05-06
[QUOTE=poofyhairguy]First of all, make sure you replace the ESSID 
Do you mean re-type the name of the ESSID even if it is already there?

and the TYPED OUT 128bit key in the network tool....[/QUOTE]
Now I am using 65bit encryption and you are suggesting to go with 128.  

In that case I will try both of your suggestions.

Thanks!

---

### Post by az on 2005-05-06
I know that some wireless cards (one which use the ac10 or ac111 chipsets) work, but do not support WEP.

WEP support was just added to the driver upstream and may make it into Breezy.  If you have such a card, you may use ndiswrapper to run the windows driver and use WEP.

Do
lspci
to see what card you have...

---

### Post by joplass on 2005-05-06
[QUOTE=azz]I know that some wireless cards (one which use the ac10 or ac111 chipsets) work, but do not support WEP.

WEP support was just added to the driver upstream and may make it into Breezy.  If you have such a card, you may use ndiswrapper to run the windows driver and use WEP.

Do
lspci
to see what card you have...[/QUOTE]

I got "AC 97"

---

### Post by az on 2005-05-06
I made a typo.  It should be ac100 or ac111.

AC 97 is your sound system.

---

### Post by joplass on 2005-05-06
[QUOTE=azz]I made a typo.  It should be ac100 or ac111.

AC 97 is your sound system.[/QUOTE]

Here is that output:
job@ubuntunotebook:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 05)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 05)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801CA/CAM SMBus Controller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:02.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:02:02.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
0000:02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:02:08.0 Ethernet controller: Intel Corp. 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
0000:03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
job@ubuntunotebook:~$

---

### Post by radhaz on 2005-05-07
[QUOTE=joplass]Here is that output:
job@ubuntunotebook:~$ lspci
0000:03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
job@ubuntunotebook:~$[/QUOTE]

Since it apprear's you have a broadcom chipset [this howto](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+wifi) might be a good read (10 page's worth) to find some answers?  

Sorry I'm too much a n00b to help you, but hopefully I can at least help you along.

---

### Post by mono2 on 2005-05-11
I am having problems receiving an IP from my router.

Below you can see the output from iwconfig for the device. To me, it looks like it has authenticated to the network, and I'm just not receiving an ip from the dhcp server... is that so? Can my wep passphrase in alpha or hex still be wrong?

```

eth2   IEEE 802.11b/g  ESSID:"nsfWLAN2002"
          Mode:Managed  Frequency:2.437GHz  Access Point: 00:06:AB:00:1C:0B
          Bit Rate:11Mb/s   Tx-Power=31 dBm   Sensitivity=20/200
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B
          Link Quality=50/0  Signal level=-62 dBm  Noise level=-120 dBm
          Rx invalid nwid:0  Rx invalid crypt:67  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by dave9191 on 2005-05-11
[QUOTE=mono2]I am having problems receiving an IP from my router.

Below you can see the output from iwconfig for the device. To me, it looks like it has authenticated to the network, and I'm just not receiving an ip from the dhcp server... is that so? Can my wep passphrase in alpha or hex still be wrong?

```

eth2   IEEE 802.11b/g  ESSID:"nsfWLAN2002"
          Mode:Managed  Frequency:2.437GHz  Access Point: 00:06:AB:00:1C:0B
          Bit Rate:11Mb/s   Tx-Power=31 dBm   Sensitivity=20/200
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B
          Link Quality=50/0  Signal level=-62 dBm  Noise level=-120 dBm
          Rx invalid nwid:0  Rx invalid crypt:67  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```[/QUOTE]

There are a lot of invalud crypts there, but it looks like it connected. What is the output from dhclient when you run it to get the IP?

---

### Post by mono2 on 2005-05-11
[QUOTE=dave9191]There are a lot of invalud crypts there, but it looks like it connected. What is the output from dhclient when you run it to get the IP?[/QUOTE]

It just times out without receiving an ip, as you can see below. 

```
Listening on LPF/eth2/00:04:e2:63:f2:cb
Sending on   LPF/eth2/00:04:e2:63:f2:cb
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
--notification is an invalid option. See 'zenity --help' for more details
```

On a sidenote, I can't access any settings on the router as it is not mine (home office supplied by employer of one my flatmates).

DHCP works perfectly on several Mac's and Windows machines we have on the network.

---

### Post by dave9191 on 2005-05-11
It looks like it should work :(

Also   Link Quality=50/0 looks kinda strange. should be more like 50/100. Maybe the linux driver doesnt support your card properly? I dunno sry.

---

### Post by mono2 on 2005-05-11
[QUOTE=dave9191]It looks like it should work :(

Also   Link Quality=50/0 looks kinda strange. should be more like 50/100. Maybe the linux driver doesnt support your card properly? I dunno sry.[/QUOTE]

I've seen many reports that the card works perferctly with linux, so it can't be that. Anyhoo.. looks like I just have to keep trying :/

---

### Post by mono2 on 2005-05-11
Thanks for taking a look, btw. :)

---

### Post by Toddy on 2005-05-11
Make sure your router is configured for "open" authentication, not "shared".

---

### Post by mono2 on 2005-05-12
[QUOTE=Toddy]Make sure your router is configured for "open" authentication, not "shared".[/QUOTE]

That's the thing.. I don't have access to the router :(

But is that something that is make or break with wep and linux? Shared works against the macs and windows machines, while being unsupported on linux?

If I'm able to get admin priviliges on the router, will switching to shared break the setup between the windows and mac machines on the network?

---

### Post by betamax on 2005-05-12
Hi there,

One thing with WEP which worked for me.
When putting your wireless WEP key into the network settings add 
**s:** to the start.

e.g.  "s:wepkey"

This worked great on my IBM t23.
A friend passed this on to me from a Suse support site.

Good Luck.

---

