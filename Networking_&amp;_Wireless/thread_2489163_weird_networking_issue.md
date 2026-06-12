---
title: "weird networking issue"
date: 2023-07-20
forum: Networking &amp; Wireless
---

### Post by kirksilson1 on 2023-07-20
My Ubuntu Server 22.04 VM is experiencing network connectivity issues. 
When checking the network configuration using ip addr show, it displays an MTU of 1500 and a state of DOWN with the group default glen set to 1000. The etc/netplan/00-installer-confg.yaml file shows the correct IP address, but pinging the IP address fails even after bringing the state up.

 rebooted several times, but no change.

when I check the VM settings,  the summary shows a MAC address for the IP address, but there is no connectivity. The issue started suddenly as it was working before.

I am at a loss at what to do next, other than wipe and reload, which I would hate to do.  any suggestions?

---

### Post by mwei19 on 2023-07-26
I'm not a networking pro but I do have a few suggestions: 
- Are you able to ping the gateway once the VM's network interface is UP? 
- Is the VM configured for the correct network interface/bridge. Is the host network interface that is being used by the VM UP with gateway pingable? 
- Is the routing configuration for the VM's network interface correct/enabled/auto? 
- Try removing the VM's network interface completely and then re-adding a the network interface and see if that changes anything.

---

### Post by TheFu on 2023-07-26
> **kirksilson1 said:**
> My Ubuntu Server 22.04 VM is experiencing network connectivity issues. 
When checking the network configuration using ip addr show, it displays an MTU of 1500 and a state of DOWN with the group default glen set to 1000. The etc/netplan/00-installer-confg.yaml file shows the correct IP address, but pinging the IP address fails even after bringing the state up.

 rebooted several times, but no change.

when I check the VM settings,  the summary shows a MAC address for the IP address, but there is no connectivity. The issue started suddenly as it was working before.

I am at a loss at what to do next, other than wipe and reload, which I would hate to do.  any suggestions?

Do you think that the MAC address in the IP should work?  It shouldn't.

If it worked previously and you didn't change anything, then the first thing I'd do is to validate that the netplan files haven't been altered by looking through some recent backup sets.  If this started last week, I'd check the backups for the last few weeks.  You do have versioned backups, right?  /etc/ is tiny, so there really isn't any good excuse for not having it backed up, at least weekly, if not daily.

Working before could mean yesterday or 1.3 yrs ago, if the VM hasn't been booted all this time. Please clarify.  Is this system running daily, 24/7/366?

Which hypervisor?
What sort of networking was configured by the hypervisor?  Perhaps NAT or host-only or bridged?
When posting, please include exactly which system is being discussed for each part.  Networking on the host or networking from inside the client?
Don't use DHCP when there are issues. Set static IPs where they need to be set.

It would help to see both *netplan* files - the one on the host and the one inside the client. When posting netplan files, you absolutely MUST use 'code tags' in these forums. This is because the whitespace in those YAML files is critical, so we must see it. If you don't, nobody can help.

Commands:
netplan generate  --debug
netplan apply   --debug

I don't really use MAC addresses in netplan. I do set a MAC in the hypervisor so that last part matches the last part of the IP address. Not really required, but it does help if there are network issues to have a clear mapping when 1 side isn't available.  

I use the specific named interface and IPs in netplan.  

There are different renderers, each with strengths and weaknesses.  I've been using *networkd* for some time with my more complex needs.   I avoid anything related to network-manager at any level. I was burned and decided I'd never use that pile of @#$@#S again, anywhere.  I use wicd or conman on some systems, just to avoid network-manager.  

YMMV.  

We need to see facts. Please.  Run the commands, post both the command AND the relevant output.  For example, I don't think qlen mean what you think it means.

---

