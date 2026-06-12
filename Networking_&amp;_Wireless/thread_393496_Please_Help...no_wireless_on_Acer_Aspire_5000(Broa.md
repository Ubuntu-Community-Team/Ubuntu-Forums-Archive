---
title: "Please Help...no wireless on Acer Aspire 5000(Broadcom)"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by FNGtyler on 2007-03-25
i have followed every tutorial i can find everything works fine
until I get to this command:

root@laptop:/home/tyler# modprobe acer_acpi

FATAL: Error inserting acer_acpi (/lib/modules/2.6.17-10-generic/extra/acer_acpi.ko): No such device

I installed everything tried reininstalling still no luck, about to give up on linux
i installed ndiswrapper went fine
I attempted to install acer_acpi which is appearently needed no luck still.

---

### Post by FNGtyler on 2007-03-25
anyone?

---

### Post by Floppyjoe on 2007-03-25
> **FNGtyler said:**
> i have followed every tutorial i can find everything works fine
until I get to this command:

root@laptop:/home/tyler# modprobe acer_acpi

FATAL: Error inserting acer_acpi (/lib/modules/2.6.17-10-generic/extra/acer_acpi.ko): No such device

I installed everything tried reininstalling still no luck, about to give up on linux
i installed ndiswrapper went fine
I attempted to install acer_acpi which is appearently needed no luck still.

possibly try:
```
 sudo modprobe acer_acpi

```

---

### Post by FNGtyler on 2007-03-26
im in the root drive i don't believe that will make any difference.
either way I have tried that still the same response.

---

### Post by Floppyjoe on 2007-03-26
What is your wireless card?
Can you post the result of:
```
lspci
```

---

### Post by FNGtyler on 2007-03-26
It is a broadcom

---

### Post by Floppyjoe on 2007-03-26
> **FNGtyler said:**
> It is a broadcom

Which version of Broadcom?

---

### Post by FNGtyler on 2007-03-26
ok...update i just installed a fresh version of ubunto 6.06 64bit version
then only modification i have done so far is to edit the blacklist

blacklist ipv6 

to allow me to get on the internet via ethernet.

Here is a copy of my lspci:
tyler@tyler-laptop:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter

BTW it is a Broadcom 4318 in a Acer Aspire 5000

Thanks in advance
FNG

---

### Post by Floppyjoe on 2007-03-26
> Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
This is your Broadcom card. There is a link in my signature that has a tutorial to get those cards to work. If you have already tried a bunch of tutorials make sure you blacklisted the native broadcom driver. bcm43xx

---

### Post by FNGtyler on 2007-03-26
i am very new to linux

shoud i add to
/etc/modprobe.d/blacklist

Code:
blacklist bcm43xx

---

### Post by Floppyjoe on 2007-03-26
> **FNGtyler said:**
> i am very new to linux

shoud i add to
/etc/modprobe.d/blacklist

Code:
blacklist bcm43xx

Yes.

---

### Post by FNGtyler on 2007-03-27
alright following your how to for some reason when i try running ndiswrapper
is says:

tyler@tyler-laptop:~$ sudo ndiswrapper
Error: no versions of ndiswrapper found!
tyler@tyler-laptop:~$ sudo ndiswrapper -l
Error: no versions of ndiswrapper found!
tyler@tyler-laptop:~$

not sure why i triple checked
it says it is installed.
I rebooted
tried reinstalled
made sure i was in root

any ideas?

---

### Post by Floppyjoe on 2007-03-27
> **FNGtyler said:**
> alright following your how to for some reason when i try running ndiswrapper
is says:

tyler@tyler-laptop:~$ sudo ndiswrapper
Error: no versions of ndiswrapper found!
tyler@tyler-laptop:~$ sudo ndiswrapper -l
Error: no versions of ndiswrapper found!
tyler@tyler-laptop:~$

not sure why i triple checked
it says it is installed.
I rebooted
tried reinstalled
made sure i was in root

any ideas?

did you install "ndiswrapper-common" and "ndiswrapper-utils-1.8"

---

### Post by FNGtyler on 2007-03-27
yes i found ndiswrapper 1.8 in synaptic then i searched google for ndiswrapper-common and found it at ubuntu downloaded it and it says it is installed in synaptic.

not sure why it worked fine in ubuntu 6.10

---

### Post by Floppyjoe on 2007-03-27
> **FNGtyler said:**
> yes i found ndiswrapper 1.8 in synaptic then i searched google for ndiswrapper-common and found it at ubuntu downloaded it and it says it is installed in synaptic.

not sure why it worked fine in ubuntu 6.10

Did you also install it after you downloaded it?
What is the output of :
```
ndiswrapper -v
```
It should say something like this if it is installed.
> utils version: 1.9
driver version:        1.22
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1


---

### Post by FNGtyler on 2007-03-27
still says same thing no version installed

---

### Post by Floppyjoe on 2007-03-27
Try issuing the following commands at the terminal.
```
sudo apt-get install ndiswrapper-utils-1.8
```
and
```
sudo apt-get install ndiswrapper-common
```

---

### Post by FNGtyler on 2007-03-27
tyler@tyler-laptop:~$ sudo apt-get install ndiswrapper-utils-1.8
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndiswrapper-utils-1.8
tyler@tyler-laptop:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree... Done
ndiswrapper-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 116 not upgraded.
tyler@tyler-laptop:~$


here is the response

---

### Post by Floppyjoe on 2007-03-27
> **FNGtyler said:**
> tyler@tyler-laptop:~$ sudo apt-get install ndiswrapper-utils-1.8
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndiswrapper-utils-1.8
tyler@tyler-laptop:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree... Done
ndiswrapper-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 116 not upgraded.
tyler@tyler-laptop:~$


here is the response
Are you connected to the internet with a network cable using Linux?
If yes then maybe you need to go into System/Administration/Synaptic Package Manager. Then click on settings/repositories and make sure all the boxes in the Ubuntu 6.10 tab are checked off. If you are not using Edgy 6.10 then make sure all your repositories are enabled and try the following again.
```
sudo apt-get install ndiswrapper-utils-1.8
```

---

### Post by FNGtyler on 2007-03-28
i am actually using ubuntu 6.06

I still tried unchecking all the boxes, and there is no change.(still get same message)
should I possibly try reinstalling with ubuntu 6.10
I am connected through ethernet currently. and sending this email from linux

---

### Post by Floppyjoe on 2007-03-28
> **FNGtyler said:**
> i am actually using ubuntu 6.06

I still tried unchecking all the boxes, and there is no change.(still get same message)
should I possibly try reinstalling with ubuntu 6.10
I am connected through ethernet currently. and sending this email from linux

All the boxes should be checked.

---

### Post by FNGtyler on 2007-03-28
i rechecked them, still same ****, does it make a difference that i am using the 64bit version?

---

### Post by Floppyjoe on 2007-03-28
> **FNGtyler said:**
> i rechecked them, still same ****, does it make a difference that i am using the 64bit version?
It makes a difference in which drivers you use with ndiswrapper yes.
But if you can't install ndiswrapper then that won't make any difference.
From the output of one of your previous posts its obvious that ndiswrapper-utils-1.8 is not installed on your computer.
If you can't install it from the internet with synaptic then perhaps try to install it from the Ubuntu Install Disk.

---

### Post by FNGtyler on 2007-03-28
well no sure what is going on just did another fresh install with ubuntu 6.10 gonna retry

---

### Post by Camaxtli on 2007-03-28
I had the same problem with this wireless card on Edgy, and this is how I solved it:

First off, uninstall the old driver and stop the module in case it's running:
```
sudo ndiswrapper -r bcmwl5
sudo rmmod ndiswrapper
```

Now uninstall (Preferably purge) all instances of ndiswrapper.

Then do the following three steps:
- Download the latest source of Ndiswrapper from [http://ndiswrapper.sf.net](http://ndiswrapper.sf.net)
- Untar it to something like ~/wireless
- Download the 64bit drivers from [http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5)

Now install the build-essential package:
```
apt-get install build-essential
```

When that's finished go ~/wireless or where ever you decided to untar the ndiswrapper source to and run (This shouldn't give errors):
```
sudo make uninstall
sudo make distclean
make
sudo make install[/quote]

Now the module is compiled and installed it's time to install the driver:
[code]sudo ndiswrapper -i /path/to/the/driver.inf
ndiswrapper -i
```

This should yield something like:
```
camaxtli@hermes:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
camaxtli@hermes:~$
```

Now that's done, it's time to blacklist the bcm43xx driver (If this line doesn't work, just add it manually) and in case it's still running remove the module:
```
echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
```

Last steps:
```
sudo ndiswrapper -m
echo "ndiswrapper" | sudo tee -a /etc/modules
sudo modprobe ndiswrapper
```

Now run iwconfig and the wireless card should be working. I recommend using NetworkManager to manage the connection.

---

### Post by FNGtyler on 2007-03-28
well so far I just did a fresh install of edgy, everything went good i followed floppyjoe's howto
no errors, but also no wireless internet
here is the report from my:
lspci and iwconfig

tyler@tyler-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tyler@tyler-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter
tyler@tyler-laptop:~$ 

I had a blinky light for awhile now no blinky light

---

### Post by FNGtyler on 2007-03-28
I read in a couple of threads that i must run acer_acpi......Is this true?
I am very new to linux, sorry for all the stupid questions...but im gonna do whatever it takes to get rid if windows

---

### Post by Camaxtli on 2007-03-28
> **FNGtyler said:**
> well so far I just did a fresh install of edgy, everything went good i followed floppyjoe's howto
no errors, but also no wireless internet
here is the report from my:
lspci and iwconfig

tyler@tyler-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Your wireless card is configured as eth1, just use networkmanager to create a connection to your wireless network.

---

### Post by FNGtyler on 2007-03-28
not sure how to use network manager. I just went to synaptic and downloaded network manager and installed it.

how do I use it?

Are you also using an acer?

---

### Post by Floppyjoe on 2007-03-28
I do have an Acer(32bit) with the Broadcom 4318 card. If you are using Network-Manager you need to disable all your network interfaces in System/Administration/Networking for it to work properly. I have a button/light on the front of my laptop that activates my wireless card. I have to be careful not to hit this button when I am using it because then it will turn it off and I will wonder why I can't get the wireless to work.

I did not have to use the acer_acpi bit to get it working.

---

### Post by FNGtyler on 2007-03-29
i did another fresh install followed floppyjoe's tutorial, I know have a blinky light, that i can turn off or on by pressing the button no errors at all during install. but for some reason still no internet here is a copy of my iwconfig? any ideas?

tyler@tyler-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Floppyjoe on 2007-03-29
What happens When you issue the following?:
```
sudo iwlist eth1 scan
```
If you are not using Network-Manager-Gnome then you need to add some information about your wireless access point into /etc/network/interfaces.

This is what my file looks like when i issue:
```
sudo gedit /etc/network/interfaces
```
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto rausb0
iface rausb0 inet dhcp
wireless-essid WarGames
wireless-channel 7
wireless-mode managed
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

The stuff under the rausb0 is my wireless-access point information plus my WPA information.

---

### Post by FNGtyler on 2007-03-29
eth1      Scan completed :
          Cell 01 - Address: 00:0F:B3:37:46:69
                    ESSID:"ACTIONTEC"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-46 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
          Cell 02 - Address: 00:0C:41:A2:38:ED
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-89 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

I turned wep off for now for testing, what else would i need to do. is it a good idea to run network manager or any other programs?

---

### Post by Floppyjoe on 2007-03-29
I use Network-Manager on my Acer Aspire Laptop. To use it you have to disable all your network interfaces in System/Administration/Networking to let Network-Manager take over those functions.

---

### Post by FNGtyler on 2007-03-29
what would it take to install it? do i just go to synaptic download and install it?

then how do i set it up and how do i use it?

Also do I just uncheck the box under system/admin/networking (for the wireless device)

---

### Post by Floppyjoe on 2007-03-29
> **FNGtyler said:**
> what would it take to install it? do i just go to synaptic download and install it?

then how do i set it up and how do i use it?

Also do I just uncheck the box under system/admin/networking (for the wireless device)
I think you just install network-manager and network-manager-gnome via synaptic
There is not much set-up you just click on the Icon in the top menu bar that looks like power bars and it will show you the available networks. you just click on the one you want to connect to and add any necessary info.

Yes uncheck the box in System/Admin/networking.

---

### Post by FNGtyler on 2007-03-29
ya thats wierd i dont see any change when I installed it? no bars..I am getting so damn close finally after a weak.  Maybe I will try installing it through the terminal..What would I need to type to do that. Thanks again for all your help

---

### Post by Floppyjoe on 2007-03-29
> **FNGtyler said:**
> ya thats wierd i dont see any change when I installed it? no bars..I am getting so damn close finally after a weak.  Maybe I will try installing it through the terminal..What would I need to type to do that. Thanks again for all your help
You have to remember to deactivate all your network adapters in System/Administration/Networking, even the wired ethernet one. It will try to connect you to the ethernet first so unplug that cable first.

---

### Post by FNGtyler on 2007-03-29
alright i disabled all connections in admin/networking

rebooted still no little bar thing in upper right hand corner, and cannot connect to internet.

I do however have a solid light now. Got to be getting close

---

### Post by Floppyjoe on 2007-03-29
Can you post your /etc/network/interfaces file?
```
sudo gedit /etc/network/interfaces
```
sometimes you need to comment out all but the lo(loopback) interface lines by putting a # in front of the lines in that file.

---

### Post by FNGtyler on 2007-03-29
auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






auto eth0

---

### Post by Floppyjoe on 2007-03-29
The solution on this link may work for you it worked for me.

[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=4](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=4)

---

### Post by FNGtyler on 2007-03-29
Nevermind, I figured it out IT WORKS!!!!
You are friggin awesome. Thanks for all your help!!!!
I didn`t have all of network manager installed.

I can't thank you enough! Good bye Windows

---

### Post by Floppyjoe on 2007-03-29
> **FNGtyler said:**
> Nevermind, I figured it out IT WORKS!!!!
You are friggin awesome. Thanks for all your help!!!!
I didn`t have all of network manager installed.

I can't thank you enough! Good bye Windows

Welcome to the wonderful world of Linux!

---

