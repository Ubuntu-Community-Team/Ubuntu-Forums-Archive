---
title: "[SOLVED] Marvell Libertas 8335"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by ninedice on 2008-10-22
I have followed the directions on [here]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29") and [here]("https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k") but when I iwconfig i get no wlan0. When i iwlist wlan0 scan, it says that it does not support scanning.
when i open up wicd, it says no wireless connections found, but i know i have one up, and i ndiswrapper shows that my card is installed and present. anyone know what i am talking about or am i speaking jibberish? help please?

---

### Post by caljohnsmith on 2008-10-22
Did you download and compile your own ndiswrapper (use the "make" and "make install" commands), or did you use the one in the repositories? Also, are you using the Windows XP wireless driver or the Vista one, and where did you get it? Please post:
```
ndiswrapper -l
ndiswrapper -v
sudo lshw -C network
ifconfig
iwconfig
dmesg | grep -ie ndis -ie wlan0 -ie error
```
And we can work from there. :)

---

### Post by ninedice on 2008-10-22
i used both ndiswrapper methods for different verions. and the drivers i got from a link from the second site i put in my previous post

```
ben@ninedice:~$ ndiswrapper -l
mrv8335 : driver installed
	device (11AB:1FAA) present
ben@ninedice:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-21-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-21-generic SMP mod_unload 
ben@ninedice:~$ sudo lshw -C network
[sudo] password for ben: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 9
       bus info: pci@0000:04:09.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
ben@ninedice:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:4b:07:27:bb  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::204:4bff:fe07:27bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:139126 (135.8 KB)  TX bytes:80335 (78.4 KB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2970 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:148500 (145.0 KB)  TX bytes:148500 (145.0 KB)

ben@ninedice:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ben@ninedice:~$ dmesg | grep -ie ndis -ie wlan0 -ie error
[   29.551519] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   50.287257] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   50.421787] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   50.421793] ndiswrapper (load_sys_files:210): couldn't prepare driver 'mrv8335'
[   50.422241] ndiswrapper (load_wrap_driver:112): couldn't load driver mrv8335; check system log for messages from 'loadndisdriver'
[   50.434046] usbcore: registered new interface driver ndiswrapper
ben@ninedice:~$ 

```

---

### Post by caljohnsmith on 2008-10-22
> **ninedice said:**
> 
```

ben@ninedice:~$ dmesg | grep -ie ndis -ie wlan0 -ie error
[   29.551519] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   50.287257] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[COLOR="Red"][   50.421787] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B[/COLOR]
[   50.421793] ndiswrapper (load_sys_files:210): couldn't prepare driver 'mrv8335'
[   50.422241] ndiswrapper (load_wrap_driver:112): couldn't load driver mrv8335; check system log for messages from 'loadndisdriver'
[   50.434046] usbcore: registered new interface driver ndiswrapper
ben@ninedice:~$ 

```
I think that error message above is most likely the crux of your problem; you're using 64-bit Hardy it looks like and yet your Windows driver is for 32-bit architectures. You'll have to find a 64-bit Windows driver it seems, otherwise you'll have to install Ubuntu 32-bit I think.

---

### Post by ninedice on 2008-10-22
hm.. that might solve my flash problems too.. 
thank you very much, getting x86 asap


is there a way to "case solved" this or something?

---

### Post by caljohnsmith on 2008-10-22
Just go to the top of the thread where there is a link for "thread tools" and you can select "marked as solved" from the drop-down list. Anyway, cheers and good luck. :)

---

