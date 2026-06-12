---
title: "Installing Intel PRO/1000 PT NIC drivers"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by sanzaborn33 on 2006-08-02
[SIZE="2"]I am currently running a server with Ubuntu 6.06 and my current kernel version is: 2.6.15-26-amd64-generic

My ifconfig eth0 info is:

eth0      Link encap:Ethernet  HWaddr 00:15:17:0B:FF:B7
          inet addr:192.168.0.180  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:17ff:fe0b:ffb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1951314 (1.8 MiB)  TX bytes:458505 (447.7 KiB)
          Base address:0xac00 Memory:fe9e0000-fea00000

Internet is working ok, but when I run (lspci | grep Eth):

timserver@timserver-desktop:~$ lspci | grep Eth
0000:02:00.0 Ethernet controller: Intel Corporation: Unknown device 107d (rev 06)

I don't think Ubuntu is recognizing my NIC properly. I have found the newest base drivers from Intel's website here: 

[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=2249&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=2249&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

Below is what Intel has for installing the newer driver:
[/SIZE]
[SIZE="1"]Building and Installation
=========================

To build a binary RPM* package of this driver, run 'rpmbuild -tb
<filename.tar.gz>'.  Replace <filename.tar.gz> with the specific filename
of the driver.

NOTE: For the build to work properly, the currently running kernel MUST
      match the version and configuration of the installed kernel sources.
      If you have just recompiled the kernel reboot the system now.

      RPM functionality has only been tested in Red Hat distributions.

1. Move the base driver tar file to the directory of your choice.  For
   example, use /home/username/e1000 or /usr/local/src/e1000.

2. Untar/unzip archive:

     tar zxf e1000-x.x.x.tar.gz

3. Change to the driver src directory:

     cd e1000-x.x.x/src/

4. Compile the driver module:

     make install

   The binary will be installed as:

     /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000/e1000.[k]o

   The install locations listed above are the default locations.  They
   might not be correct for certain Linux distributions.  For more
   information, see the ldistrib.txt file included in the driver tar.

5. Load the module using either the insmod or modprobe command:

     modprobe e1000

     insmod e1000

   Note that for 2.6 kernels the insmod command can be used if the full
   path to the driver module is specified.  For example:

     insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000/e1000.ko[/SIZE]

===============================

[SIZE="2"]Can someone please explain how I get this to work in Ubuntu???

I am at my wits end trying to figure out a simple driver update.[/SIZE]  ](*,)

---

### Post by sanzaborn33 on 2006-08-03
Just a bump in hopes someone can pass over some advice. Thanks!

---

### Post by mrweirdo on 2006-08-03
weird I use an intel PRO/1000 MT card and it seems to work just fine. You shouldnt need drivers for intel cards as they are suposed to be supported out of the box unless your runing an acient version of linux I have been told.

---

### Post by mrweirdo on 2006-08-03
oh didnt catch it at first for starters your should be issuing:
lspci | grep eth0

just noticed you left the 0 off. dunno if that was just in the post or in the command itself but its needed ;)

---

### Post by sanzaborn33 on 2006-08-03
> **mrweirdo said:**
> weird I use an intel PRO/1000 MT card and it seems to work just fine. You shouldnt need drivers for intel cards as they are suposed to be supported out of the box unless your runing an acient version of linux I have been told.

Thanks for the reply. When you run the "lspci | grep eth0" command on your machine, is your Intel card coming back as an unknown device?

---

