---
title: "LTSP and Windows 2003 server DHCP"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by newsflash on 2007-04-23
Hi!

I've just installed LTSP 5 on a Ubuntu 7.04 machine, but I can't seem to get it to work with my Win 2k3 server DHCP. I've added the following options to the Win DHCP server:

option 12 newsflash-server
option 17 192.168.0.1:/opt/ltsp/i386
option 66 192.168.0.1
option 67 /opt/ltsp/i386/vmlinux-2.6.20-15-386
option 211 tftp

I found the options to set at the ltsp.org wiki. I read a bit further and found this:

"Remember that windows pads the root-path with 000 so the path passed to the terminal is /opt/ltsp/i386000"

So does this mean I have to rename /opt/ltsp/i386 to /opt/ltsp/i386000 ? I tried this but my clients still can't find the tftp image. Any suggestions?

Thanks
-Vin

---

### Post by haelters on 2007-04-26
if you are talking about the tftp image, it is not configured by the option 17 (which is the option for the root-path for the nfs).

Does your client get an kernel when it boots with PXE ?

---

### Post by peckman12 on 2007-04-28
Just add the following on your client reservations:

NOTE: You may be able to set some of these on the scope, but I know they work when you add all of them directly on the reservation.

NOTE: These must be placed at the client reservation level to work.

17 Root Path - 192.168.1.100:/opt/ltsp/i386
66 Boot Server Host Name - 192.168.1.100
67 Bootfile Name- /ltsp/i386/pxelinux.0

---

### Post by peckman12 on 2007-04-29
YOU MUST CORRECT THE SETUP LTSP DOES NOT SUPPORT THE WAY OPTION 17 is in other messages.
JUST REMOVE THE IP LIKE BELOW!  I was having a video problem before this.

Just add the following on your client reservations:

NOTE: You may be able to set some of these on the scope, but I know they work when you add all of them directly on the reservation.

NOTE: These must be placed at the client reservation level to work.

17 Root Path - /opt/ltsp/i386
66 Boot Server Host Name - 192.168.1.100
67 Bootfile Name- /ltsp/i386/pxelinux.0

---

