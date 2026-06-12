---
title: "CNet CWC-903 (Ralink RT2600 chipset) in Edgy problems"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by unprinted on 2006-10-27
This CardBus wireless adapter was called network device ra0 in Dapper ...and never worked for me. Sometimes just having the card installed meant the laptop wouldn't finish booting into Dapper.

It's now detected as wlan0 and unknown device wmaster0 ..and still doesn't work, with no LEDs (showing 'working'/Rx/Tx) lit. It doesn't stop it booting though, so that is an improvement over Dapper :)

The home page of Ralink's site makes a fuss about the chipset, but there don't seem to be any drivers for it there. 

Needless to say, the thing works under Windows XP, grrr.

The card: [http://www.cnet.com.tw/product/cwc-903.htm]("http://www.cnet.com.tw/product/cwc-903.htm")

lspci's output: 02:00.0 Network controller: RaLink Ralink RT2600 802.11 MIMO

---

### Post by unprinted on 2006-10-27
sudo iwconfig's output:

wmaster0  IEEE 802.11g  Frequency: 2.412 GHz  
          RTS thr: off  Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"[my essid]"  
          Mode:Managed  Frequency: 2.412 GHz  Access Point: Not-Associated   
          RTS thr: off  Fragment thr=2346 B   
          Encryption key: off

---

### Post by marytgras on 2006-10-28
I have a Belkin wireless card with the same RT2600 chipset, I get the exact same lspci output, except I am getting a power light when I boot up Edgy.  Let me know if you find anything else.

---

### Post by unprinted on 2006-11-05
> **marytgras said:**
> Let me know if you find anything else.

See the big thread at [http://ubuntuforums.org/showthread.php?t=285072](http://ubuntuforums.org/showthread.php?t=285072) - it works for me (this is being done over the wireless network...)

---

