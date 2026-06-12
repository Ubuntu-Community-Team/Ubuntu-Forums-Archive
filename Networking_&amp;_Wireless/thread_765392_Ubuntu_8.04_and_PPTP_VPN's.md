---
title: "Ubuntu 8.04 and PPTP VPN's"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by SparkDog on 2008-04-24
Hello all!

It's been a while since I've had a Linux distro on one of my boxes. I think the last version I tried was Mandrake of some version. Anyway, I'm very pleased with 8.04 as a whole. I have been using 8.04 for a few months now almost exclusively, outside of booting into Windows to get some gaming time in. (Really wish game makers would start catering to Linux!!)

Sorry, I'm babbling. One of the major problems I've been having is with pptp routing using the built in gnome network manager. I have a hand full of clients that have Microsoft pptp servers setup. I can get the tunnel to connect but DNS resolution is completely screwed up. If I configure the tunnel to use remote DNS, it puts only remote DNS servers in resolv.conf which for some reason doesn't allow me to resolve on my network or the remote network. I can ping addresses on both networks, but cannot call them up by name. If I choose not to use remote DNS servers, my resolv.conf stays in tact and I can ping local machines by name and of course remote resolution does not work.

Does anyone know of a work around for this, or if it's being addressed already?

Note: I have tried manually adding DNS entries to the resolv.conf after connecting which doesn't seem to help. After the tunnel is connected, it seems to ignore any additional entries into the resolv.conf.

---

