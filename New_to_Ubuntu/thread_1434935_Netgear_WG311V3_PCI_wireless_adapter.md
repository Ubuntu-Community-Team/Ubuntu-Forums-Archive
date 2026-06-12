---
title: "Netgear WG311V3 PCI wireless adapter"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by anewguy on 2010-03-20
I thought I would post this, since prior to installing this card for Linux I went looking on the net and found several articles/threads, but they seem to be out of date given my experience.  There are threads/wiki's out there saying you have to install wpa-supplicant and manually fill out the config file.  These must surely be out of date.

I just installed the Windows drivers (from the Netgear site itself) using ndiswrapper.  My SSID is hidden, so I manually requested connect to a hidden network - it asked for my WPA-PSK/AES type and password, put them on the keyring, automatically had the option to connect automatically checked, and everything went fine.  No problems, not even 5 minutes of work.  I did use ndisgtk instead of the command line to ndiswrapper, and everything has worked fine, been remembered from one boot to the next, etc..

I am running Ubuntu 9.10.

So, if you've been thinking of getting one of these wireless adapters (several places are selling these as refurbished - mine came from an EBay auction [2 cards]) don't be worried.  Mine were very inexpensive ($13 each including shipping) but work great.  Very simple to get running in Linux.  Forget the wiki's and how-to's that mention all kinds of things you need to do to make this adapter work as they are obviously now outdated.  Use the Windows drivers, ndiswrapper (and ndisgtk if you don't want to issue the command line things to ndiswrapper).

Dave ;)

---

### Post by mikewhatever on 2010-03-21
Why didn't you get a device with native Linux support? Doesn't Netgear make any?

---

### Post by anewguy on 2010-03-22
> **mikewhatever said:**
> Why didn't you get a device with native Linux support? Doesn't Netgear make any?

As an ex-systems programmer and systems administrator on everything from big iron to micros, my question would be why does it matter if it works?????

---

