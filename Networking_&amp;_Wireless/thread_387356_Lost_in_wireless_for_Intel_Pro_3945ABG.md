---
title: "Lost in wireless for Intel Pro 3945ABG"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by jcbell3 on 2007-03-18
Hello,


Thanks and congrats to all the Linux developers. This is my 3rd spin with Linux and it keeps improving each time. I'm trying to get to the point where Linux can function as my daily OS.

I've installed a dual-boot system on a Dell Latitude D 620 with a Nvidia Quadro NVS 110M video card and a Intel Pro 3945ABG wireless adapter.

I wanted to get two things working in Linux:

1) Video driver to allow me to use my monitor, docking station and perhaps compiz desktop
2) My wireless card to work (3945ABG Intel Pro)

I haven't had much success with either topic.


I thought things would work out fine when I found the Linux Intel drivers on their home page.  However, I don't get very far in the instructions and I suspect that I'm going to get into more trouble as I progress through these 'quick' install steps.

[http://ipw3945.sourceforge.net/INSTALL](http://ipw3945.sourceforge.net/INSTALL)


The install of ieee80211-1.2.16 went ok.

When I try to build the ipw3945.ko module the system coughs and mentions that I need to re-build the kernel because it doesn't like the previous step of installing a newer/different ieee80211 subsystem.

My question is - Is this the best/only way to get the wireless driver working?  I don't have much of a clue what is going on so, I suspect these instructions are over my head.  I'm curious if there is a 'better' way to go....


Thanks,

John

---

### Post by Kobalt on 2007-03-18
I think you can try this method as well to get your card flyin' : 
```
$ sudo aptitude install linux-headers-$(uname -r) wireless-tools linux-restricted-modules-$(uname -r)
```

Downloading latest version of ieee802111:

```
$ cd /usr/src
$ sudo wget ttp://prdownloads.sourceforge.net/ieee80211/ieee80211-1.2.15.tgz?download
```

Installing ieee80211:

```
$ sudo tar xvfz ieee80211-1.2.15.tgz
$ cd ieee80211-1.2.15
$ sudo sh remove-old
$ sudo make IEEE80211_INC=/usr/include
$ sudo make install
```

Installing driver ip3945 in /usr/src:

```
$ sudo wget http://umn.dl.sourceforge.net/sourceforge/ipw3945/ipw3945-1.1.0.tgz
$ cd /usr/src
$ sudo tar xvfz ipw3945-1.1.0.tgz
$ cd ipw3945-1.1.0
$ sudo ./unload    #Error
$ sudo make IEEE80211_IGNORE_DUPLICATE=y
```

Installing firmware and daemon:

```
$ sudo wget http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.13.tgz
$ sudo tar xvfz ipw3945-ucode-1.13.tgz
$ cd ipw3945-ucode-1.13
$ sudo cp ipw3945.ucode /lib/firmware/
```

```
$ sudo wget http://bughost.org/ipw3945/daemon/ipw3945d-1.7.22.tgz
$ sudo tar xvfz ipw3945d-1.7.22.tgz
$ cd ipw3945d-1.7.22
$ sudo cp x86/ipw3945d /sbin
```

---

### Post by handaxe on 2007-03-18
Nice reply Kobalt - a simple question, why is this at all necessary seeing that the ipw3945 is supported by the standard install? 

My own interest, if nothing else..

ta verily,

HA

---

### Post by Kobalt on 2007-03-18
As a matter of fact, in some cases installing linux-restricted-modules-$(uname -r) is enough, but some other times it's not sufficient...

---

### Post by handaxe on 2007-03-18
thanks from a (now enlightened) ipw3945 owner.

HA

---

### Post by jcbell3 on 2007-03-18
Thank you very much - these seem much easier to follow.  

The only down side is that I still get stuck with the same note:

ur kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e 
 ERROR: A compatible subsystem was not found in the following path[s]:

        /lib/modules/2.6.17-11-generic/include/ /lib/modules/2.6.17-11-generic/

You need to install the ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)
and point this build to the location where you installed those sources, eg.:

        % make IEEE80211_INC=/usr/src/ieee80211/

or use the 'make patch_kernel' within the ieee80211 subsystem to patch your
kernel sources.

make: *** [check_inc] Error 1
========================================

This step fails :

sudo ./unload    #Error

It gives a syntax error indicating that it wants a ')' in the command?


I assume that I'm doing the same thing wrong.  The biggest problem is that I don't know enough about the process to debug things.

Thanks for any guidance.

-john

---

### Post by Jamshedk on 2007-03-18
> **Kobalt said:**
> As a matter of fact, in some cases installing linux-restricted-modules-$(uname -r) is enough, but some other times it's not sufficient...


Followed your instruction to the T mate I even got teh updated versions like 1.2.0 etc etc 

but when I finally tried to run it, I get this error?  funny thing is notthing in the entire process errored at al...


slim@slim-laptop:/usr/src/ipw3945d-1.7.22$ sudo cp x86/ipw3945d /sbin
slim@slim-laptop:/usr/src/ipw3945d-1.7.22$ sudo modprobe ipw3945
FATAL: Error inserting ipw3945 (/lib/modules/2.6.17-11-386/ipw3945.ko): Invalid module format
2007-03-18 23:53:01: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

---

### Post by ctschap on 2007-03-23
I installed Edgy 6.10 a few days ago and had the same exact problems as jcbell3. Eventually I could connect to unsecured WLANs, but none that were secure...even with WEP.

I attempted to update the Intel 3945ABG drivers to 1.2.0 but was never successful.

Finally I reverted back to the 1.1.0 "out of the box" drivers and installed Wicd, found here: [http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

Now I can connect to any WLAN I choose...WPA, WEP, Open.:)

---

### Post by handaxe on 2007-03-23
@jcbell3

If your problem persists you might try deleting all the stuff you installed and simply try and load the ipw3945 drivers that come standard with ubuntu. If the card did not work with the install the best bet is that the install detection process failed to trigger the installation of the restricted modules package (seems to happen...). So,

First install the restricted modules package (NB)

then 

```
sudo depmod -a
sudo modprobe ipw3945
```Errors from this process are bad :-(.

If it works, I can then highly recommend Wicd referred to by ctschap.

---

### Post by jcbell3 on 2007-03-23
Thank you everyone - 

It is good to know that I'm not the only one with the issue.

I have tried to roll-back to the older driver.  I used the suggestions from ctschap which ran with no errors or problems.  However, I have the same issue with the standard driver.  The WI-FI adapter light flashes very fast when I try to use the wireless.

I may just wait until the new release is ready - I hear that the support for wireless and video adapters is a bit better.

Thanks again everyone - I'm getting closer to getting Linux loaded!

---

### Post by handaxe on 2007-03-23
Hi,

Out of interest, could you post the following outputs (assuming you have the driver "installed"), each separately from the terminal command line

```
dmesg | grep ipw

sudo lshw -c network

sudo ifconfig

sudo iwconfig
```

The the wireless AP you are trying to connect to unsecured, wep or wpa? (iwconfig should show this, I know...)

tx,

HA

---

### Post by jcbell3 on 2007-03-24
Thanks again for all the help.

I've pasted the results from your query below.  

john@risksupport1:~$ dmesg | grep ipw
[17179588.256000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
[17179588.256000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179588.724000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[17179590.720000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
john@risksupport1:~$ sudo lshw -C network
Password:
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:38:41:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.1.0mp firmware=13.0 1:0 () link=no multicast=yes wireless=unassociated
       resources: iomemory:dcfff000-dcffffff irq:177
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:4c:f5:af
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.59.1 firmware=5752-v3.19 link=no multicast=yes port=twisted pair
       resources: iomemory:dcef0000-dcefffff irq:74
  *-usb:1
       description: Bluetooth wireless interface
       product: Wireless 350 Bluetooth
       vendor: Dell Computer Corp.
       physical id: 4
       bus info: usb@1:2.4
       version: 24.22
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
john@risksupport1:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:4C:F5:AF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:38:41:D6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:110005 errors:0 dropped:6331 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0xe000 Memory:dcfff000-dcffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

john@risksupport1:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6331   Missed beacon:0

sit0      no wireless extensions.

What am I doing wrong?

---

### Post by handaxe on 2007-03-24
I have the same card and your info looks like mine. Mine works well. So should yours.

Did you have the wireless AP/router on when you did those commands? There is no sign of it. I assume you know this card works (say in Windoze).

What is the encryption type: wep, wpa, open? If all works, then the following command should reveal all (with the AP on):
```

sudo iwlist eth1 scan
```

Based on discussions elsewhere, also make sure that your wired connection is not connected.

HA

---

### Post by jcbell3 on 2007-04-28
Thanks everyone.  I took a bit of break for vacation and work.

I think I'm throwing in the towel on this issue.  I've upgraded to the new version (7) and eventhough it appears to be using the Intel driver it still behaves in the same fashion.  The WiFI light flashes and doesn't connect to a wide open SID.

I also have issues with my video driver which prevents me from using it with my docking station.  I'm going to wait until the next release (maybe 8?).

Thank you everyone for helping - I use Linux on a few servers at work so, we continue to support all of the effort.


Thanks,

jbell

---

### Post by NilsE on 2007-05-02
In ubuntu 7.04 the following steps worked for me which I culled from a few other posts.  This also added the capability to use WPA

```
[COLOR="Blue"]In Synaptic package manager:[/COLOR]

1) Make sure network-manager-gnome  is installed
2) Make sure wpasupplicant is installed
3) Install libpam-keyring
```
```
[COLOR="Blue"]In System Administration:[/COLOR]

Make sure the restricted driver for the chip is there.

```
```
[COLOR="blue"]In terminal[/COLOR]

1) sudo echo "@include common-pamkeyring" | sudo tee -a /etc/pam.d/gdm

NOTE: This will allow you to remember connection passwords/keys in the keyring
and not get prompted by the keyring manager every time. This is not mandatory.

```
```
[COLOR="blue"]In System/Preferences/Session[/COLOR]

1) Add gksudo nm-applet (if it is not there) as the command line to a new start programs. 
You can name it whatever you want. It may work without the gksudo.
```
[COLOR="Red"]SHUTDOWN AND RESTART[/COLOR]

NOTE: The applet may not show up in the upper panel so you can right click 
on the top panel, select add to panel then add the notification applet.

NOTE: After the first time you try to connect to a new available network in the pulldown it will ask for the SSID and key etc. but should remember it after that.

NOTE: Make sure that in the manual settings for the configuration that all devices are set to roaming.

NOTE: You may also have to clean out the /etc/network/interfaces file if you have configured any devices manually.  Just leave these 2 lines. (back it up first)

```
auto lo
iface lo inet loopback
```


I hope this helps.

---

