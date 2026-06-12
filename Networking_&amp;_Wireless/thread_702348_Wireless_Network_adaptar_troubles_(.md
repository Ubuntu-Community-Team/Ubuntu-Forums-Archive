---
title: "Wireless Network adaptar troubles :("
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by Vatho on 2008-02-20
Hello everyone!! As some of you know, I have just started out ubuntu... I made the 7.10 Gutsy gibbon CD as of last night. I tried out the live cd, and loved it right away, when I was trying out the live cd, I could see the wireless networks around my house listed in the top right of ubuntu. So I went ahead and installed ubuntu on my pc. BUT, when I started ubuntu up (without the cd) the networks were no longer listed, and it seemed as if ubuntu didn't recognize my wireless adapter, because it asked me to enable some restricted drivers. I enabled those, and yet, no internet.. I am totally stumped here :confused: :confused:

I use the Belkin Wireless G USB Network Adapter (no on board wifi card), My router has no encryption on, just allows pc's with specified mac addresses to get on (so it shouldn't be a problem).

 I completly uninstalled windows, and dont regret it (as long as I can get my internet working)

Any help would be greatly appreciated :)

Signed,
An ubuntu newbie

---

### Post by Bridger987 on 2008-02-20
I have been having a very similar problem with my Gateway laptop, which contains a Realtek RTL8187 internal card.  When using the wireless connection with the live CD, it worked fine, but then once I wiped XP off of my system, and installed Ubuntu Gutsy Gibbon onto the hard drive, my wireless card has, all of a sudden, become unreliable and slow.

Wired ethernet works fine, and I'm more than happy with the rest of the Ubuntu environment.  I'd hate to have to go back to Windows just because of a simple problem with a wireless driver, or maybe a new Gutsy security program that might be getting in the way or something.

I also posted my problem as a thread, here:
[http://ubuntuforums.org/showthread.php?t=701794]("http://ubuntuforums.org/showthread.php?t=701794")

And found similar (but not identical) problems here:
[http://ubuntuforums.org/showthread.php?t=581055]("http://ubuntuforums.org/showthread.php?t=581055")

---

### Post by Vatho on 2008-02-20
Yupp, gutsy pulled a fast one on both of us :(

Ive been searching all day, trying to find a fix, and can't :(

I dont have the windows installation disk, so i'm kinda screwed there...

I'll keep searching till a smart fellow can help us!

---

### Post by mrsteveman1 on 2008-02-20
Do you know what the chipset is in the stick? I seem to remember that belkin sticks use zydas, realtek and atheros chipsets depending on the revision of each model.

Check when its plugged in run:

```
sudo lshw -C network
```

Since the stick worked out of the box with the livecd, im going to guess its a zydas chipset.

Also, plug the device in and run:

```
sudo dmesg | tail -n 30
```

and post the results.

---

### Post by Vatho on 2008-02-20
Alright, When I typed in the first one, I got..

```
)-network DISABLED
description: wireless interface
physical id: 1
logical name: wlan0
serial: 00:11:50:c0:e5:24
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

And when I typed in the second...

```
[   131.75904] usbcore: registered new interface driver rt2500usb
[ 131.824360] usbcore: registered new interface driver rt73usb
[ 132.250421] intel8x0_measure_ac97_clock: measured 55223 usecs
[ 132.250434] intel8x0: clocking to 48000
[ 133.178632] lp: driver loaded but no devices found
[ 133.283116] Adding 674688k swap on /dev/sda5.  Priority:-1 extents:1 across:6
74688k
[133.784675] EXT FS on sda1, internal journal
[ 136.108032] input: Power Button (FF) as /class/input/input4
[ 136.108750] ACPI: Power Button (FF) [PWRF]
[ 136.144020] input: sleep button (CM) as /class/input/input5
[ 136.144747] ACPI: Sleep Button (CM) [SLPB]
[ 136.340795] No dock devices found.
[ 138.841961] ACPI: PCI Interrupt 0000:00:1f.6[B]  -> Link [LNKB]  -> GSI 10 (level, low)  -> IRQ 10
[ 138.842016] PCI: Setting latency timer of device 0000:00:1f.6 to 64
[ 138.946575] MC'97 1 converters and GPIO not ready (0xff00)
[ 140.173474] phy0  -> rt2500usb_enable_radio: Error - Register initialization failed.
[ 140.386139] ppdev: user-space parallel port driver
[ 140.533183] audit (1203517285.364:3): type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4902 profile="/usr/sbin/c
upsd"
[ 140.628079] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[ 140.628108] apm: overridden by ACPI.
[ 141.006475] Failure registering capabilities with primary security module.
[ 141.393727] Bluetooth: Core ver 2.11
[ 141.394047] NET: Registered protocol family 31
[ 141.394055] Blutetooth: HCI device and connection manager initialized
[ 141.394065] Bluetooth: HCI socket layer initialized
[ 141.449338] Bluetooth: L2CAP ver 2.8
[ 141.449350] Bluetooth: L2CAP socket layer initialized
[ 141.473595] Bluetooth: RFCOMM socket layer initialized
[ 141.473834] Bluetooth: RFCOMM TTY layer initialized
[ 141.473842] Bluetooth: RFCOMM ver 1.8
```

Hope that info can come up with a solution :)

---

### Post by mrsteveman1 on 2008-02-20
I see one problem already, its trying to load 2 drivers at the same time.

rt2500usb and rt73usb are, i believe, separate drivers and only one should be loaded.

Since lshw didn't show much, run lsusb while the stick is plugged in and see if it tells you the chip name. If lsusb doesn't give you anything useful run sudo update-usbids first and try lsusb again afterward.

You might also just try removing both modules and inserting one or the other and see what happens like this:

```
sudo rmmod rt2500usb
sudo rmmod rt73usb
sudo modprobe rt2500usb
ifconfig -a
```

I believe belkins realtek chipset is a 2500 but they may have made a new one.

In any case these chips probably require firmware to function, which might be why ubuntu bugged you about restricted drivers.

---

### Post by Vatho on 2008-02-20
Alright, I'll have to try that when I get home (have to go out for a bit)

and in windows, it required a cd to install a software in which you connected to networks..

So your saying if I dont get it to work, my computer is gonna be offline forevor?

---

### Post by mrsteveman1 on 2008-02-20
Nah, the drivers definitely work, so its just an issue of getting the system to load them right.

The application in windows is probably the manufacturers connection program, they include them all the time for some reason and they are unnecessary even in windows.

---

### Post by Vatho on 2008-02-20
Woot! Ty for the info :)  It now lists the wifi's in my area, but it's doing what it did in the live cd, that is, the bottom light is green, and that blue thing keeps spinning until eventually, I get no connection to it still =/

Thanks so much for getting me this far, any ideas this time? :)

---

### Post by mrsteveman1 on 2008-02-20
Ok, what do the following commands return:

```
sudo iwlist scan

sudo iwconfig 
```

If you loaded the rt2500usb module you might want to blacklist the other one, rt73usb.

---

### Post by Vatho on 2008-02-20
Alright, for the first one, I got..
```
lo Interface doesn't support scanning.

wmaster0 Interface doesn't support scanning.

wlan0 scan completed:
(It listed the wifi networks around my house,so I just wrote down what it came up with for mine)
Address:00:1B:2F:08:37:88
ESSID:"family"
mode:Master
Channel:11
frequency: 2.462 GHz
signal level = -74 dBm
encryption key:off
BitRates: 1 MB/s; 2 Mb/s (etc. etc.)
Extra:tsf=00000001fa1567db
```

And the second command returned..

```
lo  No wireless extensions.
wlan0  IEEE 802.11g ESSID:" "
mode:Managed       Frequency:2.412 GHz     Access Point:Not-associated
Retry minlimit: 7 RTS thr: off fragment   thr=2346B
Encryption key: off
link quality:0    Signal level:0   Noise level:0
rx invalid nwid:0  Rx invalid crypt:0   Rx invalid frag:0
Tx excessive retries:0  Invalid misc: 0
missed beacon:0
```

Hope that is useful as well!  :)

PS. Thanks a bunch for helping me :D

---

### Post by mrsteveman1 on 2008-02-21
It seems the driver works fine at the moment, so you're saying that the ubuntu networkmanager applet isn't connecting correctly?

It sounds like your network isn't encrypted so try this:

```
sudo iwconfig wlan0 essid family
sudo dhclient wlan0
ping yahoo.com
```

this should connect the card to your router, grab the IP address etc, and try to ping yahoo.

---

### Post by Vatho on 2008-02-21
Alright, sorry it took me so long to reply, 
Here is what I got..

```
There is already a pid file /var/run/dhclient.pid with pid 5652
Killed old client process, Removed PID file

wmaster0:unknown hardware address type 801
wmaster0:unknown hardware address type 801

Listening on LPF/wlan0/00:11:50:c0:e5:24
sending on LPF/wlan0/00:11:50:c0:e5:24
sending on Socket/Fall back
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DCHPoffers recieved.
No working leases in persistent database - sleeping

```

And then when I tried to ping yahoo..

```

ping:unknown host yahoo.com

```

This problem has me scratchin my head :(

See anything I might be doing wrong?? Any ideas on how to get it connected?

---

### Post by mrsteveman1 on 2008-02-21
When you do 

```
sudo iwconfig wlan0 essid family
sudo iwconfig
```

what does iwconfig wlan0 tell you? Does it show a connection? In particular does it list an access point mac address on the right?

---

### Post by Vatho on 2008-02-22
Yea, after typing in "sudo iwconfig wlan0 essid family" And then "sudo iwconfig wlan0"   I do get a mac address (it's in "Access Point: 00:1B:2F:08:37:88 )

---

### Post by mrsteveman1 on 2008-02-22
Ok so the card is able to associate with the access point, but apparently isn't able to do much yet.

Try setting the ip address manually to see if everything works:

```
sudo ifconfig wlan0 192.168.1.10

```

then try to ping your router, EG ping 192.168.1.1 if thats the address

---

### Post by Vatho on 2008-02-22
Alright, I'll try it out when I get home..

---

### Post by Vatho on 2008-02-22
Alright!! The pinging to my ip was successful! :)

That means we're getting somewhere!!

Haha...Now...how do we go about connecting to the internet? :)

---

### Post by mrsteveman1 on 2008-02-22
If your routers ip address is 192.168.1.1, you can set it as the default route like this:
```

sudo route add default gw 192.168.1.1
```

then you need to add a dns server, so find out what dns server you are supposed to be using (might even just be pointed to your router) and add it to the /etc/resolv.conf file:

```
sudo nano /etc/resolv.conf
```

and add a line like this:

```
nameserver 192.168.1.1
```

If all that works, i'm not sure why the networkmanager applet wouldn't be able to set this stuff and connect to the access point, but perhaps its just acting weird.

---

### Post by Vatho on 2008-02-22
Alright, so Do I replace 'nameserver' with my dns server??

And btw, how would I go about finding my DNS server? :confused:
(sry, ima nub when It comes to networking)

---

### Post by mrsteveman1 on 2008-02-22
Your ISP should have given you a dns server to use, or perhaps your router just gets it from your ISP directly. Some cable and dsl modems do that.

In any case your /etc/resolv.conf file should look like this:

```
domain local
nameserver 192.168.1.1
```

nameserver stays, the IP changes if you aren't using your router for the DNS.

Is this a dual boot machine? What is XP using?

---

### Post by Vatho on 2008-02-22
Alright, I'll configure it in a sec, and no, I made the mistake of installing ubuntu over xp, so i'm stuck with ubuntu (no chance on windows - no disks) And am accessing enet with my 32mb ram windows 98 pc :(

I really need the internet, and am going to try and figure it out..i'll reply with the outcome in a couple mins

---

### Post by mrsteveman1 on 2008-02-22
For the moment you can use opendns servers: 208.67.222.222 and 208.67.220.220

Either one should work for you, or both, so just add a line like this to /etc/resolv.conf:

```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

Once you do that DNS should no longer be a problem, and since you said you can ping your router, and i assume the default route works, everything should be ok. If not just post back :D

---

### Post by Vatho on 2008-02-23
It works!!! :)

Ty soo much for your help :)

Just one problem, When I was surfing, it would go slow to fast, and then eventually disconnect from the internet again..

Is it my adapter doing it, or my router, or what??

Ty again :D

*EDIT*
I just restarted pc, to see if it would change something, and I have to do everything all over again (like rmmod the drivers, add the resolv.conf things)
Gah..anyway to make this auto be there?? As I am back to the beginning :(

---

### Post by mrsteveman1 on 2008-02-23
If the rt2500usb module is the one that works, blacklist the other one by adding a line like this to /etc/modprobe.d/blacklist:

```
blacklist rt73usb
```

resolv.conf sometimes gets written over by dhcp clients, and yea the network settings themselves aren't going to stay unless you add them to /etc/network/interfaces like this:

```

auto wlan0
iface wlan0 inet static
wireless-essid  family
wireless-mode managed
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1

```

Note however that if you set things manually like this, you will have to change them if you want to use this computer on another wireless network etc.

I'm still curious why the system itself works but the GUI cant connect it for you, it's quite odd.

It's also possible that the driver for this chipset in the current Ubuntu kernel just isn't all that stable. There are new drivers available that can be used on the older kernel, but I'm not sure if they currently include the rt2500usb module.

---

### Post by Vatho on 2008-02-23
Alright, i'll check it out, and my adapter uses the rt73usb driver

I'll try and see if I can remember how I did it (was messing with the actual GUI, and then did what you said, and kinda blindly did it) haha..i'll make notes of what I did, ty for your help (again) :) :D

---

