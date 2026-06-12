---
title: "cant get wireless card to work"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by bertasius.palmer on 2007-02-07
Hi,

Really hoping someone will read this and be able to help. We have been struggling for 2 weeks to figure out how to use our wireless network with ubuntu. 
Toshiba Satellite pro 4600 with a 3com OfficeConnect 3CRWE154g72 v2.0
we have installed the windows drivers, and the card is showing as below:
eth1      NOT READY!  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tony@ubuntu:~$ 
I having been reading so many different posts that I am unsure what my next step should be. could someone please advise?
Many thanks!!!

---

### Post by gradedcheese on 2007-02-07
can you scan?

```

sudo iwlist eth1 scanning

```

if so, pick the SSID for the network you'd like to join and:

```

sudo iwconfig eth1 essid put_the_ssid_here

```

---

### Post by bertasius.palmer on 2007-02-07
tony@ubuntu:~$ sudo iwlist eth1 scanning
Password:
eth1      No scan results
tony@ubuntu:~$ 

also - what does the phrase NOT READY! refer to?

---

### Post by chili555 on 2007-02-07
NOT READY means, roughly, there are a few more parameters I need before I can connect. I might be able to get them from the access point or from you, the linuxian, but...I'm not ready, yet.

No scan results means there is no access point in range for your card to connect to. Did you power up the router? Is the router defective? Did the neighbor catch you trying to get free access? Is there an antenna on your wireless card or router that has come loose? Whatever the reason, there are no signals to detect.

---

### Post by bertasius.palmer on 2007-02-07
we have an office connect adsl router sitting less than 1 foot away - it is ours and we know the ESSID and password:lolflag: we have 3 laptops 2 x ubuntu, 1 x windows xp. the win xp connects no probs. encryption is 128 wep and is DHCP. - also, am quite confused as some wepages refer to our 3com pcmcia card requiring something called prism 54 or prism frisbee, but have not a clue how to find out if we have it already, wether we need it, and if we did how we might install it??
please keep the suggestions coming

---

### Post by edubarr on 2007-02-07
I've also run into problems when trying to connect with routers using 128-bit WEP. I can connect using 64-bit WEP and also WPA, but the 128-bit WEP always fail.

It's an intel 2915ABG chip.

---

### Post by bertasius.palmer on 2007-02-07
tried changing from 128 to 64 - no joy :(

---

### Post by edubarr on 2007-02-08
Are you using the network-manager applet? You could give it a try, it's more geared toward WPA, but it's what I'm using and allows me to connect to 64-bit WEP also.

Here's a link to the howto: [WifiDocs/WPA]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo")

---

### Post by dannyboy79 on 2007-02-08
FYI, edgy and wg511t was not good out of the box supposedly per this link. [http://madwifi.org/ticket/1016](http://madwifi.org/ticket/1016)
madwifi fixed this issue around 2/6/07 for the wg511t, Gnome NetworkManager (using wpa_supplicant, using madwifi-ng, using ath_pci).

so maybe this is the issue for your wifi card as well?

---

