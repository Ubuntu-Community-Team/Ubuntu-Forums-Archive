---
title: "[Wireless Networking] Trying to get TEW-423PI to work!!!"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by BB2008 on 2008-07-20
Linux newbie here! I am trying to get my PCI wireless network card to work with ubuntu 8.04. I installed the ndiswrapper using apt-get and then used ndiswrapper to install the WinXP driver for this card. Bottomline is, I am not able to get the card to work. Please help!!!!

When I issue the "**sudo modprobe ndiswrapper**" command, I see an error in the **/var/log/messages**. It says:

Jul 20 00:43:21 BigBoy kernel: [ 1061.369999] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Jul 20 00:43:21 BigBoy loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver mrv8000c 
Jul 20 00:43:21 BigBoy kernel: [ 1061.382733] usbcore: registered new interface driver ndiswrapper

**lspci** sees the hardware:

03:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

And this is the output of **lspci -n**

.....
03:07.0 0200: 11ab:1faa (rev 03)
.....


**iwconfig:**

lo        no wireless extensions.

eth0      no wireless extensions.


**ifconfig:**

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:5a:0b:e1  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe5a:be1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10723 errors:0 dropped:42275684294 overruns:0 frame:0
          TX packets:6580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12731407 (12.1 MB)  TX bytes:852735 (832.7 KB)
          Interrupt:254 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100069 (97.7 KB)  TX bytes:100069 (97.7 KB)

---

### Post by jluquette on 2008-07-20
Man I really wish I could help you but you
are probably ahead of me.  Could you please tell me where you got your Windows driver that you used with ndiswrapper.  And what is the name of the file and how do you know that this is the right file?

---

### Post by BB2008 on 2008-07-20
Sure. I got the driver from the trendnet website - [http://www.trendnet.com/asp/download_manager/list_subcategory.asp?SUBTYPE_ID=690#](http://www.trendnet.com/asp/download_manager/list_subcategory.asp?SUBTYPE_ID=690#). Note that the hardware version on my card is B1 - your could be different, in which case you will need a different driver.

My doubt is - this is a 32 bit driver, while my system is AMD 64x2 platform. That could be the reason why my driver is not loading.

And yes, the driver file name is mrv8000c.inf. In case you have not seen this page, it is quite helpful - [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).

Best of luck!

---

### Post by BB2008 on 2008-07-20
Ok, I did a bit more poking around, and this is what i have so far. I think my hunch around the driver being 32 bit is right. Output of dmesg is as under:

**dmesg | grep ndis**
[   45.048441] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   45.249631] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   45.249636] ndiswrapper (load_sys_files:210): couldn't prepare driver 'mrv8000c'
[   45.249973] ndiswrapper (load_wrap_driver:112): couldn't load driver mrv8000c; check system log for messages from 'loadndisdriver'
[   45.250016] usbcore: registered new interface driver ndiswrapper

Also, I ran lsmod, and the output is:

**lsmod | grep ndis**
ndiswrapper           243872  0 
usbcore               169904  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd


So, the question is - is there a 64 bit driver out there for this card? It is a Trendnet PCI card, TEW-423PI, Hardware version B1? Also, is there a way to port the 32 bit driver to 64 bits. I cannot believe that I am the first one to come across this, there must be a number of folks who must have tackled this :confused:...

Any help will be immensely appreciated!

---

