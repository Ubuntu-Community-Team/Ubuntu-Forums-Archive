---
title: "Multiple servers from a desktop"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by RichardCL on 2009-10-19
Hi Forum,

I'm now switched completely to Ubuntu with a Windows virtual box taking care of the few things I can't do in Ubuntu (MS Powerpoint, Garmin Navigation and Sony cellphone sync).

For my next beginners project, I'd like to start a mail server. I've researched a bit and asked some linux-freindly admins. It seems that Zimbra is a good starting point for what I need. I'd also like to start running the vtiger CMS.

I don't yet have a server hardware and would prefer to not invest until I've got the systems running.

Can I use virtualbox to run a separate install of Ubuntu containing Zimbra and a second virtual machine with VTiger? I need to be able to access these from the host machine (my desktop) as if they where separate machines on my desktop.

What Ubuntu should I be using? I guess 8.04 LTS for Zimbra but do I need a desktop or server install?

When I get around to buying a server hardware, can I just move virtual machine (Virtual box says that is possible but doesn't make any comment about network functionality).

I'll try to keep this forum post up to date with steps in case anyone wants to follow.


Richard

---

### Post by dominiquec on 2009-10-19
> Can I use virtualbox to run a separate install of Ubuntu containing Zimbra and a second virtual machine with VTiger? I need to be able to access these from the host machine (my desktop) as if they where separate machines on my desktop.

Yes, you can.  For VirtualBox guests, the default network setting is NAT; you'll want to change this to Bridged Adapter.

Good luck and have fun!

---

### Post by RichardCL on 2009-10-19
Dear Dominique,

Thanks for the inspiration. I've been looking at the networking possibilities and have found a tutorial [http://www.virtualbox.org/wiki/Advanced_Networking_Linux]("http://www.virtualbox.org/wiki/Advanced_Networking_Linux").

What I want is two applications VTiger and Zimbra. The VTiger installation guide suggests that it is run alone so I guess I need two virtual machines right?

The bridging tutorial tells me that only one device per bridge is possible. What do I need to take into account here? Can you suggest any tuition material?

I guess in the end that I can access the servers, even from the host machine, as if they where stand-alone in my network?

By the way, I'm also running the virtualbox with Windows Vista. The network is configured as NAT. I guess it isn't a problem to run NAT and Bridge together?

The host is connected via WLAN to the Fritzbox network. The Fritzbox takes care of the network configuration DCHP.

Thanks again



Richard

---

### Post by dominiquec on 2009-10-19
Yup, one Bridged Adapter = one real adapter.  You'll want to use Bridged Adapter if you want your guest accessible from the outside world.

However, you can create additional network devices (up to four in total) and as many internal networks as you want.  I teach at a university and this is what we do in our labs to simulate clients and servers.

NAT means outgoing access only; outside world can't initiate access to your system.

---

