---
title: "Wireless card suddenly UNCLAIMED (Intel PRO/Wireless 2915ABG)"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by ydnew423 on 2009-09-20
I have been searching the forums for a while but have not seen a solution to my problem (so sorry in advance if this has already been answered!)

I installed Ubuntu 9.04 this past week and everything was working great. At one point I lost wireless, and then realized I had accidentally turned off my card by hitting Fn+F2. This is the only way to toggle the power (no external hardware switch).

Yesterday, the wireless was working fine. Today, when I turned on my computer, no wireless. I tried to hit Fn+F2, but nothing happened. I did notice that when I right click the network icon, I no longer get an option to enable/disable wireless. I opened a terminal and typed "sudo lshw -C network" and get this for the wireless card:

 *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=24 mingnt=3

One post I read said something about enabling the card in BIOS helped them. I tried this, but it made no difference. Ubuntu's help talked about using ndisgtk package. I tried to use the .inf file from Intel's website, but I'm told it's an invalid driver. Am I doing it wrong? Do I even need to do this since my card worked fine with whatever drivers were included with Ubuntu?

Any help is appreciated! Please keep it simple, though, since I'm new (i.e., dumb it down!)

Thanks!

---

### Post by ydnew423 on 2009-09-20
New approach... I read that the driver for this card (IPW2200) is included in Ubuntu. Is there a way to reinstall this through the terminal?

---

### Post by Whiffle on 2009-09-20
Well, its a kernel module but I don't see any reason reinstalling it would make a difference.

what happens when you do:
```

sudo modprobe -r ipw2200
sudo modprobe ipw2200

```

---

### Post by ydnew423 on 2009-09-20
Thanks for your help! Like, I said, I'm new and kind of fudging my way at this point.

This is what I get:

```
wendy@wendy-laptop:~$ sudo modprobe -r ipw2200
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wendy@wendy-laptop:~$ sudo modprobe ipw2200
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

```

---

### Post by Whiffle on 2009-09-20
Hmm, I don't see why ndiswrapper is installed (you don't need it).

But it looks like the module loaded correctly.  What is the output of 
```

sudo iwconfig

```

---

### Post by ydnew423 on 2009-09-20
I get this:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Whiffle on 2009-09-20
Ok the driver is loaded, but for some reason your card is powered off.

Try this:
```

cat /sys/bus/pci/drivers/ipw2200/000*/rf_kill

```

if it comes back with a "1", then I'm on the right track.

---

### Post by ydnew423 on 2009-09-20
:-( I got a "0".

---

### Post by Whiffle on 2009-09-20
Okie dokey, I guess thats why Fn+F2 wasn't doing anything.  Lets take a step back and look at what happened when we loaded the driver.

Do this:
```

sudo modprobe -r ipw2200
sudo modprobe ipw2200

```

and then run this:
```

dmesg | grep ipw2200

```

It'll spit back some stuff about your driver, paste that up here.

---

### Post by ydnew423 on 2009-09-20
Weird. I don't know if it something you had me type, but my wireless suddenly reappeared. Before when I right-clicked, it only showed a wired connection. Suddenly, I have the wireless and it connected to my router.

---

### Post by Whiffle on 2009-09-20
Hmm thats strange.  Does it ever do anything else strange?   Maybe the card is a little loose in the slot or something.

The only thing we've done that would change anything is the modprobe stuff, which loads/unloads the driver.

---

### Post by ydnew423 on 2009-09-20
Well, thank you a MILLION!! I didn't type in your last code... should I even though it is working again?

---

### Post by Whiffle on 2009-09-20
I'd go ahead and do that last one, it'll kill your wireless for a few seconds but it might shed some light into whats going on so we can prevent it.

---

### Post by ydnew423 on 2009-09-20
Okay, here's the output:

wendy@wendy-laptop:~$ dmesg | grep ipw2200
[ 7739.538822] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[ 7739.538826] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[ 7739.538914] ipw2200 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[ 7739.546251] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[ 7739.546331] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[ 7739.849683] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[ 9967.021232] ipw2200 0000:02:03.0: PCI INT A disabled
[ 9974.927981] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[ 9974.927991] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[ 9974.929017] ipw2200 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[ 9974.929177] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[ 9974.929276] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[ 9975.062055] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[10249.482588] ipw2200 0000:02:03.0: PCI INT A disabled
[10256.264432] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[10256.264442] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[10256.264582] ipw2200 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[10256.264741] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[10256.264842] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[10256.408336] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)

I don't recall ever having issues with this card before (other than my accidental Fn+F2... I was going for another key combo and hit F2). It's a Dell Inspiron 600m and I've never tried to open the laptop insides.

---

### Post by Whiffle on 2009-09-20
Yeah I don't see anything wrong there.  *shrug*  I guess I'd just go on about my business then.  Good luck!

---

### Post by ydnew423 on 2009-09-20
*Crosses fingers* I'll just bookmark this thread for "just in case"...

Thank you so much!

---

### Post by ydnew423 on 2009-09-21
*UPDATE*

In case anyone reading this is having the same issue, I found out that every time I started up my computer, my wireless was missing. I had to use Whiffle's code to turn it on every single time:

```
sudo modprobe ipw2200
```I began scouring the internet to figure out a way around entering this at every startup. I FINALLY found the following solution. If this wrong, or someone has a better solution, please post it! It is currently working for me, so I thought I'd share.

I stumbled across this [thread]("http://ubuntuforums.org/showthread.php?t=1213671") that talked about adding code to a file called "modules". To dumb it down for those like me, this is what I did:

1) Alt+F2 pops up a window where you type  "gksudo nautilus" (found this trick at [this site]("http://www.psychocats.net/ubuntu/permissions"); this allows you to save changes to the modules file.) Type in your password when prompted.

2) Navigate to your modules file. For me this is /File System/etc/modules

3) Open modules. My document only showed one line that read "lp". Under that I typed "ipw2200" and saved. 

I'm hoping this will continue working... and help someone else! :-)

---

### Post by nealkemp on 2010-03-01
Hi guys,

I am now suffering the same issue that Wendy had, but unfortunately the solution she came up with doesn't seem to work for me.

Here is what I see when I carry out the commands suggested so far...

```
nealkemp@NealsLaptop:/$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:a6:4f:87
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.5 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:dfbfe000-dfbfffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
       resources: memory:dfbfd000-dfbfdfff
nealkemp@NealsLaptop:/$ sudo modprobe -r ipw2200
nealkemp@NealsLaptop:/$ sudo modprobe ipw2200
nealkemp@NealsLaptop:/$ dmesg | grep ipw2200
[   20.788335] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   20.788339] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   20.788417] ipw2200 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.788485] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   20.788522] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[   21.174457] ipw2200: Unable to load ucode: -62
[   21.174472] ipw2200: Unable to load firmware: -62
[   21.174475] ipw2200: failed to register network device
[   21.264244] ipw2200 0000:02:03.0: PCI INT A disabled
[   21.264260] ipw2200: probe of 0000:02:03.0 failed with error -5
nealkemp@NealsLaptop:/$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

nealkemp@NealsLaptop:/$ cat /sys/bus/pci/drivers/ipw2200/000*/rf_kill
cat: /sys/bus/pci/drivers/ipw2200/000*/rf_kill: No such file or directory

```So the wireless card is unclaimed, doing a modprobe doesn't seem to do anything and the directory 000* doesn't exist (ipw2200 is there though)

This is pretty strange as up until today I was running Ubuntu installed inside WinXP and everything was working fine, I decided to ditch Windows today as I was really happy with it, so formatted and installed a clean version of Ubuntu using the same .iso as I had used to install inside windows (booted from a USB). The version I installed is 9.10.

Through some investigation of reinstalling ipw2200 drivers and firmware I have discovered that the file

/lib/modules/2.6.31-14-generic/build/include/linux/autconf.h

does not contain any of the following strings

#define CONFIG_NET_RADIO 1
#define CONFIG_IPW2200 1
#define CONFIG_IPW2200 1

I am not sure how important that is but thought I would mention it.

Thanks in advance for any help or suggestions, this has been driving me a bit crazy today!

Regards,

Neal

---

### Post by nealkemp on 2010-03-02
I have had an equally mysterious resolution of my wireless issues. When I switched my laptop on this morning, the wireless networks had reappeared and started working. They are still there on a reboot so I can only assume things are fixed, I have absolutely no idea how though.

---

### Post by subhrm on 2010-08-28
HI All,
 
I am also facing the same problem :(. I would tryout the instructions mentioned in this thread and let you know if it works for me.

---

### Post by subhrm on 2010-09-14
I was able to solve it with **noapic** option in GRUB.

---

