---
title: "Ralink RT2561/RT61 to work in master mode"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by Archfiend on 2006-12-08
I have a wireless card:
Gigabyte AircruiserG GN-WP01GS
with the chipset correctly detected after I upgraded to the 6.10 version of xubuntu.

RaLink RT2561/RT61 802.11g PCI

I'm trying to follow the steps of this article ([http://www.linux.com/print.pl?sid=06/07/10/1729226)](http://www.linux.com/print.pl?sid=06/07/10/1729226)), in order to configure a wireless Access Point in my xubuntu distro.

The thing is, in my network settings windows theres a wlan0 and a wmaster0. Can anyone explaine the diference between this two?

Also, after I runned this command:
iwconfig wlan0 mode master
and then this:
iwconfig wlan0

it appears the mode changed to master.

but when I run ifdown wlan0 - interface wlan0 not configured
and when I run ifup wlan0 - ignoring unknown interface wlan0=wlan0.

I whould like to first be able to see all wireless access points in this area, so that I'm certain that my wireless is fuinctionning correctly, so that I can then try to build the Access Point.

As you can see, I'm a newby in linux, so any help will be very apreciated.

Thanks

---

### Post by Archfiend on 2006-12-08
Ok, so now I know I have my bridge correctly configured by running this command:
**sudo brctl show**

I've followed the rest of the steps from the site ([http://www.linux.com/print.pl?sid=06/07/10/1729226](http://www.linux.com/print.pl?sid=06/07/10/1729226)) till I reached the command:
**sudo /etc/init.d/hostapd start**
wich gave me this:

[B]Starting advance IEEE 802.11 management: 
hostapdioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
rmdir[ctrl_interface]: no such file or directory[/B]

....

My /etc/hostapd/hostapd.conf file is as follows:

[B]interface=wlan0
bridge=br0
driver=hostap
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
debug=4
dump_file=/tmp/hostapd.dump
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
ssid=Sirius
#macaddr_acl=1
#accept_mac_file=/etc/hostapd/accept
auth_algs=3
eapol_key_index_workaround=0
eap_server=0
wpa=3
wpa_psk_file=/etc/hostapd/wpa_psk
wpa_key_mgmt=WPA-PSK
wpa_pairwise=CCMP
stakey=0[/B]

Any help???? I'm stuk

---

### Post by Archfiend on 2006-12-08
any help please???????????

---

### Post by FrodoB on 2006-12-08
Your problem is this:

[B] driver=hostap

This is for the prism2 based devices. I do not know what this should be for your device or if it can be made to work.  

I seem to recall that wext works for several devices.
[/B]

---

### Post by FrodoB on 2006-12-08
Do a google search on:

rt61 hostap

It does not look promising to me.  Let us know if you succeed,  I have one of these cards myself and if it can do it, it would be nice to know.

---

### Post by FrodoB on 2006-12-08
For a modern access point an Atheros based card is the best bet:

Here are some example Atheros devices:

DWL-G510: (Atheros)
[http://www.tigerdirect.com/applicati...3131&CatId=368]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=783131&CatId=368")

DWL-G520: (Atheros)
[http://www.amazon.com/D-Link-DWL-G52...810405-1660869]("http://www.amazon.com/D-Link-DWL-G520-Wireless-Adapter-802-11g/dp/B00007LTBI/sr=11-1/qid=1165277181/ref=sr_11_1/002-9810405-1660869")



Netgear WG311T: (Atheros)
[http://www.netgear.com/Products/Adap...rs/WG311T.aspx]("http://www.netgear.com/Products/Adapters/SuperGWirelessAdapters/WG311T.aspx")
[http://www.amazon.com/Netgear-WG311T...&s=electronics]("http://www.amazon.com/Netgear-WG311T-Mbps-Wireless-Adapter/dp/B0001N6LCM/sr=8-1/qid=1165274426/ref=pd_bbs_sr_1/002-9810405-1660869?ie=UTF8&s=electronics")
[http://www.newegg.com/Product/Produc...82E16833122134]("http://www.newegg.com/Product/Product.asp?Item=N82E16833122134")


D-Link DWL-G650: (Atheros)
[http://www.amazon.com/D-Link-DWL-G65.../dp/B00007LTB6]("http://www.amazon.com/D-Link-DWL-G650-Wireless-Cardbus-Adapter/dp/B00007LTB6")
[http://www.tigerdirect.com/applicati...5115&CatId=367]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485115&CatId=367")

If you see the Atheros advertising or the 108Mbps then you are probably in the right track unless you are buying on line and they are selling multiple chipset versions of the same card model, which happens from time to time.

Warning! Atheros USB devices do not just work in Linux. For USB devices there are not a lot of works out of the box cards that I can recommend, but there are several good ones if you are willing to compile drivers. Here are devices that I have tested myself with good results:

---

### Post by ebs16 on 2007-10-20
I'm running into a related problem with the same type of card. Master mode does not yet work on a RT61 card.  There a group developing a driver that should take care of this, but it's currently in beta: [http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page).

I am trying to get the card running in master mode to use my computer as a wireless router but am running into errors while compiling.  Has anyone managed to successfully compile and use the serialmonkey RT2X00 drivers in ubuntu?

I'm running a bare install of gutsy server.

Thanks!

---

### Post by Person_1873 on 2008-01-13
you'll need to install module assistant, run it and choose prepare using sudo the whole time, this downloads all the compilers you'll ever need

---

### Post by Person_1873 on 2008-01-13
could someone tell me what "hostap" app i need for an atheros chipset? i'm getting a DWL-G520 PCI card to make a network server behind my router and it'd be nice to know

---

### Post by orbnauticus on 2008-02-22
For Atheros chipsets, set the line to "driver=madwifi"

---

### Post by unxplained on 2008-04-24
Has anybody figured anything out about this yet? I also have the ralink RT61 chipset and would like to run it in master mode...

---

### Post by cengique on 2008-07-01
The new generation rt2x00 project driver supports master mode on several Ralink chipsets. For rt61, see: 
[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=4770&st=0&sk=t&sd=a&hilit=rt61+master](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=4770&st=0&sk=t&sd=a&hilit=rt61+master)
[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=4859&sid=a22660f2e74f30fd80456bdaf7c34faf](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=4859&sid=a22660f2e74f30fd80456bdaf7c34faf)

However, they require a lot of custom compiling of kernels and other supporting programs. See rt2x00 forums for more up-to-date info.

-Cengiz

---

