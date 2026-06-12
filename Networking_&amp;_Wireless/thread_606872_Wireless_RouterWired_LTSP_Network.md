---
title: "Wireless Router/Wired LTSP Network"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by JoeGregory on 2007-11-08
Hi there,

I would like to set up an LTSP network using Ubuntu 7.10 with the following topology.

Server is connected to a Wireless router with its own DHCP. i.e. Server gets IP adress on eth1 from broadband router via wireless.

I have two options for the client network.

1. Clients are also connected to Wireless router (wired or wireless) 

2. Server and clients are connected to a separate switch (server via eth0)

I would like to ask if someone could give me some advice about which option to choose and what to watch out for in each case:)

Thanks in advance

Joe

---

### Post by SpiritIsReality on 2007-11-08
howdy
Could you look at this and see if it's any help to you ?
I know you want to connect the server to the router wireless. The rest of the
example could be the same.
[http://ubuntuforums.org/showthread.php?t=599166](http://ubuntuforums.org/showthread.php?t=599166)
trails

---

### Post by Lem on 2007-11-09
You'd be better off running the dhcp on the server with a static IP rather than the router. This makes the PXE setup pretty painless.

PXE booting over wireless is vaguely possible using a wireless bridge and some of the devices designed for xbox's and the like copy their mac address from the ethernet device they are plugged into. However, you'll probably get better mileage with hi-speed powerline adaptors if you do not want to implement a full cat5 infrastructure.

---

### Post by JoeGregory on 2007-11-09
> **Lem said:**
> You'd be better off running the dhcp on the server with a static IP rather than the router. This makes the PXE setup pretty painless.

PXE booting over wireless is vaguely possible using a wireless bridge and some of the devices designed for xbox's and the like copy their mac address from the ethernet device they are plugged into. However, you'll probably get better mileage with hi-speed powerline adaptors if you do not want to implement a full cat5 infrastructure.

But won't there be a DHCP clash i.e. Client receives IP addresses from both server and router? 

To rephrase the question, can I use the router for the LTSP network, without set-up in the router itself

Thanks

Joe

---

### Post by Lem on 2007-11-09
I have a similar testing set-up.

Either,

Use two NICS in your server. Plug the router into one with DHCP on.. and a switch with all your clients in the second. Use different IP ranges for each.. eg. 192.168.1.x for the router and 192.168.0.x for your LTSP network. Use a static IP (192.168.0.1 is default) for your LTSP NIC.
Your clients will grab a DHCP lease from the server, not your router.

Or,

Plug everything into the router, give your server a static IP and turn off the internal DHCP in your router. You will need to specify a static IP for your router box on the same subnet and the clients will grab their details from the server.

Hope that helps.

---

### Post by Lem on 2007-11-09
In the examples above, I've assumed you want to PXE boot your clients. You can't use your router to serve DHCP to the clients because the DHCP lease won't include the additional information such as where to download the kernel image from that is required by PXE.

---

### Post by JoeGregory on 2007-11-10
> **Lem said:**
> In the examples above, I've assumed you want to PXE boot your clients. You can't use your router to serve DHCP to the clients because the DHCP lease won't include the additional information such as where to download the kernel image from that is required by PXE.

I read somewhere that it is possible to program some routers so that they can provide the additional info. But I think the switch/separate IP network is the easiest way forward for now. 

I am actually not sure at present if PXE boot will work with the client I have, and I am not sure I really understand it anyway.

Thanks for all the advice.

---

### Post by Lem on 2007-11-10
Some enterprise level routers may be able to handle this, but I've not come across them.

PXE Booting:- If the BIOS of your client has an option for LAN boot or Network Boot then this should work. Most thin clients and mini-boards such as the via epias have this.

Essentially when you set-up LTSP, your DHCP server is configured to send some extra info with the DHCP packet. When your client boots, the boot rom sends out a DHCP request. Your server then responds with an IP and details of where to get the kernel image.
Your client then downloads the kernel image via TFTP from the server automatically, unpacks it and boots into it. No hard disk required.
The gives you the LDM login screen.. Enter the details of a user you've defined on your server and that's it!

---

### Post by LostIt6 on 2007-11-23
LTSP booting over wireless bridges works fine for me. I also have a WRT54G running OpenWRT. I have Edubuntu Server 7.10 (Gutsy) running in a virtual machine (when needed) that is an LTSP Server. I modified the settings in OpenWRT WebIF for DNSMASQ to tell clients to PXE boot from the Edubuntu VM. This way, even if the VM isn't running, my DHCP server (the WRT54G) is still serving up IPs on my network. Normally, the Edubuntu server is the DHCP server. My thin clients and my normal PCs are all on the same subnet.

---

