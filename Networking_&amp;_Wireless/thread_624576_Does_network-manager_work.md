---
title: "Does network-manager work??"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by gdkeene on 2007-11-27
I've been using Ubuntu for over a year now, but with Gutsy, network-manager seems to bring nothing but problems.  Whenever I change networks, it doesn't seem to get a DHCP address properly and if I set it up manually, the changes don't seem to take effect.

I've tried x@x:~$ sudo /etc/init.d/networking restart and I've tried re-booting - neither seem to work.
I've tried:

 x@x:~$ sudo ifdown eth0, but all I get is:

 ifdown: interface eth0 not configured

Usually after f*$&ing around for about an hour trying different settings in network-manager, it seems to work.  Then sometimes after it works for an hour or so, it just quits working.

I think I want to give up on network-manager and configure my network adapters manually (unless someone has a suggestion for network-manager).
Can someone give me the commands to configure an IP address both statically and with DHCP.  Also commands for setting default gateway, and DNS servers.

Thanks,

---

### Post by wieman01 on 2007-11-27
There are instructions for static IP in my WPA tutorial. Check it out, fairly straight-forward and also applicable to Ethernet networking. If you have problems, let me know. Remove NM entirely.

---

### Post by RawMustard on 2007-11-27
Yep it's a pretty crappy package, very unreliable.  Mine drops all the time and then I have to fight to get my networking back up again.  It also keeps forgetting my pass phrase for some reason.  Never had so much trouble with wirless before :(

---

### Post by dolphin_oracle on 2007-11-27
The first thing I do is uninstall network manager - it hates my rt61 wireless card.

---

