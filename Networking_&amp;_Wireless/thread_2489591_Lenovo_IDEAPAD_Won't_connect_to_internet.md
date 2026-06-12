---
title: "Lenovo IDEAPAD Won't connect to internet"
date: 2023-08-04
forum: Networking &amp; Wireless
---

### Post by heroquestelf on 2023-08-04
Folks, I am officially losing my mind. I have a new Lenovo IDEAPAD 3 and it REFUSES to connect to the internet. Wired--wireless--nothing works. It is currently running Kubuntu 22.04. It has a 8x12th GEn Intel Core i3-1215U and 7.5 GiB of ram. I'm also having to type this out by hand, so it is bound to have typos, and for that you have my apologies in advance.

The wireless adapter is completely pooched. I have tried multiple  different things and I'm getting nowhere. The laptop does not have a  network plug, all it has is a USB-C plug. My router has a USB port on it  (USB-A) , but when I plug my USB-A  to USB-C cable into the laptop  nothing happens. There is no change. It does not detect the cable. 

(Not that I think this matters a huge amount, but I originally installed Linux Mint on the machine, and the same problem occurred. I *assumed* it was the operating system and not the machine, so I uninstalled Mint and installed Kubuntu, only to have the same error. I have been working at this for over four hours now and I'm losing my mind. Hopefully you guys can help me out. I DO have D-LINK DWA-171 AC600 USB wireless adapter that I have tried inserting to get the laptop to default to that adapter, but it does not appear to be working either--either that or I can't make the machine swap adapters.)

The network controller is listed as "Realtek Semiconductor Co., Ltd. Device b852"
Subsystem: Lenovo Device 4853
Flags: fast devsel, IRQ 225
I/O Ports at 3000 [disabled] [size=256]
Memory at 50500000 (64 bit, non-prefetchable) [disabled] [size=1M]
Capabilities: <access denied>

My lshw -C network result gives me the following 
*-network UNCLAIMED
description: Network controller
product: Realtek Semiconductor
vendor: Realtek Semiconductor
physical id: 0
bus info: pci@0000:02:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress cap_list
cofiguration: latency=0
resources: ioport:3000(size=256) memory:50500000-505fffff

my lspci gives this
02:00.0 Network controller: Realtek Semiconductor, Device b852

ip link says this:
1: lo: <LOOPBACK, UP, LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group qlen 1000
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00

my nmcli device show says this
GENERAL DEVICE:   lo
GENERAL TYPE:       loopback
GENERAL HWADDR: 00:00:00:00:00:00:00
GENERAL MTU:        65536
GENERAL STATE:     10 (unmanaged)
GENERAL CONNECTION: --
GENERAL CON-PATH: --
ip4 ADDRESS[1]   127.0.0.1/8
IP4 GATEWAY       --
IP6 Address[1]          ::1/128
IP6 GATEWAY        --
IP6 ROUTE           dst = ::1/128, nh = ::, mt = 256

ifconfig:
lo: flags=73<UP, LOOPBACK, RUNNING> mtu 65536
inet 127.0.0.1 netmask 255.0.0.0
inet6: ::1 prefixlen 128 scopeid 0x10,host.
loop txqueuelen 1000 (local loopback)
RX packets 45500 bytes 3239782 (3.2 MB)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 45500 bytes 3239782 (3.2 MB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0

iwconfig
lo         no wireless extensions

Any help would be welcome!

---

### Post by readableauthor on 2023-08-04
What's the output for this:
```

lspci -nnk | grep -iA3 net

```

---

### Post by heroquestelf on 2023-08-04
02:00.0 Network Controller [0280]: Realtek Semiconductor Device [10ec:b852]
            Subsystem: Lenovo Device [17aa:4853]
03:00.0 SD Host Controller [0805]: Genesys Logic, Inc GL9750 SD Host Controller [17a0.9750] (rev 01)
            Subsystem: Lenovo GL9750 SD Host Controller [17aa:384a]

---

### Post by heroquestelf on 2023-08-04
And just so it's said, if someone could let me know the easiest way to switch from the onboard network card to the external USB network card that would go a long way.

---

### Post by readableauthor on 2023-08-04
> **heroquestelf said:**
> 
02:00.0 Network Controller [0280]: Realtek Semiconductor Device [10ec:b852]


This device should work on Linux kernel 6.2+. You could run (K)Ubuntu 23.04 off a USB stick to see if that works

---

### Post by readableauthor on 2023-08-04
> **heroquestelf said:**
> And just so it's said, if someone could let me know the easiest way to switch from the onboard network card to the external USB network card that would go a long way.

So that you can use your external Wi-Fi stick? As far as I know it requires external drivers.
[https://linux-hardware.org/index.php?id=usb:2001-3314](https://linux-hardware.org/index.php?id=usb:2001-3314)

---

### Post by chili555 on 2023-08-04
Your internal device requires drivers. Let's install the correct driver:

```
sudo apt install --reinstall git bc build-essential
git clone https://github.com/lwfinger/rtw89.git
cd rtw89
make
sudo make install
```Let’s load the required firmware:

```
cd /usr/lib/firmware/
sudo mkdir rtw89
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/rtw89/rtw8852c_fw.bin
```
You will probably need to disable Secure Boot. Reboot.

When your kernel version changes, then you need to do the following:

```
cd ~/rtw89
git pull
make clean
make
sudo make install
```

---

### Post by heroquestelf on 2023-08-04
Okay, but here is the problem... I **CAN'T **install git, bc and build-essentials. That requires me to be online. Nor can I clone anything off of github... because, again, that requires me to be online.

Unless you know of an alternate method I can use to get this stuff on my laptop. The wireless doesn't work, nor does the wired connection.

---

### Post by chili555 on 2023-08-04
Can you tether your phone?

---

### Post by heroquestelf on 2023-08-04
OMG... I didn't even know that was an *OPTION*. You're my **HERO**. I'm upgrading and working through your instructions right now. I will update this post once I'm done. I just wanted to go ahead and thank you for rescuing my sanity.

**IT WORKED!!**

You guys **ROCK.**

---

### Post by chili555 on 2023-08-04
Awesome! Glad it's working! Have fun!!

---

### Post by ensto on 2023-11-01
I have this exact issue, on another lenovo ideapad 3 running Lubuntu 22.0.4, but the product line in lshw -c network shows "Gemini Lake PCH CNVi WiFi"

how would I adapt this solution for my network card, since it uses different drivers?

also, is there a way to download everything I need onto a usb stick and transfer it over? I dont have a phone to tether.

---

### Post by chili555 on 2023-11-01
> **ensto said:**
> I have this exact issue, on another lenovo ideapad 3 running Lubuntu 22.0.4, but the product line in lshw -c network shows "Gemini Lake PCH CNVi WiFi"

how would I adapt this solution for my network card, since it uses different drivers?

also, is there a way to download everything I need onto a usb stick and transfer it over? I dont have a phone to tether.I doubt you have the same device and I doubt that this solution works for you. Please start your own new question and include the result of these terminal commands:

```
lspci -nnk | grep 0280 -A3
sudo dmesg | grep iwl
uname -r

```
Thanks.

---

