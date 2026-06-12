---
title: "How I Fixed My Wireless Issues (Hoary)"
date: 2005-06-21
forum: Networking &amp; Wireless
---

### Post by bertimus on 2005-06-21
I have gotten so very close to getting wireless working nearly perfect with Hoary and a Linksys WMP54GS thru ndiswrapper.  But it's the most frustrating thing I've ever dealt with.

After far too much much hair-pulling, ifconfiging, iwconfiging, iwlisting, iweventing, GTKWifiing, Network control paneling, IRCing, forum scavenging and config file jockeying, I finally brought Hoary up on the network without the redundant and mind-bending task of ifuping and ifdowning myself to sleep every 30 minutes.   ](*,) 

While this solution may not be an option for everyone, it works great for me: I pulled the wireless card and hard-wired my box to the router with CAT5 and an Intel 10/100.

 \\:D/

---

### Post by smedstadc on 2005-06-21
Heh, wireless is so dodgy on linux that I think it's probably far less frustrating to buy a wireless bridge, and just hardwire into that wherever you are. At least you KNOW that ought to work out-of-the-box.

---

### Post by themonkman on 2005-07-10
bsoft, thanks for such a great utility!  Gnome (and Linux in general) has been waiting long enough for this.  I'm running Hoary on an older Dell Inspiron 4000, using a Netgear WG511 .11g card.  I've tried several other access point utilities before, like wifi-radar, with no success.  Your's is the first to work right out of the gate from .deb package.  Bravo!

The only thing I wondering if it's in your plans to add a signal strength indicator inside the applet as well.  If not, could you suggest a decent substitute applet or utility?

Anxiously waiting,

themonkman

---

### Post by themonkman on 2005-07-10
[QUOTE=bertimus]I have gotten so very close to getting wireless working nearly perfect with Hoary and a Linksys WMP54GS thru ndiswrapper.  But it's the most frustrating thing I've ever dealt with.

After far too much much hair-pulling, ifconfiging, iwconfiging, iwlisting, iweventing, GTKWifiing, Network control paneling, IRCing, forum scavenging and config file jockeying, I finally brought Hoary up on the network without the redundant and mind-bending task of ifuping and ifdowning myself to sleep every 30 minutes.   ](*,) 
.

 \\:D/[/QUOTE]

My advice would to ditch your card and grab one of the better supported one's under the Linux HCL.  3com makes cards that ship with Linux drivers, too.  I've been using a Netgear WG511 ( v.2 Taiwan model) now for about a year, and never had any real problems in it under kernel 2.6.  Ubuntu Hoary is the first distro that recognized my card and got it working out of the gate, whereas I didn't have to manually install the firmware and all that hotplug junk for it myself.  Very impressive, to say the least.

Linux has come a long way, and with added interest and community support (don't forget those god like dev's!) it'll one day be as easy to use as Windows, and as widely supported by hardware vendors.

---

