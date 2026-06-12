---
title: "internet connection stopped working"
date: 2005-09-14
forum: Networking &amp; Wireless
---

### Post by c-m on 2005-09-14
I had been hapily using my netgear ma101 wireless adaptor since successfully setting it up in ubuntu sometime ago. However the other day i was having problems with the signal and so changed the channel on the router. Now my ubuntu box cannot connect to the internet using wireless lan. The wireless card can connect to the router fine, but cannot access the internet. The same goes for the PCI Kcorp 54g wireless card i set up today. It can happily access the router but not the internet.

Please help.

---

### Post by mlomker on 2005-09-15
Post the output of these commands as a place to start.

```

iwconfig
ifconfig

```

---

### Post by c-m on 2005-09-15
[QUOTE=mlomker]Post the output of these commands as a place to start.

```

iwconfig
ifconfig

```[/QUOTE]
 someone suggested that it may have lost its router or something or other, but a couple of restarts later and the thing just started working again. :-|

Now my only problem with wireless is that the signal strength keeps dropping for no reason. this happens on both cards, it will be at 75%-95% then all of a sudden it will drop to 0% then back up into the 70s. Any ideas about this?

---

### Post by mlomker on 2005-09-16
[QUOTE=c-m] it will be at 75%-95% then all of a sudden it will drop to 0% then back up into the 70s. Any ideas about this?[/QUOTE]

Interference.  Cordless-phones, other people's wireless networks in range, etc.  There use to not be very much stuff on the 2.4 Gig frequency but now it's crowded.

You can try changing the channel number on your access point.

---

### Post by c-m on 2005-09-16
the problem is every time i change the channel off the router, i cannot connect to it through the wireless in the ubuntu box. The windows one still connects though :-|

---

### Post by mlomker on 2005-09-16
Really?  I use a non-default channel on mine.  Do you reboot or re-attach using **iwconfig** after changing the channel?

---

### Post by c-m on 2005-09-19
[QUOTE=mlomker]Really?  I use a non-default channel on mine.  Do you reboot or re-attach using **iwconfig** after changing the channel?[/QUOTE]
 i've tried both without rebooting and with rebooting. last time it worked again after about 3 reboots doing other stuff. 

i am a good 25metres away from the router through 1 internel and 1 external wall. but that should easily be do able, especially since i can get over 90% signal strength and quality at times even the rain.

its just every so often the signal just drops off to nothing at then shoots back up. We do use wireless video senders in the house don't think they are the problem though since i've tried with them unplugged.

---

### Post by c-m on 2005-09-21
[QUOTE=c-m]i've tried both without rebooting and with rebooting. last time it worked again after about 3 reboots doing other stuff. 

i am a good 25metres away from the router through 1 internel and 1 external wall. but that should easily be do able, especially since i can get over 90% signal strength and quality at times even the rain.

its just every so often the signal just drops off to nothing at then shoots back up. We do use wireless video senders in the house don't think they are the problem though since i've tried with them unplugged.[/QUOTE]
 I have found the problem. I think it is the wireless video senders we use in the house. I have tried all chanels 1-11 but still without success (although the wireless B card in the room next to the router always works). Yet when i unplug the senders the connection is near perfect with my ubuntu box in the garage.

How can it be that the video senders effect the connection on all channels?

---

### Post by mlomker on 2005-09-21
> How can it be that the video senders effect the connection on all channels?

The video senders might be using all of the channels!  Video requires a lot of bandwidth so they use spread-spectrum technology to transmit on all of the channels.

One option (albeit an expensive one) would be to switch out your access point and card for one that operates on the 'A' band.  That works on 5 Ghz and there is a lot less stuff on that band.

---

### Post by c-m on 2005-09-21
[QUOTE=mlomker]The video senders might be using all of the channels!  Video requires a lot of bandwidth so they use spread-spectrum technology to transmit on all of the channels.

One option (albeit an expensive one) would be to switch out your access point and card for one that operates on the 'A' band.  That works on 5 Ghz and there is a lot less stuff on that band.[/QUOTE]
 oh well, its not really worth it, i'll only be living here for another few days anyway.

cheers.

---

