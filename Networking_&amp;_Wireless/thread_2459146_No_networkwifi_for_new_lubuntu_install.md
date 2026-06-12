---
title: "No network/wifi for new lubuntu install"
date: 2021-03-11
forum: Networking &amp; Wireless
---

### Post by porphyry52 on 2021-03-11
Installed lubuntu 20.04 on new asus l210. Installer announced no networking available so installed just from the usb.

Installed cleanly, but no internet. Icon in systray identifies as nm-tray, clicking it, left or right gets 3 item menu: Active Connections, Wifi Networks, Known Connections, all of which are dead

Network directory on Desktop shows an icon called Windows Network, clicking it gives error message, "Failed to retrieve share list from server: No such file or dirctory', followed by second error message 'The specified location is not mounted'

 sudo ip a gives
```
[sudo] password for q: 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
```


As wlan0 does not show does this mean lubuntu does not recognize the l210 network card?

sudo lshw -C network gives
```
  *-network UNCLAIMED
       description: Network controller
       product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:e000(size=256) memory:a1100000-a110ffff


```

---

### Post by TheFu on 2021-03-11
I'd ask if you've verified that the BIOS didn't disable the NIC first. Go into the bios and check that.  In fact, with Asus, you should be able to perform a BIOS upgrade over the internet from inside the BIOS, so I'd suggest trying that.  If it doesn't work then you know that the motherboard may have a bad NIC and you should get it replaced ASAP.

l210?  Are you sure it isn't an i210 or i211 both from Intel?
I know the I211 Gigabit Network is well supported and fast. I have one.  It uses the igb driver.
I know the I210 is supported and fast. I have 4. Neither of those NICs require any special effort to work.  The i210 is currently used on my router and not running Linux so I cannot tell you the driver it uses. Sorry.

I avoid wifi and realtek, so cannot help with that. Sorry.

---

### Post by praseodym on 2021-03-12
[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/rtl8821ce/rtl8821ce-dkms_5.5.2.1-0ubuntu4~20.04.3_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/rtl8821ce/rtl8821ce-dkms_5.5.2.1-0ubuntu4~20.04.3_all.deb)

Install the driver by double-clicking

---

### Post by porphyry52 on 2021-03-12
Thanks for your help, I have the download and will transfer it to the asus l210.

Oh boy, I think this will be a lengthy process, the download was missing one dependency, but that one was missing 3 more, and 2 of those missing 3 more.  Someday I am sure I'll reach the end of those dependencies, but right now I'm saying to myself, "who really needs the internet anyway?"

---

### Post by praseodym on 2021-03-13
What about adding the installation medium to the sources?! dkms and build-essential should be there

---

### Post by TheFu on 2021-03-13
> **porphyry52 said:**
> Thanks for your help, I have the download and will transfer it to the asus l210.

Oh boy, I think this will be a lengthy process, the download was missing one dependency, but that one was missing 3 more, and 2 of those missing 3 more.  Someday I am sure I'll reach the end of those dependencies, but right now I'm saying to myself, "who really needs the internet anyway?"

Does the system have wired ethernet at all?

---

### Post by porphyry52 on 2021-03-13
Doesn't seem to be.
```
/media/q/Lubuntu 20.04.2 LTS amd64 $ sudo find . -maxdepth 10 -iname '*dkms*'                                                                 
/media/q/Lubuntu 20.04.2 LTS amd64 $ sudo find . -maxdepth 20 -iname '*dkms*'                                                                 
/media/q/Lubuntu 20.04.2 LTS amd64 $   
```

Nothing for gcc either.

---

### Post by chili555 on 2021-03-13
I'm mystified. My machine reports:
```
chili@T440p:/media/chili/Ubuntu 20.04.2.0 LTS amd64$ sudo find . -maxdepth 10 -iname '*dkms*'   
[sudo] password for chili: 
./pool/main/d/dkms
./pool/main/d/dkms/dkms_2.8.1-5ubuntu1_all.deb
```The deb file should be installable.

---

### Post by porphyry52 on 2021-03-13
I notice your file is located in main/d/ on Ubuntu. Lubuntu doesn't have that directory. But thank you very much, now I know where to get it

---

### Post by guiverc on 2021-03-13
Yeah sorry @porphyry52 I just mounted my latest *focal* media and it's not there.

We (Lubuntu) don't include all *nvidia* & like closed-source drivers found on Ubuntu and *many other* flavors, which is why our ISO still fits on a 2GB thumb-drive.

---

### Post by porphyry52 on 2021-03-14
Turns out its only on the largest ubuntu iso , so I got that and installed ubuntu side by side with Lubuntu. But no help, its Software Installer gives the cryptic message "Kernel source or headers are required to compile these modules", whatever that may mean.
 All the online discussions of installing linux on this model asus referred to using a wifi dongle or even installing a different card in place of the Realtek, none mention a software solution. 
Mine arrive tomorrow. I have high hopes for the dongle.

---

### Post by praseodym on 2021-03-15
With that CD applied as source, run
```

sudo apt update
sudo apt install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) linux-generic
```
Now, try it again

---

### Post by porphyry52 on 2021-03-15
Both the dongle and the card arrived this am, and all I had to do was plug it in. Instant recognition and connection.

But I will also do the update and reinstall you recommend, I can use the usb port its plugged into for other purposes. Thank you for your help, and I'll let you know how it goes.

Immediately a problem. I'm not understanding what you mean by "...with that CD applied as source" do the 2 apt commands. man apt was not illuminating as to source. I inserted the 2.7gb ubuntu usb-stick, assuming this to be the source, and cd-ed to it in Terminal, and tried 'sudo apt update'. But of course it tries to make an internet connection.

---

### Post by porphyry52 on 2021-03-17
So I couldn't update the system without internet, and can't compile the driver because other source code it needs that I got on the ubuntu.iso is older and out of sync with the driver code. So I should have downloaded the unstable ubuntu.iso as it would be more recent than the driver.

 But I didn't. I plugged in the dongle, got connected and ran 'sudo apt update', and then 2-clicked the driver icon to install it.

No complaints about headers etc this time. What it said was "Cannot install from unsigned repo"

The moral of this story is: If your new computer needs a driver that is not already part of Linux, then a hardware solution always trumps attempting a software solution. The dongle ([TP-Link USB WiFi Adapter for PC(TL-WN725N)]("https://www.amazon.com/gp/product/B008IFXQFU/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1")) cost less than $8 and worked instantly. Its driver has long been a part of Linux.

---

