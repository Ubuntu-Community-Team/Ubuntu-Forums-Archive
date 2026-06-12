---
title: "Unstable wireless network - WPA/PSK, Ndiswrapper..."
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by FokkerCharlie on 2007-11-26
Hi all

I've been trawling through the forums and irc channels looking for, and often getting (particularly from Wieman and Jo-Elend), some help with problematic wireless networking.

Here's what I have:

An Acer Aspire 1500 laptop
AMD Athlon 64 3000+ (1800MHz)
1.25GB RAM
40GB HDD
ATI Mobility Radeon 9600
Ubuntu 7.10, i386 edition.

I'm using an un-branded wifi PCMCIA cardbus device, with a Texas Instruments ACX111 chipset.  It works splendidly under WinXP, connecting with my (unlocked) BT Voyager 2091 ADSL Modem/Wireless router.

I have been able to install Ndiswrapper for the card, the Ndiswrapper GUI reports that the hardware is present, and its happy- I have tried the drivers both from the Ndiswrapper website and from my own Windows partition, with the same results.

All is OK initially, manually configuring Network Manager finds my WPA network, and connects to it.  Then, after about 2-4 minutes, the connection seems to be lost.  I can re-start the connection using sudo /etc/init.d/networking restart , but that isn't a workable solution for the long-term.  At all times, Network manager can see my WPA network (as well as the other handful in the area), but doesn't want to connect to it without the re-start.  I have had the same result in WICD.

I have tried the Ndiswrapper 'howto'
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%20ndiswrapper%20#9995987539050855161](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%20ndiswrapper%20#9995987539050855161)
and also Wieman's guide:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
Which have both been helpful, but I am still left with an unstable wifi connection!

So it looks to me like:
Ndiswrapper is working.  My WLAN card can communicate with Network Manager.  But from there, I'm a bit stuck.

The router supports WEP (64 and 128 ), WPA, WPA-PSK, WPA2, WPA2-PSK, Mixed WPA2/WPA, Mixed WPA2-PSK/WPA-PSK.  Ideally, I will leave the security as it is if possible, as I need it for my Windows partition, and for my Wii!

I'm  effectively a Linux noob, so please be patient- I'm doing my best!

Very grateful for any input.
Charlie

---

### Post by kevdog on 2007-11-26
This is a tough one -- although you have done a good job of describing the problem -- very thorough.  Most likely its going to be a driver issue -- and frankly I don't really know what you can do about that, short of getting a wrieless card with a different chipset.

Does the problem occur when using an unencrypted or WEP encrypted connection?  I'm just trying to isolate if this is really a driver problem or more of a WPA problem.

Second try making the connection manually at the command line (see my signature for a how-to) -- hopefully this will produce something useful in terms of output.

When you do a iwlist scan, is the signal strength reported really low??  Are there any interfering things in the way as far as cordless phones or microwaves.  Because you are using ndiswrapper as an emulation layer in order to use windows drivers on linux, do not expect the same performance and reliability that you have on the windows.

After the wireless disconnects, can you also check dmesg to see if anything is reported as the source of the error.

---

### Post by FokkerCharlie on 2007-11-26
Hi Kevdog

I'll have a look at WEP in a bit- although this is definitely not what I'd like to do...

The last few lines of dmesg:

[ 1927.132000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1928.448000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1938.520000] wlan0: no IPv6 routers present
[ 1972.288000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1973.696000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1984.184000] wlan0: no IPv6 routers present
[ 2057.292000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2058.560000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2068.900000] wlan0: no IPv6 routers present

The results of the scan (edited to show just my router):

wlan0     Scan completed :
          Cell 01 - Address: 00:16:E3:13:30:B9
                    ESSID:"CharlesNet"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK

There is a cordless phone in harm's way, however unplugging it and turning the handset off resulted in no improvement. The microwave is off!

I'll also have a look at your manual instructions, will get back to you in a bit.

Cheers
Charlie

---

### Post by wieman01 on 2007-11-26
There a few things you can do, although I have to agree with Kevdog in that this is a tough one...

1. Change the (wireless) channel as there could be interference with other networks on the same channel around you.
2. Reducing the default beacon interval value to something between 20 and 40 ms.
3. Change other settings such as RTS threshold, etc.

To give you an example if have attached a screenshot of my settings. What are your values right now?

I used to have the same problem but increasing the default beacon interval (to 20 in my case) seems to have solved the problem for me. No more dropping connections.

---

### Post by kevdog on 2007-11-26
I dont play with my router settings all that much, so you would be better off listening to Weiman.  Using channels 1 or 11 would probably be your best bet to avoid interference.

I have used dd-wrt on my linksys router to boost the transmission power -- this worked well for me in terms of boosting the signal.  Your relative signal strength is 56/100 so I dont know if this would help you.

Again as far as changing to WEP for the meantime, its only to see if its a driver issue or a WPA issue.  Its not meant to be a permanent solution.  If your card drops with WEP encryption its most likely a driver/hardware issue.

Try also turning off or disabling IPv6.  IPv6 is a funny beast.  It can cause a lot of people random problems.

Here is a link: [http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

---

### Post by FokkerCharlie on 2007-11-26
Gents

It looks light we *might* have cracked it- I've changed the channel from 1 to 7 (before I saw your advice about 11, Kevdog!), and I have been online for 25 mins- about 23 more than my previous effort!

I'll keep monitoring, but hopefully that's it.

Watch this space!
Charlie

---

### Post by wieman01 on 2007-11-26
> **kevdog said:**
> I have used dd-wrt on my linksys router to boost the transmission power -- this worked well for me in terms of boosting the signal.  Your relative signal strength is 56/100 so I dont know if this would help you.
Good point... That would be worth a try as well.

---

### Post by FokkerCharlie on 2007-11-28
Hi Wieman, Kevdog

It's looking good here- my connection is now rock-solid, so I'm happy!

The trick seems to have been with to use Ndiswrapper, and changing the channel of my router.

I don't know what dd-wrt is, and I haven't been able to find/change the beacon interval, RTS etc- but I have to admit, I'm not too worried about that!

Many thanks again for your help.
Charlie

---

### Post by wieman01 on 2007-11-28
Check this out if you are interested... DD-WRT is a great firmware for Linksys and other routers:

[http://www.dd-wrt.com/dd-wrtv2/index.php]("http://www.dd-wrt.com/dd-wrtv2/index.php")

I used it and I am very happy with it, particular with "Quality of service" which works great. But that's a different topic.

---

