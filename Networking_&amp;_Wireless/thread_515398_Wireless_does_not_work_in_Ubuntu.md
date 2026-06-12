---
title: "Wireless does not work in Ubuntu"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by init1 on 2007-08-01
I can't get a wireless internet connection in Ubuntu. It works fine in Mepis, but not Ubuntu. I followed [this]("https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29") guide, and one other on the forums, but it still does not work! There are other tutorials to try, but I don't want to have to do more work than I have to. Please help!
 description: Network controller
                product: Dell Wireless 1390 WLAN Mini-PCI Card
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@06:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: iomemory:30000000-30003fff irq:3
This is part of what I get in "lshw"
I have a Compaq Presario C304NR.

---

### Post by noob12 on 2007-08-02
Can you show the full output of

```

lspci -nn

lshw -C network

```

---

### Post by init1 on 2007-08-02
Thanks for the response!

lspci -nn:
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI [8086:27c5] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
06:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 01)
08:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

lshw -C network:
  *-network UNCLAIMED     
       description: Network controller
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:30000000-30003fff irq:3
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:b7:9b:99
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.102 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-20ff iomemory:d0100000-d01000ff irq:20

---

### Post by noob12 on 2007-08-02
If you are on Feisty, I'd recommend using ndiswrapper with the Windows drivers.  

There is a generic HOWTO at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). 

If you have trouble following that, you can get more help by posting back to this thread.

---

### Post by init1 on 2007-08-02
OK, I'll try it. I already tried a similar tutorial with ndiswrapper and the Ubuntu wiki, but this might be slightly different.

---

### Post by kevdog on 2007-08-02
Follow the instructions below and avoid installing ndiswrapper from any type of repository since its an older version and in some cases will not work, in either case you will need win xp drivers for your card -- do you have those on an installation disk??:

Here are my "universal installation instructions" for ndiswrapper:

First there are a few things you need to do to compile from source -- install the build-essential package along with the linux header files.  Here is how to do this in case you dont have an internet conneciton:

```
If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


Ok, next grab the ndiswrapper source files from: _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_
You want ndiswrapper-1.47

Working at command line
```
cd ~
mkdir ndiswrapper
cd ndiswrapper
Place the ndiswrapper-1.47.tar.gz inside this ~/ndiswrapper

```
To proceed
```
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```

The output should be something like the following:
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586

```

Next create and place your Windows XP wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the WinXP driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running.

---

### Post by init1 on 2007-08-02
This is rather confusing, there are so many options to try. Apparently, I have already installed the driver, but ndiswrapper says that it is invalid.

---

### Post by init1 on 2007-08-02
> **kevdog said:**
> Follow the instructions below and avoid installing ndiswrapper from any type of repository since its an older version and in some cases will not work, in either case you will need win xp drivers for your card -- do you have those on an installation disk??:

Here are my "universal installation instructions" for ndiswrapper:

First there are a few things you need to do to compile from source -- install the build-essential package along with the linux header files.  Here is how to do this in case you dont have an internet conneciton:

```
If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


Ok, next grab the ndiswrapper source files from: _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_
You want ndiswrapper-1.47

Working at command line
```
cd ~
mkdir ndiswrapper
cd ndiswrapper
Place the ndiswrapper-1.47.tar.gz inside this ~/ndiswrapper

```
To proceed
```
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```

The output should be something like the following:
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586

```

Next create and place your Windows XP wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the WinXP driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:


Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running.
Nice tutorial, but I don't know what driver to download. I have three options

#
Card: Dell Wireless 1390 WLAN MiniCard (Dell Inspiron E1405, Dell Inspiron E1505, Dell Latitude D620, Dell Inspiron 640m, Compaq Presario V3010AU, V3011AU)

    *
      Chipset: Broadcom BCM4311
    *
      pciid: 14e4:4311 (rev 01, subsys 1028:0007)
    *
      Driver: generally called bcmwl5 [http://ftp.us.dell.com/network/R115321.EXE](http://ftp.us.dell.com/network/R115321.EXE), though reporting that R115321.EXE driver does not work for Kubuntu 6.06 LTS 64-bit (Kernel 2.6.15-27),[http://ftp.us.dell.com/network/R140747.EXE](http://ftp.us.dell.com/network/R140747.EXE) UPDATE: The above driver has a mayor security bug, the newest driver is R140747.EXE.
    *
      Alternate 64 bit driver: [http://h10025.www1.hp.com/ewfrf/wc/softwareList?lc=en&cc=us&dlc=en&tool=softwareCategory&product=3210693&os=228](http://h10025.www1.hp.com/ewfrf/wc/softwareList?lc=en&cc=us&dlc=en&tool=softwareCategory&product=3210693&os=228)

Edit:
Never mind. I know which one to use. I extract it with "unzip -a", right?

---

### Post by init1 on 2007-08-02
It's not working. It says the driver is already installed, but that it is invalid. What now?
Edit:
Never mind. I uninstalled the old one and installed the new one.

---

### Post by kevdog on 2007-08-02
Did you pick the second link -- I think that is the right driver.

Can you post back
ndiswrapper -v
ndiswrapper -l

So I can get a better idea!

---

### Post by init1 on 2007-08-02
It's working! It's working! Thank you! The light has come on. The only issue now, is that I cannot seem to figure out how to set up WPA.

---

### Post by kevdog on 2007-08-02
Just to make sure its working 

Can you ping or surf the web???
Are you getting an IP address -- ie ifconfig

If the answer to all the above is yes, then do the following

sudo aptitude install wpasupplicant

There are many ways to connect with WPA -- just need to know more what you want.  Do you need a static IP, or is a dynamic IP suitable?  Are you using network manager??? Do you intend to use multiple networks -- ie like a laptop??

---

### Post by init1 on 2007-08-02
> **kevdog said:**
> Just to make sure its working 

Can you ping or surf the web???
Are you getting an IP address -- ie ifconfig

If the answer to all the above is yes, then do the following

sudo aptitude install wpasupplicant

There are many ways to connect with WPA -- just need to know more what you want.  Do you need a static IP, or is a dynamic IP suitable?  Are you using network manager??? Do you intend to use multiple networks -- ie like a laptop??
I cannot connect yet, because I need wpa support. I want DHCP, and I don't mind setting up the configuration for each network. I am using the network manager. I already have wpa_supplicant.  If it would be easier, I wouldn't mind trying something other then network manager.

---

### Post by kevdog on 2007-08-02
Usually I like to test the network before adding wpa, but I guess we will proceed in your case, cross your fingers:

```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
gksu gedit /etc/network/interfaces
```

Comment out everything other than &#8220;lo&#8221; entries in that file and save the file

```
sudo touch /etc/default/wpasupplicant
echo "ENABLED=0" | sudo tee -a /etc/default/wpasupplicant
```

Restart the networking bus:

```
sudo /etc/init.d/dbus restart
```
 
If you cant connect, try rebooting:
```
sudo shutdown -r now
```

Go to the network manager icon in the system tray.  Click on the network you want to connect to.  It should ask you for credentials, wpa, etc.

Good luck!

---

### Post by init1 on 2007-08-02
WPA is not an option.

---

### Post by kevdog on 2007-08-02
Yea I see that, did you reboot??

Can you start posting some of the info Ive asked for:
/etc/network/interfaces
/etc/iftab
iwlist wlan0 scan
wpa_supplicant -v
ndiswrapper -v
modinfo ndiswrapper


More details about WPA -- 1/2?
TKIP/AES Cipher??
PSK -- Dont have to give me the key, just tell me is this how its configured as wpa-psk??

---

### Post by init1 on 2007-08-02
> **kevdog said:**
> Yea I see that, did you reboot??

Can you start posting some of the info Ive asked for:
/etc/network/interfaces
/etc/iftab
iwlist wlan0 scan
wpa_supplicant -v
ndiswrapper -v
modinfo ndiswrapper


More details about WPA -- 1/2?
TKIP/AES Cipher??
PSK -- Dont have to give me the key, just tell me is this how its configured as wpa-psk??
/etc/network/interfaces:
> auto lo
iface lo inet loopback


# iface eth0 inet dhcp

# auto eth1
# iface eth1 inet dhcp

# auto eth2
# iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp




# auto eth0

/etc/ifstab:
> 
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:d4:b7:9b:99 arp 1
eth1 mac 00:14:a5:de:9b:25 arp 1



iwlist wlan0 scan:
> 
wlan0     Interface doesn't support scanning.


But this works
iwlist scanning
> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:39:B4:92:8F
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 02 - Address: 00:13:10:18:AA:21
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


wpa_supplicant -v:
> 
wpa_supplicant v0.5.5
Copyright (c) 2003-2006, Jouni Malinen <jkmaline@cc.hut.fi> and contributors


ndiswrapper -v:
> 
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 


modinfo ndiswrapper:
> 
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
license:        GPL
version:        1.47
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     FA633DF63916E1784E6852C
depends:        usbcore
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

The psk is
> 
7243f3dd4e4521c3d9fdfe18f6aab7310b40d119e49d2cc32615a58c5979553b


---

### Post by kevdog on 2007-08-02
Ok, ndiswrapper by default sets up an interface on wlan0.  Assuming your wireless card is eth1, you are going to have to change eth1 to wlan0 in the /etc/iftab file.

Make sure there is one line in the /etc/modules file that says ndiswrapper, and also that in /etc/modprobe.d/ndiswrapper, its states alias wlan0 ndiswrapper.

Reboot after making the changes.

---

### Post by init1 on 2007-08-02
OK, I'll do that. But the problem is that I can't configure WPA. The network is detected.

---

### Post by kevdog on 2007-08-02
Just to make it more of a pain for you, when you reboot, make sure you dont have your wired network connected.  Ubuntu without some specialized configuration can not simaltaneously run a wired and wireless network at the same time.

---

### Post by init1 on 2007-08-02
OK, I've done everything I need to. I'm going to restart now.

---

### Post by init1 on 2007-08-02
Still cannot connect. I'll try messing with WPA stuff.

---

### Post by kevdog on 2007-08-02
Ok, time to break out the heavy armor, since something is not working, we have to figure out what it is -- (again I wish you could turn wpa off for a while to test the basic settings).

Create this file:
```
gksu gedit /etc/wpa_supplicant.conf
```
```

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
network={
   ssid="linksys"
   scan_ssid=0
   proto=WPA
   key_mgmt=WPA-PSK
   pairwise=TKIP
   group=TKIP
   psk=7243f3dd4e4521c3d9fdfe18f6aab7310b40d119e49d2cc326 15a58c5979553b
 }
```

Now at the command line type the following:
```
sudo ifconfig wlan0 down
sudo killall dhclient wpa_supplicant dhclient3
sudo rm /var/run/dhclient.pid
sudo wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo dhclient wlan0
```

---

### Post by init1 on 2007-08-02
I did all of that and then restarted. Still does not work.

---

### Post by kevdog on 2007-08-02
You dont have to restart after typing those commands, after the last command you should get something telling you that you received an IP address (if using DHCP).  What output did you get after the last command.  Forget the GUI for right now, we are doing everything manually to troubleshoot if there is a problem.  Since the GUI doesnt give feedback, we are resorting to something different to discover where the problem is.

By the way
What kind of key is this??
7243f3dd4e4521c3d9fdfe18f6aab7310b40d119e49d2cc326 15a58c5979553b

Is this a hex key, because it has a space in it, which will not work (it sure looks like hex without the space)

---

### Post by init1 on 2007-08-02
> **kevdog said:**
> You dont have to restart after typing those commands, after the last command you should get something telling you that you received an IP address (if using DHCP).  What output did you get after the last command.  Forget the GUI for right now, we are doing everything manually to troubleshoot if there is a problem.  Since the GUI doesnt give feedback, we are resorting to something different to discover where the problem is.

By the way
What kind of key is this??
7243f3dd4e4521c3d9fdfe18f6aab7310b40d119e49d2cc326 15a58c5979553b

Is this a hex key, because it has a space in it, which will not work (it sure looks like hex without the space)
The DHCP client failed. How should I obtain the key?
Edit:
Does this look right?
7243f3dd4e4521c3d9fdfe18f6aab7310b40d119e49d2cc32615a58c5979553b

---

### Post by kevdog on 2007-08-02
If you know the ASCII version of the key (hopefully it doesnt have any spaces) then you can generate the hex version by the following:

Now convert your WPA ASCII password using the following command (' ' single quotes required):

```
wpa_passphrase 'your_essid' 'your_ascii_key'
```

Resulting in an output like...

```
network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab5bbc6c52e7522f709a
}
```

The psk value is your hex key.  You would cut and paste this hex value in the /etc/wpa_supplicant.conf file.  If it really ends up with a space after doing this, then I guess this is it.

Alternative solution

so doing the above you would end up with something like:

Hex Variant
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab5bbc6c52e7522f709a

If you know the ASCII text password you could also just do the following:
psk="*ASCII_KEY*"

With the ascii key you need the quotes.

So in summary:

```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
network={
   ssid="linksys"
   scan_ssid=0
   proto=WPA
   key_mgmt=WPA-PSK
   pairwise=TKIP
   group=TKIP

----Do not include this line either use either one of the two lines (HEX or ASCII variant):
   psk=*HexKEY*
   psk=*"ASCIIKEY"*
 }
```

**Also notice quotes around ssid name!**

---

### Post by init1 on 2007-08-02
That's how I got the value. The space was added by the forum.
I have updated the config file. I will reboot soon

---

### Post by init1 on 2007-08-02
Nope. Still not working.

---

### Post by kevdog on 2007-08-02
Rather than just saying it doesnt work, can you post some error messages or something??

Check dmesg, I cant help you if you dont tell me any information.

---

### Post by init1 on 2007-08-02
OK, I didn't see anything odd in dmesg. I suspect it has to do with wpa_supplicant. When I run 
```

wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf

```
I get 
> 
Line 4: failed to parse ssid 'linksys'.
Line 4: failed to parse ssid 'linksys'.
Line 12: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.

Is this something to worry about? Or did I give bad parameters?

---

### Post by kevdog on 2007-08-03
I know you are kind of doing you own thing here but there is definitely a problem with you statement:

You have:
```
wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
```

when it should be more like the following:

```
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
```


Second take a look at your
iwlist scan 
results

I just did a second time
There are two routers with the essid of "linksys", however each have a different MAC address.  I assume you are connecting to one of these routers named "linksys", unless your essid is not being broadcast.  Do you know the name of the router??
If this is really the case, then we need to do a little modification:

Here is the modification:
```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
network={
   ssid="linksys"
   bssid=<MAC ADDRESS in format xx:xx:xx:xx:xx:xx>
   scan_ssid=0  <Use 0 if the essid is being broadcast, 1 if the essid is hidden>
   proto=WPA
   key_mgmt=WPA-PSK
   pairwise=TKIP
   group=TKIP

----Do not include this line either use either one of the two lines (HEX or ASCII variant):
   psk=HexKEY
   psk="ASCIIKEY"
 }
```

```
sudo ifconfig wlan0 down
sudo killall dhclient wpa_supplicant dhclient3
sudo rm /var/run/dhclient.pid
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

Basically you need to tell me the ssid of the router, whether the essid is being broadcast.  I dont have enough info to guide you!

---

### Post by init1 on 2007-08-03
> **kevdog said:**
> I know you are kind of doing you own thing here but there is definitely a problem with you statement:

You have:
```
wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
```

when it should be more like the following:

```
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
```


Second take a look at your
iwlist scan 
results

I just did a second time
There are two routers with the essid of "linksys", however each have a different MAC address.  I assume you are connecting to one of these routers named "linksys", unless your essid is not being broadcast.  Do you know the name of the router??
If this is really the case, then we need to do a little modification:

Here is the modification:
```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
network={
   ssid="linksys"
   bssid=<MAC ADDRESS in format xx:xx:xx:xx:xx:xx>
   scan_ssid=0  <Use 0 if the essid is being broadcast, 1 if the essid is hidden>
   proto=WPA
   key_mgmt=WPA-PSK
   pairwise=TKIP
   group=TKIP

----Do not include this line either use either one of the two lines (HEX or ASCII variant):
   psk=HexKEY
   psk="ASCIIKEY"
 }
```

```
sudo ifconfig wlan0 down
sudo killall dhclient wpa_supplicant dhclient3
sudo rm /var/run/dhclient.pid
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

Basically you need to tell me the ssid of the router, whether the essid is being broadcast.  I dont have enough info to guide you!
The ssid is "linksys". It is being broadcast.

---

### Post by init1 on 2007-08-03
Nope. Didn't work. I got some errors. 

> wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
Line 4: failed to parse ssid 'linksys'.
Line 4: failed to parse ssid 'linksys'.
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
group: 0x8
PSK - hexdump(len=32): [REMOVED]
Line 12: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface wlan0                   


> dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:a5:de:9b:25
Sending on   LPF/wlan0/00:14:a5:de:9b:25
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---

### Post by kevdog on 2007-08-03
Wow, its choking trying to find "linksys".  Can you post the following for me (I havent ever had it choke this early in the configuration:

iwlist scan
/etc/wpa_supplicant.conf

Thanks

---

### Post by init1 on 2007-08-05
> **kevdog said:**
> Wow, its choking trying to find "linksys".  Can you post the following for me (I havent ever had it choke this early in the configuration:

iwlist scan
/etc/wpa_supplicant.conf

Thanks
iwlist scan
> wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:B4:92:8F
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 02 - Address: 00:13:10:18:AA:21
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0



/etc/wpa_supplicant.conf
> ap_scan=1                                                                                                                    
ctrl_interface=/var/run/wpa_supplicant                                                                                       
 network={                                                                                                                   
  ssid=linksys                                                                                                               
  scan_ssid=0                                                                                                                
  proto=WPA                                                                                                                  
  key_mgmt=WPA-PSK                                                                                                           
  pairwise=TKIP                                                                                                              
  group=TKIP                                                                                                                 
  psk=7243f3dd4e4521c3d9fdfe18f6aab7310b40d119e49d2cc32615a58c5979553b                                                       
                                                                                                                             
  }                                                                                                                          
                                                                                                                             


---

### Post by kevdog on 2007-08-06
Can you change your wpa_supplicant.conf file so that the following line appears like this

```
ssid = "linksys"
```

I think you are missing the quotes.


Let me know what happens.

---

### Post by init1 on 2007-08-06
> **kevdog said:**
> Can you change your wpa_supplicant.conf file so that the following line appears like this

```
ssid = "linksys"
```

I think you are missing the quotes.


Let me know what happens.
Thanks. I've changed it, but I'll need to test it later.

---

### Post by fatalbert on 2008-03-16
I can't believe this guy just left this open! the other guy was really trying to help! how did it end???

---

### Post by init1 on 2008-03-18
> **fatalbert said:**
> I can't believe this guy just left this open! the other guy was really trying to help! how did it end???
No worries, I don't even use Ubuntu anymore :D
I never got it working completely, but I guess I haven't really felt compelled to do so. Maybe I'll retrace those steps in my Etch install and see if I get it working from there.

---

