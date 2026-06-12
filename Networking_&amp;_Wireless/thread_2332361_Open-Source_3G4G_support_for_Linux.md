---
title: "Open-Source 3G/4G support for Linux?"
date: 2016-07-30
forum: Networking &amp; Wireless
---

### Post by hanzona on 2016-07-30
Hi guys,


  I am looking for some advice for if it is possible to connect to 3G/4G networks using open-source software and firmware to prevent the risk of backdoors etc?

  I have looked at USB dongles but am not entirely sure if they can be run freely. Am I correct in assuming that 3G dongles contain a separate OS that  you connect to through a sort of USB to Ethernet adapter, kind of like a  mini router? If so has anyone free'd this option up with the likes of  open-wrt etc? If not is there a way to run dongles without the use of the internal firmware and just the use of Linux modules?


  WWAN cards seem like another option to consider. Are they essentially the same thing as a USB dongle or do they operate kind of like a wlan card that loads Linuxes firmware at boot time? If it is the latter does that mean they can be run without the use of embedded firmware etc?


Any advice would be good, thanks.

---

### Post by Bucky Ball on 2016-07-31
[LIST=1]
[*]Buy USB 4G dongle, charge it (or plug in to power), switch it on, give it a few minutes until all its lights are as it should be;
[*]Click network icon in Ubuntu and choose the dongle's network;
[*]Login with the security key (which would come with the dongle), that's it.
[/LIST]

There are no tricks or drivers to download. The modem is a totally independent entity and has nothing to do with your Ubuntu OS so you might be over-complicating. :)

The dongle will show like any other wireless network in your wireless network list. All you need to do is click it and log on. I get anywhere between about 20-35Mbps from mine. Incredible. Use it for travelling (live in Australia and we drive 750kms to visit in-laws so it's great for middle-of-nowhere map checking).

As an example, on my last trip the in-laws had just moved and had no internet (unexpectedly). Four of us were connecting to the modem, one machine a Mac. My in-laws simply clicked on the network and typed in the security key. That's all. Nothing else required. I know where you're coming from with this as I did a lot of research prior to buying mine. Take my word for it, there's nothing to fear and you'll be online with it in five minutes, ten at most. ;)

---

### Post by hanzona1 on 2016-07-31
Thank you for the reply.

So can you confirm that the dongle itself has a closed-source router like software on it separate from the OS?

It would also be really helpful if you could give me your insight on WWAN cards. Do they work in the same way as the USB dongle (i.e
 work independently with their own firmware onboard)? 

Thanks again.

---

### Post by Bucky Ball on 2016-07-31
> **hanzona1 said:**
> So can you confirm that the dongle itself has a closed-source router like software on it separate from the OS?

As I've said, the dongle has nothing to do with your Ubuntu OS. It is independent and works on its own with any OS, doesn't matter. It is a wireless modem. That is all. Just like any other wireless modem, probably the same as the one you're using now. Have no idea what software the modem uses; closed source, open-source or otherwise. It is not relevant and makes no difference to the end-user who has no access to the router apart from its configuration page, just like the config page of any other modem/router (open a web browser, type '192.168.0.1', or whatever the address of your router is, in the address bar).

[quote=hanzona1]It would also be really helpful if you could give me your insight on WWAN cards. Do they work in the same way as the USB dongle (i.e work independently with their own firmware onboard)? 
[/QUOTE]

Know nothing whatsoever about these devices, sorry. Others will and hopefully they can help if they are 3G/4G devices (as that is the support the title of your thread suggest you are asking for). ;)

As another example, if you go to a wireless hotspot and logon, does it matter to you what software the modem/routers of the wireless hotspot are using? No, you just use them. If you go to a friend's house and logon to their network, is it relevant whether their router is using open or closed source software? No. The network owner probably doesn't even know. They don't need to. 

There is no 'open-source' or 'closed-source' compatible router/modems. Just routers/modems. They broadcast an SSID, you logon, regardless of the OS you or it are using. Never the twain shall meet so doesn't matter.

---

