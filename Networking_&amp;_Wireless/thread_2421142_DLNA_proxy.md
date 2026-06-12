---
title: "DLNA proxy"
date: 2019-06-17
forum: Networking &amp; Wireless
---

### Post by peridian on 2019-06-17
Hi,

I'm using mini-DLNA to access my multimedia, but at the moment it's having to jump through some hoops that I was hoping to simplify.

Is there a way to have a DLNA (uPnP) server receive the broadcast traffic on the same subnet that it is on, but to advertise the TCP address of the server as being on a different subnet?  I.e. have it act as a proxy that redirects to another server?  Failing that, is there any actual proxy software that can redirect the traffic (other than the firewall)?

At the moment, my server is having to access the data source via SMB, as it is on a different subnet, but that has additional networking overheads involved.  I had wanted to redirect the traffic from the multimedia client to the other subnet so that it streamed the content direct, but the mDNS proxy on my firewall just doesn't behave well.

Regards,
Rob.

---

### Post by slickymaster on 2019-06-17
*Thread moved to **Networking & Wireless**.*

---

### Post by TheFu on 2019-06-17
Can't help with the DLNA proxy question. I avoid it by using a VPN or connecting to the webserver that controls my DLNA server directly, which supports streaming video/audio through a web interface.  From anywhere in the world with a reasonable internet connection, once I either ssh-tunnel or vpn into the same network as the DLNA server, using the web interface allows remote streaming.  It will also transcode video based on the available bandwidth.

If you have a choice between using SMB or NFS, use NFS.  This is well understood in the Kodi forums.

---

