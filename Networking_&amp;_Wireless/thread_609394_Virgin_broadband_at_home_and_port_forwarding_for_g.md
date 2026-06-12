---
title: "Virgin broadband at home and port forwarding for gtk-gnutella"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by baybe1111 on 2007-11-10
I think I have a firewall problem with my modem. Its a GlobeSurfer II 7.2 connecting to the Virgin 3G/HSDPA network. I've tried to configure port forwarding via the menu on 192.168.1.1.

I set the connection settings/security/portforwarding/

local host: to my ip address from ifconfig (192.168.1.2- I also tried pointing it to a domain name instead, but didnt work)
protocol:any
forward to port: specify: somewhere aroound the 52000

Then I set gtk-gnutella to listen on the above port.

Then voilla- nothing happens. gtk-gnutella still says I'm firewalled and trying to download a torrent fails.

Any ideas as to what to do next would be sweet.

---

### Post by cbiere on 2007-11-18
You can't use gtk-gnutella to download torrents, it's not a BitTorrent application. You can download .torrent files just like any other files with it, if that's what you meant. You should try [http://canyouseeme.org/](http://canyouseeme.org/) to see if your port forwarding works or not. If it doesn't work, maybe you have a local firewall blocking all incoming connections like Firestarter or Guarddog? If that's the case, you have to open the port there as well.

---

