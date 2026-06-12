---
title: "netgear wg111t wirless asb adapter freezes ubuntu 8.04"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by joe9110 on 2008-07-05
hi guys im new to ubuntu and already love it to bits, at the moment im dual booting with win xp , but im going to just use ubuntu soon!

iv already installed ndiswrapper and got both the inf files working on it, but when i plug the usb in it will say hardware detected  and then 5 seconds later it will freeze the whole screen, no mouse movement, no keyboard, nothing . so i have to hard reboot which i know is not good.

so please help and thanks in advance

---

### Post by pytheas22 on 2008-07-05
Sometimes the Windows driver that you load into ndiswrapper just doesn't agree well.  It might help to try using a different version of the Windows driver.

Also, try unloading ndiswrapper before plugging in your device.  Enter in a terminal (Applications>Accessories menu):
```

sudo rmmod ndiswrapper
```

then plug in your device (it won't work at this point), and then type:
```

sudo modprobe ndiswrapper
```

Does it still freeze?

Otherwise, information about why the device is causing the freeze should be logged to dmesg (a Linux logging service).  Unfortunately dmesg gets lost after you reboot, so the trick here is to plug the device in, and then, before your system freezes, immediately save dmesg to a file that can be recovered later.

Try opening a terminal and type this command (all on one line), but don't press enter right away:
```

dmesg | tail > ~/Desktop/dmesg1.txt; sleep 1; dmesg | tail > ~/Desktop/dmesg2.txt; sleep 1; dmesg | tail > ~/Desktop/dmesg3.txt; sleep 1; dmesg | tail > ~/Desktop/dmesg4.txt
```

Then press enter while simultaneously plugging in your wireless adapter.  This will create files on your desktop containing information about the crash.  Depending on how many seconds the system remains stable before freezing, you'll get up to four different text files on your desktop.  After it crashes, reboot, open the dmesg files from you desktop and copy the contents of those files here and we can figure out what's wrong.

---

### Post by prshah on 2008-07-05
> **joe9110 said:**
> 
but when i plug the usb in it will say hardware detected  and then 5 seconds later it will freeze the whole screen,


Are you by any chance using the Win98 driver? This is a known problem with ver 1.0 of the NetGear windows 98 drivers. Change to XP, WinNT or Win2K drivers, or get the latest Windows 98 drivers from the NetGear site and use them.

Sorry I don't know how you can check the version of the .INF file you already have.

---

### Post by joe9110 on 2008-07-06
hey **pytheas22**
iv tried the first one and it has seemed to work because it has stopped freezing, but now it says under network settings "wireless connection" and apears to be connected and in network tools it has a drop down menu and in that it says "wireless interface (wlan0) it aslo says "wireless interface (wlan0:avahi)"
when i select "wireless interface (wlan0:avahi)" it says under interface inormation : "multicast: enabled" and also under link speed it says "108 mbps" and under state it says "active" 
but yet when i go on to the internet it says **"address not found"**

please help
thanks for your support and thanks in advance

---

### Post by joe9110 on 2008-07-06
heya 
just after i posted the comment before i plugged in my usb adapter and it froze so i rebooted and this time i did the 2nd thing u said to do and this is what it said 
**_no.1_**
[   68.637105] Bluetooth: HCI device and connection manager initialized

[   68.637113] Bluetooth: HCI socket layer initialized

[   68.688541] Bluetooth: L2CAP ver 2.9

[   68.688549] Bluetooth: L2CAP socket layer initialized

[   68.751285] Bluetooth: RFCOMM socket layer initialized

[   68.751311] Bluetooth: RFCOMM TTY layer initialized

[   68.751315] Bluetooth: RFCOMM ver 1.8

[   70.543105] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.

[   70.543123] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode

[   70.543158] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

**_no.2_**
[   68.751315] Bluetooth: RFCOMM ver 1.8

[   70.543105] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.

[   70.543123] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode

[   70.543158] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

[  160.150129] usb 5-6: new high speed USB device using ehci_hcd and address 4

[  160.283503] usb 5-6: configuration #1 chosen from 1 choice

[  160.349086] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)

[  160.524990] usb 5-6: reset high speed USB device using ehci_hcd and address 4

[  160.686490] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded

[  160.796100] usbcore: registered new interface driver ndiswrapper

**_no.3_**
[  160.283503] usb 5-6: configuration #1 chosen from 1 choice

[  160.349086] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)

[  160.524990] usb 5-6: reset high speed USB device using ehci_hcd and address 4

[  160.686490] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded

[  160.796100] usbcore: registered new interface driver ndiswrapper

[  161.058957] usb 5-6: USB disconnect, address 4

[  161.329433] usb 5-6: new high speed USB device using ehci_hcd and address 5

[  161.462669] usb 5-6: configuration #1 chosen from 1 choice

[  161.625293] usb 5-6: reset high speed USB device using ehci_hcd and address 5

[  161.789998] ndiswrapper: driver netwg11t (NETGEAR,01/07/2005,1.0.1.1007) loaded

**_no.4_**
[  160.686490] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded

[  160.796100] usbcore: registered new interface driver ndiswrapper

[  161.058957] usb 5-6: USB disconnect, address 4

[  161.329433] usb 5-6: new high speed USB device using ehci_hcd and address 5

[  161.462669] usb 5-6: configuration #1 chosen from 1 choice

[  161.625293] usb 5-6: reset high speed USB device using ehci_hcd and address 5

[  161.789998] ndiswrapper: driver netwg11t (NETGEAR,01/07/2005,1.0.1.1007) loaded

[  162.161059] wlan0: ethernet device 00:14:6c:0c:ca:0b using NDIS driver: netwg11t, version: 0x10000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 1385:4250.F.conf

[  162.161107] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA

[  162.176482] ADDRCONF(NETDEV_UP): wlan0: link is not ready

hope you can make sense of this  
thanks in advance

---

### Post by pytheas22 on 2008-07-06
Thanks for all that information.  I'm not positive, but it seems like ndiswrapper might be trying to load two different Windows drivers for the same device.  I think this because I see these two lines:

```
[ 160.686490] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded
[ 161.789998] ndiswrapper: driver netwg11t (NETGEAR,01/07/2005,1.0.1.1007) loaded
```

This might be ok, but I don't think it is; I don't think ndiswrapper should be trying to load two different drivers at the same time.  Otherwise, dmesg doesn't mention any errors.

Do you remember installing more than one Windows driver into ndiswrapper?  What does:
```

ndiswapper -l
```

say?

Also, if you type:
```

ndiswrapper-buginfo
```

(I just discovered this on my computer) you should be brought through a trouble-shooting session for ndiswrapper.  Please try that and see if it sheds light on anything.

---

### Post by joe9110 on 2008-07-12
hi 
im trying to attach a pic of what it says when i type in that command in terminal but it comes up with a server error ?

sorry i havent posted a comment in a while i have just formatted my computer and installed ubuntu all again

thanks for the support

---

### Post by joe9110 on 2008-07-12
hi 
just managed to attach the pic of the drivers in ndiswrapper

thanks in advance
_________________________________________________________________

In a world without walls, who needs windows?

---

### Post by pytheas22 on 2008-07-13
Thanks for the picture.  First of all, was your wireless device plugged in at the time you took the picture?  Because you should be seeing a message that says, "Hardware Present: Yes," but yours say, "No."  If you just didn't have the card plugged in at the time, though, then that explains it.

The second question is did you install those two drivers, atfmwdl and netwg11t, separately, or do you remember installing only one driver?  Normally that screen would only show one driver listed.

You could try removing one of the drivers (using the button on the right) to see if it helps.  If it doesn't, try removing the second driver and reinstalling the first one.  As I said earlier, your system messages show ndiswrapper trying to load both Windows drivers at the same time, and I don't think it's supposed to be doing that, which explains the crashes.

There could also be something else going on here, though, so if removing one of the drivers doesn't help, we can look at some other things.  Please let me know.

---

### Post by joe9110 on 2008-07-18
hi 
it wasnt plugged in when i took the pic 
i tried removing the atfmwdl and still it froze so i removed the netwg11t and installed the atfmwdl one,, still no luck.
i installed both drivers at the same time .

thx 4 you help 
_________________________________________________________________

in a world without walls,, who needs windows

---

### Post by pytheas22 on 2008-07-20
Why did you install both drivers at the same time?  You should need only one, as far as I know.  You could try purging and reinstalling ndiswrapper:
```

sudo apt-get remove --purge ndiswrapper*
sudo apt-get install ndiswrapper* ndisgtk
```

Then install just one Windows driver and see if it helps.

Otherwise, again, trying to use a different version of the Windows drivers might make a difference.

It may also be useful to see your system log.  If you run this command:
```

cat /var/log/syslog.0 > ~/Desktop.syslog
```

you'll get a text file on your desktop called "syslog."  If you post it here, maybe someone can make something of it.  The dmesg output above contains the same stuff as it pertains to ndiswrapper, but syslog will provide a bigger picture of your system, which may be useful in figuring out if something else is going wrong.

---

### Post by joe9110 on 2008-09-09
hi to everyone 

thank you so much for your help and support on this problem.

i have finaly resolved my problem by just wiring up to my bedroom from the office with cat 5.

and to anyone thats intrested im only 13 years old.

thanks to every one for there help

---

