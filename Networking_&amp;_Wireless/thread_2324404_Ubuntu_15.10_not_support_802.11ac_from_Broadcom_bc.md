---
title: "Ubuntu 15.10 not support 802.11ac from Broadcom bcm4360"
date: 2016-05-13
forum: Networking &amp; Wireless
---

### Post by patrick120 on 2016-05-13
Was wondering if Ubuntu 15.10 does not support 802.11ac from Broadcom bcm4360. New to Ubuntu and recently switched over with a new pc trying to connect to my 802.11ac network but am unable to find it with my tp-link t8e archer. Am able to pick up all other networks aside from my 802.11ac. Any advice or answers would be welcome.

---

### Post by Bucky Ball on 2016-05-13
*Thread moved to **Networking & Wireless**.*

Welcome. So you're saying you have 15.10 installed and you can't get connected to the internet or you are yet to install and just curious?

If the latter, you want to be looking at 16.04 LTS and forget about 15.10. That has about a month and a half of support left at which time you'll need to upgrade to 16.04 LTS anyway. LTS is a long-term support and 16.04 LTS is supported for five years until 2021.

16.04 also has drivers for newer hardware and is the way to go if you are running newer hardware. Does this apply to you? Either way, many Broadcom devices work out of the box or with little effort now in Ubuntu. A few, on the other hand, don't. Have you done any research about this apart from asking here? Always a good idea. For instance, [you might have found this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") in a minute or less. ;)

[Second link here]("https://duckduckgo.com/?q=bcm4360+ubuntu").

---

### Post by patrick120 on 2016-05-13
Am able to connect to the Internet but am unable to find or connect to the 802.11ac wireless network that i currently have running. Didn't know that there was a 16.04 had the 15.10 lying around since i started my new pc. Will prob download 16.04 then see if I am able to access my 802.11ac network.

---

### Post by Bucky Ball on 2016-05-13
Well how are you connecting to the internet if not out through a router/access point? In other words, 'the network'? Bit confused. Might pay to outline the exact setup you have there. Not sure what an '802.11 ac network' is as opposed to any other. You mean you are not reaching the expected speeds for that protocol?

Whatever device is hosting this mystery network, can you ping it with:

> ping ---.---.---.---

... where '---.---.---.---' is the IP address of the device, e.g. 192.168.0.1. 

> ping 192.168.0.1

Find out your device IP and try it. Does it ping back? 

Are you running two LANs? Have you got a modem cable connected directly to your computer to connect to the internet but when you connect to your local network, you can't get on the internet??? :-k

---

### Post by patrick120 on 2016-05-13
Tp-link t8e archer (Broadcom4360) is the wireless adapter I'm using to connect to my router to get internet. My router has 3 separate networks running at the moment; 1 for Cable tv, 1 for my computer, and 1 for everything else. Of these networks there is two 2.4ghz bands and one 5ghz band which is the 802.11ac which runs up to 80mhz speed for my computer. I can connect to the INTERNET but only through the two 2.4ghz band networks but am unable to find the 802.11ac(5ghz band) network with my adapter. Ping test worked. I have already installed the driver

---

### Post by Bucky Ball on 2016-05-13
That is much clearer, thanks, not that I can give you much help with it, but that information will help others. Good luck.

---

### Post by praseodym on 2016-05-13
Change the driver via LAN:

```
sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-2_all.deb 
```
Reboot

---

### Post by patrick120 on 2016-05-15
Ok ubuntu 16.04 has issues that I'm just not going to mention. Reinstalled 15.10 set up my wifi again and still can only see the 2.4ghz networks.

---

### Post by blackgr on 2016-05-15
Hey Patrick,

Can you please provide the output of ```
iw list
```

Thanks,
Alex

---

