---
title: "Packet sniffer not working correctly"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by edfredcoder on 2007-03-03
Hello. I am trying to get a packet sniffer working at school. I have permission from the computer science teacher, and I do it under his supervision. I am trying to get a better understanding of how networks work (wow that sounds redundant), not do bad things. I am using Wireshark and Ubuntu Edgy Eft 6.10.

When I start the capture of packets, I enable promiscuous mode. I am able to collect packets, but all of them are either broadcast packets or those going to and from my computer. ??? I am collecting using wireless, and there is wireless traffic everywhere on campus. We are using WEP, if that matters. Could that be it? Do I need to put the card into monitor mode?

Mr. Merrill (my teacher) doesn't understand either why it won't work.

Do you have any ideas as to why it might not be working?

---

### Post by spd106 on 2007-03-03
If you want capture all frames being sent over the airwaves then you will need to put the card into monitor mode (rfmon). There are a few cards out their that support this mode, unfortunately ndiswrapper doesn't support this feature so you will need a card that has a native driver. I have had luck with an Atheros based card and I believe that some people have had Intel cards working. It should be too difficult to locate some hardware that will work. I have also found that the airodump-ng utility in the aircrack-ng package is quite useful for creating dump files.

Unless you have access to the networks encryption key or are near unencrypted traffic you won't be able to see much of what's going on. At least you won't be able to see what's going on above the mac layer. Scanning through frames gets boring very quickly, unless you're really into low level network engineering.

It's the higher level protocols such as http, arp, ssdp that are more interesting. That's what wireshark is more useful for.

---

### Post by kidders on 2007-03-03
Yep... unfortunately wireless networking is a bit different, because of all the encryption.

> I am trying to get a better understanding of how networks work (wow that sounds redundant), not do bad things.Your very first step will have to be "bad" things! Like spd106 says, you won't be able to see anything of interest until you've cracked the encryption keys being used by the networks you're monitoring. If traffic volumes are reasonably high, and you have some networks that are vulnerable to well-known attacks (eg Newsham's 21-bit crack), you'll get there pretty quickly.

That will give you access to the more interesting, higher-level detail of what's going on on the network.

As an alternative, you could ask a network admin to run his wireless LAN unencrypted for an hour or two. His users would still be protected by protocols such as SSL (so personal data wouldn't be exposed), but the network itself would be temporarily vulnerable.

---

### Post by edfredcoder on 2007-03-03
The wireless traffic is almost all from the school; every computer is connected wirelessly, as they have tons of computers! I asked the sysadmin at my school for the WEP key and explained why I wanted it, and she gave it to me.

I have the encryption key, and I can connect to the school's wireless fine, but I see nothing but my own traffic and broadcast packets, even in promiscuous mode.

The monitor mode sounds interesting. How do I put my card into monitor mode?

And what is ndiswrapper?

---

### Post by spd106 on 2007-03-03
If you haven't already done so, I suggest that you have a read through this web page [http://wiki.wireshark.org/CaptureSetup/WLAN](http://wiki.wireshark.org/CaptureSetup/WLAN)

---

### Post by edfredcoder on 2007-03-03
I just read through the document that you linked to. It is interesting. It seems that monitor mode is what I need. However, I have some more questions about it: does it work with WEP (assuming that I have the key, of course) and how do I put my card into monitor mode?

---

### Post by edfredcoder on 2007-03-03
I google'd around a bit and found out how to put my card into monitor mode:

iwconfig <interface> mode monitor


I can do that fine, but a few seconds after I put it into monitor mode, it auto-connects to my wifi. Does anyone know how you turn off autoconnecting to wireless networks?

---

### Post by spd106 on 2007-03-04
It depends which way you have it to auto-configure. It may be enough to temporarily comment out some line in your /etc/network/interfaces file. Then use ifconfig to bring up the interface.

---

### Post by edfredcoder on 2007-03-04
My /etc/network/interfaces file looks like this:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

eth1 is my wireless card, so I tried commenting out the two lines relating to eth1, but it did not work:

```
#auto eth1
#iface eth1 inet dhcp
```

Even with those changes, it will autoconnect. I have since changed it back.

If it matters, I am using the NetworkManager Applet 0.6.3.

---

### Post by edfredcoder on 2007-03-05
Also, does anyone know if monitor mode will be able to monitor encrypted (WEP) channels, assuming I know the WEP key?

And still, how do I turn off the autoconnecting to wifi's?

---

### Post by spd106 on 2007-03-05
Usually you will capture all traffic for a given period to a file, then import the capture file into wireshark for analysis, or you can use wireshark for the whole process See [http://wiki.wireshark.org/HowToDecrypt802.11](http://wiki.wireshark.org/HowToDecrypt802.11)

To turn off auto config with network manager you can right click the panel applet and uncheck wireless. Now you enable the interface via ifconfig e.g. sudo ifconfig wlan0 up.

---

### Post by edfredcoder on 2007-03-05
Thank you very much! Your solution has helped me greatly, and coupled with the book I'm borrowing from my teacher on TCP/IP, this is really cool.

But I have another question, if you don't mind; I can capture packets fine with wireshark, but I would like to save them as a pcap file that is unencrypted, that is with the contents of the packets minus any WEP. When I save the capture, does it do this or must I specify some special thing to tell it to save it as such, that is, unencrypted?

---

