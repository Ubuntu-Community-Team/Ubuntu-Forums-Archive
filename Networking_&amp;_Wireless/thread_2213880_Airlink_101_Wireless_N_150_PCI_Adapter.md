---
title: "Airlink 101 Wireless N 150 PCI Adapter"
date: 2014-03-29
forum: Networking &amp; Wireless
---

### Post by x862 on 2014-03-29
i downloaded the ubuntu live cd to install ubuntu and replace windows vista but i ran into a snag this time. the live cd didn't pick up a wireless signal at (only ethernet) and i wasn't able to connect to my wireless home network. i'm a total linux and CLI noob... but i would appreciate any help to install the missing driver since to resolve this driver issue. i have used the CLI to update and upgrade packages but detecting drivers or enabling the wifi card is much more complicated for me.

my system specs: 

**Airlink 101 Wireless N 150 PCI Adapter, model #AWLH5085
dell optiplex 760 (small tower)
windows vista x64
250GB hdd sata
4GB ram
intel core 2 duo e8400 cpu

---

### Post by MikRose on 2014-03-29
You have to learn to check compatibility of hardware before you buy using Linux.  You have a Vista system, so your computer must be a little dated...which means maybe your drivers might not be capable of some things.  I have been using Linux from some of the earlier ones (Knoppix to learn) ... until 12.04LTS.  I like the long term support versions and just keep them updated until the next LTS comes out.  

When I look up your Airlink Adapter:  [http://airlink101.com/products/awlh5085.php](http://airlink101.com/products/awlh5085.php), it only lists Windows Systems.  

Linux has several compatibility lists you can Google to check if your Ubuntu version will work with different hardware devices, either out of the box or with a few tweaks.  I have learned how to do some tweaks, but out of the box is by far the easiest...it lets you start using the system faster and not get frustrated enough to return to Windows.  Here is one source: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I have found this D-Link wireless adapter will work on several older desktops and laptops with Ubuntu either as the only operating system or dual booted with Windows.  D-link DWA-140B2 Wireless N Wifi Network USB Adapter

I have Windows XP on a second computer so I can help other people with Windows problems, but since I've been using Linux I have no desire to upgrade to a newer Windows system...I will remain Linux Ubuntu "iintermediate-user".

---

### Post by Rob Sayer on 2014-03-29
Drivers work differently in linux.  In windows you have a folder with a gazillion .dll files.  Not in linux.  You don't just download them.

Post the output (within code tags from the menu) of:

```
sudo lshw -C network
```

... since usb adapters often have a different chipset in them, and they often change them.

And it'd really be a better idea if you put the output of the abov e command in a new thread in the Wireless & Networking section.

---

### Post by mörgæs on 2014-03-29
> **Rob Sayer said:**
> 
And it'd really be a better idea if you put the output of the abov e command in a new thread in the Wireless & Networking section.

No, we don't want multiposting.
If a thread needs moving (I have done already with this one) please use the 'report' button.

---

