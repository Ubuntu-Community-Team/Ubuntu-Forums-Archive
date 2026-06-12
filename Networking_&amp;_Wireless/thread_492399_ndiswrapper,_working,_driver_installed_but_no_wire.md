---
title: "ndiswrapper, working, driver installed but no wireless connection in network manager"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by S15_88 on 2007-07-04
Hi there i have successfully installed ndiswrapper with ease, loaded the driver with ease, added ndiswrapper to the boot modules but i still do not have a wireless connection in the network settings and no wifi light!  this has me quite puzzled and would appreciate any input from anyone with regard to this matter.  Look forward to getting my wireless working, putting me one step closer to eliminating my windows dual boot and having a pure linux machine!

I have included output and the version of ndiswrapper i am using, hope it's helpful!

Thanks in advance, Alain

the card is an intel next-gen: 4965AGN

here's some output:

alain@S15:~$ ndiswrapper -l
netw4v32 : driver installed
        device (8086:4229) present
alain@S15:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586

---

### Post by #Reistlehr- on 2007-07-04
sudo depmod -a
sudo modprobe ndiswrapper  

see if it is there now.

---

### Post by limbourg31 on 2007-07-04
if the card isn't active try to activate it through the networking manager... see if setting it up on roaming mode or something manages to get you a signal, otherwise you're having the problem where the card is recongized but can't be activated, and then you will have to post the lspci stuff. it is a pci card right?

---

### Post by S15_88 on 2007-07-04
those two lines i presume did nothing as this is what happened in the terminal:

alain@S15:~$ sudo depmod -a
alain@S15:~$ sudo modprobe ndiswrapper 
alain@S15:~$ 

it should've prompted me for my password correct?  i tried pressing the wireless shortcut key, my bluetooth goes on and off but no wireless?

as for limbourg31 here is the output for lspci:

> 
alain@S15:~$ sudo update-pciids
--17:32:38--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 121,276 (118K) [text/plain]

100%[====================================>] 121,276      153.19K/s             

17:32:39 (152.97 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [121276/121276]

Done.
alain@S15:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
alain@S15:~$ 


---

### Post by Jouke74 on 2007-07-04
See if you can use "Network" under the Administration (without WPA but WEP) instead. I had the same problem, Ndiswrapper installed fine, but the Gnome-network-manager failed to connect  to my router under any conditions. Sudo apt-get remove gnome-network-manager and setting all details by hand using "Network" instead solved that for me.

Somehow the communication between Network-manager > Ndiswrapper > drivers is not holding.

---

### Post by S15_88 on 2007-07-04
under network>administration there is no wireless jus wired and modem.  now i'm starting to get a little confused haha oh boy!  i know how to set the card to roaming mode, i know wat WPA and WEP are but how do i do all this if there is no wireless???? 

Thanks, Alain

---

### Post by limbourg31 on 2007-07-04
well the card is definetly seen...  i would guess that its just no being activated or no signal is available... there was a major problem with rt61 cards in edgy

with sudo, if already used, it would not ask for the password

---

### Post by S15_88 on 2007-07-04
well i'm off to grab all u can eat sushi!  thanks for all the help so far and feel free to post any other suggestions you have!  

Thanks, Alain

---

### Post by #Reistlehr- on 2007-07-04
do an ifconfig and post what it says, and an iwconfig

do you have gnome network manager installed?  

if not, try these..

Edit the following file, and comment out (put a "#" in front of) all lines that don't reference the "lo" interface. (N.B. there are two lines, probably at the top, which do reference the "lo" interface. Again, leave these two alone, uncommented.)
```
gksudo gedit /etc/network/interfaces
```
```
sudo apt-get install network-manager-gnome
```
```
sudo /etc/init.d/dbus restart
```

---

### Post by kevdog on 2007-07-04
I skimmed through the post, but missed something (I wish I was eating sushi).

Anyway I missed a few details.  Can you tell me what type of networking card or Usb device you are trying to work with.  If it contains an rt61 chipset, I personally wouldnt recommend ndiswrapper.  

Also if you could post the following it would help for troubleshooting

lshw -C network

Thanks

---

### Post by S15_88 on 2007-07-04
for #Reistlehr- here is your if and ip config:

> 
alain@S15:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:7A:3C:13  
          inet6 addr: fe80::215:c5ff:fe7a:3c13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:615 errors:0 dropped:0 overruns:0 frame:0
          TX packets:516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:620209 (605.6 KiB)  TX bytes:67237 (65.6 KiB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:67.70.60.50  P-t-P:64.230.197.229  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2100 (2.0 KiB)  TX bytes:1202 (1.1 KiB)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:67.70.61.250  P-t-P:64.230.197.229  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:590049 (576.2 KiB)  TX bytes:50909 (49.7 KiB)

alain@S15:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

ppp1      no wireless extensions.


Here is your output Kevdog:  

The card is an intel PRO/Wireless 4965AGN; and lshw -C network returned:

> 
alain@S15:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:efdfe000-efdfffff irq:4
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:7a:3c:13
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 multicast=yes
       resources: iomemory:ef9fe000-ef9fffff irq:17


Again thanks everyone for all the feedback and i look forward to getting my wireless up and running! 

Thanks, Alain

---

### Post by kevdog on 2007-07-05
There is no driver assigned to wireless card if I am interpreting your output.  Look at the results of lshw command. 

In the first listed device - network Unclaimed there is no driver listed.  
As a comparison look at the second device, you see it states driver=b44.  Its also assigned the eth0 interface

Lets just check a few things about the ndiswrapper installation first
ndiswrapper -v
ndiswrapper -l

Where did you get the driver for your wireless card?
Also you can not have wired and wireless running simaltaneously.  In fact to change between the two requires a reboot.

Also can you post the following
/etc/network/interfaces
/etc/iftab
sudo modprobe -l | grep ndiswrapper
/etc/modprobe.d/blacklist

Also if you could do the following.  Take a look at the boot log, by issuing dmesg | more.  I dont want you to post the whole log.  Is there any section you find about ndiswrapper??

---

### Post by S15_88 on 2007-07-05
yes i noticed that aswell that it's unclaimed.  So let's see if we can get that claimed haha  

I got my drivers from the intel website:
> 
 [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2753&OSFullName=Windows+Vista*+Home+Premium%2C+32-bit+version&lang=eng&strOSs=153&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2753&OSFullName=Windows+Vista*+Home+Premium%2C+32-bit+version&lang=eng&strOSs=153&submit=Go%21)


As soon as i get home from work, a few hours from now, i''ll post the output, my company supplies us with notebooks to use at the office so i don't usually bring my personal one to work with me.

Thanks, Alain

---

### Post by S15_88 on 2007-07-05
So here we go lots of code and there are a few things i noticed.

here is ndiswrapper -v, ndiswrapper -l
> 
alain@S15:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 

alain@S15:~$ ndiswrapper -l
netw4v32 : driver installed
        device (8086:4229) present


pretty sure that's the latest version and the driver is installed. all good so far.

here is /etc/network/interfaces
> 
auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0

iface eth0 inet manual


now /etc/iftab
> 
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:15:c5:7a:3c:13 arp 1


Now sudo modprobe -l | grep ndiswrapper
> 
/lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
[/]QUOTE

Now /etc/modprobe.d/blacklist
[QUOTE]

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187


Now this is where it gets scary, dmesg | more, i found the ndiswrapper unfortunitely. i included a part afterwords aswell as it said driver installed but no device present, it's in yellow text.
> 

[   17.440000] ndiswrapper version 1.47 loaded (smp=yes)
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregist
erMiniportDriver'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfi
gurationEx'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMinip
ortAttributes'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegister
MiniportDriver'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWor
kItem'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegister
InterruptEx'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx
'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGLi
st'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterr
uptEx'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsCom
plete'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   17.716000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   17.716000] ndiswrapper (load_sys_files:216): couldn't prepare driver 'netw4v32'
[   17.716000] ndiswrapper (load_wrap_driver:118): couldn't load driver netw4v32; check system log for mess
ages from 'loadndisdriver'
[   17.720000] usbcore: registered new interface driver ndiswrapper
[   17.824000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   17.824000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.044000] hda_intel: azx_get_response timeout, switching to polling mode...
[   19.952000] fuse init (API version 7.8)
[   20.024000] lp: [COLOR="Yellow"]driver loaded but no devices found[/COLOR]


so that was fun!  now i sit asking myself what now?  it seems i have a few problems? where do i start? should i abandon ndiswrapper and go for the iwlwifi way?  i felt like i was so close to getting it working but as soon as one thing went well i found something else that set me back!  soo close but yet sooooo far haha alrighty i appreciate everyones efforts any comments regarding further steps would be great!

Thanks, Alain

---

### Post by #Reistlehr- on 2007-07-05
do you have network-manager-gnome installed? if so, comment everything but the strings referencing the lo (loopback), in /etc/network/interfaces

/etc/init.d/dbus restart

see how taht works

Gonna brainstorm some more idea's for you. I fixed my problem. Had to uncomment and comment some things, which by your posted outputs, is a slightly different problem.

---

### Post by S15_88 on 2007-07-05
yes i have network-manager-gnome installed according to add/remove but to be honest i don't know where to find it, it's not under internet, silly question but is network-manager-gnome the same as administration>network?? I went in /etc/network/interfaces and commented the lines but it wouldn't let me save it, said i do not have permission?  I feel like a total noob haha 

thanks, Alain

---

### Post by kevdog on 2007-07-05
Possibly someone else could lend you a hand -- definitely looks like a bad driver from the dmesg file.  Do you know of any alternatives such as a win2000 or win98 driver you could try??  Is this the winxp driver that you linked to?? I didnt check the link.

---

### Post by S15_88 on 2007-07-05
vista home premium, my plan was once i got the wireless figured out there would be no more need for windoze, i hardly venture into vista except when i am in need of wireless.

---

### Post by #Reistlehr- on 2007-07-05
ok type this:
```
gksudo gedit /etc/network/interfaces
```

youll be asked for your root password, enter it, and a thing will pop up. 

network-manager-gnome is actually the computer icons (one-ontop-of-another) near the system clock. for you it will probably have a orange icon on it somewhere or something.

after you do those comments, restart, and try.

(i make a lot of typo's so double check)

---

### Post by kevdog on 2007-07-05
I could be wrong but I dont think vista drivers work with ndiswrapper.  Either get the Winxp drivers from the install disk, or visit the manufactures website to download the xp drivers.

---

### Post by dnathe4th on 2007-07-05
i had vista drivers work
once
until i restarted and the settings dissapeared

---

### Post by fredj on 2007-07-06
Kevdog is right. Get the windows XP driver. Ndiswrapper is unlikely to work with a Vista driver.

---

### Post by Jouke74 on 2007-07-06
To help you still a bit:

The NDISwrapper homepage has a good list of wireless hardware that it supports (or not). Also there it is said which driver is working in combination with your hardware: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

In any case your Ndiswrapper needs to work correctly before you can configure your wireless interface in Ubuntu.


Afterwards you have three options. 

1 / One is to use the still somewhat buggy gnome-network-manager. This has the advantage that you can switch accesspoints and look for networks around. The disadvantage is that is is still a bit buggy (did not want to connect with my card) and you need to type your password for the keyring manager every reboot (without hack). If it does support WPA.

Behind the scenes your /etc/network/interfaces file needs to be deconfigured. So the Gnome-network-manager applet can use it's own config. Hence thers should be no config info for any of the connections eg: 

auto ath0 
iface ath0 inet dhcp


2 / Going to Administration > network. Here you can click on wlan0 (if Ndiswrapper is working correct) and than go to properties. Now you need to type your Acces ID point (name of your network), which encryption you use (WEP tekst / hex / None) and accordingly your password, finally set your connection mode to DHCP for getting an IP address or enter a static IP address. If you enable your card this way, it won't be working with Gnome-network-manager anymore, it's either one or the other. Behind the scenes this program writes your card configuration to the /etc/network/interfaces file. It will like like this for a given interface:

auto ath0
iface ath0 inet dhcp
wireless-essid WANADOO-3EB4
wireless-key 962341B24DAF56AD0966AB5B38

The advantage here is that once it is configured you don't need to type a password anymore for your network when you boot. Disadvantage is that there is no direct WPA configuration.

3/ Manually adjust your /etc/network/interfaces file and don't use any program to do it for you. Problem, that takes some time getting into the material / text that is required to make it running.

---

### Post by S15_88 on 2007-07-06
ok just to give everybody an update i downloaded the XP drivers, but i'm going out of town for the weekend with some friends so i'm going to bring my laptop and tinker with it then i'll report back on monday if i was successful!  Again thank you everybody for all your input and i'll be sure to let everyone know if i get it alll working!!

what i'm going to do is:
install the XP driver
comment everything NOT referencing io in etc/network/interfaces
then do a /etc/init.d/dbus restart
then sudo reboot

if that doesn't work, which i'm hoping doesn't happen haha then i'll do:
lshw -C network and see if everything is good
then check the boot log to see if ndiswrapper booted properly!

hope it all goes well! 

Thanks, Alain

---

### Post by S15_88 on 2007-07-09
well i finally got it working!  did exactly wat i stated above adn now she's good to go, looked like it was the vista driver that was holding back, i'm using xp now and it's all good.  Just a few questions now:

when i'm in network manager i can't click the configure button, wondering why this is?

how do i see wireless signals, i don't have a router at home cause frankly i don't need one, but there are plenty of wireless signals around as i'm in an apartment building and could see them all when in windows, right now i have wifi radar installed and i use that to show me the signals but it won't connect to any of unsecured ones and of course the secured one's.

and just a note i saw this somewhere in the forum but the wifi light is fklickering quick easy fixto that, or is it gunna be total chaos again haha

well thatnks everyone for all the help adn i am glad that i got it all sorted out!

thanks, Alain

---

