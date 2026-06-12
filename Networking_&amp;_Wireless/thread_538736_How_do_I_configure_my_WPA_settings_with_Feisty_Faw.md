---
title: "How do I configure my WPA settings with Feisty Fawn?"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by mamadu bwana on 2007-08-30
Hi,

I have finally found a wifi card which really works out of the box (it is recognized by the computer and it sees several networks, including mine).  My problem is that my home network is setup with WPA and not WEP.

On my fully updated Ubuntu Feisty Fawn 7.04 the network manager simply does not offer the option to enter a WPA key.  All I get is a WEP key in either hexadecimal or ascii. (I have seen the very same interface in a magazine article with WPA as a choice in the network configuration combo box).  I have installed wpasuppicant and I looked up this [Ubuntu WPA HOWTO]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-a2f430f5491955864047bd2a904c2f1fa7d4c516").  Alas, I do not have any /etc/wpa_supplicant.conf file anywhere on my computer.  In /etc I do have a wpa_supplicant/ directory with these two files: functions.sh and ifupdown.sh.  Besides, this HOWTO appears to be for the previous version of Ubuntu.

Let's assume that my key is 'TUXWINS'.  How do I configure my WPA key?  Which file do I edit? And how do I get the Gnome Network Manager to offer me a WPA option in the setting configuration for my wifi card?  Should I just created a /etc/wpa_supplicant.conf myself?!

Many thanks in advance for any help!

Mamadu

---

### Post by bmartin on 2007-08-30
[Here's the HOWTO]("http://ubuntuforums.org/showthread.php?t=318539") from the top of the wireless section.

You might find it useful to use the [WICD]("http://wicd.sourceforge.net/") program to connect to wireless networks. It boasts built-in WPA support. Quick installation instructions can be found [here]("http://blakecmartin.googlepages.com/wicd.html").

---

### Post by mamadu bwana on 2007-08-30
I began installing wicd using [these instructions]("http://blakecmartin.googlepages.com/wicd.html") only to realize that the installation of this package removes network-manager and network-manager-gnome.  I then lost all network connection.  I then noticed this little warning "* note: The wicd package conflicts with other wireless connection managers, such as wifi-radar. Installing it will require you to remove their respective packages.".  I guess I should have been more cautions.

I then did a "apt-get remove wicd" only to get these messages:

[I]root@Ubuntu2:~# apt-get remove wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wicd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 133180 files and directories currently installed.)
Removing wicd ...
Stopping wicd daemon...
 Removing any system startup links for /etc/init.d/wicd ...
   /etc/rc0.d/K20wicd
   /etc/rc1.d/K20wicd
   /etc/rc2.d/S80wicd
   /etc/rc3.d/S80wicd
   /etc/rc4.d/S80wicd
   /etc/rc5.d/S80wicd
   /etc/rc6.d/K20wicd
dpkg - warning: while removing wicd, directory   not empty so not removed.
dpkg - warning: while removing wicd, directory `/opt/wicd' not empty so not removed.
dpkg - warning: while removing wicd, directory `/opt' not empty so not removed.[/I]

I managed to somehow get my connection up again and reinstall the removed packages.  I took a look at '/opt' `/opt/wicd/' and `/opt/wicd/data' and since there was some stuff in there I did not touch it.

Did I undo the damage done by removing the network manager?

I do not feel comforable installing something which conflicts with and removes key Gnome packages.  Can somebody reccommend a Gnome-compatible way to configure WPA please?

Thanks,

Mamadu

---

### Post by bmartin on 2007-08-30
Did you read the HOWTO from the wireless section?

---

### Post by mamadu bwana on 2007-08-30
yes, I have "RTFM". and it is "over my head" and only applies to a static IP whereas my wife network at home is DHCP.  Besides, surely there must be some noobie-compatible to enter a WPA key without having to edit files with vi/gedit and not running DHCP.  Surely Newbie+DHCP+WPA is not something unheard of here, or am I at the wrong forum here and should post in some super-retard newbie forum?!

Please allow me make one thing clear: I AM A TOTAL NEWBIE AT 1) UBUNTU 2) NETWORKS 3) WIRELESS 4) WPA

---

### Post by bmartin on 2007-08-30
Perhaps you should learn patience... and read more often.

---

### Post by mamadu bwana on 2007-08-30
yes, I should. you are right. thank you for your help!

---

### Post by imdano on 2007-08-30
> **mamadu bwana said:**
> 

Did I undo the damage done by removing the network manager?

I do not feel comforable installing something which conflicts with and removes key Gnome packages.  Can somebody reccommend a Gnome-compatible way to configure WPA please?

Thanks,

MamaduRemoving network-manager doesn't actually cause any damage.  It's no more a "key Gnome package" than wicd is, really.  They both manage network connections, network-manager is just the one installed by default  (although a few applications make use of NM to find out about connection status, but not having it just means it finds out slower than it normally would).  Wicd is set to conflict with network-manager because trying to run both at the same time is likely to cause connection problems.

Also there is not harm in removing the /opt/wicd folder if you don't want to use it.  It's probably just configuration files that are left over.

---

### Post by mamadu bwana on 2007-08-30
Thanks a lot for this information, I really appreciate it.  Would you have any advice as to how I could solve my Newbie+DHCP+WPA headache with either a Gnome application or at least a Gnome-compatible one?

In particular, how do I get a WPA option in the network configuration combo box? I mean, I have actually seen this in a magazine.  The same Ubuntu version and the same network configuration application but with both WEP and WPA as a choice.  Surely that must be the best way to go to make that happen?

---

### Post by imdano on 2007-08-30
Assuming you have NetworkManager installed now, you should be able to just select your network from the list it finds, and it should ask for a key and WPA should be the encryption option you see.  If only WEP is showing up, that likely means you have a driver problem of some kind.  Open up a terminal and paste the output of the following ```
sudo lshw -C network
iwlist scan
```

---

### Post by mamadu bwana on 2007-08-30
ok sure. here goes:


```
root@Ubuntu2:~# sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 9
       bus info: pci@01:09.0
       logical name: wifi0
       version: 01
       serial: 00:0f:b5:5c:88:80
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.1) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:ff8d0000-ff8dffff irq:11
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@01:0a.0
       logical name: eth0
       version: 10
       serial: 00:30:bd:22:7f:74
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:c400-c4ff iomemory:ff8ffc00-ff8ffcff irq:11
root@Ubuntu2:~# 
```

and

```

root@Ubuntu2:~# sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 9
       bus info: pci@01:09.0
       logical name: wifi0
       version: 01
       serial: 00:0f:b5:5c:88:80
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.1) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:ff8d0000-ff8dffff irq:11
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@01:0a.0
       logical name: eth0
       version: 10
       serial: 00:30:bd:22:7f:74
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:c400-c4ff iomemory:ff8ffc00-ff8ffcff irq:11
root@Ubuntu2:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:15:E9:6C:50:22
                    ESSID:"dlink"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=10/94  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f01010000ff7f
          Cell 02 - Address: 00:12:17:3C:F9:EB
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/94  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:1A:70:E2:63:98
                    ESSID:"bwananet"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/94  Signal level=-57 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 04 - Address: 00:16:B6:A8:71:DD
                    ESSID:"linksys_SES_11643"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=4/94  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  

root@Ubuntu2:~# 
```

does this help?

BTW - the this shows all the networks around my house, including the ones of my neighbors, mine being 'bwananet'

many many thanks!

---

### Post by imdano on 2007-08-30
Your driver appears to be installed correctly and iwlist scan is correctly reporting that your network is using WPA encryption, so I'm not sure why NetworkManager isn't giving you the option.  I know quite a few people who have an Atheros card (like you do) have had success using wicd, so you might want to give it a try.  It might help to follow the installation instructions bmartin posted upthread.

---

### Post by kevdog on 2007-08-30
You are probably better off with WICD, but if you want to try one last effort with gnome network manager, read this -- and notice your interface name is ath0 and not wlan0:

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by shamrock_uk on 2007-09-03
I'll second the 'use WICD' advice, after plowing through the wpa_supplicant howto on xubuntu with no success (not a newbie here, either), WICD worked flawlessly for me. 

Mamada, I would suggest you go to [here](https://sourceforge.net/project/showfiles.php?group_id=194573) and download the stable .deb file. 

Double-click it and then hit install. 

You don't mention what happened after you installed it last time, other than you immediately reinstalling network manager, so what you need to do is find WICD on the applications menu (or run it by typing Alt+F2 and inputting *wicd* in the box and hitting enter).

Then your network should show there and you should have the option to input your WPA options. 

Do let us know how it is going.

---

### Post by dysphoros on 2007-09-03
I have an Atheros AR5212 NIC which did not work 'out of the box' on Feisty.  The problem seems to be with the MadWifi driver.

- add ath_hal and ath_pci to /etc/modprobe.d/blacklist
- reboot or rmmod these modules
- install ndiswrapper-common and ndiswrapper-utils-1.9
- download the windows drivers for your card (you need an .INF and corresponding .SYS file)
- install the driver using ndiswrapper (e.g. sudo ndiswrapper -i NET5211.INF)
- sudo depmod -a
- sudo modprobe ndiswrapper
- sudo ndiswrapper -m

I now have a working network card which connects using WPA2!

For more detailed information see:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Good Luck

---

### Post by mamadu bwana on 2007-09-06
> **shamrock_uk said:**
> I'll second the 'use WICD' advice, after plowing through the wpa_supplicant howto on xubuntu with no success (not a newbie here, either), WICD worked flawlessly for me. 

Mamada, I would suggest you go to [here](https://sourceforge.net/project/showfiles.php?group_id=194573) and download the stable .deb file. 

Double-click it and then hit install. 

You don't mention what happened after you installed it last time, other than you immediately reinstalling network manager, so what you need to do is find WICD on the applications menu (or run it by typing Alt+F2 and inputting *wicd* in the box and hitting enter).

Then your network should show there and you should have the option to input your WPA options. 

Do let us know how it is going.

The first time I downloaded and installed WICD it freaked me out by disconnecting me off the Internet.  In a panic, I apt-get removed it and reinstalled gnome network manager.  then I went back to the network setup and somehow managed to reconnect to the internet.  my palms by then were cold and sweaty and I was freaked out.

The thing is that by cutting off my internet connection the installation of WICD prevented me from downloading the gnome network manager it had uninstalled.  I have no idea why I manager to reconnect and reinstall the gnome network manager.

Is there any way I can protect myself from loosing my connection when I install WICD?  I would gladly try installing WICD if I would know that I am not going to loose my connection.

Many thanks for any help and sorry for the late reply to your kind offer.

Mamadu

---

### Post by kevdog on 2007-09-06
You can download the appropriate deb files but not install them

sudo aptitude download network-manager network-manager-gnome

These files will be kept in /var/cache/apt/archives.

That way if you need to reinstall them later without an internet connection, you will already have a copy of them.  Look in the archives directory first, you might already have the packages.

---

### Post by unisol on 2007-09-06
> **mamadu bwana said:**
> I began installing wicd using [these instructions]("http://blakecmartin.googlepages.com/wicd.html") only to realize that the installation of this package removes network-manager and network-manager-gnome.  I then lost all network connection.  I then noticed this little warning "* note: The wicd package conflicts with other wireless connection managers, such as wifi-radar. Installing it will require you to remove their respective packages.".  I guess I should have been more cautions.

I then did a "apt-get remove wicd" only to get these messages:

[I]root@Ubuntu2:~# apt-get remove wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wicd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 133180 files and directories currently installed.)
Removing wicd ...
Stopping wicd daemon...
 Removing any system startup links for /etc/init.d/wicd ...
   /etc/rc0.d/K20wicd
   /etc/rc1.d/K20wicd
   /etc/rc2.d/S80wicd
   /etc/rc3.d/S80wicd
   /etc/rc4.d/S80wicd
   /etc/rc5.d/S80wicd
   /etc/rc6.d/K20wicd
dpkg - warning: while removing wicd, directory   not empty so not removed.
dpkg - warning: while removing wicd, directory `/opt/wicd' not empty so not removed.
dpkg - warning: while removing wicd, directory `/opt' not empty so not removed.[/I]

I managed to somehow get my connection up again and reinstall the removed packages.  I took a look at '/opt' `/opt/wicd/' and `/opt/wicd/data' and since there was some stuff in there I did not touch it.

Did I undo the damage done by removing the network manager?

I do not feel comforable installing something which conflicts with and removes key Gnome packages.  Can somebody reccommend a Gnome-compatible way to configure WPA please?

Thanks,

Mamadu

to completely remove wicd type these commands in a terminal
sudo apt-get remove wicd
sudo rm -rf dir /opt/wicd

---

### Post by mamadu bwana on 2007-09-12
Ok.  So I decided to give wicd a shot, but with with a live-CD first, just in case.  I followed all the installation instructions with not problems.  Then I tired to start wcid from the applications menu but nothing would happen, so I tried from a root terminal and here is what I got:

> ubuntu@ubuntu:~$ sudo wicd
attempting to connect daemon...
daemon not running, running gksudo ./daemon.py...
daemon still not running, aborting.
Traceback (most recent call last):
  File "/usr/local/bin/wicd", line 37, in <module>
    daemon = dbus.Interface(proxy_obj, 'org.wicd.daemon')
NameError: name 'proxy_obj' is not defined
ubuntu@ubuntu:~$ 

Any ideas as to what this means?

Many thanks,

Mamadu

---

### Post by merlin666 on 2007-09-12
I have just got my wifi up and running using WPA-TKIP, MAC filtering,and ESSID disbaled following this how-to:

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) 

I found the set-up very easy, but it seems network manager becomes useless with a manual configuration. I will remove the network manager, and may try wcid too, though.

---

### Post by imdano on 2007-09-12
> **mamadu bwana said:**
> Ok.  So I decided to give wicd a shot, but with with a live-CD first, just in case.  I followed all the installation instructions with not problems.  Then I tired to start wcid from the applications menu but nothing would happen, so I tried from a root terminal and here is what I got:



Any ideas as to what this means?

Many thanks,

MamaduThe wicd daemon isn't running. run ```
sudo /etc/init.d/wicd start
```

---

### Post by mamadu bwana on 2007-09-18
I am truly sorry for being so totally obtuse and I beg for your help.

I followed the following instructions to install wicd:
> 
echo "deb [http://wicd.longren.org](http://wicd.longren.org) feisty extras" | sudo tee /etc/apt/sources.list.d/wicd.list
sudo apt-get update
sudo apt-get install wicd
sudo ln -s /opt/wicd/gui.py /usr/local/bin/wicd
sudo wget -O /usr/local/bin/wicd-tray [http://blakecmartin.googlepages.com/wicd-tray](http://blakecmartin.googlepages.com/wicd-tray)
sudo chmod 755 /usr/local/bin/wicd-tray

It all worked well but as soon as I did "sudo apt-get install wicd" it shot the network I was using (nothing fancy, regular cable connectiopn to my router with DHCP) and, of course, as soon as I got to sudo "wget -O /usr/local/bin/wicd-tray" it could not wget anything.  I tried using the network manager GUI but to no avail.  I tried "ifconfig eth0 dynamic && ifconfig eth0 up" (that is the correct syntax to start a card with DHCP from the CLI, right?) - but my network is down.

How did the folks who suggested the commands above think we could wget anything once the network is down?!  What am I missing?

Please help!

Thanks,

Mamadu

---

### Post by mamadu bwana on 2007-09-21
bump (sorry - I *really* need help here!)

---

