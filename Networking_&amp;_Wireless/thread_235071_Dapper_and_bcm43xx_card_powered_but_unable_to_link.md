---
title: "Dapper and bcm43xx card powered but unable to link to router"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by frozenpenguin on 2006-08-12
Hi this is the 3rd time I have tried to get my Broadcom wireless card working in Dapper on my Dell Inspiron 1300. I seem to have gotten a bit further this time but need some assistance.

I am running the standard kernel 2.6.15-25.46, and have followed the following to the letter:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

I have set up the scripts and run them and for the first time have been able to get the wireless light to light up on the machine but am unable to scan for my router ESSID.

lsmod |grep bcm43xx returns:

bcm43xx               124044  0
ieee80211softmac       29696  1 bcm43xx
ieee80211              37064  2 bcm43xx,ieee80211softmac
iain@frozenpenguin:/lib/firmware$

iwconfig returns:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"gi11ian1"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I have run "sudo iwconfig eth1 ap any" but this does not change the ap being invalid.  I have tried both WEP 64 and 128 and no encryption to no avail.

This is the last sticking point to me again saying bye bye to Win XP, having run linux in various guises with dial up since 2000.

Please help.

Iain

---

### Post by Darkhack on 2006-08-15
It is invalid because you havn't specified an ESSID nor connected to one.  Assuming you are using WEP encryption, type the following...

"sudo iwconfig eth1 key restricted ABCDEF123456789"  <-- enter your WEP key

"sudo iwconfig eth1 essid NAME" <-- replace name with your essid.

"sudo ifup eth1"  <-- enjoy!

---

