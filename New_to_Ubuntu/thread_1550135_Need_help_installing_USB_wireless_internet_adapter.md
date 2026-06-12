---
title: "Need help installing USB wireless internet adapter WL-167G V3"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by l0ijoat on 2010-08-10
hey,
i've come to believe that the wireless card on this laptop is shot, so i bought an ASUS WL-167G V3 USB adapter hoping to get the wireless working. i'm very new to ubuntu/linux, i'm running ubuntu studio 10.4 and the readme that came with the the USB adapter does not make any sense to me. i don't know how to install the drivers, or where to start, i don't know what 'make' means. i've searched help forums for instructions on how to use makefiles and stuff like that and i've fussed around in the terminal for a while trying different things but to no avail. i've included the readme at the bottom, so hopefully someone can make sense of it. stuff like this is very frustrating, any help is much appreciated!
```
Release Date: 2009-0825, ver 0003 
RTL8192SU Linux driver
   --This driver supports RealTek rtl8192SU USB Wireless LAN NIC
     for
     2.6 kernel:
     Fedora Core 2/3/4/5, Debian 3.1, Mandrake 10.2/Mandriva 2006, 
     SUSE 9.3/10.1/10.2, Gentoo 3.1, Ubuntu 7.10/8.04, etc.
     2.4 kernel:
     Redhat 9.0/9.1

===============================================================================
				Component 
===============================================================================
The driver is composed of several parts:
	1. Firmare to make nic work
           1.1 firmare/RTL8192SU

	2. Module source code
	   2.1 ieee80211 
	   2.2 HAL/rtl8192u
	   2.3 wpa_supplicant-0.5.10 (User can download the latest version from 
	       internet also, but it is suggested to use default package contained
	       in the distribution because there should less compilation issue.)
	
	3. Script to build the modules
	   3.1 Makefile 

	4. Script to load/unload modules
	   4.1 wlan0up 
	   4.2 wlan0down 

	5. Script and configuration for DHCP
 	   5.1 wlan0dhcp
	   5.2 ifcfg-wlan0

	6. Example of supplicant configuration file:
	   6.1 wpa1.conf

	7. Script to run wpa_supplicant
	   7.1 runwpa

===============================================================================
				Installation 
===============================================================================
<<Method 1>>
Runing the scripts accomplish all operations including building up modules 
from the source code, installing driver to the kernel and starting up the nic.
	1. Build up the drivers from the source code
	  make

	2. Install the driver to the kernel
          make install
          reboot

	3. bring up wlan if nic is not brought up by GUI, such as NetworkManager
	  ifconfig wlan0 up 
	  Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to check your wlan interface name, 
                since it may change wlan0 to wlan1,etc.

<<Method 2>>
Or only load the driver module to kernel and start up nic.
	 1. Build up the drivers from the source code
	  make
         2. Copy firmware to /lib/firmware/ or /lib/firmware/(KERNEL_VERSION)/
            cp -rf firmware/RTL8192SU /lib/firmware
          or
            cp -rf firmware/RTL8192SU /lib/firmware/(KERNEL_VERSION)
          Note: This depends on whether (KERNEL_VERSION) subdirectory exists under /lib/firmware

	 3. Load driver module to kernel and start up nic.
	  ./wlan0up
          Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes out
                after run ./wlan0up, please run ./wlan0down first, then it should 
                be ok..
	  Note: If you see the message of "unkown symbol" during ./wlan0up, it
		is suggested to build driver by <<Method 1>>.

===============================================================================
				Set wireless lan MIBs 
===============================================================================
This driver uses Wireless Extension as an interface allowing you to set
Wireless LAN specific parameters.

Current driver supports "iwlist" to show the device status of nic
        iwlist wlan0 [parameters]
where
        parameter explaination      	[parameters]    
        -----------------------     	-------------   
        Show available chan and freq	freq / channel  
        Show and Scan BSS and IBSS 	scan[ning]          
        Show supported bit-rate         rate / bit[rate]        

For example:
	iwlist wlan0 channel
	iwlist wlan0 scan
	iwlist wlan0 rate

Driver also supports "iwconfig", manipulate driver private ioctls, to set
MIBs.

	iwconfig wlan0 [parameters] [val]
where
	parameter explaination      [parameters]        [val] constraints
        -----------------------     -------------        ------------------
        Connect to AP by address    ap              	[mac_addr]
        Set the essid, join (I)BSS  essid             	[essid]
        Set operation mode          mode                {Managed|Ad-hoc}
        Set keys and security mode  key/enc[ryption]    {N|open|restricted|off}

For example:
	iwconfig wlan0 ap XX:XX:XX:XX:XX:XX
	iwconfig wlan0 essid "ap_name"
	iwconfig wlan0 mode Ad-hoc
	iwconfig wlan0 essid "name" mode Ad-hoc
	iwconfig wlan0 key 0123456789 [2] open
	iwconfig wlan0 key off
	iwconfig wlan0 key restricted [3] 0123456789
        Note: Better to set these MIBS without GUI such as NetworkManager and be sure that our
              nic has been brought up before these settings. WEP key index 2-4 is not supportted by
              NetworkManager.

===============================================================================
				Getting IP address
===============================================================================
After start up the nic, the network needs to obtain an IP address before
transmit/receive data.
This can be done by setting the static IP via "ifconfig wlan0 IP_ADDRESS"
command, or using DHCP.

If using DHCP, setting steps is as below:
	(1)connect to an AP via "iwconfig" settings
		iwconfig wlan0 essid [name]	or
		iwconfig wlan0 ap XX:XX:XX:XX:XX:XX

	(2)run the script which run the dhclient
		./wlan0dhcp
           or 
		dhcpcd wlan0
              	(Some network admins require that you use the
              	hostname and domainname provided by the DHCP server.
              	In that case, use 
		dhcpcd -HD wlan0)
		

===============================================================================
			WPAPSK/WPA2PSK 
===============================================================================
	Wpa_supplicant helps to secure wireless connection with the protection of 
WPAPSK/WPA2PSK mechanism. 

	If the version of Wireless Extension in your system is equal or larger than 18, 
WEXT driver interface is recommended. Otherwise, IPW driver interface is advised.  
	Note: Wireless Extension is defined us "#define WIRELESS_EXT" in Kernel
	Note: To check the version of wireless extension, please type "iwconfig -v"


 	If IPW driver interface is used, it us suggested to follow the steps from 1 to 6. 
If wpa_supplicant has been installed in your system, only steps 5 and 6 are required 
to be executed for WEXT driver interface.

	To see detailed description for driver interface and wpa_supplicant, please type
"man wpa_supplicant".  
	
	(1)Download latetest source code for wpa supplicant or use wpa_supplicant-0.5.10 
	   attached in this package. (It is suggested to use default package contained
           in the distribution because there should less compilation issue.)

	   Unpack source code of WPA supplicant:

	  tar -zxvf wpa_supplicant-0.5.10.tar.gz (e.g.) 
	  cd wpa_supplicant-0.5.10
	
	(2)Create .config file:
	  cp defconfig .config
	
	(3)Edit .config file, uncomment the following line if ipw driver interface 
	   will be applied:
	  #CONFIG_DRIVER_IPW=y.
		
	(4)Build and install WPA supplicant:
	  make
	  cp wpa_cli wpa_supplicant /usr/local/bin	
	
	NOTE:
	 1. If make error for lack of <include/md5.h>, install the openssl lib(two ways):
	  (1) Install the openssl lib from corresponding installation disc:
	      Fedora Core 2/3/4/5(openssl-0.9.71x-xx), 
	      Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),
	      Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl), 
	      Gentoo(dev-libs/openssl), etc.
	  (2) Download the openssl open source package from [www.openssl.org](www.openssl.org), build and 
	      install it.
	 2. If make errors happen in RedHat(and also Fedora Core) for kssl.h,
please add lines below into Makefile
	      CPPFLAGS+=-I/usr/kerboros/include
	 
	(5)Edit wpa_supplicant.conf to set up SSID and its passphrase.
	  For example, the following setting in "wpa1.conf" means SSID 
          to join is "BufAG54_Ch6" and its passphrase is "87654321".

	   Example 1: Configuration for WPA-PWK
	  network={
			ssid="BufAG54_Ch6"
			#scan_ssid=1 //see note 3
			proto=WPA
			key_mgmt=WPA-PSK
			pairwise=CCMP TKIP
			group=CCMP TKIP WEP104 WEP40
			psk="87654321"
			priority=2
		  }
	
	    Example 2: Configuration for LEAP
	    network={
			ssid="BufAG54_Ch6"
			key_mgmt=IEEE8021X
			group=WEP40 WEP104
			eap=LEAP
			identity="user1"
			password="1111"
		  }
	    Example 3: Linking to hidden ssid given AP's security policy exactly.(see note 3 below)
            ap_scan=2
	    network={
		ssid="Hidden_ssid"
		proto=WPA
		key_mgmt=WPA-PSK
		pairwise=CCMP
		group=CCMP
		psk="12345678"
	  	}
		
	    Example 4: Linking to ad-hoc (see note 4 below)
	    ap_scan=2
	    network={
		ssid="Ad-hoc"
                mode=1
		proto=WPA
		key_mgmt=WPA-NONE
		pairwise=NONE
		group=TKIP
		psk="12345678"
		}
	Note: 1. proto=WPA for WPA, proto=RSN for WPA2. 
	      2. If user needs to connect an AP with WPA or WPA2 mixed mode, it is suggested 
		 to set the cipher of pairwise and group to both CCMP and TKIP unless you 
		 know exactly which cipher type AP is configured.
	      3. When connecting to hidden ssid, explicit security policy should be given with 
		 ap_scan=2 being setting.
	      4. It is suggested setting ap_scan to 2 and mode to 1 when linking to or creating an ad-hoc. Group and pairwise
		 cipher type should also be explicit, always with group setting to TKIP or CCMP and pairwise setting
		 to NONE. Lower version wpa_supplicant may not allow setting group to CCMP with pairwise setting to NONE.
		 So if any problem, you may try to set both group and pairwise to CCMP, leaving other setting unchanged, when
	         connecting to an CCMP-encrypted ad-hoc.
	      5. More config setting option, please refer to wpa_supplicant.conf in wpa_supplicant.tar.gz that we provide.

	(6)Execute WPA supplicant (Assume rtl8192E and related modules had been
           loaded):
           ./runwpa

           Note: The script runwpa will check Wireless Extension version automatically.
                 If the version of Wireless Extension is equal or larger than 18, the
                 option of "-D wext" is selected. If the version of Wireless extension
                 is less than 18, the option of "-D ipw" is selected.

===============================================================================
			For kernel 2.4 notes
===============================================================================
    First of all, we have to install the necessary tools for building the driver. In the RedHat9 installation, please
choose the "Customize the set of packages to be install" and include two packages "Development Tools", "Kernel Development".

    The RedHat 9 (kernel 2.4.20-8) just suppports the WEP security for Wifi. We have to patch the kernel with updating 
wireless extension so that the kernel just supports the WPA, WPA2 functionalities by stardard wireless extension. This 
driver had been verified on the patched 2.4.20-8 kernel and the WPA/WPA2 PSK works fine on the patched kernel.

    First of all, we must have three patch file to update the wireless extension.
    1. iw241_we16-6.diff     ([http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/iw241_we16-6.diff](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/iw241_we16-6.diff))
    2. iw249_we17-13.diff    ([http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/iw249_we17-13.diff](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/iw249_we17-13.diff))
    3. iw240_we18-5.diff     ([http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/iw240_we18-5.diff](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/iw240_we18-5.diff))
    
    Copy these three patch files to the patient directory of the linux kernel source folder and use the following
command to patch the RedHat 9 kernel.
    $> patch -p0 < ./iw241_we16-6.diff
    $> patch -p0 < ./iw249_we17-13.diff
    $> patch -p0 < ./iw240_we18-5.diff
    
    After patching the kernel, please remember to re-build the updated kernel/modules and use it for your target platform.
Now, the patched kernel had got the ability to support the WPA/WPA2 PSK functionalities with wireless extension interface.

    Reminding: At the first time to use the wpa_supplicant, pleasee remember to compile the wpa_supplicant with the updated
kernel so that the wpa_supplicant will get the latest wireless extension version for supporting more functionalities.

    Finally, the kernel 2.4 can't support the WPS functionality.
```

---

### Post by l0ijoat on 2010-08-10
bump

---

### Post by davidmohammed on 2010-08-10
Hi there,
  please open a terminal session and unplug your device.

type 

dmesg

A bunch of text will be displayed.

plug in your usb device.

type

dmesg

some new text will be displayed.  Please can you copy and paste that new text in a reply here.  Thanks.

---

### Post by l0ijoat on 2010-08-10
davidmohammed, thanks for your response! i did what you said, and here's what came back. i think it was more text than the terminal could display though, is there a way to see it all?

```
[    0.698640] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.698773] mice: PS/2 mouse device common for all mice
[    0.699826] rtc_cmos 00:09: RTC can wake from S4
[    0.699877] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    0.699916] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.700028] device-mapper: uevent: version 1.0.3
[    0.700158] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.700235] device-mapper: multipath: version 1.1.0 loaded
[    0.700238] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.700366] EISA: Probing bus 0 at eisa.0
[    0.700372] Cannot allocate resource for EISA slot 1
[    0.700375] Cannot allocate resource for EISA slot 2
[    0.700378] Cannot allocate resource for EISA slot 3
[    0.700381] Cannot allocate resource for EISA slot 4
[    0.700384] Cannot allocate resource for EISA slot 5
[    0.700396] EISA: Detected 0 cards.
[    0.700477] cpuidle: using governor ladder
[    0.700480] cpuidle: using governor menu
[    0.700991] TCP cubic registered
[    0.701176] NET: Registered protocol family 10
[    0.701684] lo: Disabled Privacy Extensions
[    0.702042] NET: Registered protocol family 17
[    0.702082] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (2 cpu cores) (version 2.20.00)
[    0.702126] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13
[    0.702129] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x15
[    0.702132] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[    0.709943] Using IPI No-Shortcut mode
[    0.710031] PM: Resume from disk failed.
[    0.710045] registered taskstats version 1
[    0.710429]   Magic number: 6:555:137
[    0.710448] block ram2: hash matches
[    0.710548] rtc_cmos 00:09: setting system clock to 2010-08-09 17:06:38 UTC (1281373598)
[    0.710553] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.710556] EDD information not available.
[    0.712042] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.881328] ACPI: Battery Slot [BAT0] (battery present)
[    0.884321] isapnp: No Plug & Play device found
[    0.948042] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.081918] usb 1-1: configuration #1 chosen from 1 choice
[    1.132364] Freeing unused kernel memory: 660k freed
[    1.132897] Write protecting the kernel text: 4680k
[    1.132941] Write protecting the kernel read-only data: 1840k
[    1.153803] udev: starting version 151
[    1.196110] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    1.254692] sata_nv 0000:00:0e.0: version 3.5
[    1.254710] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    1.254714] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.254771] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.281493] scsi0 : sata_nv
[    1.299332] scsi1 : sata_nv
[    1.299570] ata1: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 23
[    1.299574] ata2: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 23
[    1.299636] pata_amd 0000:00:0d.0: version 0.4.1
[    1.299693] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.311232] scsi2 : pata_amd
[    1.324805] scsi3 : pata_amd
[    1.325583] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    1.325588] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    1.325666] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.325982] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.325989]   alloc irq_desc for 20 on node -1
[    1.325992]   alloc kstat_irqs on node -1
[    1.326004] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    1.326011] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.326060] nv_probe: set workaround bit for reversed mac addr
[    1.332953] Initializing USB Mass Storage driver...
[    1.333080] scsi4 : SCSI emulation for USB Mass Storage devices
[    1.333188] usbcore: registered new interface driver usb-storage
[    1.333192] USB Mass Storage support registered.
[    1.333199] usb-storage: device found at 2
[    1.333201] usb-storage: waiting for device to settle before scanning
[    1.335306] usb 1-4: configuration #1 chosen from 1 choice
[    1.488345] ata3.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NC08, max MWDMA2
[    1.488377] ata3: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    1.504303] ata3.00: configured for MWDMA2
[    1.768069] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.776229] ata1.00: ATA-7: ST9160821AS, 3.BHD, max UDMA/100
[    1.776232] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.792246] ata1.00: configured for UDMA/100
[    1.792421] scsi 0:0:0:0: Direct-Access     ATA      ST9160821AS      3.BH PQ: 0 ANSI: 5
[    1.792617] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.792809] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.792859] sd 0:0:0:0: [sda] Write Protect is off
[    1.792863] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.792889] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.793034]  sda: sda1 sda2 < sda5 >
[    1.834564] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.845164] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:4f:4e:5c
[    1.845169] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    2.114625] ata2: SATA link down (SStatus 0 SControl 300)
[    2.118182] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NC08 PQ: 0 ANSI: 5
[    2.129103] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.129107] Uniform CD-ROM driver Revision: 3.20
[    2.129224] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.129295] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.129395] ata4: port disabled. ignoring.
[    2.135077] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    2.135097] ohci1394 0000:07:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, high) -> IRQ 5
[    2.191063] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.470029] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.468283] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00c5302600]
[    6.332291] usb-storage: device scan complete
[    6.334258] scsi 4:0:0:0: Direct-Access     ST350083 0AS                   PQ: 0 ANSI: 2 CCS
[    6.334734] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    6.335363] sd 4:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    6.336106] sd 4:0:0:0: [sdb] Write Protect is off
[    6.336110] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
[    6.336114] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.338105] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.338110]  sdb: sdb1
[    6.349107] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.349111] sd 4:0:0:0: [sdb] Attached SCSI disk
[   17.098309] udev: starting version 151
[   17.138203] lp: driver loaded but no devices found
[   17.203427] Adding 5847032k swap on /dev/sda5.  Priority:-1 extents:1 across:5847032k 
[   17.407190] acpi device:22: registered as cooling_device2
[   17.407357] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   17.407424] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   17.508925] vga16fb: initializing
[   17.508933] vga16fb: mapped to 0xc00a0000
[   17.509058] fb0: VGA16 VGA frame buffer device
[   17.575423] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   17.576559] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   17.576583] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   17.580750] Linux video capture interface: v2.00
[   17.597429] ricoh-mmc: Ricoh MMC Controller disabling driver
[   17.597433] ricoh-mmc: Copyright(c) Philip Langdale
[   17.597468] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)
[   17.597484] ricoh-mmc: Controller is now disabled.
[   17.599411] sdhci: Secure Digital Host Controller Interface driver
[   17.599415] sdhci: Copyright(c) Pierre Ossman
[   17.601272] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 19)
[   17.601717] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   17.601735] sdhci-pci 0000:07:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[   17.605161] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   17.613600] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:0b.1/usb1/1-4/1-4:1.0/input/input7
[   17.613806] usbcore: registered new interface driver uvcvideo
[   17.613859] USB Video Class driver (v0.1.0)
[   17.614985] Registered led device: mmc0::
[   17.616069] mmc0: SDHCI controller on PCI [0000:07:05.1] using PIO
[   17.879483] Console: switching to colour frame buffer device 80x30
[   17.884215] type=1505 audit(1281373615.670:2):  operation="profile_load" pid=689 name="/sbin/dhclient3"
[   17.884531] type=1505 audit(1281373615.670:3):  operation="profile_load" pid=689 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.884708] type=1505 audit(1281373615.670:4):  operation="profile_load" pid=689 name="/usr/lib/connman/scripts/dhclient-script"
[   17.886348] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   17.886356]   alloc irq_desc for 21 on node -1
[   17.886359]   alloc kstat_irqs on node -1
[   17.886372] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[   17.886376] hda_intel: Disable MSI for Nvidia chipset
[   17.886563] HDA Intel 0000:00:10.1: setting latency timer to 64
[   18.095353] type=1505 audit(1281373615.882:5):  operation="profile_load" pid=894 name="/usr/share/gdm/guest-session/Xsession"
[   18.097594] type=1505 audit(1281373615.886:6):  operation="profile_replace" pid=895 name="/sbin/dhclient3"
[   18.097917] type=1505 audit(1281373615.886:7):  operation="profile_replace" pid=895 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.098098] type=1505 audit(1281373615.886:8):  operation="profile_replace" pid=895 name="/usr/lib/connman/scripts/dhclient-script"
[   18.102267] type=1505 audit(1281373615.890:9):  operation="profile_load" pid=896 name="/usr/bin/evince"
[   18.106622] type=1505 audit(1281373615.894:10):  operation="profile_load" pid=896 name="/usr/bin/evince-previewer"
[   18.109235] type=1505 audit(1281373615.898:11):  operation="profile_load" pid=896 name="/usr/bin/evince-thumbnailer"
[   18.433605] apm: BIOS not found.
[   18.462758] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   18.524436] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   18.535229] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[   18.536722] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[   18.538094] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[   18.540189] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[   18.542151] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[   18.542155] psmouse.c: issuing reconnect request
[   18.562355] ppdev: user-space parallel port driver
[   26.769866] Linux agpgart interface v0.103
[   26.797503] [drm] Initialized drm 1.1.0 20060810
[   26.836352] nouveau 0000:00:05.0: power state changed by ACPI to D0
[   26.836390] nouveau 0000:00:05.0: power state changed by ACPI to D0
[   26.836738] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 18
[   26.836745]   alloc irq_desc for 18 on node -1
[   26.836748]   alloc kstat_irqs on node -1
[   26.836760] nouveau 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, high) -> IRQ 18
[   26.836766] nouveau 0000:00:05.0: setting latency timer to 64
[   26.839806] [drm] nouveau 0000:00:05.0: failed to evaluate _DSM: 5
[   26.840852] [drm] nouveau 0000:00:05.0: Detected an NV40 generation card (0x04e000a2)
[   26.841549] [drm] nouveau 0000:00:05.0: Attempting to load BIOS image from PROM
[   26.841566] [drm] nouveau 0000:00:05.0: ... BIOS signature not found
[   26.841569] [drm] nouveau 0000:00:05.0: Attempting to load BIOS image from PRAMIN
[   26.881473] [drm] nouveau 0000:00:05.0: ... appears to be valid
[   26.881477] [drm] nouveau 0000:00:05.0: BIT BIOS found
[   26.881481] [drm] nouveau 0000:00:05.0: Bios version 05.51.28.53
[   26.881485] [drm] nouveau 0000:00:05.0: TMDS table script pointers not stubbed
[   26.881488] [drm] nouveau 0000:00:05.0: BIT table 'd' not found
[   26.881491] [drm] nouveau 0000:00:05.0: Found Display Configuration Block version 3.0
[   26.881496] [drm] nouveau 0000:00:05.0: DCB connector table: VHER 0x30 5 10 2
[   26.881500] [drm] nouveau 0000:00:05.0:   0: 0x00000000: type 0x00 idx 0 tag 0xff
[   26.881503] [drm] nouveau 0000:00:05.0:   1: 0x00000131: type 0x31 idx 1 tag 0xff
[   26.881506] [drm] nouveau 0000:00:05.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   26.881510] [drm] nouveau 0000:00:05.0:   3: 0x00000211: type 0x11 idx 2 tag 0xff
[   26.881513] [drm] nouveau 0000:00:05.0:   4: 0x00000213: type 0x13 idx 2 tag 0xff
[   26.881516] [drm] nouveau 0000:00:05.0:   5: 0x00000340: type 0x40 idx 3 tag 0xff
[   26.881520] [drm] nouveau 0000:00:05.0: Raw DCB entry 0: 03005313 00000004
[   26.881524] [drm] nouveau 0000:00:05.0: Raw DCB entry 1: 02010300 00000023
[   26.881527] [drm] nouveau 0000:00:05.0: Raw DCB entry 2: 024123f1 0040c080
[   26.881533] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 0 at offset 0xE225
[   26.881602] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 1 at offset 0xE364
[   26.881605] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 2 at offset 0xE365
[   26.881787] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 3 at offset 0xE4E7
[   26.881790] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001305 not verified ===
[   26.881793] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001401 not verified ===
[   26.881796] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001405 not verified ===
[   26.881799] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001409 not verified ===
[   26.881802] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x0000140D not verified ===
[   26.881811] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 4 at offset 0xE533
[   26.898577] [TTM] Zone  kernel: Available graphics memory: 437358 kiB.
[   26.898582] [TTM] Zone highmem: Available graphics memory: 998002 kiB.
[   26.898595] [drm] nouveau 0000:00:05.0: 64 MiB VRAM
[   26.900881] [drm] nouveau 0000:00:05.0: 64 MiB GART (aperture)
[   26.901220] [drm] nouveau 0000:00:05.0: Allocating FIFO number 0
[   26.901771] [drm] nouveau 0000:00:05.0: nouveau_channel_alloc: initialised FIFO 0
[   26.901779] [drm] nouveau 0000:00:05.0: Initial CRTC_OWNER is 0
[   26.901843] [drm] nouveau 0000:00:05.0: Detected a LVDS connector
[   27.012340] [drm] nouveau 0000:00:05.0: Detected a VGA connector
[   27.012388] [drm] nouveau 0000:00:05.0: Detected a TV connector
[   27.013348] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on lvds encoder (output 0)
[   27.013353] [drm] nouveau 0000:00:05.0: Calling LVDS script 6:
[   27.013357] [drm] nouveau 0000:00:05.0: 0xD3CD: Parsing digital output script table
[   27.304052] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on vga encoder (output 1)
[   27.304058] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on TV encoder (output 2)
[   27.384234] [drm] nouveau 0000:00:05.0: allocated 1280x800 fb: 0x49000, bo f4045200
[   27.384324] fb1: nouveaufb frame buffer device
[   27.384327] registered panic notifier
[   27.384335] [drm] Initialized nouveau 0.0.15 20090420 for 0000:00:05.0 on minor 0
[   27.625826] [drm] nouveau 0000:00:05.0: Allocating FIFO number 1
[   27.626667] [drm] nouveau 0000:00:05.0: nouveau_channel_alloc: initialised FIFO 1
[   27.640890] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[   27.640896] [drm] nouveau 0000:00:05.0: Calling LVDS script 2:
[   27.640900] [drm] nouveau 0000:00:05.0: 0xD432: Parsing digital output script table
[   27.792040] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on lvds encoder (output 0)
[   27.792044] [drm] nouveau 0000:00:05.0: Calling LVDS script 5:
[   27.792047] [drm] nouveau 0000:00:05.0: 0xD3B6: Parsing digital output script table
[   28.176049] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[   28.800033] eth0: no IPv6 routers present
[   79.504046] Clocksource tsc unstable (delta = -171339750 ns)
[  567.253096] usb 1-6: new high speed USB device using ehci_hcd and address 4
[  567.701986] usb 1-6: configuration #1 chosen from 1 choice
[  567.718732] scsi5 : SCSI emulation for USB Mass Storage devices
[  567.728212] usb-storage: device found at 4
[  567.728220] usb-storage: waiting for device to settle before scanning
[  572.730271] usb-storage: device scan complete
[  572.732308] scsi 5:0:0:0: Direct-Access     USB      DISK 2.0         0403 PQ: 0 ANSI: 0 CCS
[  572.739752] sd 5:0:0:0: Attached scsi generic sg3 type 0
[  572.745646] sd 5:0:0:0: [sdc] 3981312 512-byte logical blocks: (2.03 GB/1.89 GiB)
[  572.748945] sd 5:0:0:0: [sdc] Write Protect is off
[  572.748958] sd 5:0:0:0: [sdc] Mode Sense: 43 00 00 00
[  572.748965] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  572.785132] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  572.785153]  sdc: sdc1
[  572.799129] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  572.799147] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[  651.663298] usb 1-6: USB disconnect, address 4
[23577.236077] usb 1-6: new high speed USB device using ehci_hcd and address 5
[23577.633654] usb 1-6: configuration #1 chosen from 1 choice
[23577.635181] scsi6 : SCSI emulation for USB Mass Storage devices
[23577.635556] usb-storage: device found at 5
[23577.635562] usb-storage: waiting for device to settle before scanning
[23582.632627] usb-storage: device scan complete
[23582.634320] scsi 6:0:0:0: Direct-Access     USB      DISK 2.0         0403 PQ: 0 ANSI: 0 CCS
[23582.635792] sd 6:0:0:0: Attached scsi generic sg3 type 0
[23582.654149] sd 6:0:0:0: [sdc] 3981312 512-byte logical blocks: (2.03 GB/1.89 GiB)
[23582.656178] sd 6:0:0:0: [sdc] Write Protect is off
[23582.656193] sd 6:0:0:0: [sdc] Mode Sense: 43 00 00 00
[23582.656201] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[23582.662202] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[23582.662217]  sdc: sdc1
[23582.668151] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[23582.668166] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[25052.965076] CE: hpet increasing min_delta_ns to 15000 nsec
[25261.740297] usb 1-6: USB disconnect, address 5
[25274.096771] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on lvds encoder (output 0)
[25274.096777] [drm] nouveau 0000:00:05.0: Calling LVDS script 6:
[25274.096782] [drm] nouveau 0000:00:05.0: 0xD3CD: Parsing digital output script table
[35189.564027] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on lvds encoder (output 0)
[35189.564038] [drm] nouveau 0000:00:05.0: Calling LVDS script 2:
[35189.564049] [drm] nouveau 0000:00:05.0: 0xD432: Parsing digital output script table
[35189.716057] [drm] nouveau 0000:00:05.0: Calling LVDS script 5:
[35189.716068] [drm] nouveau 0000:00:05.0: 0xD3B6: Parsing digital output script table
[35983.232093] usb 1-6: new high speed USB device using ehci_hcd and address 6
[35983.626786] usb 1-6: configuration #1 chosen from 1 choice
[35983.627651] scsi7 : SCSI emulation for USB Mass Storage devices
[35983.628050] usb-storage: device found at 6
[35983.628056] usb-storage: waiting for device to settle before scanning
[35988.628713] usb-storage: device scan complete
[35988.630282] scsi 7:0:0:0: Direct-Access     USB      DISK 2.0         0403 PQ: 0 ANSI: 0 CCS
[35988.631354] sd 7:0:0:0: Attached scsi generic sg3 type 0
[35988.649766] sd 7:0:0:0: [sdc] 3981312 512-byte logical blocks: (2.03 GB/1.89 GiB)
[35988.652493] sd 7:0:0:0: [sdc] Write Protect is off
[35988.652508] sd 7:0:0:0: [sdc] Mode Sense: 43 00 00 00
[35988.652516] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[35988.659164] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[35988.659180]  sdc: sdc1
[35988.665151] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[35988.665167] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[41844.853352] PM: Syncing filesystems ... done.
[41844.920059] PM: Preparing system for mem sleep
[41844.920064] Freezing user space processes ... (elapsed 0.00 seconds) done.
[41844.921115] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[41844.921198] PM: Entering mem sleep
[41844.921212] Suspending console(s) (use no_console_suspend to debug)
[41844.936283] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[41844.957201] sd 0:0:0:0: [sda] Stopping disk
[41847.142466] PM: suspend of drv:sd dev:0:0:0:0 complete after 2206.182 msecs
[41847.564980] PM: suspend of drv:psmouse dev:serio1 complete after 392.873 msecs
[41847.666944] ACPI handle has no context!
[41847.666953] sdhci-pci 0000:07:05.1: PCI INT B disabled
[41847.666957] ACPI handle has no context!
[41847.684073] ACPI handle has no context!
[41847.700780] forcedeth 0000:00:14.0: PCI INT A disabled
[41847.860059] HDA Intel 0000:00:10.1: PCI INT B disabled
[41847.876037] PM: suspend of drv:HDA Intel dev:0000:00:10.1 complete after 159.998 msecs
[41847.876124] sata_nv 0000:00:0e.0: PCI INT A disabled
[41847.892133] ata4: port disabled. ignoring.
[41847.908042] ehci_hcd 0000:00:0b.1: PCI INT B disabled
[41847.908053] ohci_hcd 0000:00:0b.0: PCI INT A disabled
[41847.908073] [drm] nouveau 0000:00:05.0: Evicting buffers...
[41847.994650] [drm] nouveau 0000:00:05.0: Idling channels...
[41847.994756] [drm] nouveau 0000:00:05.0: Suspending GPU objects...
[41848.145736] [drm] nouveau 0000:00:05.0: And we're gone!
[41848.145784] nouveau 0000:00:05.0: PCI INT A disabled
[41848.160111] nouveau 0000:00:05.0: power state changed by ACPI to D3
[41848.160123] PM: suspend of drv:nouveau dev:0000:00:05.0 complete after 252.052 msecs
[41848.160479] PM: suspend of devices complete after 3238.966 msecs
[41848.160483] PM: suspend devices took 3.240 seconds
[41848.160960] ricoh-mmc: Suspending.
[41848.160967] ricoh-mmc: Controller is now re-enabled.
[41848.192419] PM: late suspend of devices complete after 31.930 msecs
[41848.192576] ACPI: Preparing to enter system sleep state S3
[41848.208030] Disabling non-boot CPUs ...
[41848.208053] CPU0 attaching NULL sched-domain.
[41848.208058] CPU1 attaching NULL sched-domain.
[41848.272035] CPU0 attaching NULL sched-domain.
[41848.273124] Breaking affinity for irq 1
[41848.273179] Breaking affinity for irq 12
[41848.273213] Breaking affinity for irq 21
[41848.273226] Breaking affinity for irq 23
[41848.376025] CPU 1 is now offline
[41848.376028] SMP alternatives: switching to UP code
[41848.380753] Back to C!
[41848.380753] Enabling non-boot CPUs ...
[41848.380753] SMP alternatives: switching to SMP code
[41848.387207] Booting processor 1 APIC 0x1 ip 0x6000
[41848.380245] Initializing CPU#1
[41848.380245] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[41848.380245] CPU: L2 Cache: 512K (64 bytes/line)
[41848.380245] CPU: Physical Processor ID: 0
[41848.380245] CPU: Processor Core ID: 1
[41848.476109] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[41848.476180] CPU0 attaching NULL sched-domain.
[41848.476233] Switch to broadcast mode on CPU1
[41848.504041] CPU0 attaching sched-domain:
[41848.504044]  domain 0: span 0-1 level MC
[41848.504048]   groups: 0 1
[41848.504053] CPU1 attaching sched-domain:
[41848.504055]  domain 0: span 0-1 level MC
[41848.504058]   groups: 1 0
[41848.504424] CPU1 is up
[41848.504559] ACPI: Waking up from system sleep state S3
[41849.642767] pci 0000:00:00.0: Found disabled HT MSI Mapping
[41849.642773] pci 0000:00:00.0: Enabling HT MSI Mapping
[41849.642886] pcieport 0000:00:02.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[41849.642918] pci 0000:00:00.0: Found enabled HT MSI Mapping
[41849.642936] pcieport 0000:00:03.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[41849.642970] pci 0000:00:00.0: Found enabled HT MSI Mapping
[41849.643132] pci 0000:00:0a.3: restoring config space at offset 0xf (was 0x1030200, writing 0x103020a)
[41849.643197] ohci_hcd 0000:00:0b.0: restoring config space at offset 0x1 (was 0xb00007, writing 0xb00003)
[41849.643232] ehci_hcd 0000:00:0b.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[41849.643288] sata_nv 0000:00:0e.0: restoring config space at offset 0x1 (was 0xb00005, writing 0xb00007)
[41849.643349] pci 0000:00:09.0: Found enabled HT MSI Mapping
[41849.643364] pci 0000:00:10.0: restoring config space at offset 0x7 (was 0x28000f0, writing 0x828000f0)
[41849.643429] pci 0000:00:09.0: Found enabled HT MSI Mapping
[41849.643443] HDA Intel 0000:00:10.1: restoring config space at offset 0xf (was 0x5020200, writing 0x502020b)
[41849.643457] HDA Intel 0000:00:10.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[41849.643523] pci 0000:00:09.0: Found enabled HT MSI Mapping
[41849.643603] ohci1394 0000:07:05.0: restoring config space at offset 0x4 (was 0x0, writing 0xb8000000)
[41849.643609] ohci1394 0000:07:05.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804000)
[41849.643615] ohci1394 0000:07:05.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[41849.643643] sdhci-pci 0000:07:05.1: restoring config space at offset 0x4 (was 0x0, writing 0xb8000800)
[41849.643649] sdhci-pci 0000:07:05.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804000)
[41849.643657] sdhci-pci 0000:07:05.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[41849.643685] ricoh-mmc 0000:07:05.2: restoring config space at offset 0x4 (was 0x0, writing 0xb8000c00)
[41849.643692] ricoh-mmc 0000:07:05.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[41849.643701] ricoh-mmc: Resuming.
[41849.643708] ricoh-mmc: Controller is now disabled.
[41849.643729] pci 0000:07:05.3: restoring config space at offset 0x4 (was 0x0, writing 0xb8001400)
[41849.643737] pci 0000:07:05.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100102)
[41849.656036] __ratelimit: 12 callbacks suppressed
[41849.656039] pci 0000:07:05.4: Refused to change power state, currently in D3
[41849.656480] PM: early resume of devices complete after 13.887 msecs
[41850.056116] PM: resume of drv:battery dev:PNP0C0A:00 complete after 392.033 msecs
[41850.065447] [drm] nouveau 0000:00:05.0: We're back, enabling device...
[41850.065482] nouveau 0000:00:05.0: power state changed by ACPI to D0
[41850.065515] nouveau 0000:00:05.0: power state changed by ACPI to D0
[41850.065547] nouveau 0000:00:05.0: power state changed by ACPI to D0
[41850.065579] nouveau 0000:00:05.0: power state changed by ACPI to D0
[41850.065590] nouveau 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, high) -> IRQ 18
[41850.065596] nouveau 0000:00:05.0: setting latency timer to 64
[41850.065599] [drm] nouveau 0000:00:05.0: POSTing device...
[41850.065604] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 0 at offset 0xE225
[41850.065681] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 1 at offset 0xE364
[41850.065684] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 2 at offset 0xE365
[41850.065751] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 3 at offset 0xE4E7
[41850.065755] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001305 not verified ===
[41850.065758] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001401 not verified ===
[41850.065762] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001405 not verified ===
[41850.065765] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001409 not verified ===
[41850.065769] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x0000140D not verified ===
[41850.065782] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 4 at offset 0xE533
[41850.065785] [drm] nouveau 0000:00:05.0: Reinitialising engines...
[41850.065851] [drm] nouveau 0000:00:05.0: Restoring GPU objects...
[41850.095482] [drm] nouveau 0000:00:05.0: Restoring mode...
[41850.095518] [drm] nouveau 0000:00:05.0: Calling LVDS script 6:
[41850.095523] [drm] nouveau 0000:00:05.0: 0xD3CD: Parsing digital output script table
[41850.095543] [drm] nouveau 0000:00:05.0: Calling LVDS script 2:
[41850.095546] [drm] nouveau 0000:00:05.0: 0xD432: Parsing digital output script table
[41850.244037] [drm] nouveau 0000:00:05.0: Calling LVDS script 5:
[41850.244040] [drm] nouveau 0000:00:05.0: 0xD3B6: Parsing digital output script table
[41850.412831] [drm] nouveau 0000:00:05.0: Restoring CRTC_OWNER to 0.
[41850.422015] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on lvds encoder (output 0)
[41850.422019] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on vga encoder (output 1)
[41850.422023] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on TV encoder (output 2)
[41850.442472] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[41850.442476] [drm] nouveau 0000:00:05.0: Calling LVDS script 6:
[41850.442480] [drm] nouveau 0000:00:05.0: 0xD3CD: Parsing digital output script table
[41850.896039] [drm] nouveau 0000:00:05.0: Calling LVDS script 2:
[41850.896042] [drm] nouveau 0000:00:05.0: 0xD432: Parsing digital output script table
[41851.048031] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on lvds encoder (output 0)
[41851.048035] [drm] nouveau 0000:00:05.0: Calling LVDS script 5:
[41851.048038] [drm] nouveau 0000:00:05.0: 0xD3B6: Parsing digital output script table
[41851.768039] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[41851.777974] PM: resume of drv:nouveau dev:0000:00:05.0 complete after 1712.527 msecs
[41851.778005] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[41851.778012] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[41851.800040] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[41851.800046] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[41851.800061] pata_amd 0000:00:0d.0: setting latency timer to 64
[41851.801324] ata4: port disabled. ignoring.
[41851.801341] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[41851.801345] sata_nv 0000:00:0e.0: setting latency timer to 64
[41851.801491] pci 0000:00:10.0: setting latency timer to 64
[41851.801503] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[41851.801508] HDA Intel 0000:00:10.1: setting latency timer to 64
[41851.964336] ata3.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
[41851.964340] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[41851.964374] ata3: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[41851.980283] ata3.00: configured for MWDMA2
[41852.268062] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[41852.276224] ata1.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
[41852.292240] ata1.00: configured for UDMA/100
[41852.321194] eth0: no link during initialization.
[41852.321319] PM: resume of drv:forcedeth dev:0000:00:14.0 complete after 519.776 msecs
[41852.378046] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[41852.384059] sdhci-pci 0000:07:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[41852.516035] PM: resume of drv:usb dev:usb1 complete after 130.432 msecs
[41852.534620] ata2: SATA link down (SStatus 0 SControl 300)
[41852.632034] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[41852.765260] PM: resume of drv:usb dev:1-1 complete after 245.066 msecs
[41852.876034] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[41853.017005] PM: resume of drv:usb dev:1-4 complete after 251.699 msecs
[41853.017025] sd 0:0:0:0: [sda] Starting disk
[41853.140034] usb 1-6: reset high speed USB device using ehci_hcd and address 6
[41853.274510] PM: resume of drv:usb dev:1-6 complete after 244.451 msecs
[41853.274559] PM: resume of devices complete after 3618.038 msecs
[41853.274744] PM: resume devices took 3.616 seconds
[41853.274785] PM: Finishing wakeup.
[41853.274787] Restarting tasks ... done.
[41854.093751] eth0: link up.
[50044.871838] usb 1-6: USB disconnect, address 6
[54318.024957] ISO 9660 Extensions: Microsoft Joliet Level 3
[54318.068607] ISOFS: changing to secondary root
[54418.812077] usb 1-6: new high speed USB device using ehci_hcd and address 7
[54418.947321] usb 1-6: configuration #1 chosen from 1 choice
[70861.336576] usb 1-6: USB disconnect, address 7
[70867.464078] usb 1-6: new high speed USB device using ehci_hcd and address 8
[70867.837332] usb 1-6: configuration #1 chosen from 1 choice
[70867.838408] scsi8 : SCSI emulation for USB Mass Storage devices
[70867.838737] usb-storage: device found at 8
[70867.838744] usb-storage: waiting for device to settle before scanning
[70872.837643] usb-storage: device scan complete
[70872.840033] scsi 8:0:0:0: Direct-Access     USB      DISK 2.0         0403 PQ: 0 ANSI: 0 CCS
[70872.846387] sd 8:0:0:0: Attached scsi generic sg3 type 0
[70872.866190] sd 8:0:0:0: [sdc] 3981312 512-byte logical blocks: (2.03 GB/1.89 GiB)
[70872.867923] sd 8:0:0:0: [sdc] Write Protect is off
[70872.867935] sd 8:0:0:0: [sdc] Mode Sense: 43 00 00 00
[70872.867942] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[70872.873897] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[70872.873912]  sdc: sdc1
[70872.880778] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[70872.880792] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[71106.872093] usb 1-6: USB disconnect, address 8
[71130.372072] usb 1-6: new high speed USB device using ehci_hcd and address 9
[71130.507311] usb 1-6: configuration #1 chosen from 1 choice
[71135.342337] usb 1-6: USB disconnect, address 9
[71148.092088] usb 1-6: new high speed USB device using ehci_hcd and address 10
[71148.227573] usb 1-6: configuration #1 chosen from 1 choice
[71151.704461] usb 1-6: USB disconnect, address 10
[71164.284080] usb 1-6: new high speed USB device using ehci_hcd and address 11
[71164.419743] usb 1-6: configuration #1 chosen from 1 choice
[71266.652852] usb 1-6: USB disconnect, address 11
[71285.447838] usb 1-1: USB disconnect, address 2
[71315.144077] usb 1-6: new high speed USB device using ehci_hcd and address 12
[71315.279441] usb 1-6: configuration #1 chosen from 1 choice
[71351.471714] usb 1-6: USB disconnect, address 12
[71411.696076] usb 1-6: new high speed USB device using ehci_hcd and address 13
[71411.831317] usb 1-6: configuration #1 chosen from 1 choice

```

---

### Post by l0ijoat on 2010-08-11
bump

---

### Post by davidmohammed on 2010-08-11
is the stuff towards the bottom the "new" bit added to the dmesg output after you plugged in the usb device?

The reason why I ask - the last 10 to 20 lines should contain information on what your device is requesting from the kernel.

Can you try again, but just copy and paste the last 20 lines.

Also,  please copy and paste the output of

lsusb

also
sudo lshw -C network

for all of your replies please make sure you use CODE tags otherwise it makes it difficult to read the output.  Thanks.

Also - please double check that there is not a device requesting to be activated in Administration - Hardware drivers.

---

### Post by l0ijoat on 2010-08-12
davidmohammed,
here's the last few lines from dmesg:
```
[143163.241265] PM: resume of drv:usb dev:1-2 complete after 241.672 msecs
[143163.241315] PM: resume of devices complete after 3376.708 msecs
[143163.241501] PM: resume devices took 3.376 seconds
[143163.241541] PM: Finishing wakeup.
[143163.241543] Restarting tasks ... done.
[143163.571582] VFS: busy inodes on changed media or resized disk sr0
[143163.901346] VFS: busy inodes on changed media or resized disk sr0
[143164.231309] VFS: busy inodes on changed media or resized disk sr0
[143164.298483] eth0: link up.
[143164.891103] VFS: busy inodes on changed media or resized disk sr0
[143165.550959] VFS: busy inodes on changed media or resized disk sr0
[143165.930841] VFS: busy inodes on changed media or resized disk sr0
[143166.348442] VFS: busy inodes on changed media or resized disk sr0
[143166.725354] VFS: busy inodes on changed media or resized disk sr0
[143167.400418] VFS: busy inodes on changed media or resized disk sr0
[143167.786166] VFS: busy inodes on changed media or resized disk sr0
[143168.120224] VFS: busy inodes on changed media or resized disk sr0
[143168.859944] VFS: busy inodes on changed media or resized disk sr0
[143169.190300] VFS: busy inodes on changed media or resized disk sr0
[143169.519674] VFS: busy inodes on changed media or resized disk sr0
[143169.849527] VFS: busy inodes on changed media or resized disk sr0
[143170.510006] VFS: busy inodes on changed media or resized disk sr0
[143170.839281] VFS: busy inodes on changed media or resized disk sr0
[143171.169183] VFS: busy inodes on changed media or resized disk sr0
[143171.499269] VFS: busy inodes on changed media or resized disk sr0
[143177.701815] ISO 9660 Extensions: Microsoft Joliet Level 3
[143177.743165] ISOFS: changing to secondary root
[148562.788071] usb 1-6: new high speed USB device using ehci_hcd and address 18
[148562.923451] usb 1-6: configuration #1 chosen from 1 choice
[148589.700880] usb 1-6: USB disconnect, address 18
[148602.784074] usb 1-6: new high speed USB device using ehci_hcd and address 19
[148602.919461] usb 1-6: configuration #1 chosen from 1 choice

```

lsusb:
```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 019: ID 0b05:1791 ASUSTek Computer, Inc. 
Bus 001 Device 017: ID 059f:0951 LaCie, Ltd 
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

sudo lshw -C network didn't return anything

---

### Post by davidmohammed on 2010-08-12
hi there,

lsusb did not show your usb wireless device.

This could be due to
1. you did not have the device inserted into your usb port when you ran the command
2. the device needs to be "switched on"
3. the device is defective

If its the first or second, please can you rectify and rerun the commands in the above post again.  Thanks.

---

### Post by l0ijoat on 2010-08-12
it is showing up - it's the ASUSTek Computer, Inc. it's an ASUS WL-167G V3

```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 019: ID 0b05:1791 ASUSTek Computer, Inc. 
Bus 001 Device 017: ID 059f:0951 LaCie, Ltd 
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by davidmohammed on 2010-08-13
Hi there,
  happy to be wrong - From your dmesg trace, the kernel should have recognised your usb wireless chipset.  You'll notice nothing is recognised other than something had been inserted.

In that case, the lucid kernel does not recognise your usb device.  Is this a very (very) new device?  I find it strange that lucid doesnt recognise the wireless chipset.  Google search reveal that this model is linux compatible - so hence why my previous question about whether the device is defective or not.

If you are still convince the device is still working then as you intimated at the beginning, you'll need then to do one of two things

1. try one of the newest maverick kernels to see if it recognises your device
2. find the .inf and windows driver, and add it through ndiswrapper (use the gui I suggested).

Can I suggest you try the 2.6.35 kernel from [here]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds").  If it doesnt work, you could alway remove the kernel.

---

### Post by l0ijoat on 2010-08-13
davidmohammed,
but the usb adapter came with a cd for installing it. and there's a folder on the cd called linux which is full of a bunch of files (to install the driver etc.) that i don't know what to do with. don't you think i should be able to install this stuff first before i go messing around with the kernel? would it help if i gave you a list of the files that are given with the cd? maybe you could make some sense of the readme then? i'll include a list of what's on the cd below, and the readme is in the first post of this thread.
thanks for your help thus far!
hart

```
folder: Linux
      >folder: rtl8192su_linux_2.4_2.6.0003.0301.2010
             >folder: firmware
                    >folder: RTL8192SU
                           >file: rtl8192sfw.bin
             >folder: HAL
                    >folder: rtl8192u (bunch of files in here)
             >folder: ieee80211 (bunch of files in here)
             >files: 
                   - ifcfg-wlan0
                   - Makefile
                   - RadioPower.sh
                   - runwpa
                   - wireless-rtl-ac-dc-power.sh
                   - wlan0dhcp
                   - wlan0down
                   - wlan0up
                   - wpa1.conf
                   - wpa_supplicant-0.6.9.tar.gz
```

---

### Post by davidmohammed on 2010-08-15
Hi there,
  drivers that come with a wireless card are often (but not always) to allow a user to patch an old or custom built kernel.

The mainline kernels often sweep up all of these drivers so that you dont need to worry about installing them.

I suspect that the 2.6.32 kernel that comes with lucid missed your driver from the cut when it was built.  Google reveals some conflicting advice, but I would summise that your wireless chipset was included in the 2.6.33 kernel i.e. one above lucid.

For my part, I've got various intel graphics issues that have been fixed by the last two kernels 2.6.34 and 2.6.35.  I'm running lucid with 2.6.35 just fine.

The link I gave you shows that you download just three files and you run one install command (sudo dpkg -i *.deb).  

If you want to backout the installation, install ubuntu-tweak.  Boot from the standard 2.6.32 lucid kernel from grub.  Use ubuntu-tweak to remove the 2.6.35 kernel.

---

### Post by cchhrriiss121212 on 2010-08-17
Studio does not work with wireless by design, to see that it does read this thread:
[http://ubuntuforums.org/showthread.php?t=1525705]("http://ubuntuforums.org/showthread.php?t=1525705")

---

### Post by l0ijoat on 2010-08-26
ok, so i download networkmanager, and the icon is in the tray. today when i plugged in the wireless adapter, a little thing popped up telling me to install the drivers, so i went into hardware drivers and there are two new drivers to be installed: "Broadcom B43 wireless driver" and "Broadcom STA wireless driver" . the first one seems to install fine, but the second one gives me an error saying > sorry, installation of this driver failed. please have a look at the log file for details: /var/log/jockey.log
any idea what's wrong?
hart

---

### Post by l0ijoat on 2010-08-26
bumpy

---

### Post by l0ijoat on 2010-08-26
bump

---

### Post by nickthrolson on 2010-10-08
Glad I'm not the only one having trouble with this wireless card which I bought due to the fact tons of websites state works perfectly with any linux os hope someone gets v3 of wl-167g working.

---

### Post by biltong on 2010-12-02
> **nickthrolson said:**
> Glad I'm not the only one having trouble with this wireless card which I bought due to the fact tons of websites state works perfectly with any linux os hope someone gets v3 of wl-167g working.

I also recently pruchased one of these adapters... also no luck installing.  Also tried installing the driver on the CD... just get compile errors.

Any updates from anyone?

---

### Post by biltong on 2010-12-02
ok, after hours of googling and googling... it looks like we might have a solution. \\:D/

The Asus 167g V3 uses the Realtek 8192su driver (which is also found on the cd) and since I'm now using Maverick (10.10) a solution might be at hand.  See link below on how to install the driver on Maverick.

[http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html)

Let us know if this works for you...I'll try it later tonight.

---

### Post by biltong on 2010-12-03
\\:D/  It is working   \\:D/

---

### Post by vivek.pandey on 2010-12-04
> **davidmohammed said:**
> hi there,

lsusb did not show your usb wireless device.

This could be due to
1. you did not have the device inserted into your usb port when you ran the command
2. the device needs to be "switched on"
3. the device is defective

If its the first or second, please can you rectify and rerun the commands in the above post again.  Thanks.

dont be panic by this reply it may only be that ur adapter doesnt support linux...as soon as u insert ur adapter for first time a new windows appear to configure.. u can edit the changes or else better ask the company of ur adapter ...does it supports linux

---

### Post by paris_l87 on 2010-12-23
> **biltong said:**
> \\:D/  It is working   \\:D/

i cant get it to work though with this guide..i still get compile errors no matter what i try ugh..

does anyone have another solution?
i tried compiling from the cd but i got this:

  ```
CC [M]  /home/paris/Desktop/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.o
/home/paris/Desktop/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_usb_probe’:
/home/paris/Desktop/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12325: error: ‘struct net_device’ has no member named ‘open’
/home/paris/Desktop/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12326: error: ‘struct net_device’ has no member named ‘stop’
/home/paris/Desktop/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12327: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/paris/Desktop/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12328: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/paris/Desktop/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12329: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/paris/Desktop/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12330: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/paris/Desktop/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12331: error: ‘struct net_device’ has no member named ‘get_stats’
/home/paris/Desktop/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12332: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/paris/Desktop/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.o] Error 1
make[1]: *** [_module_/home/paris/Desktop/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [all] Error 2
```i even tried ndiswrapper,but no luck.... -.-

---

