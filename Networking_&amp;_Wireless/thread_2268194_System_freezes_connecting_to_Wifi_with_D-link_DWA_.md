---
title: "System freezes connecting to Wifi with D-link DWA 142 USB network adapter."
date: 2015-03-06
forum: Networking &amp; Wireless
---

### Post by revblk on 2015-03-06
Hi folks,
I have a problem that I'm hoping you can help me with. Right off the bat, I should mention that the system mentioned below is Linux Mint 17 rather than Ubuntu, and while I know they are different, it's my understanding that Mint is an off-shoot of Ubuntu, so I'm hoping some of your expert knowledge will still apply. I did post in the Mint forums before coming here, but after 4 days and 61 views on the Mint forums, my request for help there hasn't garnered a single reply.
Here's the story:
Several days ago I set out to create a dual-boot Windows 7  64bit/Linux Mint 17 64bit machine. The OSes are on separate hard drives.  Mint is first in boot priority and OS selection is handled with grub,  as one would expect.

Everything went perfectly save for one problem: no wifi, though this was somewhat expected.
I  have an internal NIC, but this tower lives in a different room that  the router, making jacking into the router infeasible for long periods  of time. 
Under Windows 7, the solution has been to use a USB Network Adapter I had lying around. Specifically the [D-Link DWA-142]("http://www.dlink.com/uk/en/support/product/dwa-142-wireless-n-usb-2-0-adapter"). 
[This post (under USB DWA-142)]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink") led me to believe that this adapter would work, though the driver listed there (netmw245 (marvell)) is the WinXP 32bit driver. 

The "before you post" info for this forum requests that we first run 
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
and post the results, so before I list the steps I've taken so far, here is a link to the pastebin for the results of that script:
[http://pastebin.ubuntu.com/10553448/](http://pastebin.ubuntu.com/10553448/)
I'll admit that I'm having trouble entirely understanding this output.

Here are the steps I've taken so far:
I started googling the problem and these are the steps I took:
1. Download relevant drivers from D-Link. There were four: Windows XP/Win XP 64bit/Vista/Vista 64bit.
2. Install ndisgtk
3. Install drivers with ndisgtk
ndisgtk threw the following error: *modprobe:FATAL:Module ndiswrapper not found*
After  closing the error, the Vista drivers were marked as Invalid, but the XP  drivers were marked as Installed with Hardware Present.
4. more googling to find a solution to the modprobe:FATAL error.
5. Installed ndiswrapper-dkms
6. Ran
```
sudo modprobe ndiswrapper
```
in the terminal.
7. Reinstalled the drivers. Joy! Installing the XP 64  bit driver results in Wifi being an available in Network Settings, and  the computer sees locally broadcasting networks!
8. Try to connect to my local 2.4GHz b/g/n, auto channel, WPA2-PSK[AES] network.
Every  time I do this, the network settings shows that it is attempting to  connect, and then the entire system freezes. No Keyboard, no mouse;  nothing. 
9. Hard reboot.
10. Try to fiddle with the connection settings, same result.

Here is a list of the ndiswrapper related packages I have installed:
mintwifi
ndisgtk
ndiswrapper-dkms
ndiswrapper-common
ndiswrapper-utils-1.9

And here is the result of running
```
sudo /usr/lib/linuxmint/mintWifi/mintWifi.py
```

```
-------------------------
* I. scanning WIFI PCI devices...
-------------------------
* II. querying ndiswrapper...
netmw246 : driver installed
    device (07D1:3B10) present
-------------------------
* III. querying iwconfig...
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-------------------------
* IV. querying ifconfig...
eth0      Link encap:Ethernet  HWaddr 00:24:81:86:0c:1b  
          inet6 addr: fe80::224:81ff:fe86:c1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:116965896 (116.9 MB)  TX bytes:4650913 (4.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1798 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:180287 (180.2 KB)  TX bytes:180287 (180.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:9a:51:32:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

-------------------------
* V. querying DHCP...
-------------------------
* VI. querying nslookup google.com...
;; connection timed out; no servers could be reached
```

11. On a recommendation from a friend, I tried installing *linux-headers-generic* and *linux-firmware-nonfree*, but neither had an effect. 
12. I  also tried changing the encryption settings of the router from WPA2-PSK  [AES] to WPA-PSK [TKIP] + WPA2-PSK [AES], but that too had no effect.
13. To verify that it wasn't just the USB hub crashing, I plugged a PS/2 keyboard into the tower. No luck.

So, that's where I'm at. Any help you can offer would be greatly appreciated. This is really the only thing keeping me from making Linux my primary OS. 
Thanks!

---

### Post by gordintoronto on 2015-03-07
This problem will go away if you throw about $15 at it, by buying a Linux-friendly USB adapter, and discard your seven-year-old D-Link.

With a Linux-friendly device, you plug it in and it "just works," maybe after a reboot. You don't need to install a driver, because it's built-in.

---

### Post by revblk on 2015-03-08
I recognize and appreciate that as one possible solution, and absent any other solution, that's likely the road I'll need to go down. 
That said, I'm currently hoping to find a solution that's a bit more conservative than throwing money at a new adapter and tossing an otherwise perfectly serviceable one away, especially when that adapter appears so close to being functional in Linux.

That said, I'm open to new hardware recommendations.

---

### Post by fwwarr2 on 2015-07-11
Hi [COLOR=#000000]revblk, 

I'm having the exact same problem as you. Did you find a way to get the DWA 142 working, or did you get a different adapter after all?

Thanks![/COLOR]

---

