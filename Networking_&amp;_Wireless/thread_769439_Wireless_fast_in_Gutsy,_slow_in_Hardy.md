---
title: "Wireless fast in Gutsy, slow in Hardy"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by daniel_summers on 2008-04-26
I upgraded my Averatec 6240 laptop to Hardy (8.04) yesterday, and since then, my wireless connection has been about half the speed it used to be when I was running Gutsy (7.10).  The connection is now so slow that I can't stream video from YouTube or other streaming flash video sites.  Before the upgrade, KNetworkManager showed 4 of 4 bars most of the time, and it would dip to 3 occasionally.  Now, I'm lucky to get 2.

Where would I begin to look to determine where the slowness is?  Here's the lspci for my network card...

00:0e.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

Thanks...

---

### Post by daniel_summers on 2008-04-27
More information - I think I've determined the "why" on the slowness.  Here's the output from iwconfig

ra0       IEEE 802.11g  ESSID:"NextelCup"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: [mac-address]
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=51/100  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The "Bit Rate" is set at 1 Mb/s!  So, I guess it's 53x slower than before... :)  Anyway, here's the iwlist scan for the "NextelCup" network.

ra0       Scan completed :
          Cell 01 - Address: [mac-address]
                    ESSID:"NextelCup"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=72/100  Signal level=-46 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000071c708b9f0

I'm guessing that the driver is set up to auto-negotiate speeds - but all the other computers in the house are running at 54 Mb/s, so I don't think it's an issue with the router.  I haven't done any special tweaking in any configuration files, so it should be taking the defaults.

I tried reconnecting to the network, but got the same thing.  It's almost like it had trouble at one time, and now it's remembering that and not even trying to connect at a higher speed.  The dmesg from the reconnect looks good, except for the last line.  I'm not positive, but I don't think I've seen that there before.

[16768.243601] ra0: Initial auth_alg=0
[16768.243607] ra0: authenticate with AP [mac-address]
[16768.244244] ra0: RX authentication from [mac-address] (alg=0 transaction=2 status=0)
[16768.244248] ra0: authenticated
[16768.244250] ra0: associate with AP [mac-address]
[16768.245515] ra0: RX AssocResp from [mac-address] (capab=0x431 status=0 aid=2)
[16768.245518] ra0: associated
[16768.245522] ra0: switched to short barker preamble (BSSID=[mac-address])

Does this help inspire any ideas?

---

### Post by corneel on 2008-04-27
I cannot help you. I have the same troubles. And the Ubuntu/Canonical people? They are silence and ceeping a low profile! The act like Microsoft; Troubles with wireless? I do not know...

---

### Post by daniel_summers on 2008-04-27
Well, it is the weekend, and I imagine that they're quite busy with support.  The advice I've received here in the past is always worth more than I paid for it.  :)  The fact that we're both having the same problem is a good sign - if it's a common problem, it will probably be addressed more quickly.

---

### Post by ogregore on 2008-04-27
This is an ongoing problem since Hardy was in Alpha.  If you search RT2500 you will find numerous threads concerning the slow down.  Most people seem to be either installing the RT2500 module from the serialmonkey website or on the short term you may get some speed up by entering the following from the terminal:

sudo iwconfig ra0 rate 54M

Cheers
Ogre

---

### Post by daniel_summers on 2008-04-27
> **ogregore said:**
> This is an ongoing problem since Hardy was in Alpha.

Heh - wonder what changed?

Thanks for the iwconfig command - that worked!  I'll look into that other module.

---

### Post by ogregore on 2008-04-27
Gutsy used the legacy RT2500 driver and Hardy uses RT2500pci which is a bit wonky, but I think they are working on it for the next kernel.

Cheers
Ogre

---

### Post by Akita on 2008-04-27
Same issue here. Gutsy used the rt2x00 driver and worked great, Hardy loads the rt2500pci and won't go above 1Mbps. I tried to force it to use the rt2x0pci driver. It loads but doesn't work. God thing I have an extra Intel card lying about. My wired driver is toast too. I find it rather hard to believe that Hardy shipped with both of these borked drivers when the issues were KNOWN during the beta. 

<rant>
Would it have been that difficult to ship it with the slightly older, known-to-work drivers instead of the known-to-not-work ones?
</rant>

*sigh*

---

