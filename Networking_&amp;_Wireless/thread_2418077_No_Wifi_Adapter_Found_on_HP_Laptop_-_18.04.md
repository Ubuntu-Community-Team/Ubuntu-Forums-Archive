---
title: "No Wifi Adapter Found on HP Laptop - 18.04"
date: 2019-05-01
forum: Networking &amp; Wireless
---

### Post by hypermesher on 2019-05-01
[COLOR=#242729][FONT=Arial]My laptop: HP 15-DA1006NT 5MM06EA i5-8265U 4GB 1TB 128GB SSD 2GB MX110 15.6 FreeDOS[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I installed 18.04 Ubuntu both with 3rd party hardware and without them. I have same problem: "**No wifi adapter found**"[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
iwconfig[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]eno1 no wireless extension[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]lo no wireless extension[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
When I wrote "rfkill", I didn't have any results or error.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I looked the old topics and populer solution is bcmwl-kernel-source. However, when I wrote bcmwl-kernel-source to &#305;nstall to term&#305;nal, I took this error:[/FONT][/COLOR]
**[COLOR=#242729][FONT=Arial]unable to locate package bcmwl-kernel-source[/FONT][/COLOR]**
[COLOR=#242729][FONT=Arial]
Then I researced this error's solution.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][URL="https://askubuntu.com/questions/671251/installing-broadcom-wireless-drivers-for-ubuntu-15-04"]
Installing Broadcom Wireless Drivers for ubuntu 15.04[/URL] This topic doesn't work for me [/FONT][/COLOR][COLOR=#242729][FONT=Arial]and I've tried a few more things like that, but it didn't work. What are your solution suggestions?[/FONT][/COLOR]

---

### Post by kc1di on 2019-05-01
Your machine has an Realtek wifi card and you'll have to install some drivers from git hub to get it going.  Can you temporarily connect via Ethernet?  
If so follow the instructions found [here.]("https://askubuntu.com/questions/996562/wifi-not-working-in-hp-laptop-rtl8723de-realtek-wireless-driver")  Follwo the instruction in answer # 2 Good luck and Welcome to Ubuntu Forums.

---

### Post by hypermesher on 2019-05-01
> **kc1di said:**
> Your machine has an Realtek wifi card and you'll have to install some drivers from git hub to get it going.  Can you temporarily connect via Ethernet?  
If so follow the instructions found [here.]("https://askubuntu.com/questions/996562/wifi-not-working-in-hp-laptop-rtl8723de-realtek-wireless-driver")  Follwo the instruction in answer # 2 Good luck and Welcome to Ubuntu Forums.

Thank you for your reply. However, with an internet connection, when firstly, I try to install build-essential or any packages, I take this error:

[B]<package name> [COLOR=#242729][FONT=Arial]has no installation candidate.[/FONT][/COLOR]
[/B]
I write <package name>, because I take this error for every package or this error:

**unable to locate package <name>**

---

### Post by jeremy31 on 2019-05-01
Try ```
sudo apt update
```
See if it finds the packages then

And post results for ```
lspci -nnk | grep -iA3 net
```

---

### Post by hypermesher on 2019-05-01
> **jeremy31 said:**
> Try ```
sudo apt update
```
See if it finds the packages then

And post results for ```
lspci -nnk | grep -iA3
```

Output is of `lspci -nnk | grep -iA3`

myHP:~$ lspci -nnk | grep -iA3

Usage: grep [OPTION]... PATTERN [FILE]...
Try 'grep --help' for more information.

---

### Post by jeremy31 on 2019-05-01
Fixed the command
```
lspci -nnk | grep -iA3 net
```

---

### Post by hypermesher on 2019-05-01
> **jeremy31 said:**
> Fixed the command
```
lspci -nnk | grep -iA3 net
```

This is the output:

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8533]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    Subsystem: Hewlett-Packard Company Device [103c:8319]

---

### Post by jeremy31 on 2019-05-01
Check ```
mokutil --sb-state
```
If it says Secure Boot is enabled, then reboot and disable Secure Boot in BIOS, leave the Secure Boot keys alone
Then do
```
sudo apt update
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```
Reboot

---

### Post by hypermesher on 2019-05-01
> **jeremy31 said:**
> Check ```
mokutil --sb-state
```
If it says Secure Boot is enabled, then reboot and disable Secure Boot in BIOS, leave the Secure Boot keys alone
Then do
```
sudo apt update
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```
Reboot

I made this step by step, but still I have same problem: no wifi adapter found.

Edit: Problem is solved. Thank you your help jeremy31. I am very happy now. Thanks.

---

