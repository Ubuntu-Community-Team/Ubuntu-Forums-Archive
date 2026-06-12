---
title: "Debian Sarge w/BlackBox - Linksys BEFCMU10 v3 USB Modem"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by shawnrgr on 2006-07-25
Ok, i have been taking some free time aside for 3 months now trying to get this working. Hopefully someone in here can help me out.

The scenario:

Pentium 233
No Ethernet Card, Just USB
Debian Sarge running BlackBox
Linksys BEFCMU10 v3 USB Modem
Comcast Cable

My main computer is a compaq laptop. I use the ethernet port on the modem for internet access. There is also a USB port on the back of the modem. I want to be able to use that USB port to get my old p233 online. I am currently out of a job an literally have no money so purchasing a 20 dollar ethernet card is out of the question (i know its sad).

When I plug the modem into the old pc via usb the usb light on the modem turns red\orange and blinks. When I boot up the system (everything scrolls by too fast to accurately see what it says) I see at one point when its scanning the usb devices "Linksys USB Ethernet....." or something like that. So I know the system can see the device.

After I get into a desktop, i start tinkering around with the pppconfig stuff. It tells me that it sees "1 connection, eth0..." so I run the test. At this point the USB light on the modem turns GREEN!! I think YAY! However my excitement is short lived when it tells me that there was no response from the device and the config program times out.

I found this post here: [Linksys USB Modem...]("http://www.linuxquestions.org/hcl/showproduct.php?product=1703&cat=myprod")

Which clearly stats that it IS possible to get this modem working. But I'm still learning linux and I don't know anything about... CDCEther, af_packet modules, ifcfg-usb-eth, or any of that.

Can someone please help me out here. And help is good help.

---

### Post by mips on 2006-07-25
Sorry I cannot help but hopefully there is someone else here that knows a bit more.

---

### Post by shawnrgr on 2006-07-26
*bump*
someone? anyone?

---

### Post by shawnrgr on 2006-08-07
well you guys were so helpful thanks. 

i eventually figured it out. if anyone is trying to get there usb modem working. try these steps:

1. make sure CDCEther is loaded at start. modprobe CDCEther 
2. shut down pc
3. shut down modem
4. make sure only usb is plugede into the modem.
5. turn modem on and let completely boot up
6. turn pc on
7. if nothing at boot up thats fine. log in
8. at prompt: dhclient eth0

worked for me with my linksys usb modem on an older p1 ;) hopefully this can help a few people out.

---

### Post by haganerei on 2007-10-13
Ubuntu 7.04 alternate command-line install
cdc_ether already running
BEFCMU10 v4 US connected via USB
dhclient eth1

done

note: dhclient eth0 found my integrated NIC

---

