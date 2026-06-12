---
title: "I just want a wireless connection"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by jurgen32 on 2007-06-25
Hello there.
I'm making a laptop from a friend work with feisty.
Now i've got a prob. with the wireless speedtouch 121g usb connection.
I allready tried it with ndiswrapper (severall times) but without succes.
I'm stranded at the next command:
[I]terry@terry:~/Desktop/ST121g Setup/Driver$ sudo ndiswrapper -i BT4501G.inf
Password:
driver bt4501g is already installed
terry@terry:~/Desktop/ST121g Setup/Driver$ sudo ndiswrapper -l
bt4501g : driver installed
terry@terry:~/Desktop/ST121g Setup/Driver$[/I]
The last command (ndiswrapper -l ) should give me two outputs;
bt4501g : driver installed AND hardware present
But there is no hardware present??
I really don't have a clue what I did wrong.

I hope somebuddy can help me out.
Jurgen

---

### Post by lunarcloud on 2007-06-25
The version of ndiswrapper that comes with ubuntu has never worked for me. Get an up to date version and compile (pretty easy) from source.

uninstall ndiswrapper first.

[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=515643](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=515643)

unpack
go inside the folder in the command line
sudo make install

its annoying that ubuntu wouldnt use versions of ndiswrapper compatible to the current kernel, but as long as i have wireless i'm happy.

---

### Post by jurgen32 on 2007-06-25
Oke thanks for the repl.
I tried it like you said but for some reason it wil not install like it should.
I will paste some info:

ifconfig:
[I]eth0      Link encap:Ethernet  HWaddr 00:40:D0:66:7A:E4
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10638761 (10.1 MiB)  TX bytes:887092 (866.3 KiB)
          Interrupt:10 Base address:0xe300

eth0:avah Link encap:Ethernet  HWaddr 00:40:D0:66:7A:E4
          inet addr:169.254.9.111  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0xe300

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/I]

iwconfig
[I]lo        no wireless extensions.

eth0      no wireless extensions.
[/I]
lspci
[I]00:00.0 Host bridge: VIA Technologies, Inc. P/KN266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
[/I]
sudo dmesg | tail
Password:
[I][   37.836000] [drm] Initialized drm 1.1.0 20060810
[   37.848000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   37.852000] [drm] Initialized savage 2.4.1 20050313 on minor 0
[   37.852000] mtrr: base(0x92000000) is not aligned on a size(0x5000000) boundary
[   37.852000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   37.852000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[   37.852000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[   48.824000] eth0: no IPv6 routers present
[ 4969.600000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 4980.472000] eth0: no IPv6 routers present
[/I]

I hope somebudy can help me further.

---

### Post by kevdog on 2007-06-25
Since you are using a wireless USB device, I think you need to post

lsusb


rather than lspci.

---

### Post by jurgen32 on 2007-06-26
Yep you're right I forgot.
lsusb
[I]Bus 003 Device 003: ID 06b9:0120 Alcatel Telecom
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000[/I]

---

### Post by kevdog on 2007-06-26
Can we just check a few things before proceeding.

Can you post the following, I want to check the installation of ndiswrapper
ndiswrapper -v
ndiswrapper -l

Can you also tell me more about you wireless USB device.  I know the chipset of the device, does it have a brand name?

Please also post
lshw -C network

Hopefully we can get you up and running today!

---

### Post by jurgen32 on 2007-06-26
Oke thanks for your time. 

All I can find about teh device is this:

Thomson speedtouch 120g
wireless 802.11g USB client

Here are the results:

terry@terry:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586

terry@terry:~$ ndiswrapper -l
bt4501g : driver installed

terry@terry:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:d0:66:7a:e4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.2 ip=192.168.2.103 latency=32 maxlatency=8 mingnt=3 multicast=yes
       resources: ioport:e300-e3ff iomemory:f0000100-f00001ff irq:10

hope this wil help,
jurgen

---

### Post by kevdog on 2007-06-26
Ok, most of the information was helpful.  Im no expert on the subject, but I think your installation of ndiswrapper may not be right.  

> 
terry@terry:~$ ndiswrapper -v
utils Error: no version specified!
driver version: 1.38
vermagic: 2.6.20-16-generic SMP mod_unload 586


I think the big Error statement tells you this.  No one however has been able to confirm if to me if this matter or not.  To solve this problem, you need to backtrack. First uninstall your driver
sudo ndiswrapper -r *****  (put in driver name but do not type the extension .inf)
Then uninstall ndiswrapper -- you likely used Synaptic to install this, so use synaptic to uninstall.

The following is how we are going to install ndiswrapper from source.  If this computer does not have a working internet connection (ie a wired connection) then you are going to have to use another computer to help you.

If wired connection, at command line type
sudo aptitude install build-essential

If no wired connection but have installation cd, put cd in drive and type
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

Next visit the following site and download the ndiswrapper.tar.gz file (I think the version is 1.47)
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/)

Look for the download section.  This should give you a file named ndiswrapper-1.47.tar.gz.  Place this in your home directory.  You can either do this via command line or GUI using nautilis
Then lets unpack the tar file from command line:
cd ~
tar -zxvf ndisrapper-1.47.tar.gz
cd ndiswrapper -1.47
make distclean
make
sudo make install

Check now if you have the right version of ndiswrapper and everything is correct with this program
ndiswrapper -v
You should get no errors with this statement
Then rewrap driver like you did above
sudo ndiswrapper -i *****.inf <----substitute name of file here with .inf extension.  Make sure you have .inf and .sys file in the same directory where you are running this command.

Then load module into kernel
sudo modprobe -r ndiswrapper
sudo depmod -a
sudo modprobe -i ndiswrapper

And then make module load at runtime
sudo ndiswrapper -m

Ndiswrapper makes a default installation on wlan0.  This sometimes causes problems for some people because as a default their wirleless connection is setup on eth0, or eth1, etc.  We can fix this for you if need be.  

Some modifications may need to be done to your /etc/network/interfaces and /etc/iftab files also.

Please do the steps I listed above, and then report back.  When you report back please post the results of:
ifconfig
/etc/network/interfaces

Thanks.

---

### Post by jurgen32 on 2007-06-27
Aaaahhhh yeh!
I tried it over and over again and finaly I used a other driver (120g instead of 121g) and now it works fine.

But one problem is that my router seems to give a very strange ip adres.
It should be a number with 192.168.2.*** but he gives 169.254.8.157
Do you know how this comes or is this a new topic;-)
By the way.
On my own laptop I work with cardbus adapter and that works fine with feisty but also that strange ip adres.
With this strange adres I seem not to get internet acces.

If you also have a answer for this it would by great.
I'm allready very happy with this.
Thanks for your help!

Jurgen

---

### Post by kevdog on 2007-06-27
Are you sure you are connecting through your router and not someone else's???

What is the output of the following:
iwlist scan

---

### Post by jurgen32 on 2007-06-27
Allrighty than!!!!
Never mind the last problems.
I just had to activate wireless in knetworkmanager and everything went smoothly.
This man is very happy!

Again thank's for all the help.

Jurgen

---

### Post by jurgen32 on 2007-06-28
Yes you'r right.
It's the router from nextdoor. This is no problem because I can change my network in knetwork manager.
I was reading this whole topic and I find something stupid.
I started this topic with a question about the speedtoucht 12**1**g but I discoverd further in this topic that it should be 12**0**g.#-o
All the time I have been bucking other people with my problem but in the meanwhile I did not used my eyes:-\"
Still i'm happy because I learned a lot about networking and ndiswrapper.
So thank's Kevdog for your patience and help=D>

greetz,
Jurgen

---

### Post by SmartPC on 2007-07-08
Thanks kevdog,

This solved my problem as well with my WL usb stick [speedtouch 121G].
Now all is working fine.

regards,
Enrico

> **kevdog said:**
> Ok, most of the information was helpful.  Im no expert on the subject, but I think your installation of ndiswrapper may not be right.  



I think the big Error statement tells you this.  No one however has been able to confirm if to me if this matter or not.  To solve this problem, you need to backtrack. First uninstall your driver
sudo ndiswrapper -r *****  (put in driver name but do not type the extension .inf)
Then uninstall ndiswrapper -- you likely used Synaptic to install this, so use synaptic to uninstall.

The following is how we are going to install ndiswrapper from source.  If this computer does not have a working internet connection (ie a wired connection) then you are going to have to use another computer to help you.

If wired connection, at command line type
sudo aptitude install build-essential

If no wired connection but have installation cd, put cd in drive and type
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

Next visit the following site and download the ndiswrapper.tar.gz file (I think the version is 1.47)
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/)

Look for the download section.  This should give you a file named ndiswrapper-1.47.tar.gz.  Place this in your home directory.  You can either do this via command line or GUI using nautilis
Then lets unpack the tar file from command line:
cd ~
tar -zxvf ndisrapper-1.47.tar.gz
cd ndiswrapper -1.47
make distclean
make
sudo make install

Check now if you have the right version of ndiswrapper and everything is correct with this program
ndiswrapper -v
You should get no errors with this statement
Then rewrap driver like you did above
sudo ndiswrapper -i *****.inf <----substitute name of file here with .inf extension.  Make sure you have .inf and .sys file in the same directory where you are running this command.

Then load module into kernel
sudo modprobe -r ndiswrapper
sudo depmod -a
sudo modprobe -i ndiswrapper

And then make module load at runtime
sudo ndiswrapper -m

Ndiswrapper makes a default installation on wlan0.  This sometimes causes problems for some people because as a default their wirleless connection is setup on eth0, or eth1, etc.  We can fix this for you if need be.  

Some modifications may need to be done to your /etc/network/interfaces and /etc/iftab files also.

Please do the steps I listed above, and then report back.  When you report back please post the results of:
ifconfig
/etc/network/interfaces

Thanks.

---

### Post by fredj on 2007-07-09
The IP address being assigned is a default address that you get when DHCP isn't working.
Post the contents of your /etc/network/interfaces file.

---

### Post by wijbenga on 2007-07-11
I was very pleased to notice that someone succeeded in communication with the speedtouch 121g. I tried to follow the procedure, but got stuck halfway.

I am relatively new to ubuntu and creating programs by the make-procedure.

I followed all the steps until:
~/ndiswrapper-1.47$ make
make -C driver
make[1]: Map '/home/wijbenga/ndiswrapper-1.47/driver' wordt binnengegaan
Can't find kernel build files in /lib/modules/2.6.20-16-386/build;
  give the path to kernel build directory with 
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Fout 1
make[1]: Map '/home/wijbenga/ndiswrapper-1.47/driver' wordt verlaten
make: *** [all] Fout 2

Yes I am Dutch, so I have to translate it:
~/ndiswrapper-1.47$ make
make -C driver
make[1]: Map '/home/wijbenga/ndiswrapper-1.47/driver' is entered
Can't find kernel build files in /lib/modules/2.6.20-16-386/build;
  give the path to kernel build directory with 
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Map '/home/wijbenga/ndiswrapper-1.47/leaving driver' 
make: *** [all] Error 2

I suppose that I have te create my own kernel. Is that correct or is something else going wrong?

I would be grateful for any support as I had the speedtouch 121g running with Dapper, but after upgrading to Feisty I have to use cable connection, which is lying loose through the house, since 21 June.

---

### Post by kevdog on 2007-07-11
Im not sure -- but you might not have the header files installed.  Hopefully you have a wired connection.

Type this at the command line:

```
 sudo aptitude install linux-headers-$(uname -r)
```

---

### Post by wijbenga on 2007-07-11
Thank you for your answer. I (we) keep on tring

Well I got the headers, but

wijbenga@wijbenga:~/ndiswrapper-1.47$ make
make -C driver
make[1]: Map '/home/wijbenga/ndiswrapper-1.47/driver' entered
/bin/sh: cannot create crt_exports.h: Permission denied
make[1]: *** [crt_exports.h] Error 2
make[1]: Map '/home/wijbenga/ndiswrapper-1.47/leaving driver'
make: *** [all] Error 2

Suggestion for a next step?

---

### Post by wijbenga on 2007-07-11
I managed upto and including the "sudo make install"

testing the version:
$ ndiswrapper -v
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename:       /lib/modules/2.6.20-16-386/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-16-386 mod_unload 486 

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

Do I have to disgard the note "module version is too old!" ??
I downloaded 1.47, but it seems to be version 1.38

---

### Post by kevdog on 2007-07-11
I dont know -- keep going.  Just verify that it was truly 1.47 you downloaded.

---

### Post by wijbenga on 2007-07-12
Thanks for your attention. I tried to get the wireless up and running through wifi-radar, but after my request voor connection this tool reports: "Could nog get IP addres"

Here are mij ifconfig, iwconfig and interfaces.
After finishing the recipy above, the iwconfig came up with Medion, which is probably of one of the nabours. After the trying the connection through wifi-radar, the iwconfig showed the right ESSID.

I guess that I need some more configuration in interfaces and wpasupplicant, is not?
Anyway, your support is highly appreciated.
Kind regards

wijbenga@wijbenga:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:50:BF:E3:2B:38  

          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0

          inet6 addr: fe80::250:bfff:fee3:2b38/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:31 errors:0 dropped:0 overruns:0 frame:0

          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:4009 (3.9 KiB)  TX bytes:5212 (5.0 KiB)

          Interrupt:10 Base address:0x6000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)



wlan0     Link encap:Ethernet  HWaddr 00:12:BF:22:86:C5  

          inet6 addr: fe80::212:bfff:fe22:86c5/64 Scope:Link

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:398 (398.0 b)



wijbenga@wijbenga:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"SX551D8A61"

          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   

          Bit Rate=2 Mb/s   Tx-Power:18 dBm   

          RTS thr=2347 B   Fragment thr=2346 B   

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


auto lo

iface lo inet loopback



auto eth0

iface eth0 inet dhcp



auto eth1

iface eth1 inet dhcp



iface wlan0 inet static

address 192.168.2.2

netmask 255.255.255.0

gateway 192.168.2.1

wireless-essid SX551D8A612

wireless-key s:"my secret key, which is a WPA-key"

---

### Post by kevdog on 2007-07-12
You are trying to use WPA -- I see that from your secret key:

> iface wlan0 inet static

address 192.168.2.2

netmask 255.255.255.0

gateway 192.168.2.1

wireless-essid SX551D8A612

wireless-key s:"my secret key, which is a WPA-key"

Do the following:
1. Turn off WPA/WEP/Mac filtering for the time being (we will activate this later).  I just want to verify that we have basic connectivity.  Also while doing this can you substitue
```
auto wlan0 
iface wlan0 net dhcp

```
I know this is not what you want, but it will at least tell us if the basics work.  If you cannot use dhcp then change the above to:
```
auto wlan0 
iface wlan0 net static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid SX551D8A612
```

See if that works.

Adding WPA, although not hard, is a whole different animal that takes a few more steps than Ive described.  Please tell me if you can connect without WPA,  the line: > wireless-key s:"my secret key, which is a WPA-key" is only for WEP keys.

---

### Post by wijbenga on 2007-07-12
While using Dapper I had a dhcp connection with the speedtouch 121g, so I know that it works with dhcp and WPA.

It doesnot work without WPA, as I am using an Experia-box delivered bij the ADSL-provider and it only wokrs with WPA. XP can handle that and Dapper could also, although I have to admit that I also had a struggle then to get it up and running.

The fact that I was using a fixed IP-adress is one of those remaining I tried. Apparently I had not yet returned to using dhcp.

Its what I said before, my choices are:
- keep on trying to find a solution
- buy another usb wireless adapter that works out of the box.

I am the type of terrier, thus I have not yet given up

---

