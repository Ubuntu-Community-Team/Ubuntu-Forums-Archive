---
title: "HP 6910p wireless problem"
date: 2016-06-14
forum: Networking &amp; Wireless
---

### Post by stinovlas on 2016-06-14
Hello, 

it has been a while (I guess it was since 14.04? not sure) since my wireless stopped working after upgrading my Ubuntu. It shows "disabled by hardware switch". Now I have read lots of topics on this matter and none of which helped. 

I am dualbooting windows and wifi works perfectly in W7. Nevertheless, my hardware switch does nothing in Ubuntu. Even though I have read numerous topics, I was not able to solve this issue for about two years and I was just too lazy to care about it, so I used windows. I tried every release, hoping the bug was fixed, but it wasn't - well, I didn't even post it anywhere, so nobody knew. 

Here are some echos which I have seen in a few topices and which I have done:
```
xaver@tempest-lnx:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: hp-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: yes
3: hp-gps: GPS
    Soft blocked: yes
    Hard blocked: yes
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


```

```
xaver@tempest-lnx:~$ cat /sys/class/rfkill/rfkill0/hard
1
xaver@tempest-lnx:~$ sudo -i
[sudo] password for xaver: 
root@tempest-lnx:~# echo 0 > /sys/class/rfkill/rfkill0/hard
-bash: /sys/class/rfkill/rfkill0/hard: Permission denied

```

I would greatly appreciate if anyone would be able to help me. 

The laptop is HP Compaq 6910p.


EDIT (this might be useful...):

```


xaver@tempest-lnx:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)



```

---

### Post by stinovlas on 2016-06-14
so... this is strange. I got home from work now, thought I might give it a try. So I chose Ubuntu in Grub menu and turned the wireless HW switch _OFF_. When my desktop showed up (automatic login), the wifi button (which is a touch button and also ON/OFF light) was ON and I could choose my wifi network. I am now writing this from my wifi. 

So I actually just need to bypass something in the system that checks for the HW switch and decides whether it is ON or OFF, so I can force it ON. Although it would be much better if I could make it work right, so I could lower the battery consumption when I don't need wireless.

```

xaver@tempest-lnx:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hp-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
3: hp-gps: GPS
    Soft blocked: yes
    Hard blocked: yes
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

