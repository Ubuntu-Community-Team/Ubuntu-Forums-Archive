---
title: "netowrk unclaimed intel 3945"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by tsur on 2008-06-01
hi, does anyone know how to get around this problem?

i am trying get my wireless intel 3945 internal card , to work
on my laptop hp dv8000.

i am not an expert , digging in this forum  and trying various techniques
i think i pinpointed the problem to something along this lines:

when i type

sudo lshw -C network


i get NETWORK -unclaimed

for my wireless card.
anyone with an insight on this would be helpful thanks in advance

---

### Post by superprash2003 on 2008-06-01
please type iwconfig in your terminal and post output

---

### Post by hal10000 on 2008-06-01
I don#t know if you already tried to connect using your network-config tool (I guess in gnome it can be found under System--->Settings--->configure network or manage network, i don'use gnome, so i can't tell you the exact menu entry).
If you cna not connect using this tool, then you shold post the output of the following two commands on order to get the PCI-ID for your card:

1. [COLOR="Red"]lspci[/COLOR]
2. [COLOR="Red"]lspci -n[/COLOR]

---

### Post by tsur on 2008-06-02
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
satori@laptop:~$ lspci -n
00:00.0 0600: 8086:27a0 (rev 03)
00:01.0 0604: 8086:27a1 (rev 03)
00:1b.0 0403: 8086:27d8 (rev 01)
00:1c.0 0604: 8086:27d0 (rev 01)
00:1c.1 0604: 8086:27d2 (rev 01)
00:1c.2 0604: 8086:27d4 (rev 01)
00:1d.0 0c03: 8086:27c8 (rev 01)
00:1d.1 0c03: 8086:27c9 (rev 01)
00:1d.2 0c03: 8086:27ca (rev 01)
00:1d.3 0c03: 8086:27cb (rev 01)
00:1d.7 0c03: 8086:27cc (rev 01)
00:1e.0 0604: 8086:2448 (rev e1)
00:1f.0 0601: 8086:27b9 (rev 01)
00:1f.1 0101: 8086:27df (rev 01)
00:1f.2 0106: 8086:27c5 (rev 01)
00:1f.3 0c05: 8086:27da (rev 01)
01:00.0 0300: 10de:01d8 (rev a1)
06:00.0 0280: 8086:4222 (rev 02)
08:06.0 0607: 104c:8039
08:06.1 0c00: 104c:803a
08:06.2 0180: 104c:803b
08:06.3 0805: 104c:803c
08:08.0 0200: 8086:1092 (rev 01)


this is the lspci and lspci -n
the wireless card appears.

iwconfig is:

> satori@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.



please help

i also downloaded the package from linuxwireless but when i try to load
it it says something about unrecognized symbol in mac80211

o.k thats what i know any help would be greatly appreciated.

---

### Post by chili555 on 2008-06-02
Please let us see:```
sudo cat /var/log/messages | grep switch
lsmod | grep iwl
```Thanks.

---

### Post by tsur on 2008-06-03
hello, thank you for your quick reply,
hmm both lines of code you mentioned returned empty.

maybe it has to do with rebuilding the mac80211 sub-system, i dont really understand
what it means, but maybe this can help because it says unkniwn symbol when i try to 
install the linuxwirless drivers.

if someone could guide me on how to re-install this mac80211 it would be great.

---

### Post by hal10000 on 2008-06-03
Hi,
i have found another thread with exactly the same problem as yours, and the solution was to turn on the wifi-button on the laptop.
Here it is:
[http://ubuntuforums.org/showthread.php?t=567957&highlight=wireless+intel+3945]("http://ubuntuforums.org/showthread.php?t=567957&highlight=wireless+intel+3945")

---

### Post by tsur on 2008-06-03
hmm there is wireless push buttonon top of the keyboard just below the lcd
when i push it bluetooth pops into life but still network UNCLAIMED in the
wireless card.

anyone else ? maybe this mac80211 or am i completly off topic?

---

### Post by chili555 on 2008-06-03
Please do:```
sudo modprobe iwl3945
```Is your wireless still UNCLAIMED? Please post the output of:```
ifconfig
```Thanks.

---

### Post by hal10000 on 2008-06-03
> hmm both lines of code you mentioned returned empty.

do you mean that [COLOR="Red"]lsmod | grep iwl[/COLOR] gives no answer???

If so, then try [COLOR="Red"]sudo modprobe iwl3945[/COLOR]. Then try again [COLOR="Red"]lsmod | grep iwl[/COLOR] to verify if it is loaded now and reconfigure your network with network-manager

---

### Post by CHW on 2008-06-03
> **chili555 said:**
> Please do:```
sudo modprobe iwl3945
```Is your wireless still UNCLAIMED? 

I had the same problem! And searched for two hours in the forums. Now it isn't UNCLAIMED any more and it works like before.

Thank you Chili555!

---

### Post by CHW on 2008-06-03
I have still a little problem, when I reboot, everything is gone and I have to reenter this command.

---

### Post by tsur on 2008-06-03
yes 
> lsmod | grep iwl
no answear

and when i do

sudo modprobe iwl3945 
i get
> 
tsur@laptop:~$ sudo modprobe iwl3945
WARNING: Error inserting iwlwifi_mac80211 (/lib/modules/2.6.24-17-generic/updates/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwl3945 (/lib/modules/2.6.24-17-generic/updates/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
tsur@laptop:~$ 


so this is probably the problem no?

 thank you guys for the help
i nevere seen such a responsive and helpful community.
ubuntu - humanity towards others.
thanks
tsur

---

### Post by chili555 on 2008-06-03
@CHW- Thanks for the kind comments. I don't know why this doesn't just load automagically; maybe we can give it a little nudge. *sudo gedit /etc/modules* and add, on its own line:```
iwl3945
```Save and close gedit. Now does it load correctly at boot?

---

### Post by chili555 on 2008-06-03
@tsur- > so this is probably the problem no?Yes, indeed. Let's follow the clue we were given and look at:```
dmesg | grep iwl
```> maybe it has to do with rebuilding the mac80211 sub-systemYes, indeed. Can you please give us a link to the file you downloaded and I'll try to see what's gone wrong. If you can run 'make' or 'make install' again and reproduce the errors or warnings and post the terminal output, maybe we can help figure out the problem.

What about the built-in iwl3945 didn't work for you?

For the benefit of the searchers, if your 'make' ends in errors, stop! Move away from the keyboard! Anything and everything beyond that point is going to be a train wreck. Re-read the README or Google the error and fix the underlying problem before you try 'make' again.

---

### Post by CHW on 2008-06-03
I also had a look at this file before, but I didn't dare to change something there... Yes it helped. Thank you again :)

---

### Post by hal10000 on 2008-06-03
> i also downloaded the package from linuxwireless but when i try to load
it it says something about unrecognized symbol in mac80211

maybe this is the problem, because if you downloaded a driver not from the ubuntu-repositories, then it presumably doesn't fit your kernel-version. This is at least what your modprobe says:

> 
tsur@laptop:~$ sudo modprobe iwl3945
WARNING: Error inserting iwlwifi_mac80211 (/lib/modules/2.6.24-17-generic/updates/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwl3945 (/lib/modules/2.6.24-17-generic/updates/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)


So you might have to reinstall the apprpriate package, the package is called [COLOR="Red"]linux-ubuntu-modules-2.6.24-17-generic[/COLOR]. You can do that with Synaptic (or another package-tool)

After you have done this, you should again try [COLOR="Red"]sudo modprobe iwl3945[/COLOR] and if this works, then try to configure it with your network-manager.

---

### Post by hal10000 on 2008-06-03
i have just found another link here: [http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/")

It says, that the iwl... drivers shipped with hardy are somehow buggy and that you should install the backported drivers to make it work better.

---

### Post by tsur on 2008-06-09
somehow with the backports turned on the wireless came back to showing up.
now i need to find a wireless network to see if it actually recieves anything
thanks for you help keep up the good work

---

