---
title: "Figuring out how to communicate with a network-connected device"
date: 2014-07-11
forum: Networking &amp; Wireless
---

### Post by JazzPotato on 2014-07-11
Hi there,
At my workplace we have a Realand A-C071 fingerprint reader that employees use to clock in and out of work. Currently, we retrieve logs from it by downloading them to a USB stick, but I'd like to track employee clock-in and outs in a more sophisticated way. 

The device is ethernet connected, and nmap tells me it has port 5005 open. The problem is, I have no idea how to talk to the thing. 

Realand do provide windows software that is supposed to be able to download logs from their devices but I would like to store and manage logs on my own SQL server, so I need to figure out how to talk to the device.

Now, has anybody had any experience with talking to things that at first don't understand you? How can I can I start to establish some level of communication here? I think this will be a good way for me to learn more about nmap and networking in general. I have contacted Realand and asked for an SDK that they mention on their website but I can't find anywhere, so in the mean time I'd like to be a bit more proactive.

Thanks in advance,
Gary

---

### Post by tgalati4 on 2014-07-11
I would set up a Windows machine with the correct software to talk to the device.  Set up a Linux machine with *wireshark* and sniff the packets that are traveling between the device and the Windows machine.  The initial handshake may happen on port 5005 (port knocking) but the reply could be on any port, and it may change based on time-of-day.  

Once you have some packets captured, you can try to figure out the commands used to talk to the device and dump the data.  It may be a simple ASCII string of commands or it could be a sophisticated authentication (it is a fingerprint reader after all) procedure to dump the data.  An alternative is to hook up an external USB hard drive [enclosure]("http://www.amazon.com/NetDisk-ENCL-1P-3-5-Inch-Ethernet-Enclosure/dp/B0032HETIC") with an ethernet port.  Dump the data to the hard drive with USB and use the ethernet connection to then capture the data from the hard drive through the Linux machine.

The other method, which I will not discuss in this forum is to use penetration techniques against the device similar to hacking a router.

---

