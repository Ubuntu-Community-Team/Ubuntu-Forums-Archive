---
title: "Network Throughput Question"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by RobNY on 2007-01-15
I have Dapper installed on an Asus A8R-MX mobo.  Northbridge is an ATI RS482 and the South is a ULI M1573.  According to the mobo docs, the NIC is a Realtek 8201CL.

After installing Dapper, the following driver was installed:

0000:00:1b.0 Ethernet controller: ALi Corporation M5263 Ethernet Controller (rev 50)

However, when I transfer a file from my Win PC to Ubuntu, I'm only getting about 3 MB per sec throughput.  All my switches/routers/hubs are 100 mb devices.

The install CD for the mobo references drivers from syskonnect website (Marvel).

I'm confused as to whether the current driver is correct and how I can take full advantage of 100 mbit throughput.

Any suggestions would be appreciated.

Thanks.

---

### Post by RobNY on 2007-01-22
This was solved as follows:

1) Samba is notoriously slow as outlined in several other posts so I didn't focus on this protocol.

2) I was accessing an internal FTP server (pureFTP) using the external DNS name.  This was forcing the data over a Passive FTP session (due to NAT translation) using the external DNS hostname.  This, in turn, caused my network router to have to re-port-forward the traffic back to the Ubuntu box.  Dumb on my part.  By using other aliases (or dot addresses) and forcing an Active FTP session, the throughput went up to about 10 MB/sec -- which is acceptable.  :-)

Posting here because I realize that my initial question focused on the NIC and not the application.  This was uninteded misdirection on my part.

---

