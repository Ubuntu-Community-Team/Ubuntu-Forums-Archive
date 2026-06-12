---
title: "Periodically Losing Wired Network Connection"
date: 2015-05-29
forum: Networking &amp; Wireless
---

### Post by Chief_Wiggum on 2015-05-29
This issue has been driving me crazy for a while now.  Symptoms:

- The wired network connection on the machine will go down.
- USUALLY happens every day
- ALWAYS happens after 12:00pm
- ALWAYS will come back online after a variable period of time.  Sometimes less than one hour, sometimes eight or nine hours
- NEVER happens when the office is closed
- Cannot ping the gateway from the problem machine when it goes down
- We have other users on both wired and wireless with no connectivity issues, while at the same time this machine cannot ping the gateway

This is a small "server" running 14.04 desktop being used as a department file server in a small business.  It was running a very old 10.x Ubuntu version, and we never had a problem with it.  Literally, it ran for years with zero issues.  When this started, I figured I ought to update it, and did a clean install of 14.04.  Problem persists.

Machine has two built in NICs.  Problem persists no matter which one I use.

I purchased a USB NIC and set that up.  Problem persists.

Ran memtest on the machine for a couple of hours.  0 errors found.

When the machine is down, ifconfig shows the interface as UP with an IP (static) assigned.

Right now, the machine is plugged into a switch which is connected to the router, but I can plug the server directly into the router and the problem still happens.

I've checked syslog and dmesg during the problem times, and don't see anything of interest.  Although, I don't really know what I would be looking for.  lspci/lsusb shows the devices present during the problem time.

Since the problem continues despite the fresh OS and hardware changes, perhaps this is something going on in my network?  I have no idea what to check.  The only thought I had was maybe an IP address conflict or routing issue of some kind.  The server is on a reserved static IP and most of the rest of the machines are using DHCP.

If anyone has any idea where I should be looking, either on the machine itself, or somewhere else in the network I would greatly appreciate it.

---

