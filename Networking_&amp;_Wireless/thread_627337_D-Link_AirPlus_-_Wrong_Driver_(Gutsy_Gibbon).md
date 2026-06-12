---
title: "D-Link AirPlus - Wrong Driver (Gutsy Gibbon)"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by esoikie on 2007-11-30
I recently installed Xubuntu 7.10 (gutsy gibbon) on my laptop.

I am using a D-Link Airplus DWL-650+ wireless network card.

lshw -C network reports:

       description: Wireless interface
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:80:c8:ab:5a:f1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx promiscuous=yes wireless=IEEE 802.11b+

you will notice that it reports as a generic Wireless Interface created by Texas Instruments.  It is not using the required Prism Driver.  It also registers as wlan0, and not eth1 or ath1 which I have heard mention of in other threads.  The question is: A) what driver do I need to be using? b) is there anything I need to know to have it replace the existing driver?

---

### Post by esoikie on 2007-11-30
For anybody who comes here looking for help, I figured I'd make a few notes as I work my way through the process.

Apparently the DWL-650+ is not a Prism card, (search for 650+ and you too often get the 650 in google)

The DWL-650+ has the Texas Instruments AR5210 chipset.  This is supposedly supported by MadWifi.  I did download and install MadWifi long before I posted here, but perhaps I made an error.  I will try again, and let you know what happens.

---

### Post by rustybronco on 2007-11-30
> "product: ACX 100 22Mbps Wireless Interface
vendor: Texas Instruments"
t.i acx-100 chipset, my acx111 is supported, don't see why it doesn't work for you.
> configuration: broadcast=yes driver=acx_pci latency=64 module=acx promiscuous=yes wireless=IEEE 802.11b+
looks like it's installed and recognized properly, what encription are you using?

---

### Post by esoikie on 2007-11-30
I suppose now I need to explain why I'm going through this.  Yes, I can connect to 128 bit encrypted network.  So why bother with all this?

A friend of mine and I were discussing the wireless network for his buiness, and how secure it is.  I decided the best way was to test it and find out.  Never having done anything like that before, I knew linux was where I needed to be in order to really test his security (and learn about security testing).  So I installed Xubuntu.  From, there, I found this related howto:

[http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/](http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/)

After installing everything it recommended, I get to the first step in the process.  airmon.  Which when started reports the following:

usage: /usr/sbin/airmon <start|stop> <interface> [channel]

-e Interface    Chipset         Driver

wlan0           Unknown         Unknown

Which got me to start looking at the driver and wondering why airmon wouldn't recognize the chipset or driver.  The next step is Kismet and all I could find was mention of Atheros (I think that's it) or hostap, so I figured I need to get one of those drivers working for my card.  After a day or so, I kind of got lost and confused and figured I'd post a message and see if the response gave me a fresh approach for the next day.

---

### Post by esoikie on 2007-12-01
Alright, seems the existing driver WAS in fact working okay.  It's simply that the HOWTO didn't mention turning the card into 'monitor mode' which solved the errors I was getting.  Though, I am still kind of curious why Kismet didn't recognize the chipset or driver.

---

