---
title: "PCMCIA - RTL8139 or DSE XH8267 driver installation problems."
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by MilosI on 2008-04-29
**Hello everyone,**

Thanks for opening this thread.

We are running **Ubuntu 8.04 LTS Server Edition**.

I have been having great trouble trying to setup this card to work on my friend's laptop which is by the way really old (originally run Windows 98, which is of course from 1998 ).
The drivers that came on the CD were for Windows and Linux, it was difficult to understand the readme for the file and even after asking for help in a channel on FreeNode there wasn't any more luck.

The message that it displays in */var/log/messages* is "CardBus not supported" when the card is inserted.

*ifconfig eth0* says device not found.
After trying to make ndiswrapper to possible emulate the windows driver or whatever ndiswrapper does, it said Error 2. Great, what the heck does that mean.

This is what the readme for the file said:

> 
RTL8139 driver(written by Donald Becker) is distributed with Linux
after kernel version 2.0.34. It is better to build it into kernel.

The procedure to activate rtl8139 on linux if not build in kernel:

step 1: compile:
The instruction for compiling the driver is include at the
end of the driver file. (run this instruction at
/usr/src/linux)

step 2: insert the driver as module:
insmod rtl8139.o
parameter can be added by adding options=..... behind the istrruction
0x16(bit 4):full duplex
bit 0-3 :default port
(run 'lsmod' to see if the module is inserted)

step 3: bind your card to an IP address

/sbin/ifconfig eth0 ${IPADDR} broadcast ${BROADCAST} netmask ${NETMASK}
(run 'netstat -i' to see if there is a interface 'ne0')

step 4: add your card to IP routing table, then add gateway also
your card:
/sbin/route add -net ${NETWORK} netmask ${NETMASK} eth0
(should be able to ping local network now)
gateway:
/sbin/route add default gw ${GATEWAY} netmask 0.0.0.0 metric 1

step 5: start inet deamon.
/usr/sbin/inetd
(you are on the network now)

*make sure that your kernel is built with network,CardBus, fast_ethernet
and module support. Otherwise, you have to rebuild your kernel.
(1:go to /usr/src/linux directory
2:run 'make menuconfig' or 'make config'
3:mark the options list above.
4:exit and rebuild your kernel.
make dep;make clean;make zImage
the file 'zImage' will be at
/usr/src/linux/arch/i386/boot/zImage
5:modify /etc/lilo.conf.(this file specify where kernel image is)
6:run 'lilo' )

You cna run 'netconfig' which will do step 3,4,5 for you. This will create
'/etc/rc.d/inet1' and 'inet2' files. These two files will run at boot time.
Then just add a line at the beginning of 'inet1'.
'insmod /your driver'path/rtl8139.o'
then your driver will work every time you boot.



The PCMCIA card was bought in a shop called Dick Smith Electronics, and here is the website with information about the card.

[http://www.dse.co.nz/cgi-bin/dse.storefront/4817ce09096e4374273fc0a87f3b0687/Product/View/XH8267](http://www.dse.co.nz/cgi-bin/dse.storefront/4817ce09096e4374273fc0a87f3b0687/Product/View/XH8267)

--------------------------------------------------------------

Any help would be appreciated, and remember we don't have ethernet on this machine, (that's what we're trying to get) and so if there's anything required to download we have to get the package and then burn it to a disc, mount and then be able to install whatever is needed.

Thanks once again.

---

### Post by chili555 on 2008-04-29
> kernel version 2.0.34Why won't these disc brakes with anti-lock braking sensors drop right on to my 1938 Dodge?

Your Ubuntu 8.04 uses the 2.6.24 kernel. There are vast differences between 2.0.x and 2.6.x kernels. So vast that I doubt you could get this dinosaur to even compile. So please rename the README to DONTMAKEMELAUGH.

But there is good news. There is a module built-in to your shiny new 2.6.24 kernel called 8139too. If we are lucky, you can open a terminal and do:```
sudo modprobe 8139too
ifconfig
```And you may see your eth0, or some other ethernet interface. If so, hook up the wire and do:```
sudo dhclient eth0
```Did you connect?

Please try it and let us know.

---

### Post by Nallen01 on 2008-04-29
Hi There,

I am the friend in this conversation who can not get it to work.

```
sudo modprobe 8139too
```echos nothing back.
```
ifconfig
``` returns data for "Local Loopback".

```
sudo dhclient eth0
``` returns 4 errors saying "Device Not Found".


Any other suggestions?

---

### Post by chili555 on 2008-04-29
Let's try:```
sudo ifconfig eth0 up
```If you have restarted the computer since you modprobed, let's do that again before you 'up' eth0.

When a command returns nothing, it generally means the command was executed without error. That's a good thing.

If those work OK, then try:```
sudo dhclient eth0
```Let us know.

---

### Post by Nallen01 on 2008-04-30
Hi again,

```
sudo ifconfig eth0 up
``` returns this error:
> eth0: ERROR while getting interface flags: No such device

any more suggestions?

---

### Post by chili555 on 2008-04-30
> laptop which is by the way really old (originally run Windows 98, which is of course from 1998...snip....
The message that it displays in /var/log/messages is "CardBus not supported" when the card is inserted.I found this, which may be your situation: [http://linux.derkeiler.com/Mailing-Lists/Debian/2006-10/msg01041.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2006-10/msg01041.html)

It's beginning to sound like we are trying to get a 32-bit card going in a 16-bit slot that was never designed for 32-bit, because it didn't exist in 1998.

Is there some other mechanism we can use to get this oldie on line?

---

### Post by MilosI on 2008-04-30
> 
It's beginning to sound like we are trying to get a 32-bit card going in a 16-bit slot that was never designed for 32-bit, because it didn't exist in 1998.


The card works fine when Windows 98 is installed on the machine. The drivers install and it works like a charm; we wouldn't be trying this if it wasn't possible! The card was working perfectly before we tried Linux, or, more specifically Ubuntu.
Is there anything we can do with NDISwrapper? I heard it allows you to use some Windows drivers instead of Linux ones...? Correct me if I'm wrong.

I told my friend to try Ubuntu after getting slightly bored with Windows 98 so he formatted the drive and installed Ubuntu 8.04 LTS Server and the next thing you know the card doesn't work natively - that's how all this started.

> 
Is there some other mechanism we can use to get this oldie on line?


Sadly there isn't another way to get this oldie online, so we'll keep trying until we just can't try anymore :P

---

### Post by chili555 on 2008-04-30
Well, ndiswrapper is the next logical step. Do you have a driver disc with an XP .inf file? Can you find one on the web? Here is a tutorial on ndiswrapper that will get you started. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Let us hear from you if you get stuck.

---

### Post by MilosI on 2008-04-30
Thanks for your continuous support chili555, it's really appreciated.

I had thought of using NDISwrapper but thought I'd ask you guys for help before I attemt it.

We're going to try NDISwrapper now with the *netrtOEM.inf* file that is in the "WinXP" folder of the driver CD and we'll keep you posted.

---

### Post by Nallen01 on 2008-04-30
> 3.2.1. PCI Wireless Adapter
Open a Terminal (Applications | Accessories | Terminal), type lspci and press the return/enter key.
Look through the output of the lspci command for an entry for your wireless card.

When I do lspci it does not return any values for the Ethernet card. Should we just skip this step since all it does is locate the driver and we already have the driver?

---

### Post by chili555 on 2008-05-01
> Should we just skip this stepYessir!

---

### Post by MilosI on 2008-05-01
Hello again,

My friend has tried what you suggested earlier but to no avail. It still says *"CardBus cards are not supported"* and when you try and get it to show eth0 information, it simply says *"Device not found"*.

Does anyone have any other ideas or possibly some information on how to actually know that this driver (yes even if it did come on the CD) actually works for this PCMCIA card?

Thanks guys.

---

