---
title: "Internet connection suddenly gone"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by rayhorn13 on 2007-10-08
All of a sudden, my internet is totally gone.

My recent activity: I just got finished changing my ATI card to an nVidia card.  Since I didn't know any better, I changed it first & had to run "sudo dpkg-reconfigure xserver-xorg" to get the gui to come back up.  From there I tried Automatix to install the nVidia drivers.  That gave me a blank screen upon reboot, so I went into recovery mode and ran "automatix-nvidia-restore" like it told me to do.  
No problems so far.

I got back in and decided to uninstall a few things as a "clean-up" before trying the drivers again.  The only thing I uninstalled (I think) was the security package (clamshell antivirus & guarddog firewall).  

Since I did that, I have no internet.  I can't connect with anything (browsers, update manager, etc.).  I even had to boot into XP to post this.  I know it's not a mechanical thing because I'm using the same computer & network card to send this.

I'm trying to get into Ubuntu, but haven't gotten very far into it yet so I know a little, but probably just enough to be dangerous.

Is there something I can do to repair the connection or reinstall it?

Can anyone please help me shed some light on this??

***Please & thank you in advance!***

---

### Post by noob12 on 2007-10-09
How gone?  

Is this a wired connection?

First check that the device shows up in **lspci -nn** output.  What kind of ethernet device do you have? Can you post the relevant line from that?  If it is gone here and is not an onboard device, check that you didn't unseat the card by mistake.  Also check the output of **dmesg** for signs of PCI routing issues.

If it shows up there and looks ok, then run **sudo lshw -C network** and see whether the device has been claimed or not by a driver. If it is unclaimed, then check **dmesg** for clues.  If it is claimed, what driver shows in the configuration line of the output?  

Does the interface show up in **ifconfig -a** ?

What does **sudo ethtool eth0** say?  (Replace eth0 with the actual name of the interface if it is different.)

---

### Post by rayhorn13 on 2007-10-09
Thanks for the reply, Noob.

It is an on-board, wired NIC.  I do have a wireless PCI card that I have never configured in the box as well.

As for your other questions?  You might as well have been speaking Latin because I didn't get most of it, but I did run the tests in the order that you listed them (if it mattered).

The attached ZIP file has all of the output from the tests in 2 different TXT files.

I wish I knew what I was looking at (or for, specifically).  Can you help??

MANY thanks in advance.

:guitar:

---

### Post by noob12 on 2007-10-10
When you said "totally gone" I thought you had meant your ethernet interface had gone, which can happen with driver issues, but yours is there, looking pretty happy.

I wasn't sure you would be able to post from the machine.  But this is good. 

What this 
```

dad@dad-desktop:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:13:20:3b:d7:dc
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72.1 duplex=full firmware=5751-v3.23a ip=192.168.1.43 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:dbff0000-dbffffff irq:16

```
tells us is that your wired NIC is very much there.  It  is using the tg3 driver.  It has an established Ethernet link 
at 100 mbps full duplex and it got an ip address 192.168.1.43.


Here's another view of it from your **ifconfig -a** output
```

eth0      Link encap:Ethernet  HWaddr 00:13:20:3B:D7:DC  
          inet addr:192.168.1.43  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe3b:d7dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:764 (764.0 b)  TX bytes:838 (838.0 b)
          Interrupt:16 

```

So far this all looks healthy and normal. 

Can you post the output of these commands to investigate further?
```

cat /etc/network/interfaces

route -n

cat /etc/resolv.conf

sudo iptables -nL

```

Here are some tests you can do to determine how much more of your connectivity is still healthy.

From the output of the **route -n** command above you should see one row with a UG in the Flags column.    The address in the second column of that row is probably 192.168.1.1  (or 192.168.1.254).  It is your router.  

Whatever that address is, use that address and try to ping it.  For example if you see 192.168.1.1 try
```

ping -c 4  192.168.1.1

```

If you can reach that also try to ping an external point like this google IP
```

ping -c 4 64.233.167.99

```

See if you can resolve a hostname
```

host www.google.com

```

See if you are able to visit  Google in Firefox using the ip address directly in the URL like this
```

http://64.233.167.99/

```

---

### Post by rayhorn13 on 2007-10-10
I tried to get in to conduct some of the tests, and couldn't get to the login - nothing but a flashing cursor in the upper-left corner.

SO...  I am going to reinstall the whole she-bang.  I've posted a new thread [HERE]("http://ubuntuforums.org/showthread.php?t=572827") concerning reinstalling on a dual boot machine.

Noob, I wanted to thank you again for the help - even though it was for naught.  I wasn't going to leave you hanging & just not reply since you obviously spent some time looking at my problem.

---

