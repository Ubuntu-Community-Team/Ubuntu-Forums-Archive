---
title: "Need help with zd1211 on powerpc"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by jomny on 2007-03-16
Ive got an older ibook that Ive been trying to get online with little luck. At first I bought a usb adapter that I thought was zd1211 but it turned out to be rt73. Ive since gotten an adapter that is zd1211, Im verifying this with the output for when I use lsusb command which gives me:

Bus 002 Device 006: ID 0ace:1215 ZyDAS
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Ive followed the tutorial from here: [http://ubuntuforums.org/showthread.php?t=296310&highlight=zd1211+powerpc](http://ubuntuforums.org/showthread.php?t=296310&highlight=zd1211+powerpc) with some success. I get a number of warnings when I compile the driver files (Ive tried  32, 52, 59, 77, 80, and 85 so far) but Ive gotten the zd1211.ko file each time with no errors. 

That being said, the driver seems to install ok, but when I plug the adapter in instead of getting the output Im supposed to from the driver recognising the device, I just get 

[ 1085.299297] usb 2-1: new full speed USB device using ohci_hcd and address 3

or something to that effect. Heres what I get after I installed r59 just now:

[ 1580.749136] zd1211 - [http://zd1211.ath.cx/](http://zd1211.ath.cx/)
[ 1580.749172] Based on [www.zydas.com.tw](www.zydas.com.tw) driver version 2.4.0.0
[ 1580.751775] usbcore: registered new driver zd1211
[ 1672.521665] usb 2-1: new full speed USB device using ohci_hcd and address 4

and thats it. Ive verified that the adapter is working by installing it sucessfully on a windows machine so I know its an issue with the way Ive got things working on my ibook. Im new to the whole linux thing so it quite possible that I messed something up along the way. Any help would be greatly appreciated, Id really like to get this laptop online.

---

### Post by Darkhack on 2007-03-16
Make sure that you've set B=1 in those instructions from the other thread.  That is a zd1211B device you have there.  Secondly, that message should be just fine about using the new highspeed USB device.  Just try using 'ifconfig' and 'iwconfig' to get online.  I have the same chipset and it starts up with the interface 'eth1'.  Assuming you are on an unencrypted network...

sudo ifconfig eth1 up
sudo iwconfig eth1 essid YOUR_ESSID

You should be able to start browsing.  Try it with an unencrypted network first to verify that the driver works and then we can add security via WEP or WPA.

---

### Post by jomny on 2007-03-17
That did help, its probably a stupid question but how did you know it was a b device?

Anyway, while the adapter is being recognised by the driver Im not able to connect to anything. It seems that the adapter is coming up by itself, but even with the commands you listed Im not able to get any kind of connection. Im not really sure that things are working correctly as when I do an ifconfig I get the following:

wlan0     Link encap:Ethernet  HWaddr 00:02:72:5C:CF:7B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:237 dropped:0 overruns:0 frame:237
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Obviously no packets being transmitted and a lot of errors indicate somethings wrong, but thats about as much as I can figure out.

Ive tried using wlassistant to get things working but although it does detect the available networks, when I try to connect to any of the networks the attempt fails. Heres what a dmesg gets me after I connect the adapter in case it makes anything more apparent:

[  929.160789] ZD1211B - [http://zd1211.ath.cx/](http://zd1211.ath.cx/) - r85
[  929.160828] Based on [www.zydas.com.tw](www.zydas.com.tw) driver version 2.5.0.0
[  929.164463] usbcore: registered new driver zd1211b
[  948.954294] usb 2-1: new full speed USB device using ohci_hcd and address 2
[  949.342295] usb 2-1: reset full speed USB device using ohci_hcd and address 2[  949.545076] Release Ver = 4810
[  949.545107] zd1211:bulk out: wMaxPacketSize = 40
[  949.545118] zd1211:bulk in: wMaxPacketSize = 40
[  949.545129] zd1211:interrupt in: wMaxPacketSize = 40
[  949.545140] zd1211:interrupt in: int_interval = 1
[  949.545150] zd1211:bulk out: wMaxPacketSize = 40
[  949.545167] EEPORM Ver = 4810
[  949.561804] zd1211:USB Download Boot code success
[  949.570260] zd1211:MAC address = 00:02:72:5c:cf:7b
[  949.574268] zd1211:AddrEntryTable = f7c6
[  949.578262] zd1211:RF_Mode = 80000584
[  949.578277] PA type: 0
[  949.578285] Airoha AL2230S_RF
[  949.578815] zd1211:Pure B-Mode
[  949.934262] zd1211:AllowedChannel = 000007ff
[  949.938269] zd1211:LinkLEDn = 200
[  949.942270] AllowedChannel = 000107ff
[  949.942287] Region:48
[  950.554263] zd1205: (exit) zd1205_config, /usr/src/zd1211-driver-r85/src/zd1205.c line 2607
[  950.554818] zd1205: (exit) zd1205_init, /usr/src/zd1211-driver-r85/src/zd1205.c line 8582
[  951.390711] zd1205: (enter) zd1205_open, /usr/src/zd1211-driver-r85/src/zd1205.c line 4359
[  951.442840] zd1205: (exit) zd1205_open, /usr/src/zd1211-driver-r85/src/zd1205.c line 4442
[  951.444186] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  953.270807] zd1211:Pure B-Mode
[  953.950807] zd1211:Pure B-Mode
[  954.630807] zd1211:Pure B-Mode

Ive tried all the versions I did before (compiled with the B option) and none of them did any better, although with the older ones wlassistant doesnt detect any networks.

---

### Post by Darkhack on 2007-03-17
I knew it was a B device because lsusb provided the device ID of "0ace:1215" which you had in your first post.  The zd1211 website has a list of compatible hardware and shows this ID as being a B device... [http://zd1211.ath.cx/](http://zd1211.ath.cx/).  I also have the same device which helps too.

I would double check to make sure that you've followed the proper instructions for the B device and not the regular ones.  Also, I found a slight error in that "How To".  On step 11, it is installing the wrong driver for B devices.  Try this...

**sudo modprobe -r zd1211**    (this will remove the regular zd1211 driver)
**sudo depmod sudo modprobe -v zd1211b**    (installs the proper driver for B devices)

Notice the final 'b' on the driver name.  Step 11 failed to mention this.  When you have a B device it generates zd1211b.ko instead of zd1211.ko for the kernel module.

Once you've done this, try using ifconfig and iwconfig again.  If possible, show the output of both and let me know if iwconfig will "hold" the essid.  Sometimes with buggy drivers iwconfig will show your essid as "off/any" even if you've tried to set it.

One last thing.  I have good news for you.  The upcoming feisty release will have a new driver called "zd1211rw" (rewrite) which is a single driver that works for both standard and B devices.  Better yet, it is included in the kernel and should auto-detect your device.

---

### Post by jomny on 2007-03-17
I actually figured the bit about registering the zd1211b.ko driver myself before, so unfortunately the former problems still stand.  Here is the output of an ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:30:65:FB:0C:74
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:65ff:fefb:c74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:597 errors:0 dropped:0 overruns:0 frame:0
          TX packets:424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:632000 (617.1 KiB)  TX bytes:45473 (44.4 KiB)
          Interrupt:41 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:02:72:5C:CF:7B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:396 dropped:0 overruns:0 frame:396
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Here is an iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"linksys"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=28/100  Signal level=18/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:521
          Tx excessive retries:128440  Invalid misc:0   Missed beacon:0

In case its important, the device comes up by itself when I plug it in, so I dont have to do the ifconfig wlan0 up bit. I do have to assign the essid each time though, so when you look at this I did do the iwconfig wlan0 essid linksys command before getting the output to these commands.

---

### Post by Darkhack on 2007-03-17
Assuming you've removed all encryption it should work.  Post your output from "less /etc/network/interfaces".  Look for a line with wlan0 in there since that appears to be the interface it is using.  If you are using DHCP then it should look something like this...

auto wlan0
iface wlan0 inet dhcp

If it is not there, then add it.  Then try...

sudo killall dhclient  (to shutdown any currently running DHCP clients)
sudo killall dhclient3   (sometimes distros append the 3 to the name)
sudo dhclient  (to restart the client)

It looks like the interface is working and it just needs to be properly configured now, which is a step in the right direction.

---

### Post by jomny on 2007-03-18
Unfortunately still no luck. My /etc/network/interfaces has a sectionfor wlan0 just like the one you posted so Im pretty sure thats not it. Im thinking its not really working correctly, as the ifconfig is showing no packets sent or recieved but a lot of errors (the number of errors goes up the longer the adapter is connected). Maybe there is  some further tweaking that needs to be done?

---

### Post by jomny on 2007-03-18
Giving this a bump since it has fallen fast and maybe someone besides Darkhack (who is the man for giving me so much help) could offer some new info?

---

### Post by jomny on 2007-03-20
Bump for some help.

---

### Post by stoof on 2007-04-01
Ive think i have the same problem as you, I get the module to load and I can scan for networks "iwlist scan" but i wount be able to get an ip when i run dhclient. Cant figure out whats wrong, I have tried both ndiswrapper and the zd1211rw module, all without luck!

---

