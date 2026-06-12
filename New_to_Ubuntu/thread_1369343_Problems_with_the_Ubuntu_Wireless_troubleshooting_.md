---
title: "Problems with the Ubuntu Wireless troubleshooting protocol"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Drjim on 2009-12-31
Hello folks,

I hope you all had a great holiday. 

I'm still trying to get my Samsung netbook to work with my wireless system. I've been going through the online troubleshooting guide and came to a point where I got stuck.

I opened a terminal and entered: "sudo lshw -C network"

I got information telling me that I have Realtech (Realtek?) network hardware for which wireless is "unclaimed".

According to the troubleshooting guide, this means that there is no driver loaded, as least in Ubuntu (wireless works using windows 7). I'm supposed to locate a windows driver with the .inf suffix and install the ndisgtk package. There is a hyper link on installing the ndisgtk package that yields the error message "firefox doesn't know how to open this address because the protocol isn't associated with any program". 

I tried to find the indicated package using synaptek with my netbook connected via ethernet (wired connection works in Ubuntu) but got nowhere. I'm also a a bit of a loss as to how to find the windows driver ending in .inf.

Is there a chance that there's a Ubuntu driver I can download that will work? Failing that, can someone give me some tips on finding ndisgtk or the windows driver?

Thanks,

Jim

---

### Post by bkratz on 2009-12-31
> **Drjim said:**
> Hello folks,

I hope you all had a great holiday. 

I'm still trying to get my Samsung netbook to work with my wireless system. I've been going through the online troubleshooting guide and came to a point where I got stuck.

I opened a terminal and entered: "sudo lshw -C network"

I got information telling me that I have Realtech (Realtek?) network hardware for which wireless is "unclaimed".

According to the troubleshooting guide, this means that there is no driver loaded, as least in Ubuntu (wireless works using windows 7). I'm supposed to locate a windows driver with the .inf suffix and install the ndisgtk package. There is a hyper link on installing the ndisgtk package that yields the error message "firefox doesn't know how to open this address because the protocol isn't associated with any program". 

I tried to find the indicated package using synaptek with my netbook connected via ethernet (wired connection works in Ubuntu) but got nowhere. I'm also a a bit of a loss as to how to find the windows driver ending in .inf.

Is there a chance that there's a Ubuntu driver I can download that will work? Failing that, can someone give me some tips on finding ndisgtk or the windows driver?

Thanks,

Jim

I went to Synaptic and just typed in ndis in search by the time I got that far it found all the ndiswrapper packages.  What repositories do you have ticked? Try a reload. By the way ndisgtk is on the live CD also. Anyway, do you need to use ndiswrapper? What did it show your wireless card to be?

---

### Post by Drjim on 2010-01-01
> **bkratz said:**
> I went to Synaptic and just typed in ndis in search by the time I got that far it found all the ndiswrapper packages.  What repositories do you have ticked? Try a reload. By the way ndisgtk is on the live CD also. Anyway, do you need to use ndiswrapper? What did it show your wireless card to be?

If I'm doing this right, here is the info on my card when I typed in: sudo lshw -C network

*- network UNCLAIMED
description: Realtek Semiconductor Co., Ltd
product: ditto above
physical id: 0
bus info: pci@0000:02:00.0
version: 01
width: 32 bits
clock: 33MHZ
capabilities: pm nsi pciexpress bus_master cap_list
configuration: latency=0
resources: ioport:2000(size=256) memory:f0100000-f0100000-f0103fff

then there's some info on my ethernet connection, which works fine.

Does this tell you what you need to know about my wireless card?


Thanks for the help, 


Jim

Jim

---

### Post by anewguy on 2010-01-01
It would also help if you'd do the following:

lspci

find the line(s) for your wireless and copy/paste in a reply back here.  That should hopefully show us the chipset so we might be able to help you more.

As far as Windows drivers go, do you have a driver cd for the card?  Can you download the drivers from the manufacturers site?

Dave :)

---

### Post by Drjim on 2010-01-03
> **anewguy said:**
> It would also help if you'd do the following:

lspci

find the line(s) for your wireless and copy/paste in a reply back here.  That should hopefully show us the chipset so we might be able to help you more.

As far as Windows drivers go, do you have a driver cd for the card?  Can you download the drivers from the manufacturers site?

Dave :)

I hope someone can help. I've spent hours on the wireless troubleshooting protocol, got ndiswrapper installed, found the .inf file for my driver, installed in and it still won't work. I suspect this is because, even though the download stated it was for a 32 bit system, all I found were drivers designated 64, and 86. the 64 wouldn't install with with Windows Wireless Drivers app (ndiswarpper), the 86 did but there was still no recognition of my hardware. 

I entered lspci at a terminal as suggested. I don't know how to cut and paste from a terminal but I hope the important lines are:
Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)

and maybe:
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL810E PCI Express fast ethernet controller (rev 02)

I really hope someone can help because, as of now, Ubuntu is fairly useless for internet access which is kind of ironic since that's one of the major reasons I wanted to use it. 

Again, wireless works in windows and ethernet works in both OS

Thanks,

Jim

---

