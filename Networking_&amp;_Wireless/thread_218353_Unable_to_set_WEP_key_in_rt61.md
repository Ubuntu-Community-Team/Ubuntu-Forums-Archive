---
title: "Unable to set WEP key in rt61"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by kevin.gibbs on 2006-07-18
uname -r: 2.6.15-23-amd64-generic (Dapper 6.06)
Wifi NIC: Edimax EW-7128G PCI (rt2561/rt61 chipset apparently)
lspci: 0000:04:09.0 Network controller: RaLink: Unknown device 0301
lspci -n: 0000:04:09.0 0280: 1814:0301
driver: rt61-cvs-2006071513 (rt61 PCI/PCMCIA nightly CVS tarball from [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com))
-----------------------------------------------------

Hi Everyone,
Hope someone out there can help me out (both the wall and my head are feeling it now!)

If I turn off all security on the router I am able to connect/ping etc OK.  

However, turn on WEP (both 64/128 bit), I am unable to do anything.

Now, here's the strange bit:
If I perform "iwconfig ra0 key XXXX-XXXX-XX" and then "iwconfig ra0" - the key appears briefly:
  ra0       RT61 Wireless  ESSID:"gibbs"
            Mode:Managed  Frequency:2.437 GHz  Access Point: XX:XX:XX:XX:XX:XX (not the real AP of course)
            Bit Rate=54 Mb/s
            RTS thr:off   Fragment thr:off
            Encryption key:AABB-CCDD-EE   Security mode:open
            Link Quality=82/100  Signal level:-59 dBm  Noise level:-79 dBm
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
(Obviously "AABBCCDDEE" is *not* the key I'm using - but, I've left the correct ssid in for a reason...)
--------
Now, wait a few seconds and take another look:
  ra0       RT61 Wireless  ESSID:"gibbs"
            Mode:Managed  Frequency:2.437 GHz  Access Point: XX:XX:XX:XX:XX:XX
            Bit Rate=54 Mb/s
            RTS thr:off   Fragment thr:off
            Encryption key:0069-6262-73   Security mode:open
            Link Quality=80/100  Signal level:-59 dBm  Noise level:-95 dBm
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Notice how the key has changed?!
And here's the interesting bit, "69-6262-73" translates to "ibbs" - the last four chars of my ssid!!!
--------
And a few seconds later:
  ra0       RT61 Wireless  ESSID:"gibbs"
            Mode:Managed  Frequency:2.437 GHz  Access Point: XX:XX:XX:XX:XX:XX
            Bit Rate=54 Mb/s
            RTS thr:off   Fragment thr:off
            Encryption key:0001-1000-00   Security mode:open
            Link Quality=76/100  Signal level:-59 dBm  Noise level:-95 dBm
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
--------
"iwlist ra0 key" kinda mirrors iwconfig:
  ra0       2 key sizes : 40, 104bits
            4 keys available :
                  [1]: AABB-CCDD-EE (40 bits)
                  [2]: off
                  [3]: off
                  [4]: off
            Current Transmit Key: [1]
            Security mode:open
----------
Then:
  ra0       2 key sizes : 40, 104bits
            4 keys available :
                  [1]: 0001-1000-00 (40 bits)
                  [2]: off
                  [3]: off
                  [4]: off
            Current Transmit Key: [1]
            Security mode:open
-----------
You guys are my last hope now - I've wasted far too much time on this and I'm about to buy another card.

P.S. The problem cannot be at the gateway end because I also have a SuSE 10.1 machine and my son's XP machine (grrr) both with rt2500 pci cards and connecting OK.

Many, many thanks - Kevin

---

### Post by kevin.gibbs on 2006-07-18
Mmm,
Looks like this may be a bug -
[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=1640&sid=4992dab1d4e6206ae0ffa2d153e95951](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=1640&sid=4992dab1d4e6206ae0ffa2d153e95951)

The above thread states that this problem is not in the stock RT61_Linux_STA_Drv1.0.4.0 driver - unfortunately for me that driver crashes the kernel (seem to remember reading somewhere that it was a problem with the 64bit version)

---

