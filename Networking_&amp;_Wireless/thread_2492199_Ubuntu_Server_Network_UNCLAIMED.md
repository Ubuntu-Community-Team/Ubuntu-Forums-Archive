---
title: "Ubuntu Server Network UNCLAIMED"
date: 2023-11-02
forum: Networking &amp; Wireless
---

### Post by salehbozeed on 2023-11-02
Hello

I'm using my HP laptop as a local server for a radius system which is running on Ubuntu server v14.04 and I'm having a problem with the ethernet.

"lshw -c network" output:
```
 *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@000:00:1f.6
       version: 21
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f021ffff

```

"lspci | grep -i ethernet" output:
```
00:1f.6 Ethernet controller: Intel Corporation Device 15d7 (rev 21)
```

---

### Post by MAFoElffen on 2023-11-03
A few things would help us to help you...

What model is this laptop? 

Is it 64bit or 32bit OS?

Why is it on 14.04? Is there any reason why it is not on a supported OS like 22.04?

What does it show for 
```

lspci -nnv | grep -A1 -Ei 'ethernet|network'

```

---

### Post by salehbozeed on 2023-11-03
-It's HP EliteBook 840 G4
-64bit
-I know that 14.04 already reached EOSS but unfortunately, it's not up to me to choose. the only option for a radius system that provides my needs is running on Ubuntu server 14.04.

Here's the output of ```
[COLOR=#000000][FONT=&quot]lspci -nnv | grep -A1 -Ei 'ethernet|network'[/FONT][/COLOR]
```

00:1f.6 Ethernet controller [0200]: Intel Corporation Device [8086:15d7] (rev 21)
        Subsystem: Hewlett-Packard Company Device [103c:828c]
--
02:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)
        Subsystem: Intel Corporation Device [8086:1010]

---

### Post by chili555 on 2023-11-03
> Intel Corporation Device [8086:15d7] (rev 21)The usual driver for this device is called e1000e. I doubt that it existed in Ubuntu 14.04. Check:

```
modinfo e1000e | grep -i 15d7
```Perhaps you could find a version of e1000e to download that is compatible with your nine year old kernel version and gcc version. Perhaps you could download and install the dozens of prerequisites; again, compatible with 14.04, without any internet connectivity. Perhaps you could then compile and install it. I am a bit skeptical, however.

---

### Post by MAFoElffen on 2023-11-03
Still unanswered: Is it 64bit or 32bit OS? Why is it on 14.04? Is there any reason why it is not on a supported OS like 22.04? What is the Model?

Because Ubuntu 14.04 reached end of support on Sep 19th 2019, 4 years ago... If you did get on a supported release, it would have drivers for it.

---

### Post by salehbozeed on 2023-11-03
@[chili555]("https://ubuntuforums.org/member.php?u=35909") the command didn't give any output. so, I guess that means it doesn't exit in 14.04

---

### Post by salehbozeed on 2023-11-03
@[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547") I did answer your questions! please check my reply again.

---

### Post by chili555 on 2023-11-03
> **salehbozeed said:**
> @[chili555]("https://ubuntuforums.org/member.php?u=35909") the command didn't give any output. so, I guess that means it doesn't exit in 14.04
No response at all means that the module does exist but that it doesn't cover your exact device. That's common when we install an old Ubuntu version and use relatively newer hardware devices. Quite simply, in 2014, when the latest e1000e driver was published, the Intel Corporation Device [8086:15d7] (rev 21); Subsystem: Hewlett-Packard Company Device [103c:828c] didn't yet exist.

Please try:

```
sudo -i
modprobe e1000e
echo 8086 15d7 > /sys/bus/pci/drivers/e1000e/new_id
dmesg | grep e100
exit
```

Any improvement?

---

### Post by salehbozeed on 2023-11-03
When I type sudo -i it takes me back to the radius system main menu!
So I tried
```
sudo -i modprobe e1000e
echo 8086 15d7 > /sys/bus/pci/drivers/e1000e/new_id
```
but it freezes after that

---

### Post by chili555 on 2023-11-04
> it freezes after thatThat was the last hail Mary, last ditch, desperate technique we could try.

The only suggestion I have left is to try a USB-to-ethernet adapter. They are almost always fully supported in even older versions of Ubuntu. Try one with a generous return period in case you stumble on the one exception that doesn't work.

I'm sorry I have no other useful suggestions.

---

### Post by chili555 on 2023-11-04
> it freezes after thatThat was the last hail Mary, last ditch, desperate technique we could try.

The only suggestion I have left is to try a USB-to-ethernet adapter. They are almost always fully supported in even older versions of Ubuntu. Try one with a generous return period in case you stumble on the one exception that doesn't work.

I'm sorry I have no other useful suggestions.

---

### Post by TheFu on 2023-11-04
Load a supported OS onto the real hardware, then run a virtual machine and put 14.04 inside it.  This way, the actual hardware used is disconnected from the out-of-support 14.04 OS.  You may actually find that running the Radius service inside a Linux Container to be an even better choice.  Again, the actual hardware support would be abstracted away from the out-of-support 14.04.

If using a VM, choose virtio for the network adapter to the guest 14.04 VM.
If it were me, I'd try to get an lxd compatible image of 14.04.  To see the available lxc container images, 
```
lxc image list images:ubuntu
```

You'll need to know the damn release codename - they don't use "14.04" in the image descriptions and I don't have a clue what the codename for it was anymore.

lxd/lxc let us treat containers like a full VM with very few restrictions and generally run at hardware speeds with 10-100x less overhead than a full VM.

---

### Post by chili555 on 2023-11-04
> I don't have a clue what the codename for it was anymore.Trusty Tahr

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by salehbozeed on 2023-11-04
@[[COLOR=#000000]TheFu[/COLOR]]("https://ubuntuforums.org/member.php?u=1037685")[COLOR=#000000]  Yep, that's what I did last night after every suggestion didn't work.

Thanks to @[/COLOR][chili555]("https://ubuntuforums.org/member.php?u=35909") & @MAFoElffen for taking the time to help with my problem.

---

### Post by aljames2 on 2023-11-05
> **chili555 said:**
> Trusty Tahr

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Thanks for the link chili555

---

