---
title: "D-Link DWL-G122 Installing Help"
date: 2005-09-06
forum: Networking &amp; Wireless
---

### Post by eddygigot on 2005-09-06
Hi,
Can anyone tell me how to install the D-Link DWL-G122 USB Bluetooth dongle.Just trying Ubuntu for the first time and can't suss it out
Thanks

---

### Post by macgyver2 on 2005-09-06
Take a look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=57228](http://www.ubuntuforums.org/showthread.php?t=57228)

---

### Post by jalmas on 2005-09-28
These are the steps I do to install my D-Link DWL-G122 B1 usb wireless adapter.
This wiki was very useful: 
[INDENT]
[https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo/)[/INDENT]
You can pick the driver tarball from this url: 
              [INDENT][http://prdownloads.sourceforge.net/rt2400/rt2570-1.1.0-b1.tar.gz](http://prdownloads.sourceforge.net/rt2400/rt2570-1.1.0-b1.tar.gz)[/INDENT]
or from the download page

[INDENT][http://prdownloads.sourceforge.net/rt2400/](http://prdownloads.sourceforge.net/rt2400/)[/INDENT]

The chipset is the 2570-xxxx-b1 (as the hw version of the adapter).

Please, look at "PROBLEMS" at the end.

Also, I try the driver provided by Ralink, but I prefer this first driver.

_Build the driver._

[INDENT]$ tar -xzf rt2570-1.1.0-b1.tar.gz[/INDENT]
[INDENT]$ cd rt2570-1.1.0-b1[/INDENT]
[INDENT]$ cd Module[/INDENT]
[INDENT]$ make[/INDENT]

_You can test before to install (as superuser)._

[INDENT]$ insmod rt2570[/INDENT]

You can look at /var/log/syslog if the kernel loads the driver and
the adapter is recognized.

The adapter is named "rausb0". You can inspect it.
[INDENT]$ iwconfig rausb0[/INDENT]

_Install the driver (as superuser)._

Remember to extract the adapter before install.
Assume you are in the Module directory.
	
[INDENT]$ cp rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/[/INDENT]
[INDENT]$ depmod[/INDENT]

_Configuration._

This is the /etc/network/interfaces part used to configure for home network.
I need this configuration before to bring-up the adapter, elsewhere, I have to
manually configure the adapter :-(                
[INDENT]#
# wifi usb
#
auto rausb0[/INDENT]
[INDENT][INDENT]iface rausb0 inet static
address 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1
name 'D-Link DWL-G122 USB Wireless' 
dns-nameservers 192.168.0.1
mode Managed
wireless-essid ADSL 
wireless-key restricted s:KADSL [2][/INDENT][/INDENT]

_Using it._

To work with the wireless network I had to disable the ethernet adapter.

[INDENT]$ ifdown eth0[/INDENT]

and enable the wireless adapter

[INDENT]$ ifup rausb0[/INDENT]


_Ralink Driver._

You can find in the URL
[INDENT][http://www.ralinktech.com/drivers/Linux/RT25USB-SRC-V2.0.5.0.tar.gz](http://www.ralinktech.com/drivers/Linux/RT25USB-SRC-V2.0.5.0.tar.gz)[/INDENT]
or browsing the home page, the "support" and choose "USB(Source Code)" at the
end of the Linux list.

_Build the driver._

[INDENT]$ tar -xzf RT25USB-SRC-V2.0.5.0.tar.gz
$ cd RT25USB-SRC-V2.0.5.0[/INDENT]

The file README has instructions to build the driver.

[INDENT]$ cp Makefile.6 Makefile   # I am using 2.6.10 kernel.

$ make
$ insmod rt2570.ko        # Insert driver module
$ ifconfig rausb0 up      # Bring up device[/INDENT]

To install the module into the kernel, according to the wiki (as superuser),
[INDENT]$ ifdown rausb0
$ cp rt2570.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
$ depmod[/INDENT]

_RaConfig2500._


The tarball comes with a binary executable of the RaConfig2500 utility. It is
under directory 
[INDENT]LINUX_RACONFIG_V2.0.0.6/bin//Fedora-Core3[/INDENT]

I can execute it directly.


_PROBLEMS._


1. Trying to configure the wireless adapter with System-> Administration -> Networking, the system blocks when I press "Activate". I have to power-off and restart. :confused: 

2. Randomly, the system blocks when the wireless adapter is enabled a second time, i.e. when I am working with the wireless network (first ifup rausb0), and I switch to ethernet (first ifdown rausb0), and I come back to wireless (ifup rausb0). This later command blocks the system, but randomly.:rolleyes: 

3. Sometimes, the interface may appears as not enabled after ifup rausb0.
With a ping you may bring it to live.;-)

_FINAL._
I put this reply using the usb adapter.:razz:

---

