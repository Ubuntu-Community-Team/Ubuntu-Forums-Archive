---
title: "After removing wireless PCI card for 1st time, no more wireless internet"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by hanzj on 2008-04-02
[SIZE=4]****[/SIZE]From January 2007 upto February 2008,  I was connecting to the internet using  a wired ethernet cable connection.
 But in the month of March 2008, I used a D-Link WDA-2320 RangeBooster G Desktop Adapter. This was how I installed it:
 
 Turned off desktop computer.
 Installed the D-Link PCI adapter to one of the open PCI slots.
 Turned on computer.
 Ubuntu automatically discovered the D-Link adapter.
 All I had to do was choose from the list of 4 wireless networks.
 
 
I don't remember whether I added the network-applet to the panel, or whether Ubuntu automatically did, but whichever the case, everytime I turned on the computer, I had a wireless internet connection.
 
Now, on March 31, Monday, I turned off the desktop computer and physically removed the D-Link PCI adapter. I then installed some other Wireless PCI Adapter. Let's call this "the no-name adapter". See attached pic.
 .
 When I turned on the computer, the network applet had an icon indicating that it couldn't find any internet connection. 
 
 So without an internet connection, I went to System | Help & Support to try to get my wireless internet connection working.
 
 I went to section 3.2 (Internet and Networks / Wireless Networking / Troubleshooting)
 
 
 "3.2.1 Check for Device Recogintion. 
Step one tells me to "Open Device Manager" which is found, it says, in "System > Administration Device Manager". Actually, I find it in Preferences / Hardware Information.
 
Step 2 tells me to check to see whether the hardware is recognized. So I look through the list and find an entry in "CK804 PCI Bridge".
 Here is some information:
 
 Marvell Technology Group Ltd.
 88w8335 [Libertas] 802.11b/g Wireless
 info.parent /org/freedesktop/Hal/devices/pci_10de_5c
 info.udi /org/freedesktop/Hal/devices/pci_11ab_1faa
 linux.hotplug_type 2 (0x2)
 linux.sysfs_path /sys/devices/pci0000:00/0000:00:09.0/0000:01:07.0
 pci.product_id (and pci.subsys_product_id) 8106 (0x1faa)
 pci.vendor_id (and pci.subys_vendor_id) 4523 (0x11ab)
 
 Since it is recognized, I go to Section 3.2.2, as per this step.
 
 
 Section 3.2.2 is "Check for Driver"
 Step 1 is "sudo lshw -C network" .
 When the Wireless PCI Card is installed, "sudo lshw -C network" gives:
 "
   *-network UNCLAIMED     
        description: Ethernet controller
        product: 88w8335 [Libertas] 802.11b/g Wireless
        vendor: Marvell Technology Group Ltd.
        physical id: 6
        bus info: pci@0000:01:06.0
        version: 03
        width: 32 bits
        clock: 66MHz
        capabilities: pm bus_master cap_list
        configuration: latency=32"
 
 (When wireless card is not installed, "sudo lshw -C network" gives a blank.)
 
 Step 2 says, "If there is a driver listed, then see "Section 3.2.3 -- Check Device is On."
 
 3.2.3. "Check Device is On."
Step 1 says "Many wireless network devices can be turned on or off. Check to see if the device is turned on by opening a Terminal and type the command: sudo lshw -C network."
 I don't know where in "sudo lshw -C network" it is shown that my device is on.
 
 
 Step 2 says "If it is turned on then see Section 3.2.4 
 
 3.2.4. Check for a connection to the router
 
 Step 1. Open a Terminal and type the command: iwconfig.
 When I do "iwconfig", I get
 
 lo        no wireless extensions.
 
 eth0      no wireless extensions.
 
 ---- end of paste of iwconfig-----
 
In March 2008 (when wireless internet was working, with DLink), I remember that ath0 was the "device" that my Ubuntu computer was using to get onto the wireless internet connection.
 But now, there's no mention of ath0 anywhere that I've looked.
 
 
 
Sections 3.2.4 (Check for a connection to the router), 3.2.5 (Check IP assignment), and 3.2.6 (Check DNS) are steps that I don't think I needed to check, since my problem is below those sections.
 
 
 -----------------
 
This no-name wireless PCI card that I tried to install on April 1st is brand new, but just to see whether it itself was the problem, I tried to re-install a D-Link Wireless PCI Network Card. This time, it doesn't work at all. 
In March 2008 (when I was able to get onto the internet wirelessly), Network Settings | "Connections tab" had "Wireless Connection" as one of the choices. But ever since I've removed the D-Link card on March 31st, "Wireless Connection" is no longer in the list in "Connections tab".
 
I'm writing this from a public computer, so if you gave me all the information/advice whithout having to have me respond too many times, that would be appreciated. If you do need to ask questions, please ask them all at once, so that I can give you all the answers all at once.
 Thank you for your understanding.

---

### Post by dstew on 2008-04-02
> I tried to re-install a D-Link Wireless PCI Network Card.Is this the exact same card you originally had in there?

To get your no-name card to work, you will probably need to use ndiswrapper with Gutsy. Here is an [Ubuntu document]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29") that tells you how.

---

### Post by hanzj on 2008-04-02
dstew,
yes. same exact dlink model.

re: using ndiswrapper
I thnk that getting that is a step too advanced of my problem. in other words, we have to have the computer get fixed to be usable with any wireless card first.


PLEASE HELP, PEOPLE!!!

---

### Post by dstew on 2008-04-03
> yes. same exact dlink modelSometimes the same model will use a different chipset. If you want to try to get the dlink card to work, we can do that. The first thing to do is enter the commands```
lspci
lspci -n
```and post the output to the forum. That will tell us exactly which chipset the card uses. Also, post the output of```
ifconfig
iwconfig
```with the d-link card in there.

---

### Post by hanzj on 2008-04-03
I got wireless internet working ON XUBUNTU 8.04 but not on UBUNTU 7.10. This is what I did.

1) Installed Xubuntu 8.04 Beta onto a separate partition.
2)Installed ndiswrapper (utils and common) from the Xubuntu CD
3) Checked the network applet and confirmed that wireless connection was selected and that roaming mode was on (it was)
4. Enjoyed.

---

### Post by hanzj on 2008-04-03
dstew, Looks like we posted at the same minute. 8-)

I prefer NOT to use the dlink card, but perhaps, for reference sake, I can post the outputs of what you're asking here soon.

---

### Post by dstew on 2008-04-03
Don't bother. Enjoy.

By the way, based on your description, it's the 8.04 native driver that is working. You installed ndiswrapper, but that is just the shell. If you don't install the Windows drivers into ndiswrapper, and if you don't install the filled ndiswrapper into your system, it is just sitting there, like any other inactive application. No need to un-install it, though.

---

### Post by hanzj on 2008-04-03
dstew, 
funny thing, I can get wireless internet working in Xubuntu 8.04 with ndiswrapper (common and utils) and with the Wireless Card's install CD's .inf and .sys files.
But doing the same thing in Ubuntu 7.10 doesn't work. 8-(

Wonder why.

---

### Post by dstew on 2008-04-03
Thanks for the clarification. It probably has to do with a newer version of both ndiswrapper and the kernel. If you look at a lot of ndiswrapper posts, you see that newer versions, often compiled from source obtained from the ndiswrapper site, work better than the versions that are packaged for Ubuntu. Newer is better for ndiswrapper, and for the kernel.

---

### Post by hanzj on 2008-04-03
dstew, thanks for your post. So you're saying that higher version of ubuntu is better than lower version. (8.04 > 7.10). Correct?

---

### Post by dstew on 2008-04-03
Only for some things. Generally, for hardware, newer is better. But not always.

---

