---
title: "How do I get a Static IP?"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by mindtrick on 2007-05-27
I need a Static IP to setup port forwarding. I have Ubuntu Feisty installed. 
How can I?
Thanks

---

### Post by scrooge_74 on 2007-05-27
YOu have to manually set ip up, from Admin>Network Change from using dhcp to manual IP

---

### Post by jonallport on 2007-05-27
Hi mindtrick,

two ways to do this:

1) Edit /etc/network/interfaces.  For the entry pertaining to the adaptor attaching to the network in question (e.g. eth0), change 'iface eth0 inet dhcp' to 'iface eth0 inet static', and below that line add the following:

address {static ip address}
netmask {subnet mask}
gateway {ip addr of router}

(as you're asking qustions about port forwarding I'll assume you understand IPv4 addressing)

2) Assign a static address in your DHCP config (on router/server/gateway)

(2) Has the advantage of giving you the same IP address if your dual-booting and avoiding the need to edit configuration of you attach you machine to someone else's network (like work or a friend's house, obviously, NOT staling the neighbours' WiFi !!!)

Hope that helps
J

---

### Post by jonallport on 2007-05-27
You're quite right, Scrooge_74.  I forget there's a GUI to do all this stuff, I usually spend my days on the server distro plugging away in the CLI.

J ;^)

---

