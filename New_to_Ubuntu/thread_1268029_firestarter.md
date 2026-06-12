---
title: "firestarter"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by dzon65 on 2009-09-16
I'm trying to figure out bittornado.Downloadspeed is véééééééééry slow.According to bittornado it's listening.However,when I check with netstat no such port can be found.
So i thought checking firestarter to open gates.Only,there's a small problem,I can't configure firestarter anymore,there's no menu.I've uninstalled it for now.Anyone had this before?

---

### Post by katakaio on 2009-09-16
When you say that there's no menu, what do you see when opening Firestarter?

(BTW: I'll put in a shameless plug for [Deluge]("http://deluge-torrent.org/"), which is the best BitTorrent client I've seen on any platform. I waited a long time for a uTorrent-like client for Linux, and Deluge is it. Give it a spin and see if you like it and/or if it solves your problem. It's in the Ubuntu repos as **deluge**.)

---

### Post by dzon65 on 2009-09-16
Nothing, exept (since it's in my panel)starterproperties,remove from panel......When I click properties I only get the starterproperties window.Btw,I've read about that deluge.I'll most certainly will check it out.But for now....

---

### Post by 3rdalbum on 2009-09-16
By default, Ubuntu's firewall is not configured at all. So any incoming connections will be allowed, assuming there is anything listening on the port.

So, the ports were already open, and you probably closed them with Firestarter.

If you must use a personal firewall, *please* use gUFW as the configuration program.

If you already have a firewall built-in to your broadband modem/router (most do), then you don't need a personal firewall running on your computer, and incidentally you should check to see if the router's firewall is set up to do Bittorrent port forwarding to your computer.

---

### Post by dzon65 on 2009-09-16
No,slightly different.There was no firewall.It was during downloading (slow)I figured to have a look at a firewall to configure the ports.I installed it and saw there was no menu.(had it before so..)
But,as you proposed the other one,I'll check it out and I'll post the outcome.In the mean time,as someone suggested,I've uninstalled bittornado and using Deluge now.Strange enough,this torrentclient reaches downloadspeeds up to 60.Allready a lot better than the 2 on the other client.But still,I'm used to well...more.As for the router firewall forwarding,ubuntu's still véééry new to me so I'll have a better look at the threads already posted on this item.Thanks for the tips guys.

---

### Post by HarrisonNapper on 2009-09-16
There's probably a firewall on your router. Google "port forwarding" for more information or contact your ISP.

---

### Post by dzon65 on 2009-09-16
Will do,thanks.

---

### Post by lovinglinux on 2009-09-16
I suggest the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923). It has everything you need to setup Deluge properly and also a troubleshooting section to help determine the causes of low download speeds and how to test your ports.

---

### Post by dzon65 on 2009-09-17
Thanks people.I will have a look there.

---

