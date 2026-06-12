---
title: "Lost wireless after update"
date: 2016-09-26
forum: Networking &amp; Wireless
---

### Post by john526 on 2016-09-26
Firstly I am new to Ubuntu.

I have a Dell XPS 13 laptop with Ubuntu 14.04 LTS

After an automatic update and installation the wireless stopped working on my laptop.  I've had the laptop for a couple months and the wireless worked fine up to this point. I don't have a port for an Ethernet cable on the laptop and don't have a way of connecting to the internet on it without wireless.

I got this information from the command line:
:~$ nm-tool
NetworkManager Tool
State: disconnected

:~$ sudo lshw -C network
    *-network UNCLAIMED     
          description: Network controller
          product: Wireless 8260
          vendor: Intel Corporation
          physical id: 0
          bus info: pci@0000:3a:00.0
          version: 3a
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress cap_list
          configuration: latency=0
          resources: memory:dc200000-dc201fff

Any help would be very appreciated.

thanks,

John

---

### Post by john526 on 2016-09-26
Hi 

In case anyone has a similar problem, I resolved the issue with the help of dell support.  The fix was as follows:   

I shut down.  Then powered on and hit the F2 key which booted into BIOS.  I then disabled secure boot (it had been enabled), and hit "apply".  Then I exited.  

When it restarted, the wifi had returned.

The dell support thought a likely cause of the problem was interference between the dell drivers and the Ubuntu 14.04 updates.  He recommended that for a more robust fix I upgrade to Ubuntu 16.04

---

### Post by jeremy31 on 2016-09-26
The newest Ubuntu kernels enforce Secure Boot rules, so I wonder if something from Dell used linux backports to provide support for the 8260 as backports do not provide a signing key

---

