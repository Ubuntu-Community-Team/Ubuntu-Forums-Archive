---
title: "Need help share internet to pc with win98"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by NAKLOV on 2008-05-07
Hi,

At the moment im busy with DHCP and trying to configure my network to share the internet.

Im having a connection on my server pc.
Now I want the server to share the connection to the win98 pc, with a HUB between them

I have 2 NICs

eth0 connected to the internet
and
eth1

Could someone help me with this because I did all I can with the howTO's I found on the ubuntu forums.

---

### Post by bluefrog on 2008-05-07
in that case install firestarter (look in synaptic package manager) on your ubuntu box and launch it. The configuration wizard says it all it memory serves.

---

### Post by NAKLOV on 2008-05-07
ok,

I logged in as root
typed apt-get install firestarter
everything went ok

then when I want to start firestarter in the terminal I get the following error:

> (firestarter:12552): Gtk-WARNING **: cannot open display:

?

---

### Post by bluefrog on 2008-05-07
sorry, skipped the fact you are on a server without a GUI. Too bad

---

### Post by NAKLOV on 2008-05-07
Is it better when you're on a server with a GUI?

if so, how can I get on one

---

### Post by bluefrog on 2008-05-07
for those who have a problem with command line, it is better.

you could install ubuntu-desktop, so that you can also use your server as a desktop

---

### Post by NAKLOV on 2008-05-07
well nevermind,

I followed something on the Ubuntu forums
I actually managed to fix it
with the DHCP

but only got one problem, 
my client gets an IP address but I cant view websites in internet explorer.

edit:
got it working, change the dns and edited the dhcpd.conf with the new dns 
now I can ping form server to client and from client to server and other site's/ips
and I can view site's

Thanks for replying and trying to help me bluefrog! :D

---

