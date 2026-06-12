---
title: "Huawei mobile connect e169g"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by clownius on 2008-06-26
Hi i stupidly ended up with the e169g usb stick modem instead of the E220 usb modem when i recently brought a mobile internet package through 3 Australia.  It works under windows but im not having any luck under Kubuntu. Any and all help appreciated to get this working as it pains me to boot into Windows to surf the web when im out and about.

I cant seem to use this modem with kppp it doesnt detect any modem is can communicate with

lsusb gives me
```
myusername@mycomputername:~$ lsusb
Bus 007 Device 003: ID 05a9:2640 OmniVision Technologies, Inc.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 006: ID 0a5c:4503 Broadcom Corp.
Bus 001 Device 005: ID 0a5c:4502 Broadcom Corp.
Bus 001 Device 004: ID 413c:8126 Dell Computer Corp.
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp.
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000


```

Ive also seen people mention wvdial so it turns out this
```
myusername@mycomputername:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.


```

Ill run anything else people need to help track this down its driving me insane.

---

### Post by Zymous on 2008-08-26
It may be too late to help, but somebody got this modem to work with Xandros on the EeePC see [http://dalelane.co.uk/blog/?p=254]("http://dalelane.co.uk/blog/?p=254")

-- 
Zym

---

### Post by TDFlanders on 2008-08-26
Hi there aussie,

I am using 3 UK now. There seem to be several ways to solve this. True wvdial or shell scripts, or by installing networkmanager 0.7.0. Unfortunately none of the shell scripts worked for me really. You can install networkmanager as described below, or you can upgrade to intrepid. Please note that this is not a stable release yet, and you probably will encounter many bugs, like I have for the last few weeks. It works though. Take care!

[http://ubuntuforums.org/showthread.php?t=897067&highlight=huawei](http://ubuntuforums.org/showthread.php?t=897067&highlight=huawei)

[http://ubuntuforums.org/showthread.php?t=897695&highlight=huawei](http://ubuntuforums.org/showthread.php?t=897695&highlight=huawei)

---

### Post by TDFlanders on 2008-08-26
One more thing,

did you use huaweiAktBbot to switch from flash memory plug and play mode to the other mode? It is described in the posts. If that is not the problem, you could also try ps -A and then sudo kill -9 the process that could be using it, like pppd, gnome-ppp or wvdial maybe? Anyway, good luck. Ask GeorgeVita maybe for help (see previous post), he is a nice guy, but I don't have time at the moment.

Cheers,

Thomas

---

### Post by liamgh on 2008-08-26
I've put together a package to make it easier to use the E169G under Ubuntu - I'm using it on my Ubuntu powered EEE PC. Details are at: [http://www.greenhughes.com/content/huawei-e169g-easy-way]("http://www.greenhughes.com/content/huawei-e169g-easy-way") it would be great if a few people could give it a go to see if it works for them. The package uses usb_modeswitch to configure the E169G and includes the configuration files needed.

---

### Post by clownius on 2008-08-31
I will have a play with this at work over the next few days.  Im still unable to use it under Ubuntu at the moment as it wont hold connection.  As i only use it at work ive been using another OS when i need it.  Ill try this package to see if it works once i get back within range of mobile coverage at work as i have none at home.  Thanks for all the help and ill yell if it works.

---

### Post by mashcaster on 2008-09-12
Have you tried updating the network manager?
[http://ubuntuforums.org/showthread.php?t=797059](http://ubuntuforums.org/showthread.php?t=797059)

---

### Post by ahsaeed on 2008-09-12
hey i  i had the same problem with my Pantech wireless card  and it is solved now 
first 
*$lsusb*

you get a list of ur usb list devices 
sec.
*$ sudo modprobe usbserial vendor=xxxx product=xxxx *
fill the xxxx from the usb devices list uthat u get at the first step

then i used *gppp *to setup my network configurations also u can use *KPPP *to do it
hope that help!

note: it some times need to restar after configuration and some times need to retry for many times 
and in the devises list in kppp may u need to try it one by one 

good luck

---

### Post by Turev on 2008-10-06
Hi All;

If it is not too late, I have an E169G as well, after all the digging I have found the software to get this thing working. It can be found under:

[http://forum.ubuntuusers.de/topic/o2-surfstick-mit-ubuntu-7.04-7.10-8-04/](http://forum.ubuntuusers.de/topic/o2-surfstick-mit-ubuntu-7.04-7.10-8-04/)

Scroll down the page and you will find a link for the file "UMTSmon_0.8_o2.deb (226.6 KiB)". Simply download this deb file and install. You do not need (well I did not need) to do any more adjusting etc... E169G simply works with this software. 

Enjoy

Gokhan-

---

### Post by yadhav on 2008-12-29
Hi, following all these steps and many more, I had been able to connect my Huawei e169G Modem in Ubuntu. I made a blog where all the steps from A to Z have been mentioned. I'm 100 % sure that if you follow it properly, yours will be connected to. Here it is:
[http://crazyaboutubuntu.wordpress.co...ick-on-ubuntu/](http://crazyaboutubuntu.wordpress.co...ick-on-ubuntu/)

---

### Post by labinnsw on 2008-12-29
[Correction to link posted by yadhav]("http://crazyaboutubuntu.wordpress.com/huawei-e169g-hsdpa-usb-stick-on-ubuntu/")

[Link to simpler instructions that also work]("http://ubuntuforums.org/showthread.php?t=887022")
See post #5

When you are finished it would also be a good idea to see [this]("http://ubuntuforums.org/showthread.php?t=797059") link

This also works for other Huawei models.

---

### Post by oygle on 2008-12-29
> **labinnsw said:**
> 
This also works for other Huawei models.

Can the E169 be used as a dongle (i.e. **NOT** attached to a router, but directly attached to the computers USB port), **AND** get eth0 working **WITH** Network Manager 0.7 and Intrepid ??

No answers at [http://ubuntuforums.org/showthread.php?t=1022569](http://ubuntuforums.org/showthread.php?t=1022569)   :(

Oygle

---

### Post by labinnsw on 2008-12-29
Definitely. That is how I am using the E160G

---

### Post by oygle on 2008-12-29
> **labinnsw said:**
> Definitely. That is how I am using the E160G

Those links you provided seem to be for using wvdial or similar to dialout. My situation is to try and use Network manager, not wvdial, or Gnome PPP, etc.

If you use NM 0.7 with Intrepid, and use the E169 attached to the computer, then you will have to have ppp0 and eth0 up and running. If you are doing that, can you post your  /etc/network/interfaces file please ?

Oygle

---

### Post by labinnsw on 2008-12-29
I did install GNOME PPP before doing an installation of Network Manager 0.7

It works as set out [here]("http://www.darrenalbers.net/blog/?p=9")

If this is not what you are looking for, then, sorry. I must have misunderstood your request.

The connection is "Auto Mobile Broadband" not "Auto Eth0"

---

### Post by oygle on 2008-12-29
My understanding is that an E169 connection with Intrepid is by _either_ a dialup script (GNOME PPP, wvdial, etc) _OR_ network manager 0.7

If you installed GNOME PPP, possibly it is not used when you are connected ?

Did you setup the wireless broadband connection under network manager ? If so, then my understanding is that any interface in /etc/network/interfaces is disregarded ?

Or, more to the point, I have seen posts where people recommend that if they are having trouble with some interface (say eth0 ), _AND_ they use Network manager 0.7 , then they should remove that interface from /etc/network/interfaces

Can you post the contents of /etc/network/interfaces please ?

Oygle

---

### Post by labinnsw on 2008-12-29
On installation of the network manager the settings were automatically copied form GNOME PPP or some other source that was already installed. That is why I recommend installing in that order. Connection to the Internet is via the network manager.

---

### Post by oygle on 2008-12-29
> **labinnsw said:**
> 
The connection is "Auto Mobile Broadband" not "Auto Eth0"

Yes, the mobile broadband will be ppp0 if you are using a E169 attached direct to the USB port of your computer. The LAN (eth0) is different. I need to know how to get _both_ going (ppp0 and eth0) in Intrepid with Network manager 0.7 installed and being used.

---

### Post by labinnsw on 2008-12-29
> **oygle said:**
> Can you post the contents of /etc/network/interfaces please ?

Oygle

auto lo
iface lo inet loopback


iface ppp0 inet ppp
provider ppp0

auto ppp0

---

### Post by labinnsw on 2008-12-29
Earlier I was using the Mobile. At the moment I am using the Wired (i.e. Auto Eht0) They are both available in the network manager but they cannot be used simultaneously. You must disconnect one to use the other.

You can IM me if you wish.

---

### Post by oygle on 2008-12-29
> **labinnsw said:**
> auto lo
iface lo inet loopback


iface ppp0 inet ppp
provider ppp0

auto ppp0

Thanks muchly.  :)

Interesting, you have no LAN interface in that file. That would suggest that your eth0 is 'defined' via network manager. I remember there was a tab there for 'wired' connection. Must check out what I stated there.

Thanks,

Oygle

---

### Post by oygle on 2008-12-29
> **labinnsw said:**
> Earlier I was using the Mobile. At the moment I am using the Wired (i.e. Auto Eht0) They are both available in the network manager but they cannot be used simultaneously. You must disconnect one to use the other.

You can IM me if you wish.

I saw this post just now. Okay, so this again suggest that I must specify the wired connection in Network manager.

But if a person can only have one interface going at once, then how can I 'share' the wireless connection ? I can only share it via the LAN (eth0).

Oygle

---

### Post by labinnsw on 2008-12-29
That is where I think I may have mis-understood your request. If it is possible to share the connection while it is plugged directly in the USB port, I don't know how.

---

### Post by oygle on 2008-12-29
I can do it on Hardy, no worries. But with Intrepid, and the arrival of network manager, which made things easier for some connections, but seems to have 'killed' the possibilty of using ppp0 and eth0 at the same time.

Still, your post with the contents of the interfaces file looks promising. I will do full backups of both computers, and try changing some settings.

Oygle

---

