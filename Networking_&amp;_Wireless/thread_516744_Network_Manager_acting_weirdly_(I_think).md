---
title: "Network Manager acting weirdly (I think)"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by TehDooMCat on 2007-08-03
I have a laptop with a generic PCMCIA wifi card. I don't think my problem is hardware or driver-based, 'cause it can see it perfectly, and the card can see wireless networks and one time did connect to my home network, so I think it's something to do with NetworkManager.

It's connected to my network once before, and I could ping all the computers and so on. I can't remember what I did, but I remember it was with a static config (static IP, roaming mode disabled). Recreating what I did doesn't make it connect succesfully, however. In fact, I seem to have no control over when it connects, either.

I accidentally removed nm-applet from the tray too; how do I add it again? Starting it again doesn't do anything, I replaced it with the normal network monitor which doesn't let you do anythign to the network.

I can't really explain it well, but: how do I get it to connect to my home network?

---

### Post by spd106 on 2007-08-04
nm-applet is not a tray applet in the normal sense, it exists in the notification area. That means you need to make sure that you have the notification area applet running on the panel and that nm-applet is in the start-up options tab of the System -> Pref -> Sessions capplet.

Once you've got that working, post back and we'll try to help with the rest of the problem.

It might be worth having a read through this wiki page too
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by ugm6hr on 2007-08-04
> **TehDooMCat said:**
> I have a laptop with a generic PCMCIA wifi card. I don't think my problem is hardware or driver-based, 'cause it can see it perfectly, and the card can see wireless networks and one time did connect to my home network, so I think it's something to do with NetworkManager.

It's connected to my network once before, and I could ping all the computers and so on. I can't remember what I did, but I remember it was with a static config (static IP, roaming mode disabled). Recreating what I did doesn't make it connect succesfully, however. In fact, I seem to have no control over when it connects, either.

I accidentally removed nm-applet from the tray too; how do I add it again? Starting it again doesn't do anything, I replaced it with the normal network monitor which doesn't let you do anythign to the network.

I can't really explain it well, but: how do I get it to connect to my home network?

I think you should start from the beginning.  

Tell us your hardware setup:
```
lspci -nn | grep Network
lspci -nn | grep Ethernet
```

Let us know which driver the wifi card uses:
```
lshw -C network
```

Show us whether it is connected:
```
ifconfig
iwconfig
```

Show us whether it scans OK:
```
iwlist scan
```

It's much harder to help if you have already made certain assumptions about your setup that we are not aware of.

---

