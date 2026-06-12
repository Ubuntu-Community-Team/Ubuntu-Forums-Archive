---
title: "[SOLVED] help setting up wireless connection"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by cpeters12 on 2008-07-12
Hi,

I've done alot of searching around this forum but haven't found anything yet.  I was looking in the sticky "How To: Manual Network Configuration without the need for Network Manager".


I am setting up a WEP Connection.  The code is pasted below.  I go through the process and then it says:
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Is there something I did wrong?  Thanks

Code:

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> **essid** "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  <<<----See note below
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

---

