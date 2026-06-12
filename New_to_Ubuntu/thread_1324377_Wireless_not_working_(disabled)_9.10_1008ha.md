---
title: "Wireless not working (disabled) 9.10 1008ha"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by man4mac on 2009-11-12
Hello,

My wireless card on my 1008ha netbook appears to be disabled. I don't know how to enable it. I've read tons of docs on it and still can't seem to figure it out. It appears to be recognized by the OS, but in the menu bar there are no options for wifi it just says "wireless is disabled" When I run lshw I get this about the network card:

-network DISABLED
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlan0
                version: 01
                serial: 00:25:d3:37:0f:f8
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:18 memory:fbef0000-fbefffff


Can anyone help please? The ethernet does work so I do have an internet connection. I have installed the linux-backports as some forums suggested.

Thanks!

---

### Post by jdodson29 on 2009-11-15
I have ran into the same issues and read the same documentation and still can't find out to enable it.  I am dual booting between Ubuntu 9.10 and WinXP Media Center and the wireless is working as expected in the Windows environment.  

I have about a 6 year old Gateway laptop.

This is also my first time with Linux/Ubuntu so I'm green but am a .NET developer so I can get around on Windows a bit.

If anyone can help us get our wireless connected that would be great!  

Thanks.

---

### Post by bwzz on 2009-11-15
Try this:

Re-install: bcmwl-kernel-source and bcmwl-modaliases via Synaptic Package Manager
 
If you went to the Synaptic Package Manager, and the 
**bcmwl-kernel-source and bcmwl-modaliases **
was NOT installed, just install it.
Once installed and rebooted, the wireless should work

---

### Post by man4mac on 2009-11-15
Ok, so for all you noobs out there like me. Apparently several netbooks come with the wireless turned off in the bios from shipment. Microsoft skips this with some strange subroutine, and thats why it works in Windows. All you have to do is boot up into the bios and turn wifi on. I can't believe I missed this step somehow, but just in case there are any other idiots like me struggling with this...thats what you do.

---

### Post by mr clark25 on 2009-11-15
i have a question for you: why would you use a wireless Internet instead of Ethernet? 
Ethernet may be a little old, but it still beats wireless by far. i get 110-130kb/s with Ethernet....

can you beat that with wireless? i doubt it....

---

### Post by man4mac on 2009-11-15
Really? You are seriously asking why would you use wireless on netbook? I'm going to assume that was a joke.

---

### Post by pootan on 2009-11-15
> **mr clark25 said:**
> i have a question for you: why would you use a wireless Internet instead of Ethernet? 
Ethernet may be a little old, but it still beats wireless by far. i get 110-130kb/s with Ethernet....

can you beat that with wireless? i doubt it....

 My mothers notebook gets 350kbs a second with wireless no problem on a cheap prepaid plan.

---

### Post by jdodson29 on 2009-11-18
I tried bwzz's suggestion by installing **bcmwl-kernel-source and bcmwl-modaliases **and it didn't work for me.  Thanks for that help though.

Now, through trying other things, my wireless adapter isn't showing up in the Network tools.  If I run the command to show me my connections at the terminal the wireless controller shows up as Unclaimed.  That evidently means there are no drivers for it.  So now my issue is that I can't find the drivers online that I need for the Broadcom BCM4318 Airforce One 54g wireless card.

Can anyone tell me where they have had success downloading these drivers?

Thanks.

---

