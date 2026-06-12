---
title: "Access Point: Not-Associated ?!?"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by Papa-san on 2006-11-04
sudo iwconfig =
```
eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:XXXX-XXXX-XX (shows the correct one)
          Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
I posted a similar one in the 'absolute beginners' forum, but didn't get any views or help. ANYTHING would be appreciated! My wife is about to re-format my laptop with WinXP because I can not ever get things to run smoothly!

---

### Post by amohanty on 2006-11-05
So is your wireless router setup as an access point?
Can you post the contents of /etc/network/interfaces
The output if **ifconfig**

AM

---

### Post by Papa-san on 2006-11-05
Thanks!

Here's ipconfig:```
john@laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5B:E1:BA:40
          inet addr:192.168.1.45  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fee1:ba40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1457129 (1.3 MiB)  TX bytes:272312 (265.9 KiB)
          Interrupt:11 Base address:0xec00

eth1      Link encap:Ethernet  HWaddr 00:90:4B:2C:52:6B
          inet6 addr: fe80::290:4bff:fe2c:526b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:f8ffc000-f8ffe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:283 errors:0 dropped:0 overruns:0 frame:0
          TX packets:283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22236 (21.7 KiB)  TX bytes:22236 (21.7 KiB)

```And /etc/network/interfaces:
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface eth1 inet dhcp
wireless-essid 06B408770040
wireless-key XXXXXXXXXX (it's right)

auto eth0

auto eth1
``` (However the contents of this change!)

---

### Post by FrodoB on 2006-11-05
And that is the same essid that you have in your access point?

---

### Post by Papa-san on 2006-11-05
Yup, The wireless card picks it up right from the router.

---

### Post by amohanty on 2006-11-05
> (However the contents of this change!)

They really shouldnt!!, unless you have a startup scrip that uses wireless tools to scan and use one.

1. Can you make sure that the essid is correct?
2. Is the router configured to be an access point (being just a router in ad-hoc mode is different from being an access point)?
3. try adding **wireless-mode managed** to the end
4. Finally try taking down both interfaces and bringing up only the wireless one?

Also post the output of iwconfig

AM

---

### Post by Papa-san on 2006-11-05
OK...
ESSID verified, It's printed right on the bottom of the router.

I don't know how to tell if it is ad-hoc or access point. The instructions show adding wireless boxes as three simple steps. (for mac and win users)

> john@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I think I changed the settings there. (just got rid of a wlan0 that wouldn't show in my networking gui) 

I'll put the 'wireless-mode managed' in /etc/network/interfaces, disable both and try enabling the wireless only! I'll let ya know!

---

### Post by amohanty on 2006-11-05
> ESSID verified, It's printed right on the bottom of the router.

Oh no no no, the essid being talked about here is the broadcast SSID that you setup on the router. The string that comes up in WinXP when you scan for routers. You can get a list of thise by doing a:
**iwlist scan**

If you havent yet changed it, I would suggest changing it. Todo so you will need to login to the web interface of the router.

HTH
AM

---

### Post by Papa-san on 2006-11-05
06B408770040

I took this from the 'Wireless Configuration' tab while logged on to the router. url 192.168.1.1

How do I do screenshots? I forget... LOL```

john@laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:12:0E:4E:F7:A9
                    ESSID:"06B408770040"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-25 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

sit0      Interface doesn't support scanning.

```

---

### Post by Papa-san on 2006-11-05
Oh yeah, the mode managed thing didn't work...

---

### Post by amohanty on 2006-11-05
well the screenshots not needed, the essid is correct - just that I have never seen one like that... tell you how much I know :)

anyway did adding the wireless-mode managed to the end help at all?

So add**wireless-mode managed** to the end and restart networking: **sudo /etc/init.d/networking restart**

Then take down both interfaces, and bring up only the wireless one
[B]sudo ifdown eth0
sudo ifdown eth1
sudo ifup eth1[/B]

Then see if it works.
AM

---

### Post by Papa-san on 2006-11-05
The essid is pre-set by verizon.

I tried and got this far:```
john@laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... /etc/network/interfaces:21: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:21: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]

```Doesn't seem quite right... LOL

---

### Post by Papa-san on 2006-11-05
I re-edited the /etc/network/interfaces I added a 'return' space and moved the wireless-mode managed down one line, and tried again. The error was :22: So I removed the wireless-mode managed, saved, and tried running the restart command:```
john@laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... /usr/sbin/postconf: fatal: open /etc/postfix/main.cf: No such file or directory
cp: `/etc/resolv.conf' and `/etc/resolv.conf' are the same file
run-parts: /etc/resolvconf/update-libc.d/postfix exited with return code 1
run-parts: /etc/resolvconf/update.d/libc exited with return code 1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:06:5b:e1:ba:40
Sending on   LPF/eth0/00:06:5b:e1:ba:40
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:06:5b:e1:ba:40
Sending on   LPF/eth0/00:06:5b:e1:ba:40
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
/usr/sbin/postconf: fatal: open /etc/postfix/main.cf: No such file or directory
cp: `/etc/resolv.conf' and `/etc/resolv.conf' are the same file
run-parts: /etc/resolvconf/update-libc.d/postfix exited with return code 1
run-parts: /etc/resolvconf/update.d/libc exited with return code 1
bound to 192.168.1.45 -- renewal in 35246 seconds.
                                                                         [ ok ] 
``` Sorry, but this is what it gave me in response...
Same messages, only specific to eth0 & 1 with the ifdown commands.

---

### Post by yargevad on 2006-11-06
> **Papa-san said:**
> ```

john@laptop:~$ iwlist scan
eth1      Scan completed :
          Cell 01 - Address: 00:12:0E:4E:F7:A9
                    ESSID:"06B408770040"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    [SIZE="4"]**Quality:0/100**[/SIZE]  Signal level:-25 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
```


I'm actually having [exactly the same problem]("http://ubuntuforums.org/showthread.php?t=293995"), just manifesting under slightly different circumstances. See how the Quality is 0/100? That means the signal strength is really low. That's strange though, since you control your own Access Point (in my case, I don't). If I connect to a wireless network in an area where the Quality is good and then move to where it isn't, it loses its connection to the Access Point (says 'AP: Not-Associated') and won't get it back if I move back to the good area, only if I reboot and stay in the good area. I'm probably going to have to put a repeater in the good area so the connection is usable in other places, but it'd still be nice to know wth is going on.

---

### Post by amohanty on 2006-11-06
So did you try this:
Then take down both interfaces, and bring up only the wireless one
sudo ifdown eth0
sudo ifdown eth1
sudo ifup eth1

---

### Post by somersetsimon on 2006-11-06
> **yargevad said:**
> I'm actually having [exactly the same problem]("http://ubuntuforums.org/showthread.php?t=293995"), just manifesting under slightly different circumstances. See how the Quality is 0/100? That means the signal strength is really low. That's strange though, since you control your own Access Point (in my case, I don't). If I connect to a wireless network in an area where the Quality is good and then move to where it isn't, it loses its connection to the Access Point (says 'AP: Not-Associated') and won't get it back if I move back to the good area, only if I reboot and stay in the good area. I'm probably going to have to put a repeater in the good area so the connection is usable in other places, but it'd still be nice to know wth is going on.

What wireless device and driver are you using? I had problems for weeks. Every driver I seemed to use was able to scan and find the wireless network, but wouldn't let me connect. Luckily I managed to find a really new driver (for zd1211b) that connected immediately.

---

### Post by yargevad on 2006-11-06
> **somersetsimon said:**
> What wireless device and driver are you using? I had problems for weeks. Every driver I seemed to use was able to scan and find the wireless network, but wouldn't let me connect. Luckily I managed to find a really new driver (for zd1211b) that connected immediately.

I'm using a 3Com XJack wireless card with MadWifi. I'm not having problems connecting initially, just after I've already connected and then I go somewhere where the signal is really weak, it won't ever recover.

---

### Post by Papa-san on 2006-11-09
> **amohanty said:**
> So did you try this:
Then take down both interfaces, and bring up only the wireless one
sudo ifdown eth0
sudo ifdown eth1
sudo ifup eth1

Yes, I did to no avail. However, none of this really matters at this point, because my power converter for my laptop bit the big one... My linux box is a paperweight...:(

---

### Post by Papa-san on 2006-11-09
OK, I did the ifup/ ifdown thing again, (cause I rigged the juice :D  ) Now, during the sudo ifdown eth1 command, I got:```
Listening on LPF/eth1/00:90:4b:2c:52:6b
Sending on LPF/eth1/00:90:4b:2c:52:6b
Sending on Socket/fallback
DHCPRELEASE on eth1 to **[SIZE="4"]192.168.2.2[/SIZE]** port 67
send_packet: Network is unreachable
```This is what I need to locate... Where is this being stored?!? My router's IP is 192.168.1.1  My old router was 192.168.2.2

However, I have tried to put the new information in through my networking gui, and this old IP is the one that gets searched for... The networking gui shows my proper information, but because it is a DHCP router setup, it doesn't show the IP. I have tried to set it manually as a static IP, but that doesn't work...

---

### Post by amohanty on 2006-11-12
Most probably in /etc/network/interfaces (if it had been hardcoded in the firstr place) The way dhcp works is that information or request for it is broadcast and servers listen for requests and respond.

[http://en.wikipedia.org/wiki/Dhcp](http://en.wikipedia.org/wiki/Dhcp)

So if it was not hardcoded in the first place it probably wont be there. If you have a windows box use something like Look@Lan to see if that IP is still active on your network. Dont know how though - if you removed it.

AM

---

### Post by FrodoB on 2006-11-12
Publish the output of the arp command:

$ arp

---

### Post by Papa-san on 2006-11-12
OK...
```
arp
Address                  HWtype  HWaddress           Flags Mask            Ifacedslrouter                ether   00:18:3A:07:26:2A   C                     eth0
```

---

### Post by FrodoB on 2006-11-12
You need to make a little script can call it test.sh and put the following into it:

#!/bin/sh
/usr/bin/sudo /sbin/iwconfig eth1 mode "Managed"
/usr/bin/sudo /sbin/iwconfig eth1 key "XXXXXXXXXXXXXXXXXXXXXXXXXX"
/usr/bin/sudo /sbin/iwconfig eth1 essid "06B408770040"
/bin/sleep 5
/usr/bin/sudo /sbin/dhclient eth1

Modify the key to be the hex value of the key from Xs to that your access point uses or if you only know the ASCII equivalent then put it in as: (note I am using 128bit (104bit) wep examples.

/usr/bin/sudo /sbin/iwconfig eth1 key "s:XXXXXXXXXXXXX"

instead.

Save it and change the permissions to:

$ chmod 755 test.sh

then run it:

$ ./test.sh

run iwconfig and hopefully all will be good and then check iwconfig, ifconfig, and netstat -rn. Post the results to the group.

---

### Post by Papa-san on 2006-11-12
Thanks.
I'm not exactly sure what it means or how to change the permissions on anything. 
I did open gedit, entered the information, and saved it as test.sh
in gedit, when i: 'View > highlight mode > scripts', it shows a bullet next to 'sh' So I am assuming I saved it correctly. (Windows needs to be told separately where to put things) I am assuming Linux is different here...

Then in terminal:
```
john@laptop:~$ chmod 775 test.sh
john@laptop:~$ ./test.sh
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:90:4b:2c:52:6b
Sending on   LPF/eth1/00:90:4b:2c:52:6b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
john@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

john@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

john@laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5B:E1:BA:40
          inet addr:192.168.2.45  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23396 errors:0 dropped:0 overruns:1 frame:0
          TX packets:7349 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3892939 (3.7 MiB)  TX bytes:777252 (759.0 KiB)
          Interrupt:11 Base address:0x8c00

eth1      Link encap:Ethernet  HWaddr 00:90:4B:2C:52:6B
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:f8ffc000-f8ffe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:21596 (21.0 KiB)  TX bytes:21596 (21.0 KiB)

john@laptop:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.2.2     0.0.0.0         UG        0 0          0 eth0

```Evidently it didn't work... :(
EDIT:
When I try to right click on the file and do 'Properties > Permissions' I am told I am not the owner... Help!

---

### Post by FrodoB on 2006-11-12
I don't know what the bullet is, there is none here.

Maybe you should run each command one at a time by cutting and pasting them into a terminal. 

Did you modify the key to match your? Was the essid correct?

Try one line at a time and check iwconfig after each one to see if it is working.

---

### Post by Papa-san on 2006-11-12
OK,
The other thing I need to look at is whether or not I am getting the encryption key right. When I entered it, it was simply done using the appropriate numbers like I would type into the networking GUI. A ten character key... Would I need to modify it somehow?

Thanks!

(Sorry I know so very little about this OS and it's intricacies! I am much more well versed in Tolkien!)

Jack

---

### Post by FrodoB on 2006-11-12
Ten characters in Hexidecimal or just ASCII. The Hex key is 26 characters and the ASCII is 13 for 128bit wep.

The best place to make new keys is:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

It can give you the same key in ASCII and Hex.

if you want to try to enter an ASCII key in Linux: (128bit)

/usr/bin/sudo /sbin/iwconfig wlan0 key "s:XXXXXXXXXXXXX"

change the Xs to the correct key.

---

### Post by Papa-san on 2006-11-12
So can I edit the script, or do I need to redo it?
 And how?

OOPS NM... OK!

---

### Post by FrodoB on 2006-11-12
Open Application --> Accessories --> Text Editor, that gedit and then paste the script in and make the modifications for your WEP keys.

---

### Post by Papa-san on 2006-11-12
Nothing so far... How do I change the permissions?

OK, I just did the chmod command, and hope that is the one that changes the perms.
 Anyways, at least something is different this time!
```
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Invalid argument.

```Then everything else is the same as my previous results post...

---

### Post by FrodoB on 2006-11-12
Open a terminal and see if it is in your home, I hope it is:

ls  - List short - like DOS dir command

$ ls

You hope to see test.sh

chmod - change permissions for Ower Group World

$ chmod 755 test.sh

Makes the file executable, read, and write for you and executable and readable for your group and everyone else.

---

### Post by Papa-san on 2006-11-12
it is there as well as one with a ~ next to it.

(I edited my prevoius post on pg 3...)

---

### Post by FrodoB on 2006-11-12
That would be the previous version that the editor is saving in case you need to refer back to it.

---

### Post by Papa-san on 2006-11-12
That's what I thought...

So, nothing really made a difference... Hmmmmm.

---

### Post by FrodoB on 2006-11-12
Well after you enter this command you should see that the essid has change in a iwconfig command:

$ sudo iwconfig eth1 essid "06B408770040"

$ iwconfig

Should see something like:

eth1      IEEE 802.11b  ESSID:"06B408770040" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit: 4   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=35/92  Signal level=-57 dBm  Noise level=-92 dBm
          Rx invalid nwid: 0  Rx invalid crypt:0  Rx invalid frag:4
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Of course your access point will not show up yet.

---

### Post by Papa-san on 2006-11-12
Still getting the ESSID off/any

---

### Post by FrodoB on 2006-11-12
OK, your device just seems to dead.  Can you publish any details about it (manufacturer, model, etc)?

---

### Post by Papa-san on 2006-11-12
It's a Broadcom 4306 (truemobile)
```
*-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 02
       serial: 00:90:4b:2c:52:6b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper multicast=yes wireless=IEEE 802.11g
       resources: iomemory:f8ffc000-f8ffdfff irq:5

```

```
john@laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:12:0E:4E:F7:A9
                    ESSID:"06B408770040"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-25 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
```It's just really strange, because it was working perfectly right up until we changed the router. The computer didn't move, even... It just seems like really odd timing...

---

### Post by FrodoB on 2006-11-12
What about the access point router? Maybe you should go back and look at its details.

What is the router access points IP address and netmask?

Are you broadcasting the ESSID or SSID?

Have you tried just turning all encryption off and connecting?

Is the DHCP server turned on?

The signal quality worries me, but maybe we should ignore it?

---

### Post by FrodoB on 2006-11-12
Oh I suppose the access point is working with a windows machine? If so can you go to it and get the information concerning its IP address, default route etc.

---

### Post by Papa-san on 2006-11-12
I will go through those suggestions tomorrow. I need to get ready for class tonight...
(Yes, Sunday night is a bit odd, until you realize that I am in school to be a pastor... lol We don't get Sundays off anymore!)

---

### Post by FrodoB on 2006-11-12
Have a good evening and enjoy your studies.

On the Windows side if you are running Windows XP or 2000 the command output that you want is from the ipconfig command:

C:\Documents and Settings\Owner>ipconfig /all > ip.txt
C:\Documents and Settings\Owner>notepad ip.txt

Then you can paste the data from notepad into your browser.

---

