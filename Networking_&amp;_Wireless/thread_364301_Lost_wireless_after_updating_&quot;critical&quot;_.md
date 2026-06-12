---
title: "Lost wireless after updating &quot;critical&quot; packages - Edgy Eft 6.10"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by natern on 2007-02-18
Okay, so I had fully working wireless, performed the critical system updates, and now it isn't working.
My laptop is a HP Pavillion ze5385, with a built-in 802.11b wireless card. It uses a prism2 driver, and other than that, I know very little about the wireless card. The card DOES show up in the gnome network manager, but it is displayed as a wired connection, not wireless. Below is the output of a few various network information commands.

```
 sudo lshw -C network
  *-network:0 **DISABLED **   
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5 link=no multicast=yes
       resources: iomemory:d000a000-d000afff irq:10
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation

```

```
sudo lsmod | grep prism
prism2_pci             74752  0 

```

```
sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr** 00:00:00:00:00:00**  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:dc928000-dc929000 


```

```
sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device

```

```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.
```

Any help with this would be great because I'd much rather not have to reinstall ubuntu and disable system updates. Thanks!
Nathan

---

### Post by gradedcheese on 2007-02-18
boot into your previous kernel (press ESC to get the grub menu at bootup, right after the BIOS screen) and see if it works (it probably will).  Use that kernel for now...

---

### Post by fpurdue on 2007-02-18
I had a similar thing happen - wireless worked fine up to about 2 hrs ago, did a bunch of updates and it doesn't show up any more.  The card no longer shows up under any of the network managers - it used to be eth1

```
 *-network               
       description: Ethernet interface
       product: NetXtreme BCM5753M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@08:00.0
       logical name: eth0
       version: 21
       serial: 00:16:d4:46:ce:33
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 ip=192.168.26.111 multicast=yes
       resources: iomemory:e4100000-e410ffff irq:90
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945
       resources: iomemory:e4000000-e4000fff irq:185

```

```

ipw3945               124576  1 
ieee80211              35272  1 ipw3945

```

I do however see this in the syslog:

```

Feb 18 04:44:42 chigau kernel: [17179594.840000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Feb 18 04:44:42 chigau kernel: [17179595.228000] tg3: eth0: Link is up at 100 Mbps, full duplex.
Feb 18 04:44:42 chigau kernel: [17179595.228000] tg3: eth0: Flow control is off for TX and off for RX.
Feb 18 04:44:42 chigau kernel: [17179596.708000] ipw3945: Radio Frequency Kill Switch is On:
Feb 18 04:44:42 chigau kernel: [17179596.708000] Kill switch must be turned off for wireless networking to work.

```

---

### Post by gradedcheese on 2007-02-18
like I said, boot into your previous kernel.  that should take care of it.  If you want to use the new kernel (you do **not** have to!), then you'll need to reinstall your ndiswrapper stuff or recompile your various WiFi drivers.

---

### Post by Unseelie on 2007-02-18
i lost my wireless also, came here, read this, rebooted as the older one, but still had noting, i reinstalled my connection using th howto i originay used, [here but i still have no connection, its just dissapereared]("http://www.ubuntuforums.org/showthread.php?t=296822&highlight=phq")

---

### Post by vrunner on 2007-02-18
Can Confirm this. ipw3945 driver here.
Rebooting to the older kernel doesn't work.

Strangely enough my wired connection doesn't work as well now. Some network-manager issues maybe ?

Am on my other computer right now.

---

### Post by natern on 2007-02-18
Since it's such a short process, I think I'm just going to reinstall the system and disable updates.

---

### Post by fpurdue on 2007-02-18
Not sure what it was in the update but once I went into the bios and disabled LAN/WLAN switching and the hardware lock went away -

---

### Post by eppoh on 2007-02-18
Same thing happened with my thinkpad and Prism wireless card. new kernel and now the card is not being assigned a hardware address.
Old kernel works, but makes me skittish about doing so called "critical updates"

---

### Post by satriani on 2007-02-18
I have the same problem here.
I have updated to the latest kernel (2.6.17-11-generic) and wireless stops working
When I boot my old kernel (2.6.17.10-generic) all is fine.

In my old kernel, I have lo, eth0 and eth1 , while in the ...11 kernel i have lo, eth0, sid0 and wlan0. With iwconfig it doesnt find wireless extensions.
What I did find is that it uses a different driver.
In ..10 it uses the orinoco_pci and in the ..11 it uses prism2_pci

I tried updating in the /etc/iftab but no results what soever..

Any ideas / solutions would be great!

---

### Post by natern on 2007-02-18
My wireless would not work in either kernel after the update, so there may be a couple updates affecting this problem. I've reinstalled already though, so I'm back up and running great. Best of luck to the rest of you! =)

---

### Post by trab_irl on 2007-02-19
... just a confirmation...

after last 3 days trouble to get wifi to work i got it finaly last night :)  (on a fresh installation without updates) ...
today i made some updates (me idiot didnt read this post :/ ) and... yes the wireless stops working and disapeart...  but going back to prvious kernel works...

---

### Post by Unseelie on 2007-02-20
anyone who lost their wireless on the old kernel (.10) and cannot seem to get it back up might want to check and make sure that their wireless card is all of the way into its slot, because that may be your problem (mine had popped out somehow, i blame karma)

---

### Post by satriani on 2007-02-22
Sorry to say this: (Not to flame you in any way)
But thats definitely not the solution. I cannot "pop" the card into the slot, its a mini-pci card. ;)

I guess I am not the only one with mini-pci (or other way of integrated wlan)

---

### Post by mikewhatever on 2007-02-22
It seems that the solution for the following card
> description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
it to install the linux-restricted-modules for the newer kernel.
You can verify which kernel that is > uname -a
and then search for the restricted modules in synaptic. If there is no internet connection of any kind and not from the older kernel, the appropriate package can be downloaded from [from here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all").

In my case no wireless worked under both kernels, until these modules were installed.

---

### Post by tc10b on 2007-02-22
I have an Atmel card, and it's as dead as it was under dapper.
I've tried the earlier kernel and no luck, and I've also tried the restricted modules and no luck.
I really don't want to have to reinstall, but I will if I must. 

Any help much appreciated.

Tom

---

### Post by mikewhatever on 2007-02-22
> **tc10b said:**
> I have an Atmel card, and it's as dead as it was under dapper.
I've tried the earlier kernel and no luck, and I've also tried the restricted modules and no luck.
I really don't want to have to reinstall, but I will if I must. 

Any help much appreciated.

Tom
You should probably ask for help with your card in a new thread giving some information and choosing a different title.
> lspci |grep -network

Not too many will look into the end of this one. Searching the forums for 'Atmel something' might also turn up stuff.

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

