---
title: "XDMCP From WAN"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by usmcpug82 on 2007-02-15
Hey All:

    I'm having issues connecting to my Ubuntu server form my WAN. I can get XDMCP connection from my LAN but not my WAN. I get the black/dotted Xwin screen with the old-school 'X' cursor. I have my router forwarding the ports to the computer but still nothing. Anyone have suggestions/help? Thanks!!! Will also be posting this in networking forum but figured I'd try a wide area too :)

---

### Post by usmcpug82 on 2007-02-15
Hey All:

    I'm having issues connecting to my Ubuntu server form my WAN. I can get XDMCP connection from my LAN but not my WAN. I get the black/dotted Xwin screen with the old-school 'X' cursor. I have my router forwarding the ports to the computer but still nothing. Anyone have suggestions/help? Thanks!!!

---

### Post by dmizer on 2007-02-15
don't do this unless you REALLY know what you're doing.  i get well over 1000 probes for xdmcp at my firewall per day.  unless you've set it up to work like vpn over ssh tunneling or some sort, all that will be between your computer and the internet ... is a single password.  a password which can quickly be cracked by a simple script.

xdmcp is fine for lan interaction, but incredibly dangerous to open out to the wan.

is there some particular reason you need xdmcp open out to the wan?  perhaps there is a safer alternative for you?

---

### Post by usmcpug82 on 2007-02-15
Yea, so I can remotely administer it. I have no problem doing it thru SSH either, but even that's giving me a access denied even though both the server & router firewalls/NAT are open/forwarding. It's driving me nuts. I can get VNC but I can't SSH / VNC to get an XDMCP session.

---

