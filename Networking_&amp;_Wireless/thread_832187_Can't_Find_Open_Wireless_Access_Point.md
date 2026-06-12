---
title: "Can't Find Open Wireless Access Point"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by evlutn on 2008-06-17
Hi all,

I've been searching for an answer to this problem but I haven't found one, so hopefully someone here will have an answer.

I have a Broadcom 4318 wireless card that's working just fine with the wireless fix and ndiswrapper.  I'm staying at a friend's house and she can connect to an open wireless connection in the area but it doesn't show up on network-manager, even though we're sitting right next to each other.  She's using XP and I'm using Hardy.  Is there anything I can do to be able to see this connection?  Any solutions?

Thanks

---

### Post by pytheas22 on 2008-06-17
If the AP that you're connecting too is far away, then it might be the case that it's just out of range for your card.  Maybe your friend's card has a better antenna.  But I'm surprised that you really can't see the network at all.  Did you try scanning from the command line (iwlist wlan0 scan) several times to see if it gets picked up at all?  And you're sure that your card works in other locations?

If so, the only suggestion I have for trying to get a better signal is to try different rates, e.g.:
```

sudo iwconfig wlan0 rate 1M
```

might increase your range.

Also try moving the laptop around a lot to see if it makes a difference.  At longer ranges (I know from experience) even literally a centimeter in one direction or the other can be the difference between a strong signal and no signal at all.

---

