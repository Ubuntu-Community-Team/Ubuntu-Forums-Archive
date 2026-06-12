---
title: "I am struggling to install Ethernet Adapter Drivers in my Ubuntu 20.04"
date: 2022-01-14
forum: Networking &amp; Wireless
---

### Post by xaydkibriya on 2022-01-14
Can someone please help me install these uGreen Ethernet Drivers in my Ubuntu so I can get connect to the Internet.

I have purchased an Ethernet Adapter (UGREEN USB C TO Ethernet Adapter Gigabit) from Amazon which is compatible with Linux.

However, I am struggling a lot, just to follow the instructions to install the Drivers as mentioned in the ReadMe file.

I have invested about 5 hours and still no luck.

[ATTACH=CONFIG]289801[/ATTACH][ATTACH=CONFIG]289802[/ATTACH]

---

### Post by Holger_Gehrke on 2022-01-14
Have you tried just connecting the device ? The driver module 'ax88179_178a.ko' (which this readme tells you to compile from source) already exists on my system in various places under '/lib/modules/' (a directory which has one subdirectory per kernel version currently installed ...). It *should* just work ... This driver is probably meant for people who are running a version of Linux so old it doesn't include this driver.

Holger

---

### Post by Tadaen_Sylvermane on 2022-01-15
Was going to ask the same thing. With your low beans count I can only imagine you are fairly new to linux? Possibly this forum. At any rate the idea of downloading and manually installing drivers is a rare occurence for linux stuff. Most of the time the driver is already in place.

---

### Post by Innernet on 2022-01-16
Not an expert but will place my spoon in your plate.

Used similar gadgets for years as I do not use WiFi; only wired ethernet and never had to setup nor tweak a thing to make Ubuntu or Chromebooks to work immediately on the internet.  Retry with no WiFi settings.

---

### Post by xaydkibriya on 2022-01-18
Hello. I did try to connect the device and it is not detected. No internet. (Internet Cable/Connection and Device works fine because I have Dual Boot Windows and its just plug and play there). 

I'm new to this, which is why I installed it as a Dual Boot. but I'm technically sound, I wanted to get a grip on Linux. I tried contacting the Support Team for the uGreen but its not helping. I'm just stuck with no Internet.

---

### Post by xaydkibriya on 2022-01-18
[LIST]
[*]That is right, I'm totally new to this. I've been playing around with it since 2 weeks but this is the first time I'm installing the drivers. It would be helpful if you could help me past this thing.
[/LIST]

---

### Post by xaydkibriya on 2022-01-18
I guess I need to figure the difference between Temporary Directory and Current Directory first.

Can anyone post step-by-step process in layman terms?

Thank you in advance.

---

### Post by SeijiSensei on 2022-01-18
Try this. With the device attached, open a terminal and run

```
sudo modprobe ax88179
```

If that doesn't work, try

```
sudo modprobe ax88179_178a
```

The driver comes with 20.04 and resides in /usr/lib/modules/[KERNEL_VERSION]/kernel/drivers/net/usb/.  modprobe should try to load it.  See if it throws any errors.

A quick google search for "ubuntu packages ax88179 20.04" brings up a lot of articles that might help.

---

### Post by TheFu on 2022-01-18
> **Holger_Gehrke said:**
> Have you tried just connecting the device ? The driver module 'ax88179_178a.ko' (which this readme tells you to compile from source) already exists on my system in various places under '/lib/modules/' (a directory which has one subdirectory per kernel version currently installed ...). It *should* just work ... This driver is probably meant for people who are running a version of Linux so old it doesn't include this driver.

Holger

If that is the correct driver for the device, I can confirm that it works - plug-n-play  - with Ubuntu 18.04. No extra effort necessary. Just plug it in and wait 5 seconds for the connection.  I use a USB3 -to- GigE adapter based on that driver many times a week.

```
$ lsmod |grep ax88
ax88179_178a           24576  0
usbnet                 45056  1 ax88179_178a
mii                    16384  2 usbnet,ax88179_178a

```
That's pulled right now.  I never grabbed and code or compiled the driver in the years I've been using it. This is the 3rd laptop I've used it with.

I haven't tried it with 20.04, so I don't know about that, but I do see the files and module available on a 20.04 system here. It is a virtual machine, so not really worth attempting the USB connection. Sorry.

I do know that with prior Ubuntu Server distros, the driver **is not** provided by default.  Seems the server NIC packing guys decided that USB Network adapters wouldn't be used.

I have no explanation for why it isn't working in your system, except that the device may not really use that driver (doesn't have that chip)?
Can you run **lsusb** ?  When I run it, among other outputs, it shows this:
```
$ lsusb
Bus 002 Device 003: ID [COLOR="#FF0000"]0b95:1790[/COLOR] ASIX Electronics Corp. AX88179 Gigabit Ethernet
...
```
There is just a few lines of output.
The "0b95:1790" is a device identifier that we can look up.  Yours will likely be different since mine is 3+ yrs old.

---

### Post by xaydkibriya on 2022-01-19
I do see the ethernet adapter when i run lsusb. here's the output: Bus 002 Device 003: ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet. 

It is not a VM. 

May be I am just not able to follow the guide for installing the drivers. I can send you screenshots of every command you ask me to run. if that helps.

This is my first time installing drivers on Linux so I'd appreciate the help.

---

### Post by xaydkibriya on 2022-01-19
with the first command the output is: modprobe: FATAL: Module ax88179 not found in directory /lib/modules/5.13.0-27-generic
and with the second command there isn't one. 

Google search is coming back with a lot of results but not one single video. If only there was a video for it.

---

### Post by TheFu on 2022-01-20
On 5.4, I have /lib/modules/5.4.0-94-generic/kernel/drivers/net/usb/ax88179_178a.ko
On 5.11, I have /lib/modules/5.11.20-generic/kernel/drivers/net/usb/ax88179_178a.ko
I don't have 5.13.

These are all pre-installed. I didn't need to do anything. When the device is connected, it is automatically loaded into the **lsmod** list. All that remains is to configure the adapter with IP, gateway, netmask. That's where I think you are.

a) not interested in seeing pictures/images.  Text only.  You can run commands and redirect the output to a file.  Copy that file to flash storage, then pull the file form the storage and copy/paste it here.  Best to be complete with the exact command AND the exact output as shown in a terminal.

```
$ echo "some command" | tee -a /tmp/output
$ some command | tee -a /tmp/output
```

That will append the command and the output to a file. Copy that file somewhere that you can access when connected back here. Also, please post using 'code-tags'.  Anything run in a terminal should be posted wrapped in code tags here.

Images are a problem for people with poor eyesight. Screen readers don't know what it is and the result is usually the wrong size or out of focus.  We cannot easily copy/paste important parts to point out issues and errors.
If you want more on this: [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) is a very knowledge-dense document. Re-reading it annually will get more knowledge yearly. It has a good section on file redirection too.

---

### Post by slickymaster on 2022-01-20
*Thread moved to **Networking & Wireless**.*

---

### Post by Holger_Gehrke on 2022-01-20
I did a quick check: the module in question is in the package linux-modules-extra-{Kernel-Version-Number}-generic. According to packages.ubuntu.com it is part of this package for version 5.13.0-19 but for some reason isn't in 5.13.0-27. The whole 'drivers/net/usb' part of the directory hierarchy seems to not be in there. I don't know if that was intentional and there's a new package with additional modules or if these where left out for a reason or if it's simply an error. Additionally for 5.15.0-17 (one Kernel for what's going to become 22.04) the module seems to be back.

You might want to do a 'find /lib/modules -name ax88179_178a.ko' to see whether you've got an older kernel which has the module. If you do, you can try to boot that from the grub menu.

Holger

---

### Post by TheFu on 2022-01-20
> **Holger_Gehrke said:**
> I did a quick check: the module in question is in the package linux-modules-extra-{Kernel-Version-Number}-generic. According to packages.ubuntu.com it is part of this package for version 5.13.0-19 but for some reason isn't in 5.13.0-27. The whole 'drivers/net/usb' part of the directory hierarchy seems to not be in there. I don't know if that was intentional and there's a new package with additional modules or if these where left out for a reason or if it's simply an error. Additionally for 5.15.0-17 (one Kernel for what's going to become 22.04) the module seems to be back.

You might want to do a 'find /lib/modules -name ax88179_178a.ko' to see whether you've got an older kernel which has the module. If you do, you can try to boot that from the grub menu.

Holger

That explains a bunch. Likely a human mistake/oversight of some sort.  Might be easiest to just boot the older kernel and redo a patch run (update/upgrade) which should get the latest kernel and drivers.

---

### Post by chili555 on 2022-01-20
> **xaydkibriya said:**
> with the first command the output is: modprobe: FATAL: Module ax88179 not found in directory /lib/modules/5.13.0-27-generic
and with the second command there isn't one. 

Google search is coming back with a lot of results but not one single video. If only there was a video for it.The command should be: 

```
sudo modprobe ax88179_178a
```If it loads without error, then let's see:

```
ip addr show
sudo dmesg | grep ax88

```If there is an error, let's see:

```
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
```

---

### Post by xaydkibriya on 2022-01-23
Please find the attached screenshots. I have checked the device status, it is being detected. however it is still not working. Can anyone tell me why am I not seeing "Wired Connections" in settings?[

---

### Post by chili555 on 2022-01-23
Your screenshots are very difficult to read. Since you have a connected wireless device, please copy and paste the text in your reply and enclose it in code blocks using the **#** button at the top like this:

```
some code here
```

We are interested in why your ethernet appears to be unmanaged. Please show us:

```
cat /etc/network/interfaces
cat /etc/netplan/*.yaml
sudo dmesg | grep enx
```

---

### Post by xaydkibriya on 2022-01-23
Please find the outputs below:

```
nmcli d
```

**Output:**
DEVICE             TYPE      STATE         CONNECTION 
wlp0s20f3          wifi      disconnected  --         
enx000ec649eae4    ethernet  unmanaged     --         
lo                 loopback  unmanaged     --         
p2p-dev-wlp0s20f3  wifi-p2p  unmanaged     --     
    

```
lshw -c network
```
[B]
Output:[/B]
  *-network
       description: Wireless interface
       product: Cannon Point-LP CNVi [Wireless-AC]
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlp0s20f3
       version: 30
       serial: 90:78:41:9c:a0:81
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.13.0-27-generic firmware=46.4d093a30.0 9000-pu-b0-jf-b0- latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:a1218000-a121bfff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       bus info: usb@2:3
       logical name: enx000ec649eae4
       serial: 00:0e:c6:49:ea:e4
       size: 10Mbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ax88179_178a driverversion=5.13.0-27-generic duplex=half link=no multicast=yes port=MII speed=10Mbit/s



```
lsusb
```[B]
Output:[/B]
Bus 002 Device 003: ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b5c5 Chicony Electronics Co., Ltd HD WebCam
Bus 001 Device 003: ID 1c7a:0570 LighTuning Technology Inc. EgisTec Touch Fingerprint Sensor
Bus 001 Device 011: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




I tried enabling/disabling the network settings. Basically, today, I have tried doing everything that the forums asked me to. I do not know where am i going wrong. Please help. thanks.

P.S.: I hope I have written the text in a way you could understand better.

---

### Post by chili555 on 2022-01-23
> 
 I do not know where am i going wrong. Please help. Please post the result of the commands that I requested above.

> I hope I have written the text in a way you could understand better.Yes, indeed. Thanks.

---

### Post by xaydkibriya on 2022-01-24
I just spent about 20 mins creating a document with commands and outputs and when I hit post, there was some issue with the token and all of it was gone. Good lord! I will have to type everything again.

---

### Post by xaydkibriya on 2022-01-24
Please find the attached output files.

---

### Post by xaydkibriya on 2022-01-24
I have not been able to post due to the output being too large.

---

### Post by chili555 on 2022-01-24
How about the last two?

```
cat /etc/network/interfaces
sudo dmesg | grep enx
```If it is more convenient, paste the results here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by xaydkibriya on 2022-01-24
Here is snippet from:
```
sudo dmesg
```

[B]Partial output since the output was too large:
[/B]
```
62.159174] usb 2-3: Product: AX88179A
[   62.159178] usb 2-3: Manufacturer: ASIX
[   62.159181] usb 2-3: SerialNumber: 0000000000066E
[   62.290574] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[   62.301142] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[   62.513223] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[   62.628522] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x0006: -32
[   62.628536] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): invalid MAC address, using random
[   62.639094] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0006: -32
[   62.650063] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0005: -32
[   62.659076] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[   62.670946] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[   62.682756] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[   62.693054] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[   62.703040] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[   62.712917] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[   62.723106] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[   62.735036] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x0001: -32
[   62.745750] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[   62.757056] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x001f: -32
[   62.766163] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0019: -32
[   62.776904] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x001f: -32
[   62.788785] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[   62.799048] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[   62.809712] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[   62.819971] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x000e: -32
[   62.830144] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[   62.842044] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[   62.852560] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[   62.862877] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[   62.873994] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x0000: -32
[   62.874158] ax88179_178a 2-3:2.0 eth0: register 'ax88179_178a' at usb-0000:00:14.0-3, ASIX AX88179 USB 3.0 Gigabit Ethernet, ba:ee:ff:2a:de:fc
[   63.010613] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[   63.020961] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[   63.232915] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[   63.346685] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to read reg index 0x0006: -32
[   63.346708] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): invalid MAC address, using random
[   63.356994] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0006: -32
[   63.367440] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0005: -32
[   63.379437] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[   63.389860] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[   63.400606] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[   63.410903] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[   63.421546] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[   63.433818] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[   63.444015] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[   63.454533] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to read reg index 0x0001: -32
[   63.464978] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[   63.475368] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x001f: -32
[   63.487786] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0019: -32
[   63.497964] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x001f: -32
[   63.508476] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[   63.519088] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[   63.529429] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[   63.541171] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to read reg index 0x000e: -32
[   63.551628] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[   63.561961] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[   63.572391] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[   63.582813] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[   63.594513] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to read reg index 0x0000: -32
[   63.595303] ax88179_178a 2-3:2.1 eth1: register 'ax88179_178a' at usb-0000:00:14.0-3, ASIX AX88179 USB 3.0 Gigabit Ethernet, 7e:35:b5:fd:f5:89
[   63.638089] usbcore: registered new interface driver ax88179_178a
[   63.641353] usbcore: registered new interface driver cdc_ether
[   63.644063] usbcore: registered new interface driver cdc_ncm
[   63.646482] usbcore: registered new interface driver cdc_wdm
[   63.648722] usbcore: registered new interface driver cdc_mbim
[   64.912348] usb 2-3: USB disconnect, device number 2
[   64.912385] ax88179_178a 2-3:2.0 eth0: unregister 'ax88179_178a' usb-0000:00:14.0-3, ASIX AX88179 USB 3.0 Gigabit Ethernet
[   64.938714] ax88179_178a 2-3:2.0 eth0 (unregistered): Failed to write reg index 0x0002: -19
[   64.938719] ax88179_178a 2-3:2.0 eth0 (unregistered): Failed to write reg index 0x0001: -19
[   64.938721] ax88179_178a 2-3:2.0 eth0 (unregistered): Failed to write reg index 0x0002: -19
[   64.938789] ax88179_178a 2-3:2.1 eth1: unregister 'ax88179_178a' usb-0000:00:14.0-3, ASIX AX88179 USB 3.0 Gigabit Ethernet
[   64.970828] ax88179_178a 2-3:2.1 eth1 (unregistered): Failed to write reg index 0x0002: -19
[   64.970845] ax88179_178a 2-3:2.1 eth1 (unregistered): Failed to write reg index 0x0001: -19
[   64.970853] ax88179_178a 2-3:2.1 eth1 (unregistered): Failed to write reg index 0x0002: -19
[   65.400118] usb 2-3: new SuperSpeed USB device number 3 using xhci_hcd
[   65.574476] usb 2-3: New USB device found, idVendor=0b95, idProduct=1790, bcdDevice= 2.00
[   65.574483] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   65.574485] usb 2-3: Product: AX88179A
[   65.574487] usb 2-3: Manufacturer: ASIX
[   65.574489] usb 2-3: SerialNumber: 0000000000066E
[   66.262010] ax88179_178a 2-3:1.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x0040: -32
[   66.572387] ax88179_178a 2-3:1.0 eth0: register 'ax88179_178a' at usb-0000:00:14.0-3, ASIX AX88179 USB 3.0 Gigabit Ethernet, 00:0e:c6:49:ea:e4
[   66.630984] ax88179_178a 2-3:1.0 enx000ec649eae4: renamed from eth0
[ 7395.655390] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
[ 7395.658371] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
[ 9026.233568] usb 2-3: USB disconnect, device number 3
[ 9026.233739] ax88179_178a 2-3:1.0 enx000ec649eae4: unregister 'ax88179_178a' usb-0000:00:14.0-3, ASIX AX88179 USB 3.0 Gigabit Ethernet
[ 9026.256921] ax88179_178a 2-3:1.0 enx000ec649eae4 (unregistered): Failed to write reg index 0x0002: -19
[ 9026.256927] ax88179_178a 2-3:1.0 enx000ec649eae4 (unregistered): Failed to write reg index 0x0001: -19
[ 9026.256930] ax88179_178a 2-3:1.0 enx000ec649eae4 (unregistered): Failed to write reg index 0x0002: -19
[ 9034.633910] usb 1-3: new high-speed USB device number 6 using xhci_hcd
[ 9034.791866] usb 1-3: New USB device found, idVendor=05ac, idProduct=12a8, bcdDevice=11.02
[ 9034.791880] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 9034.791885] usb 1-3: Product: iPhone
[ 9034.791889] usb 1-3: Manufacturer: Apple Inc.
[ 9034.791892] usb 1-3: SerialNumber: 00008020000B654E3C92002E
[ 9034.833499] usbcore: registered new device driver apple-mfi-fastcharge
[ 9034.874283] ipheth 1-3:4.2: Apple iPhone USB Ethernet device attached
[ 9034.874423] usbcore: registered new interface driver ipheth
[ 9034.882384] ipheth 1-3:4.2 enxc2a600b8c9bb: renamed from eth0
[22068.019954] apple-mfi-fastcharge 1-3: USB disconnect, device number 6
[22068.062147] ipheth 1-3:4.2: Apple iPhone USB Ethernet now disconnected
[26154.699170] usb 2-3: new SuperSpeed USB device number 4 using xhci_hcd
[26154.985845] usb 2-3: New USB device found, idVendor=0b95, idProduct=1790, bcdDevice= 2.00
[26154.985859] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[26154.985864] usb 2-3: Product: AX88179A
[26154.985868] usb 2-3: Manufacturer: ASIX
[26154.985872] usb 2-3: SerialNumber: 0000000000066E
[26155.089304] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[26155.098780] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[26155.312357] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[26155.423250] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x0006: -32
[26155.423261] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): invalid MAC address, using random
[26155.433577] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0006: -32
[26155.443858] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0005: -32
[26155.455596] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[26155.466103] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[26155.476479] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[26155.486810] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[26155.497319] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[26155.509208] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[26155.519569] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[26155.530086] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x0001: -32
[26155.540765] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[26155.550828] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x001f: -32
[26155.562809] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0019: -32
[26155.573375] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x001f: -32
[26155.583666] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[26155.594221] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[26155.604994] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[26155.616196] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x000e: -32
[26155.627508] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[26155.637198] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[26155.647580] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[26155.658106] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[26155.671221] ax88179_178a 2-3:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x0000: -32
[26155.671384] ax88179_178a 2-3:2.0 eth0: register 'ax88179_178a' at usb-0000:00:14.0-3, ASIX AX88179 USB 3.0 Gigabit Ethernet, 0a:59:c1:da:3b:47
[26155.810246] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[26155.820582] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[26156.032325] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[26156.143403] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to read reg index 0x0006: -32
[26156.143431] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): invalid MAC address, using random
[26156.153741] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0006: -32
[26156.164252] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0005: -32
[26156.176227] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[26156.186544] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[26156.196913] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[26156.207315] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[26156.217650] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[26156.229570] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[26156.240284] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[26156.250675] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to read reg index 0x0001: -32
[26156.261258] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[26156.271635] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x001f: -32
[26156.283608] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0019: -32
[26156.294214] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x001f: -32
[26156.304533] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[26156.315250] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[26156.325611] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[26156.337541] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to read reg index 0x000e: -32
[26156.348226] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[26156.358593] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[26156.369297] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[26156.379682] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[26156.391449] ax88179_178a 2-3:2.1 (unnamed net_device) (uninitialized): Failed to read reg index 0x0000: -32
[26156.391907] ax88179_178a 2-3:2.1 eth1: register 'ax88179_178a' at usb-0000:00:14.0-3, ASIX AX88179 USB 3.0 Gigabit Ethernet, 1a:db:38:6b:56:28
[26157.707711] usb 2-3: USB disconnect, device number 4
[26157.707750] ax88179_178a 2-3:2.0 eth0: unregister 'ax88179_178a' usb-0000:00:14.0-3, ASIX AX88179 USB 3.0 Gigabit Ethernet
[26157.724605] ax88179_178a 2-3:2.0 eth0 (unregistered): Failed to write reg index 0x0002: -19
[26157.724610] ax88179_178a 2-3:2.0 eth0 (unregistered): Failed to write reg index 0x0001: -19
[26157.724611] ax88179_178a 2-3:2.0 eth0 (unregistered): Failed to write reg index 0x0002: -19
[26157.724681] ax88179_178a 2-3:2.1 eth1: unregister 'ax88179_178a' usb-0000:00:14.0-3, ASIX AX88179 USB 3.0 Gigabit Ethernet
[26157.772681] ax88179_178a 2-3:2.1 eth1 (unregistered): Failed to write reg index 0x0002: -19
[26157.772696] ax88179_178a 2-3:2.1 eth1 (unregistered): Failed to write reg index 0x0001: -19
[26157.772703] ax88179_178a 2-3:2.1 eth1 (unregistered): Failed to write reg index 0x0002: -19
[26158.194626] usb 2-3: new SuperSpeed USB device number 5 using xhci_hcd
[26158.368352] usb 2-3: New USB device found, idVendor=0b95, idProduct=1790, bcdDevice= 2.00
[26158.368356] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[26158.368358] usb 2-3: Product: AX88179A
[26158.368359] usb 2-3: Manufacturer: ASIX
[26158.368360] usb 2-3: SerialNumber: 0000000000066E
[26159.065770] ax88179_178a 2-3:1.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x0040: -32
[26159.376947] ax88179_178a 2-3:1.0 eth0: register 'ax88179_178a' at usb-0000:00:14.0-3, ASIX AX88179 USB 3.0 Gigabit Ethernet, 00:0e:c6:49:ea:e4
[26159.465021] ax88179_178a 2-3:1.0 enx000ec649eae4: renamed from eth0
[26303.321407] acer_wmi: Unknown function number - 8 - 0
```

---

### Post by xaydkibriya on 2022-01-24
> **chili555 said:**
> How about the last two?

```
cat /etc/network/interfaces
sudo dmesg | grep enx
```If it is more convenient, paste the results here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Sorry, I forgot to add that one last time.
the first come came as: ```
cat /etc/network/interfaces
```
zaid@ubuntu:~$ cat /etc/network/interfaces
cat: /etc/network/interfaces: No such file or directory

second one: ```
sudo dmesg | grep enx
```
[    9.065547] ax88179_178a 2-4:1.0 enx000ec649eae4: renamed from eth0
[    9.673569] ax88179_178a 2-4:1.0 enx000ec649eae4: Failed to read reg index 0x0040: -32
[   12.647595] ax88179_178a 2-4:1.0 enx000ec649eae4: ax88179 - Link status is: 1
[   12.851118] IPv6: ADDRCONF(NETDEV_CHANGE): enx000ec649eae4: link becomes ready

---

### Post by xaydkibriya on 2022-01-24
I turned my laptop On and i see "wired connection".

Finally, for the first time in 12 days, it started working. I literally have no idea what exactly happened as I have been doing everything you asked me plus the YouTube videos. So, its sad I wouldn't know which step/command did the job for me. 

BIG THANKS TO EACH ONE OF YOU. I HAVE LEARNED SO MUCH DURING THE TROUBLESHOOTING PROCESS. thank you again.

---

### Post by xaydkibriya on 2022-01-24
```
root@ubuntu:~# sudo apt update
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]         
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                                                 
Hit:4 [http://ppa.launchpad.net/micahflee/ppa/ubuntu](http://ppa.launchpad.net/micahflee/ppa/ubuntu) focal InRelease                                       
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security InRelease [114 kB]
Ign:6 [http://ppa.launchpad.net/qji/ax88179/ubuntu](http://ppa.launchpad.net/qji/ax88179/ubuntu) focal InRelease
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages [1,510 kB]
Hit:8 [http://ppa.launchpad.net/strukturag/libheif/ubuntu](http://ppa.launchpad.net/strukturag/libheif/ubuntu) focal InRelease
Err:9 [http://ppa.launchpad.net/qji/ax88179/ubuntu](http://ppa.launchpad.net/qji/ax88179/ubuntu) focal Release
  404  Not Found [IP: 91.189.95.85 80]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main i386 Packages [592 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [282 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages [894 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe i386 Packages [664 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [363 kB]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [944 B]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/main i386 Packages [363 kB]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/main amd64 Packages [1,178 kB]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [40.5 kB]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/main amd64 c-n-f Metadata [9,132 B]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/universe i386 Packages [532 kB]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/universe amd64 Packages [677 kB]
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [66.5 kB]
Get:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/universe amd64 c-n-f Metadata [13.0 kB]
Get:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Reading package lists... Done                                                 
[B]E: The repository 'http://ppa.launchpad.net/qji/ax88179/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
[/B]
```
Could this have been any reason why it wasn't working?

---

### Post by Cokaban on 2022-06-21
I may have the same problem. After some debugging, it looks like the problem is in the wrong order of kernel module loading. For some reason, the adapter seems to need both **ax88179_178a** and **cdc_mbim**, and **cdc_mbim** must be loaded first.

A solution that works until the next reboot is to execute:
```
sudo rmmod ax88179_178a
sudo modprobe cdc_mbim
sudo modprobe ax88179_178a  # optional

```

I do not know how to specify the dependency of  **ax88179_178a** on **cdc_mbim** to fix the problem permanently.

---

