---
title: "Wireless Card in HP"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by amcavoy on 2006-07-25
I just purchased an HP notebook and installed Ubuntu Dapper for the 64 bit processors.  The notebook came with a wireless card installed already, but Dapper doesn't seem to recognize it.  How might I configure this card?

Thank you.

---

### Post by H.E. Pennypacker on 2006-07-25
You should use Network Connections (Network Settings).  It is used for setting up wireless connections (and any other kinds of connections).  

Check it out here:

[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

---

### Post by amcavoy on 2006-07-26
Thanks for the reply.  I have tried the suggestion, but under the Networking options I don't see my wireless connection.  It appears that Ubuntu doesn't know that a wireless connection even exists.  My card seems to be working fine in Windows so I don't think it's a hardware problem.  Is there any way I can manually search for wireless networks seeing as how it isn't recognized in the Networking panel?

Thanks again.

---

### Post by Slicedbread on 2006-07-26
Its most likely a BCM4318, most AMD HP's use the broadcom chipset. Search the howto's on installing bcm4318, there is an automatic script floating somewhere that should work.

---

### Post by H.E. Pennypacker on 2006-07-27
> **amcavoy said:**
> Thanks for the reply.  I have tried the suggestion, but under the Networking options I don't see my wireless connection. 

That means the card has not been detected.

> It appears that Ubuntu doesn't know that a wireless connection even exists.  My card seems to be working fine in Windows so I don't think it's a hardware problem. 

It's possible that Windows wouldn't recognize the card if the manufacturer didn't pre-install it (Windows and everything else).

>  Is there any way I can manually search for wireless networks seeing as how it isn't recognized in the Networking panel?

You can't search for any wireless networks before the card is recognized.  You would otherwise be able to search for networks using something like Network Manager, or the iwlist command in the terminal.

We have to first begin with determining the chipset (the name of the card as known to the manufacturer - remember that OEMs rename hardware they receive) of your wireless card.  You can do that by looking under Device Manager.  Find the WLAN interface.  First, do a forum search on that chipset to see if there is help on this already.  If not, reply to this thread and tell us about the chipset.  We'll go from there.

If you prefer using the terminal, you'll find the chipset with the lshw -C network command.

---

### Post by amcavoy on 2006-07-27
OK I just found out that I have the Broadcom 4311, not the 4318.  Will the 4318 driver work for this?

Thank you.

---

