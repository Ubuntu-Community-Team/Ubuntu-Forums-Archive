---
title: "Network Card Not Active"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by kbow on 2008-05-15
I have a Dell Latitude D830. It's running XP as the main OS so I decided to try the Option in the new 8.04 to Install Ubuntu without having to mess with the partitions.

I went ahead and installed, rebooted system and it booted into Ubuntu fine (Gave me choice of Xp or Ubuntu).

I get into Ubuntu and do not have any Network connections (Wired or Wireless). I am on a DHCP Network, and I made that change but I don't even have a link light.

Can anyone help with this ? Not sure where to do next.

Card is Broadcom NetXtreme 57xx Gigabit Controller

---

### Post by NAKLOV on 2008-05-15
Hi,

Try typing the following

> dhclient

---

### Post by kbow on 2008-05-15
Thanks for the Reply.

I ran dhclient from the command line, and it's basically says "Network Is Down" for both Interfaces, the Wired and Wireless.

Ifconfig shows the Interface with a 169.254.x.x address and shows what is the probably MAC address of the card.

When running Network Tools from the GUI, it states "Interface Does Not Exist"

Running lspci shows the Broadcom card listed. 

I can restart back into XP and all interfaces are in proper working order.

Any more ideas ?

---

### Post by kbow on 2008-05-15
Dell Latitude D830

Broadcom NetXtreme 57xx Gigabit Controller
Dell Wireless 1490 Dual Band WLAN Mini-Card

Yesterday, I installed Ubuntu 8.04 using the option "Install Inside Windows" 

I am now running Windows Xp and Ubuntu, but when I boot into Ubuntu 8.04 it does not detect any Network Interfaces. I don't even have a link light.

Anyways just trying to get up and running

Thanks

---

