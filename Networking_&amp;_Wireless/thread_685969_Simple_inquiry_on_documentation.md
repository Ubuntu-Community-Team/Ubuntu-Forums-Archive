---
title: "Simple inquiry on documentation"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by Richiee18 on 2008-02-02
Hi, 

I'm trying to set up a USB ADSL modem with the Speedtouch driver under Ubuntu. I've been following this guide so far: [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch?highlight=%28CategoryNetworking%29]("https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch?highlight=%28CategoryNetworking%29")

But I've now come across something I'm not to sure about, the guide tells me to paste the following configuration file into a text editor but replace 'username' with your own that is provided by the ISP and to also change 0.00 with the _VP/VC values_. 

[HTML]noipdefault
defaultroute
user 'username'
noauth
updetach
usepeerdns
plugin pppoatm.so
0.00

### You may need to uncomment these
### options to connect with some ISP's.
### They disable compression.

# noaccomp
# nobsdcomp
# nodeflate
# nopcomp
# noccp
# novj

### If the firmware loads and pppd won't
### connect uncomment this option to make
### pppd be more verbose in the system log

# debug

### For more details (and more options)
### Read man pppd[/HTML]

So the question is what are VP/VC values?

---

### Post by Whiffle on 2008-02-02
Virtual Path/Virtual Channel, according to a google search its different for every dsl provider.

---

### Post by Richiee18 on 2008-02-02
Is there anyway I can check it on the computer or do I have to ask the dsl provider.

---

