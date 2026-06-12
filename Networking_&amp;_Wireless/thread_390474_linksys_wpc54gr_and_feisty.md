---
title: "linksys wpc54gr and feisty"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by woodamand on 2007-03-22
I am rather new to ubuntu but I have checked the forums, perhaps I have missed something but here is the situation:
I am running the lastest kernel and trying to use my wpc54gr on an HP laptop. When I plug the card in after its booted, I get some encouraging messages from /var/log like:

[I]Mar 21 21:50:02 bb3 kernel: [  164.261497] pccard: CardBus card inserted into slot 1
Mar 21 21:50:02 bb3 kernel: [  164.465093] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
Mar 21 21:50:02 bb3 kernel: [  164.465116] rt61 1.1.0 CVS CVS [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
Mar 21 21:50:02 bb3 kernel: [  164.466097] RT61: Vendor = 0x1814, Product = 0x0401 
Mar 21 21:50:02 bb3 kernel: [  164.655836] RT61: RfIcType= 4[/I]


so it looks like the rt2x driver is already installed, the lights go on on the card and they blink and when I do an ifconfig I get something like this:

[I]ra0       Link encap:Ethernet  HWaddr 00:16:B6:9B:7F:FE  
          inet6 addr: fe80::216:b6ff:fe9b:7ffe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9958 errors:0 dropped:0 overruns:0 frame:0
          TX packets:319 errors:1 dropped:1 overruns:0 carrier:0
          collisions:9 txqueuelen:1000 
          RX bytes:852192 (832.2 KiB)  TX bytes:3308 (3.2 KiB)
          Interrupt:11 [/I]

this in addition to the info on eth0 which works fine. The problem is that I cannot connect to my wireless network, when I try it fails and falls back on the wired card.
My question: do I need to look at the ndiswrapper? Or am I missing something else here?
I am happy to do some more reading if someone could point me in the right direction!

TIA

---

### Post by chili555 on 2007-03-22
If I read this correctly:```
it fails and falls back on the wired card
```I take this to mean you are trying to activate wireless with wired connected. Yes? No?

You will probably never get your computer to get two IP addresses on two interfaces without some serious fiddling deep within the warp core. And why would you want to?

I think your computer is saying, "I already have a way to the network, I don't want or need another. No thanks, wireless."

Are you able to configure and connect without the wired connected and after a sudo ifdown eth0?

---

### Post by woodamand on 2007-03-22
No I am not trying to have both interfaces up at once. It was my understanding that the app that controls the connection could switch interfaces between the wired and the wireless connections - this is certainly what it appears to be doing:
1) I look at the available connections, I am hooked up as wired
2) I choose my wireless network
3) the app disconnects my wired connection and
4) tries to connect via wireless and fails.
So my assumption was that once the wired connection was disabled, the IP address would be freed up so that the wireless card could now have an IP address bound to it - isn't this how it is supposed to work??
Certainly I can try your suggestion about setting eth0 to down, and if that works, OK, it just seems a mite clumsy, although if that is what I have to do so be it. I would assume that there is a way to disable the wired connection at boot, at least I hope that is possible for a NIC that is on the motherboard.
Thanks much for taking the time to respond, its most appreciated!

---

### Post by chili555 on 2007-03-22
Do I conclude it is NetworkManager you are working with? The little blue whirlygig?

Please see [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) especially: > The computer should use the wired network connection when its plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connectionIs it doing exactly what it's designed to do?

---

