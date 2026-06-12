---
title: "Netgear DG834 (v2) Resetting"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by southanesq on 2006-08-01
Hi all,

I'm new to Ubuntu (and Linux) and have spent the last week using the excellent HOWTOs to configure my box.

I now have everything as I want it but for one niggle. I use a wired Netgear DG834 (v2) to connect to the Internet. In about one-in-three reboots the router resets itself (although it still shows as "active" in "Networking") and I have to de-activate and reactivate via "Adminstration" > "Networking" in order to get online.

Is this a common problem with wired routers or just me?

Like I said, it's only a niggle but any help would be appreciated.

Regards

Southanesq

---

### Post by southanesq on 2006-08-04
Polite bump

---

### Post by ske1fr on 2006-08-04
Only just found your post, but it strikes a chord with me.

When you say reset, do you mean the router restarts, flashes the indicator lights and apparently reconnects to the ISP (or telecoms) network?  Did it used to do this before you started using Linux?

This is not unlike the occasional problem I have, where I sometimes find that when I boot either of the machines attached to my router, although the router lights suggest it is functioning, it's impossible to use a browser or other internet software until the router is physically switched off and on again.  Your suggestion suggests that you can still access the web interface, so have a look at the log and see if you can see any activity before this reset, if the log file survives through it.

Does your ISP give you a static or dynamic IP address?  I've read that the latter can mean that when the ISP issues you with another IP address, the telecom provider stops recognising your internet session as valid, and you get this "frozen session", or that a process within the router crashes and fails to restart.

Oh and finally, have you set Ubuntu to collect an IP address from the router (DHCP), or have you set a fixed IP address?  If you've never needed to configure networking then it should be the former.

I don't know whether the above will help, but I can assure you you're not the only one with router issues, and they're not necessarily related to Ubuntu.

---

