---
title: "Zyxel ZyAir g-302 v3 problem (realtek chipset)"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by LEDominator on 2007-06-19
Hey all,

I was hoping you could help me with this problem. I have put a Zyxel ZyAir G302-V3 card into my system and am running Ubuntu Feisty. The problem is it is listed in lshw and lspci, but I can't get the driver to compile and install. Any help is appreciated

> 
    lshw result

    *-network UNCLAIMED
    description: Ethernet controller
    product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
    vendor: Realtek Semiconductor Co., Ltd.
    physical id: 8
    bus info: pci@04:08.0
    version: 20
    width: 32 bits
    clock: 33MHz
    capabilities: bus_master cap_list
    configuration: latency=32 maxlatency=64 mingnt=32
    resources: ioport:bc00-bcff iomemory:fdbfe000-fdbfe1ff irq:5

    lspci -v

    04:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Contro
    ller (rev 20)
    Subsystem: ZyXEL Communication Corporation Unknown device 340d
    Flags: bus master, medium devsel, latency 32, IRQ 5
    I/O ports at bc00 [size=256]
    Memory at fdbfe000 (32-bit, non-prefetchable) [size=512]
    Capabilities: <access denied>

    make error

    tniblett@slo-ubuntu-mpc:~/Desktop/rtl8180-0.21$ sudo make
    Password:
    make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/tniblett/Desktop/rtl8180-0.21 MODVERDIR=/home/tniblett/Desktop/rtl8180-0.21 modules
    make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
    scripts/Makefile.build:17: /home/tniblett/Desktop/rtl8180-0.21/Makefile: No such file or directory
    make[2]: *** No rule to make target `/home/tniblett/Desktop/rtl8180-0.21/Makefile'. Stop.
    make[1]: *** [_module_/home/tniblett/Desktop/rtl8180-0.21] Error 2
    make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
    make: *** [2.6] Error 2
    tniblett@slo-ubuntu-mpc:~/Desktop/rtl8180-0.21$



---

### Post by LEDominator on 2007-06-19
bump

---

### Post by LEDominator on 2007-06-19
anyone? bump

---

### Post by LEDominator on 2007-06-19
anyone please

bump

---

### Post by LEDominator on 2007-06-19
bump again

I have looked everywhere to no avail and read about 20+ guides.  The card is supported, I just can't get it to work.  Any ideas are more than welcome

---

### Post by LEDominator on 2007-06-19
you know, if they fixed this part of the guide

> lshw result

*-network UNCLAIMED
description: Ethernet controller
product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 8
bus info: pci@04:08.0
version: 20
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=32 maxlatency=64 mingnt=32
resources: ioport:bc00-bcff iomemory:fdbfe000-fdbfe1ff irq:5

lspci -v
it would be a whole lot easier.  I finally gave up on trying the linux driver and went to ndiswrapper.  At least I can see my wireless lan now, though now I have to get wpa working.  I also noticed that in the linux driver build it is trying to install the module with a .ko extension though I don't see that in any of the files present (though I am also pretty new to linux so this may not mean anything at all).  I next tried to move the folders into the module section and modprobe them there, but I don't have the permissions to move and it won't let me log in as root.  I was liking Ubuntu up to this point, but I am about ready to say screw it, wipe my hard-drive and move to a new distro.

---

### Post by morpheusj30 on 2007-06-19
LEDominator don't give up just yet...
Here is what you need to do to get the root password.
1. From the terminal type sudo passwd root
2. You will be prompted for a new password, type what you want, then confirm it.

that is it for the root password part.
now for you wireless problem.  I got the same card and I am having the same problem. Apparently, there is a bug in Fiesty, refer to this link to read more [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsZyxel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsZyxel)

I beleive between you and I, we can get this problem solved.
So far, I reinstall Edgy on my box.... but if you are able to scan in fiesty, you are almost there.

---

### Post by Bachstelze on 2007-06-19
Setting up a root password is neither necessary, nor useful, let alone recommended.

About your wireless problems, it seems you guys will have to use Ndiswrapper.

---

### Post by LEDominator on 2007-06-19
> **morpheusj30 said:**
> LEDominator don't give up just yet...
Here is what you need to do to get the root password.
1. From the terminal type sudo passwd root
2. You will be prompted for a new password, type what you want, then confirm it.

that is it for the root password part.
now for you wireless problem.  I got the same card and I am having the same problem. Apparently, there is a bug in Fiesty, refer to this link to read more [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsZyxel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsZyxel)

I beleive between you and I, we can get this problem solved.
So far, I reinstall Edgy on my box.... but if you are able to scan in fiesty, you are almost there.
I stumbled across that same document while reading through the various wiki how-to's.  I can see my network and everything with ndiswrapper.  The next part for me was getting to the WPA security but I am running into troubles with that as well.  My question for you is did it work fine in Edgy?  If so it might be worth going back to that, though it would be a pain for me to re-setup MythTV (though doable if I have to).  I just didn't think Feisty would be giving me so much crap.  Although it is newer... so, I guess that is to be expected.  Did ndiswrapper in feisty not work for you at all?

---

### Post by morpheusj30 on 2007-06-20
So far no, I am not able to associate my essid with the card. I can only scan for broadcast.
I am going to turn off encryption on my AP to see if I can get in.

I will keep you updated.

---

### Post by tturrisi on 2007-06-20
This is how to install the correct drivers, along w/ a patch that enables the card to work w/ aircrack.  It should work.
0. get rid of ndiswrapper & network-manager
1. open a root terminal
2. do:
```

cd /usr/src
apt-get install build-essential llinux-headers-`uname -r`
ifconfig wlan0 down
rmmod r8180
wget http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz
wget http://patches.aircrack-ng.org/rtl8180-0.21v2.patch
tar -xvzf rtl8180-0.21.tar.gz
cd rtl8180-0.21
patch -Np1 -i ../rtl8180-0.21v2.patch
make && make install
depmod -a
modprobe r8180
```

---

### Post by morpheusj30 on 2007-06-21
ok, I got the card to work and I successfully connected to the internet. Has a matter of fact, this is the connection I am using right now.  BUT, this connection is with no WEP or WPA.

Here is what I did to get this to work:

A. Copy the WINXP directory from the Drivers directory on the NIC CDROM somewhere in your system. I placed mine in /usr/share/LinuxWirelessDrivers/WINXP.

B. then I followed the directions from this link: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

Here is my bash history:

First cd into the directory where you have the windows drivers
sudo ndiswrapper -i net8185.inf 
sudo ndiswrapper -l
dmesg | grep ndiswrapper
sudo rmmod ndiswrapper; sudo modprobe ndiswrapper
dmesg | grep ndiswrapper
ifconfig  (By this point you should see wlan0 listed)
sudo modprobe ndiswrapper
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo dhclient wlan0

I have some wpa_supplicant history, but it is not working out yet.
I will keep you posted.

---

### Post by morpheusj30 on 2007-06-23
have you been able to get wpa to work?

---

### Post by morpheusj30 on 2007-06-23
tturrisi,

I followed your instructions and that did not work.

---

### Post by djongo on 2007-06-27
I sort of followed the instructions given by morpheusj30, but got sidetracked when I got to the ndiswrapper website. After uninstalling ndiswrapper and then installing it from source (version 1.47), I got it working with wpa briefly by following the instruction on the ndiswrapper webpage. I unplugged my cable and had everything working. After a restart it stopped working though, so I'm still looking for a solution.
I've tried following morpheusj30's instructions to the letter, but no luck with wpa.

---

### Post by djongo on 2007-07-18
Got it working! I did a detour around some other distros to see whether they could handle wpa wireless, but had no luck with fedore 7, debian etch, suse 10.2, FreeSpire, or PCLinuxOS 2007. PCLinuxOS had the best graphical interface for this sort of stuff IMO. Anyway, reinstalled the fawn. These are the steps i followed to get wireless with wpa working:
1) remove ndiswrapper
2) get ndiswrapper from their website [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net). I have version 1.47. 
3) compile ndiswrapper. There may be some package you need to install to resolve dependencies.
4) get wpa_supplicant from their website . I have version 0.5.8
5) compile wpa_supplicant
6) download newest windows driver from zyxels homepage
7) download and compile Wireless Tools for Linux ([http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html))
8 ) follow the excellent guide at ndiswrappers homepage about setting up ndiswrapper and wpa_supplicant
9) This is my /etc/network/interfaces
auto wlan0
iface wlan0 inet dhcp
wireless-essid ESSID
wireless-channel 11
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
10) I still need to run "/etc/init.d/networking restart" after booting to get an ip address from my dhcp server, but I will work on getting that run in a boot script now.

---

### Post by m_bridge on 2007-10-18
you may be interested in that
[http://ubuntuforums.org/showthread.php?p=3563852#post3563852](http://ubuntuforums.org/showthread.php?p=3563852#post3563852)
same card, working fine

---

