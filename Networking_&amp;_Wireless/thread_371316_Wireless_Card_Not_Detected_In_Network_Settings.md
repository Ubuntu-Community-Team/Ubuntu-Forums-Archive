---
title: "Wireless Card Not Detected In Network Settings"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by Joners on 2007-02-26
Hey,

Im new to ubuntu (well linux in general). Ive got an Acer Aspire 1520WLMI with Ubuntu 6.10 Install.

However after the worst installation problems ive ever come across, (just bad luck in this case) ive come to try and get my laptops inbuilt wireless card to work (IPN2220).

I understand  (on Ndiswrapper's wiki) that I have to use Ndiswrapper and the neti2220.inf driver. Think that I have that issue all sorted, Ndiswapper has loaded the driver and confirms that its there and that it can see the hardware. 

Although the network settings manager doesn't recognise my wireless card? It can see my wired connection and modem , but thats it.

When i open device manager I can see that my wireless card is there however it doesn't know what to do with it. Ive found the pci device Id and instructed Ndiswrapper to use the driver with the device and still no difference.

Just dont know how to get network manager to find my hardware!

Any thoughts would be appreciated.

Thanks!

---

### Post by Metaljaz on 2007-02-27
type the following command from the terminal window to make sure you are using the right driver:

lspci

Look for the network controller line, should look something like this.

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
(Broadcom is my wireless card and the chipset is BCM4306)

---

### Post by Joners on 2007-02-28
I did that and this is all that it comes up with!

00:0a.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

Any suggestions on what I should do from here?

Thanks!

---

### Post by Metaljaz on 2007-03-01
Read the below link. May provide a solution.

[http://www.ubuntuforums.org/showthread.php?t=34934&highlight=IPN+2220+Wireless+LAN+Adapter](http://www.ubuntuforums.org/showthread.php?t=34934&highlight=IPN+2220+Wireless+LAN+Adapter)

---

### Post by chris.olsen on 2007-03-01
> **Metaljaz said:**
> type the following command from the terminal window to make sure you are using the right driver:

lspci

Look for the network controller line, should look something like this.

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
(Broadcom is my wireless card and the chipset is BCM4306)

Sorry for the hijack, but to continue on from where was left off.  I am having the same problem.  Wierd thing is that on the install previous to the current the wireless was detected immediately after ubuntu install.  This time the card doesn't exist in the networking window.

So where does a person go from here to get things working?  BTW  I should mention that the wireless card is displayed on the lspci output

oops I misread the starters reply.  I thought they couldn't find it in the list.  So disregard my post

Thanks

---

