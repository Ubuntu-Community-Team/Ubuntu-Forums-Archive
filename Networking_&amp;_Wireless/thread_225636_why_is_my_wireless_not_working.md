---
title: "why is my wireless not working?"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by olivesmarch4th on 2006-07-30
I've been running Ubuntu about two months, for the last three weeks or so I've been running Dapper, with perfect, flawless wireless.  Today I'm just doing my online routine and suddenly I have no wireless.  It's not the router.  My husband's Windows computer works perfectly.  I have unplugged/replugged/restarted everything multiple times.

I learned there was a kernel-upgrade wireless problem, so I blacklisted the ipv6 modules as instructed, saved the file, restarted the computer.  Nothing.  The only thing I installed recently (within the last two days) were the Mozilla Firefox updates and some kdelibs-bin/data/etc upgrades, so I don't get how this could be a kernel thing. 

Please save a convert.  I cannot go without wireless.

Thanks for your time,

Christy Moceri

---

### Post by jpkotta on 2006-07-30
Post the output of ```
iwconfig
``` and ```
ifconfig
```

---

### Post by olivesmarch4th on 2006-07-30
FROM iwconfig:

eth1      radio off  ESSID:"Lion14"
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

FROM ifconfig:


eth1      Link encap:Ethernet  HWaddr 00:13:CE:E4:19:89
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x6000 Memory:b800a000-b800afff

---

### Post by jpkotta on 2006-07-30
> **olivesmarch4th said:**
> 
eth1      radio off  


That's the problem.  Your hardware is off.  My laptop has different ways to toggle it on and off.  I can do it in the BIOS, or there's a function key to do it while it's running, "Fn+F2" (the F2 key has a little blue antenna icon).

---

### Post by olivesmarch4th on 2006-07-30
Ok, toggling doesn't seem to work.  How would I do this in the BIOS?

---

### Post by jpkotta on 2006-07-31
By "toggling doesn't work", I assume you mean that the "radio off" message in iwconfig doesn't change (if it does, then your wireless is on, and it's a further configuration issue).

You get to the BIOS by pressing some key when the computer first powers up.  On Dells, this is generally F2.  There should be a message when the machine first turns on that says something like "press F2 to enter setup".  Once you're in there, look around for wireless options.

---

### Post by olivesmarch4th on 2006-07-31
That is correct, the toggle does not function.  iwconfig gives the same message; namely, that wireless radio is off.  None of the toggle buttons work. :(

Okay, going to see if I can access the BIOS...

---

### Post by olivesmarch4th on 2006-07-31
F2 did take me into the BIOS but I could find NO MENTION whatsoever of the wireless radio.  The only thing internet related mentioned was the LAN with a simple enable/disable option.

Is it possible to turn the wireless on through the terminal?

#sudo ifup eth1 
only does configuration, not activation-- and it says I'm configured anyways.

This is so frustrating because I know exactly what the problem is!

~Christy

---

### Post by jpkotta on 2006-07-31
Try ```
iwconfig eth1 txpower auto
```

---

### Post by olivesmarch4th on 2006-07-31
SET failed on device eth1 ; Input/Output error.



?????

---

### Post by jpkotta on 2006-08-01
Sorry, prefix with sudo.

---

### Post by Geoff2077 on 2006-08-01
I also have this problem after doing the updates last night. Firefox and email wont connect and I cannot see other computers on my lan.
Strangely though, I can still install software that comes from ubuntu servers.
what is going on here??

---

### Post by olivesmarch4th on 2006-08-01
thanks, JP... I am proud to say I figured out on my own that I needed that prefix!  (maybe I'm catching onto this stuff after all) :)

Still, getting that Input/Output error message:

SET failed on device eth1 ; Input/output error.


What does this mean?  This has gone from, "a minor inconvenience" to "days without internet" ... but I'm determined to work it out!

Thanks,

Christy

---

### Post by jpkotta on 2006-08-02
Unfortunately, I'm running out of ideas.  More suggestions:
```
sudo iwconfig txpower on
```
```
sudo iwconfig power on
``` 

Also, post the output of
```
iwpriv
```

---

### Post by jpkotta on 2006-08-02
> **Geoff2077 said:**
> I also have this problem after doing the updates last night. Firefox and email wont connect and I cannot see other computers on my lan.
Strangely though, I can still install software that comes from ubuntu servers.
what is going on here??

You do not have the same problem, because you can connect to the internet.  I suspect it has something to do with DNS.  If ```
ping 64.233.187.99
```
works but
```
ping google.com
```
doesn't, then you know it's DNS.

---

### Post by olivesmarch4th on 2006-08-02
JP, none of those alternates worked. :(

results of iwpriv (uh, I have to type this by hand):

eth1 available private ioctls

set_power... 8BEO : set 1 int  & get 0

get_power...      : set 0      & get 80 char

set_mode...       : set 1 int & get 0

get_mode...       : set 0      & get 80 char

set_preamble      : set 1 int  & get 0

get_preamble      : set 0      & get 16 char

reset             : set 0 int  & get 0

sw_reset          : set 0 int  & get 0

monitor           : set 2 int  & get 0


Well, there you go.  I really appreciate you trying to help, for real.

---

### Post by jpkotta on 2006-08-03
That looks the same as mine.  How about running this command and posting the output:
```
sudo iwconfig eth1 txpower on ; dmesg | tail -n 20
```

BTW, do you know how to use copy/paste with the terminal?  Copy is selecting text, paste is middle mouse button (usually the wheel).

---

### Post by olivesmarch4th on 2006-08-08
Thanks for hanging in there with me, sorry for the delay!

Yes, I know how to copy and paste, but I cannot easily access the internet using my Linux computer without wireless, so it's rather hard to copy and paste from one computer to another!

I did, however, use a flash drive and transfer the document so I can copy and paste it through windows.

Here is the result of the command:

Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Input/output error.
[17179598.864000] ppdev: user-space parallel port driver
[17179600.028000] apm: BIOS not found.
[17179600.480000] [drm] Initialized drm 1.0.1 20051102
[17179600.484000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179600.484000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[17179601.948000] Bluetooth: Core ver 2.8
[17179601.948000] NET: Registered protocol family 31
[17179601.948000] Bluetooth: HCI device and connection manager initialized
[17179601.948000] Bluetooth: HCI socket layer initialized
[17179602.004000] Bluetooth: L2CAP ver 2.8
[17179602.004000] Bluetooth: L2CAP socket layer initialized
[17179602.088000] Bluetooth: RFCOMM socket layer initialized
[17179602.088000] Bluetooth: RFCOMM TTY layer initialized
[17179602.088000] Bluetooth: RFCOMM ver 1.7
[17179616.624000] NET: Registered protocol family 10
[17179616.624000] lo: Disabled Privacy Extensions
[17179616.624000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179616.624000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179616.624000] IPv6 over IPv4 tunneling driver
[17179697.156000] ipw2200: Failed to send TX_POWER: Command timed out.



Hope that helps!  Thank you a million times!

Olives Always,
Christy

---

### Post by homerhomer on 2006-08-08
I was able to get mine to work with this command after boot up


sudo iwpriv wlan0 SetRates "1,2,5,11,54"

---

### Post by olivesmarch4th on 2006-08-08
Thanks for the suggestion, homer.

When I run that command, I get:

> wlan0      no private ioctls.


:(

---

### Post by bensexson on 2006-08-08
You will want to use eth1 instead of wlan0.

---

### Post by olivesmarch4th on 2006-08-08
*smacks forehead*

Uh, right.

Okay, so now I get "Invalid Command: SetRates."

---

### Post by jpkotta on 2006-09-17
Did you ever get this working?  The allowed iwpriv commands are listed when you run iwpriv (you have already posted the list of available commands in this thread).  I'm sorry, but I'm still out of ideas.

---

### Post by mrlarone on 2006-09-22
hello, i'm having the same problem (acer 2420, centrino 2200a/b/g wifi card).  i ran the cmds:

$sudo iwpriv set_power 1

then

$iwlist eth1 power

this reports eth1 as on.

Q: does this cmd really turn the card on or only perform a boolean switch?

is this newbie fluke or blunder? i'm guessing the latter as it doesn't seem to help my situation. if it is fluke how do i proceed from here?

---

### Post by meech on 2006-09-22
I am having a similar problem with my wlan. I have a toggle button for the radio which seems to be on. Here are details regarding requested info:

iwconfig:
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"x"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.457 GHz  Access Point: x
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


ifconfig:

eth0      Link encap:Ethernet  HWaddr x
          inet addr:x  Bcast:x  Mask:255.255.255.0
          inet6 addr: x Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8577110 (8.1 MiB)  TX bytes:1139019 (1.0 MiB)
          Interrupt:185 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr x
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7716 errors:0 dropped:202 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:857723 (837.6 KiB)  TX bytes:2666 (2.6 KiB)
          Interrupt:10 Base address:0x4000



iwconfig eth1 txpower auto:

Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Operation not permitted.


Any advice you could offer would be greatly appreciated.
Michelle

---

### Post by mrlarone on 2006-09-23
Michelle you beauty,

run this cmd:

$sudo iwconfig eth1 power 1 

then this one to confirm the card is powered on.

$iwlist eth1 power

remember if you run a cmd and you get a permissions error put 'sudo' in front of the cmd to enable root permissions.

thanks for the spark of inspiration :D 

p.s. if you want to turn the card off run

$sudo iwconfig eth1 power 0

let me know if you have any futher issues.

---

### Post by meech on 2006-09-24
Absolutely, anytime :)

---

### Post by meech on 2006-09-25
```

$sudo iwconfig eth1 power 1
Password:
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device eth1 ; Operation not supported.

$iwlist eth1 power
eth1

```

Also, Network Manager (with a red "x" on the eth1 icon) is saying the status of eth1 is 'disconnected;' however, eth1 was working without issue yesterday until I must have altered some conf files and possibly something else for the sake of WPA.

Here is the contents of /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid xxxx
#pre-up wpa_supplicant -Bw -Dndiswrapper -ieth0 -c/etc/#wpa_supplicant.conf
#post-down killall -q wpa_supplicant
#wireless-essid materEatsPinkyToes

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

I know I am not obtaining the wrt54g's MAC anymore.

Thanks for your help, any advice really appreciated.
Michelle

/edit My wireless radio had decided to turn itself off and since the hardware-based- switch doesn't work in Ubuntu, I switched to XP only long enough to rectify the problem. I'm using eth1 for this connection, my only concern is whether or not people using this setup will have to switch boot from XP in order for their cards to work, as opposed to cold boot to Ubuntu. Again, thank you for your help :D

---

### Post by mrlarone on 2006-09-25
looks like you're a bit more advanced than me ;) 

have you tried running the cmd you showed me with sudo, i.e:

$sudo iwconfig eth1 txpower auto

i read in another thread regarding this issue people settled for booting from XP to Ubuntu after ~20 posts with other ideas, which was why i was so happy when mine started working.

the only thing i can think to ask is whether have you got the latest drivers installed? if not maybe newer ones support power management.

---

### Post by nopainogain on 2007-01-25
This is my first post on this forum, im also a linux noob,
 I have been an IT Network consult in the windoze/Cisco world for years but i would rather be a linux guy than a windows guy. I am posting because i received a solicitation from a potential customer who is using ubuntu and has had trouble getting his wireless up and running. when i ran it from the Live DVD of 6.10 found in Linux Format magazine on my dell c600 p3 1ghz laptop i experienced similar problems. i figured i needed to sit back and install ubuntu on the laptop fully then configure it. 
I have gained a lot of understanding just reading your replies to users' posts in here today and hope to be around here a long time to help when i can. 

Thanks
nopainogain

---

### Post by jpkotta on 2007-02-13
So I was just playing around with my laptop, and I decided to find the command to power the radio off.  I can do this with Fn+F2, and I'm starting to suspect that the BIOS controls it (i.e. no such command).  Anyway, I found something interesting.  If you play with the sysfs, you can actually completely disable the wireless.  The script /etc/acpi/wireless.sh toggles it on and off.  In case you don't have it, I have attached it.  If you do this, it will not even show up when you run iwconfig.  I don't know yet how complete disabling and radio off together affect power consumption.

Edit:
More evidence for BIOS control: I did all of the tests [here]("https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch"), and nothing except: when using the showkey command, I got messages from the driver.
```
[17434002.892000] ipw2200: Failed to send CARD_DISABLE: Command timed out.

```

Then looking at /var/log/messages, I see:```
Feb 13 17:05:34 localhost kernel: [17434183.124000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Feb 13 17:05:42 localhost kernel: [17434190.772000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
```
when I press the wireless enable/disable key.  Other details: CARD_DISABLE messages appear in /var/log/messages also.  CARD_DISABLE messages do not appear when hotkey-setup is restarted.  The hotkey always worked (e.g. it would always toggle radio on/off) in all tests I did.

I still don't know exactly what to make of all this, but it seems like the key is talking directly to the kernel (driver), thus if the hotkey doesn't work, a kernel patch may be necessary.  For OP, perhaps a downgrade of the kernel will do it.  I have heard reports of Windows doing strange things to hardware (like turning them off) that Linux just doesn't know about.

---

### Post by dsorensen on 2007-03-06
I had the same problem where my wireless was listed with radio off and nothing would turn it back on until i did the following:

Download the tar/gz of acerhk at [http://freshmeat.net/projects/acerhk/]("http://freshmeat.net/projects/acerhk/")

Once finished downloading, extract to a folder and then navigate to that folder in the console, then execute the following commands

```
make
sudo make install
modprobe acerhk
echo 1 > /proc/driver/acerhk/wirelessled
```

if everything worked run iwconfig to see if the power is now on

basically your installing a driver that allows you to access special key codes that can turn on/off the wireless card.

---

### Post by steelblue77 on 2007-03-17
Thanks for posting this info.  My fiancee just about had a fit when her laptop wouldn't reconnect with out wireless network.  We don't use the function keys normally, so I didn't suspect it was so simple.  Until coming here.  Sure enough, it was the Fn-F2 problem.

She has a Gateway that is always finicky about it's keyboard and she must have brushed the right combination of keys to turn the radio off.

---

