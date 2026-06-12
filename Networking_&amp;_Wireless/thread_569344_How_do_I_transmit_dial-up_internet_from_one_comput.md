---
title: "How do I transmit dial-up internet from one computer to another?"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by s3a on 2007-10-06
I have the Airlink 101 AWLH3026T as well as the D-Link AWL-G122. The computer with functional dial-up is the one with the Airlink AWLH3026T PCI card. What I want to do is share my dial-up internet from that comp to my laptop's DWL-G122 USB adapter. Before you go about saying that, it will be too slow, etc...I don't care since, both computers will not be using the internet at the same time...I just want to be able to go from one computer to another without problem and since I have a second phone line, I no longer need to ever disconnect, so...someone please help me achieve this without a router or any extra material that is not software. I am very desperate!

Thanks in advance!

---

### Post by helgman on 2007-10-07
If I understand you correctly you have one computer (A) connected to the Internet via a dial-up and you want that one to share it's Internet connection with another computer (B) via a wireless link.

What you need to do is the following:

1) Create an Ad Hoc network that connects computer A and B.

2) Enable IP Forwarding (and NAT) on computer A.

3) Make sure that computer B has A as it's default gateway and that it also has a DNS server configured (presumably the same as computer A).

Then you should be good to go.

As for step one [this document](https://help.ubuntu.com/community/WifiDocs/Adhoc) has some information.

As for step two, I've never gotten a dial-up to work on any of my computers, but I guess it works like any other network interface so there should be plenty of guides out there for how to do it. 

[[SOLVED] Sharing dialup connection over network cable](http://ubuntuforums.org/showthread.php?t=57937)
[internet sharing from Ubuntu to Mac](http://ubuntuforums.org/showthread.php?t=563501)

In the second link above someone asked "firestarter?" I've installed it but I've yet not had the chance to test it so I can't really say but it might be worth a shot. The iptables and ip_forward is something I've used successfully so that's why I suggest it.

Please ask if you have any questions.

Regards,
Helgman

---

### Post by s3a on 2007-10-08
The official website of Firestarter only seems to have a 5.04 Hoary Hedgehog version of its software and I am using 7.04 (Feisty Fawn). Is there any place that has a 7.04 version? Am I not looking into their site the right way?

---

### Post by helgman on 2007-10-08
```
$ sudo apt-cache search firestarter
firestarter - gtk program for managing and observing your firewall
[...]
$ firestarter -v
Firestarter 1.0.3
```

Don't know what version is the latest on the website.

Regards,
Helgman

---

### Post by s3a on 2007-10-08
> **helgman said:**
> ```
$ sudo apt-cache search firestarter
firestarter - gtk program for managing and observing your firewall
[...]
$ firestarter -v
Firestarter 1.0.3
```

Don't know what version is the latest on the website.

Regards,
Helgman
I have Firestarter installed but now it says that the device (ra1) "is not ready." I think that that is my wireless card. Please help and thanks for bringing me this far!

---

### Post by helgman on 2007-10-08
You've had the wireless working before? And you've used it?

Regards,
Helgman

---

### Post by s3a on 2007-10-12
No, I haven't ever gotten either one of the wireless devices working, however, I can say that they both have the ability to scan and see wireless internet signals. Would I need things like NDISWRAPPER? I've heard I would need such a thing for my D-Link DWL-G122 USB device and that the Airlink "equivalent" should work out of the box.

---

### Post by helgman on 2007-10-14
My suggestion is that you look for threads about your wireless cards in the forum and if you can't find any that works start a new thread where you ask for help with a specific card. I've got no experience messing with the wireless part since my card "works out of the box" these days.

Sorry I can't help with the wireless problems.

Regards,
Helgman

---

