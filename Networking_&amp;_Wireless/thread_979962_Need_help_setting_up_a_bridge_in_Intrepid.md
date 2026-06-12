---
title: "Need help setting up a bridge in Intrepid"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by ltkermit on 2008-11-12
Hello all,

I need some help setting up my bridged connection in Intrepid (8.10).  I had everything working in Hardy (8.04) by customizing my "/etc/network/interfaces" but the nm-applet in Intrepid will not load with my customized interfaces.  This is a problem because I can't make my PPTP VPN connection work without the nm-applet.  So basically what I have to do is load my customized interfaces and reboot to use my bridge with Virtualbox 2.0.4, then revert to the default interfaces and reboot to use VPN via nm-applet.

The reason I need both is that I have many clients that I need VPN access to, and I have to have XP because the company I work for uses some software that is not compatible with WINE.

Is there a way to setup a temporary bridge without editing my interfaces?  My computer does have two NICs (eth0 in use by Ubuntu, eth1 not used) if that would help in anyway.

Any ideas?  If you need any additional information I will gladdy provide it.

Thanks a bunch! :)

---

### Post by kngunn on 2008-11-20
Get the VirtualBox user manual (pdf) from their website.  Look on page 79 for instructions on setting it up.

I've bridged mine successfully, but am still working out a few kinks, so I'm pointing you to their instructions since any I give you wouldn't be quite right.

---

### Post by ltkermit on 2008-12-16
Thanks for the info, I actually have the bridge working fine the issue I was having was in regard to the Network Manager applet and PPTP VPNs, which was actually fixed with the latest version of the applet, so after an update it is working correctly.

---

