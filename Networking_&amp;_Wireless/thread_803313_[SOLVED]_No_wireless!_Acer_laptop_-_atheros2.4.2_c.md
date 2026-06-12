---
title: "[SOLVED] No wireless! Acer laptop - atheros2.4.2 chipset"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2008-05-22
Hi all. I love the fact that I can smoothly install a linux on my laptop.
I never thought that the day would come.
But....

I have installed ubunti 8.0.4 on an 
Acer Extena 5220 laptop.

I can plug into my router fine using the ethernet adaptor. But I can't access the router wirelessly.
The network widget that comes with gnome isn't showing any info for a wireless networks.

After much reading, I tried many things.

I installed ndisgtk and tried to install a windows driver. This froze my laptop entirely. This matches this fellows experience:
[www.savagehamsters.com/?p=55](www.savagehamsters.com/?p=55)

I installed madwifi using apt. This did not help either.
modprobe tells me that I have ath_pci running, but I still can't see a way to get on the network.

How do I do it?

I really don't want to have to go and buy a usb wireless adapter.
They stick out the side of the laptop and are a pain in the ***.

Thanks.

---

### Post by dmizer on 2008-05-22
we need more information about your network adapter (specificaly what chipset it has).  in order to find this, please post the output of:
```
lshw -C network
```

---

### Post by nicedude on 2008-05-22
Unfortunatly while the advise above or lspci are the best device listing ones I know, They both give incorrect ID of my wifi adapter and I have a Acer 5520-5716 with a Atheros AR5007EG wifi chipset. Under gutsy these commands said I had a AR5006EG and now under hardy they report it as AR242x, so the only true way for me to figure out what my laptop has was I foound it on an Acer support website and not without allot of looking as it was not available on the USA website I think I found the info on the Canadian Acer site. Unfortunatly in my experience PC makers act like the wifi chipset is top secret or something as it is rare from what I have seen for them to just list it on the specs page. If you dig enough you should be able to find out what you have though and by all means I don't mean that you shouldn't use the listing commands like the one above, just don't assume its correct 100% and google around for it as well to see if you can confirm the ID as it will save you a bunch of headache in the long run. If you post your exact model and series like Acer 5220-???? I will look around for you as well if you can't find the info. 

If you do find in the end that you have an Atheros chipset you are actually lucky as they are great chipsets once you get them setup right. 

Also post whether you installed 64 or 32 bit Ubuntu Hardy as it makes a difference in what drivers are available for Atheros wifi as the best Atheros drivers are the madwifi.org drivers just for Atheros but they only work with the 32bit OS as for 64bit Ndiswrapper in conjunction with a windows driver will be your only Atheros solution. You may however learn you don't even have an Atheros chipset but I can't tell at all from info so far.

So hope this helps and run the command above that the nice member has provided and post that here along with a series number (Look on bottom of laptop at white barcode sticker )to go with that model number and I will try to help you the best I can as will the others here in these forums.

Hope I can help and I am 99% sure you will be able to solve this :-)

---

### Post by ugm6hr on 2008-05-22
> Under gutsy these commands said I had a AR5006EG and now under hardy they report it as AR242x,

Indeed, this chipset is currently the most troublesome Atheros one.

There are some good How-tos for it now (and 32-bit madwifi drivers).

*lspci* is still helpful though.

---

### Post by SpinningAround on 2008-05-22
> **ugm6hr said:**
> Indeed, this chipset is currently the most troublesome Atheros one.

There are some good How-tos for it now (and 32-bit madwifi drivers).

*lspci* is still helpful though.

As a newbie would you like to explain why it's so troublesome and if you possible have some insight to the programing why it haven't been added as "work from start" yet?

---

### Post by terazen on 2008-05-22
This is probably something you already checked...but, on mine I just installed this weekend I had to enable the driver under system->administration->hardware drivers.  It said something about it being an unsupported driver ubuntu couldn't vouch for I forget exactly...

---

### Post by ugm6hr on 2008-05-22
> **SpinningAround said:**
> As a newbie would you like to explain why it's so troublesome and if you possible have some insight to the programing why it haven't been added as "work from start" yet?

Atheros wifi chipsets are amongst the best supported by Linux.

However, this is a result of the madwifi driver (which I believe is independent of Atheros).

Therefore, new chipset drivers for Linux always lag behind their release, since madwifi don't create the driver until after the release.

This is a new chipset, and the standard madwifi drivers as of the 8.04 release did not include it.  Hopefully, this will change as of the next release.  The madwifi 64-bit driver still does not exist though.

You can read more here: [http://madwifi.org/](http://madwifi.org/)

PS: How-tos: [http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686) [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by bobdobbs on 2008-08-02
Hi guys.

Thanks for the responses.

Since I began this thread in May, I've learnt a lot about drivers, wireless networking and a lot more else.

But I still can't actually get on to a wireless network.

I now have the madwifi drivers.
I compiled them from source and installed them with the madwifi provided scripts.

I now have wireless interfaces. This is more than I had before.
It seems that the ath_pci LKM provides two interfaces - ath0 and wifi0.

But I can't scan for networks. And if I use nm-applet to connect to a network that I know is there, nm-applet doesn't see it and won't allow me to connect to it.

The relevant entry from lshw -C network:

  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wifi0
       version: 01
       serial: 00:17:c4:1a:96:2e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11b


This is driving me nuts.
Can anyone help me out here? I've been tampering with my laptop for two months now, and I still can't connect to my wifi at home.

---

### Post by ugm6hr on 2008-08-02
You haven't confirmed whether you are using 32-bit or 64-bit Ubuntu.

And presumably you are on Ubuntu 8.04 too?

Have you tried any of the multitude of How-Tos scattered around this forum?  Just search for AR5007 in the Netorking or Tutorials sections.

---

### Post by bobdobbs on 2008-08-02
Hi.

I'm using 32-bit Hardy Heron.
My hardware is all 32-bit.

I've found about three how-to's and a few blog posts about the atheros chipset and how to get it working. I tried a number of solutions.

I eventually abandoned using ndiswrappers. Whenever I tried to load a driver, my system froze and would not recover.

Eventually I found a madwifi walk-through.
Along with the other resources, it helped me to get where I am at the moment - better informed in some ways, confused in others, and with a kernel module that loads a driver.

Some forum posts say that the atheros chipsets are amongst the best supported by linux. Other posters are pulling hair.

I count myself amongst the latter.

With the driver present and the ath0 interface up, I still can't get on the network.
I've found a kde app that scans for networks, and it can't see my home wifi network. It doesn't have a log or any diagnostic messages that I can find.
According to the madwifi docs, you can scan from the command line with:
modprobe wlan_scan_sta

But when I do that, I get the error:
FATAL: Module rt73 not found.

Google tells me that this is related to a ralink device. 
This seems irrelevant to my situation. This is a driver I don't need and don't care about. But it seems that I have to figure out what it is, maybe compile it and load it in order to get my atheros-based wifi adapter to scan successfully for networks?
Another wrong tree to bark up.

I'm grateful that I've gotten this far, but I'm a little frustrated with myself that I haven't gotten results yet after navigating the vast array of documentation, posts and blogs on wifi, ubuntu and the atheros chipsets.
I feel like I'm just going deeper into the rabbit hole here.

---

### Post by dmizer on 2008-08-02
Sorry for your frustration.  Believe me, many of us have been there.  I know I certainly have.  If at all possible, it may save you a lot of baldness if you simply purchase a new and better supported card.

To address your question though, you can scan from the command line with this command:
```
sudo iwlist ath0 scan
```
this command will be independent of device or driver as long as "ath0" matches your wireless device (sometimes it's wlan0 or sundry other things).

---

### Post by bobdobbs on 2008-08-02
> **dmizer said:**
> Sorry for your frustration.  Believe me, many of us have been there.  I know I certainly have.  If at all possible, it may save you a lot of baldness if you simply purchase a new and better supported card.

To address your question though, you can scan from the command line with this command:
```
sudo iwlist ath0 scan
```
this command will be independent of device or driver as long as "ath0" matches your wireless device (sometimes it's wlan0 or sundry other things).

Trouble is, if I had searched the web for detail on linux suport for this chipset before I bought the laptop, I would have thought that it was supported. In theory it is supported by madwifi. Some postings say it is well supported. Some people have no luck getting it working.

I still haven't figured out if it is possible to get it working. I'd like to think that it is impossible. Then I could have the luxury of giving up.


 iwlist ath0 scan
ath0      No scan results

Hm... 

I wonder what to conclude from this.
I know that the network is there, 'cos two other pc's have wireless access to it.
Does this mean that the driver isn't working?
Do I have to try another driver?

There is also a line in the dmesg log:
ath0: no IPv6 routers present

What can I conclude from that

---

### Post by dmizer on 2008-08-02
> **bobdobbs said:**
> ```
 iwlist ath0 scan
ath0      No scan results
```

Hm... 

I wonder what to conclude from this.
I know that the network is there, 'cos two other pc's have wireless access to it.
Does this mean that the driver isn't working?
Do I have to try another driver?
No, it's much more sinister than that.  It means the driver is loaded and driving the card, but that it simply does not see any networks.

> **bobdobbs said:**
> There is also a line in the dmesg log:
ath0: no IPv6 routers present

What can I conclude from that
This is nothing to worry about.  If you want to get rid of the message, you can disable IPv6: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?) But that won't fix your wireless problem.

---

### Post by bobdobbs on 2008-08-02
Hm.

This is no good at all.

Any idea how I can drill down and find what the problem is?

---

### Post by dmizer on 2008-08-03
On the off chance ...

Does your wireless card have an on/off switch?  There may also be a setting in the BIOS for it as well.

How far are you from the access point?

---

### Post by bobdobbs on 2008-08-04
Thanks for the suggestion.
I always forget the basic things.

Fancy that. My laptop does indeed have an on/off switch. Who'd a thought?
:rolleyes:
(Im kinda new to laptop ownership and laptops)

Alas, playing with the switch doesn't seem to help.

Distance from the access point isn't a problem. I've got other wireless devices nearby all on the network. The distance is about 8 feet.

Looking around the BIOS settings is interesting. There doesn't seem to be anything pertaining to a network device, but it is interesting.


When I flick the switch, there is no indication if the switch is off or on. The resting point is the same for both off and on. There is a little green LED that should indicate on. This doesn't come on. 

Digging in the logs I find this:

> 
[  314.132851] wlan: svn r3698
[  314.349465] ath_pci: svn r3698
[  314.349691] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[  314.349706] PCI: Setting latency timer of device 0000:04:00.0 to 64
[  314.837758] MadWifi: ath_attach: HAL managed transmit power control (TPC) disabled.
[  314.837779] MadWifi: ath_attach: Interference mitigation is supported.  Currently disabled.
[  314.842011] MadWifi: ath_attach: Switching rfkill capability off.
[  314.913486] ath_rate_sample: 1.2 (svn r3698)
[  314.914946] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[  314.914952] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  314.914959] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[  314.914963] wifi0: Atheros AR2425 chip found (MAC 14.2, PHY SChip 7.0, Radio 10.2)
[  314.914969] wifi0: Use hw queue 1 for WME_AC_BE traffic
[  314.914971] wifi0: Use hw queue 0 for WME_AC_BK traffic
[  314.914972] wifi0: Use hw queue 2 for WME_AC_VI traffic
[  314.914974] wifi0: Use hw queue 3 for WME_AC_VO traffic
[  314.914975] wifi0: Use hw queue 4 for XR traffic
[  314.914977] wifi0: Use hw queue 7 for UAPSD traffic
[  314.914978] wifi0: Use hw queue 8 for CAB traffic
[  314.914979] wifi0: Use hw queue 9 for beacons
[  314.949342] unable to load wlan_scan_sta
[  314.949966] ath_pci: wifi0: Atheros 5424/2424: mem=0xf8000000, irq=17
[  325.769181] ath0: no IPv6 routers present


From this I can only tell that something is happening.
I don't see any red lights. Just the message that we can't scan.

Where to go from here?

---

### Post by 1nsanity_is_key on 2008-08-30
I have the exact same problem with my Acer laptop with an atheros card, and the 'dmesg' output looked very similar to yours.

	My problem resulted after I installed some ralink device drivers for a wireless usb device.
After i uninstalled the ralink drivers, and tried modprobe-ing the 'wlan_scan_sta' module,
 I was recieving the same 'rt73 module not found' error.

	I found a file called 'ralink' in the '/etc/modprobe.d' folder, and deleted it. (But saved a backup copy if something goes wrong)
And then, I executed the following command:
```

sudo modprobe wlan_scan_sta

```

The contents of the file I deleted were:
```

alias wlan* rt73

```

I don't know if this fix will work for everyone, but it looks like the problem could be related to modprobe maybe.

I think somehow the wlan_scan_sta module is aliased to the rt73 module.

Everything started to work again after a few seconds. I'm glad my wireless is working again :)

---

### Post by bobdobbs on 2008-08-30
Hi.
That might actually be it.
I might have loaded a ralink driver for a usb wireless card.

After "round one" of my struggles with the laptop wireless I went out and bought a USB wireless adaptor. 
After much hair pulling, I couldn't get that working either. 
So, I just left the whole problem for a while.

I think that more recently when I went back to the trying to get the inbuilt wireless adaptor to work I must have left the ralink drivers in place.

So, next step - start all over again. 

I'll have another go at it within the next few days and come back and report my results.

Thanks.

---

### Post by bobdobbs on 2008-11-01
Problem solved.

After I updated to ibis, I can now use the wireless.

---

