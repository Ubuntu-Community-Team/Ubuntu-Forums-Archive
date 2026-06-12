---
title: "Where's my printer's MAC address?"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by Coburn on 2007-03-02
I can't find my Epson CX5000's MAC address!   I've looked on the label and the self-test page, looked through half a dozen config files, and tried as many commands like udevinfo, lsusub, and ifconfig.

CUPS docs say it should be "on the bottom of the print server."  What's that?  The address isn't in the files I looked in.

The recommended methods for setting up my printer as a network device tell you to use the MAC address.  This combination of printer and OS is very finicky, so I don't think a generic setup will work.  But, yeah, it does work as a local printer.

My network is just two cans on a string.  NFS.  The AIO printer is hooked to the USB of the client.

Thanks.

---

### Post by spd106 on 2007-03-03
Are you sure it has a network card?

From the information I can gather it has only a USB interface.

---

### Post by Mr. C. on 2007-03-03
Only Ethernet devices have MAC addresses.  Your printer is a local USB printer.

---

### Post by Coburn on 2007-03-05
Props to you guys; you are right.

Epson tech support told me:

"[I]The CX5000 is not a networkable unit out of the box. You can share the
printing features over a network with a peer to peer setup.  (Unit must be
directly connected to one of the computers on the network.)

Note: There will be no networking option for the scanner portion of the
unit.[/I]"

And:

"[I]The CX5000 does not have an integrated NIC or Print Server Card and hence
there is no MAC address for it.[/I]"

Apparently the CX5000 is a "Lite" printer.  Thank you, Sam Walton!  =D> (Well, at least I could afford it.  And it's more than adequate for my needs.  So, yeah, thanks.)

But that does not solve my problem completely.  I see now that the behavior of CUPS-mgr when I try to add the printer as a network device is actually normal.

So, I ask myself, how do I "share the printing features over a network with a peer to peer setup?"  I mean, I did like they said and made sure the "unit [was] directly connected to one of the computers on the network.":rolleyes:   Also, the computer it is _not_ connected to (the server) does _see_ it on the network--but jobs sent to it don't come out of the front part!:evil: 

I think Firestarter (on the server) is configured to allow port 631.  I should check if it passes print jobs.  Any other ideas?:-k

---

### Post by Mr. C. on 2007-03-05
You are confusing two concepts.  A network printer has several meanings. 

In general, a network printer indicates the printer itself has hardware that allows connection directly to a network (such as Ethernet, TokenRing, AppleTalk, etc.).

A peer-to-peer (sic) printer really is a printer hosted and managed by the native OS, where its resources are made available through a compatibility layer.  In otherwords, the Windows drivers and software that come with your printer allow your Windows system to either a) provide its own sharing ability, or b) use the native windows file and printer sharing capability.

Your printer software, drivers, and Windows are required to do this.

Since such software doesn't exist in Linux, you cannot share this printer, nor will Cups be able to find it; i.e. because it is presently not on the network.

Connecting and configuring the printer to a running Windows system, will allow you to use Samba to reach the printer, provided your USB printer uses Windows File and Print sharing and not its own protocol.

MrC

---

