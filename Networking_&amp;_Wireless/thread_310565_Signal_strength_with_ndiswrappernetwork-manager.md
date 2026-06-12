---
title: "Signal strength with ndiswrapper/network-manager"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by Thumper322 on 2006-12-01
Hello,

I've managed to get my wireless card working (it's a Linksys WPC54G) using Network Manager and **ndiswrapper**. The Network Manager panel applet is always showing full signal strength, though, even when I know for a fact the signal strength is low.

According to the ndiswrapper [FAQ]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ#Link_quality.2Fstatistics"),
> Windows drivers don't support link quality and noise level. Some drivers may use undocumented features to display them in Windows, but these are specific to those cards and unless the vendor discloses them, it is not possible to support these features. This is the reason why in Windows you need to install wireless monitoring tool supplied by the vendor, instead of native Windows application displaying it. So it is not possible to have quality/noise level availalbe in ndiswrapper. All the information available through NDIS calls can be seen in /proc/net/ndiswrapper/wlan0/stats.

But under Windows XP SP2, the Wireless Zero Configuration tool had no difficulty with displaying link quality--I never had to touch Linksys' custom wireless tool.

Also, the file mentioned (/proc/net/ndiswrapper/wlan0/stats) doesn't exist. My wireless card is listed as eth1; does this make a difference?

So, my question is: Can I, and if so, how do I, display the correct signal strength? Is there a decent Linux driver for this card that I should use instead (I had to blacklist bcmw43xx to work the card)?

Thanks for any help.

---

### Post by Tilex on 2006-12-01
If you issue the command "iwconfig eth1", do you see something under "Link quality", "Signal Level", "Noise level"?

Maybe, in WinXP, they use a generic driver for displaying the link quality, so it is not very precise...??:-k 

I've a built-in wireless card, and when I use network-manager to scan for wireless networks, it shows link quality.  However, when I issue a command line for sniffing on a channel, it says that seeing "signal strength" is not supported by my wireless card.  Weird, huh.

---

### Post by Thumper322 on 2006-12-01
> **Tilex said:**
> If you issue the command "iwconfig eth1", do you see something under "Link quality", "Signal Level", "Noise level"?

Maybe, in WinXP, they use a generic driver for displaying the link quality, so it is not very precise...??:-k 

I've a built-in wireless card, and when I use network-manager to scan for wireless networks, it shows link quality.  However, when I issue a command line for sniffing on a channel, it says that seeing "signal strength" is not supported by my wireless card.  Weird, huh.
I'm not on my box right now, but off the top of my head I recall it showing all three. Link Quality is always listed as 100/100, and Signal Level and Noise Level are both listed as negative numbers in units of dBM, I think.

Wireless cards are wacky.

---

### Post by hush on 2007-02-07
i have this same problem.. very frustrating

---

### Post by cb474 on 2007-02-20
I have this problem too. I also found that Windows had no trouble detecting signal strength with my built in Atheros AR5212 card.

iwconfig says:

ath0      IEEE 802.11b  ESSID:"FreeCableAccess"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:90:96:58:0D:76   
          Bit Rate:11 Mb/s   
          Power Management:off
          Link Quality:100/100  Signal level:-54 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I also notice that when I connect to different access points, iwconfig reports different signal levels. But link quality is always "100/100" and noise level is always -256dBm.

No solution?

---

### Post by cb474 on 2007-02-20
I just noticed in the ndiswrapper wiki that the paragraph about link quality has a couple extra sentences added to it:

>  Link quality/statistics

Windows drivers don't support link quality and noise level. Some drivers may use undocumented features to display them in Windows, but these are specific to those cards and unless the vendor discloses them, it is not possible to support these features in ndiswrapper. All the information available through NDIS calls can be seen in /proc/net/ndiswrapper/wlan0/stats. [COLOR="Blue"]NDIS version 6 supports these features. Support for ndis6 is being added at this time. When that is complete, with Windows vista drivers, these features should be available in ndiswrapper.[/COLOR]

Now that Vista is out, I wonder if this means we can use the Vista drivers, if one is released for your specific card? What version of ndiswrapper will it require to use vista drivers? When is the support being developed going to be ready? I'm going to try the vista drivers just for the heck of it.

---

### Post by cb474 on 2007-02-20
Well, I tried the Vista driver with ndiswrapper 1.8 and it didn't work at all. Hopefully ndiswrapper will be updated soon to work with Vista drivers and that will fix the signal strength issue.

---

