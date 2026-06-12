---
title: "VMWare/Samba/Homeplug - disappointing performance"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by Heresiarch on 2007-11-14
Hi all, first post, and greetings to all you lovely people.

I've got a Gutsy server hidden under the stairs that runs a couple of virtual machines on VMWare Server - a web-facing Linux and a WinXP pro.  The host runs samba for file serving and a MythTV backend, not a lot else.  The guest OSes have a variety of software installed on them and small virtual disks - when they need to manipulate large amounts of data, they do it on the host via Samba.

Said machine is connected to my router with Homeplugs, as they're convenient, reliable and actually pretty fast - I typically get 40 meg throughput doing a simple copy, more than adequate for a file server.

However, there's a problem - I've recently noticed that if I start doing anything file-intensive on an SMB mount in the guest, it saturates the link to the router.  It appears that the VMWare bridged network is doing a round-trip to the router for every access by a guest to a host Samba share, and the powerline link just isn't up to it.  This is annoying as it means that if one of the guest machines is running a transcode (or whatever) then the server is no longer useful as the ping times rocket up to 4000ms.

I'm by no means an expert on IP but I'm wondering if it would be possible to set up the routing to prevent the Samba packets from host to guest leaving the box.  I could whack a spare interface in, if necessary, but I'm a bit stumped as to how you'd configure the setup - is this even possible?

Thanks for any help.

---

### Post by veloce on 2007-11-15
Yes, smb performance btw vm and host over bridged network can be appalling.  The answer is to set up host only networking for access between host and vm.  The host only virtual network runs **really** fast.

This can be done by giving each vm two network adapters.  

Alternatively, I have a virtual firewall (IPCop) that provides external access to the vms.  other vms only have host only networking.

---

### Post by Heresiarch on 2007-11-15
Thanks, that sounds like a very good shout - going to give it a whirl and see how it works out.

:)

---

### Post by Heresiarch on 2007-11-17
Just wanted to say thanks again to veloce, had time to set this up and it works like an absolute charm.

For anyone trawling the archives in search of the solution, this is what I did.

Find out what the virtual IP of your host is on the host-only network - on my machine it's vmnet1 

```

jim@monster:~$ ifconfig vmnet1
vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.150.1  Bcast:192.168.150.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

jim@monster:~$

```

Shut down the guest, add a host-only network interface to the hardware configuration via the console and reboot it.

Edit your guests hosts file and add a name for the host on this alternative IP.

Ensure that your smb shares in the guest mount using the new name.

I didn't have to tinker with my host's smb.conf, it listens on all interfaces by default.

The guests can now read and write host files very fast indeed, and it doesn't disrupt the host's access to the network - so in my case I can now run batch jobs at the same time as watching Myth recordings.  

Thanks again.

:)

---

