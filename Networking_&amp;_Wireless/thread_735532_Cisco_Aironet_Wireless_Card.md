---
title: "Cisco Aironet Wireless Card"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by bluefly on 2008-03-25
Hi!

I've tried to install Ubuntu on my Thinkpad T41.  The only thing that doesn't work is the wireless.  However, I would like to see if I can make it work.

My wireless card is a Cisco Aironet 802.11b.

When I use the network manager to connect to my network (with WEP encryption, shared key), it asks for the WEP passphrase which I give it.  Then it proceeds to "get the Network key," but never gets further than that.  I've tried putting in the Hex key instead of just the passphrase to no avail.  Is there something else I can do?  I've also tried manually configuring it (by going to System->Network, etc), but that has not worked either.  Connecting with a wired connection, of course works.

Thinkwiki says that there should be no problem in connecting.  I am using Ubuntu 7.04.  I am somewhat computer literate (i.e. I have written numerous perl scripts and one large c program.  I work on a linux system at school, but do not ever install anything (unless perl modules count)).

Thanks so much.

* I just realized I asked this exact same question a little less than a year ago!  There was no response then; maybe by now someone has figured it out?*

---

### Post by dstew on 2008-03-25
It seems that the card is working, in that it shows up in your System --> Administration --> Network window. I would guess it is a configuration issue. Can you connect to a non-encrypted access point?

---

### Post by bluefly on 2008-03-25
I have no problems connecting to an unencrypted network.  It's just when I have to put in a key that things go haywire.

---

### Post by dstew on 2008-03-26
I think you should look carefully at the encryption configuration. Are you sure it is WEP **shared  key**? 64 or 128 bit?

---

### Post by bluefly on 2008-03-26
It's definitely a WEP shared key (128 bit).  I tried to switch my network to open authentication to see if I could then connect, but no dice.

Thanks so much for your replies.

---

### Post by dstew on 2008-03-26
I am running out of ideas. Disable roaming and see if that makes a difference.

---

### Post by chili555 on 2008-03-26
Does it connect if you do the old-fashioned way? Open a terminal and do:```
sudo iwconfig eth1 ssid your_ssid
sudo iwconfig eth1 key 096c7fxxx restricted
```Substitute your *hex* key here. Tell iwconfig you use a shared key with the word 'restricted.' Then do:```
sudo dhclient eth1
```Does it connect or time out?

---

### Post by bluefly on 2008-03-26
No, it just times out.  Here is the output:

There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:0e:9b:43:f7:05
Sending on   LPF/eth1/00:0e:9b:43:f7:05
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by bluefly on 2008-03-26
Also, is there some special way I should be inputting the hex key?  i.e. should I be using colons instead of dashes (-) every 4 characters?  (I also tried with no additional punctuation)

Disabling roaming didn't help.  I understand this might not work, but thanks for answering my questions.

---

### Post by chili555 on 2008-03-27
According to *man iwconfig* you can put your key in with dashes or no punctuation at all. I put mine in with no puntuation, like 096c7f280b1154c...etc.

If you are sure you are using 128-bit hex, are you sure you are using 26 characters? Have you double-checked the exact name of the SSID? For example, Linksys is not the same as linksys is not the same as LINKSYS. The best way to make certain is to scan:```
sudo iwlist wifi0 scan
```If your SSID has spaces in it, then you must put quotes around the name, thus:```
sudo iwconfig essid "My Router"
```

I just noticed that I accidently used 'ssid' above, when, according to *man iwconfig*, it should be **essid**. I'm sorry.

---

### Post by bluefly on 2008-04-04
Sorry, I've taken so long to reply (you've maybe moved on to more interesting things than my wireless problems).  I've checked both of those things.  My hex key is 26 characters and the ESSID has no spaces.  Also, I knew that you meant essid.  Is there something else I can try?

My computer is definitely picking up on the wireless signal of my network.  It just won't let me on.  Maybe I'm SOL.

---

### Post by chili555 on 2008-04-04
Please humor an old geezer and try these commands:```
sudo iwconfig eth1 essid <your_essid>
sudo iwconfig eth1 key <your_26_character_key> **open**
sudo dhclient eth1
```Did you get an IP address or time out?

I know you said 'shared key' but let's satisfy ourselves that neither 'restricted' nor 'open' is the problem.

To me, hardly anything is more interesting than wireless!

---

### Post by bluefly on 2008-04-04
nope, no bananas.  Here's the output (almost same as before):

There is already a pid file /var/run/dhclient.pid with pid 7536
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:0e:9b:43:f7:05
Sending on   LPF/eth1/00:0e:9b:43:f7:05
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I've been searching around these forums, and found this thread; the last comment seems to say it's a driver issue (and therefore something I can't fix?):

[http://ubuntuforums.org/showthread.php?t=89517](http://ubuntuforums.org/showthread.php?t=89517)

My card isn't exactly the one they are talking aboutm, but it's from the same era (i.e. old Cisco Aironet).

---

### Post by chili555 on 2008-04-04
I'm almost sure it"s not a driver issue since I am answering this on an IBM Thinkpad T40 using a Cisco Aironet 350! I suppose it could be a firmware issue, but I doubt that, too.

When I installed Ubuntu on this old girl, I simply issued the commands I recommended to you:```
sudo iwconfig eth1 essid your_ssid
sudo iwconfig eth1 key 096c7fxxx restricted
sudo dhclient eth1
```And I was connected. I did no other configuration. So the Aironet does work.

Either the ESSID is wrong, the key is wrong or restricted vs. open is wrong. You might check to be sure the router is set to issue enough DHCP addresses. Did you double-check that the ESSID is correct with:```
sudo iwlist eth1 scan
```You might have a look at:```
cat /proc/driver/aironet/eth1/Status
```See if there is anything fishy in there. For reference, my firmware is 5.20.17.

---

### Post by bluefly on 2008-04-04
My network shows up in the scan (pertinent pasting):

Cell 04 - Address: 00:E0:98:C0:C2:15
                    ESSID:"PSJB"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-39 dBm  Noise level:-100 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=200

Here's the output about the driver:

i@ubuntu:~$ cat /proc/driver/aironet/eth1/Status
Status: CFG ACT SYN PRIV KEY WEP 
Mode: 39f
Signal Strength: 100
Signal Quality: 25
SSID: PSJB
AP: 
Freq: 0
BitRate: 11mbs
Driver Version: airo.c 0.6 (Ben Reed & Javier Achirica)
Device: 350 Series
Manufacturer: Cisco Systems
Firmware Version: 5.41
Radio type: 2
Country: 0
Hardware Version: 28
Software Version: 541
Software Subversion: 0
Boot block version: 159


Just for kicks, I changed the key at my router to a hex key that I made up and saved.  I then tried that one with "iwconfig eth1 key xxx restricted" it still didn't work.  I also tried a text passphrase using "key s:passphrase", but that didn't work either.  

I'm going to try to reset the key one more time just in case I did something wrong last time.  Thanks for your help; it does make me feel better that your wireless works with the same computer.

---

### Post by chili555 on 2008-04-04
I just saw this: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/44733](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/44733)

Please try our favorite commands again, but add the [1]:```
sudo iwconfig eth1 essid PSJB
sudo iwconfig eth1 key **[1]** 096c7fxxx restricted
sudo dhclient eth1
```

I notice you have firmware 5.40 and I have 5.20.17.

I am still looking.

---

### Post by bluefly on 2008-04-04
Ok, so I found this thread:

[http://ubuntuforums.org/showthread.php?t=318884](http://ubuntuforums.org/showthread.php?t=318884)

Which made the same suggestion as yours with the addition of the [1].

Wait, it TOTALLY WORKED!!  Thanks so much for your patience with me.  You are awesome.

---

### Post by chili555 on 2008-04-04
Thanks for your kind words. Glad it's working. Are you ready to commit this to permanent? If you just use the machine around home, we can make all the commands permanent. If you roam, it's a bit trickier.

---

### Post by bluefly on 2008-04-04
If you know of a link to some instructions on what to do if you roam (like I want to use my laptop at Starbucks or something) that would be cool.  However, I primarily boot into Ubuntu when I'm doing work at home, so I'm not often roaming.  I'd rather make it permanent so that every time I turn on my computer, it connects to my network.

---

### Post by chili555 on 2008-04-07
NetworkManager is supposed to do a good job at roaming but I'm not a fan. I read lots of posts where users just can't connect. A GUI approach that seems to work better is Wicd.  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

As you may have gathered from my 'terminal command' approach, I do exactly what Wicd or NetworkManager does, but from the command line. I do ```
sudo iwlist eth1 scan
```Once I see the ESSID I want, with 'key: off' I do:```
sudo iwconfig eth1 essid STRBUX
sudo iwconfig eth1 key off
sudo dhclient eth1
```

To make your settings for home permanent, *sudo gedit /etc/network/interfaces* to make your eth1 lines look like:```
auto eth1
iface eth1 inet dhcp
wireless-essid PSJB
wireless-key [1] 096c7fxxxx restricted
```You can safely remove any other stanzas **except** lo, eth0 and wifi0. Be sure to save the file and close. Your wireless should connect at home automagically.

---

### Post by yukonho on 2008-04-26
I fixed it this way, which should still work even if the kernel gets updated (I think). Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

This fixed wireless on my Cisco Aironet 350 and eliminated the hang during boot.

---

### Post by jwander on 2008-04-27
Same problem (hang during boot) and same fix (blacklist...) for me.

This problem appeared only after updating to hardy, gutsy was working fine out of the box on my system (Cisco Aironet 350 on Thinkpad R50e).

---

### Post by dcu693 on 2008-04-27
> **yukonho said:**
> I fixed it this way, which should still work even if the kernel gets updated (I think). Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

This fixed wireless on my Cisco Aironet 350 and eliminated the hang during boot.BIG THANK YOU to yukonho! I had been going nuts figuring out why the wireless on my T41 was no longer working even though it worked fine in Gutsy.

---

### Post by bluefly on 2008-04-27
> **yukonho said:**
> I fixed it this way, which should still work even if the kernel gets updated (I think). Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

This fixed wireless on my Cisco Aironet 350 and eliminated the hang during boot.
Thanks so much yukonho!  I just installed Hardy Heron, and my wireless card wouldn't even show up.  So I checked back into this old thread I started, and my question was answered without anyone having to ask it!!  These forums rock.

---

### Post by cgcedisto on 2008-04-29
> **yukonho said:**
> I fixed it this way, which should still work even if the kernel gets updated (I think). Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

This fixed wireless on my Cisco Aironet 350 and eliminated the hang during boot.

Thanks for this fix, worked for me. I am surprised however that 8.04 LTS got out with this problem, from reading the bug report the problem was identified during beta. After an upgrade to a new release, the last thing you want to happen is have your machine hang on the reboot. Bad. Wonder how many Cisco Aironet users fell into this hole?

---

### Post by DarrenCT on 2008-04-30
Thanks yukonho! .. this worked on my T41 with my Aironet wireless on board card!

02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b

---

### Post by speedster239 on 2008-05-26
I´m certain this is a gravedig but I can feel good unless I think you yukonho.

This helped (on an IBM T30):
-Remove boot-hang (which was a pain)
-Allow my volume controls to be recognized
-Allow my Aironet 350 Series Adapter (AIR-PCM350 SERIES) to work
-Allow my Aironet 350 Series Mini-PCI internal adapter to work
-Drastically decrease the overall system lag

This bug definetely needs to be fixed in the next release.

<3, Speedster239

---

### Post by J-Rod on 2008-05-31
I just have to respond with gratitude to this thread. After the upgrade, Cisco was no longer working, boot was hung, and sound was not working. I was disappointed and about to just go back to Gutsy, and I found this fix. Worked great, everything is fine now. I can say with certainty that I would not have found this wading around on my own. Many props!

---

