---
title: "force wlan frequency on atheros card"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by natirips on 2008-02-12
I have an Atheros wireless networking card, lspci say the following:
```
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```
And iwconfig usually says following:
```
natirips@natirips-laptop:~$ iwconfig 
lo        no wireless extensions.

eth73     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.472 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
Which, doesn't work.
I've noticed that on rare occasions when my wlan works that frequency is 2.412 Ghz
```
wlan0     IEEE 802.11g  ESSID:"PRE"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:01:E3:CD:BD:D6   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1159186  Invalid misc:2486624   Missed beacon:0
```
I've tried "sudo iwconfig wlan0 freq A B" (where A is either "2.412G" or "2412000000" and B is either "commit" or nothing - I've tried all combinations), but iwconfig output doesn't change....

Edit: It's 64-bit Ubuntu Gutsy 7.10, using windows drivers via ndiswrapper.

So, is there any other way to force my wlan frequency?

---

### Post by rustybronco on 2008-02-12
> **natirips said:**
> I have an Atheros wireless networking card, lspci say the following:
```
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```
And iwconfig usually says following:

wlan0     IEEE 802.11g  ESSID:off/any  
          **Mode:Managed**  Frequency:2.472 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/CODE]
Which, doesn't work.

I've tried "sudo iwconfig wlan0 freq A B" (where A is either "2.412G" or "2412000000" and B is either "commit" or nothing - I've tried all combinations), but iwconfig output doesn't change....

Edit: It's 64-bit Ubuntu Gutsy 7.10, using windows drivers via ndiswrapper.

**So, is there any other way to force my wlan frequency?**

[http://maemo.org/development/documentation/man_pages/iwconfig.html](http://maemo.org/development/documentation/man_pages/iwconfig.html)

> freq/channel  
  Set the operating frequency or channel in the device. A value below 1000 indicates a channel number, a value greater than 1000 is a frequency in Hz. You may append the suffix k, M or G to the value (for example, "2.46G" for 2.46 GHz frequency), or add enough '0'. 
Channels are usually numbered starting at 1, and you may use iwlist(8) to get the total number of channels, list the available frequencies, and display the current frequency as a channel. Depending on regulations, some frequencies/channels may not be available. 
**When using Managed mode, most often the Access Point dictates the channel and the driver may refuse the setting of the frequency.** In Ad-Hoc mode, the frequency setting may only be used at initial cell creation, and may be ignored when joining an existing cell. 
You may also use off or auto to let the card pick up the best channel (when supported). 
Examples : 
        iwconfig eth0 freq 2422000000 
        iwconfig eth0 freq 2.422G 
        iwconfig eth0 channel 3 
        iwconfig eth0 channel auto 

So I believe no you can not.

If you need it [http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

---

### Post by natirips on 2008-02-13
That was of no use :(, because MadWifi (whatever version/tutorial/howto/whatever I used (tried to use) didn't work at all. Ndiswrapper acctually works sometimes (when it feels like it). I used drivers from the disk I got with my computer (64-bit Windows XP version (I refuse to even try something as unholy as Vista drivers), because I use 64-bit Ubuntu). But thanks anyway, I'll just keep on depending to my luck :S.

---

### Post by rustybronco on 2008-02-13
Well you can always get a compatable card that works to to keep your system "holy".

---

### Post by natirips on 2008-02-13
> **rustybronco said:**
> Well you can always get a compatable card that works to to keep your system "holy".

Lol, but it's a laptop...

---

