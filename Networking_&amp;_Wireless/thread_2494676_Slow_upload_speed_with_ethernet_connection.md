---
title: "Slow upload speed with ethernet connection"
date: 2024-01-23
forum: Networking &amp; Wireless
---

### Post by dorasmith24 on 2024-01-23
My computer is getting a slow upload speed with an ethernet connection.   

I am paying for 1 gig of internet speed, with upload speed of 35 mbps/ sec.  At my computer I am getting 17 to 24 mbps/ sec, more often 17.   

The problem is I am trying to get a work from home customer service job, and speed downgrades with distance.   To any server in Colorado, where the employer is, I am only getting 7 mbps.  Employer needs a screenshot showing I have atleast 10 mbps with my application.  

I had a technician from my ISP out here.  He found 950 mbps download, 37 mbps upload, at the modem - after he ran upgrades on the modem.  In my room with the ethernet cable, which is 50 feet long to the modem, with his testing equipment, he also got 950 mbps download and 37 mbps upload. He showed me both test results.   But speed test on my computer, speedtest.net (ookla) only getting 24 mbps upload, same as I was getting last night, and as poor as 600 mbps download, though sometimes it gets 850 download.

The ethernet cable is e 5e, and the technician's test at my computer's end of the cable proved the cable is fast enough.  It doesn't look like I need a cat 6 cable.  

Wireless signal is from an extender that is plugged into the ethernet port on the computer, and speeds varie from 200 to 650 mbps download, upload forgetaboutit.  I was actually getting consistent 300 mbps download when that was what I was paying for.  

It looks like something specifically about my computer is causing slow upload speed. 

Is fixing it as simple as an ethernet card?

Also, if what I need is an ethernet card, what kind should I get?  My research shows that some don't reach full speed, and some either don't support linux or need drivers, in which case it isn't clear if they support Ubuntu 20.04.

On Amazon I am finding inexpensive gigabit to 1.25 gigabit cards that say they use Intel 82571, 82573, and 82576 chipset.   My motherboard's ethernet adapter, which is gigabit, uses an Intel 82579 chipset.  Is a lower number likely to be any faster, or would they work regardless of having a lower number because it is most likely my ethernet adapter is wearing out?  

Here are the relevant specs on my computer and its ethernet adapter.

Ubuntu 20.04.6 LTS
CUP Intel Core i5-2400 CPU  3.10GHz  4 cores 4 threads
Motherboard Intel Corporation DH67BL

 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
    DeviceName: Intel(R) 82579LM Gigabit Network Device
    Subsystem: Intel Corporation 82579V Gigabit Network Connection
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at f4a00000 (32-bit, non-prefetchable) [size=128K]
    Memory at f4a28000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e


dora@dora-desktop-ubuntu:~$ lspci -nnk | grep net -A2
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
    DeviceName: Intel(R) 82579LM Gigabit Network Device
    Subsystem: Intel Corporation 82579V Gigabit Network Connection [8086:2002]

The driver I am running for that adapter is e1000e, version 3.2.6-k.   This is evidently the correct driver.   

The latest release is 3.8.7.    

I have been running Software Updater.

How do I update this driver?

Actually the page where I found what driver I should be using has update instructions, but, it is convoluted and difficult,and this is never how I installed it in the first place!

[https://www.intel.com/content/www/us/en/support/articles/000005480/ethernet-products.html](https://www.intel.com/content/www/us/en/support/articles/000005480/ethernet-products.html)

[FONT=intel-clear]The drivers are only supported as a loadable module. We don't supply patches against the kernel source to allow for static linking of the drivers. For questions related to hardware requirements, see the documentation supplied with your Intel® Gigabit Network Adapter. All hardware requirements listed apply for use with Linux.[/FONT]
[FONT=intel-clear]Features now available in supported kernels:[/FONT]

[LIST]
[*]Native VLANs
[*]Channel Bonding (teaming)
[*]SNMP
[/LIST]
[FONT=intel-clear]Find Channel Bonding documentation in the Linux kernel source: [/documentation/networking/bonding.txt]("https://www.kernel.org/doc/Documentation/networking/bonding.txt").[/FONT]
[FONT=intel-clear]This release doesn't support the driver information previously displayed in the /proc file system. You can also use ethtool (version 1.6 or later), lspci, and ifconfig to get the same information.[/FONT]
[TABLE="class: icstable icsnote, width: 100%"]
[TR]
[TD]Note[/TD]
[TD]The Intel® 82562v 10/100 Network Connection only provides 10/100 support.[/TD]
[/TR]
[/TABLE]
[FONT=intel-clear]Building and installation[/FONT]
[FONT=intel-clear]Steps below require elevated privileges.[/FONT]
[TABLE="class: icstable, width: 100%"]
[TR]
[TD]Prerequisites[/TD]
[TD][FONT=intel-clear]Red Hat based platforms: CentOS, RHEL, or Fedora[/FONT]

[LIST]
[*]yum install gcc make
[*]yum install kernel kernel-devel
[/LIST]
Ubuntu and Debian based platforms
[LIST]
[*]apt-get install linux-headers-$(uname -r)
[*]apt-get install gcc make
[/LIST]
You may need to perform a general update and restart before the next steps.[/TD]
[/TR]
[/TABLE]

[LIST=1]
[*][FONT=intel-clear]Download current e1000e package from [Download Center]("https://downloadcenter.intel.com/download/15817"). Move the base driver tar file to the directory of your choice.
For example, use */home/<USERNAME>/e1000e or /usr/local/src/e1000e.*[/FONT]
[*][FONT=intel-clear]Untar/unzip the archive, where <x.x.x> is the version number for the driver tar file:[/FONT]
*tar zxf e1000e-<x.x.x>.tar.gz*
[*][FONT=intel-clear]Change to the driver src directory, where <x.x.x> is the version number for the driver tar:[/FONT]
*cd e1000e-<x.x.x>/src/*
[*][FONT=intel-clear]Compile the driver module:[/FONT]
*make install*[FONT=intel-clear]The binary installs as:[/FONT]
*/lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000e/e1000e.ko*[FONT=intel-clear]The install location listed above is the default. Location may differ for various Linux* distributions.[/FONT]
[*][FONT=intel-clear]Load the module using either the insmod or modprobe command:[/FONT]
*modprobe e1000e insmod e1000e*[TABLE="class: icstable icsnote, width: 100%"]
[TR]
[TD]Note[/TD]
[TD]You can use the insmod command for 2.6 kernels if you specify the full path to the driver module. For example:[FONT=intel-clear]insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000e/e1000e.ko[/FONT]
[FONT=intel-clear]With 2.6 based kernels, make sure that older e1000e drivers are removed from the kernel before you load the new module:[/FONT]
rmmod e1000e; modprobe e1000e[/TD]
[/TR]
[/TABLE]
[*][FONT=intel-clear]Assign an IP address to the interface by entering the following, where <x> is the interface number:[/FONT]
*ifconfig eth<x> <IP_address>*
[*][FONT=intel-clear]Verify that the interface works. Enter the following, where <IP_address> is the IP address for another machine on the same subnet as the interface you're testing:[/FONT]
*ping <IP_address>*
[/LIST]
[TABLE="class: icstable icsnote, width: 100%"]
[TR]
[TD]Note[/TD]
[TD][FONT=intel-clear]Some systems have trouble supporting MSI and/or MSI-X interrupts. If your system must disable this style of interrupt, build and install the driver with the command:[/FONT]
make CFLAGS_EXTRA=-DDISABLE_PCI_MSI install[FONT=intel-clear]Normally the driver generates an interrupt every two seconds. If you're no longer seeing interrupts in cat /proc/interrupts for the ethX e1000e device, then this workaround may be necessary.[/FONT][/TD]
[/TR]
[/TABLE]
Linux* e1000 base driver for Intel® PCI, PCI-X Gigabit Network Connection installation instructions[FONT=intel-clear]
[/FONT]
[TABLE="class: icstable icsnote, width: 100%"]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
[TABLE="class: icstable icsnote, width: 100%"]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
[TABLE="class: icstable, width: 100%"]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

[LIST=1]
[*][FONT=intel-clear]
[/FONT]
[*][TABLE="class: icstable icsnote, width: 100%"]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
[/LIST]


What IP address?   My ISP?  My machine on my local network?    Why do I have to give it an ISP address?

Thanks!

Yours,
Dora Smith

---

### Post by makitso on 2024-01-24
Boot live CD, test with openspeedtest.net.
What browser are you using, Firefox?  Remove plugins, try a different browser.

---

### Post by dorasmith24 on 2024-01-24
Employer requires a screenshot of a specific test in Chrome.   I would expect it to be fastest.

So far I have tried Windows 10 with all updates run, Ubuntu 22.04 on my desktop, and Ubuntu Budgie 22.04 on my laptop, with kernel 6.1 installed on both.  The driver is incorporated into the kernel so that automatically gave me a more recent version.   

It is a little faster in both Windows 10 and Ubuntu 22.04 with kernel 6.1, and a little slower in same on my laptop.   

The laptop is also a slightly older machine.   3rd generation i5 processor.   My desktop has a 2nd generation i5 processor.   

openspeedtest.com gets a speed of 523 mbps download and 8.68 mbps to Irving, TX, which sounds about right, to Irving, Texas.

   It isn't as fast in Firefox - which I very rarely use.

The ISP tech and I were both using speedtest.net, which was getting that sort of speed to servers in Colorado, but 860 download speed and 26 upload to a server in Austin, where I live.   I'm paying for 1 gig download and 35 gig upload.  He was getting 37 gig uload both at the modem at at my computer's end of the 50 foot cat5e ethernet cable.   So there's a drop to what my computer can do.   

When I used a different computer it simply got worse.

That is all the troubleshooting I know how to do.

What is causing that drop in speed?   I have only Chrome open with eight windows, and only four on my laptop, and nothing else running.

I thought if it's not the driver, maybe the ethernet adapter on my board is wearing out.   Using another computer didn't get higher speeds.  Got lower.

---

### Post by foxsquirrel on 2024-01-28
Go to your local cellphone store and see what that have. We have a wireless failover and its around 20G up and down or so and our facilty is out in the weeds.

---

