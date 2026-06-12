---
title: "Networking Epson USB printer (NFS)"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by Coburn on 2007-03-01
My Epson CX5000 printer isn't recognized by my home network.  I'm running Dapper on 2 computers hooked by a wire through a switchbox.  (My network is NFS, not Samba.  I tried setting up Samba and found it too finicky about settings, so I shelved the project until I have more time.  Then I broke the Windows on the dual boot that I needed Samba for, so, no worries!)  The printer is not hooked to the router, but to the client computer's USB port.  The server computer is running Firestarter, but I haven't checked the settings yet.

There is no point checking settings because I haven't assigned an IP address to the printer yet.  To do that, the docs I am reading say I should know the MAC address of the printer.  It is not on the label, not on the self-test page, and I am so far unable to find it using GUI or command-line.  As an example, I tried <netstat -p | less>, but why would that work if the printer is not a network-connected device?  I dunno.  Maybe the MAC was on the box.  I should go to Wal-Mart and look at the ones on the shelf...:lolflag: 

I have tried a lot of different ways of addressing the printer to set it up as a CUPS network device.  Again, the recommended way for Epson, per CUPS, is to do <socket://{address}>, but I have no address.

Anybody got a way out of this catch-22?:confused: 

Thanks

---

