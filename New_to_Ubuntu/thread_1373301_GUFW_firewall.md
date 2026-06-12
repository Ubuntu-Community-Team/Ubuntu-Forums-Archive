---
title: "GUFW firewall"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Dx11 on 2010-01-05
I just installed Kubuntu. I use GUFW for the firewall. When I set GUFW on Deny all incoming traffic I still can use all internet activities e.g torrents and nzb traffic. Is this normal? I checked the ufw status and it is enabled.

---

### Post by bodhi.zazen on 2010-01-05
Yes. 

Your firewall is iptables which in turn is a front end for netfilter.

At any rate, (g)ufw denies all NEW traffic, ESTABLISHED traffic is allowed.

If you wish to deny all incoming traffic, new, Established, and everything, you will need to use iptables or an alternate config tool.

The settings, as they are in GUFW are sufficient for the vast majority of Desktop users.

---

### Post by The Cog on 2010-01-05
This is normal. You are denying incoming connections from outside the PC. It is normal to allow outgoing connections from the PC (and responses to those connections). You will find that all your torrent connections are outgoing ones, where you connected to them rather than them to you. I have heard that this makes torrents go slow (doesn't seem to affect me that way), so you might want to make an exception for BitTorrent. Never heard of nzb.

---

### Post by Bartender on 2010-01-05
I just used gufw for the first time the other day.  Went into the "preconfigured" option and enabled all that stuff, and clicked the "Allow incoming traffic" radio button just cause it seemed like the thing to do.  Are you guys saying I can go back to the "Simple" setting and leave the "Deny incoming traffic" radio button clicked on??

---

### Post by bodhi.zazen on 2010-01-05
> **Bartender said:**
> I just used gufw for the first time the other day.  Went into the "preconfigured" option and enabled all that stuff, and clicked the "Allow incoming traffic" radio button just cause it seemed like the thing to do.  Are you guys saying I can go back to the "Simple" setting and leave the "Deny incoming traffic" radio button clicked on??

yes =)

---

