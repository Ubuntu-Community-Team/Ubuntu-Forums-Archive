---
title: "Wireless on my 4 year old HP laptop"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by green_earth on 2007-06-19
Got Ubuntu up and running just over a week ago... time to get the wireless going!

Here is what I see when I run "lshw" in the terminal:

*-network:1 DISABLED
                description: Ethernet interface
                product: Prism 2.5 Wavelan chipset
                vendor: Intersil Corporation
                physical id: 6
                bus info: pci@02:06.0
                logical name: wlan0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=prism2_pci latency=64 multicast=yes

I believe this is my wireless card - it looks to me like it is recognizing it as a regular Ethernet connection? I'm totally new to Linux and don't know any commands or how to snoop around yet. I'm learning as I go and enjoying it. Any help on how I can get my wireless card working is appreciated.

---

### Post by benanzo on 2007-06-19
What version of Ubuntu are you using?

All the Prism wireless chipsets have good support in Linux.

To see if your wireless card is working properly open a terminal and do:
```
sudo iwconfig | less
```
to find your wireless interface.
Press Q to exit.

Then do:
```
sudo iwlist wlan0 scan
```
where *wlan0* is your wireless interface.

---

### Post by green_earth on 2007-06-19
Thanks for the reply - I'm using Ubuntu 7.04 - the Feisty Fawn. When I type in "sudo iwconfig | less" here is what is returned:
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

Yet I have a wireless card of course - I know that when I run lshw it says:
> 
*-network:1 DISABLED

When I had windowsxp on the laptop there is a small blue led button on the left side of the laptop that would switch the wireless on and off. I always left it on. Now that I've got Ubuntu, I cannot use the button and it will not light up. Could that have something to do with why it is disabled?

---

