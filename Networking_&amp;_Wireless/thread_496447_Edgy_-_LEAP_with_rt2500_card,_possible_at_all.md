---
title: "Edgy - LEAP with rt2500 card, possible at all?"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by Aramis on 2007-07-09
Hi y'all,

In this thread I shall outline my university wireless problem to you guys, and hopefully you might be able to help me out.

My **hardware is** composed of a SAMSUNG A10 laptop (I know it is ancient), and a Hawking Technology Hi Speed 54g (Revision T) wireless card in PCMCIA. This card uses the RalTek 2500 chipset, and hence, since Edgy, is supported by Ubuntu with the rt2500 drivers shipped with the OS.

Like many universities across the globe, my institution uses MSCHAPv2 and LEAP as mean to authentication for its wireless service. Interestingly enough, our IT department finally caved in to the demand to have Linux (SuSE only at the moment) support, and their recommended configuration is as follows:

code for wpa_supplicant:
```

ctrl_interface=/var/run/wpa_supplicant
network={
		mode=0
		auth_alg=LEAP
		ssid="someSSID"
		scan_ssid=1
		key_mgmt=WPA-EAP
		proto=WPA
		group=TKIP
		eap=LEAP
		phase2="auth=MSCHAPV2"
		identity="myID"
		password="myPaswword"
	}

``` 

In conjunction with the above I use the following "interface" file:

```

iface ra0 inet dhcp
 wpa-driver wext
 wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```

Now, I know what you are all thinking.... This is not going to work because the wireless card uses the rt2500 drivers and not the generic Linux ones (NB: it is my understanding that wext is a generic wireless for Linux - correct me if I am wrong).

Indeed, the configuration in the above does not work :(, even if I comment out "wpa-driver wext") from the **interface** file.

Now, I must stress that this card and this driver work perfectly on my home network which uses WPA + TKIP (thanks to the thread on this matter cf. top of the page of this forum), hence I believe my problem falls in this category : [link]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=12988&sid=8cb25e34fb40aa24b77a1102263c5fbd")
Sadly, I do not understand what actually happened.. the thread's author got it to work but I cannot figure out how he did it. What I do not understand is the drivers that are referred to... am I using the same drivers as mentioned in the referenced thread? In the 5th post **serialmonkey** mentions that the rt2500 and so on are legacy drivers, and hence do not support EAP. That would be consistent with the fact that I can get the card to work at home, but not at Uni.

So my questions are:

a) is the rt2500 driver shipped with Edgy the same as the rt2x00 driver mentioned in the thread on LEAP (cf. first link)?
b) if not. How do I replace/install the rt2x00 drivers on my laptop?
c) if I manage - eventually - to install the "better" drivers, will this cause conflicts?

thanks in advance to whoever will be able to help me out :mrgreen:

I will be keeping an eye on this thread, therefore do not hesitate to ask for more details.

Cheers,

Ar@mi$

note: my Uni IT dep says that the wext drivers might need replacing with ndiswrapper... sadly, this application does not work for me at all, and in fact never has... the driver installs no problem.. even if I remove the rt2500 from the kernell the wireless card does not appear in the "iwconfig" list... So, I conclude that the ndiswrapper avenue is simply not for me

---

