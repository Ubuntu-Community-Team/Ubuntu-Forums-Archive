---
title: "[Need help] Windows Server Hyper-V host Ubuntu guest network down until restart"
date: 2024-03-21
forum: Networking &amp; Wireless
---

### Post by hundrambit2 on 2024-03-21
Hi.

I have a Windows Server 2022 host with Hyper-V installed. There are two Generation 2 VM's installed, Ubuntu 20.04 and 22.04 LTS servers.

Host machine has a network configuration that looks like this:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293516&stc=1[/IMG]

Basically it has a main static IP and 4 more additional IP's attached.

Hyper-V virtual switch is configured as following:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293517&stc=1[/IMG]

Then I have a Ubuntu 20.04 LTS server guest with following netplan configuration:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293518&stc=1[/IMG]

And following Hyper-V setup:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293519&stc=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293520&stc=1[/IMG]

This VM uses one of additional static IP's available to host.

Everything works as expected until there is a network disconnect for any reason, let it be maintenance work at hoster level, or a DDoS attack that brings network down for 1-2 minutes.

The actual problem is that Ubuntu guest machine remains offline until it is completely restarted. The network configuration does not try to reinitiate and become online again by itself. It simply stays offline forever.

There is a second virtual machine that has exactly the same problem, running Ubuntu server 22.04 LTS, using netplan network configuration exactly the same as previous server, but for next additional IP available.

There is one very important thing that I should mention. While Ubuntu guests stays forever offline after any disconnection reason, the host Windows Server always comes back online once connection is back, without need to restart it.

I need help understanding what is wrong, with either my Ubuntu server network configuration, or Hyper-V configuration.

I have changed two different hosters, but the problem remains.

Please help.

Regards.

---

### Post by volkswagner on 2024-03-22
Are you hiding part of the netplan cfg file?

Are there any other interfaces on the Ubuntu VM?

Why did you need to specify a mac address in the yml file?

Are there any relevant entries in the log/journald?

I'm curious why you've opted for setting the route rather than the default gateway
(I see gateway has been commented out in favor of route).

Although this is not part of the issue, I'm a fan of using NAT for the VMs and
a proper router/gateway in front, ESPECIALLY when Windows OSs are involved.

Having a public IP configured on a Windows host is not for the faint of heart.

You say you need to reboot, but have you tried "netplan apply" when networking
goes down?

How often do you get DDoS attacks? Perhaps you should use this as an indicator
that a proper firewall should be considered.

Is Hyper-V in a cluster?  I see you have settings enabled to move the VM
if a network issue is detected. Does the MV get migrated to another host
in the cluster when network issue occurs? If you only have one host, why
is this setting enabled?

---

### Post by hundrambit2 on 2024-03-23
Thank you for your post [volkswagner]("https://ubuntuforums.org/member.php?u=288711").

No, all you see of netplan configuration file, is all there is.

There is only localhost interface and eth0 on Ubuntu VM's, no others.

I specified MAC address in configuration because I had to test if it would do any difference, with same result, so it did not change anything.

Here is journal entries for "netplan apply" after network went down:

> Mar 21 11:31:38 corona-vm sudo[296994]:    corona : TTY=tty1 ; PWD=/home/corona ; USER=root ; COMMAND=/usr/sbin/netplan applyMar 21 11:31:38 corona-vm sudo[296994]: pam_unix(sudo:session): session opened for user root by corona(uid=0)
Mar 21 11:31:38 corona-vm systemd[1]: Reloading.
Mar 21 11:31:39 corona-vm systemd[1]: /lib/systemd/system/cloud-init-local.service:15: Unknown key name 'ConditionEnvironment' in section 'Unit', ignoring.
Mar 21 11:31:39 corona-vm systemd[1]: /lib/systemd/system/cloud-init.service:19: Unknown key name 'ConditionEnvironment' in section 'Unit', ignoring.
Mar 21 11:31:39 corona-vm systemd[1]: /lib/systemd/system/cloud-init.target:15: Unknown key name 'ConditionEnvironment' in section 'Unit', ignoring.
Mar 21 11:31:39 corona-vm systemd[1]: /lib/systemd/system/cloud-final.service:9: Unknown key name 'ConditionEnvironment' in section 'Unit', ignoring.
Mar 21 11:31:39 corona-vm systemd[1]: /lib/systemd/system/cloud-config.service:8: Unknown key name 'ConditionEnvironment' in section 'Unit', ignoring.
Mar 21 11:31:39 corona-vm systemd-networkd[693]: eth0: Re-configuring with /run/systemd/network/10-netplan-eth0.network
Mar 21 11:31:39 corona-vm systemd-timesyncd[661]: Network configuration changed, trying to establish connection.
Mar 21 11:31:39 corona-vm systemd-networkd[693]: eth0: IPv6 successfully enabled
Mar 21 11:31:39 corona-vm systemd-networkd[693]: eth0: Re-configuring with /run/systemd/network/10-netplan-eth0.network
Mar 21 11:31:39 corona-vm systemd[1]: Condition check resulted in OpenVSwitch configuration for cleanup being skipped.
Mar 21 11:31:39 corona-vm systemd-networkd[693]: eth0: IPv6 successfully enabled
Mar 21 11:31:39 corona-vm sudo[296994]: pam_unix(sudo:session): session closed for user root
Mar 21 11:31:42 corona-vm systemd-resolved[695]: Using degraded feature set (UDP) for DNS server 45.---.---.5.
Mar 21 11:31:48 corona-vm systemd-resolved[695]: Using degraded feature set (TCP) for DNS server 45.---.---.5.
Mar 21 11:31:48 corona-vm systemd-resolved[695]: Using degraded feature set (UDP) for DNS server 1.0.0.1.
Mar 21 11:31:52 corona-vm systemd-resolved[695]: Using degraded feature set (UDP) for DNS server 1.1.1.1.
Mar 21 11:31:55 corona-vm systemd-resolved[695]: Using degraded feature set (TCP) for DNS server 1.0.0.1.
Mar 21 11:31:58 corona-vm systemd-resolved[695]: Using degraded feature set (TCP) for DNS server 1.1.1.1.
Mar 21 11:31:58 corona-vm systemd-resolved[695]: Using degraded feature set (UDP) for DNS server 45.---.---.5.
Mar 21 11:32:04 corona-vm systemd-resolved[695]: Using degraded feature set (TCP) for DNS server 45.---.---.5.
Mar 21 11:32:04 corona-vm systemd-resolved[695]: Using degraded feature set (UDP) for DNS server 1.0.0.1.
Mar 21 11:32:04 corona-vm canonical-livepatch.canonical-livepatchd[743]: Client information is recent, not refreshing.
Mar 21 11:32:04 corona-vm canonical-livepatch.canonical-livepatchd[743]: Error in livepatch check state: check-failed.
Mar 21 11:32:07 corona-vm systemd-resolved[695]: Using degraded feature set (TCP) for DNS server 1.0.0.1.
Mar 21 11:32:07 corona-vm systemd-resolved[695]: Using degraded feature set (UDP) for DNS server 1.1.1.1.
Mar 21 11:32:09 corona-vm canonical-livepatch.canonical-livepatchd[743]: Failed to refresh patch information: livepatch check failed: POST request to "https://livepatch.canonical.com/v1/client/5a56..9608/updates" failed.
Mar 21 11:32:09 corona-vm canonical-livepatch.canonical-livepatchd[743]: Task "refresh" returned an error: livepatch check failed: POST request to "https://livepatch.canonical.com/v1/client/5a56..9608/updates" failed, retrying in 1m0s.
Mar 21 11:32:10 corona-vm systemd-resolved[695]: Using degraded feature set (TCP) for DNS server 1.1.1.1.
Mar 21 11:32:13 corona-vm systemd-resolved[695]: Using degraded feature set (UDP) for DNS server 45.---.---.5.
Mar 21 11:32:16 corona-vm systemd-resolved[695]: Using degraded feature set (UDP) for DNS server 1.0.0.1.
Mar 21 11:32:19 corona-vm systemd-resolved[695]: Using degraded feature set (TCP) for DNS server 45.---.---.5.
Mar 21 11:32:19 corona-vm systemd-resolved[695]: Using degraded feature set (UDP) for DNS server 1.1.1.1.
Mar 21 11:32:19 corona-vm systemd-resolved[695]: Using degraded feature set (TCP) for DNS server 1.0.0.1.
Mar 21 11:32:22 corona-vm systemd-resolved[695]: Using degraded feature set (TCP) for DNS server 1.1.1.1.

I did comment out "gateway4" option because it's now deprecated according to netplan manual. It should be specified in routes using "via" option instead. As you can see, the gateway address is specified there instead.

I was thinking of NAT aswell, but can I really NAT public IP's that my hoster statically assigns to me? NAT is more for local IP ranges like 192.168.x.x.

I do need public IP for host server aswell, it is running Windows services like game servers, that Linux can't run. So I do need all 3 servers being online, one host and two guests.

Hyper-V is not in a cluster, no. That checkbox is checked by default. I did try without it aswell. I had to try everything I could possibly test. There is only one host and no migrations are made.

Yesterday evening I remembered something I forgot to mention. The VM guests are cloned from my earlier setup - Windows Server 2019. Could there possibly be some kind of driver incompatibility? Linux kernel is usually responsible for network driver part, isn't it? But how much could 2019 vs 2022 virtual network adapter differ in features?

Regards.

---

### Post by volkswagner on 2024-03-25
You can NAT public or private IPs.

You'll need is setup a router/firewall with your public IP
subnet. Then with firewall rules and NAT you can forward
specific ports to each server based on the destination IP
address and forward it to the correct server.

Your system(s) can be much more secure by limiting the
exposure to each system to the Internet.


Rather than having a firewall on each server, you protect them
and only open/forward the necessary ports using a firewall.

You might try changing 'optional = true' to 
```

critical: true

```

Netplan [link]("https://manpages.ubuntu.com/manpages/jammy/man5/netplan.5.html")

The downside to enabling critical/true is the system can hang on boot waiting
for the link to work. If rebooting is currently not an issue, you should be fine, but
if you try rebooting without a valid connection, expect it to hang.

---

### Post by hundrambit2 on 2024-03-27
> [COLOR=#000000]The downside to enabling critical/true is the system can hang on boot waiting[/COLOR]
[COLOR=#000000]for the link to work. If rebooting is currently not an issue, you should be fine, but[/COLOR]
[COLOR=#000000]if you try rebooting without a valid connection, expect it to hang.[/COLOR]

Acutally yes! Before I added **[COLOR=#000000]optional=true[/COLOR]**[COLOR=#000000], the Ubuntu startup was hanging for several minutes before it was able to initialize network service and continue initializing Linux. I think that was related to IPv6 actually, but I'm yet not sure. That was pretty annoying so I added that option to avoid waiting. But, when network initialization took long time, I had exactly the same issue on network disconnects. So basically I have already tested that option, with same result.

As of NAT, it sounds complicated. Sure, Windows Server itself can act as a router assigning NAT information to each VM, but then my VMs can't actually use Internet freely, the NAT firewall has to be reconfigured each time public services need any type of change. I mostly refer to it as complicated because earlier I never had to do that on previous hoster where additional IPs were assigned using static MAC address for each.[/COLOR]

---

