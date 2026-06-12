---
title: "Wireless connection not possible - no IP-adress?"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by Sofie on 2007-10-05
I am trying to use my wireless internet. The name of my own wireless internet does not appear on the list of wireless networks?

But even when I try to connect to other (non-secure-) networks, my notebook does not log on.

 The information on my connection is:
"Interface: wireless Ethernet (ath0)
Speed: Unknown
Driver: ath_pci

Ip-adress ... all to secondary DNS: are all 0.0.0.0

and hardware adress is the only one with a number"

What can I do?

Thanks

---

### Post by El Rogueo on 2007-10-05
> **Sofie said:**
> I am trying to use my wireless internet. The name of my own wireless internet does not appear on the list of wireless networks?

But even when I try to connect to other (non-secure-) networks, my notebook does not log on.


I assume you can /see/ the networks you want to connect to. Is your connection DHCP? That makes things easy usually.

And have you tried manually connecting by typing in the connection information in the network manager? That would rule out incompatibility for the most part if it worked.

What kind of wireless card is this? Do you have the drivers from the restricted packages, and if you don't can you get them? Your config says it's an atheros chipset, which is pretty common, but if that's not what you have that could also be the problem.

provide more info plz- what exactly happens during the "not-logging-on" stage? Error messages?

Thanks

---

### Post by Sofie on 2007-10-06
Thanks!

My net card is:
WN2302A-F4 13ch. mPCI WLAN IEEE802.11 b/g (Atheros)

I see all the networks when I am not wirered, and when I choose my own its trying for a long time to connect, but then it just doesnt connect. For a long time it says "attempting to join..." and then it ends saying "no network connection".

It asks for my WPA personal key, I enter it, but no. I tried changing it to TKIP instead of default, but still no.

I also tried manual, but no.

It wont even connect to the non-secure networks on the list.

If I find the driver for my atheros, how do I install it proberly?

Thanks!

---

### Post by El Rogueo on 2007-10-06
> **Sofie said:**
> Thanks!

If I find the driver for my atheros, how do I install it proberly?

Thanks!

Well, what I meant was that your config says you're using the atheros chipset and have the drivers for it. Whether or not your card actually *uses* the atheros chipset I dunno, and that's where you'd want to check.

Sometimes a bad install can do it. If you don't mind the data loss you can always reinstall the OS and then choose to use DHCP IP resolution when it initially tries to test the card during the installation. That's a pretty good baseline for internet connectivity.

It's also a good way to ensure your settings are all clean and reset so you know the problem's not from human error etc

---

### Post by El Rogueo on 2007-10-06
I'm sorry! I overlooked the simplest explanation for your first problem!

You have a b/g card. If you try to connect to your network, which you can confirm is wireless accessable either through another computer or other operating system, and you still can't see it in your current linux installation, one possible explanation is that it's an "a" or even the new "n" network type.

the letter stands for frequency

[http://compnetworking.about.com/cs/wireless80211/a/aa80211standard.htm](http://compnetworking.about.com/cs/wireless80211/a/aa80211standard.htm)

If your router is broadcasting on the "a" frequency and you have a b/g card that could be why. It's doubtful, but it's also an easy fix if that's the problem: get a new network card or change routers

hope that helps narrow things down

---

### Post by Sofie on 2007-10-06
I only a very beginner (sorry - I also spilled my beens?)

How do I check what my config says?

Reinstalling OS - does that mean reinstall ubuntu? And how do I choose DHCP IP resolution?

I have found other diskussions that says my network should work... So I hope its not the card. I worked with windows...

Thanks!!!

---

### Post by El Rogueo on 2007-10-06
> **Sofie said:**
> 
 The information on my connection is:
"Interface: wireless Ethernet (ath0)
Speed: Unknown
Driver: ath_pci


That looks like a config print out to me- how did you get it?

I'm fairly new too, but I think you're maybe looking for

```
iwconfig
```

OS stands for Operating System, sorry. So yes, reinstall your distribution

If it worked with windows I would suspect a driver problem or a configuration problem.

As for DHCP (Dynamic Host Configuration Protocol) you can find it if you go into your network settings (through the System tab on your desktop I think, maybe Administrator, I dunno, I'm running Xubuntu right now :confused:) and that'll bring up your connections. Click on your wireless connection and then click the properties button. It'll pop up a window and you want to either look for a check box that says autoconfigure, or a drop-down menu under Connection Settings called Configuration. One of the options in there should be "Automatic configuration (DHCP)"

If it doesn't work then, I'd suggest hunting for drivers specific to your card, and once you get them we'll go for there.

---

