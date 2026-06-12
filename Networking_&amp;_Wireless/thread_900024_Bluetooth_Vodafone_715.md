---
title: "Bluetooth Vodafone 715"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by samden on 2008-08-24
I have a Vodafone 715 (Huawei U120) phone, which I have connected using bluetooth (USB dongle) to Ubuntu 8.04 computer. I can connect it using the GUI for file sharing, and see saved files using obex.

I am trying to synchronise the phonebook etc with Evolution, and cannot get this to work. I have tried several pieces of software (Wammu, Multisync and BitPim) and cannot get them to recognise the phone. I have been following advice on many threads, but most notably these two:
[http://ubuntuforums.org/showthread.php?t=885765](http://ubuntuforums.org/showthread.php?t=885765)
[https://help.ubuntu.com/community/syncnokia6230iwammu](https://help.ubuntu.com/community/syncnokia6230iwammu)

```
hcitool scan
```
returns
```
	00:1E:10:01:A6:DF	phone
```
I have edited the rfcomm configuration file /etc/bluetooth/rfcomm.conf to:
```
rfcomm0 {
bind yes;
device 00:1E:10:01:A6:DF;
}
```
I then enter:
```
rfcomm connect 0
```
and confirm this on the phone, seems to connect fine.
But now if I enter
```
rfcomm
```
I get
```
rfcomm0: 00:1E:10:01:A6:DF channel 1 clean 
```
I understand this should say "connected", not "clean".

Neither Wammu nor BitPim are able to detect the phone. What am I doing wrong? How might I get this working?

---

