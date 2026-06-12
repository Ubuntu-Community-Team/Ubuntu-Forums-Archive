---
title: "Bluetooth obex file transfer"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by ltmon on 2006-11-12
Hi All,

Just got a new phone (Nokia 6131) and I'm trying to send files to it via Obex.

Neither kbluetoothd or gnome-bluetooth can see my phone however.  The phone can see my laptop, and typing:
```

hcitool scan

```
into a terminal finds my phone also, but no luck with the GUI utilities.

If I pair from my phone, then kbluetoothd finally sees the phone (in "bluetooth:/"), but all obex file transfers from my laptop to the phone just hang.

Sending files the other way around works however.

Can anybody shed some light on this?  What log files would I possibly see a problem in?

L.

---

### Post by graz848 on 2006-11-17
Same problem! hcitool scan see thedevice but no way to send to it files via ny GUI programs. the only command-line tool (partially) working is obexftp. It was all right in Edgy.
Help us!!!

---

### Post by ltmon on 2006-11-17
I fixed it up by compiling the newest version of kbluetoothd for myself.  It seems the version included in Edgy doesn't match up with the versions of the libraries it uses.

As far as fixing obex transfers goes, this was a bug with openobex that caused it to lock up on my particular phone model.  Downloading and recompiling the latest obexftp release fixed up my file transfers.

I thought my days of compiling this and that to get things working on Linux were over, but at least it does now all work fine.

---

### Post by pavel_kbc on 2006-11-28
nothing works for me i give up :( ubuntu sucks on few way..

---

