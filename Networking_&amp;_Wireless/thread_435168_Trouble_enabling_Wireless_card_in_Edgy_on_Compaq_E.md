---
title: "Trouble enabling Wireless card in Edgy on Compaq Evo 610c"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by pilchinsky on 2007-05-06
Hi, 
I've been trying to get my Belkin F5D6020 wireless card to work, on Edgy, by following the instructions on [WirelessTroubleShooting ]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check")site.   But unfortunately I run into the problem of "*-network DISABLED" for my wireless card when I run "lshw" command.  

Unfortunately, I was unable to find a way to enable the card anywhere on the web.  In theory, and according to one site, Fn-F2 was supposed to do it, but it didn't (Fn-F2 has a wireless/radio logo on it).  

Does anyone out there know how to deal with this? 

Thanks, 
Alex

More info on my Belkin card as given by the "lshw" command
*-network DISABLED
          description: Wireless interface
          product: Wireless PCMCIA Card - F5D6020
          vendor: Belkin
          physical id: 0
          bus info: pci@03:00.0
          logical name: wlan0
          version: 20
          ...
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=rtl8180 multicast=yes wireless=802.11b
          resources: ioport:2800-28ff iomemory:46000000-460001ff irq:11

---

### Post by cbpxy on 2007-06-12
I've been having a similar problem with a Compaq Presario 1200US using a pcmcia card.  My lshw output is similar, except I have (and this is typing as I have no net access & no handy USB keychain):
```

 product: ACX 1000 22Mbps Wireless Interface
 vendor: Texas Instrument
 ...
 configuration: broadcast=yes driver=acx_pci ....
``` 
I've been hitting Fn-F2 and other keys, but that all seems so Windows-ish.  (And I also arrived here at the forums with this question through Section 3.2.5 of the [Wireless Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide").

Thanks in advance for any suggestions!

---

