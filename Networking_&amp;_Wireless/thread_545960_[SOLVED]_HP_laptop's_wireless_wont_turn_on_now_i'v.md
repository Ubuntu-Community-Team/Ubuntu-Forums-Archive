---
title: "[SOLVED] HP laptop's wireless wont turn on now i'v installed ubuntu"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by dlaporte on 2007-09-08
Hi, I have read some other threads about this but i am completely new to ubuntu so some step by step help is needed.

Now I have installed ubuntu the wireless button when pressed no longer lights up and so i cannot get my wireless to turn on.

Any help would be much appreciated but before someone tell me to go to the terminal and type xyz someone needs to tell me what the terminal is??

As i said i am a total beginner.

Thanks

---

### Post by dlaporte on 2007-09-08
ok so i know what the terminal is now, anybody got any suggestions on what i can do please?

---

### Post by noob12 on 2007-09-08
We need to see what device and driver you have on your laptop.  Can you post the output of these commands
```

lspci -nn

sudo lshw -C network

```

---

### Post by dlaporte on 2007-09-08
lspci - nn gives this output:
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)
02:06.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
02:06.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
02:06.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
02:06.5 Communication controller [0780]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller [104c:8035]
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express [14e4:167d] (rev 11)


sudo lshw -C network gives this output:
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@10:00.0
       logical name: eth0
       version: 11
       serial: 00:15:60:b8:e5:eb
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72.1 duplex=full firmware=5751m-v3.29a ip=192.168.0.191 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:d0000000-d000ffff irq:16
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@02:04.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:61:87:7f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: iomemory:d0400000-d0400fff irq:22

---

### Post by noob12 on 2007-09-08
Try this
```

sudo modprobe -r ipw2200
sudo modprobe ipw2200 led=1

```

Then try the switch.

If that works, the solution is at hand.  Otherwise more diagnostics will be needed.

Note that you also have to enable the wireless in NetworkManager (NM) by right clicking on the little dual computer icon in the upper right hand panel.

---

### Post by dlaporte on 2007-09-08
Thanks, Im afraid that didnt fix it though. Was anything supposed to come up after i typed it and hit enter?

---

### Post by noob12 on 2007-09-08
Nothing would come up.  After you ran the commands, you should operate the switch and you should enable wireless in NM.

Can you also post the output of
```

cat /sys/class/net/*/device/rf_kill

```

---

### Post by dlaporte on 2007-09-08
2

---

### Post by noob12 on 2007-09-08
OK.  The 2 indicates it is disabled at the hardware level. If the switch didn't work after you did the modprobe commands I indicated, you should next check your BIOS settings.  Make sure that wireless is enabled in the BIOS.  If there is a setting that says something like Application/OS control
you generally want that on as well.

Can you also post the specific model number of the laptop that you have?

---

### Post by dlaporte on 2007-09-08
I have enabled WLAN in the bios

The laptop is a hp compaq nc6220

Thanks again for your help

---

### Post by noob12 on 2007-09-08
It wasn't clear if you meant this worked or you still have the problem.  If you still have the problem, do this:

```

echo "options ipw2200 led=1" | sudo tee -a /etc/modprobe.d/options

```

Then reboot and after your reboot, try the switch, and also post the output of

```

dmesg

```

[COLOR="Red"]UPDATE:  I see you marked the thread solved.  Can you let people know what solved it for you?[/COLOR]

---

### Post by dlaporte on 2007-09-09
I believe it must have been one of the solutions you gave me, as i noticed later on that the laptop had detected my wireless network however the led for the button was not on. When you had asked me to try pressing the button after the instructions you had given me i was just looking to see if the led came on. So the button does turn the wireless on and off now but for some reason the light not come on.

Thank you for the help you gave me.

---

### Post by noob12 on 2007-09-09
OK.  It is not clear to me whether the modprobe commands did it or you had to change settings in the BIOS.

If you didn't change any settings in the BIOS, it was the modprobe commands, and in this case, in order to get that to happen automatically on all boots, you need to do the command in my previous post, namely:
```

echo "options ipw2200 led=1" | sudo tee -a /etc/modprobe.d/options

```
This adds the **led=1** flag to the options that are applied during a normal boot.  The option name is a misnomer.  It doesn't necessarily turn on the led on all models.  It should make the driver sensitive to the toggle switch setting.

---

### Post by subru77 on 2007-09-16
> **noob12 said:**
> Nothing would come up.  After you ran the commands, you should operate the switch and you should enable wireless in NM.

Can you also post the output of
```

cat /sys/class/net/*/device/rf_kill

```

Hi,
I have the same issue in my laptop and I am trying to follow the instructions here.

But the output for thea bove command was

 cat: /sys/class/net/*/device/rf_kill: No such file or directory

What should I do now ??

---

### Post by security_mon on 2008-06-18
:guitar:
Thanks noob12! I have an HP NC6220 and this solution worked great!!! The LED still does not work, but that is not important to me, the good part is I can control my hardware now.  FYI I'm running 8.04.

Since there were two solutions, just to clarify, what worked for me was:

sudo modprobe -r ipw2200
sudo modprobe ipw2200 led=1
Thanks again!

---

