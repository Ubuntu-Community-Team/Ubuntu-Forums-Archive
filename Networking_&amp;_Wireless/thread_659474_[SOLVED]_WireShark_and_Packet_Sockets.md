---
title: "[SOLVED] WireShark and Packet Sockets"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by anderskitson on 2008-01-05
[SIZE="4"]I have Wire shark running and capturing, I am filtering for TCP and can see my traffic for non secure htp logins, but no one else on my network.

According to Wire Shark You need to have Packet Socket enabled in Linux [http://wiki.wireshark.org/CaptureSetup/CaptureSupport ]("http://wiki.wireshark.org/CaptureSetup/CaptureSupport")
 and I am not sure how to tell if Ubuntu has this or not, and if not how to go about enabling it. [/SIZE]

---

### Post by kidders on 2008-01-07
Hi there,

Packet socket support is pretty fundamental, so it'd be very unusual not to have it. In any case, here's how to check...```
$ grep 'CONFIG_PACKET\W' /boot/config-`uname -r`
CONFIG_PACKET=y
```This command looks up the kernel version you're currently using, checks /boot for matching configuration information, and filters it for the appropriate parameter. Provided CONFIG_PACKET is set to 'y' or 'm', you're fine. If it's set to 'm' (module), you may want to check that it's been loaded...```
$ lsmod | grep af_packet
af_packet              21768  2
```

Anyhow, this is very unlikely to be connected to your problem. Do you know for sure that you *should* be seeing traffic traveling between other computers on your network? How is your network organised (ie in hardware terms)?

---

### Post by anderskitson on 2008-01-12
[SIZE="3"]Hi thanks for the response, Um for my home network all the computers are running through a hub, that runs through a router to the internet. I can see files on all the other computers that are shared.So i am not sure how i need to set up the network? to make sure it will work. I have been told you can see the other computers traffic wirelessly, now is it easier to see others packets when you are connected wirelessly on the same network. I just figured if you could do this wirelessly through the router why not wired. I just found this interesting for surfing in coffee shops and hot spots, and you log into htp sites that on the same network your name and password can be revealed. I'm not out to do any mischief, just more interested for my own security[/SIZE]  

And yes packets sockets are definitely there and loaded

---

### Post by kidders on 2008-01-12
You can only see data that actually passed by your network interface ... I suppose that's pretty obvious hehe. Naturally, over a wireless link, *everything* does, because the transmission medium is the atmosphere. Over wired network connections, on the other hand, being connected to switches or similar hardware can limit the volume of data that's exposed to the physical network cabling between you and its endpoint.

In electrical terms, if a change in voltage across a particular piece of cable won't result in a corresponding change on the cable connected to *your* NIC, then you can't eavesdrop on it. The more "intelligent" switching & routing devices are normally specifically designed not to send you traffic that has nothing to do with you. If they didn't, negotiating for transmission space on a network would quickly become impossibly complicated.

Anyhow, that's why I was interested in your hardware. Assuming your cabling goes [FONT=Courier New]You <-> Hub <-> Switch <-> Router[/FONT], it's highly likely that you'll get to see very little coming from anything not physically connected to the hub. To see the data passing through the hub, be sure your NIC is operating in promiscuous mode, so your hardware doesn't throw away data that isn't addressed to it.

---

### Post by steeleyuk on 2008-01-12
What model hub have you got? If you have got a hub and your network card is running in promiscuous mode, you should see any traffic being broadcast by the hub.

If your 'hub' is really a switch, theres no chance you can see any other traffic unless you poison the ARP cache of the other machines connected to the switch.

---

### Post by anderskitson on 2008-01-12
Well I guess my problem is my definition is wrong, I always thought a hub and a switch were that same, but i take it a hub shares bandwidth while a switch just passes it along. So i have a switch that is my problem. But I am going to try it wirelessly

thanks for the help

---

### Post by 4nsitian on 2008-04-06
i know how to use wire shark. now i need to capture the packets from a remote interface.
i have an idea that i can use any open port of that remote host.
but how the whole listening/capturing could be done?

---

