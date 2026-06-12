---
title: "Edubuntu 7.10 Thin Client issue"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by Pärez on 2007-10-29
Hello everyone!

I have been trying to setup an edubuntu thin client environment in the school I'm working. "at the moment" :)

The computer I'm using as a server is: Dell Poweredge 2500, it has two 1 Gigabits processors, about 2 Gigabits of memory and two network cards. The cards are: Intel Corporation 82557/8/9 Ethernet pro 100 and 3Com 3c905B 100BaseTX [Cyclone].
I'm using Intel's card to connect to internet and 3Com to share ip's for thin clients through a router.

The thin client I'm using to test the environment has: 2,5 Gigahertz AMD processor and 1,024 memory. It has integrated NIC on it's motherboard, NIC is NVidias nForce Networking controller.  

I've installed Edubuntu 7.10 on the server and modified the dhcpd.conf file.
Then I run the thin client and get this message at boot:

          [17179570.788000] ACPI; Getting cpuindex for acpiid 0x1
          ipconfig; eth0: SIOCGIFINDEX: No such device
          ipconfig: no devices to configure
          /init: .: 1: Can't open /tmp/net-eth0.conf
          [17179571.112000] Kernel panic - not syncing: Attempted to kill init! 

I'm still quite an amateur with Ubuntu, I've worked with it only for a couple of months so please, make your explanation as simple as possible. Thanks!

---

### Post by daengbo on 2007-10-29
Is your client PXE booting? From the snippet, it appears that the client go an address and received the kernel correctly, but the kernel doesn't recognize the NIC. Perhaps the kernel doesn't have the correct driver built in.

I'm not that familiar with Edubuntu, but if it's like other Linux thin client platforms, the process looks like:
PXE boot / Ehterboot -> get an IP address and info about where to download the kernel -> download the kernel and partially boot, initializing the network hardware -> Mount the root filesystem via NFS and change (pivot) into the root filesystem -> continue to boot, starting a blank X session -> Connect the X session to your terminal server.

You appear to be getting stuck on step 3. The network interface isn't coming up.

Can you give some more information about the client you are using?

You might want to go over to [http://k12ltsp.org](http://k12ltsp.org) and ask this question on their mailing list, because almost everyone there is dealing with thin client setups, while very few on this forum are. You're more likely to get a knowledgable response from them.

Best of luck,

Daeng

---

