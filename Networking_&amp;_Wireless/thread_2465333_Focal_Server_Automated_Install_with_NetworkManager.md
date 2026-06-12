---
title: "Focal Server Automated Install with NetworkManager"
date: 2021-07-29
forum: Networking &amp; Wireless
---

### Post by reedacus25 on 2021-07-29
I'm hoping someone may be able to point me in the right direction here.

Goal:
[LIST]
[*]Ubuntu 20.04 Server installed using automated installer (subiquity)
[*]Networking with DHCP using dhcp-client-identifier
[/LIST]

I feel like I have been as far down the rabbit hole as I can go with systemd-networkd/netplan trying to get dhcp-client-identifier working.
dhclient is still installed by default, plop = gethostname() at the end of the client-identifier line, `dhclient -r ; dhclient`, the dhcp server sees the write identifier, hands out the correct address, reboot, dhclient isn't what comes up to request a lease, networkd is.
In theory, I could make a oneshot systemd unit for dhclient that runs at boot to release/renew, but this seems problematic and not ideal. 

So now I've been trying to use NetworkManager as the renderer in place of networkd.
I know with NetworkManager that these settings actually work, but now I can't get netplan to keep stepping on the settings I set.

First, just trying to change my autoinstaller iso to specify NetworkManager instead of networkd causes subiquity to crash immediately.
Tried adding the network-manager package to the manifest, same issue.

So if I use networkd to bootstrap, and then I try to come in after the fact and set everything for NetworkManager, it works, exactly like networkd.
I can run `# nmcli con modify $interface ipv4.dhcp-client-id $HOSTNAME`, it works, verified with `$ nmcli con show $interface | grep dhcp`
Then if I reboot or if I `netplan try/apply` the nmcli stuff gets whacked, and resets back to the null default.
Same thing if I do the interactive `# nmcli con edit $interface` and use `set ipv4.dhcp-client-id $HOSTNAME ; save ; quit` and then using the nmcli show and grep, its there, then netplan whacks it again.

So at this point I'm pretty much resigned to using the mac as my client identifier, request, save and place, reboot to release and renew, and it *should* come up with the correct address.
You just have to hope that nothing comes along and somehow futzes with the interface mac address like I've had happen with nvidia drivers somehow.

But the point remains, short of either:
[LIST]
[*]going back to ifupdown, which doesn't seem like a good idea long term.
[*]setting static ips, but now I don't get dns registration via dhcp lease/mapping and I'm no better than where I'm starting currently.
[*]munging dhclient to (hopefully) work on boot
[*]relying on mac addresses, which is pretty much my only real option at this point, which takes a lot more effort than pre-populating the static lease table with what I want ahead of time
[/LIST]

Is there really no clear path to victory here?

For all the good networkd/netplan does by making networking a simple yaml file, the fact that it obfuscates and deprecates lots of advanced functionality seems really, really short sighted, nevermind that its been since 17.10 that netplan

---

