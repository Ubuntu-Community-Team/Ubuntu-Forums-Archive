---
title: "Wifi channels 12 and 13"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by rkelly on 2005-11-07
I´am using an Linksys WMP54GV4 (RaLink 2500 chipset) pci card.
Some problems possibly due to DECT phones in the neighbourhood let me change the configuration of my WRT54GV2.2 to use another channel, so I changed it´s configuration to use channel 13. Doing so I lost my connection to the accesspoint ... Iwlist shows that only the channels 1 to 11 are available.
Luckily I have a laptop still with some M$ product on it so I could reset it to another channel. Over here in Europe we are allowed to use the channels 1 to 13. 

Does somebody know how to enable the last two channels?

---

### Post by mips on 2005-11-08
Does the AP support channels 12&13 or is it restricted to 1-11 ???

Have a look, if you dont come right please post the following info:
1.AP Brand
2.AP Model
3.AP Firmware file name & version.

---

### Post by rkelly on 2005-11-08
[quote=mips]Does the AP support channels 12&13 or is it restricted to 1-11 ???[/quote] 
As stated in my original post I changed the AP to use channel 13. The accesspoint does support channels 12&13. The wireless drivers in Ubuntu do not support channels 12&13 out of the box, they are restricted to channels 1 to 11. 

[quote=mips]Have a look, if you dont come right please post the following info:
1.AP Brand
2.AP Model
3.AP Firmware file name & version.[/quote] 
The AP, or to be more correct the router, is a Linksys WRT54G V2.2, loaded with the latest firmware from Linksys, V4.20.8 if I recall correctly...

---

### Post by mips on 2005-11-08
Apologies, I read that wrong :oops:   I thought you changed the card. Will come bac to you.

---

### Post by rkelly on 2005-11-08
No need to apologise ;-)

---

### Post by mips on 2005-11-08
Post your **wlan.conf **file here.

---

### Post by rkelly on 2005-11-08
wlan.conf does not exsist anywhere on my system. It is not provided with the package wireless-tools.
The WPM54G V4 PCI card with RA2500 chipset is supported out of the box in Breezy.

---

### Post by mips on 2005-11-08
Deleted. Posted to wrong thread by mistake...

---

### Post by FLeiXiuS on 2005-11-08
Have you tried iwconfig DEVICE chan 13?  

Perhaps there is no support for channel 13 under your cards drivers.  I'll look further into it after you reply. 

[COLOR="DarkOrange"]Example:[/COLOR]
iwconfig eth0 chan 13 essid FLeiXiuS

---

### Post by rkelly on 2005-11-08
[quote=FLeiXiuS]Have you tried iwconfig DEVICE chan 13?  

Perhaps there is no support for channel 13 under your cards drivers.  I'll look further into it after you reply. 

[COLOR=DarkOrange]Example:[/COLOR]
iwconfig eth0 chan 13 essid FLeiXiuS[/quote] 
Yup, tried that too. 
I even get the following when checking what the running config is:
```
ra0       RT2500 Wireless  ESSID:"Mine"
          Mode:Managed  Frequency=2.472 GHz  Access Point: 00:12:17:C7:81:F0
          Bit Rate:54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=80/100  Signal level=-70 dBm  Noise level:-204 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``` The shown frequency is the correct frequency for channel 13, but I don´t have any connection with the rest of my network. As you wrote: it looks like the driver does not support these 2 channels. Perhaps because these are not allowed in the US?

Instead of wlan.conf I have a file /etc/network/interfaces with the following section for ra0:
```
iface ra0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid Mine
wireless-key [munged]
```

---

### Post by Lambert on 2005-11-09
I don't have an exact answer but it looks like you need to change a country/ region code. 

Maybe look for a file called RT2500STA.dat

Back up with a copy before you make any changes.

You may find some other help on this [[COLOR="Blue"]here[/COLOR]]("http://61.222.76.235/phpbb2").

---

### Post by rkelly on 2005-11-10
[quote=Lambert]I don't have an exact answer but it looks like you need to change a country/ region code. 

Maybe look for a file called RT2500STA.dat

Back up with a copy before you make any changes.

You may find some other help on this [[COLOR=Blue]here[/COLOR]]("http://61.222.76.235/phpbb2").[/quote] 
Can´t find that file on my system. I will search for it on internet and add it to see if it will help.

Thanks.

---

### Post by rkelly on 2005-11-19
I just took the time to follow up on this.
At the moment I am using channel 13.

This solution applies to all cards using the Ralink RT2500 chip, not just the Linksys WMP54GV4.

Here is how to do it:[LIST=1]
[*]Start a terminal.
[*]Create the directory /etc/Wireless/RT2500STA
(this is case-sensitive!)
[*]Put the attached file in the just created directory and rename it to RT2500STA.dat  (again case-sensitive!)
[*]Edit the file and add/change as required:[LIST]
[*]CountryRegion (2 enables channels 1 to 13)
[*]Channel (if left at 0 this enables scanning)
[*]and AuthMode and EncrypType for your desired encryption.
[*]Fill in the correct value for your SSID[/LIST] 
[*]Reboot your system, the configuration file is read when the kernel module is loaded.[/LIST]Full details can be found in the attached ra2500readme.txt.

Have fun!

---

### Post by swinster on 2006-04-01
Hi Rkelly (or anyone else viewing this.

I am running dapper (Kubuntu 6.06) and am still having issues with this very problem. I tried the fix above but no joy. Do i need to make changes to the /etc/network/interfaces file as well?

---

### Post by duality on 2006-04-01
channel 1-11 US, channel 1-13 EUROPE

---

### Post by rkelly on 2006-04-01
[quote=swinster]Hi Rkelly (or anyone else viewing this.

I am running dapper (Kubuntu 6.06) and am still having issues with this very problem. I tried the fix above but no joy. Do i need to make changes to the /etc/network/interfaces file as well?[/quote]

No, not in my case.
I don't know where you live, but are you sure that channels 12 and 13 are actually available in your hardware? 
As stated before in this thread, channels 12 and 13 are illegal in the US...
Some other countries impose different restrictions, even in the EU...

---

### Post by swinster on 2006-04-01
I'm in the UK and the router supports channels 1-13, in fact I run on 13 when in windows. It was of the major headaches as to why I couldn't get my WiFi working in the first place under Breezy then Dapper. The channel setting was one of the last things I altered on the router after down grading all the security etc etc.

I can now run on channel 11 with WPA authentication (not WPA2 yet, but I don't think this is supported at the driver level (even in windows) - although it is on my router), but I can't connect on channel 12 or 13. In fact I can switch the router to any channel 1-11 and the laptop will change with it, but 12 and 13 are a no go.

I have set the country code to 2 and may only small changes to the WPA and ESSID stuff, but it doesn't seem to make any difference. I can post the interfaces file or other stuff if needed but I'll have to do this tommorow as I have to put my neice to bed now.

I see you have seen my other thread in the dapper forum. I keep this one active as its more general

---

### Post by LOCOSLAW_PL on 2007-12-14
**rkelly** :

I tried to make my wireless working with your way, but it's still not working.

What can be wrong?

when I type "iwlist wlan0 freq" all the time I have freq from 1-11. (I need 12)

I use ubuntu 7.10 and rt2500 driver

Can you or anybody other help me?

> Create the directory /etc/Wireless/RA2500STA
Is this mistake or not? Should'n be RT2500STA?

Sorry for my poor English

---

### Post by rkelly on 2007-12-14
> **LOCOSLAW_PL said:**
> 

I tried to make my wireless working with your way, but it's still not working.
What can be wrong?
When I type "iwlist wlan0 freq" all the time I have freq from 1-11. (I need 12)
I use ubuntu 7.10 and rt2500 driver


Using the stock driver? It could be this solution does not work with the current stock Ubuntu drivers. You could try again with the serial monkey drivers.
See [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/") for the latest info.

> **LOCOSLAW_PL said:**
> 

Is this mistake or not? Should'n be RT2500STA?
Yes, you are right, and the first to notice in 2 years ;-) I fixed the line in my original post. The textfile is correct however.

I'm sorry I can't help you with it, I don't have any rt2500 hardware around at the moment to check.

---

### Post by mips on 2007-12-14
I must check if my rt2500 has ch12&13 support.

---

### Post by LOCOSLAW_PL on 2007-12-14
I already changed RA2500STA to **RT2500STA** and it is working :D

thanks ;)

---

### Post by jbernardo on 2008-01-01
If you're using the rt2x00 drivers you need a different strategy. I found this on the [serialmonkey forum]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=2488&highlight=ieee80211regdom").
From a console, type the following (If you're using gnome, replace as appropriate):
```
kdesudo kate /etc/modprobe.d/options
```Add the following line:
```
options mac80211 ieee80211_regdom=64
```Save, and after rebooting, you should now have channels 12 and 13 available. The easiest way to check is doing a "iwlist freq" at a command prompt.

---

