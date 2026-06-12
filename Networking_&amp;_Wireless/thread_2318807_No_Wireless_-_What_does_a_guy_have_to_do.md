---
title: "No Wireless - What does a guy have to do?"
date: 2016-03-29
forum: Networking &amp; Wireless
---

### Post by Bob_Pennington on 2016-03-29
I have a new Lenovo G50-45 laptop.  Ethernet connectivity works fine, but wireless is hopeless at this point. I've tried everything in every thread that mentions the wireless nic in the laptop.  No help or solution.
I'm up live in new Ubuntu Beta 2 now and have same results.  Lubuntu 15.10  is installed to HDD on laptop & no wireless on it either.  The following reflects the hardware involved.  
Can anyone help please?  All help is greatly appreciated & thanks in advance.

 lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
    Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3812]
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by eltonw on 2016-03-29
> **Bob_Pennington said:**
> I have a new Lenovo G50-45 laptop.  Ethernet connectivity works fine, but wireless is hopeless at this point. I've tried everything in every thread that mentions the wireless nic in the laptop.  No help or solution.
I'm up live in new Ubuntu Beta 2 now and have same results.  Lubuntu 15.10  is installed to HDD on laptop & no wireless on it either.  The following reflects the hardware involved.  
Can anyone help please?  All help is greatly appreciated & thanks in advance.

 lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
    Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3812]
    Kernel driver in use: r8169
    Kernel modules: r8169

I also have a Lenovo, and was able to get wifi and bluetooth with help over at the Mint Linux forums. Please NOTE: I am supposed to be running Mint Linux 17.2, but my updates tell me I'm on Ubuntu 14.04. I'm quite disappointed that the newer ubuntu versionstill does not work with the Lenovo.
Kindly refer to this link which might solve your problem: [https://forums.linuxmint.com/viewtopic.php?f=53&t=204566&p=1075788&e=1075788](https://forums.linuxmint.com/viewtopic.php?f=53&t=204566&p=1075788&e=1075788)

HTH.:)

---

### Post by jeremy31 on 2016-03-29
Bob_Pennington

Please post ```
uname -r; modinfo ath10k_pci; dmesg | grep ath10k
```

And where did you get the firmware and board files from?


Hi Elton
Linux Mint is based on Ubuntu and uses some Ubuntu repos but it does have it's own repos for what they maintain which is basically artwork and their Update Manager, and possible a desktop environment. if ```
cat etc/lsb-release
```
Shows Linux Mint, you have Linux Mint.  Topics concerning Linux Mint here get moved to [http://ubuntuforums.org/forumdisplay.php?f=453](http://ubuntuforums.org/forumdisplay.php?f=453)

---

### Post by eltonw on 2016-03-30
> **jeremy31 said:**
> Bob_Pennington

Please post ```
uname -r; modinfo ath10k_pci; dmesg | grep ath10k
```

And where did you get the firmware and board files from?


Hi Elton
Linux Mint is based on Ubuntu and uses some Ubuntu repos but it does have it's own repos for what they maintain which is basically artwork and their Update Manager, and possible a desktop environment. if ```
cat etc/lsb-release
```
Shows Linux Mint, you have Linux Mint.  Topics concerning Linux Mint here get moved to [http://ubuntuforums.org/forumdisplay.php?f=453](http://ubuntuforums.org/forumdisplay.php?f=453)

Yes I'm quite aware that while Mint is based on Ubuntu, there are important differences. I just thought the solution that worked for me _might_ work for the O.P., given that his also is a Lenovo machine.
To reply to the other part of your comment: Whenever I boot the machine it says "Ubuntu 14.04" _**before**_ I get to the desktop.

Here's the result I get in the console: 
```

G50-45 ~ $ cat etc/lsb-release
cat: etc/lsb-release: No such file or directory

```

ADDENDUM: Sysinfo gives me this:
SYSTEM INFORMATION
	Running Ubuntu Linux, the Ubuntu 14.04 (trusty) release.
	GNOME: 3.8.4 (Ubuntu 2015-12-02)
	Kernel version: 3.19.0-30-generic (#34~14.04.1-Ubuntu SMP Fri Oct 2 22:09:39 UTC 2015)
	GCC: 4.8 (x86_64-linux-gnu)
	Xorg: 1.15.1 (12 February 2015  02:49:29PM)
	Hostname: Lenovo-G50-45
	Uptime: 0 days 0 h 37 min



**NOTE to moderator(s):** It's been about a couple of years that I have not been active in the ubuntu forums, so I apologise if I have posted in the wrong section.

respectfully

---

