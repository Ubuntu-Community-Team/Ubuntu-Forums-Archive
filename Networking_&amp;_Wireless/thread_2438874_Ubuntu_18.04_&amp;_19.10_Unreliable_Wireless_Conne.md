---
title: "Ubuntu 18.04 &amp; 19.10 Unreliable Wireless Connection"
date: 2020-03-19
forum: Networking &amp; Wireless
---

### Post by dengineer on 2020-03-19
Wireless-info attached. Like many posters here I have been having ongoing difficulty with WiFi: At apparently random times "Connection failed. Activation of network connection failed." occurs. Afer a restart it may be successful. Have verified Secure Boot is disabled. Code associated with wireless adapter is 103c:18ec; not sure what to do with that.

---

### Post by chili555 on 2020-03-19
I suspect that the problem may actually be in the router. We see this:

> 
TP-Link_7169      <MAC 'TP-Link_7169' [AN2]>  Infra  3     2422 MHz  270 Mbit/s  63      &#9602;&#9604;&#9606;_  WPA2       yes     * 
Channel 3 is a very unusual channel to choose when setting up your router. I suspect that the router is, in fact, set to auto select the channel, meaning that, like my ex-girlfriend, wherever you think I am, I have moved. Good luck finding me.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Reboot and tell us if the behavior has improved.

---

### Post by dengineer on 2020-03-20
Thank you for your assistance. This TP-Link router is new (the problem first occurred on an older D-Link  router. The current router had been set to ch 3 to avoid a near  neighbor's strong signal on 11 and to straddle some weaker others  around channels 1 and 6. Per your suggestion I have now set the router to channel 6 which is reasonably clear of nearby competition. I am reading -50 to -60  db for my router's signal at the laptop  according to a phone app and usually showing (when laptop wifi working) 3  to 4 bars. Router also had been set to WPA2-PSK (Personal) with AES  encryption. I have now switched 2.4 width to 20 from auto.  Neither router caused any difficulties with a desktop Ubuntu 18.04  situated 3 feet from this laptop and using a D-Link wifi adapter. The  REGDOMAIN was already correct (as CA). 
I do not think that the  router or domain are factors, given the circumstances as described  above, but it's good to verify them. As I prepare to  post this, I have turned off my wired connection (see below) and successfully turned  on wifi, showing 4 bars. I expect that it will operate properly for an  indeterminate length of time and then pop up the "Connection failed.  etc" message for no obvious reason. When that happens I'll post another  wireless info result. Please advise if there is a further step that I  can take; I would prefer to not need a wifi adapter. I suppose there  could be some mechanical issue with the internal adapter; I've not  wanted to open the case and risk causing damage if there is no reason to  do that.
(BTW, two days ago I installed a TP-Link range extender  next to this laptop and have been using its _wired _connector when I lose  the wifi connection. I have not yet switched to the extender's wifi, not  wanting to add another factor to the trouble-shooting.)
I do hope we can resolve this; I, as I expect do the other posters here, want Ubuntu and Linux in general to be available to everyone.

---

### Post by chili555 on 2020-03-20
> When that happens I'll post another wireless info result. Please do. I shall have my fingers crossed.

---

### Post by dengineer on 2020-03-20
After coming out of suspend this morning wifi was operational until late afternoon. Since all was good later in this period, I switched the wifi connection to the range externder TP-Link_EXT without a visible hiccup. However after an hour or so the usual "Connection failed. ..." occurred.  I updated wireless info a minute or two after that; it is attached. 
This evening I brought PC out of suspend and wifi operating normally again.
I remain curious about the code associated with the wifi adapter: 103c:18ec. How does one access the list you partially included in one of the Broadcom driver post responses where these codes are cross-referenced to what I gather are supported drivers? Is there any value in investigating such for this adapter?

---

### Post by chili555 on 2020-03-20
> I remain curious about the code associated with the wifi adapter: 103c:18ec. How does one access the list you partially included in one of the Broadcom driver post responses where these codes are cross-referenced to what I gather are supported drivers? Is there any value in investigating such for this adapter?
Please see your result:> 
Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [[COLOR="#FF0000"]1814:3290[/COLOR]]
	DeviceName: Ralink WLAN Ralink RT3290LE Roma 802.11bgn Wi-Fi
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]I believe that the pci.id you quote, 103c:18ec, is relevant to the bluetooth part of the combination adapter. The wifi part is 1814:3290.

The list I posted relative to Broadcom adapters is a list I myself created. There is no list, as far as I know, for this series of Ralink adapters. The driver in use, rt2800pci, is the only known driver for 1814:3290. Generally, and certainly in the case of these Ralinks, only one and usually the only driver will load based on the pci.id, also known as alias, in the driver code. Let's check: ```
modinfo rt2800pci
``````

filename:       /lib/modules/5.3.0-42-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     397494504AF0682FF05116A
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
<snip>
alias:          pci:v0000[COLOR="#FF0000"]1814[/COLOR]d0000[COLOR="#FF0000"]3290[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
<snip>
```There is a driver parameter that you could try:```
sudo -i
echo "options rt2800pci nohwcrypt=Y"  >  /etc/modprobe.d/rt2800pci.conf
exit
```Reboot.

I notice that your extender has all the misconfiguration issues that I recommended be corrected above; most notably, but not limited to TKIP:

```
Cell 06 - Address: <MAC 'TP-Link_7169_EXT' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"TP-Link_7169_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000055fd7a199
                    Extra: Last beacon: 22240ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
```Please review my comments above and fine-tune the extender.

---

### Post by dengineer on 2020-03-22
Despite the changes you have suggested,(which I appreciate) the wireless behavior has not improved.  I appreciate your enlightenment about the Ralink driver status. There does seem to be a significant number of posts on this and other communities referring to similar and other problems with  Ralink wifi and/or HP PCs. But at least I now know that I am using the only driver available and that it is expected to be functional. 
One suggestion I have would be to improve, if possible, the error reporting for the wifi connection failure and for subsequent failure(s) to automatically re-establish the connection. Perhaps there is information in a log somewhere but if so it is not generally accessible.
To summarize my case:
[LIST]
[*]the only apparent common factors are the (internal HP laptop) Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter and the associated rt2800pci driver.
[*]the wireless connection fails, sometimes after hours of normal use and sometimes frequently, and almost without exception cannot succeed in automatically reconnecting.
[*]usually a suspend/restart brings up a working connection.
[*]this has persisted for a few weeks despite:
[*]replacing the router with a new one of a different brand;
[*]relocating the laptop to close proximity with the router;
[*]adjusting router wifi settings;
[*]adding a wifi range extender (which provides alternate uninterrupted wired connectivity to nearby devices but does not cure the wifi failures).
[*]upgrading Ubuntu 18.04 to 19.10.
[/LIST]
Throughout, a nearby desktop equipped with a D-Link WiFi adapter has been operating without fail on the same wifi connectivity with Ubuntu 18.04.

So for now I shall assume that the only viable wifi solution is to add a USB wireless adapter of recent vintage.

---

### Post by chili555 on 2020-03-22
Thr rt2800-series have a long and troublesome history as a Google search will clearly show. No thread that I've been able to find ends in 'Solved.'

We have used up our entire arsenal of tips and tricks. All that I can suggest is this:> 
a nearby desktop equipped with a D-Link WiFi adapter has been operating without fail Get another one, or one with the exact same chipset. You will probably also need to blacklist rt2800pci. 

I wish that I had a better recommendation.

---

