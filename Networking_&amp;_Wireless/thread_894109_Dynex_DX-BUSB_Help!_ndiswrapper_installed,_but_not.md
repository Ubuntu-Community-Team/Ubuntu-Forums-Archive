---
title: "Dynex DX-BUSB Help! ndiswrapper installed, but not working!"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by cal9745 on 2008-08-18
There are a ton of forum posts about the Dynex DX-BUSB in linux, and I haven't found one that gets it working yet!

I run the newest ubuntu (with acpi problem boot).

lsusb tells me the card is located at "Bus 006 Device 007: ID 4317:0720"

Nothing happens at the final "modprobe ndiswrapper" step, and afterward my wireless card isn't working. The .inf drivers are installed fine according to "ndiswrapper -l" but the modprobe step doesn't complete I guess.

Just so you know, in Slax linux I got a "segmentation fault" at the same exact step.

Thanks, Cal.

---

### Post by cariboo on 2008-08-19
You won't get any thing echoed back if the ndiswrapper module install correctly. To check and make sure ndiswrapper is loaded in a terminal type:

```
lsmod | grep ndiswrapper
```

You will get something echoed back with ndiswrapper in the contents, but this doesn't mean that the drivers are loaded. To find out if the drivers have loaded in a terminal type:

```
ndiswrapper -l
```

This should echo back something like this:

```
Installed ndis drivers:
  {name of driver} driver present, hardware present
```

If all the above works correctly in a terminal try:

```
sudo iwlist <wlan0> scan
```

Where <wlan0> is your wireless device. If you're not sure what your device should be, in a terminal type:

```
sudo iwconfig
```

 Jim

---

### Post by cal9745 on 2008-08-19
Thanks Jim, but that is my problem: iwconfig doesn't display a wlan0 device at all, and "ndiswrapper -l" tells me I have the driver installed, but the device isn't present. However, I know ubuntu sees the device with "lsub" calling it "Bus 006: Device 007: ID 4317:0720"

Oddly enough, "ndiswrapper -l" displayed driver and device present in Slax..but it still didn't work at the modprobe step.

---

### Post by cariboo on 2008-08-20
So what you're saying is that when you try to load ndiswrapper like this:

```
sudo modprobe ndiswrapper
```

it fails?

are you using the same windows drivers? I had a broadcom based pci wirekss card that finally died, I tried the XP drivers, Windows 98 drivers and finally found that the Windows 2000 drivers worked better than the other 2.


Jim

---

### Post by cal9745 on 2008-08-20
The only other driver's I've found were windows Vista drivers, and I thought I read somewhere not to use those.

And modprobe ndiswrapper doesn't do anything it seems, no message is displayed and afterwards it doesn't work (still no wlan0 showing up anywhere).

---

