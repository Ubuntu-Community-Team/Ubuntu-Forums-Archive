---
title: "Amateur Radio AX25 Config"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by ka1vgm on 2008-08-10
I am having troubles setting up AX25 on my machine. Let me give some background"

I am new to AX25 but not linux.  I have Ubuntu 8.04 server with ax25 installed.

I can connect from this computer with minicom to other packet stations. Other stations can connect to me.. I have a KPC3+.

When I put the TNC into KISS mode and start up ax25, kissattach, etc..I can send out a connect request : axcall vhfport kb1nxe-10

Monitoring it from another tnc I can see the other station sending the connect acknowledgment with their connect info but my machine never accepts the connect...

When i check ifconfig I can see many tx packets.. but no receive packets..

Is there a setting file in inetconf I need to change to allow incoming connects on ax25?

This seems to be the only thing I can't figure out..

I can connect to this same tnc with minicom (out of kiss mode) and have a conversation)

Just seems like I am getting blocked at the ax25 end of incoming connects..


Any help would be appreciated.

KA1VGM

---

