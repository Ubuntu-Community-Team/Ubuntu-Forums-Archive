---
title: "usbnet broken by Gutsy?"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by gwi on 2007-11-04
I have a Motorola A780, that I could telnet to from Ubuntu, using usbnet and cdc-acm modules.

When following the instructions on the [OpenEZX wiki]("http://wiki.openezx.org/Get_a_shell#Linux") I get the first two of the three expected lines of output, but the third line
```
usb0: register usbnet at usb-0000:00:10.2-2, pseudo-MDLM (BLAN) device, 8e:36:06:d5:16:9d
```
does not appear.

If I then try to do
```
ifconfig usb0 192.168.1.1 netmask 255.255.255.0 mtu 900
```
I get error messages saying usb0 does not exist.

If I switch the phone from USB modem to USB LAN mode, dmesg shows the following:
```
[ 2134.368000] usb 2-5: USB disconnect, address 6
[ 2135.044000] usb 2-5: new full speed USB device using ohci_hcd and address 7
[ 2135.264000] usb 2-5: configuration #1 chosen from 1 choice
```
Nothing on usbnet.

Other articles/postings indicate I should check the contents of /proc/bus/usb/devices, but that file isn't even there.

So: what's wrong here? It has worked before (before the upgrade to Gutsy that is...), so did the upgrade (or later the fresh Gutsy install) break something?

---

### Post by nosneros on 2007-11-05
Hi,

I'm having problems with usbnet too. I am attempting to connect my Dell Axim X30 to my desktop. I am able to boot Linux on it using HaRET; however, it does not appear to be detected by Ubuntu. 

I think it is supposed to be detected by hotplug and have the cdc_subset/usbnet drivers automatically loaded. dmesg doesn't show any signs of this happening (on the other hand, it does get detected by the ipaq driver when running WinCE). Well, I think I should get a usb0 interface as well, but of course it's not there since the driver didn't get loaded.

BTW, gwi, I think you can look in /sys/class/net for your network interfaces and /sys/bus/usb for usb related stuff. I'm not too sure how to parse all the info in there yet.

So, back to the original question, what is the best way to go about troubleshooting the lack of driver detection/usb0 interface? Anyone have info/know where to look about that?

Any help is greatly appreciated!!! :)

Thanks,
nos

---

### Post by gwi on 2007-11-23
Tested it again with the Feisty live CD. usbnet is working there. SO ik looks like Gutsy has broken usbnet somehow.

nosneros, could you add your usbnet problem to the but I filed [**here**]("https://bugs.launchpad.net/ubuntu/+bug/162003")? Maybe we will get some sort of response from Ubuntu side.

---

### Post by panduro on 2007-11-27
Hello
i think you need the zaurus-module :) for that. In  gutsys default-kernel its not compiled.
you need to do that manualy.
sorry for my bad english.

bye

---

### Post by nosneros on 2007-12-02
Hi guys,

After doing some more investigation, I think the problem I'm having is with the usbnet stack on my PDA, not in Ubuntu. I'm going to try compiling a more recent kernel for the PDA and see if that fixes the problem, but it might take me a while to get it running.

Regards,
nos

---

### Post by arnaldo on 2008-01-24
I have the same problem, and my cell is a Motorola A1200.  I compiled in zaurus module, and after connecting the phone and doing some magic to get it into usbnet mode, interface usb0 does appear.

I have it duly configured as 192.168.1.1, while the phone configures itself as 192.168.1.2.
Everything seem OK, but I cannot ping in either direction.

On the computer side, the same failure shows up with gutsy kernel 2.6.22-14 and the older 2.6.20-16 (which was packaged with zaurus).

Perhaps, as was suggested, the problem lies in the phone; any suggestion on how to assert that?

---

### Post by gwi on 2008-01-28
I did not try the zaurus module.
I tried the Feisty live-cd, and with that I can telnet to my A780.
With Gutsy I can not. It's as simple as that.

I reported a bug ([Bug #162003]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162003")). It now has the status "Confirmed", but I have no idea if anyone is working on it. Feedback and Ubuntu bugs seem to be incompatible.... :(

---

### Post by arnaldo on 2008-01-30
Solved it!

The problem is two-fold:

1) Inexplicably, the zaurus module is missing from the kitchen sink kernel 2.6.22-14-386 package.  

2) firestarter blocks access to the new interface, by default.

(1) is a blunder by the maintainers, which is trivial to solve at their level.  My solution turned out to be ugly - I did not want to compile a full kernel, but had to.  After compiling and installing the modules of a new kernel, minimally configured, I tried a hack that turned out to work: copy the zaurus module to the appropriate position in the current kernel libs, and copy all lines mentioning zaurus from de dep files of the new to the compiled one.  I will not give more details - if this is not sufficient, you should not follow this route.  Just install a new kernel, it is easier than it sounds.

(2) should be easy: just fire up firestarter, and inform of the new interface.  Maybe I am a little dumb, but I could not make it work.  After a while, I got fed up, and created the executable /etc/network/if-up.d/80fixusb:

#!/bin/sh

ip -o address show usb0|grep -q 192.168 || exit

iptables -A INPUT  -s 192.168.1.2 -j ACCEPT 
iptables -A OUTPUT -d 192.168.1.2 -j ACCEPT 


In /etc/network/interfaces I added the following stanza, as per many recommendations around:

mapping hotplug
script grep
map usb0
auto usb0
iface usb0 inet static
    address 192.168.1.1
    pointopoint 192.168.1.2
    netmask 255.255.255.0
    mtu 900

Now, after connecting the phone and doing the appropriate magic on its side, the usb0 interface does appear.  Still, it looks like auto doesn't work there.  I have to execute

ifdown usb0;ifup usb0

Now, everything works.  

Maybe somebody can simplify all that, and I hope that new kernels will have zaurus already compiled in.

---

### Post by gwi on 2008-01-30
Re 1: I will wait for the official fix.

Re 2: That has nothing to do with the broken usbnet problem.

---

### Post by LoCusF on 2008-01-30
I know this [guide]("http://www.ruault.com/Zaurus/ethernet-over-usb-howto.html") is a little bit old (ok ok really old :) ), but I have decided to give it a try. 

Since the kernel image that is shipped with Gutsy should be the same as the kernel sources that are awailable in the repositories, the total kernel recompilation shouldn't be an issue. So I'll give this approach a try (ie. make modules modules_install) try and report here.

---

### Post by TheodoreWard on 2008-04-22
> **LoCusF said:**
> I know this [guide]("http://www.ruault.com/Zaurus/ethernet-over-usb-howto.html") is a little bit old (ok ok really old :) ), but I have decided to give it a try. 

Since the kernel image that is shipped with Gutsy should be the same as the kernel sources that are awailable in the repositories, the total kernel recompilation shouldn't be an issue. So I'll give this approach a try (ie. make modules modules_install) try and report here.

Well??

---

### Post by Statik on 2008-05-17
I have a new A780 and I've tried following the steps both [Here]("http://wiki.openezx.org/Get_a_shell#Linux") and [here]("http://www.troodon.org/a780/a780-linux-howto.htm"). Everything seems to be working until I get to the stage where USB0 should appear as a usbnet device. You can see all the specs and such here: [http://www.motorolafans.com/forums/showthread.php?t=1746&page=5]("http://www.motorolafans.com/forums/showthread.php?t=1746&page=5").

Any assistance would be appreciated.

Statik

---

### Post by Statik on 2008-05-17
Found Applications->Other->Usb Devices which reports:
```

Motorola USBLAN

Manufacturer: Motorola

```

Its listed under:
OHCI Host Controller (1)
..BCM92045B3 ROM
....Motorola USBLAN

How can I connect to this?

Statik

---

