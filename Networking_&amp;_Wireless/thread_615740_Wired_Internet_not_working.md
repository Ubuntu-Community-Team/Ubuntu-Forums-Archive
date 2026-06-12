---
title: "Wired Internet not working"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by Voyageur on 2007-11-17
This is driving me nuts!
I have an Ubuntu laptop connected to a wireless network with Verizon FIOS.
I have connected a newly installed Ubuntu desktop to port 1 on the router using a cable. The internet does not work on the wired desktop.
I have set the eth0 properties to DHCP with an IP address 1 up from the wireless laptop. The subnet mask & gateway address are the same as the working wireless laptop connection.
Any pointers?

---

### Post by jshurst on 2007-11-20
You say that you have setup the wired connection with DHCP on address up from the laptop...Do you mean that your router handed out this address or that you assigned it a static one?

If you set it static then I would change it to just accept the ip address from the router and see if that works first, then try to change it to a static address.

Also, usually unplugging the router and waiting for 10-20 seconds then plugging it back in usually does the trick.

J

---

