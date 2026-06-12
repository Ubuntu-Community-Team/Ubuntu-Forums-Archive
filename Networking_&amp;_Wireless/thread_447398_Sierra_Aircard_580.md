---
title: "Sierra Aircard 580"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by arfitty on 2007-05-17
As a VERY recent graduate from That Other OS, I've had a dream run with Ubuntu 7.04, compared with a number of other dis(as)tros - Ubuntu detected my d-Link WiFi and hopped on the LAN like a good 'un.  If I could get it talk to my laptop's wireless broadband - the Sierra Aircard 580 - I'd be a happy road warrior and Mr G would see me no mo'.  However, working through a helpful link at [http://postnuke.systura.com/modules.php?op=modload&name=News&file=article&sid=51](http://postnuke.systura.com/modules.php?op=modload&name=News&file=article&sid=51), I fell at the first hurdle. The link said:
To begin we need to insert our wireless card into our PCMCIA slot. 'lspci -v' shows us what this card looks like:

03:00.0 USB Controller: Agere Systems (former Lucent Microelectronics) USS-312 USB Controller (rev 10) (prog-if 10 [OHCI])
        Subsystem: Agere Systems (former Lucent Microelectronics) USS-312 USB Controller
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at 40800000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [50] Power Management version 2

However, when I did the lspci -v, I got:

02:00.0 USB Controller: Agere Systems USS-312 USB Controller (rev 10) (prog-if 10 [OHCI])
        Subsystem: Agere Systems USS-312 USB Controller
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at 34000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

I assume the <access denied> is why nothing else works!  The lappy sees the card - and the card's light flashes green, so it sees the machine - but having set up the pppconfig I can't ppd the ISP.

Any ideas?  

Running the latest build of Ubunto on an ACER Aspire 3000

Regards

Ross

---

### Post by chili555 on 2007-05-18
```
Capabilities: <access denied>
```This simply means the full capabilities of the card will only be available to the super-user. Please run the command:```
**sudo** lspci -v
```

I have never set up pppconf but it sounds to me like the card and drivers are set up correctly. You might let us see ```
iwconfig
```Thanks.

---

### Post by arfitty on 2007-05-18
iwconfig returns:

lo no wireless extensions
eth0 no wireless extensions

But thanks for the heads-up about the first issue:  I'll do that and see what happens.

Ross

---

### Post by arfitty on 2007-05-18
Does this help?

ross@Whiteclover:~$ sudo /sbin/ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:B4:35:99
             UP BROADCAST MULTICAST  MTU:1500  Metric:1
             RX packets:0 errors:0 dropped:0 overruns:0 frame:0
             TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000
             RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
             Interrupt:16 Base address:0x1800  eth0:avah Link encap:Ethernet  HWaddr 00:C0:9F:B4:35:99             inet addr:169.254.7.236  Bcast:169.254.255.255  Mask:255.255.0.0
             UP BROADCAST MULTICAST  MTU:1500  Metric:1
             Interrupt:16 Base address:0x1800  
lo          Link encap:Local Loopback
             inet addr:127.0.0.1  Mask:255.0.0.0           
             inet6 addr: ::1/128 Scope:Host
             UP LOOPBACK RUNNING  MTU:16436  Metric:1
             RX packets:26 errors:0 dropped:0 overruns:0 frame:0
             TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:0
             RX bytes:2464 (2.4 KiB)  TX bytes:2464 (2.4 KiB)

---

### Post by chili555 on 2007-05-18
Well, it looks like your card is *not* set up properly yet. Please proceed with the remaining steps from the HOWTO you linked.

---

### Post by arfitty on 2007-05-18
The next instruction is:

Once we get here, we need to create our ppp config: vi /etc/ppp/peers/lxevdo

-detach
ttyUSB0
115200
debug
user [email]user@telstra.pcpa[/email]ck
password telstra
defaultroute
usepeerdns
crtscts
lock
connect '/usr/sbin/chat -v -t3 -f /etc/ppp/peers/lxevdo_chat

I assume this is a script along the lines of a Windows bat file?  I can create a script using Pico or Vim, but I'm  not sure where this gets me - don't understand the vi /etc/ppp/peers/lxevdo reference.

Ross

---

### Post by chili555 on 2007-05-18
If you have done these steps:```
/sbin/modprobe usbserial vendor=0x1199 product=0x0112

mknod /dev/ttyUSB0 c 188 0
```Then I think we need to switch to Ubuntu tools and away from FC4 tools. The outcome will be similar. Instead of manually creating these configuration files, let's use pppconfig. Pop your install CD in the tray and do:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install pppconfig
```It will complain it cannot get to the internet repositories, but you can safely ignore that.

When you run pppconfig, you will be able to set up your connection details and the  needed configuration files will be created.

---

### Post by arfitty on 2007-05-18
Er...

ross@Whiteclover:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
E: Failed to mount the cdrom.
ross@Whiteclover:~$

---

### Post by chili555 on 2007-05-19
Stubborn things, sometimes. You might try placing the disc in the tray and then:```
sudo apt-cdrom -m add
```Follow with the remaining commands.

---

### Post by arfitty on 2007-05-20
That certainly persuaded the system to mount the CDROM, but the installation disk is completely WINDOWS-focused using .msi, and the operation failed because the system, correctly, deduced that "it is not a Debian disk."  What I don't understand (among the many) is what's missing here: the card LCD shines green which indicates that it thinks it's somewhere.  This is such a brilliant OS that I'm reluctant to give up now, but I really don't know where to go next.

---

### Post by chili555 on 2007-05-21
Are you using your Ubuntu install CD or otherwise? pppconfig will be on your Ubuntu install CD.

---

### Post by arfitty on 2007-05-21
My mistake; missed the plot - have pppconfig, so I'm ok there; have run it and set up the details I need (password, dial number etc).  What do I do to connect?

---

### Post by arfitty on 2007-05-23
Works!   Went back over your posts, Chili, and it occurred to me that all the components were there, so used pppdcall Provider and, bingo! online.  Thanks for taking the time.  I'm a Linux road warrior!

---

### Post by chili555 on 2007-05-23
Glad you are all set up. I was worried, a bit, because I've never worked with pppconf. I hoped it would work, somehow, automagically. Sounds like my prayers to the Great Penguin were answered!

---

