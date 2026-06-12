---
title: "Network controller: Qualcomm Atheros Device 0042 (rev 30) [Wifi Not Working]"
date: 2015-10-16
forum: Networking &amp; Wireless
---

### Post by adrin7 on 2015-10-16
Hello, Im new, I've a aspire e 15 and I Installed ubuntu gnome 14.04 LTS, everything works super sweet, except the wifi, I made some research and ask for help in the IRC ubuntu channel
but nothing... so here's some data:


```
$lspci
      Network controller: Qualcomm Atheros Device 0042 (rev 30)
```

```
$ lspci -vv -s
     Network controller: Qualcomm Atheros Device 0042 (rev 30)
    Subsystem: Lite-On Communications Inc Device 1806
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 255
    Region 0: Memory at f0800000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>

```

Thanks  in advance for any help & cheers!

---

### Post by Hadaka on 2015-10-16
Hi, post # 3 should load the driver you need,,,ath10k
[http://ubuntuforums.org/showthread.php?t=2298485&highlight=ath10k](http://ubuntuforums.org/showthread.php?t=2298485&highlight=ath10k)
thanks

---

### Post by jeremy31 on 2015-10-17
Device 0042 is still unsupported, bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1496878](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1496878)

---

### Post by adrin7 on 2015-10-17
So, should i try the post Hadaka is recommending? or there's no point in trying that?.

---

### Post by Hadaka on 2015-10-17
Hi, I apologize for not being up to date on the new ath10k driver.
Qualcomm Atheros Device 0042 (rev 30) is not yet supported

you can verify this by doing,.
```
modinfo ath10k | grep 0042
```
you wont get a result,because its not there.
you can try a usb wifi untill such time are your 0042
gets some kind of working driver,
good luck

---

### Post by adrin7 on 2015-10-18
yeah, totally true, it output the following:

```
modinfo: ERROR: Module ath10k not found.
```

well thank you both guys :), i really appreciate the help and the clarification.

so, should i report it? maybe in launchpad or something, just to make some "pressure"?.

---

### Post by Hadaka on 2015-10-18
you can go here,,
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1496878](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1496878)
and add your name to the list in the bug report,I cant help much as to how
having never had a need to file a bug report.

---

### Post by rinfinity on 2015-11-07
[http://ubuntuforums.org/showthread.php?t=2300861&page=3](http://ubuntuforums.org/showthread.php?t=2300861&page=3)

Here's all you need to make this card work. Head over to post#25 and post your result with the fix.

---

