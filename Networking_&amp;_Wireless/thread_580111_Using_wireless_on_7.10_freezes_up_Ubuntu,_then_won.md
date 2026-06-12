---
title: "Using wireless on 7.10 freezes up Ubuntu, then won't reboot"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by tra4d on 2007-10-18
Just downloaded and installed 7.10 desktop version.  Wireless card (DLink DWL G630 card on Dell laptop) works out of the box, sees wireless network.  But, when I configure the network to connect to this wireless network and setup WPA, it freezes everything and then nothing responds at all.  Tried to do a hard reboot and then won't boot up.

Reinstalled, tried again and had the exact same results.  I have seen many a post where this happened to others, even those running 7.10 Beta releases.  I.E.: 
[http://ubuntuforums.org/showthread.php?t=571840](http://ubuntuforums.org/showthread.php?t=571840)

Anybody have any ideas?

---

### Post by spd106 on 2007-10-18
Which driver is your card using? Are you using 64-bit like the others in the thread you linked to?

According to the [wiki]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink") there are two different versions of that card each with a different driver.

---

### Post by tra4d on 2007-10-19
In response to your questions:

1.  Not sure, it won't boot anymore (stops at CUPS starting).

2. No, 32 bit.

---

### Post by tra4d on 2007-10-19
Ok.  I have reinstalled.  After running:
```
sudo lshw -C network
```
I see that the driver is acx_pci.

After looking here:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)
I think I may have to use ndiswrapper.  My hardware version is B1 so I think ndiswrapper may be the way to go.  

Anybody think there is a way to get this to work w/o using ndiswrapper?  Any help/insights would be appreciated.

---

### Post by tra4d on 2007-10-19
After some more searching, I think the hardware version I have doesn't support WPA.  

See this:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/)

So I am assuming that even if there is a correct driver out of the box, it will not do WPA.  This is probably why the system was locking up.  Can anyone confirm this?

---

