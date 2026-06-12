---
title: "Integrated Intel® Pro 10/100 Ethernet Network Card Driver Help"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by mgretton on 2006-10-12
Hello all,

I installed Ubuntu for the first time yesterday on my dell dimension e520 machine. Everything worked fine apart from the fact that Integrated Intel® Pro 10/100 Ethernet Network Card was not recognised (As far as I can tell).

When I run ifconfig from the terminal no ethernet device is displayed (no eth0, eth1 etc) only lo (Loopback). Running lspci shows that there is an ethernet controller recognized although it is listed as unknown.

My initial thought was that I need to install drivers for the intel Network Card but when I went to the intel site it was not clear which drivers I needed to install.

My questions are:

1) Is there anything else I should be doing to make Ubuntu recognise the network card before searching for and installing drivers?

2) If installing drivers is the solution does anyone know precisely which drivers I should install for the Integrated Intel® Pro 10/100 Ethernet Network Card in my machine? There seem to be many appropriate drivers on the intel site and I am unsure which one I will need.

Thanks in advance for any help, it will be greatly appreciated.

Matt.

---

### Post by Buffalo Soldier on 2006-10-12
what is the exact model of the network card? try the **lspci** command in the terminal and paste here the output.

---

### Post by mgretton on 2006-10-12
Hi,

Thanks for the reply. Please see * for a full lspci print out.

Additional information:

I opened up my dell pc and there was a serial number next to the ethernet port (D38658-301). This seems to fit the structure for an intel network card code but I could not find a match on the intel website.

Also if it is of any help the serial number of the motherboard is E210882.


*
0000:00:00.0 Host bridge: Intel Corporation: Unknown device 29a0 (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation: Unknown device 29a1 (rev 02)
[COLOR="Red"]0000:00:19.0 Ethernet controller: Intel Corporation: Unknown device 104c (rev 02)[/COLOR]
0000:00:1a.0 USB Controller: Intel Corporation: Unknown device 2834 (rev 02)
0000:00:1a.1 USB Controller: Intel Corporation: Unknown device 2835 (rev 02)
0000:00:1a.7 USB Controller: Intel Corporation: Unknown device 283a (rev 02)
0000:00:1b.0 0403: Intel Corporation: Unknown device 284b (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation: Unknown device 283f (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation: Unknown device 2830 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation: Unknown device 2831 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation: Unknown device 2832 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation: Unknown device 2836 (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
0000:00:1f.0 ISA bridge: Intel Corporation: Unknown device 2812 (rev 02)
0000:00:1f.2 RAID bus controller: Intel Corporation: Unknown device 2822 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation: Unknown device 283e (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d1 (rev a1)

Thanks again for the reply.

Matt.

---

### Post by mgretton on 2006-10-16
Additional information:

The model of the network card is 82562V, I still cannot find linux drivers for it however...

---

### Post by thocu on 2006-10-22
I've run into the same problem. Found a driver however on the intel site : [http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=998&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=998&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)
As I am completely new to linux, so far I haven't gotten to trying it out. If it worked or if you found another solution, could you post resutlts?
good luck.

---

### Post by louistan3 on 2006-10-22
how come uve got a lot of unknown devices?

maybe u dont have the kernel restricted modules installed? if i remember right.. i think that is where most drivers for out of the box hardware are..

hope this helps :D

---

### Post by handy on 2006-10-22
I used to run an Intel Pro 10/100 PCI NIC & Ubuntu's Breezy & Dapper, both found driver's for it?

The Intel Chip's ID below, if anyone is interested?

[B]GD82559      

L9421G43[/B]

---

### Post by NRTech on 2006-11-12
I have been toying with changing over my MS servers over to Linux. I recently installed on my test server Ubuntu Dapper LAMP server which automatically recognized and installed an Intel Pro 100 NIC. When I re-installed Ubuntu Edgy LAMP server (not upgrade), it didn't even see the Intel NIC. I got the screen that says you are installing without a network device, do you want to continue. I decided to continue and try to fix it later. Will continue to try your fixes and post back.

---

### Post by kweiner on 2006-12-03
> **mgretton said:**
> Additional information:

The model of the network card is 82562V, I still cannot find linux drivers for it however...

I have the same network card and had the same problem when I tried installing Ubuntu 6.06.  However, when I installed 6.10, my network card worked without having to configure anything special.  Ubuntu 6.10 did not recognize my cdrom so I had to install it using a network installation.

The driver (or is it a kernel module?) that seems to be working is called e1000:
[http://support.intel.com/support/network/sb/cs-006120.htm](http://support.intel.com/support/network/sb/cs-006120.htm)

I hope that helps.

---

### Post by yulewang on 2007-01-21
well, the problem is that if i down load the source, I need to compile it.
but how can I apt-get a gcc before I compile the ethernet driver?

btw, who can compile the driver for us and post your module here? 
thanks in advance.
I use 2.6.15 kernel[ubuntu dapper drake]

---

### Post by netztier on 2007-01-21
> **yulewang said:**
> well, the problem is that if i down load the source, I need to compile it.

Well if the module does not auto-load, it doesn't mean that it's not there.

Did you try **modprobe e100**, **modprobe e1000** or **modprobe eepro100** and check kernel output with **dmesg** afterwards? 

If either of these modules load successfully, you can list it in **/etc/modules** to have it loaded at system startup. My Dapper Drake installation lists all these modules in **/lib/modules/<kernel-version>/kernel/drivers/net/***.

best regards

Marc

---

### Post by yulewang on 2007-01-21
I try to follow your instruction, but no luck:(
maybe the e100 driver in ubuntu is too old?

intel 82562v 10/100

---

### Post by netztier on 2007-01-22
> **yulewang said:**
> I try to follow your instruction, but no luck:(
maybe the e100 driver in ubuntu is too old?


Rather not too old, but too new. The 82562 module is 10/100 only, but should be supported by the e100 module, see [Intel® 82562 Fast Ethernet Controllers Downloads]("http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=998&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21"). The source they offer builds the **e100** module which should support your NIC.

What does **dmesg** actually say after a **"sudo modprobe e100"** and/or **"sudo modprobe e1000"**? Remember, only loading the module won't bring networking to life, you'll need to start networking services, too - best is to list the module in /etc/modules and reboot the box.


best regards

Marc

---

### Post by handy on 2007-01-22
@ netztier,  reading your signature I'm sure you are a fan of Blade Runner... :D

---

### Post by canga on 2007-01-28
I have been having my own problems with an Intel EtherPro 100 card and thought that my results may help you.

I installed Dapper onto an old, but functioning, clean PC that includes an Intel EtherPro 100 PCI card.  At the end of the install I didn't have a functioning network card.  The [FONT="Lucida Console"]lspci -bv[/FONT] command showed that the card was present but trying to start the network through the network administration window failed without any error.  The command [FONT="Lucida Console"]cat /proc/interrupts[/FONT] didn't show an interrupt for the ethernet card.  Entering the command [FONT="Lucida Console"]ifconfig eth0[/FONT] at a command prompt gave information for the card but no IP address and statistics showing that no data was flowing.  The syslog also showed that the network wasn't working.  Entering the [FONT="Lucida Console"]ifconfig eth0 up[/FONT] command returned an error containing [FONT="Lucida Console"]SIOCSIFFLAGS: Resource temporarily unavailable[/FONT]  A search on Google uncovered the information that there is an issue with the e100 kernel module (which was the one loaded at boot time).  The remedy was to edit the file /etc/modprobe.d/blacklist so as to allow use of the eepro100 module and bar use of the e100 module, now the appropriate section of the file looks like so 
```
# replaced by e100
#blacklist eepro100
blacklist e100
```

I now have a functioning network interface.  Along the way I found that the man page for ifconfig refers to a web site that no longer exists, that configuration of modprobe has changed with the 2.6 kernel, but also that a problem raised with Intel's e100 driver several years ago still causes problems today.

I realise that your card/chip is different, but perhaps an alternative driver will work for you too.

---

