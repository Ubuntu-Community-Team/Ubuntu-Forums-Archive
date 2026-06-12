---
title: "Linksys WMP54G problem (almost connected)"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by aqualad on 2007-03-21
I bought a new WMP54G wireless Linksys card because I read online that it would work out-of-box with Edgy Eft, but unfortunately I got the 4.1 revision.

After multiple attempts at installing drivers using wiki's I came very close by using ndisgtk (A visual front-end for ndiswrapper), but that too ended up failing when the wlan0 interface just up and disappeared after a few minutes.

After those failed attempts I tried a fresh install of edgy with the card already installed, and surprisingly it works...well...almost.

Here's what I can do

```
aqualad@austin:~$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

wmaster0  No scan results
wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:43:0E:B9
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz
                    Encryption key:on
                    Extra:tsf=000000148a502184

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.
```

```
aqualad@austin:~$ iwconfig
lo        no wireless extensions.

wmaster0  IEEE 802.11g  ESSID:""
          Mode:Master  Frequency:2.412 GHz
          RTS thr:off   Fragment thr=2346 B

wlan0     IEEE 802.11g  ESSID:"linksys"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          RTS thr:off   Fragment thr=2346 B

eth0      no wireless extensions.

sit0      no wireless extensions.
```

```

aqualad@austin:~$ lspci | grep 802
02:0b.0 Network controller: RaLink RT2561/RT61 802.11g PCI

```

```
aqualad@austin:~$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:f8:34:1a:86
Sending on   LPF/wlan0/00:18:f8:34:1a:86
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
```

It does the last snippet of code about 5 times before it says "No DHCPOFFERS received.  No working leases in persistent database - sleeping."


All of these commands were run on a fresh install with no work on the drivers, I believe they were autodetected.

My router is a linksys WRT54G with the ESSID linksys and a 128-bit encrypted hex password.

Any help is appreciated :]

---

### Post by gm333tb on 2007-03-22
I second the request.  I have the identical setup, WRT54G and WMP54G.  Brand new to Linux.  Computer with router runs windows XP until I get comfortable with Linux.  Second desktop (Linux Guinne Pig) runs Ubuntu 6.10.  I have no clue how to get connected.  Tried to use Linksys install CD with no luck, Linux won't read it.  Is this becasue it is for windows only?  Installed card in Linux computer and tried to enter info in the network settings per the instructions.  No luck.  Any and all input is appreciated.

---

### Post by aqualad on 2007-03-22
I can tell you this, try
```
iwconfig
```

and if it returns one of your interfaces as wlan0 or wmaster0 or even eth1 (Just so long as it isn't "no wireless extensions") then the card is recognized.

Try the following commands and post the results:

```
sudo iwlist scan
iwconfig
ifconfig -a
```

Good luck, hope this bump helps us :]

---

### Post by Frak on 2007-03-22
You must reinstall the Ralink RT2561/2661 Driver.  When the developers integrated the serial monkey drivers into edgy, they corrupted on bootstrapping. 

More info [here]("http://ubuntuforums.org/showthread.php?t=296822").

---

### Post by aqualad on 2007-03-23
I already tried that, but I've run into 2 issues. First, I can't find linux-headers for 2.6.17-6-386 and 2, even when I did find them a while back, for some reason I didn't have the folder /lib/modules/build, so the makefile wouldn't work.  I even tried switching it to /usr/src/build but that folder didn't exist either.  I'm pretty much stumped about how to get it working that way, though I did manage to get it up using ndiswrapper, but that would never grab the DHCP lease.

Anyone know how to help with the lack of /lib/modules/build folder? I have /lib/modules, just no /build

Thanks.

Edit: Also, should I update my kernel? and if so, how without a manual compilation? Thanks again.

---

### Post by Frak on 2007-03-23
what stumps me is the fact that, for some reason, mkdir has been disabled from use. It just returns this message.

```
mkdir etc/Wireless/Module
Could not create directory:Directory does not exist
```

---

### Post by MeeMaw on 2007-03-23
> **Frak said:**
> what stumps me is the fact that, for some reason, mkdir has been disabled from use. It just returns this message.

```
mkdir etc/Wireless/Module
Could not create directory:Directory does not exist
```

I had that problem once and it seems to me that I created the    /etc/Wireless   first and then changed directories to /etc/Wireless and  then created the /etc/Wireless/Modules from there. Also, with the Ralink rt61 driver, this post helped me lots

[http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

If you need help, just let us know.

---

### Post by Frak on 2007-03-23
That makes sense, it has the /etc directory, it wants the /Module directory, but you can't just skip the /Wireless/ directory, I just presumed that it would create the /etc/Wireless/ Directory by itself to fulfill the need for the /etc/Wireless/Module directory, thanks for the response, this should solve my problem. :)

---

### Post by Frak on 2007-03-23
> **MeeMaw said:**
> I had that problem once and it seems to me that I created the    /etc/Wireless   first and then changed directories to /etc/Wireless and  then created the /etc/Wireless/Modules from there. Also, with the Ralink rt61 driver, this post helped me lots

[http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

If you need help, just let us know.
Thank you so much, I finally got my wireless interface up and am compelled to write a script for people that have the same problem. :)

---

### Post by MeeMaw on 2007-03-23
Excellent!!!!    I'm so glad!
The script would be great -
(and if you could amend the title of this post saying "solved" or something like that I'm sure it would help others.)

:)

---

### Post by Frak on 2007-03-23
Hopefully I can get Aysiu to help :), He is definitely the master at creating scripts :guitar:

---

### Post by Frak on 2007-03-23
> **MeeMaw said:**
> Excellent!!!!    I'm so glad!
The script would be great -
(and if you could amend the title of this post saying "solved" or something like that I'm sure it would help others.)

:)

Heres the script I said I'd make, since the RT61 Driver is under the GPL, I included it in this file.

1. Just untar this into your ~/ directory, and run
```
sudo sh configure.sh
```
And follow the instructions in the README afterward, kinda buggy, but it works.

Good Luck! :guitar:

---

### Post by beuh_dave on 2007-03-25
> **Frak said:**
> Heres the script I said I'd make, since the RT61 Driver is under the GPL, I included it in this file.

1. Just untar this into your ~/ directory, and run
```
sudo sh configure.sh
```
And follow the instructions in the README afterward, kinda buggy, but it works.

Good Luck! :guitar:
Thanks frak! Your help and script are awesome. I had the exact same problem as aqua! I was about to give up on Ubuntu, hahaa... I did everything as you said, I commented out "/etc/network/interfaces" and ran the script, it ran flawlessly... I just want to add for anyone else using this script that the "rt61sta.dat" which one must edit to configure the SID and so forth is located at "/etc/Wireless/RT61STA". 

With the default drivers installed with Edgy, when i ran "sudo iwlist ra0 scan" it returned 2 wireless networks.. now with the new drivers, it returns 35 wireless networks.. I can't be happier!!

My warmest salutations! Everything works perfectly.. Thank you Frak again! :)

---

### Post by Frak on 2007-03-25
Your welcome, I made an updated script [here]("http://ubuntuforums.org/showthread.php?t=392017"), it does just about everything now on that script, this one does the job, my new one configures some basic settings needed.
And I'm glad to have made the script, feels good to have helped the community, instead of profiting off of one. :) :guitar:

---

### Post by aqualad on 2007-03-26
Wow, okay, so I finalyl got it all finished and solved.

Once I updated to 2.6.17-11-386 I got the /lib/module/<kernel>/build folder I needed, from there the how-to guide got me through, though I did get stuck for a couple of hours on configuring the rt61sta.dat file for WEP.  It ended up being a mistake I made on my first attempt to configure the file.  I changed a 0 to a 1 and bam, it-no-worky for 3 hours because of that.

If anyone has any questions about getting this up and working I might be able to help now (seeing as how I made almost every mistake possible along the way)

Good luck all, and thanks for the guidance :]!

---

