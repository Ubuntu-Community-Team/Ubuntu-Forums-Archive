---
title: "new to linux, trying to stay simple, wireless headache."
date: 2010-04-10
forum: New to Ubuntu
---

### Post by gunnbuntu on 2010-04-10
I'm building an HTPC to save money on the cable bill, and in an effort to keep costs down im planning to use ubuntu instead of windows.

I've never used linux before so its going to be a learning experience. I've put together most of the components I plan to buy, but when it came time to pick a wireless adapter I noticed a lot of comments about the ones I looked at not being compatible with linux.

I know there is a wikilist here for cards that will work, but the thing is it all reads as gibberish to me since I have zero experience with linux right now.

If it's not too much to ask could someone just point me in the direction of a usb dongle wireless adapter that would be plug and play with the latest version of ubuntu?

I'm going to have to finance the parts so I would like to be sure it would work before ordering so I don't have to deal with a difficult rma process if I order the wrong thing.

Thanks in advance.

notes - my current wireless is 802.11g, would like to update to N later so if it has N capability thats a plus, but not required.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128439](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128439)
thats the mobo in case its important
and the build is for an HTPC to run boxee etc.

---

### Post by Georules on 2010-04-10
Hopefully this can help:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Scroll down a bit and you can find links for people's success with different USB wifi devices.  Check the "works out of the box" column.

---

### Post by huygens on 2010-04-10
I have a built in Intel WiFi card, so I cannot guarantee that it will work.

However, reading the Ubuntu wiki about supported (or not) adapters (check [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)), I have more or less randomly picked-up one which is working out of the box (plug and play) on Ubuntu Karmic (so the latest released version).
This USB dongle is a D-Link DWA-110 ([https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB)), it is reported as working out of the box. It is however only 802.11g compatible, not n.

If you really want to have 802.11n, then here could be a possibility.
From D-Link, there is another adapter compatible 802.11.n that's looking promising, it's the DWA-140. However, if you have the "B" hardware (instead of the "A", it's the hardware revision), you might have trouble with it using Karmic. There are however resources to help solve the problem, but it is not really simple:

[LIST]
[*][http://swiss.ubuntuforums.org/showthread.php?t=1333255](http://swiss.ubuntuforums.org/showthread.php?t=1333255)
[*][http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/dwa-140&ei=zjhAS7OxJIfEsQPYg9nGBA&sa=X&oi=translate&ct=result&resnum=6&ved=0CBgQ7gEwBQ&prev=/search%3Fq%3D07d1:3c0a%26hl%3Den](http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/dwa-140&ei=zjhAS7OxJIfEsQPYg9nGBA&sa=X&oi=translate&ct=result&resnum=6&ved=0CBgQ7gEwBQ&prev=/search%3Fq%3D07d1:3c0a%26hl%3Den)
[/LIST]

N.B.: Dongles seem rather badly supported on Linux in general... :-( so I would do some kind of dongle dance while buying one, just to please their gods so that it will work out of the box ;-)

---

### Post by bear24rw on 2010-04-10
What i usually do it go to newegg, sort by reviews and then just go down the list and search the reviews for 'linux' or 'ubuntu'

first one that comes up:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833130111](http://www.newegg.com/Product/Product.aspx?Item=N82E16833130111)

search for linux, looks good people say it works great

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010410031+1133010001&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=31&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010410031+1133010001&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=31&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

---

### Post by buddyd16 on 2010-04-10
a solution that might be a bit over the top is to buy a wireless bridge like the Linksys WET610N this way you avoid the whole wireless headache and just connect via ethernet.

---

