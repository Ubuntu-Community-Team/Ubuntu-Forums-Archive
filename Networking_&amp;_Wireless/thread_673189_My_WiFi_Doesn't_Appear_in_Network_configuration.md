---
title: "My WiFi Doesn't Appear in Network configuration"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by Dr. Faustus on 2008-01-20
So I woke up this morning and found my internet connection had stopped working.  I went to check the System>Administration>Network tab and the "Wireless Connection" portion of it had vanished.  At first I couldn't even get the wired connection working again, but after a few sites and turning the computer on and off a couple of times it started working.  The wireless connection, however, still doesn't show up.   

I checked <a [http://64.233.167.104/search?q=cache:8fFS1UCPxpcJ:https://wiki.ubuntu.com/WirelessTroubleshootingGuide+ubuntu+wireless+connection+doesn%27t+show+up&hl=en&ct=clnk&cd=1&gl=us](http://64.233.167.104/search?q=cache:8fFS1UCPxpcJ:https://wiki.ubuntu.com/WirelessTroubleshootingGuide+ubuntu+wireless+connection+doesn%27t+show+up&hl=en&ct=clnk&cd=1&gl=us) webpage and it said to run:

```
sudo pccardctl ident
```

I got no output, and it said that:

> If you get no output then the memory on the card cannot be read.


So where do I go from here?  Is the WiFi portion of my ethernet card toast or is it a software thing?

---

### Post by Dr. Faustus on 2008-01-20
Here is the info on my card from running "lshw"

```
 configuration: driver=pcieport-driver
           *-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0b:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=ipw3945 latency=0 module=ipw3945

```

"iwconfig" outputs the following:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

