---
title: "Alright, I am so close to giving up here on my C712NR and this broadcom internal wifi"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by brianslater on 2008-05-07
I am beginning to this it is not possible. I have followed 5-6 guides on how to install my broadcom internet wifi with my compaq 712NR with Hardy Heron. I was wondering if someone can walk me through this step by step because I am tired of booting this thing into horrible horrible vista. 

Can someone please help me with this!!!

---

### Post by GrouchoMarx on 2008-05-08
Have you given the following method a shot?

[Broadcom Wireless Setup for Hardy (Step by step)]("http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+b43")

Step 2 involves finding the driver file for your specific card. You can find driver files for various wireless cards on the [Ndiswrapper site]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/"). If you're not sure which is the appropriate driver file, then you can use your card's PCI-id to find the appropriate driver file. To find your wireless card's PCI-id enter the following into the terminal:
```
sudo lshw -C network
```
This should output something something like:
> ...
*-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:**03:00.0**
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
...

The PCI address of your wireless card is listed under "bus info" (in bold). Then match the PCI address to the output of the following command:
```
lspci -n
```
The output should look something like:
> ...
03:00.0 0280: **14e4:4320 (rev 02)**
...
The 8 digit string in bold + (rev #) is the PCI-id of your particular card. Using the PCI-id you can find the appropriate driver file on the [Ndiswrapper site]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/"). Note that the search function doesn't work so you have to go "B" for Broadcom, or your particular manufacturer, and then you can match the specific PCI-id #.

Once you have your driver file, you can continue with the other steps, substituting your driver for "bcmwl5.inf" in the howto. Although step 3 is a little bit redundant, you can do it just to be safe. The key steps are 5, 6, and 7, which unload the native wireless modules at startup (for some reason they load even if blacklisted, necessitating the init script).

---

### Post by Pablo12CR on 2008-05-08
I hope this one works, it will be my last try for Hardy to work :(

---

### Post by Pablo12CR on 2008-05-09
Oh Thanks, It really works!!! :guitar:

---

