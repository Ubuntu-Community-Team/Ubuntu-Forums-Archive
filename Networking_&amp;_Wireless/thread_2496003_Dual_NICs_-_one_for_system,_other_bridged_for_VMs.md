---
title: "Dual NICs - one for system, other bridged for VMs"
date: 2024-03-11
forum: Networking &amp; Wireless
---

### Post by townleyc on 2024-03-11
[COLOR=#000000][FONT=Verdana]I have Ubuntu 22.04LTS on a Intel NUC12, running a few VMS under KVM/QEMU. I have set up a bridged NIC onto a USB NIC, and want to restrict that to the VMs, with the server only using the main NIC.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]
The VMs work fine with the bridged NIC, but how can I prevent the host from using that NIC, and just use the main NIC?

Any thoughts?

Chris[/FONT][/COLOR]

---

### Post by TheFu on 2024-03-11
You need to enable IOMMU and PCIe passthru for the NIC to be used exclusively by a specific VM. Then the hostOS won't use it.  I don't know if a NUC supports IOMMU, but it is required.  

Also, I don't know how to setup a single NIC that cannot be seen by the host, but can be used for bridges by all VMs.  You can, of course, just have the hostOS ignore the second NIC, don't give it any IPs and only use the other one without any bridge for the HostOS.  However, I don't know how data would get to-from the VMs without the bridge having some host network configuration.  Perhaps it will work. IDK.

---

### Post by volkswagner on 2024-03-11
Do you plan on providing internet to the VM’s?

Please provide your goals and network topology (will the NUC be connected to multiple networks, if you are providing Internet to the VM’s is via your current bridge, how will you connect to VMs, is your bridge NAT’d).

---

### Post by townleyc on 2024-03-12
Both NICs are connected to a single network, and the VMs can (and do) connect to the internet, using ISP router for SMTP and NAT. That all works - my sole aim here is to prevent the host OS from using the bridged connection

---

### Post by TheFu on 2024-03-12
> **townleyc said:**
> Both NICs are connected to a single network, and the VMs can (and do) connect to the internet, using ISP router for SMTP and NAT. That all works - my sole aim here is to prevent the host OS from using the bridged connection

Have you tried using a lower metric for the IPs between the host NIC (50) and the bridged NIC (100)?  If routing isn't available on the system and the VMs connectivity still works, then you know you've achieved the goal.

---

### Post by townleyc on 2024-03-12
I had thought of that, but if it sees  query on the bridged NOC, it will still respond. That is what I am trying to stop

---

### Post by volkswagner on 2024-03-12
> **volkswagner said:**
> 

... how will you connect to VMs, is your bridge NAT’d).

I'd love to help but you've missed some questions.

---

### Post by TheFu on 2024-03-12
> **townleyc said:**
> I had thought of that, but if it sees  query on the bridged NOC, it will still respond. That is what I am trying to stop

The bridge doesn't need an IP on the host.

If you don't want the host to see it, then PCIe passthru via IOMMU and dedicated hardware is the only choice I can see.

---

### Post by townleyc on 2024-03-13
> **volkswagner said:**
> I'd love to help but you've missed some questions.
The bridged adaptor is not NATed on the host, just on the router.

---

### Post by townleyc on 2024-03-13
> **TheFu said:**
> The bridge doesn't need an IP on the host.

If you don't want the host to see it, then PCIe passthru via IOMMU and dedicated hardware is the only choice I can see.

The host is capable of VT-x and VT-d, but I need to enable VT-d in BIOS.

Problem is that I know diddly squat about IOMMU. Need to investigate further

---

### Post by TheFu on 2024-03-13
> **townleyc said:**
> The host is capable of VT-x and VT-d, but I need to enable VT-d in BIOS.

Problem is that I know diddly squat about IOMMU. Need to investigate further

VT-d is for the CPU.
IOMMU is for the motherboard.
Both are needed for PCI passthru.

---

### Post by townleyc on 2024-03-13
> **TheFu said:**
> VT-d is for the CPU.
IOMMU is for the motherboard.
Both are needed for PCI passthru.

IOMMU is the generic name. AMD use VT, Intel VT-d 
My CPU is Intel

---

### Post by volkswagner on 2024-03-14
Since your VMs appear on your Local LAN, you should be able to do as
@TheFu suggested (leave the Bridge interface unconfigured/no IP address).

I've never set up an interface without an IP, so I can't provide instructions.
If it's not easy to set it up as unconfigured, I'd simply assign it a static IP (outside
of your LAN) with a /32 and no gateway. This would allow the second NIC to be
used exclusively for the host's network. 

Your VM bridge simply needs to act as a "dumb" layer 2 switch.

You can have your second NIC as DHCP or Static on your LAN with configured
gateway, DNS, etc.

---

### Post by townleyc on 2024-03-14
> **volkswagner said:**
> Since your VMs appear on your Local LAN, you should be able to do as
@TheFu suggested (leave the Bridge interface unconfigured/no IP address).

I've never set up an interface without an IP, so I can't provide instructions.
If it's not easy to set it up as unconfigured, I'd simply assign it a static IP (outside
of your LAN) with a /32 and no gateway. This would allow the second NIC to be
used exclusively for the host's network. 

Your VM bridge simply needs to act as a "dumb" layer 2 switch.

You can have your second NIC as DHCP or Static on your LAN with configured
gateway, DNS, etc.

Thanks, I was considering trying that, but at the moment I don't want two of the VMs offline, so that will have to wait a bit.

I will update here when I manage to work out how, and then implement

Thanks

Chris

---

### Post by TheFu on 2024-03-14
So, the idea in post #2 above hasn't been tried yet?
> You can, of course, just have the hostOS ignore the second NIC, don't give it any IPs and only use the other one without any bridge for the HostOS. 

I've done this by accident a few times.

---

### Post by townleyc on 2024-03-15
> **TheFu said:**
> So, the idea in post #2 above hasn't been tried yet?


I've done this by accident a few times.

Basically the same thing. Just not had the chance to work out how - too much going on, and not enough time. I will get around to it in die course

---

