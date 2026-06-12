---
title: "onboard eth not supported"
date: 2005-10-01
forum: Networking &amp; Wireless
---

### Post by Andy16 on 2005-10-01
Hi out there,

installing Ubuntu on a new PC I run into problems regarding the onboard eth which during installation "cannot configure DHCP" - well the link does not come up....

HW: 
Gigabyte GA-7N400-L Motherboard having a Realtek 8100C onboard

(Ubuntu discovers a GA-7VM400M and a RTL-8139/8139C/8139C+)

BUT I cannot bring up the link and get a connection to my router....

Can someone post a set of commands I should run to debug this issue?
Realtek shouldn't be so extraordinary, right?

Any help is welcome
regards
Andy

---

### Post by Andy16 on 2005-10-01
well here are the first results:

lspci  | grep -i ethernet
0000:01:0b.0 Ethernet controler: Realtek Semiconductor Co., Ltd RTL-8139/8139C/8139C+ (rev 10)

ifconfig eth0
eth0   Protokoll Ethernet Hardware Adresse 00:0D.61:1B.20:08
BROADCAST MULTICAST MTU:1500 Metric:1
RX ...
TX...
Kollisionen ...
Interrupt:16 Basisadresse: 0xc000

sudo ifup eth0
....
sit0: unknown hardware adress type 776
sit0: unknown hardware adress type 776
Listening on LPF/eth/00:0d:61:1b:20:08
Sending on LPF/eth//00:0d:61:1b:20:08
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 intervall 5
... intervall 14
... intervall 17
... intervall 14
... intervall 11
No DHCPOFFERS received.
No working leases inpersistent database - sleeping


from /etc/network/interfaces
iface eth inet dhcp
auto eth0


Link never comes up / no control LED on router (obviously no DHCP ip ;-> )

what else may I send - what can I do ???

HELP

Andy

---

### Post by oeoe on 2005-10-02
I have exactly the same problem. The chip is found and correctly recognized. It doesn't help to plug out the 8139cp module and just go with the 8139too, as [someone suggested]("http://ubuntuforums.org/showthread.php?t=70213&highlight=8139") . I'm really lost in this issue, this chip shouldn't be a problem.
Any suggestions?

---

### Post by Andy16 on 2005-10-02
Hi oeoe - hurray! At least I'm not alone.... ;-)

Did you try knoppix/debian (native)/kubuntu?
For me, all the installers couldn't bring up the eth0.
I even tried Solaris10(intel) - and the network wasn't discovered.

As you agree, this isn't a magic network card and should work....
What else in installed in your PC? What's the Motherboard?

I don't want to add another network card (as I already have on and a second card will drive my WinXP crazy - for sure :rolleyes: )

Where are the debian gurus out there? You have two volunteers :razz: 

Andy

---

### Post by oeoe on 2005-10-02
My motherboard is a Shuttle FT62 (I have a Shuttle Zen). I tried with Knoppix too, but without luck. Since this computer only have one PCI slot, I don't feel like using it for networking...

---

### Post by Andy16 on 2005-10-09
strange enough - this is how I got it to work:

install another eth on pci - which was discovered perfect!
connect to internet
apt-get dist-upgrade
reboot 
hey! I do have two eth!
configure onboard eth
shutdown
remove the additional pci card
boot

that's it!

hope it works also for you!
regards

---

### Post by oeoe on 2005-10-09
hey andy, I must try this when I get back to my house! I'll post here again when I've tried this!

---

### Post by oeoe on 2005-10-10
didn't work :-(

or didn't your internal networking card start working until you had removed the additional pci card?

I'm suspecting that this is a hardware error.


ciao /oeoe

---

