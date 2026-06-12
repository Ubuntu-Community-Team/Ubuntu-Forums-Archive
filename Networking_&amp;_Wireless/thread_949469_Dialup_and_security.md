---
title: "Dialup and security"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by oygle on 2008-10-16
We have relocated, and can't get broadband, so have had to resort to dialup.

Previously, had a NAT firewall included with the ADSL router, but don't feel quite secure with only just Ubuntu.

Have installed Firestarter as a firewall, and will use GNOME PPP to dialup (currently using wvdial).

Will Ubuntu/Firestarter be 'as secure' as a NAT firewall, or are there other measures I could atke to improve security ?

One other issue now is the Ubuntu updates, I'm unable to do them all, and only do the security ones, as one file in the 'recommended' was 17 Mb.

Have considered using IPCOP, that would no doubt be more secure, plus the cache/proxy on it, would help surfing speed a little.

Would appreciate some advice please.

---

### Post by oygle on 2008-11-24
Would have ipmasq help with the security side of things , when using Firestarter and dialup ?

---

### Post by gTinker on 2008-11-24
[QUOTE=oygle]
Previously, had a NAT firewall included with the ADSL router, but don't feel quite secure with only just Ubuntu.
[/QUOTE]

You should feel secure since Ubuntu doesn't have any open ports by default, if you haven't opened any for any reason then it's still secure. NAT really is only so you can have more than one computer connected to the Internet connection at one time on the router, the dialup connection is going to be fairly low bandwidth for more than one connection at a time. Of course, it depends on how much surfing and downloading you do.

[QUOTE=oygle]
Have installed Firestarter as a firewall, and will use GNOME PPP to dialup (currently using wvdial).
[/QUOTE]

Remember that Firestarter is a GUI for configuring iptables, there is no need to have the GUI running in order for iptables to do its work. You can use the GUI to monitor the hits you are getting but that info is in kernel.log too. Firestarter on this connected computer could also handle Internet connecting sharing if you also had a hub or switch for a network.

[QUOTE=oygle]
Will Ubuntu/Firestarter be 'as secure' as a NAT firewall, or are there other measures I could atke to improve security ?
[/QUOTE]

In my opinion it will be as secure as when you were connected to the gateway (router).

[QUOTE=oygle]
Have considered using IPCOP, that would no doubt be more secure, plus the cache/proxy on it, would help surfing speed a little.
[/QUOTE]

IPCop would work fine and it could be similar to the gateway you used previously if you added a hub or switch. Then you would be able to have more than one computer connected to the dialup Internet connection at one time and they would share the bandwidth. With IPCop you have to have a computer which you can dedicate as firewall, although just about any old computer would do. I have run an IPCop firewall on a dialup connection with a 486 with 16MB of RAM and it had no trouble keeping up with a dialup connection. However, it was very slow browsing to router configuration pages.

---

