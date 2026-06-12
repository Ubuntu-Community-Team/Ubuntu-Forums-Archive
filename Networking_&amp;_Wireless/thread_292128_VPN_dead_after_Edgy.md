---
title: "VPN dead after Edgy"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by rjakiel73 on 2006-11-03
Well it looks like I am not the only one with this problem but I cannot fix it.  After upgrading one of my boxes to edgy PPTP VPN dies with the following message "Cannot determine ethernet address for proxy ARP".

Now I have read through the forums and tried the different fixes that have worked for some but to no avail.  Luckily I still have a couple of boxes running Dapper that aren't experiencing this problem so I can still connect via PPTP to different remote sites.  Was wondering if anyone has any late breaking info on why this is broke and a fix/patch to the offending bits?

---

### Post by rjakiel73 on 2006-11-03
Anyone?  There has to be something to fix this.

---

### Post by SoT on 2006-11-05
I have the same problem too...:( 

Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/1
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP

---

### Post by quadrant2 on 2006-11-06
I got the same problem too, this time in Kubuntu edgy.
I have tried a couple of the fixes posted and they dont work for me.
I installed knetworkmanager and this doesn't even run!

This is a serious problem for vpn users and nobody seems to know how to fix it, I regret moving on from Dapper, I had that set up working perfectly and doing everything I needed it to do.

Regards

Ben

---

### Post by alexpb on 2006-11-07
I had exactly the same problem: after upgrading from Dapper to Edgy I could not make ppptpconfig work any more. 

What I found is not a direct solution but rather an alternative: network-manager. 

You need to install the following packages (either using Synaptic, or by running "apt-get install"):

network-manager
network-manager-pptp
network-manager-gnome (if you want the gnome frontend)

You get a Network connection icon in the panel beside the clock.

One more thing. I am connecting to a Windows machine. I had to check the "Refuse EAP" in the connection options to make it work.

---

### Post by BrendanM on 2006-11-25
Has anyone come up with any real solutions to this issue yet? I can't use NetworkManger because I'm using an rt61 wireless card, and NM doesn't support it (or it doesn't support NM, not sure which). I've tried several of the "add a script here" type workarounds, but they don't seem to be doing it. Thanks.

---

### Post by MaskedMarauder on 2006-12-04
> **alexpb said:**
> ...
You need to install the following packages (either using Synaptic, or by running "apt-get install"):

network-manager
network-manager-pptp
network-manager-gnome (if you want the gnome frontend) ...

Where do you get network-manager-pptp?  I tried to install it and apt-get came back with: 
[INDENT]~# apt-get install network-manager-pptp
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package network-manager-pptp[/INDENT]

Do I need to add alternative sites to the apt repository configurations?

---

