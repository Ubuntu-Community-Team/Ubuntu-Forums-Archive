---
title: "Davicom Ethernet Issue in Feisty"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by Roarden on 2007-09-09
I've messed with this too long and am finally out of ideas.

I have LAN network set up with a Davicom 21x4x DEC-Tulip compatible 10/100 ethernet card.  The card works fine in Windows, but in Feisty, it fails to send or receive any packets.

The card is recognized fine and using the dmfe driver. (there apparently was some similar trouble to mine earlier, but that was with the Tulip driver. It apparently was fixed with feistly) See:[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/48026](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/48026)

I cannot figure out what the issue is-  here is my dmesg and ifconfig

Dmesg is entirely tons of
```
[ 2153.313334] eth1: Tx timeout - resetting
[ 2155.312084] eth1: Tx timeout - resetting
[ 2157.310834] eth1: Tx timeout - resetting
[ 2159.309584] eth1: Tx timeout - resetting
[ 2161.308334] eth1: Tx timeout - resetting
[ 2163.307084] eth1: Tx timeout - resetting
[ 2165.305834] eth1: Tx timeout - resetting
[ 2167.304584] eth1: Tx timeout - resetting
[ 2169.303334] eth1: Tx timeout - resetting
[ 2171.302084] eth1: Tx timeout - resetting
[ 2173.300834] eth1: Tx timeout - resetting
[ 2175.299585] eth1: Tx timeout - resetting
[ 2177.298334] eth1: Tx timeout - resetting
[ 2179.297084] eth1: Tx timeout - resetting
[ 2181.295834] eth1: Tx timeout - resetting
[ 2183.294584] eth1: Tx timeout - resetting
[ 2185.293334] eth1: Tx timeout - resetting
[ 2187.292085] eth1: Tx timeout - resetting

```

Except for a random line of this every now and again
```
[ 1248.027524] Unknown InputIN=eth1 OUT= MAC= SRC=192.168.12.12 DST=192.168.12.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 

```

relevant ifconfig:
```
eth1      Link encap:Ethernet  HWaddr 00:08:A1:05:E7:CA  
          inet addr:192.168.12.12  Bcast:192.168.12.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xd200 

```

Thanks for any help.   It's driving me nuts.

---

### Post by noob12 on 2007-09-09
These
> 
[ 2153.313334] eth1: Tx timeout - resetting
[ 2155.312084] eth1: Tx timeout - resetting
[ 2157.310834] eth1: Tx timeout - resetting

indicate that your problem is probably with the IRQ configuration of the card at boot.
What's likely to be interesting is the whole **dmesg** captured soon after a boot.

I suspect booting with the **pci=noacpi** option will help.  If you need instructions on setting boot options, let me know.

> 
[ 1248.027524] Unknown InputIN=eth1 OUT= MAC= SRC=192.168.12.12 DST=192.168.12.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58

This message is from iptables configured using Firestarter.  You might want to get your network working first then enable your firewall just to make sure it isn't in the picture while you're debugging basic connectivity.

The ifconfig output suggests you probably set the address manually.  The counts are all zero.

---

### Post by Roarden on 2007-09-10
Thank you for your help.

Unfortunately however, adding pci=noacpi in my grub option crashed the system.  Should I be doing something in the bios?

Also, for reference, the actual card is a CNET Pro200WL.   I've found other people with the same or similar problem, and the pci=noacpi fix has worked for some. (but not me :( ) 
[Here is the dmesg at startup]("http://rubenstube.googlepages.com/dmesg_output_startup.txt").  Thanks again for your time.  I appreciate it.

---

### Post by noob12 on 2007-09-10
UPDATE:  Can you confirm you are running Feisty (2.6.20 kernel)?  **uname -r**    Prior kernel versions had tulip and dmfe drivers loading for some of the Davicom devices and this used to cause problems (which you could solve just by blacklisting tulip and loading dmfe).  That was fixed for Feisty, and your machine seems to be loading dmfe at boot.

Based on poking around the web, it appears that it is not a problem with IRQ routing, but a problem with the dmfe driver.  One posting suggests that forcing 10mbps full duplex works. 

You should file a bug on launchpad.  Hopefully the response to your bug report or other readers on the forum will suggest a better solution, or it means getting a new card and avoiding the Davicom chipset.

To try the 10mbps workaround one or both of these methods should work.  Let me know if the timeout messages go away after doing this, and if so you can at least run eth1 somewhat reliably.  

Watch your kernel log in a one terminal window by typing **tail -f /var/log/kern.log**.  See if the eth1 timeouts stop after doing one of these:

Try this first
```

sudo ifdown eth1
sudo ethtool -s eth1 speed 10 duplex full autoneg off
sudo ifup eth1

```

If that doesn't work, try this:
```

sudo /etc/init.d/networking stop
sudo modprobe -r dmfe
sudo modprobe dmfe mode=4
sudo /etc/init.d/networking start

```

See if after either of these the timeouts go away and the connection becomes more reliable.
If so, I'll tell you how to configure these to work automatically.

---

### Post by Roarden on 2007-09-10
Yep, I can confirm I'm on the 2.6.20 kernel.  I had already tried blacklisting tulip just out of curiosity to see if it did anything but no such luck. 

When I tried to set 10mbps duplex with your code this was the response
```
chris@chris-feistyfawn:~$ sudo ethtool -s eth1 speed 10 duplex full autoneg off
Cannot get current device settings: Operation not supported
  not setting speed
  not setting duplex
  not setting autoneg

```

Driver issue still?

And if it helps,  when I turn eth1 back on (ifup eth1)  this is the response:
```
RTNETLINK answers: File exists
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2

```

I really appreciate your help with this. I'll file a bug report on launchpad a little later today, and if nothing pops up in the next couple days I think I'll just scrap the card and pickup another.   Thank you!

---

### Post by noob12 on 2007-09-10
DId you try the second method:
```

sudo /etc/init.d/networking stop
sudo modprobe -r dmfe
sudo modprobe dmfe mode=4
sudo /etc/init.d/networking start

```
That tells the driver using a driver option at load time to be 10mbps full duplex.

---

### Post by Roarden on 2007-09-10
Yeah... I had- no such luck.  Ah well.  Still getting the Tx timeout message.

---

### Post by noob12 on 2007-09-10
I strike out. Sorry.  Seek better help :)

---

### Post by NightFlyer on 2007-09-13
Well the first method worked perfectly for my problem so I'd like to know how to set it up auto please :)

---

### Post by noob12 on 2007-09-13
NightFlyer:  Sure. Which method worked for you?  If you let me know I can tell you how to set it up to happen automatically.

---

### Post by NightFlyer on 2007-09-13
this is the one that worked for me 

```

sudo ifdown eth1
sudo ethtool -s eth1 speed 10 duplex full autoneg off
sudo ifup eth1

```

---

### Post by noob12 on 2007-09-13
OK.  I'll use **eth1** as the example, but if your interface is **eth0** or something else, just substitute your actual interface name in the text below.

Edit your **/etc/network/interfaces** file (**sudo gedit /etc/network/interfaces**)

In general, in the editor find the stanza (section) for eth1 and add this immediately after the **iface** line.
```

pre-up ethtool -s eth1 speed 10 duplex full autoneg off

```

This says to run this command just before bringing the interface up.

If you have no section for your interface in the **/etc/network/interfaces** file, then you will need to add a section like this:
```

auto eth1
iface eth1 inet dhcp
pre-up ethtool -s eth1 speed 10 duplex full autoneg off

```
You should omit the **auto eth1** line if you aren't always plugged in and you don't want the interface to come up automatically at boot time.

---

### Post by NightFlyer on 2007-09-13
Thankyou for your help noob12 it all works perfectly now :)

---

