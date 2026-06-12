---
title: "Upgrade to Hardy - Lost Network"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by Just4Fun20 on 2008-08-21
I've seen several posts on this but none seem to describe my problem.  

I was running on Ubuntu 6.06 LTS.  I decided to "upgrade" to 8.04 LTS, through the standard upgrade (not CD install) process.  For the most part everything worked fine.  Except now I can't get on the network.  

I have two Ethernet adapters.  An onboard SiS900 PCI Ethernet (10/100) and an installed NetGear GA 311 (Realtek RTL-8169).  

Typically I disable the onboard adapter (SiS 900).  

After the upgrade I lost all network connectivity.  

So first - with the onboard adapter disabled.  When I connect the cable the light comes on.  If I run the hardware diagnostics or lspci -v the adapter shows up (but fails).  It does not show up in network configuration nor to an ifconfig.

If I remove the GA 311 and enable the onboard adapter...  
Still no connectivity.  Yes, I get lights.  HW diag and lspci show the adapter.  ifconfig does not show eth0 but if I do an ifconfig eth0 it does show up.  ifup fails.  If I ping myself (or the loopback) it works but if I ping the network it shows as network not available.  

Running both adapters doesn't change the specifics for either adapter.  

Oh, this is not a dual boot machine.  I did the power off, unplug the cable and reset procedure, to fix the dual boot problem, just in case, but it didn't help.  

What tests or procedures should I run?  

TIA for any help.

---

