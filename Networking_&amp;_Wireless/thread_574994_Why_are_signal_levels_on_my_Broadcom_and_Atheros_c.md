---
title: "Why are signal levels on my Broadcom and Atheros cards vastly different?"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-10-13
On my laptop, I have 2 pcmcia slots where I have plugged in an** atheros card** (with madwifi drivers) and a **broadcom card** (with ndiswrapper).  The broadcom card is wlan0, and the atheros card is ath0.

iwlist scan reveals the following:

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:9E:B4:D8
                    ESSID:"Dorchester#2"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                   ** Quality:50/100**  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:15:E9:17:D9:68
                    ESSID:"Dorchester"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    **Quality:26/100**  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

ath0      Scan completed :
          Cell 01 - Address: 00:1C:10:9E:B4:D8
                    ESSID:"Dorchester#2"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                   ** Quality=27/70**  Signal level=-68 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101800003a4000027a4000042435e0062322f00
          Cell 02 - Address: 00:15:E9:17:D9:68
                    ESSID:"Dorchester"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    **Quality=15/70**  Signal level=-80 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f01010008ff7f

I find it odd that the atheros card reports the signal strength roughly 2/3 the value of the broadcom card.

I tried boosting the tx power of the atheros card (sudo iwconfig ath0 txpower ....), however Im topped out at 20 (which is the maximum I can do).  Do I have to chnge the country code of the card in order to boost the txpower, or do something else??  I there a test I can do to actually reveal if this suppossed difference in signal quality is actually measurable in any real way (ie does it effect bandwidth or download speed??)

Thanks

---

### Post by syxbit on 2007-12-26
signal strength is indirectly related to speed
a worse signal means you'll have to resend more packets that weren't correctly received.
i'm also surprised at your results, as i though atheros were supposed to be much better than broadcom

---

### Post by kevdog on 2007-12-27
Cant really explain it either, but when working on two computers with Gutsy side by side, the Atheros card seems to disconnect much more frequently than the Broadcom card.  Based on this experience I would recommend ndiswrapper/bcmwl5/Broadcom over madwifi/atheros/cisco networking.   Cant believe I am saying this.

---

### Post by syxbit on 2007-12-27
i actually would have to recommend the opposite :)
my new desktop had a built it wifi realtek. it connected on first boot and i was thrilled.
unfortunately it would just randomly disconnect every little while. sometimes minutes, sometimes hours.
i then was given a linksys wmp54g v2 from a friend. it's broadcom, and didn't work.
i got it working with ndiswrapper, and it connected fine, but after a reboot, it stopped (i tried modprobing etc...)
i finally just realized that my time is worth more than the price of a wifi adapter.
did a search [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")
and bought a D-Link WDA-2320. works PERFECTLY oob with gutsy's madwifi (.932 i believe)
and i paid $28 for it after rebate. I'm sure the whole super-g won't work. it's retarted, as who has the exact same router and wifi card. we all have laptops etc.. with different cards.

still. i learnt the hard way. it's not that difficult with a bit of searching to just buy linux compatible hardware. i still wish intel made a desktop wireless card (i'm sure they will soon) as they're the best, but i must say i'm very impressed with atheros. DL'd 10 gigs and 48 hours with no disconnects!
also, my atheros desktop card gets significantly worse reception than my intel 4965 on my thinkpad, but i can still get 10mbs downloads, so i can't complain.

i actually have been reading about the whole signal strength. I'm not sure it's that trustworthy. apparently there isn't some hard core rule for measuring, so each manufacturers' results can't be directly compared.

maybe you should try to compile madwifi from svn. it's pretty easy, and they have a howto on wiki.ubuntu.com
i'm sure the atheros is better than the broadcom junk!

---

### Post by thefirstM on 2007-12-27
I have noticed the same thing.  I used to have a Dlink DWL-G510 (Atheros AR5005g) and then I recently upgraded to an Intel 2915abg in a PCI-MiniPCI adapter, and now my signal strength is much better.

---

### Post by tturrisi on 2007-12-27
Signal level reporting is handled by the adapter driver.  The drivers contain code that calculates signal levels.  There are standards for signal level calculations but not all chipsets and drivers implement the same standard signal level functionality.  You cannot always rely upon the reported signal levels.

Signal strength is defined in 802.11 as the Received Signal Strength Indicator
(RSSI). RSSI, is intended to be used as a ‘relative value’ within the
chipset. This is a 1-byte value so that it could have values ranging from
0 to 255, but vendors prefer to use arbitrary scales from 0 to RSSI_Max
where the latter is vendor-specific (for instance, Cisco uses 101, Symbol
31, Atheros 60). It is not associated with any particular power scale
(e.g. mW) and is not required to be of any particular accuracy or
precision. The RSSI value is used internally by the microcode in the
adapter and this is why vendors are not forced to use a compatible
standard. As an example of its use, if the RSSI value is below some
threshold, the NIC knows that the channel is idle. Therefore, the signal
strength numbers reported by an 802.11 card will probably not be
consistent between two vendors, and should not be assumed to be particularly
accurate or precise.

---

### Post by kevdog on 2007-12-27
I know signal strength is an unreliable indicator -- Im basing my recommendation on signal drop and the need to reconnect.  The two computers (laptops) are sitting right next to each other.  Sure ndiswrapper broadcom is harder to get going, but Im talking about performance.  I have no idea how manufacturing construction differs when the same chipset is involved.  Anyway I thought I would pass this along.  Any other have any other objective measurements how to judge and quantify performance, number of dropped packets, etc.

I always compile from svn - ndiswrapper, madwifi, and pretty much any other thing I can get my hands upon.

---

