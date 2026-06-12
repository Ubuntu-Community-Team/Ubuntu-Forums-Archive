---
title: "[SOLVED] no wireless internet - can't ping router?"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by aella on 2007-07-22
I'm at my wit's end.  I've searched the forums, wiki, google, etc..endlessly for a week trying to resolve seemingly simple Fiesty issues (installation, booting, vga..etc..)  but this wireless issue is gonna drive me crazy.  I am, of course, new to Linux..so even trying to figure out what the heck grub, terminal, sudo..etc was a challenge.  :P

Anyway, I need help.  [-o<
I'm on an HP Pavilion dv6000
AMD Turion64
nvidia graphics (restricted drivers won't load at this point but that's a side issue)
broadcom 802.11b/g wlan mini
dual boot Vista/Ubuntu (32 bit)


I got the broadcom to work using bcm43xx-fwcutter (or at least I think I did, unless it was working all along and i didn't know it.)  I had originally tried ndiswrapper but made a mess and reinstalled Fiesty completely since I had no clue how to undo everything i'd tried.  Once loaded, fwcutter was the first thing and only thing I did (in terms of drivers for card i mean.)

So the thing is i can now scan and pick up the wireless networks around me, I can connect to my own wireless network (which has WPA2 on it btw).  The network manager in the corner says I'm connected to my network with a good signal but I can't access the internet.  I followed as many of the tips as I could that I found around the forums but i'm stuck.  Right now, what I know is when I try to ping the router i get no response.  4 packets sent and zero received back.

Oh and at one point I had no resolv.conf ...erm...file?  I used 'sudo touch' to create one?   :confused:

I know you probably need more info so if someone could just let me know what I need to provide (and how i access that info)  i'll be happy to do so.  Bear with me, a lot of this is WAY over my head.

---

### Post by kevdog on 2007-07-22
Can you post the following:

lshw -C network
ifconfig
lspcii -nn
iwlist scan

Thanks

---

### Post by aella on 2007-07-22
```
*-network               
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:15:51:9b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=0 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:b3200000-b3203fff irq:19
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:16:36:DF:AB:0C  
          inet addr:192.168.0.138  Bcast:192.168.3.255  Mask:255.255.252.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:1A:73:15:51:9B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:11 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:246 (246.0 b)  TX bytes:3635 (3.5 KiB)
          Interrupt:255 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:804 (804.0 b)  TX bytes:804 (804.0 b)
```

lspciii -nn :confused:
```
munki@rawkin-lappy:~$ lspcii -nn
bash: lspcii: command not found

```

I also tried lspcii-nn (same thing) and then.. lspci -nn 
```
munki@rawkin-lappy:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 PCI Express Bridge [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 01)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Unknown device [1180:0832]
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:0843] (rev 01)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

```


iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
```

---

### Post by aella on 2007-07-23
nothing?  no ideas?  point in the right direction?  :(

---

### Post by kevdog on 2007-07-23
Im really kind of confused, but bottom line is that I dont think your wirless is working.

lshw -C network
This told me your wireless interface was eth1 and the driver bcm43xx

eth0 - probably your wired card lists an internet address of:
192.168.0.138 -- This may or may not be right.  In fact are you using a wired connection??

eth1 - no internet address

iwlist scan
This command scans wireless networks in the area.
eth1      No scan results

This tells me that its not finding your router.

I think you are kind of back to square one -- basically a driver install issue.  What forum or link did you use to install the bcm43xx driver??

---

### Post by Ayuthia on 2007-07-23
Have you tried to turn off the WPA to see if you can just connect?  Also, have you tried using dhclient eth1 to see if you can connect?  If you have eth0 running at the time, you should try disconnect eth0 and do a 'sudo killall dhclient' and try to reconnect.  Sometimes if you are connected via a wired connection and then try to connect via wireless, you can have some problems.

---

### Post by aella on 2007-07-23
I used this forum for tips on the fwcutter. After reading through a ton of posts I think I just used bits of info from here and there.. and i downloaded fwcutter and bcm firmware from links in this post: [http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm43xx-fwcutter]("http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm43xx-fwcutter")

After I reinstalled fiesty I tried using a wired connection but I still couldn't access the internet.  I keep having to transfer things via flashdrive 'cause things like 'sudo apt-get' just don't work.  

as for the ip, i set a static ip (since i use for vista connection) and may have forgotten to remove it which is probably why it's showing up.   :T

should i reinstall the drivers?  I did try using the fluffy-ndiswrapper installation once but i couldn't get cabextract working and when i finally got the driver installed (the one mentioned in the tutorial) it said it was the incorrect driver...  :/

---

### Post by kevdog on 2007-07-23
If you have the windows xp driver, or the cd or zip file where they are located, why dont you just extract the file on a windows machine, go into the windows xp folder, copy and paste the *.sys *.inf and possibly *.bin files to your USB drive and bring them over to Ubuntu that way??

Can you do this??

If you can do this let me know, then we will proceed.

---

### Post by jml on 2007-07-23
aella, you mentioned that you could not connect to the internet with the wired connection either.  Are you sure that your router/access point actually works?  If you have access to another computer, try connecting with it.  If it does not work, then at least part of the problem is that hardware.

Joe

---

### Post by aella on 2007-07-23
i saw that suggestion on another post (importing drivers from vista to ubuntu) but i'm not sure how to actually get them functioning in fiesty?  i'll research how and post back.

oh and the router works.  i'm on wireless in vista (how i'm able to post here) and there are two other windows computers wired to it as well that work.

---

### Post by kevdog on 2007-07-23
If you can get the drivers over, then ndiswrapper is the way we are going to try.  Ill give you the guide below, I want you to read through the guide about 3 times before beginning.  It requires that you compile some files from source.

I think with your card it should be no problem
Here is the guide, if you have any reservations let me know!

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
I cant remember the exact output but make sure you dont get any errors.

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

### Post by aella on 2007-07-23
Ok!  I did all the above and pulled it off without a hitch! no errors and verified per your instructions along the way.    :)  What's the next step?

---

### Post by kevdog on 2007-07-23
Usually at this step people usually tell me "hey everything is working", or "nothing is working --- I'm getting this error).

I guess the next step for you would be to do the following and post the output:
lshw -C network
ndiswrapper -l
ndiswrapper -v
ifconfig
iwlist scan

Also post the following files:
/etc/network/interfaces
/etc/iftab

Your using ubuntu, and I think gnome network manager (network-manager-gnome) is installed by default.

---

### Post by aella on 2007-07-24
It worked!!  It hadn't at first but did upon second boot for some reason.  Excruciatingly slow...but it works! :D   Posting from Ubuntu = yaay!   I did have to disable WPA2 and MAC filter so should i just follow the instructions on the WPA Security sticky?

Here's the info requested..
```
*-network               
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:15:51:9b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic ip=192.168.0.199 latency=0 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:b3200000-b3203fff irq:19


munki@rawkin-lappy:~$ ndiswrapper -l
bcmwl6 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)



munki@rawkin-lappy:~$ ndiswrapper -v
modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net



munki@rawkin-lappy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:DF:AB:0C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:1A:73:15:51:9B  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe15:519b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:491 errors:0 dropped:31 overruns:0 frame:0
          TX packets:583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:614122 (599.7 KiB)  TX bytes:48183 (47.0 KiB)
          Interrupt:255 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:16:36:DF:AB:0C  
          inet addr:169.254.6.8  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:258 (258.0 b)  TX bytes:258 (258.0 b)

munki@rawkin-lappy:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:19:5B:4A:FE:ED
                    ESSID:"dlink"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=94/100  Signal level=-54 dBm  Noise level=-65 dBm
                    Extra: Last beacon: 40ms ago
          Cell 02 - Address: 00:0F:3D:07:32:51
                    ESSID:"BeMo"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=86/100  Signal level=-71 dBm  Noise level=-65 dBm
                    Extra: Last beacon: 76ms ago
          Cell 03 - Address: 00:11:50:2A:62:5F
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=80/100  Signal level=-79 dBm  Noise level=-65 dBm
                    Extra: Last beacon: 204ms ago
```

interfaces:
```
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp
address 192.168.0.138
netmask 255.255.252.0
gateway 192.168.0.1



auto eth0
```

iftab
```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:36:df:ab:0c arp 1
eth1 mac 00:1a:73:15:51:9b arp 1
```

---

### Post by kevdog on 2007-07-24
A few suggestions -- fine tunning is what I call it!!

Can you post your /etc/modprobe.d/ndiswrapper file??


Lastly, the sticky for WPA security is great -- particularly if you want to run a static IP.  This method however has some disadvantages for laptops, in that it sets up an interface that must be changed if you encounter a different router or wireless signal other than your "home" router.

If your not requiring a static IP, have a laptop, and expect to connect to different networks from time to time, I would suggest a different approach.

Remember your wireless interface as setup is eth1. First back up your old copy of your interfaces file:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.original
```
Then proceed to make the modifications as suggested.

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by aella on 2007-07-24
etc/modprobe.d/ndiswrapper:
alias wlan0 ndiswrapper

I'm going to do that back up and check out the wpa link you suggested.  ^__^  i'll post back!  you've been so much help - i'm so grateful!!

---

### Post by kevdog on 2007-07-24
Try this 

gksu gedit /etc/modprobe.d/ndiswrapper

Change wlan0 to eth1

This will associate you wireless interface eth1 with ndiswrapper.

---

### Post by aella on 2007-07-24
should i do that even if i'm connected and WPA is working??

it's working!  i'm so happy!

THANKS SO MUCH FOR ALL YOUR HELP!!  <3

---

### Post by kevdog on 2007-07-24
You can try it!, you can always change it back if it doesnt work.

---

