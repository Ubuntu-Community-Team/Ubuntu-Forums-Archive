---
title: "Fast and easy to use interface for pppoe over wireless network"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by Dre8927354 on 2008-10-10
Hi,

I stay in a student village in South Africa and each individual computer needs to use pppoe over a wireless network to connect to the internet. Each resident receives his own user account with a 1gB cap limit, however, needs to share a computer with a few other students. Is there a gui for Ubuntu that can make it simpler to establish this type of connection. For example, it is really tedious and intimidating to use “pppoeconf” every time you need to change the username and password. As far as I know there is no graphics indicating a successful connection except for the “plog” command  which, if I understand correctly from the IP addresses, that the computer found the IP of the dns and the dns assigned an IP to the computer. I have found that it is very difficult for the average user to interpret. Another problem is that the broadband connection is very unstable and it makes it difficult to pinpoint the source of the problem, for instance, is it a problem of the network manager of the computer or the network itself. I also realised that the network manager applet in combination with the wireless network is somewhat buggy...

---

### Post by funkydan2 on 2008-11-04
[me too! and also for the College environment.]

I've been trying to find this for Intrepid as well.

In Hardy, (with NetworkManager 0.6.x) I could connect to PPPoE connections by clicking on the nm-applet icon in the system try, and selecting the PPPoE connection in the 'Dialup-Connections' submenu (that appeared after setting up the connection through pppoeconf and removing a few rogue lines from /etc/network/interfaces).  However with NetworkManager 0.7, it seems that this functionaility has been removed.  I can see that there's new interface for setting up DSL connections (which I presume is PPPoE) however that seems to only be for *wired* connections and I can't seem to work out how to make it work for *wireless/wifi* connections.

@Dre - for the various users, could you setup differently named connections form them?  e.g. Bobs_dsl-provider/Toms_dsl-provider etc. and then just use pon/poff as needed?  It's not a nice, gui, but it may save the hassle of using pppoeconf.

---

### Post by anupamsr on 2009-05-24
Any updates on this front?

---

### Post by zerlgi3 on 2009-09-05
> **anupamsr said:**
> Any updates on this front?

PPPoE over wireless devices is definitely needed in NetworkManager / nm-applet

Since it is possible via command line.

another example is a virtual wireless device as provided by the iburst driver
ibdriver.sourceforge.net.  It uses the wireless stack so as to provide signal strength to network tools like Network manager, Kwifimanager, etc.
However nm-applet doesn't allow pppoe over wireless even when setting
/etc/NetworkManager/nm-settings.conf to "managed"

---

