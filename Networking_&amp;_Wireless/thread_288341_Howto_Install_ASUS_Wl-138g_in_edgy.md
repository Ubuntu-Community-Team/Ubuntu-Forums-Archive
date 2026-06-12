---
title: "Howto Install ASUS Wl-138g in edgy"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by Stinger on 2006-10-29
This card will only work with ndiswrapper so you'll need to install the ndiswrapper packages first.
Go to System > Administration > Synaptic-packagemanager and look for these packages (a simple search for ndiswrapper should bring them up):

ndiswrapper-common 1.18-1ubuntu2 (edgy)

ndiswrapper-utils-1.8 1.18-1ubuntu2 (edgy)

Install both packages.
Only these two packages should be present !

Now we need the windows driver from the ASUS installation CD-rom , it should be located in Driver > WinXP , [COLOR="Red"]don't use the driver from ASUS Website it screws up your system[/COLOR] 
This driver from Planet Technology WL-8313 works
[ftp://ftp1.planet.com.tw/Wireless_Lan/WL-8313/DR-WL8313v230.zip]("ftp://ftp1.planet.com.tw/Wireless_Lan/WL-8313/DR-WL8313v230.zip")
, copy the 2 files mrv8k51.inf and MRV8K51.sys to your desktop.

Installation from terminal (ndisgtk doesn't work like it did in dapper).
```
cd Desktop
sudo ndiswrapper -i mrv8k51.inf
``` 

then ```
sudo ndiswrapper -m
```to make the module alias in   the /etc/modprobe.d/ndiswrapper file , here is mine.
> alias wlan0 ndiswrapper
And to load the module at boot time , add "ndiswrapper" to your /etc/modules file ,
```
sudo gedit /etc/modules
``` remember to save the file ,as an example here is my /etc/modules file.
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper


To check the driver do ```
ndiswrapper -l
``` it should give > Installed drivers:
mrv8k51         driver installed, hardware present , now reboot and setup your card using System > Administration > Network.
Hope it helps somebody.

---

### Post by Merlene on 2006-10-31
> **Stinger said:**
> This card will only work with ndiswrapper so you'll need to install the ndiswrapper packages first.
Go to System > Administration > Synaptic-packagemanager and look for these packages (a simple search for ndiswrapper should bring them up):

ndiswrapper-common 1.18-1ubuntu2 (edgy)

ndiswrapper-utils-1.8 1.18-1ubuntu2 (edgy)

Install both packages.

Now we need the windows driver from the ASUS installation CD-rom , it should be located in Driver > WinXP , or you could download the driver from [ASUS]("http://support.asus.com/download/download.aspx?SLanguage=en-dk") copy (or unzip from the downloaded driver) the 3 files mrv8k51.inf , MRV8K51.sys and mrv8knet.cat ( mrv8ka51.inf , MRV8KA51.sys , mrv8knet.cat from the downloaded driver)to your desktop.

Installation from terminal (ndisgtk doesn't work like it did in dapper).
```
cd Desktop
sudo ndiswrapper -i mrv8k51.inf
``` or ```
sudo ndiswrapper -i mrv8ka51.inf
```for the downloaded driver.
then ```
sudo ndiswrapper -m
``` to load the module.

To check the driver do ```
ndiswrapper -l
``` it should give  , now reboot and setup your card using System > Administration > Network.
Hope it helps somebody.


Thanks!
I just followed your advice above and got my Linksys DWL-G132 working this way. 

:D Merlene

---

### Post by TeaSipper on 2006-11-19
To add some more information:

The driver from the Asus website made my computer crash. I had more success with this driver: [ftp://ftp.dlink.com/Wireless/dwlg510/Drivers/dwlg510_driver_100.zip](ftp://ftp.dlink.com/Wireless/dwlg510/Drivers/dwlg510_driver_100.zip) (copy the files from the "manual" directory)

If you want WPA also follow these directions: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by eggesin_stefan on 2006-11-19
My Asus WLAN card does not work in any way :( I just tried several ways to make it run, but nothing really worked :(
My Problem is, that ndiswrapper shows me, the driver is already installed and the hardware is present ... but the WLAN-card isn't shown in Network ...
I already tried different windows-drivers ... win98, me, 2k and xp ... i already tried to use a driver from d-link ... alos false :(

Do u have another way to make my WLAN card running?

Here is a screenshot of my problem: [http://stefanknop.st.funpic.de/wlan.png](http://stefanknop.st.funpic.de/wlan.png)
"Kabelgebundene Verbindung" means cable network (via eth0)

Thx for help ...

---

### Post by Stinger on 2006-11-19
> **eggesin_stefan said:**
> My Asus WLAN card does not work in any way :( I just tried several ways to make it run, but nothing really worked :(
My Problem is, that ndiswrapper shows me, the driver is already installed and the hardware is present ... but the WLAN-card isn't shown in Network ...
I already tried different windows-drivers ... win98, me, 2k and xp ... i already tried to use a driver from d-link ... alos false :(

Do u have another way to make my WLAN card running?

Here is a screenshot of my problem: [http://stefanknop.st.funpic.de/wlan.png](http://stefanknop.st.funpic.de/wlan.png)
"Kabelgebundene Verbindung" means cable network (via eth0)

Thx for help ...

I think you have to many ndiswrappers installed.

> Go to System > Administration > Synaptic-packagemanager and look for these packages (a simple search for ndiswrapper should bring them up):

ndiswrapper-common 1.18-1ubuntu2 (edgy)

ndiswrapper-utils-1.8 1.18-1ubuntu2 (edgy)

Install both packages.
Only these two packages should be present !

You have ndisgtk installed and ndisgtk requires the old ndiswrapper packages which does not work.
[COLOR="Red"]
And please don't use the driver from ASUS website , TeaSipper is right , it screws up your system.[/COLOR]

---

### Post by eggesin_stefan on 2006-11-20
Now i have downloaded the driver u said, uninstalled my ndiswrapper pakages and installed only these two u listed and i also uninstalled the old drivers via sudo ndiswrapper -e mrv8k51. then i just followed ur manual but now the console said:

```
stefan@stefan-desktop:~/Desktop$ sudo ndiswrapper -e mrv8k51
stefan@stefan-desktop:~/Desktop$ sudo ndiswrapper -i mrv8k51.inf
Installing mrv8k51
stefan@stefan-desktop:~/Desktop$ sudo ndiswrapper -m
modprobe config already contains alias directive

stefan@stefan-desktop:~/Desktop$ 

```

how can i remove this alias? (maybe this is the error?!)
(i also finished ur manual and restarted my computer ... but no wlan card is shown in Network ... :( 

thx a lot :)

---

### Post by Stinger on 2006-11-20
Did you check with 
ndiswrapper -l ?
should give
```
Installed drivers:
mrv8k51         driver installed, hardware present
```
What does 
```
lspci
```give ?
Mine has this line
```
02:07.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
```
I assume your using edgy otherwise the procedure is different.
The message > modprobe config already contains alias directive is not an error it just means ndiswrapper is already present in your /etc/modprobe.d/ndiswrapper file because you have installed it before.
Here is my /etc/modprobe.d/ndiswrapper file
```
alias wlan0 ndiswrapper
```
"ndiswrapper" should be added to you /etc/modules file to load ndiswrapper module at boot time.
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper
```
I have tested the winXP driver from the ASUS CD-Rom , the Planet Technology WL-8313 winXP driver , which I'm using right now , and the dwlg510 winXP driver TeaSipper linked to , they all work fine with my card.
I have disabled my onboard LAN in BIOS maybe thats the difference ?
Hope it helps.:cool:

---

### Post by Stinger on 2006-11-24
Corrected the howto after reading the ndiswrapper wiki.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Configure_interface]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Configure_interface")

---

### Post by eggesin_stefan on 2006-11-26
ndiswrapper -l: mrv8k51   driver installed, hardware present 

lspci: 01:0a.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)

now i just added ndiswrapper to /etc/modules ... let's try => does not work 

but why should i deactivate eth0 in BIOS? both connections are already working on windows...why shouldn't they on linux?

---

### Post by Stinger on 2006-11-26
> **eggesin_stefan said:**
> ndiswrapper -l: mrv8k51   driver installed, hardware present 

lspci: 01:0a.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)

now i just added ndiswrapper to /etc/modules ... let's try => does not work 

but why should i deactivate eth0 in BIOS? both connections are already working on windows...why shouldn't they on linux?
Ok. your driver is installed propperly and ndiswrapper sees your hardware , we have the exactly the same version of wireless card.
What does your /etc/modprobe.d/ndiswrapper file say ?

what does the output from
```
iwconfig
```give you ?
Adding ndiswrapper to /etc/modules must be done as superuser:
```
sudo gedit /etc/modules
```
Reboot afterwards.


I only disabled my LAN because I run wireless only , will try to enable it and see what happens.:)

---

### Post by Stinger on 2006-11-30
I promised I would try to enable my onboard LAN , I did and when the system came to live I had two working network devices (just as good as any Windows)
:rolleyes:
Se for yourself.

---

### Post by eggesin_stefan on 2006-11-30
/etc/modprobe.d/ndiswrapper:
```
alias wlan0 ndiswrapper
```
iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```
and my /etc/modules:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
fglrx
ndiswrapper

```

nice ur screenshot ... i wanna get it run too ... ](*,)

---

### Post by Stinger on 2006-12-01
Ok ,  	/etc/modprobe.d/ndiswrapper is the same as mine and you are loading ndiswrapper in your /etc/modules file just like me but unlike me , wlan0 isn't present in your output from iwconfig , here is mine.
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"emrwlan"  Nickname:"emrwlan"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:17:D4:B9:33   
          Bit Rate=54 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-68 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```
Lets check your ndiswrapper , what does 
```
dpkg -l | grep ndiswrapper
```give ?
this is what I get
> ii  ndiswrapper-common                         1.18-1ubuntu2                        Userspace utilities for ndiswrapper
ii  ndiswrapper-utils-1.8                      1.18-1ubuntu2                        Userspace utilities for ndiswrapper
And what does 
```
lsmod | grep ndiswrapper
```
give ?
This is what I get
> ndiswrapper           208656  0 
usbcore               134912  5 ndiswrapper,usblp,ehci_hcd,ohci_hcd
Lets try to load ndiswrapper
```
sudo modprobe ndiswrapper
```does it give any kinda error ? 

There is a [ndiswrapper Troubleshooting guide]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Troubleshooting") at the [ Ndiswrapper Wiki]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page") give it a try and see if it helps.8)

---

### Post by eggesin_stefan on 2006-12-03
```
stefan@stefan-desktop:~$ dpkg -l | grep ndiswrapper
ii  ndiswrapper-common                         1.18-1ubuntu2                     Userspace utilities for ndiswrapper
ii  ndiswrapper-utils-1.8                      1.18-1ubuntu2                     Userspace utilities for ndiswrapper
```

```
stefan@stefan-desktop:~$ lsmod | grep ndiswrapper
ndiswrapper           192468  0 
usbcore               130304  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd
```

```
stefan@stefan-desktop:~$ sudo modprobe ndiswrapper
Password:
stefan@stefan-desktop:~$
```

---

### Post by eggesin_stefan on 2006-12-03
i have searched both sides and found something intresting, which can help ... maybe ...

```
Card: Asus WL-138G, 54mbps

    * Chipset: Marvell W8300
    * pciid: 11ab:1fa6 (rev 07)>
    * Driver: CDROM, ASUS [[29]]
    * Works with amd64 and 64 bits driver taken here: [ftp://dlsvr01.asus.com/pub/ASUS/lan/wifi-g/WIFI_V2712_64bit.zip]
    * Other: Works well with Ndiswrapper 1.0 and CDROM WinXP driver on Gentoo with Kernel 2.6.11. ASUS Downloaded driver fails.; Problems with new driver versions and ndiswrapper 1.x (System Freeze), but the driver on CD mrv8k51 (ASUS,12/24/2003,2.2.0.20) works fine with ndiswrapper 1.5 (1.6rc2 is more stable) on linux 2.6.14.2 and 16kstacks (I will test if it works without the 16k patch). Works better with win98 driver for the card D-Link DWL-G510 [ftp://ftp.dlink.com/Wireless/dwlg510/Drivers/dwlg510_driver_100.zip] (manual directory).
    * Other: Ubuntu Dapper comes with a native, but not working Marvell driver [[30]]. To use ndiswrapper, you must prevent it from loading at boot, e.g. by removing the mrv8k.ko file from /lib/modules/...kernel.... The DLink Win98 driver works, but I see a few system freezes. Using the newer, downloaded Asus Win98 driver (after renaming mrv8ka50.sys to mrv8ka51.sys) the system often hangs at boot, but is more stable afterwards. With both drivers, booting is slow. 
```

---

### Post by Stinger on 2006-12-05
Oh ! you mean this:
> Other: Ubuntu Dapper comes with a native, but not working Marvell driver
To use ndiswrapper, you must prevent it from loading at boot, e.g. by removing the mrv8k.ko file from /lib/modules/...kernel....
But that only goes for Dapper not Edgy.
You can read all about it at the [ndiswrapper stuff]("http://www.ubuntuforums.org/showthread.php?t=190726") thread. At post [#10]("http://www.ubuntuforums.org/showpost.php?p=1147777&postcount=10") you can see how I solved it thanks to DaveZ and RoyalShrubber.
I don't think thats your trouble , but what the heck give it a try.[-o<  

How does your /etc/network/interfaces file look ?
Here is mine
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid emrwlan
```

I really hope it helps this time.

---

### Post by eggesin_stefan on 2006-12-07
```
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.178.25
netmask 255.255.255.0
gateway 192.168.178.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

```

---

### Post by Stinger on 2006-12-10
Hmm...
try this , first:
```
sudo rmmod ndiswrapper
```
then,
```
sudo modprobe ndiswrapper
```
and after that you do
```
dmesg
```
Now the last lines listed should tell you something about the state of your ndiswrapper. Here is my last lines.
> ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
ndiswrapper: driver mrv8k51 (PLANET Technology Corp.,01/19/2004,2.3.0.3) loaded
ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 209
PCI: Setting latency timer of device 0000:02:07.0 to 64
ndiswrapper: using irq 209
wlan0: vendor: 'Marvell 802.11 Driver'
wlan0: ethernet device 00:11:2f:d7:b0:81 using NDIS driver mrv8k51, 11AB:1FA6.5.conf
ndiswrapper (set_encr_mode:689): setting encryption mode to 6 failed (C00000BB)
wlan0: encryption modes supported: WEP; TKIP with WPA

---

### Post by eggesin_stefan on 2006-12-11
now i just did what u said and this is the output of the last lines:

```
[17213652.492000] ndiswrapper version 1.25 loaded (preempt=no,smp=no)
[17213652.524000] usbcore: registered new driver ndiswrapper
stefan@stefan-desktop:~$ 
```

---

### Post by Stinger on 2006-12-12
Thats odd ! you have version 1.25 and I have version 1.22 , did you by any chance try to compile and install ndiswrapper from source ?

Lets see what kernel you are using:
```
dpkg -l | grep linux-image
```
Here is my output.
> ii  linux-image-2.6.17-10-generic              2.6.17-10.33                         Linux kernel image for version 2.6.17 on x86
ii  linux-image-generic                        2.6.17.10                            Generic Linux kernel image
I think it must be your kernel module thats wrong [COLOR="Blue"]ndiswrapper.ko[/COLOR] located in [COLOR="Blue"]/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko[/COLOR]

---

### Post by eggesin_stefan on 2006-12-15
```
stefan@stefan-desktop:~$ dpkg -l | grep linux-image
ii  linux-image-2.6.17-10-386                  2.6.17.1-10.34                    Linux kernel image for version 2.6.17 on i38
ii  linux-image-2.6.17-10-generic              2.6.17.1-10.34                    Linux kernel image for version 2.6.17 on x86
ii  linux-image-generic                        2.6.17.10                         Generic Linux kernel image
stefan@stefan-desktop:~$ 

```

---

### Post by Stinger on 2006-12-15
It seems you have been upgrading the kernel , like me , to 2.6.17.1-10.34
I still have ndiswrapper version 1.22 , what about you?
Could you try this again and post you last lines ?

sudo rmmod ndiswrapper

then

sudo modprobe ndiswrapper

and after that

dmesg
 
the kernel module should have been replaced during upgrade (ndiswrapper.ko) cause it's part of the "linux-image" package.:-k

---

### Post by eggesin_stefan on 2006-12-18
```
[17190113.276000] usbcore: deregistering driver ndiswrapper
[17190123.488000] ndiswrapper version 1.25 loaded (preempt=no,smp=no)
[17190123.504000] usbcore: registered new driver ndiswrapper
stefan@stefan-desktop:~$ 

```

---

### Post by eggesin_stefan on 2006-12-18
or should i uninstall ndiswrapper 1.25 and install 1.22 ... if i can find it anywhere ... or do u have a link for me?

---

### Post by Stinger on 2006-12-18
> **eggesin_stefan said:**
> or should i uninstall ndiswrapper 1.25 and install 1.22 ... if i can find it anywhere ... or do u have a link for me?
My best advice for you would be to backup any files you want to save and make a fresh installation of Edgy and take from there.
There must be some ndiswrapper leftovers remaining in you system from a previous installation attempt , most likely the kernel module "ndiswrapper.ko".
Ofcourse you can try the [[COLOR="Sienna"]Uninstall guide[/COLOR] ]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall") from the ndiswrapper wiki.
I have attached my ndiswrapper.ko as a zip file if you want to try replacing it.

[COLOR="Magenta"]But the best solution is a fresh installation I think !   [/COLOR]:-\"

---

### Post by eggesin_stefan on 2006-12-21
Thx for helping :-) Now I just sold my computer and I do not have this problem anymore, someone else has it now :D
But I will try to get my WLAN card running by installing Edgy on an other system.

---

### Post by Stinger on 2006-12-21
I hope you have learned as much about ndiswrapper as I have :biggrin:  
In future I'll stick to [[COLOR="Sienna"]Ralink chipsets based wireless devices[/COLOR]]("http://ralink.rapla.net/") they seem to work right out of the box , ralink is known for it's [[COLOR="Sienna"]Linux support[/COLOR]]("http://www.ralinktech.com/ralink/Home/Support/Linux.html") , I know my ASUS WL-167g usb pen does.:-D

---

### Post by Griffiss on 2007-03-11
@ Stinger

Hey!

I have done what you suggest above, and now ```
ndiswrapper -l
```gives > Installed drivers:
mrv8k51       driver installed, hardware present

The wireless connection now shows up in the Netork Settings box, but I'm not connected. I've been working on this problem for two days solidly and getting nowhere. can you help me? Please?!!

---

### Post by Griffiss on 2007-03-11
in fact, can anyone help?!!!

---

### Post by yigal.weinstein on 2007-03-11
1.  It may just have to do with multiple attempts at connecting, making your card and computer have problems with each other.  First type in the terminal (tintt).

```
sudo /etc/init.d/networking stop
```
then
```
sudo /etc/init.d/networking start
```
then
```
arp -a
```
copy the ip address, the number in parenthesis so that you have typed,
```
ping "number in ()"
```

What output do you get?

2. Here is another tutorial [http://www.megalinux.net/archives/467.html]("http://www.megalinux.net/archives/467.html")
I hope this does you some good.

---

### Post by Griffiss on 2007-03-11
thanks for your help yigal, but I need a break. been at this way too long now. I'll get back to you when I have some results

---

### Post by Stinger on 2007-03-13
Griffiss , open a terminal  , what does the output from iwconfig give you ?

Here is my output from

iwconfig

```
---@----desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"emrwlan"  Nickname:"emrwlan"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:17:D4:B9:33   
          Bit Rate=54 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-61 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

---

### Post by maxito on 2007-09-06
Hello,

I followed Stingers Instructions, at my system it worked also under Feisty.


All the Best,
max

---

### Post by mephibosheth13 on 2007-11-08
I have followed the advice in this thread and I thought I was going to get my card to work :-(  The card that I have is the D-Link Airplus DWL-510g.  I am running Ubuntu Linux with 2.6.22-14 (gutsy) Kernel.

```
mephibosheth@valkrath:/home/mephibosheth/Desktop/Driver/WinXP# lspci
02:07.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
```

I have done all the steps to this point.

```
ndiswrapper -l gives me this message:
mrv8ka51 : driver installed
        device (11AB:1FA6) present
```

but using the mrv8ka51 driver, when I would give the command
dmesg I would get an error message saying that the Kernel was 64bit but the driver mrv8ka51 was not.  I am running x86_64 system:
```
mephibosheth@valkrath:/home/mephibosheth/Desktop/Driver/WinXP# uname -a
Linux valkrath 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
```


I went and downloaded the 64bit version of the drivers from Asus (I know that it messes with your system, but I wanted to try it to see if it would rid me of the message about 64bit OS and non 64bit driver which it did).  Now when I modprobe ndiswrapper after installing the drivers with ndiswrapper -i driver.inf it just sits there doing nothing.  After I Ctrl + C I checked the dmesg again:

```
mephibosheth@valkrath:/home/mephibosheth/Desktop/Driver/WinXP# dmesg | grep ndis
[   54.049465] ndiswrapper version 1.45 loaded (smp=yes)
[   54.106194] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   54.106982] ndiswrapper: driver mrv8k64 (Marvell,06/08/2005,2.7.1.19) loaded
[   54.108805] ndiswrapper: using IRQ 19
[   54.169914] Modules linked in: ndiswrapper parport_pc lp parport snd_mpu401 snd_mpu401_uart snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd psmouse soundcore serio_raw analog gameport k8temp pcspkr xpad shpchp pci_hotplug i2c_nforce2 i2c_core joydev evdev ext3 jbd mbcache sg sd_mod ide_cd cdrom ide_disk ata_generic usbhid hid usb_storage libusual floppy forcedeth sata_nv libata scsi_mod amd74xx ide_core ehci_hcd ohci_hcd usbcore thermal processor fan fuse apparmor commoncap
[   54.170025]  [<ffffffff882880b9>] :ndiswrapper:NdisMCancelTimer+0x9/0x10
[   54.170045]  [<ffffffff88299537>] :ndiswrapper:win2lin2+0xe/0x11
[   54.170063]  [<ffffffff88299537>] :ndiswrapper:win2lin2+0xe/0x11
[   54.170084]  [<ffffffff88299537>] :ndiswrapper:win2lin2+0xe/0x11
[   54.170107]  [<ffffffff8828f42f>] :ndiswrapper:IofCallDriver+0x5f/0xc0
[   54.170133]  [<ffffffff8828f404>] :ndiswrapper:IofCallDriver+0x34/0xc0
[   54.170156]  [<ffffffff88295dd5>] :ndiswrapper:mp_init+0xa5/0x190
[   54.170174]  [<ffffffff882908c0>] :ndiswrapper:IoSyncForwardIrp+0x90/0xd0
[   54.170194]  [<ffffffff8829652b>] :ndiswrapper:NdisDispatchPnp+0xdb/0xd40
[   54.170223]  [<ffffffff8828facb>] :ndiswrapper:IoInitializeIrp+0x3b/0x70
[   54.170244]  [<ffffffff88299537>] :ndiswrapper:win2lin2+0xe/0x11
[   54.170262]  [<ffffffff8828f42f>] :ndiswrapper:IofCallDriver+0x5f/0xc0
[   54.170280]  [<ffffffff8828f404>] :ndiswrapper:IofCallDriver+0x34/0xc0
[   54.170297]  [<ffffffff882902ff>] :ndiswrapper:IoBuildSynchronousFsdRequest+0x2f/0x50
[   54.170316]  [<ffffffff8829461c>] :ndiswrapper:IoSendIrpTopDev+0xac/0x100
[   54.170338]  [<ffffffff8829491f>] :ndiswrapper:pnp_start_device+0x4f/0xa0
[   54.170360]  [<ffffffff88294b54>] :ndiswrapper:wrap_pnp_start_device+0x1e4/0x280
[   54.170382]  [<ffffffff88294c40>] :ndiswrapper:wrap_pnp_start_pci_device+0x50/0x60
[   54.170445]  [<ffffffff88284d5c>] :ndiswrapper:loader_init+0x13c/0x260
[   54.170457]  [<ffffffff880650b5>] :ndiswrapper:wrapper_init+0xb5/0xc2
```

Any ideas?  Any help would be appreciated! I have been trying to get this card working under Linux for a while now.

---

### Post by Stinger on 2007-11-08
> **mephibosheth13 said:**
>  I am running x86_64 system:

Hi ! did you see this thread:
[http://ubuntuforums.org/showthread.php?t=391416]("http://ubuntuforums.org/showthread.php?t=391416")

I have no experience in x86_64 sorry , my system is i386.

Hope it helps.

---

### Post by mephibosheth13 on 2007-11-09
> **Stinger said:**
> Hi ! did you see this thread:
[http://ubuntuforums.org/showthread.php?t=391416]("http://ubuntuforums.org/showthread.php?t=391416")

I have no experience in x86_64 sorry , my system is i386.

Hope it helps.

Thank you so very much!!  That did the trick and I am now working wireless :guitar:\\:D/\\:D/\\:D/\\:D/

---

### Post by Stinger on 2007-11-11
I'm only the messenger , the credit goes to Jouke74 , you should drop a thank you to him too ;)

I'm glad to hear you got your wireless working.

Ubuntu rocks !!

---

