---
title: "Dell Inspiron 1501 BCM4311 wireless not working"
date: 2015-02-07
forum: Networking &amp; Wireless
---

### Post by Ben_Z. on 2015-02-07
Hello, I'm new to Ubuntu. Actually I'm setting up a Ubermix 2.0 on an old laptop for my 10 year-old son to learn and use Linux.

The wired network was damaged, so I only have wireless working, which is BCM4311, and was working fine under Fedora 17 that I decide to replace with the much smaller Ubermix that fits better for a kid.

Here're the few output I got about the system:
user@system-:~$ uname -a
Linux system- 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

user@system-:~$ sudo lshw -C network
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff

user@system-:~$ sudo iwconfig
lo        no wireless extensions.
user@system-:~$ sudo modprobe b43
But the wireless doesn't lit up. 

Also, there is an entry in the blacklist.conf file:
# replaced by b43 and ssb.
blacklist bcm43xx

Since I have no wired network, I cannot run the apt-get update to get whatever. I wonder what package I should download and install.

Can anyone having encountered this before here share some insight?

---

### Post by Hadaka on 2015-02-07
Hi , Let's take a look at some stuff..
please COPY and paste one line at a time
then..
please do and post..
```
lspci -n |egrep '0200|0280' | awk '{print $3}'
rfkill list all | grep yes
lsmod | grep cfg80211
```

---

### Post by Ben_Z. on 2015-02-07
thanks so much for responding. I did read what you pointed out. Here're the output:

user@system-:~$ lspci -n | egrep '0200|0280' | awk '{print $3}'
14e4:4311

user@system-:~$ rfkill list all | grep yes
user@system-:~$

user@system-:~$ lsmod | grep cfg80211
user@system-:~$

I also tried to install the firmware-b43-installer. But it didn't work as it needs to access the site [www.lwfinger.com](www.lwfinger.com), which is impossible as I have no network at all on that laptop.

---

### Post by Bucky Ball on 2015-02-07
Welcome. See [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access"). But you are going to need access to a machine that is online to download and then transfer some things.

Generally, your card works 'out of the box' so odd it's not, but these things happen from time to time. Would be a very quick process getting it working if your ethernet cablel was connecting. ;)

---

### Post by Ben_Z. on 2015-02-08
Thank you Bucky Ball. it's very encouraging to read that.

Yes, my problem is my ethernet is not working, so have to download to usb key on another computer then install need packages. I have already installed the b43-fwcutter and other dependent packages. But firmware-b43-installer will not run to completion because it needs to access internet. Is there a work around?

As can be seen from my output from this command below , I don't even have "kernel driver in use. "

user@system-:~$ sudo lspci -vvnn | grep -A 9 Network
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=2 PME-


I have also installed bcmwl-kernel-source package. But modprobe bmcwl told me module not found.

---

### Post by Bucky Ball on 2015-02-08
Give us the output of:

```
sudo lshw -C network
```

... please.

---

### Post by Hadaka on 2015-02-08
Hi, no internet required..
read carefully,  load the b43 zip file first
[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)  
post #7

---

### Post by Ben_Z. on 2015-02-08
user@system-:~$ sudo lshw -C network
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff

---

### Post by Ben_Z. on 2015-02-08
thanks much Hadaka. 

I installed the models in your b43.zip and reboot the system. after pressing the wireless button, the lit came up!

So it's a crucial step. It is still not connecting, but it seems I'm no longer far away. just a quick report back.

Also lsmod now gives a different output:
user@system-:~$ lsmod | grep cfg80211
cfg80211  484040   2  b43,mac80211

---

### Post by Ben_Z. on 2015-02-08
it is working now. thanks so much all the help!

I added "modprobe b43" to the /etc/profile to ensure the card lit comes up at reboot.

---

### Post by chili555 on 2015-02-08
> **Ben_Z. said:**
> it is working now. thanks so much all the help!Please use thread tools at the top and give young Hadaka a well-deserved SOLVED! Thanks.

---

### Post by Ben_Z. on 2015-02-08
Strange, after reboot I always have to manually run the modprobe b43 to reenable the card.

So I added the command in the /etc/profile file. Now the lit comes up at every reboot.

many thanks.

---

### Post by Hadaka on 2015-02-08
Hi please do..
```
echo b43 | sudo tee -a /etc/modules
```
thanks.

---

