---
title: "simple nat problem (I think)"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by toby_1_kenobi on 2007-02-02
I've set up an edgy web server behind a modem/router and it's working find. I managed to get the modem to do a bit of port-forwarding for web services.

I set up some blog software (wordpress), it can be set up as a local blog, to be viewed from in the LAN so it sets the IP addess it uses for it's internal links to be the LAN IP address, or it can be set up to be live on the internet, in which case it uses the static WAN IP address.

The problem is when I set it to us the WAN then I can't access it from my home computers because my modem only does port forwarding for traffic coming from outside. When I try to browse to my static IP address from home I just get the modem interface page.

I think the solution would be to set up a simple address translation on my home workstation so that all apps think they are using the WAN IP to access the blog on my server but it secretly gets translated into the LAN IP. I think this is a NAT thing, but I can't work out how to do it.

Alternatively I might be able to change the settings on my modem to forward local traffic too, but then I don't know how I would reach the modem interface. It's a NetComm NB5Plus4 ADSL2+

Toby

---

### Post by toby_1_kenobi on 2007-02-02
perhaps no-one has answered me because I didn't really phase it as a question.

I need to translate one address to another. Can anyone help?

I tried this:
sudo ip route add nat w.x.y.z via a.b.c.d

and got this:
RTNETLINK answers: Invalid argument

I also tried this:
sudo iptables -A PREROUTING -t nat -d w.x.y.z -i eth0 -j DNAT --to-destination a.b.c.d

which doesn't give any error messages, but also doesn't have any effect that I can see (at least not the effect I'm looking for.

just a little bit of help would be much appreciated.

Toby

---

