---
title: "The internets is broken!"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by The Morninglord on 2008-06-14
I bought a new laptop for college and the first thing I did was install Ubuntu on it. From the get-go I've had *zero* bad experiences and everything has worked absolutely flawlessly. Until now.

Two nights ago, I went over to a friend's house and tried to log into his wireless network. He provided me with the password (a painfully long Hex key) and I tried logging in. Eventually my keyring asked me to save the password and I clicked that I didn't want to, which seemingly disconnected me from his network. I didn't think much of it at the time, so I went merrily along my way.

When I got back, I logged onto my own network and everything worked fine. That was yesterday. When I woke up this morning, I noticed that my notebook could neither view or access any network signals. I don't know what happened. My other devices can access my network without any problem, so I know the issue is on this device.

When I click on the networking icon on the top-right corner of my screen, the only option I have is 'wired networking' where previously I would see a list of available networks. When I right-click, the only options I have are 'enable networking' (checked), 'Connection information,' 'Edit Wireless Networks ...' and 'About.'

Is this a hardware or software problem? The notebook is literally a week old, although I suppose it could be possible for a wireless card to die that soon. I just want to exhaust all of my options before I contact Lenovo for a replacement.

The notebook is a Thinkpad T61 with an Intel Pro Wireless 3945 card.

---

### Post by wormser on 2008-06-14
Most notebooks have a switch that can turn off wireless.  Maybe you accidentally hit it.  If that does not do it then post the output of iwconfig.

```
iwconfig
```If it returns nothing then post the output of ifconfig.

```
ifconfig
```

---

