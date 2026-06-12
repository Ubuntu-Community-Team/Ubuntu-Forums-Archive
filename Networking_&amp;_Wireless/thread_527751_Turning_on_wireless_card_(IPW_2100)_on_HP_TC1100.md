---
title: "Turning on wireless card (IPW 2100) on HP TC1100?"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by Ubuntiac on 2007-08-17
Howdy All,

I almost guaranteed know what the problem is, just not how to fix it. I'm pretty sure **the problem is that the wireless card is turned off** because:

[LIST=1]
[*]kwireless pro says it's turned off
[*]I remember turning it off way back in my Window$ days just before my li(nux)beration and haven't gotten it working since.
[/LIST]

Problem is that the TC1100 (A Hewlett Packard tablet PC) doesn't seem to offer any switch or keyboard combination to turn the wireless modem back on! I've tried Fn with all the F keys. None of the keys have a wireless icon. They only gave you the M$ software in the "Q" menu as far as I can see, which doesn't help as I've long since thrown my old XP CD gleefully into landfill.

For the record:
[LIST=1]
[*]I'm using _Kubuntu Gutsy H4_ (although I've had this problem since Dapper)
[*]Eth3 (wireless) is _enabled_ in System Settings->Network Settings
[*]Network manager shows no wireless devices / options
[/LIST]

**So... anyone know how to turn my intel wireless IPW 2100 modem on?**

Heres my iwconfig -a:
```
eth2      Link encap:Ethernet  HWaddr 00:0B:CD:AD:42:2C
          inet addr:72.45.118.108  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fead:422c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:66889569 (63.7 MB)  TX bytes:4312087 (4.1 MB)
          Interrupt:12

eth3      Link encap:Ethernet  HWaddr 00:0C:F1:01:12:22
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:15 Base address:0x2000 Memory:e0002000-e0002fff

eth3:avah Link encap:Ethernet  HWaddr 00:0C:F1:01:12:22
          inet addr:169.254.2.228  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:15 Base address:0x2000 Memory:e0002000-e0002fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

and my iwconfig:```

lo        no wireless extensions.

eth2      no wireless extensions.

eth3      unassociated  ESSID:"belkin54g"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:off
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Thanks again for you generous help! Now I go to see if I can find any really noob questions I can answer to balance my forum karma... ;)

---

### Post by noob12 on 2007-08-17
To confirm your hypothesis

Post the output of these
```

ls -l /sys/class/net/eth3/device/rf_kill
cat /sys/class/net/eth3/device/rf_kill

```

0 means on
1 means off, by SW (may be able to control by writing to this file)
2 means off by HW (need to toggle either a hard switch or some other internal control using a driver)

If you're lucky you'll find 0, or 1 and that the file is writable.  Otherwise,  if you find 2, you need to find the means to turn it on.  Check the BIOS to see if you can somehow turn it on or perhaps reset the machine to a factory initial state where it is ON.

Do
```

ls -l /proc/acpi/wmi/WMID/wlan

```
to see if this exists and is writable by root.   I don't know if it will on Ubuntu with your hardware. If this file does exist  and is writable by root do the following to turn on the wireless.  **Only do this if the file above already exists and is writable by root.**
```

sudo /etc/init.d/networking stop
sudo modprobe -r ipw2100
echo "on" | sudo tee /proc/acpi/wmi/WMID/wlan
sudo modprobe ipw2100
sudo /etc/init.d/networking start

```

Most of this is just in order to unload and reload the ipw2100 driver which I think will only check power state on load.  The critical thing is the line in the middle writing to the control file.  If this works, it's reported to be persistent on your laptop.  So you may not need to write to the control file each time you boot.  If you don't find that file, we need to look for the driver source that would provide that control interface.  Such a driver is apparently distributed on some other linux distros (google for it).  That could be a long adventure.  You could also consider an external USB wireless and get that working.

Let me know how things go.

---

### Post by Ubuntiac on 2007-08-17
ok,

Just before you posted I just tried pretty much the same thing from here:
[http://math.bu.edu/people/kayeats/computers/tc1100.html](http://math.bu.edu/people/kayeats/computers/tc1100.html)

Now:

```
ls -l /sys/class/net/eth3/device/rf_kill
```
gives:
-rw-r--r-- 1 root root 4096 2007-08-17 16:50 /sys/class/net/eth3/device/rf_kill

```
 cat /sys/class/net/eth3/device/rf_kill
```
returns:
0 - so far so good...

```
sudo /etc/init.d/networking stop
sudo modprobe -r ipw2100
echo "on" | sudo tee /proc/acpi/wmi/WMID/wlan
sudo modprobe ipw2100
sudo /etc/init.d/networking start
```

Seems fine. Now when I restart, the wireless light comes on during the kubuntu splash.

iwconfig gives (note the tx-power):
```

eth3      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Only thing is that kirelessprotools still says "eth3 is powered off" and network manager doesn't show any wireless options, but I think that may be because I'm just not in range of any wireless networks at the moment. I'll post back as soon as I'm back in range.

Thanks for the quick reply! I've been trying to figure this out for months!

---

### Post by noob12 on 2007-08-17
Yes, now that your txpower no longer shows off but a signal, I think your radio is on.  And the driver thinks it is if the rf_kill shows 0.  Try an **iwlist scan** when you're near any wireless signals.

I am not familiar with kwirelesstools.  I don't use it.  It may be looking at the wrong state control file, check **cat /sys/class/net/eth3/device/power/state** perhaps.  Try writing a zero into that if it is wrong.

---

### Post by Ubuntiac on 2008-01-17
Fixed! The card *was* off and just needed to be turned back on with:
> 
modprobe tc1100-wmi
echo "on" > /proc/acpi/wmi/WMID/wlan

You can also turn it off (for plane flights, longer battery life etc) with:
> echo "off" > /proc/acpi/wmi/WMID/wlan

---

### Post by opusIV on 2008-02-26
I want to thank you for posting that tc1100 info. I thought that I wouldn't ever get any wireless going.  I now have a wireless card working the in the PCMCIA slot - thanks to your  help.  I have to learn to "officially" thank you - if you could direct me to that feature of the forum I will do so.

Regards,

opusIV

---

