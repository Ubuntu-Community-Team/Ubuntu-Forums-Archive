---
title: "Network printer/scanner not visible ?"
date: 2023-01-28
forum: Networking &amp; Wireless
---

### Post by oygle on 2023-01-28
I have a network printer/scanner, a Brother MFC-J1300DW , hard wired to the LAN, off the router. In Kubuntu, CUPS can see it, I can print to it, scan from it, but it is not visible under the following apps:

*  KVM/QEMU running windows 10 as the guest
*  CrossOver trying to do a Windows printer driver installation.

I know this is a Windows problem, but is there anything on the Kubuntu networking side of things that could be compounding the issue ?  I even tried pressing the 'scan' button on the printer on Kubuntu but some message about the PC not found. Even knowing the IP address of the printer.

So, it can get 'out' with any tools on Kubuntu. Meaning laptop to printer, and even Kubuntu scan tools back from scanner to laptop. Works fine.

But as soon as I try and use the 'windows' component it seems to **NOT** be visible at all. So, in summary:

1. Is the problem with not being able to use the 'scan' button on the scanner (PC not found) a network problem or a firewall problem ?  If it is firewall, is it the router or the Kubuntu firewall (no rules active)
2. Is the problem with Crossover/Windows install networking or firewall ?

```
sudo ufw status verbose
```

> Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip

---

### Post by TheFu on 2023-01-28
Just throwing out an idea.  Are the VMs using a bridge or NAT?

---

### Post by oygle on 2023-01-29
> **TheFu said:**
> Are the VMs using a bridge or NAT?

NAT - Virtual Manager (KVM/QEMU)

As a somewhat quick test, I installed CrossOver, the Brother printer installation failed as it couldn't find the printer/scanner. Later installed WINE, same story.

As I had a spare Lenovo laptop with Win10, I installed the Brother printer software on that. Installation went well, it found the printer. Now have done a few test scans from the Lenovo/Win10 , and even OCR is looking good. Can even now press the button on the scanner and send the PDF back to the Lenovo/Win10. This is all working well, with no VM's. No changes to firewall or network.

The moral of the story is, if it is Windows software it will most likely install and work okay with Windows, but if the Windows is in any sort of guest/VM setup, don't be surprised if there are problems. Plus many hours spent.

---

### Post by TheFu on 2023-01-29
Uh ... VMs running under NAT cannot be reached by other systems on the network.  If they have a 2-way communication, it won't work.  The solution is to use bridged networking for the VM.  For VirtualBox, that's a checkbox in the VM setup (because MS-Windows doesn't support advanced network setups), but for KVM/QEMU, since it leverages the networking built-into the host OS, we need to create a bridge for the VM to use.  I don't have any clue how to accomplish that on any desktop.  

I use the server method which is easily accomplished by editing some config files on the host, then the VMs just need to attach to the named bridge inside the VM setup, fully reboot the VM, and from that point on, it will be bridged.  While you can use DHCP from the main LAN that way, for anything on my network that doesn't get relocated to other networks, like phones, tablets, laptops, I setup static IPs on each system and update my DNS so all my systems can reach it.  With a bridged network, mDNS/Avahi will work too (a few assumptions about firewalls, but it works, generally), then any device that supports avahi networking usually will announce itself, be seen by everyone else on the LAN and work.

I think the idea that Windows doesn't work under VMs, especially with network stuff, isn't correct.  The only thing I've noticed not working fantastic inside a VM is modern games where direct access to the GPU is demanded by the game.  Everything else works.

---

### Post by oygle on 2023-01-29
> **TheFu said:**
> Uh ... VMs running under NAT cannot be reached by other systems on the network.  If they have a 2-way communication, it won't work.  The solution is to use bridged networking for the VM.  For VirtualBox, that's a checkbox in the VM setup (because MS-Windows doesn't support advanced network setups), but for KVM/QEMU, since it leverages the networking built-into the host OS, we need to create a bridge for the VM to use.  I don't have any clue how to accomplish that on any desktop. 

Thanks for the heads up re needing bridged  for a Win10 guest; no wonder I couldn't access the printer as a Win10 guest with Virt manager. I don't intend to spend any time at all on that side of things. Trying to get a Win10 guest going to the point of being usable (resources) is a non event for me, as I can use the (very fast) Lenovo laptop with Win10 on it. Everthing to do with the printer works fine.

> **TheFu said:**
> I think the idea that Windows doesn't work under VMs, especially with network stuff, isn't correct.  The only thing I've noticed not working fantastic inside a VM is modern games where direct access to the GPU is demanded by the game.  Everything else works.

Yes, but the critical component is the host and the resources the host can deliver. We obviously have very different hosts. It's not worth the time any more for me. Thanks for your help though.

---

