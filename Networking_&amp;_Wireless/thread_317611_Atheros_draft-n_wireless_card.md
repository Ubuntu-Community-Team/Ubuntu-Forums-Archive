---
title: "Atheros draft-n wireless card"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by Lowfront on 2006-12-12
Part number 41U4780

I'm really stuck on getting this network card but having a difficult time getting it.  I'm getting an x60 think pad that preconfiguerd for a great price but this card isn't involved.

But I'm working on it, wondering if this card will work in ubunutu and if I should go through the trouble and get it.

Right now I'm getting the Intel card

---

### Post by FrodoB on 2006-12-12
Draft N is not supported by the mAdWiFi native driver at this time so you would have to hope that it will work with ndiswrapper:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

If there is any way you could get a Atheros 802.11g device  that would be a lot more likely to work out of the box.  If you could  get model  numbers for the devices it would help  some tell  what  device they actually use.

I would recommend that you stay on the trailing edge of this 802.11n craze as the normal 802.11g devices are more stable and will be around for a long time.  Unless you are trying to do things on your local lan that require high speeds there will not be much advantage anyway.

Is the device going to be mini-PCI or mini-PCIe. The mini-PCI is more common and there are lots of devices that can be used to add to a notebook. The mini-PCIe is newer and not as common or cheap.

see:

[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

---

### Post by Lowfront on 2006-12-12
Well I just found out I really can't get it anyways, lenovo doesn't sell just the hardware to be put in by me.  

I'm stuck with this guy
Intel PRO/Wireless 3945ABG


I believe I have read that that works with ubuntu out of the box

---

### Post by FrodoB on 2006-12-12
Well a lot of folks have problems with it, but a lot of them eventually sort it out, so search through the forum and get prepared before you get it and good luck.

---

### Post by Lowfront on 2006-12-12
they have problems with the Intel PRO/Wireless 3945ABG????


I'm really new to ubuntu and really can't handle anything complicated.  Am I in trouble?

---

### Post by FrodoB on 2006-12-12
Take a look at these posts. Are you?

[http://ubuntuforums.org/search.php?searchid=11101707](http://ubuntuforums.org/search.php?searchid=11101707)

I am sure that some of them have the answers, but I have never needed it so I did not participate in them.

---

### Post by Lowfront on 2006-12-12
I'm getting an x60 now they have intels and thinkpads which are atheros.

Should I try to go for the atheros without the g?

Are there any problems with that one?

---

### Post by FrodoB on 2006-12-12
You would have to get more information. Usually an Atheros 802.11a/b/g is compatible. Look for 180Mbps and the terms Super G or Atheros G and  you usually have a compatible one.

I have seen a couple of folks have to use ndiswrapper on the newer pre-N devices on the forum.

Oh, Atheros USB is always non-compatible with mAdWiFi.

---

### Post by FrodoB on 2006-12-13
Note this thread:

[http://ubuntuforums.org/showthread.php?t=317823](http://ubuntuforums.org/showthread.php?t=317823)

Looks possible.

---

