---
title: "Buffalo WL12 PCI G54S wireless help please"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by jacksparrow1 on 2008-08-21
hi everyone

I was hoping some more experienced heads of Ubuntu could offer me some help please, I have spent hours and hours trying to get my wireless card to work - I know some of you might think 'how many sites are there on the Internet  to help me' I know, but I've tried and I've tried from step by steps tutorials to downloading ndiswrapper to downloading kernel but I keep getting stuck.

I know the first step for me is to install a driver, so I checked this website which told me my Wireless card was capatible and it is.  I'm not sure what to do next, any help please?

I have the following code, could some one tell me if I need a driver please?

```

ubuntu@UBUNTU-PC:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network                
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 8 
       bus info: pci@0000:04:08.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:16:01:7d:ea:7e 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 
ubuntu@UBUNTU-PC:~$  

```

**crosses finger for someone to tell me that I dont need the drivers**

The funny thing is half an hour ago I gave up, I actually shut down ubuntu and told my self I would never use it again because I got frustrated so much - however I told my self I'm not a quitter because I love the whole GUI of Ubuntu and it kicks *** compared to XP/Vista, I know one day I will overcome the whole issue of trying to get my wireless to work.

Thanks people.

---

### Post by nixscripter on 2008-08-22
I've had some trouble with this driver, but there are two conventional methods, both of which require the Windows install disks:

1. ndiswrapper uses the SYS and INI files on the disc to simulate the mechanism windows uses to control network cards. A HOWTO for that is here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

2. You can use the bcm43xx kernel driver, and then extract the firmware from the windows files so it will work. General information is here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I would simply add that both ways have worked for me before. I never got a working wireless card, it turned out, because of a busted antenna ;-). But the driver worked either way.

Hope this helps.

---

### Post by jacksparrow1 on 2008-08-22
I checked that Ndiswrapper link earlier but it sounded confusing to me:

so far I done the fololowing


```

ubuntu@UBUNTU-PC:~$ sudo apt-get install ndiswrapper-utils-1.9

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following extra packages will be installed:

  ndiswrapper-common

Suggested packages:

  ndiswrapper-source

The following NEW packages will be installed

  ndiswrapper-common ndiswrapper-utils-1.9

0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.

Need to get 0B/30.4kB of archives.

After this operation, 213kB of additional disk space will be used.

Do you want to continue [Y/n]? y

Selecting previously deselected package ndiswrapper-common.

(Reading database ... 95844 files and directories currently installed.)

Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.50-1ubuntu1_all.deb) ...

Selecting previously deselected package ndiswrapper-utils-1.9.

Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) ...

Setting up ndiswrapper-common (1.50-1ubuntu1) ...

Setting up ndiswrapper-utils-1.9 (1.50-1ubuntu1) ...

ubuntu@UBUNTU-PC:~$ 


```

Does this mean ndiswrapper has installed?  Sorry if i sound like an idiot - it's just I've never even looked at a linux before.

If ndiswrapper has installed, what do I do to install the drivers of my wireless card? (I have the drivers on my cd that came with the card)  Thanks guys much appreciated.

---

### Post by jacksparrow1 on 2008-08-22
Anyone?

---

### Post by nixscripter on 2008-08-23
Now that you've got that, you need to get your driver CD out, and look for a SYS and INI file. Put in the CD, assuming it's called MyDriverCD, and see what comes out of this command:

```
 find /media/**MyDriverCD** -iname '*sys'
```

---

### Post by jacksparrow1 on 2008-08-24
Thanks for getting back to me,

I've tried everything you suggested but I just dont know where I am going wrong.

What I done first was load the cd in XP, when I click on 'my computer' it showed that the name of the cd was airnavi870e, I right clicked on the cd and clicked on 'search'.  

I then searched for the *sys file.

airnavi870e/bin/clientmgr3/sys/sys_ev

I then searched for the *ini file:

airnavi870e/bin/driver/pcil11/win2000/wlil11

Now I know the location of both of these files, so I restarted my computer in Ubuntu, I opened up terminal and I tried the following:

```

ubuntu@UBUNTU-PC:~$ find /media/airnavi870e -iname '*sys'

find: /media/airnavi870e: No such file or directory

ubuntu@UBUNTU-PC:~$ sudo find /media/airnavi870e -iname '*sys'

[sudo] password for ubuntu: 

find: /media/airnavi870e: No such file or directory

ubuntu@UBUNTU-PC:~$ find /media/airnavi870e -iname '*sys'

find: /media/airnavi870e: No such file or directory

ubuntu@UBUNTU-PC:~$ find /media/airnavi870e/bin/ClientMgr3 -iname '*sys'

find: /media/airnavi870e/bin: No such file or directory

ubuntu@UBUNTU-PC:~$ find /media/airnavi870e/bin/ClientMgr3/sys -iname '*sys'

find: /media/airnavi870e/bin/ClientMgr3: No such file or directory

ubuntu@UBUNTU-PC:~$ find /media/airnavi870e/bin/ClientMgr3/sys/sys_env -iname '*sys'

find: /media/airnavi870e/bin/ClientMgr3/sys: No such file or directory

ubuntu@UBUNTU-PC:~$

```

**Please note some of the above coding might look out of place because when I tranfered it from ubuntu to xp I used a text file and some of the coding was all over the place.

Thanks again

---

### Post by nixscripter on 2008-08-24
Maybe the CD is mounted as a device name. When it's in, what is the contents of /media?

---

### Post by jacksparrow1 on 2008-08-24
Hi,

Well as requested, I tried the following

```

find /media/

```

And it gave me the following reply (I do think you was correct because I think it was after cdrom0)

```

/media/cdrom0/Bin/Driver/CFS11G/CESETUP.exe
/media/cdrom0/Bin/Driver/CFS11G/NETS11.inf
/media/cdrom0/Bin/Driver/CFS11G/WIN2000
/media/cdrom0/Bin/Driver/CFS11G/WIN2000/NETS11.inf
/media/cdrom0/Bin/Driver/CFS11G/WIN2000/WLIS11.sys
/media/cdrom0/Bin/Driver/CFS11G/WIN2000/wlis11.cat
/media/cdrom0/Bin/Driver/CFS11G/WINXP
/media/cdrom0/Bin/Driver/CFS11G/WINXP/NETS11.inf
/media/cdrom0/Bin/Driver/CFS11G/WINXP/WLIS11.sys
/media/cdrom0/Bin/Driver/CFS11G/WLICFS11.INI
/media/cdrom0/Bin/Driver/CFS11G/WLICFS11US.A720H.CAB
/media/cdrom0/Bin/Driver/CFS11G/WLICFS11US.A720P.CAB
/media/cdrom0/Bin/Driver/CFS11G/WLICFS11US.R4KH.CAB
/media/cdrom0/Bin/Driver/CFS11G/WLICFS11US.R4KP.CAB
/media/cdrom0/Bin/Driver/CFS11G/WLICFS11US.SAH.CAB
/media/cdrom0/Bin/Driver/CFS11G/WLICFS11US.SAP.CAB
/media/cdrom0/Bin/Driver/CFS11G/WLICFS11US.SH3H.CAB
/media/cdrom0/Bin/Driver/CFS11G/WLICFS11US.SH3P.CAB
/media/cdrom0/Bin/Driver/CFS11G/WLICFS11US.SH4H.CAB
/media/cdrom0/Bin/Driver/CFS11G/WLICFS11US.SH4P.CAB
/media/cdrom0/Bin/Driver/CFS11G/WLIS11.sys
/media/cdrom0/Bin/Driver/DISKINFO.INF
/media/cdrom0/Bin/Driver/ESSIDSET.DLL
/media/cdrom0/Bin/Driver/ESSIDSET.VXD
/media/cdrom0/Bin/Driver/ESSIDSET.sys
/media/cdrom0/Bin/Driver/GNU_LICENSE.PDF
/media/cdrom0/Bin/Driver/INST.INI
/media/cdrom0/Bin/Driver/INST.dll
/media/cdrom0/Bin/Driver/Inst.exe
/media/cdrom0/Bin/Driver/LAUNCHER.INI
/media/cdrom0/Bin/Driver/MDRIVER
/media/cdrom0/Bin/Driver/MDRIVER/DEVREMOVE.exe
/media/cdrom0/Bin/Driver/MDRIVER/DEVREMOVE.ini
/media/cdrom0/Bin/Driver/MDRIVER/DelDev16.dll
/media/cdrom0/Bin/Driver/MDRIVER/Mdriver.ini
/media/cdrom0/Bin/Driver/MDRIVER/mdriver.exe
/media/cdrom0/Bin/Driver/PCIL11
/media/cdrom0/Bin/Driver/PCIL11/WINNT
/media/cdrom0/Bin/Driver/PCIL11/WINNT/CSH.DLL
/media/cdrom0/Bin/Driver/PCIL11/WINNT/WLIL11.dll
/media/cdrom0/Bin/Driver/PCIL11/WINNT/WLIL11.sys
/media/cdrom0/Bin/Driver/PCIL11/WINNT/oemsetup.inf
/media/cdrom0/Bin/Driver/PCIL11/WLIL11.sys
/media/cdrom0/Bin/Driver/PCIL11/WVLANUIF.VXD
/media/cdrom0/Bin/Driver/PCIL11/netwli11.inf
/media/cdrom0/Bin/Driver/PCIL11/win2000
/media/cdrom0/Bin/Driver/PCIL11/win2000/netl112k.inf
/media/cdrom0/Bin/Driver/PCIL11/win2000/wlil11.sy_
/media/cdrom0/Bin/Driver/PCIL11/wli11ins.dll
/media/cdrom0/Bin/Driver/PCIOP
/media/cdrom0/Bin/Driver/PCIOP/SETUP.EXE
/media/cdrom0/Bin/Driver/PCIOP/WIN2000
/media/cdrom0/Bin/Driver/PCIOP/WIN2000/UNINST.exe
/media/cdrom0/Bin/Driver/PCIOP/WIN2000/WLIPCIK.INF
/media/cdrom0/Bin/Driver/PCIOP/WIN2000/WLIPCIK.SYS
/media/cdrom0/Bin/Driver/PCIOP/WIN2000/wlipcik.cat
/media/cdrom0/Bin/Driver/PCIOP/WIN95
/media/cdrom0/Bin/Driver/PCIOP/WIN95/WLIPCI.INF
/media/cdrom0/Bin/Driver/PCIOP/WIN95/WLIPCI.VXD
/media/cdrom0/Bin/Driver/PCIOP/WIN95R2
/media/cdrom0/Bin/Driver/PCIOP/WIN95R2/WLIIRQ.COM
/media/cdrom0/Bin/Driver/PCIOP/WIN95R2/WLIPCI.INF
/media/cdrom0/Bin/Driver/PCIOP/WIN95R2/WLIPCI.VXD
/media/cdrom0/Bin/Driver/PCIOP/WIN98
/media/cdrom0/Bin/Driver/PCIOP/WIN98/WLIPCI.INF
/media/cdrom0/Bin/Driver/PCIOP/WIN98/WLIPCI.VXD
/media/cdrom0/Bin/Driver/PCIOP/WLIPCI.SYS
/media/cdrom0/Bin/Driver/PCIOP/WinMe
/media/cdrom0/Bin/Driver/PCIOP/WinMe/WLIPCI.INF
/media/cdrom0/Bin/Driver/PCIOP/WinMe/WLIPCI.VXD
/media/cdrom0/Bin/Driver/PCIOP/WinNT
/media/cdrom0/Bin/Driver/PCIOP/WinNT/SETUP.EXE
/media/cdrom0/Bin/Driver/PCMS11
/media/cdrom0/Bin/Driver/PCMS11/NETS11.inf
/media/cdrom0/Bin/Driver/PCMS11/WIN2000
/media/cdrom0/Bin/Driver/PCMS11/WIN2000/NETS11.inf
/media/cdrom0/Bin/Driver/PCMS11/WIN2000/WLIS11.sys
/media/cdrom0/Bin/Driver/PCMS11/WIN2000/wlis11.cat
/media/cdrom0/Bin/Driver/PCMS11/WIN95
/media/cdrom0/Bin/Driver/PCMS11/WIN95/NETS11.inf
/media/cdrom0/Bin/Driver/PCMS11/WIN95/WLIS11.SYS
/media/cdrom0/Bin/Driver/PCMS11/WINXP
/media/cdrom0/Bin/Driver/PCMS11/WINXP/NETS11.inf
/media/cdrom0/Bin/Driver/PCMS11/WINXP/WLIS11.sys
/media/cdrom0/Bin/Driver/PCMS11/WLIS11.sys
/media/cdrom0/Bin/Driver/PCMS11/Win98
/media/cdrom0/Bin/Driver/PCMS11/Win98/NETS11.inf
/media/cdrom0/Bin/Driver/PCMS11/Win98/WLIS11.sys
/media/cdrom0/Bin/Driver/PCMS11/WinMe
/media/cdrom0/Bin/Driver/PCMS11/WinMe/NETS11.inf
/media/cdrom0/Bin/Driver/PCMS11/WinMe/WLIS11.sys
/media/cdrom0/Bin/Driver/Pcml11
/media/cdrom0/Bin/Driver/Pcml11/NETL11GP.INF
/media/cdrom0/Bin/Driver/Pcml11/WIN2000
/media/cdrom0/Bin/Driver/Pcml11/WIN2000/INITISA.exe
/media/cdrom0/Bin/Driver/Pcml11/WIN2000/Netl11.inf
/media/cdrom0/Bin/Driver/Pcml11/WIN2000/WLMEL48B.SYS
/media/cdrom0/Bin/Driver/Pcml11/WIN2000/wlmel48b.cat
/media/cdrom0/Bin/Driver/Pcml11/WINNT
/media/cdrom0/Bin/Driver/Pcml11/WINNT/CSH.DLL
/media/cdrom0/Bin/Driver/Pcml11/WINNT/OEMSETUP.INF
/media/cdrom0/Bin/Driver/Pcml11/WINNT/WLIL11.DLL
/media/cdrom0/Bin/Driver/Pcml11/WINNT/WLIL11.SYS
/media/cdrom0/Bin/Driver/Pcml11/WINXP
/media/cdrom0/Bin/Driver/Pcml11/WINXP/WAAGS48B.DLL
/media/cdrom0/Bin/Driver/Pcml11/WINXP/WCAGS48B.EXE
/media/cdrom0/Bin/Driver/Pcml11/WINXP/WDAGS48B.DLL
/media/cdrom0/Bin/Driver/Pcml11/WINXP/WLAGS48B.INF
/media/cdrom0/Bin/Driver/Pcml11/WINXP/WLAGS48B.SYS
/media/cdrom0/Bin/Driver/Pcml11/WINXP/wlags48b.cat
/media/cdrom0/Bin/Driver/Pcml11/WLIL11.SYS
/media/cdrom0/Bin/Driver/Pcml11/WLMEL41.SYS
/media/cdrom0/Bin/Driver/Pcml11/WLMEL48.SYS
/media/cdrom0/Bin/Driver/Pcml11/WUMEL41.VXD
/media/cdrom0/Bin/Driver/Pcml11/WUMEL48.VXD
/media/cdrom0/Bin/Driver/Pcml11/WVLANUIF.VXD
/media/cdrom0/Bin/Driver/Pcml11/Win95
/media/cdrom0/Bin/Driver/Pcml11/Win95/NETL11GP.INF
/media/cdrom0/Bin/Driver/Pcml11/Win95/WLIL11.SYS
/media/cdrom0/Bin/Driver/Pcml11/Win95/WLMEL41.SYS
/media/cdrom0/Bin/Driver/Pcml11/Win95/WLMEL48.SYS
/media/cdrom0/Bin/Driver/Pcml11/Win95/WUMEL41.VXD
/media/cdrom0/Bin/Driver/Pcml11/Win95/WUMEL48.VXD
/media/cdrom0/Bin/Driver/Pcml11/Win95/WVLANUIF.VXD
/media/cdrom0/Bin/Driver/Pcml11/Win95/Wl11gpci.dll
/media/cdrom0/Bin/Driver/Pcml11/Win98
/media/cdrom0/Bin/Driver/Pcml11/Win98/NETL11GP.INF
/media/cdrom0/Bin/Driver/Pcml11/Win98/WLIL11.SYS
/media/cdrom0/Bin/Driver/Pcml11/Win98/WLMEL41.SYS
/media/cdrom0/Bin/Driver/Pcml11/Win98/WLMEL48.SYS
/media/cdrom0/Bin/Driver/Pcml11/Win98/WUMEL41.VXD
/media/cdrom0/Bin/Driver/Pcml11/Win98/WUMEL48.VXD
/media/cdrom0/Bin/Driver/Pcml11/Win98/WVLANUIF.VXD
/media/cdrom0/Bin/Driver/Pcml11/Win98/Wl11gpci.dll
/media/cdrom0/Bin/Driver/Pcml11/WinMe
/media/cdrom0/Bin/Driver/Pcml11/WinMe/NETL11GP.INF
/media/cdrom0/Bin/Driver/Pcml11/WinMe/WLIL11.SYS
/media/cdrom0/Bin/Driver/Pcml11/WinMe/WLMEL41.SYS
/media/cdrom0/Bin/Driver/Pcml11/WinMe/WLMEL48.SYS
/media/cdrom0/Bin/Driver/Pcml11/WinMe/WUMEL41.VXD
/media/cdrom0/Bin/Driver/Pcml11/WinMe/WUMEL48.VXD
/media/cdrom0/Bin/Driver/Pcml11/WinMe/WVLANUIF.VXD
/media/cdrom0/Bin/Driver/Pcml11/WinMe/Wl11gpci.dll
/media/cdrom0/Bin/Driver/Pcml11/Wl11gpci.dll
/media/cdrom0/Bin/Driver/U2G300N
/media/cdrom0/Bin/Driver/U2G300N/NETUG300.inf
/media/cdrom0/Bin/Driver/U2G300N/U2G300N.cat
/media/cdrom0/Bin/Driver/U2G300N/U2G300N3.sys
/media/cdrom0/Bin/Driver/U2G300N/U2G300N5.sys
/media/cdrom0/Bin/Driver/U2KAMG54
/media/cdrom0/Bin/Driver/U2KAMG54/Win2000
/media/cdrom0/Bin/Driver/U2KAMG54/Win2000/Netkamgl.inf
/media/cdrom0/Bin/Driver/U2KAMG54/Win2000/ar5523.bin
/media/cdrom0/Bin/Driver/U2KAMG54/Win2000/ar5523.sys
/media/cdrom0/Bin/Driver/U2KAMG54/Win2000/athfmwdl.cat
/media/cdrom0/Bin/Driver/U2KAMG54/Win2000/athfmwdl.sys
/media/cdrom0/Bin/Driver/U2KAMG54/Win2000/net5523.cat
/media/cdrom0/Bin/Driver/U2KAMG54/Win2000/netkamg.inf
/media/cdrom0/Bin/Driver/U2KAMG54/Win9x
/media/cdrom0/Bin/Driver/U2KAMG54/Win9x/ar5523.bin
/media/cdrom0/Bin/Driver/U2KAMG54/Win9x/ar55239x.sys
/media/cdrom0/Bin/Driver/U2KAMG54/Win9x/athfmwdl.cat
/media/cdrom0/Bin/Driver/U2KAMG54/Win9x/athfmwdl.sys
/media/cdrom0/Bin/Driver/U2KAMG54/Win9x/net5523.cat
/media/cdrom0/Bin/Driver/U2KAMG54/Win9x/netkamg.inf
/media/cdrom0/Bin/Driver/U2KAMG54/Win9x/netkamgl.inf
/media/cdrom0/Bin/Driver/U2KG125S
/media/cdrom0/Bin/Driver/U2KG125S/RNDISMP.sys
/media/cdrom0/Bin/Driver/U2KG125S/RNDISMPK.sys
/media/cdrom0/Bin/Driver/U2KG125S/bcm43xx.cat
/media/cdrom0/Bin/Driver/U2KG125S/netg125s.inf
/media/cdrom0/Bin/Driver/U2KG125S/usb8023.sys
/media/cdrom0/Bin/Driver/U2KG125S/usb8023k.sys
/media/cdrom0/Bin/Driver/U2KG54
/media/cdrom0/Bin/Driver/U2KG54/Win2000
/media/cdrom0/Bin/Driver/U2KG54/Win2000/AIFILT.sys
/media/cdrom0/Bin/Driver/U2KG54/Win2000/NETU2KG.INF
/media/cdrom0/Bin/Driver/U2KG54/Win2000/U2KG54.CAT
/media/cdrom0/Bin/Driver/U2KG54/Win2000/U2KG54.sys
/media/cdrom0/Bin/Driver/U2KG54/Win2000/bfaifilt.sys
/media/cdrom0/Bin/Driver/U2KG54/Win98
/media/cdrom0/Bin/Driver/U2KG54/Win98/AIFILT.sys
/media/cdrom0/Bin/Driver/U2KG54/Win98/NETU2KG.INF
/media/cdrom0/Bin/Driver/U2KG54/Win98/U2KG54.CAT
/media/cdrom0/Bin/Driver/U2KG54/Win98/U2KG5498.sys
/media/cdrom0/Bin/Driver/U2KG54/Win98/bfaifilt.sys
/media/cdrom0/Bin/Driver/U2KG54/WinME
/media/cdrom0/Bin/Driver/U2KG54/WinME/AIFILT.sys
/media/cdrom0/Bin/Driver/U2KG54/WinME/NETU2KG.INF
/media/cdrom0/Bin/Driver/U2KG54/WinME/U2KG54.CAT
/media/cdrom0/Bin/Driver/U2KG54/WinME/U2KG5498.sys
/media/cdrom0/Bin/Driver/U2KG54/WinME/bfaifilt.sys
/media/cdrom0/Bin/Driver/USBG54
/media/cdrom0/Bin/Driver/USBG54/BWCDRV.VXD
/media/cdrom0/Bin/Driver/USBG54/BWCINST.dll
/media/cdrom0/Bin/Driver/USBG54/RNDISMPK.sys
/media/cdrom0/Bin/Driver/USBG54/bwcdrv.cat
/media/cdrom0/Bin/Driver/USBG54/bwcdrv.sys
/media/cdrom0/Bin/Driver/USBG54/netbwc2k.inf
/media/cdrom0/Bin/Driver/USBG54/netbwc98.inf
/media/cdrom0/Bin/Driver/USBG54/netusg54.inf
/media/cdrom0/Bin/Driver/USBG54/rndismpm.sys
/media/cdrom0/Bin/Driver/USBG54/rndismpw.sys
/media/cdrom0/Bin/Driver/USBG54/usb8023k.sys
/media/cdrom0/Bin/Driver/USBG54/usb8023m.sys
/media/cdrom0/Bin/Driver/USBG54/usb8023w.sys
/media/cdrom0/Bin/Driver/USBG54/wliusg54.cat
/media/cdrom0/Bin/Driver/USBKB11
/media/cdrom0/Bin/Driver/USBKB11/Firmware
/media/cdrom0/Bin/Driver/USBKB11/Firmware/USBKS11G
/media/cdrom0/Bin/Driver/USBKB11/Firmware/USBKS11G/ISLNDIS4.sys
/media/cdrom0/Bin/Driver/USBKB11/Firmware/USBKS11G/ISLNDIS5.sys
/media/cdrom0/Bin/Driver/USBKB11/Firmware/USBKS11G/ISW32N50.dll
/media/cdrom0/Bin/Driver/USBKB11/Firmware/USBKS11G/PCANDIS3.VXD
/media/cdrom0/Bin/Driver/USBKB11/Firmware/USBKS11G/SU010704.HEX
/media/cdrom0/Bin/Driver/USBKB11/Firmware/USBKS11G/Ver174.txt
/media/cdrom0/Bin/Driver/USBKB11/Firmware/USBKS11G/po010103.hex
/media/cdrom0/Bin/Driver/USBKB11/Firmware/USBKS11G/readme.txt
/media/cdrom0/Bin/Driver/USBKB11/Firmware/USBKS11G/winupdate.exe
/media/cdrom0/Bin/Driver/USBKB11/Firmware/USBKS11G/winupdate.ini
/media/cdrom0/Bin/Driver/USBKB11/NETUB11.inf
/media/cdrom0/Bin/Driver/USBKB11/NETUKB11.inf
/media/cdrom0/Bin/Driver/USBKB11/PRISMIOC.vxd
/media/cdrom0/Bin/Driver/USBKB11/WLIUKB11.sys
/media/cdrom0/Bin/Driver/USBKB11/Win2000
/media/cdrom0/Bin/Driver/USBKB11/Win2000/NETUB11.inf
/media/cdrom0/Bin/Driver/USBKB11/Win2000/NETUKB11.INF
/media/cdrom0/Bin/Driver/USBKB11/Win2000/WLIUKB11.sys
/media/cdrom0/Bin/Driver/USBKB11/Win2000/wliukb11.cat
/media/cdrom0/Bin/Driver/USBKB11/Win98
/media/cdrom0/Bin/Driver/USBKB11/Win98/NETUB11.inf
/media/cdrom0/Bin/Driver/USBKB11/Win98/NETUKB11.inf
/media/cdrom0/Bin/Driver/USBKB11/Win98/PRISMIOC.vxd
/media/cdrom0/Bin/Driver/USBKB11/Win98/WLIUKB11.sys
/media/cdrom0/Bin/Driver/USBKB11/Win98/wliukb11.cat
/media/cdrom0/Bin/Driver/USBKB11/WinMe
/media/cdrom0/Bin/Driver/USBKB11/WinMe/NETUB11.inf
/media/cdrom0/Bin/Driver/USBKB11/WinMe/NETUKB11.inf
/media/cdrom0/Bin/Driver/USBKB11/WinMe/PRISMIOC.vxd
/media/cdrom0/Bin/Driver/USBKB11/WinMe/WLIUKB11.sys
/media/cdrom0/Bin/Driver/USBKB11/WinMe/wliukb11.cat
/media/cdrom0/Bin/Driver/USBKB11/WinXP
/media/cdrom0/Bin/Driver/USBKB11/WinXP/NETUB11.inf
/media/cdrom0/Bin/Driver/USBKB11/WinXP/NETUKB11.INF
/media/cdrom0/Bin/Driver/USBKB11/WinXP/WLIUKB11.sys
/media/cdrom0/Bin/Driver/USBKB11/WinXP/wliukb11.cat
/media/cdrom0/Bin/Driver/USBKB11/wliukb11.cat
/media/cdrom0/Bin/Driver/USBL11
/media/cdrom0/Bin/Driver/USBL11/NETUSB11.INF
/media/cdrom0/Bin/Driver/USBL11/WAMEL51.DLL
/media/cdrom0/Bin/Driver/USBL11/WCMEL51.EXE
/media/cdrom0/Bin/Driver/USBL11/WIMEL51.DLL
/media/cdrom0/Bin/Driver/USBL11/WIN2000
/media/cdrom0/Bin/Driver/USBL11/WIN2000/NETUSB2K.INF
/media/cdrom0/Bin/Driver/USBL11/WIN2000/WAMEL51B.DLL
/media/cdrom0/Bin/Driver/USBL11/WIN2000/WCMEL51B.EXE
/media/cdrom0/Bin/Driver/USBL11/WIN2000/WDMEL51B.DLL
/media/cdrom0/Bin/Driver/USBL11/WIN2000/WLMEL51B.SYS
/media/cdrom0/Bin/Driver/USBL11/WIN2000/wlmel51b.cat
/media/cdrom0/Bin/Driver/USBL11/WINXP
/media/cdrom0/Bin/Driver/USBL11/WINXP/WAMEL51B.DLL
/media/cdrom0/Bin/Driver/USBL11/WINXP/WCMEL51B.EXE
/media/cdrom0/Bin/Driver/USBL11/WINXP/WDMEL51B.DLL
/media/cdrom0/Bin/Driver/USBL11/WINXP/WLMEL51B.INF
/media/cdrom0/Bin/Driver/USBL11/WINXP/WLMEL51B.SYS
/media/cdrom0/Bin/Driver/USBL11/WLMEL51.SYS
/media/cdrom0/Bin/Driver/USBL11/WUMEL51.VXD
/media/cdrom0/Bin/Driver/USBL11/Win98
/media/cdrom0/Bin/Driver/USBL11/Win98/NETUSB11.INF
/media/cdrom0/Bin/Driver/USBL11/Win98/WAMEL51.DLL
/media/cdrom0/Bin/Driver/USBL11/Win98/WCMEL51.EXE
/media/cdrom0/Bin/Driver/USBL11/Win98/WIMEL51.DLL
/media/cdrom0/Bin/Driver/USBL11/Win98/WLMEL51.SYS
/media/cdrom0/Bin/Driver/USBL11/Win98/WUMEL51.VXD
/media/cdrom0/Bin/Driver/USBL11/WinMe
/media/cdrom0/Bin/Driver/USBL11/WinMe/NETUSB11.INF
/media/cdrom0/Bin/Driver/USBL11/WinMe/WAMEL51.DLL
/media/cdrom0/Bin/Driver/USBL11/WinMe/WCMEL51.EXE
/media/cdrom0/Bin/Driver/USBL11/WinMe/WIMEL51.DLL
/media/cdrom0/Bin/Driver/USBL11/WinMe/WLMEL51.SYS
/media/cdrom0/Bin/Driver/USBL11/WinMe/WUMEL51.VXD
/media/cdrom0/Bin/Driver/Us
/media/cdrom0/Bin/Driver/Us/LAUNCHER.INI
/media/cdrom0/Bin/Driver/Us/RESOURCES
/media/cdrom0/Bin/Driver/Us/RESOURCES/LAUNCHER_US.dll
/media/cdrom0/Bin/Driver/Us/RESOURCES/SETUP_US.DLL
/media/cdrom0/Bin/Driver/Ver870.txt
/media/cdrom0/Bin/Driver/bufadpt.sys
/media/cdrom0/Bin/Driver/bufadpt.vxd
/media/cdrom0/Bin/Driver/bufadptn.sys
/media/cdrom0/Bin/Driver/bufsupp.dll
/media/cdrom0/Bin/Driver/gpl.txt
/media/cdrom0/Bin/Driver/insteng.dll
/media/cdrom0/Bin/Driver/instjp.dll
/media/cdrom0/Bin/Driver/license.txt
/media/cdrom0/Bin/Driver/microsoft
/media/cdrom0/Bin/Driver/microsoft/WindowsXP-KB822603-x86-ENU.exe
/media/cdrom0/Bin/Driver/odSupp_M.dll
/media/cdrom0/Bin/Driver/readme.txt
/media/cdrom0/Bin/Driver/rebothtm.exe
/media/cdrom0/Bin/Get_adobe_reader.gif
/media/cdrom0/Bin/MANUAL
/media/cdrom0/Bin/MANUAL/AdbeRdr705_enu_full.exe
/media/cdrom0/Bin/MANUAL/MANUAL.EXE
/media/cdrom0/Bin/MDRIVER
/media/cdrom0/Bin/MDRIVER/DEVREMOVE.exe
/media/cdrom0/Bin/MDRIVER/DEVREMOVE.ini
/media/cdrom0/Bin/MDRIVER/DelDev16.dll
/media/cdrom0/Bin/MDRIVER/Mdriver.ini
/media/cdrom0/Bin/MDRIVER/mdriver.exe
/media/cdrom0/Bin/Us
/media/cdrom0/Bin/Us/LAUNCHER.INI
/media/cdrom0/Bin/Us/MANUAL
/media/cdrom0/Bin/Us/MANUAL/MANUAL.INI
/media/cdrom0/Bin/Us/MANUAL/WHRG54S
/media/cdrom0/Bin/Us/MANUAL/WHRG54S/WHR-G54S-User.pdf
/media/cdrom0/Bin/Us/MANUAL/WHRHPAG108
/media/cdrom0/Bin/Us/MANUAL/WHRHPAG108/WHR-HP-AG108-Manual.pdf
/media/cdrom0/Bin/Us/MANUAL/WLA2G54C
/media/cdrom0/Bin/Us/MANUAL/WLA2G54C/WLA2G54C_Users.pdf
/media/cdrom0/Bin/Us/MANUAL/WLA2G54L
/media/cdrom0/Bin/Us/MANUAL/WLA2G54L/WLA2-G54L_Manual.pdf
/media/cdrom0/Bin/Us/MANUAL/WLICBAG300N
/media/cdrom0/Bin/Us/MANUAL/WLICBAG300N/WLI-CB-AG300N_manual.pdf
/media/cdrom0/Bin/Us/MANUAL/WLICBG240
/media/cdrom0/Bin/Us/MANUAL/WLICBG240/WLI-CB-G240_QSG.pdf
/media/cdrom0/Bin/Us/MANUAL/WLICBG240/WLICBG240-Manual.pdf
/media/cdrom0/Bin/Us/MANUAL/WLICBG300N
/media/cdrom0/Bin/Us/MANUAL/WLICBG300N/WLICBG300N-Manual.pdf
/media/cdrom0/Bin/Us/MANUAL/WLIPCIG300N
/media/cdrom0/Bin/Us/MANUAL/WLIPCIG300N/WLIPCIG300N-Manual.pdf
/media/cdrom0/Bin/Us/MANUAL/WLIU2AG108HP
/media/cdrom0/Bin/Us/MANUAL/WLIU2AG108HP/WLI-U2-AG108HP_manual.pdf
/media/cdrom0/Bin/Us/MANUAL/WLIU2G300N
/media/cdrom0/Bin/Us/MANUAL/WLIU2G300N/WLI-U2-G300N_Manual.pdf
/media/cdrom0/Bin/Us/MANUAL/WYRG54
/media/cdrom0/Bin/Us/MANUAL/WYRG54/WYR-G54_User_Manual2.pdf
/media/cdrom0/Bin/Us/MANUAL/WZRG108
/media/cdrom0/Bin/Us/MANUAL/WZRG108/WZR-G108-User.pdf
/media/cdrom0/Bin/Us/MANUAL/WZRG240
/media/cdrom0/Bin/Us/MANUAL/WZRG240/WZRG240-Manual.pdf
/media/cdrom0/Bin/Us/MANUAL/WZRG300N
/media/cdrom0/Bin/Us/MANUAL/WZRG300N/WZRG300N-Manual.pdf
/media/cdrom0/Bin/Us/MANUAL/WZRRSG54
/media/cdrom0/Bin/Us/MANUAL/WZRRSG54/WZR-Manual_EU2.pdf
/media/cdrom0/Bin/Us/MANUAL/Whrhpg54
/media/cdrom0/Bin/Us/MANUAL/Whrhpg54/WHR-HP-G54-User.pdf
/media/cdrom0/Bin/Us/MANUAL/wbmrg54
/media/cdrom0/Bin/Us/MANUAL/wbmrg54/WBMR-G54_USER.pdf
/media/cdrom0/Bin/Us/MANUAL/wli2cbg54l
/media/cdrom0/Bin/Us/MANUAL/wli2cbg54l/WLI2-CB-G54L_Manual.pdf
/media/cdrom0/Bin/Us/MANUAL/wli2pcig54
/media/cdrom0/Bin/Us/MANUAL/wli2pcig54/WLI2PCIG54_Manual.pdf
/media/cdrom0/Bin/Us/MANUAL/wli2pcig54s
/media/cdrom0/Bin/Us/MANUAL/wli2pcig54s/WLI2PCIG54SManual.pdf
/media/cdrom0/Bin/Us/MANUAL/wli2pcig54s/WLI2PCIG54SQSG.pdf
/media/cdrom0/Bin/Us/MANUAL/wli2usb2g54
/media/cdrom0/Bin/Us/MANUAL/wli2usb2g54/WLI2-USB-G54_Manual.pdf
/media/cdrom0/Bin/Us/MANUAL/wlicbag108hp
/media/cdrom0/Bin/Us/MANUAL/wlicbag108hp/WLI-CB-AG108HP_Manual.pdf
/media/cdrom0/Bin/Us/MANUAL/wlicbg108
/media/cdrom0/Bin/Us/MANUAL/wlicbg108/WLI-CB-G108_User.pdf
/media/cdrom0/Bin/Us/MANUAL/wlicbg54hp
/media/cdrom0/Bin/Us/MANUAL/wlicbg54hp/WLI-CB-G54HP-User.pdf
/media/cdrom0/Bin/Us/MANUAL/wlicbg54s
/media/cdrom0/Bin/Us/MANUAL/wlicbg54s/WLICBG54SManual.pdf
/media/cdrom0/Bin/Us/MANUAL/wlicbg54s/WLICBG54SQSG.pdf
/media/cdrom0/Bin/Us/MANUAL/wliu2kg125s
/media/cdrom0/Bin/Us/MANUAL/wliu2kg125s/WLI-U2-KG125S_manual.pdf
/media/cdrom0/Bin/Us/MANUAL/wliu2kg54
/media/cdrom0/Bin/Us/MANUAL/wliu2kg54/WLI-U2-KG54_ManV2.pdf
/media/cdrom0/Bin/Us/MANUAL/wliu2kg54/WLI2-U2-KG54-AI_User_Manual.pdf
/media/cdrom0/Bin/Us/RESOURCES
/media/cdrom0/Bin/Us/RESOURCES/MANUAL_US.DLL
/media/cdrom0/Bin/demo32.exe
/media/cdrom0/Bin/demo32.exe.manifest
/media/cdrom0/Setup.exe
/media/cdrom0/Setup.exe.manifest
/media/cdrom0/Setup.ini
/media/cdrom0/autorun.inf
/media/KINGSTON
/media/KINGSTON/dotnetfx.exe
/media/KINGSTON/FOUND.000
/media/KINGSTON/FOUND.000/FILE0000.CHK
/media/KINGSTON/FOUND.000/FILE0001.CHK
/media/KINGSTON/linuxcoding.txt
/media/.hal-mtab-lock
/media/cdrom
/media/floppy0

```

Which lead me to the next bit of coding because I should have replaced the airnavi.. with cdrom0

So far I done the following:

```

ubuntu@UBUNTU-PC:~$ find /media/cdrom -iname '*sys'
ubuntu@UBUNTU-PC:~$ find /media/cdrom0 -iname '*sys'
/media/cdrom0/Bin/ClientMgr3/bwsvc/bufadpt.sys
/media/cdrom0/Bin/ClientMgr3/bwsvc/bufadptn.sys
/media/cdrom0/Bin/ClientMgr3/sys
/media/cdrom0/Bin/Driver/2CBG54L/i2220.sys
/media/cdrom0/Bin/Driver/2CBG54L/i2220nta.sys
/media/cdrom0/Bin/Driver/2CBG54L/i2220ntx.sys
/media/cdrom0/Bin/Driver/2USB2G54/PRISMA02.sys
/media/cdrom0/Bin/Driver/2USB2G54/WIN2000/PRISMA02.sys
/media/cdrom0/Bin/Driver/CBAG108/cbag108.sys
/media/cdrom0/Bin/Driver/CBAG300N/ag300n3.sys
/media/cdrom0/Bin/Driver/CBAG300N/ag300n5.sys
/media/cdrom0/Bin/Driver/CBAG54L/ar5211.sys
/media/cdrom0/Bin/Driver/CBAG54L/ar52119x.sys
/media/cdrom0/Bin/Driver/CBAMG54/amg54.sys
/media/cdrom0/Bin/Driver/CBAMG54/amg549x.sys
/media/cdrom0/Bin/Driver/CBB11/Win2000/rtl8180.sys
/media/cdrom0/Bin/Driver/CBB11/WinMe/rtl8180.sys
/media/cdrom0/Bin/Driver/CBB11/WinXP/rtl8180.sys
/media/cdrom0/Bin/Driver/CBG108/wnihdd50.sys
/media/cdrom0/Bin/Driver/CBG108/wnihdd51.sys
/media/cdrom0/Bin/Driver/CBG240/tmimo30P.sys
/media/cdrom0/Bin/Driver/CBG240/tmimo31P.sys
/media/cdrom0/Bin/Driver/CBG300N/cbg300n.sys
/media/cdrom0/Bin/Driver/CBG54/WIN2000/CBG54.sys
/media/cdrom0/Bin/Driver/CBG54/WIN9X/CBG54.sys
/media/cdrom0/Bin/Driver/CBG54L/win2000/tnet1130.sys
/media/cdrom0/Bin/Driver/CBG54L/win98/tnet1130.sys
/media/cdrom0/Bin/Driver/CBG54L/winxp/tnet1130.sys
/media/cdrom0/Bin/Driver/CFS11G/WIN2000/WLIS11.sys
/media/cdrom0/Bin/Driver/CFS11G/WINXP/WLIS11.sys
/media/cdrom0/Bin/Driver/CFS11G/WLIS11.sys
/media/cdrom0/Bin/Driver/ESSIDSET.sys
/media/cdrom0/Bin/Driver/PCIL11/WINNT/WLIL11.sys
/media/cdrom0/Bin/Driver/PCIL11/WLIL11.sys
/media/cdrom0/Bin/Driver/PCIOP/WIN2000/WLIPCIK.SYS
/media/cdrom0/Bin/Driver/PCIOP/WLIPCI.SYS
/media/cdrom0/Bin/Driver/PCMS11/WIN2000/WLIS11.sys
/media/cdrom0/Bin/Driver/PCMS11/WIN95/WLIS11.SYS
/media/cdrom0/Bin/Driver/PCMS11/WINXP/WLIS11.sys
/media/cdrom0/Bin/Driver/PCMS11/WLIS11.sys
/media/cdrom0/Bin/Driver/PCMS11/Win98/WLIS11.sys
/media/cdrom0/Bin/Driver/PCMS11/WinMe/WLIS11.sys
/media/cdrom0/Bin/Driver/Pcml11/WIN2000/WLMEL48B.SYS
/media/cdrom0/Bin/Driver/Pcml11/WINNT/WLIL11.SYS
/media/cdrom0/Bin/Driver/Pcml11/WINXP/WLAGS48B.SYS
/media/cdrom0/Bin/Driver/Pcml11/WLIL11.SYS
/media/cdrom0/Bin/Driver/Pcml11/WLMEL41.SYS
/media/cdrom0/Bin/Driver/Pcml11/WLMEL48.SYS
/media/cdrom0/Bin/Driver/Pcml11/Win95/WLIL11.SYS
/media/cdrom0/Bin/Driver/Pcml11/Win95/WLMEL41.SYS
/media/cdrom0/Bin/Driver/Pcml11/Win95/WLMEL48.SYS
/media/cdrom0/Bin/Driver/Pcml11/Win98/WLIL11.SYS
/media/cdrom0/Bin/Driver/Pcml11/Win98/WLMEL41.SYS
/media/cdrom0/Bin/Driver/Pcml11/Win98/WLMEL48.SYS
/media/cdrom0/Bin/Driver/Pcml11/WinMe/WLIL11.SYS
/media/cdrom0/Bin/Driver/Pcml11/WinMe/WLMEL41.SYS
/media/cdrom0/Bin/Driver/Pcml11/WinMe/WLMEL48.SYS
/media/cdrom0/Bin/Driver/U2G300N/U2G300N3.sys
/media/cdrom0/Bin/Driver/U2G300N/U2G300N5.sys
/media/cdrom0/Bin/Driver/U2KAMG54/Win2000/ar5523.sys
/media/cdrom0/Bin/Driver/U2KAMG54/Win2000/athfmwdl.sys
/media/cdrom0/Bin/Driver/U2KAMG54/Win9x/ar55239x.sys
/media/cdrom0/Bin/Driver/U2KAMG54/Win9x/athfmwdl.sys
/media/cdrom0/Bin/Driver/U2KG125S/RNDISMP.sys
/media/cdrom0/Bin/Driver/U2KG125S/RNDISMPK.sys
/media/cdrom0/Bin/Driver/U2KG125S/usb8023.sys
/media/cdrom0/Bin/Driver/U2KG125S/usb8023k.sys
/media/cdrom0/Bin/Driver/U2KG54/Win2000/AIFILT.sys
/media/cdrom0/Bin/Driver/U2KG54/Win2000/U2KG54.sys
/media/cdrom0/Bin/Driver/U2KG54/Win2000/bfaifilt.sys
/media/cdrom0/Bin/Driver/U2KG54/Win98/AIFILT.sys
/media/cdrom0/Bin/Driver/U2KG54/Win98/U2KG5498.sys
/media/cdrom0/Bin/Driver/U2KG54/Win98/bfaifilt.sys
/media/cdrom0/Bin/Driver/U2KG54/WinME/AIFILT.sys
/media/cdrom0/Bin/Driver/U2KG54/WinME/U2KG5498.sys
/media/cdrom0/Bin/Driver/U2KG54/WinME/bfaifilt.sys
/media/cdrom0/Bin/Driver/USBG54/RNDISMPK.sys
/media/cdrom0/Bin/Driver/USBG54/bwcdrv.sys
/media/cdrom0/Bin/Driver/USBG54/rndismpm.sys
/media/cdrom0/Bin/Driver/USBG54/rndismpw.sys
/media/cdrom0/Bin/Driver/USBG54/usb8023k.sys
/media/cdrom0/Bin/Driver/USBG54/usb8023m.sys
/media/cdrom0/Bin/Driver/USBG54/usb8023w.sys
/media/cdrom0/Bin/Driver/USBKB11/Firmware/USBKS11G/ISLNDIS4.sys
/media/cdrom0/Bin/Driver/USBKB11/Firmware/USBKS11G/ISLNDIS5.sys
/media/cdrom0/Bin/Driver/USBKB11/WLIUKB11.sys
/media/cdrom0/Bin/Driver/USBKB11/Win2000/WLIUKB11.sys
/media/cdrom0/Bin/Driver/USBKB11/Win98/WLIUKB11.sys
/media/cdrom0/Bin/Driver/USBKB11/WinMe/WLIUKB11.sys
/media/cdrom0/Bin/Driver/USBKB11/WinXP/WLIUKB11.sys
/media/cdrom0/Bin/Driver/USBL11/WIN2000/WLMEL51B.SYS
/media/cdrom0/Bin/Driver/USBL11/WINXP/WLMEL51B.SYS
/media/cdrom0/Bin/Driver/USBL11/WLMEL51.SYS
/media/cdrom0/Bin/Driver/USBL11/Win98/WLMEL51.SYS
/media/cdrom0/Bin/Driver/USBL11/WinMe/WLMEL51.SYS
/media/cdrom0/Bin/Driver/bufadpt.sys
/media/cdrom0/Bin/Driver/bufadptn.sys
ubuntu@UBUNTU-PC:

```

However I'm stuck now, what do I do next?

Thanks nixscripter, all your help is much appreciated buddy.

---

### Post by nixscripter on 2008-08-26
Man, that's a lot of sys files! Just guessing, it looks like some of those are drivers, some are client files used by the windows wireless junk. I thought there would be a lot fewer of them.

What you have to do is use ndiswrapper to recognize them. This would best be done with INI files. Run that other search I suggested, and have ndiswrapper look at them one at a time: ```
sudo ndiswrapper -i filename.inf
```

If you have the right one, it will say something like: 
```
**bcmXXXX**: driver installed
device (1**234:CDEF**) present
```

Where the first string is the name of the INI file, and the second is the PCI ID of your card. You can determine the PCI ID of your card by typing: ```
lspci -nn
``` and looking for it in the list.

I'm afraid it's down to trial and error from here, depending on how many of those SYS files also have INI files. I would suggest, however, restricting your search to WinXP and Win2k drivers.

Hope this helps.

---

### Post by jacksparrow1 on 2008-08-27
> **nixscripter said:**
> What you have to do is use ndiswrapper to recognize them. This would best be done with INI files. **Run that other search I suggested, and have ndiswrapper look at them one at a time**: .

Thanks buddy, so I have to try each INI file one by one?

Just one question which code are you talking about?

Shall I run the following?

```

find /media/cdrom0-iname '*ini'

```

And then with each Ini file found shall I run the following coding?

```
sudo ndiswrapper -i filename.inf
```

Thanks

---

### Post by nixscripter on 2008-08-28
Right (assuming you meant a space between cdrom0 and -iname above).

---

### Post by jacksparrow1 on 2008-09-01
Hi,

I dont understand what I've done wrong now?

Can you spot it out?

```

ubuntu@UBUNTU-PC:~$ find /media/cdrom0 -iname '*ini' 
/media/cdrom0/Bin/ClientMgr3/Setup.ini 
/media/cdrom0/Bin/ClientMgr3/Skin/ProfileIcons/descryption.ini 
/media/cdrom0/Bin/ClientMgr3/Skinjp.ini 
/media/cdrom0/Bin/ClientMgr3/VerInfo.ini 
/media/cdrom0/Bin/ClientMgr3/aoss/AOSS.ini 
/media/cdrom0/Bin/ClientMgr3/bwsvc/BWSVC.ini 
/media/cdrom0/Bin/ClientMgr3/bwsvc/BWSVC_Install.INI 
/media/cdrom0/Bin/Driver/ABRinst/Setup.ini 
/media/cdrom0/Bin/Driver/CBG54/ABCfg.ini 
/media/cdrom0/Bin/Driver/CFS11G/BE500/Setup.ini 
/media/cdrom0/Bin/Driver/CFS11G/WLICFS11.INI 
/media/cdrom0/Bin/Driver/INST.INI 
/media/cdrom0/Bin/Driver/LAUNCHER.INI 
/media/cdrom0/Bin/Driver/MDRIVER/DEVREMOVE.ini 
/media/cdrom0/Bin/Driver/MDRIVER/Mdriver.ini 
/media/cdrom0/Bin/Driver/USBKB11/Firmware/USBKS11G/winupdate.ini 
/media/cdrom0/Bin/Driver/Us/LAUNCHER.INI 
/media/cdrom0/Bin/MDRIVER/DEVREMOVE.ini 
/media/cdrom0/Bin/MDRIVER/Mdriver.ini 
/media/cdrom0/Bin/Us/LAUNCHER.INI 
/media/cdrom0/Bin/Us/MANUAL/MANUAL.INI 
/media/cdrom0/Setup.ini 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i setup.inf 
[sudo] password for ubuntu:  
couldn't open setup.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i descryption.inf 
couldn't open descryption.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i Setup.inf 
couldn't open Setup.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i Skinjp.inf 
couldn't open Skinjp.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i VerInfo.inf 
couldn't open VerInfo.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i AOSS.inf 
couldn't open AOSS.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i BWSVC.inf 
couldn't open BWSVC.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i BWSVC_Install.inf 
couldn't open BWSVC_Install.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i Setup.inf 
couldn't open Setup.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i ABCfg.inf 
couldn't open ABCfg.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i Setup.inf 
couldn't open Setup.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i WLICFS11.inf 
couldn't open WLICFS11.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i INST.inf 
couldn't open INST.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i LAUNCHER.inf 
couldn't open LAUNCHER.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i DEVREMOVE.inf 
couldn't open DEVREMOVE.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i Mdriver.inf 
couldn't open Mdriver.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i winupdate.inf 
couldn't open winupdate.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i LAUNCHER.inf 
couldn't open LAUNCHER.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i DEVREMOVE.inf 
couldn't open DEVREMOVE.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i Mdriver.inf 
couldn't open Mdriver.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i LAUNCHER.inf 
couldn't open LAUNCHER.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i MANUAL.inf 
couldn't open MANUAL.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i Setup.inf 
couldn't open Setup.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$  


```

Thanks

---

### Post by nixscripter on 2008-09-01
Oh, you have to type the whole path to the file. For example if you have the file ```
/media/cdrom0/Bin/Driver/CBG54/ABCfg.ini
```

then you would have to

```
sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBG54/ABCfg.ini
```

And by the way, that was a typo on my part. Rather than *ini in the find, you should use *inf. I would also start with the ones in **/media/cdrom0/Bin/Driver**.

---

### Post by jacksparrow1 on 2008-09-02
Will give it a go, thanks

---

### Post by jacksparrow1 on 2008-09-02
Hi,

I done what you said but I didn't get that 

'Driver installed.....'

Below is all the coding I have:

```

ubuntu@UBUNTU-PC:~$ find /media/cdrom0 -iname '*inf' 
/media/cdrom0/Bin/Driver/2CBG54L/NET2G54L.inf 
/media/cdrom0/Bin/Driver/2USB2G54/NETU2G54.inf 
/media/cdrom0/Bin/Driver/2USB2G54/WIN2000/NETU2G54.inf 
/media/cdrom0/Bin/Driver/CBAG108/netag108.inf 
/media/cdrom0/Bin/Driver/CBAG300N/netag3n.inf 
/media/cdrom0/Bin/Driver/CBAG54L/netag54l.inf 
/media/cdrom0/Bin/Driver/CBAMG54/netamg54.inf 
/media/cdrom0/Bin/Driver/CBB11/Win2000/NETCBB11.INF 
/media/cdrom0/Bin/Driver/CBB11/WinMe/NETCBB11.INF 
/media/cdrom0/Bin/Driver/CBB11/WinXP/NETCBB11.INF 
/media/cdrom0/Bin/Driver/CBG108/Netg108.inf 
/media/cdrom0/Bin/Driver/CBG240/netcb240.inf 
/media/cdrom0/Bin/Driver/CBG300N/netg300n.inf 
/media/cdrom0/Bin/Driver/CBG54/WIN2000/net2pg54.inf 
/media/cdrom0/Bin/Driver/CBG54/WIN2000/netcbg54.inf 
/media/cdrom0/Bin/Driver/CBG54/WIN2000/netg54s.inf 
/media/cdrom0/Bin/Driver/CBG54/WIN9X/net2pg54.inf 
/media/cdrom0/Bin/Driver/CBG54/WIN9X/netcbg54.inf 
/media/cdrom0/Bin/Driver/CBG54/WIN9X/netg54s.inf 
/media/cdrom0/Bin/Driver/CBG54L/win2000/NETCG54L.INF 
/media/cdrom0/Bin/Driver/CBG54L/win98/NETCG54L.INF 
/media/cdrom0/Bin/Driver/CBG54L/winxp/NETCG54L.INF 
/media/cdrom0/Bin/Driver/CFS11G/NETS11.inf 
/media/cdrom0/Bin/Driver/CFS11G/WIN2000/NETS11.inf 
/media/cdrom0/Bin/Driver/CFS11G/WINXP/NETS11.inf 
/media/cdrom0/Bin/Driver/DISKINFO.INF 
/media/cdrom0/Bin/Driver/PCIL11/WINNT/oemsetup.inf 
/media/cdrom0/Bin/Driver/PCIL11/netwli11.inf 
/media/cdrom0/Bin/Driver/PCIL11/win2000/netl112k.inf 
/media/cdrom0/Bin/Driver/PCIOP/WIN2000/WLIPCIK.INF 
/media/cdrom0/Bin/Driver/PCIOP/WIN95/WLIPCI.INF 
/media/cdrom0/Bin/Driver/PCIOP/WIN95R2/WLIPCI.INF 
/media/cdrom0/Bin/Driver/PCIOP/WIN98/WLIPCI.INF 
/media/cdrom0/Bin/Driver/PCIOP/WinMe/WLIPCI.INF 
/media/cdrom0/Bin/Driver/PCMS11/NETS11.inf 
/media/cdrom0/Bin/Driver/PCMS11/WIN2000/NETS11.inf 
/media/cdrom0/Bin/Driver/PCMS11/WIN95/NETS11.inf 
/media/cdrom0/Bin/Driver/PCMS11/WINXP/NETS11.inf 
/media/cdrom0/Bin/Driver/PCMS11/Win98/NETS11.inf 
/media/cdrom0/Bin/Driver/PCMS11/WinMe/NETS11.inf 
/media/cdrom0/Bin/Driver/Pcml11/NETL11GP.INF 
/media/cdrom0/Bin/Driver/Pcml11/WIN2000/Netl11.inf 
/media/cdrom0/Bin/Driver/Pcml11/WINNT/OEMSETUP.INF 
/media/cdrom0/Bin/Driver/Pcml11/WINXP/WLAGS48B.INF 
/media/cdrom0/Bin/Driver/Pcml11/Win95/NETL11GP.INF 
/media/cdrom0/Bin/Driver/Pcml11/Win98/NETL11GP.INF 
/media/cdrom0/Bin/Driver/Pcml11/WinMe/NETL11GP.INF 
/media/cdrom0/Bin/Driver/U2G300N/NETUG300.inf 
/media/cdrom0/Bin/Driver/U2KAMG54/Win2000/Netkamgl.inf 
/media/cdrom0/Bin/Driver/U2KAMG54/Win2000/netkamg.inf 
/media/cdrom0/Bin/Driver/U2KAMG54/Win9x/netkamg.inf 
/media/cdrom0/Bin/Driver/U2KAMG54/Win9x/netkamgl.inf 
/media/cdrom0/Bin/Driver/U2KG125S/netg125s.inf 
/media/cdrom0/Bin/Driver/U2KG54/Win2000/NETU2KG.INF 
/media/cdrom0/Bin/Driver/U2KG54/Win98/NETU2KG.INF 
/media/cdrom0/Bin/Driver/U2KG54/WinME/NETU2KG.INF 
/media/cdrom0/Bin/Driver/USBG54/netbwc2k.inf 
/media/cdrom0/Bin/Driver/USBG54/netbwc98.inf 
/media/cdrom0/Bin/Driver/USBG54/netusg54.inf 
/media/cdrom0/Bin/Driver/USBKB11/NETUB11.inf 
/media/cdrom0/Bin/Driver/USBKB11/NETUKB11.inf 
/media/cdrom0/Bin/Driver/USBKB11/Win2000/NETUB11.inf 
/media/cdrom0/Bin/Driver/USBKB11/Win2000/NETUKB11.INF 
/media/cdrom0/Bin/Driver/USBKB11/Win98/NETUB11.inf 
/media/cdrom0/Bin/Driver/USBKB11/Win98/NETUKB11.inf 
/media/cdrom0/Bin/Driver/USBKB11/WinMe/NETUB11.inf 
/media/cdrom0/Bin/Driver/USBKB11/WinMe/NETUKB11.inf 
/media/cdrom0/Bin/Driver/USBKB11/WinXP/NETUB11.inf 
/media/cdrom0/Bin/Driver/USBKB11/WinXP/NETUKB11.INF 
/media/cdrom0/Bin/Driver/USBL11/NETUSB11.INF 
/media/cdrom0/Bin/Driver/USBL11/WIN2000/NETUSB2K.INF 
/media/cdrom0/Bin/Driver/USBL11/WINXP/WLMEL51B.INF 
/media/cdrom0/Bin/Driver/USBL11/Win98/NETUSB11.INF 
/media/cdrom0/Bin/Driver/USBL11/WinMe/NETUSB11.INF 
/media/cdrom0/autorun.inf 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/autorun.inf 
[sudo] password for ubuntu:  
couldn't find SourceDisksFiles section - continuing anyway... 
installing autorun ... 
couldn't get manufacturer section - installation may be incomplete 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/2USB2G54/WIN2000/NETU2G54.inf 
installing netu2g54 ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/2CBG54L/NET2G54L.inf 
installing net2g54l ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/2USB2G54/NETU2G54.inf 
driver netu2g54 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBAG108/netag108.inf 
installing netag108 ... 
forcing parameter MapRegisters from 256 to 64 
forcing parameter MapRegisters from 256 to 64 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBAG300N/netag3n.inf 
installing netag3n ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBAG54L/netag54l.inf 
installing netag54l ... 
forcing parameter MapRegisters from 256 to 64 
forcing parameter MapRegisters from 256 to 64 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBAMG54/netamg54.inf 
installing netamg54 ... 
forcing parameter MapRegisters from 256 to 64 
forcing parameter MapRegisters from 256 to 64 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBB11/Win2000/NETCBB11.INF 
installing netcbb11 ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBB11/WinMe/NETCBB11.INF 
driver netcbb11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBB11/WinXP/NETCBB11.INF 
driver netcbb11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBG108/Netg108.inf 
installing netg108 ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBG240/netcb240.inf 
installing netcb240 ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBG300N/netg300n.inf 
installing netg300n ... 
forcing parameter IBSSGMode from 0 to 2 
forcing parameter IBSSGMode from 0 to 2 
forcing parameter IBSSGMode from 0 to 2 
forcing parameter IBSSGMode from 0 to 2 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBG54/WIN2000/net2pg54.inf 
installing net2pg54 ... 
forcing parameter IBSSGMode from 0 to 2 
forcing parameter IBSSGMode from 0 to 2 
forcing parameter IBSSGMode from 0 to 2 
forcing parameter IBSSGMode from 0 to 2 
forcing parameter IBSSGMode from 0 to 2 
forcing parameter IBSSGMode from 0 to 2 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBG54/WIN2000/netcbg54.inf 
installing netcbg54 ... 
forcing parameter IBSSGMode from 0 to 2 
forcing parameter IBSSGMode from 0 to 2 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBG54/WIN2000/netg54s.inf 
installing netg54s ... 
forcing parameter IBSSGMode from 0 to 2 
forcing parameter IBSSGMode from 0 to 2 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBG54/WIN9X/net2pg54.inf 
driver net2pg54 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBG54/WIN9X/netcbg54.inf 
driver netcbg54 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBG54/WIN9X/netg54s.inf 
driver netg54s is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i media/cdrom0/Bin/Driver/CBG54L/win2000/NETCG54L.INF 
couldn't open media/cdrom0/Bin/Driver/CBG54L/win2000/NETCG54L.INF: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBG54L/win98/NETCG54L.INF 
installing netcg54l ... 
forcing parameter PrivacyMode from 0 to 2 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBG54L/winxp/NETCG54L.INF 
driver netcg54l is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CFS11G/NETS11.inf 
installing nets11 ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CFS11G/WIN2000/NETS11.inf 
driver nets11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CFS11G/WINXP/NETS11.inf 
driver nets11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/DISKINFO.INF 
couldn't find SourceDisksFiles section - continuing anyway... 
installing diskinfo ... 
couldn't get manufacturer section - installation may be incomplete 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/PCIL11/WINNT/oemsetup.inf 
couldn't find SourceDisksFiles section - continuing anyway... 
installing oemsetup ... 
couldn't get manufacturer section - installation may be incomplete 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/PCIL11/netwli11.inf 
installing netwli11 ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/PCIL11/win2000/netl112k.inf 
couldn't find SourceDisksFiles section - continuing anyway... 
installing netl112k ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/PCIOP/WIN2000/WLIPCIK.INF 
installing wlipcik ... 
couldn't find "pcmcia.sys" in "/media/cdrom0/Bin/Driver/PCIOP/WIN2000"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/media/cdrom0/Bin/Driver/PCIOP/WIN2000" - 
installation may be incomplete 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/PCIOP/WIN95/WLIPCI.INF 
couldn't find SourceDisksFiles section - continuing anyway... 
installing wlipci ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/PCIOP/WIN95R2/WLIPCI.INF 
driver wlipci is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/PCIOP/WIN98/WLIPCI.INF 
driver wlipci is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/PCIOP/WinMe/WLIPCI.INF 
driver wlipci is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/PCMS11/NETS11.inf 
driver nets11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/PCMS11/WIN2000/NETS11.inf 
driver nets11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/PCMS11/WIN95/NETS11.inf 
driver nets11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/PCMS11/WINXP/NETS11.inf 
driver nets11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/PCMS11/Win98/NETS11.inf 
driver nets11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/PCMS11/WinMe/NETS11.inf 
driver nets11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/Pcml11/NETL11GP.INF 
installing netl11gp ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/Pcml11/WIN2000/Netl11.inf 
installing netl11 ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/Pcml11/WINNT/OEMSETUP.INF 
driver oemsetup is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/Pcml11/WINXP/WLAGS48B.INF 
installing wlags48b ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/Pcml11/Win95/NETL11GP.INF 
driver netl11gp is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/Pcml11/Win98/NETL11GP.INF 
driver netl11gp is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/Pcml11/WinMe/NETL11GP.INF 
driver netl11gp is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/U2G300N/NETUG300.inf 
installing netug300 ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/U2KAMG54/Win2000/Netkamgl.inf 
installing netkamgl ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/U2KAMG54/Win2000/netkamg.inf 
installing netkamg ... 
forcing parameter MapRegisters from 256 to 64 
forcing parameter MapRegisters from 256 to 64 
forcing parameter MapRegisters from 256 to 64 
forcing parameter MapRegisters from 256 to 64 
forcing parameter MapRegisters from 256 to 64 
forcing parameter MapRegisters from 256 to 64 
forcing parameter MapRegisters from 256 to 64 
forcing parameter MapRegisters from 256 to 64 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/U2KAMG54/Win9x/netkamg.inf 
driver netkamg is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/U2KAMG54/Win9x/netkamgl.inf 
driver netkamgl is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/U2KG125S/netg125s.inf 
installing netg125s ... 
forcing parameter IBSSGMode from 0 to 2 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/U2KG125S/netg125s.inf 
driver netg125s is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/U2KG54/Win2000/NETU2KG.INF 
installing netu2kg ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/U2KG54/Win98/NETU2KG.INF 
driver netu2kg is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/U2KG54/WinME/NETU2KG.INF 
driver netu2kg is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBG54/netbwc2k.inf 
installing netbwc2k ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBG54/netbwc98.inf 
installing netbwc98 ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBG54/netusg54.inf 
installing netusg54 ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBKB11/NETUB11.inf 
installing netub11 ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBKB11/NETUKB11.inf 
installing netukb11 ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBKB11/Win2000/NETUB11.inf 
driver netub11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBKB11/Win2000/NETUKB11.INF 
driver netukb11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBKB11/Win98/NETUB11.inf 
driver netub11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBKB11/Win98/NETUKB11.inf 
driver netukb11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBKB11/WinMe/NETUB11.inf 
driver netub11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBKB11/WinMe/NETUKB11.inf 
driver netukb11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBKB11/WinXP/NETUB11.inf 
driver netub11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBKB11/WinXP/NETUKB11.INF 
driver netukb11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBL11/NETUSB11.INF 
installing netusb11 ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBL11/WIN2000/NETUSB2K.INF 
installing netusb2k ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBL11/WINXP/WLMEL51B.INF 
installing wlmel51b ... 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBL11/Win98/NETUSB11.INF 
driver netusb11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/Bin/Driver/USBL11/WinMe/NETUSB11.INF 
driver netusb11 is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -i /media/cdrom0/autorun.inf 
driver autorun is already installed 
ubuntu@UBUNTU-PC:~$  
driver autorun is already installed 
ubuntu@UBUNTU-PC:~$  
ubuntu@UBUNTU-PC:~$ lspci -nn 
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
00:04.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fb] (rev a1) 
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51PV [GeForce 6150] [10de:0240] (rev a2) 
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2) 
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a2) 
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a2) 
00:0a.2 RAM memory [0500]: nVidia Corporation MCP51 Memory Controller 0 [10de:0272] (rev a2) 
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a2) 
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a2) 
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev a1) 
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev a1) 
00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev a1) 
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2) 
00:10.2 Multimedia audio controller [0401]: nVidia Corporation MCP51 AC97 Audio Controller [10de:026b] (rev a2) 
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a1) 
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100] 
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101] 
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102] 
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103] 
04:08.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) 
ubuntu@UBUNTU-PC:~$  


```

Does this mean the driver has been installed? If it has could you tell me what the best way is to connect to my wireless network please?

Thanks for all your help, much appreciated.

---

### Post by nixscripter on 2008-09-02
Okay, it looks close enough. Now do:

```
sudo modprobe ndiswrapper
```

To load the module and then:

```
ifconfig -a
```

To see if any of them are actually driving the card. You should get another interface called wlan0, eth1, or something like that.

I'm not sure which module does it. You may also look at: ```
sudo ndiswrapper -l
``` to get a list and see which one is being used.

---

### Post by jacksparrow1 on 2008-09-03
Oh ok, I'm not sure if I've got it then because some of them say driver not installed:

```

ubuntu@UBUNTU-PC:~$ sudo modprobe ndiswrapper 
 [sudo] password for ubuntu:  
ubuntu@UBUNTU-PC:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:1c:25:36:69:92   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18 Base address:0x6000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1062 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1062 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:53100 (51.8 KB)  TX bytes:53100 (51.8 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:16:01:7d:ea:7e   
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-16-01-7D-EA-7E-00-00-00-00-00-00-00-00-00-00   
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
ubuntu@UBUNTU-PC:~$ sudo ndiswrapper -l 
autorun : invalid driver! 
diskinfo : invalid driver! 
net2g54l : driver installed 
net2pg54 : driver installed 
	device (14E4:4318) present (alternate driver: ssb) 
netag108 : driver installed 
netag3n : driver installed 
netag54l : driver installed 
netamg54 : driver installed 
netbwc2k : invalid driver! 
netbwc98 : invalid driver! 
netcb240 : driver installed 
netcbb11 : driver installed 
netcbg54 : driver installed 
netcg54l : driver installed 
netg108 : driver installed 
netg125s : invalid driver! 
netg300n : driver installed 
netg54s : driver installed 
	device (14E4:4318) present (alternate driver: ssb) 
netkamg : driver installed 
netkamgl : driver installed 
netl11 : invalid driver! 
netl112k : invalid driver! 
netl11gp : invalid driver! 
nets11 : invalid driver! 
netu2g54 : driver installed 
netu2kg : driver installed 
netub11 : driver installed 
netug300 : driver installed 
netukb11 : driver installed 
netusb11 : driver installed 
netusb2k : driver installed 
netusg54 : invalid driver! 
netwli11 : invalid driver! 
oemsetup : invalid driver! 
wlags48b : invalid driver! 
wlipci : invalid driver! 
wlipcik : driver installed 
wlmel51b : driver installed 
ubuntu@UBUNTU-PC:~$  


```

Thanks, again your help is much appreciated

---

### Post by nixscripter on 2008-09-03
I bet wlan0 is your wireless card. Try turning it on, going near a network and scanning for it:

```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```

If this works, then you can add ndiswrapper to the list of automatically loaded modules and reboot. Just create a file as root called **wireless** in the **/etc/modprobe.d** directory, and put the word "ndiswrapper" on the first line.

If you still get wlan0 after reboot, you can use the network manager applet to set up your connection.

---

### Post by jacksparrow1 on 2008-09-04
Hey

I tried what you suggested but it didn't work - my guess is that the driver did not instsall?

```

ubuntu@UBUNTU-PC:~$ sudo ifconfig wlan0 up 
 [sudo] password for ubuntu:  
SIOCSIFFLAGS: No such file or directory 
ubuntu@UBUNTU-PC:~$ sudo ifconfig eth0 up 
ubuntu@UBUNTU-PC:~$ sudo iwlist eth0 scan 
eth0      Interface doesn't support scanning. 
 
ubuntu@UBUNTU-PC:~$ sudo iwlist wlan0 scan 
wlan0     Interface doesn't support scanning : Network is down 
 
ubuntu@UBUNTU-PC:~$  


```

Am i correct?  Thanks

---

### Post by nixscripter on 2008-09-04
I'm not sure. What does this command say?

```
sudo lshw -C network
```

Look for "Wireless interface"

---

### Post by jacksparrow1 on 2008-09-06
Hi

I have the following 

```

ubuntu@UBUNTU-PC:~$ sudo lshw -C network 
  *-network                
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 8 
       bus info: pci@0000:04:08.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:16:01:7d:ea:7e 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 
ubuntu@UBUNTU-PC:~$  


```

Thanks

---

### Post by nixscripter on 2008-09-11
Sorry about the delay in replying. I've been busy lately.

Let me just make sure I've got everything straight. I'm going to sort of start over, but not quite.

I would guess, based on the CD listing, that the driver you want is this one: **/media/cdrom0/Bin/Driver/CBG54/WIN2000/netg54s.inf**

1. Reboot to clean up everything I told you to do before.

2. Put in the driver CD.

3. Load the driver into ndiswrapper: ```
sudo ndiswrapper -i /media/cdrom0/Bin/Driver/CBG54/WIN2000/netg54s.inf
```

3. Load the ndiswrapper module: ```
sudo modprobe ndiswrapper
```

4. Does the interface show up? It should:

```
iwconfig wlan0
```

If not, it might not be called wlan0 (I don't see why not, but my card doesn't do this right either). The way to check is to list all the cards: ```
ifconfig -a
``` and look for the MAC address listed as "hwaddr". According to what you posted, the address you should look for is **00:16:01:7d:ea:7e**. If that isn't in there, it's not working.

5. Assuming you can find it, try scanning. If it's not called wlan0, then change wlan0 in everything below to what it's called (eth1 or something like that).

```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```

If that doesn't work, then it's time for something more dramatic.

---

### Post by jacksparrow1 on 2008-09-11
Sorry but what do you mean when you say reboot?  Shall i install Ubuntu again or just restart my pc?

Thanks

---

### Post by sylindrical7 on 2008-09-14
i think the reboot means restart.. thanks for the info .. i also have that kind of adapter and i cant work with the internet.. i hope this could work.

---

### Post by nixscripter on 2008-09-18
Yes, reboot means restart.

Let me know if this works. A lot of people seem to have trouble with this card, and it would be nice if I knew I could fix it for someone.

---

### Post by regghen on 2009-03-22
I seem to have gotten this to work. I had the card inserted in the PCI slot next to my video card...I just moved it to the next available slot...and POW..instant ACCESS!!!

---

