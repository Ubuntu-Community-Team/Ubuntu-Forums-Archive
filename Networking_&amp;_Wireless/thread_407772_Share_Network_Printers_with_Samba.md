---
title: "Share Network Printers with Samba"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by Crashmaxx on 2007-04-12
I have an Ubuntu Dapper server setup at work and I use Samba to make it a file server, among other things. We have a bunch of printers that are connected directly to the network, network printers. But they don't show up anywhere in network places, so they are hard for clients to get installed.

I was wondering if there was a way to make a Samba share that would have the drivers for all these printers or even just links to their locations. And I would love for the server to find the printers, download a copy of their drivers, and place a link to them in a share. So that, if I client wants to install a printer, they would just browse to \\FileServer\Printers and see all the printers with names relating to their locations and function (ie, ColorLaserUpstairs1) and be able to just double click them to install them.

And when a new printer is put on the network, Samba would detect it and add a link to the printer share. And vise versa when it goes off the network.

Is there anyway to do something like this?

---

