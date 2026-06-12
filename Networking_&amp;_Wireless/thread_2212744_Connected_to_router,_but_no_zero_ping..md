---
title: "Connected to router, but no zero ping."
date: 2014-03-22
forum: Networking &amp; Wireless
---

### Post by Teethdude on 2014-03-22
I can successfully cannot to my router, it will work, then suddenly I have no connection speed at all. Every Windows machine in my home still works...
The only work around I have is every 2-3 minutes disabling my wifi card and re-enabling it. This all started happening about a month or so and has progressively gotten worse.

I am using an HP Pavilion g series.
It has a Realtek card I believe, but I do not know the exact hardware.

Thank you for your help.

---

### Post by houstonbofh on 2014-03-23
Look at your logs.  You are probably disassociating...  One thing I would try is looking at other drivers.  Those RT chips are cheap, and have a lot of different models.  From the terminal type "lspci" (Noo need for sudo) and find out what nic you have.  Then search Ubuntu Forums for that model nic and see if you find others with your problem.

---

### Post by Teethdude on 2014-03-23
Here's the output. It's a bit Greek to me, but I'm guessing you'll understand it.
```
mike@mike-Compaq:~$ lspci00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

```

---

### Post by houstonbofh on 2014-03-23
And here is the greek we are looking for.

```
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
```

Your wireless is a Realtek RTL8188CE chipset.  A little searching on that chipset shows that more people than just you have had a few issues with it.  Even back to 2010... [http://ubuntuforums.org/showthread.php?t=1604101](http://ubuntuforums.org/showthread.php?t=1604101)

This may help...
[http://ubuntuforums.org/showthread.php?t=2186114](http://ubuntuforums.org/showthread.php?t=2186114)

If not, this more drastic one...
[http://ubuntuforums.org/showthread.php?t=2170092](http://ubuntuforums.org/showthread.php?t=2170092)

---

### Post by Teethdude on 2014-03-24
Thanks! I'll report back in a while after testing some of these.

---

### Post by Teethdude on 2014-03-25
Thanks for the help, but the suggestions didn't seem to help, and the final link I don't really understand too well.
Any other solutions? If not, that's ok.

---

### Post by Teethdude on 2014-03-30
Well... After a while it seems to have fixed itself. I think. It's been a while since it cut out. Thanks for your help.

---

