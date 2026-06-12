---
title: "Clock ID is equal to 1 in PTPd client"
date: 2014-08-13
forum: Networking &amp; Wireless
---

### Post by h.hittini on 2014-08-13
Hi,

I have two machines running PTP daemon
The server is running Ubuntu Server 14.04, the client is running Ubuntu Server 13.10
I used the following commands to run the ptpd
```
sudo ptpd -G -b em1 -C -z    #On the server machine
sudo ptpd -g -b wlan2 -z -C    #On the client machine
```
Both of them show that "Startup finished successfully"
but the clock ID in the client is 1 and I don't see any messages indicating time synchs
This is what the server shows
```
2014-08-13 13:43:14.144331, mst, 90b11cfffea6e594(unknown)/00
```
and this is what the client shows
```
2014-08-13 13:51:17.857819, lstn_init,  1
```
Is there anything wrong with my commands?
Thank you

---

### Post by h.hittini on 2014-08-14
PTP daemon uses multicast by default, I needed to turn multicast on in my router
Now the client is synching

---

