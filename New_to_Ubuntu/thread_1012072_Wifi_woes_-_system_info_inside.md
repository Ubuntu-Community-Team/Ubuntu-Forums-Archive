---
title: "Wifi woes - system info inside"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Nico-dk on 2008-12-15
I can't get my wifi to work, any help will be greatly appreciated

```
Output from sudo lshw -C network:

 *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945
```

and iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

I've installed Wifi Radar and can't (of course) not see any networks.

Under System > Administration > Hardware Driver only Nvidia Accelerated graphics driver (latest cards) show up.

I know I need to find a driver for my Intel pro 3945 wifi, but can't.
If memory serves (which it rarely does) this is the chipset: Mobile Intel 965PM (I'm on a Dell XPS M1530)

For reference: the xp partition can connect w/o problems.

---

### Post by Michael.Godawski on 2008-12-15
According to this site the card should work out of the box:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)
But that info does not help you.

try
```

sudo /etc/init.d/networking restart
```post ```
iwconfig
``` again
and also 
```

cat /etc/network/interfaces
```

---

### Post by Nico-dk on 2008-12-15
First of all thanks for helping a complete Linux newbie :)

Second:
sudo /etc/init.d/networking restart (= win: ipconfig /release + /renew??)
 
```
 * Reconfiguring network interfaces...                                                                                                                                    [ OK ] 
nico@nico-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
```

---

### Post by Michael.Godawski on 2008-12-15
Can you also post the output from
```
sudo iwlist scan
```

Do you recognize your wireless network somewhere?

---

### Post by Nico-dk on 2008-12-15
```
nico@nico-laptop:~$ sudo iwlist scan
[sudo] password for nico: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```
Uhm, that would be a no ;)

---

### Post by decoherence on 2008-12-15
hmmm. these folks seem to be having a similar problem

[https://bugs.launchpad.net/ubuntu/+bug/284353](https://bugs.launchpad.net/ubuntu/+bug/284353)

Could you post the output of

```
uname -a
```

which will tell you what version of the kernel you're running.

---

### Post by Nico-dk on 2008-12-15
Oops, sorry 'bout that, I'm on 8.04 (HH?)
```

Linux nico-laptop 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux
```

---

### Post by Nico-dk on 2008-12-15
Looked around a bit and found these interesting links, not sure it's a good idea to add either though (yes, I'm still geting used to repositories after so many years on Win ;) )

[http://linux.dell.com/repo/community/](http://linux.dell.com/repo/community/)

[http://support.dell.com/support/downloads/download.aspx?fileid=145675](http://support.dell.com/support/downloads/download.aspx?fileid=145675)

***edit***

Also did a search for 'wireless' in Synaptics and found the following installed:
libiw29 - Wireless tools - library - Installed version: 29-lubuntu2
ndiswrapper-common - Common scripts required to use the utilities for ndiswrapper - Installed version: 1.50-lubuntu1
pcmciautils - PCMCIA utilities for Linux 2.6 - Installed version: 014-4ubuntu1
wireless-tools - Tools for manipulating Linux Wireless Extensions - Installed version: 29lubuntu2
wpasupplicant - Client support for WPA and WPA2 (IEEE 802.11i) - Installed version: 0.6.0+0.5.8 Oubunt

---

### Post by Nico-dk on 2008-12-15
hm, strangest thing just happened.
I just enabled BlueTooth on the side of my laptop, then disabled it again (I disabled BT from services yesterday), and now this is the output from iwconfig

```
nico@nico-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

... but wait it gets a bit stranger. From my other comp I can see an unknown wifi device connected (this one), but from this one I can see no networks on either Wifi Radar or Wireless Networks.
This comp is also listed as connected to None but with an IP given by the router (which has WPA2 enabled).

---

### Post by Nico-dk on 2008-12-15
See anything different about me??
Yup, that's right, I got my wifi to work.

As a reference for other newbies having trouble with wifi, here's what I did.

1: Read the instruction manual to my new laptop, and found out the button on the right side wasn't for dis- and enabling Blue Tooth, it was for wifi (Why Dell chose a BT icon for this, I wil never know).

2: Installed Wcid ([instructions here](http://wicd.sourceforge.net/download.php) ... add repository, add app)

3: Run Wcid (really, really intuitive)

4: Click wifi ESSID > Advanced > mark Use Encryption > Choose encryption for your router > type in password and THIS IS IMPORTANT*: make sure you type the right one (mark the empty box at the bottom right to see the actual key)

5: Click OK

6: Click connect

*yes, that's right. I mistyped my password on several times :oops: ](*,)
On the plus side, I did learn some new nifty commands for the terminal

7: Say thank you to anyone who took the time to help you out.

---

### Post by Tom--d on 2008-12-15
Its always the simplest thing ;)

Why not use Network Manager?

---

### Post by Nico-dk on 2008-12-16
It kept changing encryption from WPA2 to WPA, of course this was before I discovered the error was me

---

