---
title: "WiFi automatic reconnect not working properly"
date: 2016-06-19
forum: Networking &amp; Wireless
---

### Post by John Nagle on 2016-06-19
I've installed 16.04 LTS (amd64) Xubuntu on two EeePC 1001px machines. WiFi basically works, and will connect to a WPA2 network with a password. Fine so far.

Reconnecting, though, is troublesome. If the WiFi connection is lost and reestablished, a dialog pops up asking for the WiFi password. The password is prefilled; the system knows the network and the password. Clicking "Connect" dismisses the dialog but does not yield a usable connection. (Possibly because the connection had been lost for some time and something has timed out.) Then clicking on the toolbar two-arrow network icon causes the networking to recycle and connect successfully. 

This happens even with "Connect automatically" set. That popup shouldn't appear with "Connect automatically" enabled.

This is a problem because I want to run this machine unattended while it does something that doesn't require user attention.

This is similar to a [question from five years ago.]("http://askubuntu.com/questions/4037/automatically-reconnect-wireless-connection") Is this something that's still broken?

---

### Post by Rick St. George on 2016-06-21
Please follow instructions in Sticky "before posting in Network & Wireless".
And Post your Results.
Thanks!

---

### Post by John Nagle on 2016-06-23
As requested, a WiFi info dump is attached. Here's the basic system ID info. Freshly updated 16.04 LTS system. 

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
Parameters: ro, quiet, splash, vt.handoff=7
Xubuntu

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k

---

