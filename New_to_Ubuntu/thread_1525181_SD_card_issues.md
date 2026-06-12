---
title: "SD card issues"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by az bjj az on 2010-07-06
hello I am completely new to linux systems.  I purchased a gateway netbook and immediately installed ubuntu 10.04 netbook edition on it.  The computer has a built in smart card reader and I wanted to test it out so I inserted a pny SD card from my digital camera in it and there was no recognition by ubuntu.  I then tested out my micro SD card from my cell phone in its carrier and still nothing.  Its almost as if the ubuntu doesnt recognize I have a smart card drive.  I downloaded Gnome smart card reader to see if it would fix it but still no luck.  I should note when the SD card is in the camera and plugged in through the USB port the ubuntu recognizes it.  

Any ideas on how to fix it?

thankyou for your help

---

### Post by cariboo on 2010-07-06
The first thing to do, is have a look at dmesg, to see if the card is detected. Open an Applications->Accessories->Terminal and type:

```
dmesg | tail -n5
```

The output should look something like this:

```
dmesg | tail -n5
[ 7064.152679] end_request: I/O error, dev sr0, sector 4096
[ 7579.038301] sd 4:0:0:0: [sdb] 3970048 512-byte logical blocks: (2.03 GB/1.89 GiB)
[ 7579.062367] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 7579.119296] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 7579.119306]  sdb: **sdb1**
```

as you can see in the example above, my SD card is detected and given a device label of **sdb1**

Depending on what version of Ubuntu you are using, it should be auto-detected and an auto play notification similar to the on in Windows should come up.

---

### Post by az bjj az on 2010-07-06
i typed in the message but got a different response

[21737.656218] wlan0: authenticate with AP 00:0f:66:aa:ef:9f (try 1)
[21737.661049] wlan0: authenticated
[21737.661135] wlan0: associate with AP 00:0f:66:aa:ef:9f (try 1)
[21737.684870] wlan0: RX AssocResp from 00:0f:66:aa:ef:9f (capab=0x15 status=0 aid=1576)
[21737.684883] wlan0: associated

---

