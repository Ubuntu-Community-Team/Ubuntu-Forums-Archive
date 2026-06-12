---
title: "Wireless Network Connection Unstable in 16.04 on Lenovo Thinkpad Edge"
date: 2017-06-16
forum: Networking &amp; Wireless
---

### Post by mlnease on 2017-06-16
Wireless Network Connection Unstable in 16.04 on Lenovo Thinkpad Edge

Hello,

I'm trying to troubleshoot my wife's laptop; her Network Manager is sporadically (but very frequently) failing to detect connections from our CenturyLink(!) wireless router.

It's been working fine for several weeks (months?) until the last couple days so, I think, not a driver problem.

Xubuntu often finds and connects to the correct wireless connection (and displays all the other locals) on open; then fails after a minute or two.

I've googled this at some length and carefully searched the 'Network & Wireless' forum here to no avail.

Any suggestions, anyone?  Any help would be greatly appreciated--thanks in advance.

p.s.  Network Manager and wifi are working normally on my Xubuntu 16.04 desktop workstation.

---

### Post by kc1di on 2017-06-16
I know you said you didn't think it was a driver problem.  But it would be helpful to know the wireless card and driver your using in that Laptop.

---

### Post by mlnease on 2017-06-16
Thanks very much for the quick response.  Can you please tell me how to display this on the laptop?  I thought sysinfo might do it but no.

---

### Post by mlnease on 2017-06-16
Does this help:

```
lspci -k | grep -A 2 -i "VGA"
```
returns
```
VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev12)
    Subsystem:  Lenovo Core Processor Integrated Graphics Controller
    Kernel driver in use: i915

```
```
sudo ubuntu-drivers devices
```
returns
```
== cpu-microcode.py ==
driver  : intel microcode - distro non-free
```

I'm perforce copying this by hand off the laptop--hope I've got it right.

Thanks a lot again for your time and attention.

---

### Post by Hadaka on 2017-06-16
Hi, please open a terminal...ctrl/alt/t... then do and post..
```
lspci -n | awk '/0280/{print $3}'
rfkil list all | grep yes
```
thanks

---

### Post by kc1di on 2017-06-17
do this and then list the output 
In a terminal
```
sudo apt-get install inxi
``` once that install run this command and post the output,
```
inxi -N
``` 
This will give you the network cards.

---

### Post by mlnease on 2017-06-17
> **Hadaka said:**
> Hi, please open a terminal...ctrl/alt/t... then do and post..
```
lspci -n | awk '/0280/{print $3}'
rfkil list all | grep yes
```
thanks
Thanks, &#35064;,
And sorry for the slow response--I've been away from my computer.
Unfortunately,                          ```
lspci -n | awk '/0280/{print $3}'
rfkil list all | grep yes
```  didn't return anything, entered either as single lines or together (or with 'rfkill' rather than 'rfkil' as the terminal suggested).  Am I doing something wrong?
Thanks for your patience.

---

### Post by mlnease on 2017-06-17
> **kc1di said:**
> do this and then list the output 
In a terminal
```
sudo apt-get install inxi
``` once that install run this command and post the output,
```
inxi -N
``` 
This will give you the network cards.

Thanks again kc1di and sorry for the slow response--I've been away from my computer.
```
inxi -N
```
returns
```
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
```
Thanks again for your time and patience!

---

### Post by kc1di on 2017-06-17
the output does not show any wireless card only your ethernet.  
Try this instead ```
inxi -Fxz
```

---

### Post by mlnease on 2017-06-17
> **kc1di said:**
> the output does not show any wireless card only your ethernet.  
Try this instead ```
inxi -Fxz
```
```
System:    Host: rose-ThinkPad-Edge Kernel: 4.4.0-79-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Xfce 4.12.3 (Gtk 2.24.28) Distro: Ubuntu 16.04 xenial
Machine:   System: LENOVO product: 057882U v: ThinkPad Edge
           Mobo: LENOVO model: 057882U Bios: LENOVO v: 80ET36WW (1.13 ) date: 06/04/2010
CPU:       Dual core Intel Core i3 M 330 (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 8511
           clock speeds: max: 2133 MHz 1: 1199 MHz 2: 1599 MHz 3: 1199 MHz 4: 933 MHz
Graphics:  Card: Intel Core Processor Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Ironlake Mobile GLX Version: 2.1 Mesa 12.0.6 Direct Rendering: Yes
Audio:     Card Intel 5 Series/3400 Series High Definition Audio driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-79-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 3000 bus-ID: 09:00.0
           IF: enp9s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1000.2GB (1.5% used) ID-1: /dev/sda model: TOSHIBA_MQ01ABD1 size: 1000.2GB
Partition: ID-1: / size: 419G used: 6.8G (2%) fs: ext4 dev: /dev/sda5
           ID-2: swap-1 size: 8.37GB used: 0.00GB (0%) fs: swap dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 43.0C mobo: 0.0C
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 185 Uptime: 18:53 Memory: 792.0/7780.4MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35 
```Thanks again!

---

### Post by kc1di on 2017-06-17
It still is not showing any wireless card.  
please run```
rfkill list
``` and post the results.

---

### Post by mlnease on 2017-06-17
> **kc1di said:**
> It still is not showing any wireless card.  
please run```
rfkill list
``` and post the results.
This returns nothing except the terminal prompt.
Thanks again for your time and attention.

---

### Post by kc1di on 2017-06-18
you are preforming these commands on the laptop?  the results you are giving me show no Wireless card at all.
If you are running these commands while the laptop is plugged into an eternet connect (hard wire) if maybe shutting the wireless card off. 
you need to run them with it unplugged from the LAN, you can replug after the commands are run.

---

### Post by mlnease on 2017-06-18
> **kc1di said:**
> you are preforming these commands on the laptop?  the results you are giving me show no Wireless card at all.
Hello,
Yes, on the laptop.  So would I be correct in saying that the OS is not detecting the Wireless card (since the wifi was working fine up until a few days ago and has worked sporadically since)?

All the times I've run the commands, there has been no connection and no indication via Network Manager of wifi connections.  Since wifi has occasionally worked briefly on startup since the problem began, I'll try a cold reboot, run ```
rfkill list
``` immediately and post those results if any.

Thanks again.

EDIT:  No good--no wifi connection even briefly after reboot.  Also, I tried Windows (on an unused partition) and a Xubuntu startup disk--no wifi on either one.  So I'm thinking this is a firmware problem?  Maybe she needs a new wifi adapter?

---

### Post by kc1di on 2017-06-18
Ok it's beginning to sound as if the there is hardware problem with the wifi card.

---

### Post by mlnease on 2017-06-18
> **kc1di said:**
> Ok it's beginning to sound as if the there is hardware problem with the wifi card.Makes sense to me.  I'm bad enough with desktop hardware; I guess it's into the shop for this laptop.

Thanks a *million* for all your time, attention and patience.

mn

---

### Post by kc1di on 2017-06-18
One way to check is to try a cheap wifi usb dongle[ like this one.]("https://www.amazon.com/gp/product/B00EQT0YK2/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B00EQT0YK2&linkCode=as2&tag=wireless2016-20&linkId=c8598a4619fd2144bed2463f850e8b54")

---

### Post by mlnease on 2017-06-18
> **kc1di said:**
> One way to check is to try a cheap wifi usb dongle[ like this one.]("https://www.amazon.com/gp/product/B00EQT0YK2/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B00EQT0YK2&linkCode=as2&tag=wireless2016-20&linkId=c8598a4619fd2144bed2463f850e8b54")You know, the same idea crossed my mind after my last post--excellent advice.  Thanks again.

---

### Post by kc1di on 2017-06-18
Good luck let us know how your make out.

---

### Post by mlnease on 2017-06-18
> **kc1di said:**
> Good luck let us know how your make out.
Will do--thanks again!

---

### Post by praseodym on 2017-06-18
Check the UEFI settings if wireless can be activated there.

---

### Post by mlnease on 2017-06-18
Thanks for your response.  As I understand it, I would first have to convert the drive to GPT, then convert the dual-boot installation to UEFI using a UEFI-bootable Ubuntu USB drive *and* a UEFI-bootable Windows USB drive.  Is this correct?  

I'm inclined to think that the wifi card is simply kaput, as Control Panel shows no wifi connection in the Windows partition and Network Manager shows none either from the installed 16.04 or a 16.04 live cd.  Do you think that likely?  If so, converting to UEFI seems a lot of trouble just to verify a dead wifi card.

---

### Post by mlnease on 2017-06-30
> **kc1di said:**
> Good luck let us know how your make out. Got a Chinese dongle off Ebay for $1.89--problem solved.  Thanks again!

---

