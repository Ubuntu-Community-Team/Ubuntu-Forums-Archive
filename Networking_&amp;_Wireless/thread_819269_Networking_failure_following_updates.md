---
title: "Networking failure following updates"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by jbc-wales on 2008-06-05
Brand new pc, running Hardy 8.04, dual core etc.

System was working normally this am. 
System updates advised: all updates added.

Following required restart, the internet connection was lost.

Network manager no longer recognises the network device (ethernet-connected ASDL modem).

Cannot use manual configuration to connect

Tried ```
sudo pppoeconf
```

Declares NO INTERFACE FOUND, Sorry, no working internet card could be found...

Offers to run modconf to load driver manually

returns: ```
/usr/sbin/pppoeconf: 520: modconf: not found
```

Ran Ubuntu Hardward Tests

Realtek Ethernet Controller IS detected...
But then reports "No Internet connection"

Tried ```
dhclient
```

Reports: ```
No broadcast interface found - exiting
```

ifconfig returns

```
lo ...(etc)
```

but no eth0 or eth1

```
lshw -C network
```

returns: network UNCLAIMED and no LOGICAL NAME

Am now at my wits end. 

Can anyone point me in a right direction?

Is this likely to be a hardware failure? (An orange light on the ethernet controller is lit)

If all else fails, is there a reliable way to roll back the updates? And then presumably selectively update?

Any other advice?

(I'm a newcomer to Ubuntu...though learning fast...generally the hard way!):(

---

### Post by cdtech on 2008-06-05
If your using the ndiswrapper:

Try modprobe -r ndiswrapper and modprobe -r b43 the reload ndiswrapper and b43 in that order and see if it comes back.

Let me know...

---

### Post by chili555 on 2008-06-05
Generally, when an interface is unclaimed it means the appropriate driver module did not load. We can help you better if we see the ethernet portion of:```
sudo lshw -C network
```We can, hopefully, find out what module to load and what may be done to load it automatically.

Incidentally, when an update brings unexpected surprises, you can boot into the previous kernel and, in almost every case, your good working configuration, by interrupting the boot process when you see the GRUB bit on the screen count down a whopping 3 seconds. Hit the Esc key and select the previous kernel version. Press Enter and you will boot into the 'before update' version. It's very useful to be able to go on line and troubleshoot, fix the issue, and then boot back into the latest kernel.

Hmmm, wonder if Vista has this...

Ndiswrapper and b43 on a Realtek ethernet card? Probably not.

---

### Post by cdtech on 2008-06-05
My bad, I just seen that. :)

I'm getting way ahead of my own problems with the Hardy upgrade.

---

### Post by jbc-wales on 2008-06-05
First of all: huge thanks for your response(s). It's great not be on my own with this (up to now, I've resolved all Ubuntu issues from archived responses)

Second, the GRUB tip was really useful. I'm posting this via the previous kernel, so to speak. 


Third: here are the lshw reports, before (8.04.17?) and after, kernel upgrade (8.04.18?):

 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:8c:0d:0d:29
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.006.00-NAPI duplex=full ip=192.168.2.6 latency=0 link=yes module=r8168 multicast=yes port=twisted pair speed=100MB/s


Now: having booted in latest kernel (.18)

 *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0


Hope that helps...

(I didn't understand the business about  ndiswrapper, but understood from cdtech's comments that it was best to ignore them for now....)

---

### Post by chili555 on 2008-06-05
> driver=r8168 driverversion=8.006.00-NAPIWhere did this little gem come from? Did you download and install from a .tar.gz file? I'm guessing that you did. If so, please boot back into the newest kernel and build it a shiny new driver, too:```
cd r8168-8.006.00/src
make clean
make
sudo make install
sudo modprobe r8168
```Substitute your directory name, if it's not *r8168-8.006.00*.

When you compile a driver from source, you build a module, that is, an r8168 driver, for the kernel then running. You got a new kernel in the update, so now you must build a new module. 

If my assumption is incorrect, post back and we'll try to help.

---

### Post by jbc-wales on 2008-06-05
The pc is new, so I guess it was done by the vendor, who is an Ubuntu partner, f/w/i/w.

> Substitute your directory name, if it's not r8168-8.006.00.

This is where I get a bit lost....

I can't find either a file or a folder / directory with that name, using search. How then can I 'cd' to it? How would I substitute my directory for it?

:confused:

---

### Post by chili555 on 2008-06-05
The easy solution: contact the vendor and ask them.

The less easy, but self-reliant way: Open a terminal and do:```
sudo updatedb
locate r8168
```Maybe we can see where the directory is hiding, if it's there at all.

The harder, but do-able way: compile and install your own. Sound scary? It is, a little, especially for a new computer. Let's keep that as a last-ditch option for now.

---

### Post by jbc-wales on 2008-06-06
Right, I've found a file and the directory it's in:

/lib/modules/2.6.24-17-generic/kernel/drivers/net

the file is R8168.ko

So, how would that fit into the "make clean" / rebuild module sequence?

---

### Post by chili555 on 2008-06-06
That's just the module from the previous kernel. Please note:> /lib/modules/2.6.24-**17**-generic/kernel/drivers/netHowever, the update brought you -18. You can verify this with:```
uname -r
```Mine says:```
2.6.24-18-generic
```That is, -18, not -17.

I repeat my advice above. One addition is a bit of an ugly hack; ugly, but reversible, if it doesn't work. Beautiful if it does. I have never tried this, so I make no guarantees. ```
sudo cp /lib/modules/2.6.24-17-generic/kernel/drivers/net/r8168.ko /lib/modules/2.6.24-18-generic/kernel/drivers/net/r8168.ko 
```We're saying, just copy my -17 module to -18. After a reboot, it will probably work. If it doesn't, you can remove the copy with:```
sudo rm -f /lib/modules/2.6.24-18-generic/kernel/drivers/net/r8168.ko
```

Frankly, before I resorted to a hack, I'd contact the vendor of your laptop.

---

### Post by jbc-wales on 2008-06-07
Well the new pc was completely dead this am! So, having experienced exactly the same fault a fortnight ago, resulting in a replacement hard drive, I am certainly going to be contacting the vendor... to obtain a refund!

Thanks for you assists; it's been a useful learning experience, esp. re the Kernel option at login.

shalom, from Wales, UK
John

---

