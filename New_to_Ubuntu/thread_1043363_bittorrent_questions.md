---
title: "bittorrent questions"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by downloadfreak on 2009-01-18
Hello,

If I want to use bittorrent with linux what client can I use best? or is transmission enough?
And about ports how can I open them?/is it safe to open them?/will it affect other pcs I have?(since they have windows is it also safe?)
I hope anyone can answer my questions.

Best regards,
Downloadfreak

---

### Post by Ahadiel on 2009-01-18
1) I wouldn't know what client you'd use best.
2) Same as ^above^ but give Deluge a try.
3) Unless you are directly connected to the internet, ports are opened through your router's web interface. ([http://portforward.com/](http://portforward.com/))
4) Probably (just make sure they're obscure).
5) No, because the ports would be forwarded to one PC.

---

### Post by nhasian on 2009-01-18
transmission works fine.  its pretty basic but it gets the job done.  I also recommend deluge and Vuze but either is probably overkill for you.

yes opening ports on your computer for bt is safe, but it wont do you any good unless you forward those ports from your router to your computer.

this page should help you configure your router for port forwarding:

[http://portforward.com/](http://portforward.com/)

---

### Post by downloadfreak on 2009-01-18
But portforward.com is written for windows right? And my router isn't listed... (it's a router from my ISP)

---

### Post by fuser312 on 2009-01-18
go for vuze, type in synaptic.

---

### Post by mcduck on 2009-01-18
> **downloadfreak said:**
> Hello,

If I want to use bittorrent with linux what client can I use best? or is transmission enough?
And about ports how can I open them?/is it safe to open them?/will it affect other pcs I have?(since they have windows is it also safe?)
I hope anyone can answer my questions.

Best regards,
Downloadfreak

Transmission works just great for all basic torrent usage. And compared to the popular Azureus/Vuze, transmission is way lighter to run which makes it excellent choice if you don't need any special features. And even if you do need, I recommend trying Deluge and only touching Azureus/Vuze if nothing else works for you.

There's no need to open ports in Ubuntu unless you have closed them first. Since the default Ubuntu install is safe without a firewall no ports are closed. If you have set up a firewall, then you of course need to configure it to allow bittorrent traffic.

If you are using a router (and it's actually configured to route the traffic, not just bridge it) you'll probably need to forward the ports from your router. How it's done depends on your router (but not the OS you are running, you are configuring the router device itself). Doing this will not affect other computers if you do it correctly, since it will redirect traffic on those ports to the Ubuntu machine instead of opening them for _every_ machine.

---

