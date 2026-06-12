---
title: "iptables configuration for docker and native nginx to coexist on port 80/443"
date: 2016-05-28
forum: Networking &amp; Wireless
---

### Post by uwhkdb on 2016-05-28
Hi all,

I currently have a couple of third party pre-imaged docker containers running on my Ubuntu 16.04 LTS Linode listening to port 80 and 443 which iptables exposes them to the externallly routable IP on eth0. It works great standalone. However, I would like to have iptables not allow those containers to be exposed to my external routable IP on eth0 and instead have it be listening to the non-externally routable IP on eth0:1 so that I can run nginx natively to serve websites on port 80 and 443 of the eth0 IP address for any default port 80/443 requests without having to deal with docker and just reverse proxy any requests with the URL of share.abc.com to the externally non-routable ip on eth0:1 which docker containers are exposed to.

So what I want to ask is, am I even thinking about it in the most efficient/sensible way of doing what I want to do and if so, any guidance on how I might be able to do what I want to do would be very much appreciated!

Thank you so much for everyone's time!

Cheers,

-J

PS. I can't change the port mappings of these pre-imaged containers which is the root reason why I need to turn to iptables to do a less than standard config...

---

