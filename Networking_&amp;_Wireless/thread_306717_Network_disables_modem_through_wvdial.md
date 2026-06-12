---
title: "Network disables modem through wvdial"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by Coburn on 2006-11-25
When I dial up using wvdial, then use Network Manager, wvdial is disabled.

Two Athlon-based computers w/6.06, connected w/NFS.  ICS thru firestarter.  Modem is a Lucent Winmodem; client also has an Intel 537EP.  Netscape is my dialup provider.

There is something happening behind the scenes when I use two different sets of dialup connection tools.

At first, on my server computer, I used pppconfig and pon to get online.  Worked flawlessly.  8) 

I then configured it as the client computer and connected through ICS using the Intel modem on the other box.

Then I reconfigured it as the server and started running firestarter and NFS at the same time as my internet, on the server.

I had been using wvdial as my connection, since it gives you verbose feedback on what is happening.  I configured it on this computer too.

It started doing what the client computer used to do.  Whenever you connect with network-admin, or simpler tools that use the same processes to connect, you can no longer use wvdial or related programs, AKA gnome-ppp.

The most revealing example occurs when I want to specify DNS servers in order to be able to access certain sites; e.g. use Synaptic.  I need to do this because Netscape gives me primary, remote, and local IP's with every connection, and they change constantly.  :???: 

Clicking OK in network-admin does an auto restart of the network.  Somewhere in the process a call occurs that conflicts with wvdial.:twisted: 

The modem is kicked offline (Error 16 --modem hangup), and tries again to reconnect.  It fails repeatedly.  Restarting (sudo) wvdial gives an Error 16 again.](*,) 

Log file only gives the same vague information.  A modem hung up the phone.  FYI.:rolleyes: 

I don't think it is anything to do with NFS, as Samba gave the same result.

Before I report this as a conflict, can anybody help me save time tracking this down?

---

