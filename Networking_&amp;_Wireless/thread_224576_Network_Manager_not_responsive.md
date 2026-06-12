---
title: "Network Manager not responsive"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by mlaverdiere on 2006-07-28
Hi,

I have 2 laptops with Kubuntu Dapper (both freshly updated) on which I use NetworkManager/KNetworkManager, after making sure that the file /etc/network/interfaces have been modified like it should (i.e. commeting out all the lines related to network interfaces, except the lo one) .

On the first one (pentium 4 2.8 with an Atheros wifi internal card using the madwifi driver), NM is really responsive, i.e. as soon as I activate/deactivate the internal wifi card or I insert/remove my wifi Netgear MA401RA pc card, NM is recognizing the event and making necessary adjustments, and I can swith between networks without any problem.

On my second laptop (AMD Sempron 3000 wit a Broadcom NM4318 internal card, using the kernel driver or Ndiswrapper), NM is working well at boot time and when I start a KDE session, it connect successfully to my wifi home network.  The problem is that after this connection is well established and stable, NM becomes unresponsive, i.e. if I insert my wifi PC card it won't detect it.  Worst, if I deactivate the interface on which the connection is establiched, it won't notice and the Knetworkmanager will still show an active connection on this interface, even if, of course, this connection is not usable anymore.  The only thing for which NM seems ato be reactive is for the detection of new/lost networks, i.e. each time a network appears/disappears in the neighborhood, it will report it.  If I want NM to "reset" and take into account what happened with the interfaces, I have to stop and restart it again, using these commands:

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager start
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher start

In order to make sure that the problem is not due to the Broadcom internal card, I have completely deactivate it (making sure that all the related drivers are blacklisted) and rebooted Ubuntu, started a KDE session and then tried to insert my wifi PC card, which is well and quickly recognized on my first laptop.  The result on my second laptop is that  NM has not detected it.  I've also did some testing in Gnome, using nm-applet instead of Knetworkmanager, with the same results.

At the end, the only difference I can see between these 2 laptops, from a Kubuntu installation perspective, is that on the first one, I first installed a beta version of Kubuntu Dapper, with NM, and then, I n have updated it regularly.  On the second one, the installation have been made with the final release of Dapper...

Someone has an idea of what's going on and what I should do to have a "responsive" NM?

Thanks for your help.

---

