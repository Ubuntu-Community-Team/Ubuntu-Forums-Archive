---
title: "rt2860 Ralink chipset"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by burningice64ta on 2008-01-30
Hello, I recently purchase an N wireless card based on the 2860 chipset and their driver is really confuzing.  Has anyone had any success with this and if so could you please help me out?

Thanks

---

### Post by burningice64ta on 2008-01-30
it wont even work with ndiswrapper

---

### Post by burningice64ta on 2008-01-30
Sorry to keep replying to this but I have a little info on the driver 

I got the driver from here [http://web.ralinktech.com/ralink/Home/Support/Linux.html]("http://web.ralinktech.com/ralink/Home/Support/Linux.html")

And this was the build instructions and it will not finish building it only builds tools or something wierd

```


=======================================================================
Features:
==========
   This driver implements basic IEEE802.11. Infrastructure and adhoc mode with 
   open or shared or WPA-PSK or WPA2-PSK authentication method. 
   NONE, WEP, TKIP and AES encryption. 


=======================================================================
Build Instructions:  
====================

1> $tar -xvzf DPB_RT2860_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2860_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.

4> $make									# compile driver source code

5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat       
    # !!!check if it is a binary file before loading !!!  
    
6> load driver
    #[kernel 2.4]
    #    $/sbin/insmod rt2860sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2860sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2860sta
	

```

And this is the Makefile

```

#MODE  STA or AP
RT28xx_MODE = STA
#RT28xx_MODE = AP
#TARTET = LINUX or UCOS 
TARGET = LINUX
#CHIPSET = 2860 or 2870
CHIPSET = 2860
#CHIPSET = 2870
#RT28xx_DIR = home directory of RT28xx source code
RT28xx_DIR = $(shell pwd)
RTMP_SRC_DIR = $(RT28xx_DIR)/RT$(CHIPSET)
#PLATFORM = 5VT
PLATFORM = PC
#PLATFORM = IKANOS
#PLATFORM = SIGMA
#PLATFORM = INIC
#PLATFORM = STAR
#PLATFORM = IXP
#PLATFORM = INF_TWINPASS
RELEASE = DPA
#RELEASE = DPB
ifeq ($(PLATFORM),5VT)
LINUX_SRC = /opt/fvt_11N_SDK_0807/fvt131x_SDK_11n/linux-2.6.17
CROSS_COMPILE = /opt/crosstool/uClibc_v5te_le_gcc_4_1_1/bin/arm-linux-
endif

ifeq ($(PLATFORM),IKANOS)
LINUX_SRC = /home/sample/projects/LX_2618_RG_5_3_00r4_SRC/linux-2.6.18
CROSS_COMPILE = mips-linux-
endif

ifeq ($(PLATFORM),SIGMA)
LINUX_SRC = /root/sigma/smp86xx_kernel_source_2.7.172.0/linux-2.6.15
CROSS_COMPILE = /root/sigma/smp86xx_toolchain_2.7.172.0/build_mipsel_nofpu/staging_dir/bin/mipsel-linux-
endif

ifeq ($(PLATFORM),INIC)
UCOS_SRC = /opt/uCOS/iNIC_rt2880
CROSS_COMPILE = /usr/bin/mipsel-linux-
endif

ifeq ($(PLATFORM),STAR)
LINUX_SRC = /opt/star/kernel/linux-2.4.27-star
CROSS_COMPILE = /opt/star/tools/arm-linux/bin/arm-linux-
endif

ifeq ($(PLATFORM),PC)
# Linux 2.6
LINUX_SRC = /lib/modules/$(shell uname -r)/build
# Linux 2.4 Change to your local setting
#LINUX_SRC = /usr/src/linux-2.4
LINUX_SRC_MODULE = /lib/modules/$(shell uname -r)/kernel/drivers/net/wireless/
CROSS_COMPILE = 
endif

ifeq ($(PLATFORM),IXP)
LINUX_SRC = /project/stable/Gmtek/snapgear-uclibc/linux-2.6.x
CROSS_COMPILE = arm-linux-
endif

ifeq ($(PLATFORM),INF_TWINPASS)
# Linux 2.6
#LINUX_SRC = /lib/modules/$(shell uname -r)/build
# Linux 2.4 Change to your local setting
LINUX_SRC = /project/stable/twinpass/release/2.0.1/source/kernel/opensource/linux-2.4.31/
CROSS_COMPILE = mips-linux-
endif


export RT28xx_DIR RT28xx_MODE LINUX_SRC CROSS_COMPILE PLATFORM RELEASE CHIPSET RTMP_SRC_DIR LINUX_SRC_MODULE

all: build_tools $(TARGET)


build_tools:
	make -C tools
	$(RT28xx_DIR)/tools/bin2h

UCOS:
	make -C os/ucos/ MODE=$(RT28xx_MODE)
	echo $(RT28xx_MODE)


LINUX:
ifneq (,$(findstring 2.4,$(LINUX_SRC)))
	cp -f os/linux/Makefile.4 $(RT28xx_DIR)/os/linux/Makefile
	make -C $(RT28xx_DIR)/os/linux/
ifeq ($(RT28xx_MODE),AP)
	cp -f $(RT28xx_DIR)/os/linux/rt$(CHIPSET)ap.o /tftpboot
else	
	cp -f $(RT28xx_DIR)/os/linux/rt$(CHIPSET)sta.o /tftpboot
endif	
else
	cp -f os/linux/Makefile.6 $(RT28xx_DIR)/os/linux/Makefile
	make  -C  $(LINUX_SRC) SUBDIRS=$(RT28xx_DIR)/os/linux modules
ifeq ($(RT28xx_MODE),AP)
	cp -f $(RT28xx_DIR)/os/linux/rt$(CHIPSET)ap.ko /tftpboot
else	
	cp -f $(RT28xx_DIR)/os/linux/rt$(CHIPSET)sta.ko /tftpboot
endif	
endif

release:
ifeq ($(TARGET), LINUX)
	make -C $(RT28xx_DIR)/os/linux -f Makefile.release release
ifeq ($(RELEASE), DPA)
	make -C $(RT28xx_DIR)/os/linux -f Makefile.DPA release
	rm -rf build
endif
ifeq ($(RELEASE), DPB)
	make -C $(RT28xx_DIR)/os/linux -f Makefile.DPB release
	rm -rf build
endif
endif

prerelease:
	make -C $(RT28xx_DIR)/os/linux -f Makefile.release prerelease
	cp $(RT28xx_DIR)/os/linux/Makefile.DPB $(RTMP_SRC_DIR)/os/linux/.
	cp $(RT28xx_DIR)/os/linux/Makefile.DPA $(RTMP_SRC_DIR)/os/linux/.

clean:
ifeq ($(TARGET), LINUX)
ifneq (,$(findstring 2.4,$(LINUX_SRC)))
	cp -f os/linux/Makefile.4 os/linux/Makefile
else
	cp -f os/linux/Makefile.6 os/linux/Makefile
endif
	make -C os/linux clean
	rm -rf os/linux/Makefile
endif	
ifeq ($(TARGET), UCOS)
	make -C os/ucos clean MODE=$(RT28xx_MODE)
endif

uninstall:
ifeq ($(TARGET), LINUX)
ifneq (,$(findstring 2.4,$(LINUX_SRC)))
	make -C $(RT28xx_DIR)/os/linux -f Makefile.4 uninstall
else
	make -C $(RT28xx_DIR)/os/linux -f Makefile.6 uninstall
endif
endif

install:
ifeq ($(TARGET), LINUX)
ifneq (,$(findstring 2.4,$(LINUX_SRC)))
	make -C $(RT28xx_DIR)/os/linux -f Makefile.4 install
else
	make -C $(RT28xx_DIR)/os/linux -f Makefile.6 install
endif
endif


```

I have a base install of gutsy with only ndiswrapper and build-essential

Hope this information helps

thanks

---

### Post by burningice64ta on 2008-01-30
Ok so I got everything to install correctly and now when i try to do an iwlist scan i get 

```

failed to read scan data : Resource temporarily unavailable

```

iwconfig brings up

ra0         RT2860 Wireless

and lspci shows

RaLink unknown device

---

### Post by burningice64ta on 2008-01-30
Sorry to keep spamming the forums.  I got it to work should i write a guide for it ?

---

### Post by wieman01 on 2008-01-31
So you have also considered my Ralink tutorial? If not give it a go. I'll suport you. Are you on Ubuntu 32-bit?

---

### Post by burningice64ta on 2008-02-02
No i got it to work using their gpl'd drivers i just didnt read the readme

---

### Post by Bloodspike on 2008-02-04
I am having the similiar problem with the RT2860 drivers.  I have an Airlink 6080 cardbus adapter and a 802.11G network using WPA2.  I downloaded the drivers from Ralink but I'm having a problem compiling them.  I'm running Ubuntu 7.1 out of the box.

I edited the Makefile according to the directions but don't understand how to edit the config.mk file.  Can you tell me how to define the GCC and LD of the target machine and define the compiler flags CFLAGS

I'm trying to get back into Linux but it has been a few years so please explain it like I'm a newbie.

Thanks

---

### Post by dpatel on 2008-02-25
> **burningice64ta said:**
> Sorry to keep spamming the forums.  I got it to work should i write a guide for it ?

I'd like a guide please!! :)

---

### Post by 2beers on 2008-03-02
A howto for the linux driver would be quite helpful!

First of all it's not that easy to understand all the instructions in the readme.
Furthermore it should be the same paths for the last ubuntu versions i suppose. So if one figures out what settings to do/wich paths to chose - maybe he/she could just post the scripts here?

---

### Post by JensLH on 2008-03-09
I am on Kubuntu Hardy alpha 5, fresh install on a 1 day old zepto laptop. I have since installed a few extra packages, such as ndiswrapper and build-essential.

I considered using NDISWrapper, but unshield core dumps on me when I try to unpack the XP driver from zepto's ftp site. I therefore consider NDISWrapper a no-go - unless someone can point me to a working driver for the rt2860?

I have downloaded the drivers from ralinktech's home page, but I get compile errors.
[FONT="Courier New"]jens@gee-n-tee:~/2008_0108_RT2860_Linux_STA_v1.5.0.0$ sudo make
make -C tools
make[1]: Entering directory `/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/tools'
/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/Makefile
make  -C  /usr/src/linux-headers-2.6.24-10-generic SUBDIRS=/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-10-generic'
  CC [M]  /home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.o
/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c: In function ‘rt28xx_open’:
/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:537: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:537: error: (Each undeclared identifier is reported only once
/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:537: error: for each function it appears in.)
/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:537: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c: In function ‘rt_ieee80211_if_setup’:
/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:624: warning: assignment from incompatible pointer type
/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:647: warning: passing argument 1 of ‘dev_get_by_name’ from incompatible pointer type
/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:647: error: too few arguments to function ‘dev_get_by_name’
/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c: In function ‘rt28xx_probe’:
/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.c:1103: error: implicit declaration of function ‘SET_MODULE_OWNER’
make[2]: *** [/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux/../../os/linux/rt_main_dev.o] Error 1
make[1]: *** [_module_/home/jens/2008_0108_RT2860_Linux_STA_v1.5.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-10-generic'
make: *** [LINUX] Error 2[/FONT]

I am somewhat entering my desperate state - can you help me?

---

### Post by tritron on 2008-03-09
Your will not get the driver to compile with 2.6.24 and higher kernels. Now what you could do is get 2.6.23.17 kernel and compile install it reboot your notebook boot 2.6.23.17 kernel then compile driver and it will compile now. The driver does not follow linux standards so when you load the driver you will see ra0 but you need to do ifup ra0 make sure you setup ra0 in /etc/networks/interfaces. iwconfig  ra0 essid " " and the you will  be able to use dhcp.

---

### Post by xodeus on 2008-03-31
> **burningice64ta said:**
> No i got it to work using their gpl'd drivers i just didnt read the readme
Where to get those?

> **tritron said:**
> Your will not get the driver to compile with 2.6.24 and higher kernels. Now what you could do is get 2.6.23.17 kernel and compile install it reboot your notebook boot 2.6.23.17 kernel then compile driver and it will compile now. The driver does not follow linux standards so when you load the driver you will see ra0 but you need to do ifup ra0 make sure you setup ra0 in /etc/networks/interfaces. iwconfig  ra0 essid " " and the you will  be able to use dhcp.
So, when I get an older kernel and compile the module, can I just reuse it with the newer kernel without compiling? If yes then how?
Cause whe I "make install" the module is copied to the 2.6.23.XX kernel modules directory... Please help...

---

### Post by xodeus on 2008-04-01
couldn't get the driver to compile, so I tried the ndiswrapper way. I found a driver inf and sys on a fedora forum but for no help. When loaded into latest ndiswrapper, i get these errors in dmesg:
```
[   34.053345] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   34.138832] ndiswrapper: driver rt2860 (Ralink Technology, Corp.,06/27/2007, 1.00.03.0018) loaded
[   34.139081] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   34.139290] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   34.139794] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138B, count: 1, return_address: f8d0eb6b
[   34.139798] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x103
[   34.139839] ndiswrapper (mp_init:216): couldn't initialize device: C0010006
[   34.139843] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   34.139852] ndiswrapper (mp_halt:259): device f74da480 is not initialized - not halting
[   34.139854] ndiswrapper: device eth%d removed
[   34.139863] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[   34.139876] ndiswrapper: probe of 0000:0c:00.0 failed with error -22

```

---

### Post by xodeus on 2008-04-07
Good news everyone.
ralink has just mailed me a new version of this driver.
Get the source and compile you version from here
[http://www.ralinktech.com.tw/data/drivers/2008_0325_RT2860_Linux_STA_v1.6.1.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0325_RT2860_Linux_STA_v1.6.1.0.tar.bz2)

compiles and install fine with linux 2.6.24

---

### Post by Tsume on 2008-04-09
```
tsumeone@tsumeone-desktop:~/Desktop/2008_0325_RT2860_Linux_STA_v1.6.1.0$ make
make -C tools
make[1]: Entering directory `/home/tsumeone/Desktop/2008_0325_RT2860_Linux_STA_v1.6.1.0/tools'
gcc -g bin2h.c -o bin2h
bin2h.c:28:19: error: stdio.h: No such file or directory
bin2h.c:29:20: error: string.h: No such file or directory
bin2h.c:30:20: error: stdlib.h: No such file or directory
bin2h.c: In function ‘main’:
bin2h.c:34: error: ‘FILE’ undeclared (first use in this function)
bin2h.c:34: error: (Each undeclared identifier is reported only once
bin2h.c:34: error: for each function it appears in.)
bin2h.c:34: error: ‘infile’ undeclared (first use in this function)
bin2h.c:34: error: ‘outfile’ undeclared (first use in this function)
bin2h.c:42: warning: incompatible implicit declaration of built-in function ‘memset’
bin2h.c:45: warning: cast to pointer from integer of different size
bin2h.c:46: warning: cast to pointer from integer of different size
bin2h.c:49: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:54: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:57: warning: incompatible implicit declaration of built-in function ‘strcat’
bin2h.c:69: error: expected expression before ‘)’ token
bin2h.c:71: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:76: error: expected expression before ‘)’ token
bin2h.c:78: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:146: warning: incompatible implicit declaration of built-in function ‘sprintf’
bin2h.c:155: warning: incompatible implicit declaration of built-in function ‘exit’
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/tsumeone/Desktop/2008_0325_RT2860_Linux_STA_v1.6.1.0/tools'
make: *** [build_tools] Error 2
tsumeone@tsumeone-desktop:~/Desktop/2008_0325_RT2860_Linux_STA_v1.6.1.0$ 


```

If someone could tell me what I'm doing wrong, I'd greatly appreciate it ...

This is with the newest Hardy 8.04 beta and the latest Ralink drivers.  I have tried to do everything according to the readme but it's written in a way that someone of my skill level will have no way of understanding wtf they are trying to say.

---

### Post by xodeus on 2008-04-09
On ubuntu system you have to compile as root
You first need build-essential package:
```
sudo apt-get update && sudo apt-get install build-essential
```
then build and install the module as root:
```
sudo make && sudo make install && sudo reboot
```
This will build the module, install it in the right directories and reboot the system
Try this.

---

### Post by Tsume on 2008-04-09
So I don't really need to modify those files like the readme says?

Also... the only time I can get internet access is on Windows.  I have no way to get internet to use apt-get until the wireless works.

Is there any way for me to download the build essential thing in windows and transfer it over?

I'm on Hardy 8.04 btw, forgot if I mentioned that or not.

Edit:  I tried with sudo make, same thing.  I probably need the build essential.

---

### Post by xodeus on 2008-04-09
> **Tsume said:**
> So I don't really need to modify those files like the readme says?
You still have to modify the /os/linux/config.mk file corresponding to the way you would like o log in. 
If you're planning to use wicd then configure it like this:
```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

> **Tsume said:**
> Also... the only time I can get internet access is on Windows.  I have no way to get internet to use apt-get until the wireless works.

Is there any way for me to download the build essential thing in windows and transfer it over?
If you have an ubuntu install CD then you ca add it to your apt-repo

```
sudo apt-cdrom add
sudo apt-get install build-essential
```

---

### Post by sivlardemalle on 2008-04-11
> **xodeus said:**
> Good news everyone.
ralink has just mailed me a new version of this driver.
Get the source and compile you version from here
[http://www.ralinktech.com.tw/data/drivers/2008_0325_RT2860_Linux_STA_v1.6.1.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0325_RT2860_Linux_STA_v1.6.1.0.tar.bz2)

compiles and install fine with linux 2.6.24

New Ralink driver also works for me: laptop medion MD96630  + Ubuntu 7.10

---

### Post by xodeus on 2008-04-18
> **sivlardemalle said:**
> New Ralink driver also works for me: laptop medion MD96630  + Ubuntu 7.10
It's funny that they are working, cause, when I try to connect, it tries to get an IP, but nothing happens. can anyone help me with that? What output do you need? 
Just to mention, i'm using wicd to connect with wext. There were no not met dependencies when compiling the driver from source, and it compiles and loads without any problem. It's just that, when trying to connect it just tries to obtain an ip, and it doesn't matter if the network is protected or not.

---

### Post by xodeus on 2008-04-19
up with you... maybe someone new will see this one...

---

### Post by Mohhomad on 2008-04-23
I'm also having the same problem.  The driver works fine under 2.6.22 but whenever I try the latest version for 2.6.24 everything works except connecting to my network.  I can see it, just not connect.

---

### Post by dpatel on 2008-04-24
I was having a similar problem (i.e. could see wireless connections) but wouldn't connect. I got it to work by changing to WEP key rather than WPA.

Not sure if this new driver supports WPA? Anyone know?

---

### Post by fatahmy on 2008-05-13
If you use the driver comes from Ralink, you must use iwpriv <iface> set <ralink command from iwpriv_readme>=<value>. Do not use iwconfig to set your wireless unless there is futher notice from rt2x00 community.

---

### Post by xodeus on 2008-05-13
> **fatahmy said:**
> If you use the driver comes from Ralink, you must use iwpriv <iface> set <ralink command from iwpriv_readme>=<value>. Do not use iwconfig to set your wireless unless there is futher notice from rt2x00 community.

I do not understand this one...

---

### Post by fatahmy on 2008-05-13
I think your's is like mine. 11N, 20/40Mhz channel bandwidth and 300Mbps but not USB. You can refer to [http://fatah.afraid.org/files/rt2870-project/IWPRIV_USAGE](http://fatah.afraid.org/files/rt2870-project/IWPRIV_USAGE)

Example:

b> Config STA to link with AP which is SHARED/WEP(Authentication/Encryption)
	1. iwpriv ra0 set WirelessMode=5 (for 11N support)
	2. iwpriv ra0 set HtBw=1 (to enable 40MHz channel bandwidth)
// Both above to support 270Mbps, normal 54Mbps
	3. iwpriv ra0 set NetworkType=Infra
	4. iwpriv ra0 set AuthMode=OPEN
	5. iwpriv ra0 set EncrypType=WEP
	6. iwpriv ra0 set DefaultKeyID=1
	7. iwpriv ra0 set Key1="AP's wep key"
	8. iwpriv ra0 set SSID="AP's SSID"

Thanks.

---

### Post by fuzzywiggy on 2008-05-13
Jeez, after much messing about I finally got my EW-7728in card to run on compiled Ralink rt2860STA drivers, running at 270Mbs on WPA mode on Heron, although I have some bizarre niggles.

The steps I took, might be useful as a starting point for someone else with 7728in.
1. Pulled down the latest Ralink source ( 2008_0325_RT2860_Linux_STA_v1.6.1.0 ).
2. Ensured I had the build-essentials and my kernel headers ( 2.6.24-17-generic ) installed.
3. Unpacked the Ralinksource and edited the os/linux/config.mk and set ( HAS_WPA_SUPPLICANT=y ) and ( HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y )
4. Compiled and installed ( make / main install )
5. Edited the the file /etc/Wireless/RT2860STA/RT2860STA.dat, changed these settings ( I'm in the UK ):
```
CountryRegion=5
CountryRegionABand=7
CountryCode=GB
SSID=my_router_ssid
NetworkType=Infra
WirelessMode=5
Channel=0
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 

```
(The encrypted key you get from using command "wpa_passphrase ssid" )
6. edited /etc/modules and put rt2860sta in there
7. Set up my /etc/wpa_supplicant/sup.conf file with the following:

```
ctrl_interface=/var/run/wpa_supplicant
network={
ssid="my_router_ssid"
psk=xxxxxxxxxxxxxxx-encrypted string-xxxxxxxxxxxxxxxxxx
key_mgmt=WPA-PSK
proto=WPA
}

```

8. Rebooted

Now the wired stuff started happening, which I have yet to sort out. The ra0 device is loaded and appears in ifconfig, iwconfig and iwpriv listings, but it reports that it's connected at 1Mbs and no keys, nothing works. 

So I edited the /etc/network/interfaces, set the details I wanted:

```

auto ra0
iface ra0 inet static
wpa-conf /etc/wpa_supplicant/sup.conf
wpa-psk xxxxxxxxxxxxx-encrypted PSK-xxxxxxxxxxxxxxx
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid my_router_ssid
address 192.168.2.211
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1

```

Still no joy, the ifconfig reports that it all assigned but iwpriv and iwconfig still failed. SO I accidently read the README_STA with the Ralink source, they suggest the old wpa_supplicant test syntax, so I fired that up:

```

ifconfig ra0 down
ifconfig ra0 up
route add default gateway 192.168.2.1

```

Hey Presto! CHecking iwconfig shows that the ra0 device is now up at 270Mbs/s, the iwconfig "Encryption Key" is shown, whereas before it was blank. I had to add a default route so I could get out on the connection and add my DNS servers to resolv.conf. 

I rebooted and it all failed again! I then ran the ifconfig ra0 down; ifconfig ra0 up, route add, blah, blah again, the ra0 device came back up and connected the AP again! Something to do with bouncing the ra0 device. It's probably something stupid I am doing, I have messed up and mess about with so many compoennts, but the card at least appears to working at 270Mbs. Wireless-N and using WPA-PSK correctly, even if I have to manually kick it into touch to get it up. 

The silly thing I have left is FIrefox will not work, everything else is OK, so I had to install Konquerer into Gnome to get a browser to work with, bizarre!

Anyway, hope this helps someone off in the right direction.

---

### Post by xodeus on 2008-05-13
Congratulations. You're the first one I've heard of connecting. I'm going to try out your walkthrough and hope to get connected too... Thank you... Any other successfull stories?

---

### Post by fuzzywiggy on 2008-05-16
More info, managed to simplify the install some more.

OK so I was having to mess about upping and downing the interface to kick it into touch. I have been through and edited my /etc/network/interfaces file to look like this:

```
auto lo
iface lo inet loopback

iface ra0 inet static
address 192.168.2.211
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1

auto ra0

```

Next I removed the /etc/wpa_supplicant/sup.conf file I had set up, just deleted it.

Finally I removed NetworkManger-GNOME and NetworkManager packages, apparently a lot of the desktop apps look to NM to see if there is an active connection, if none in NM, then they go "offline", especially Firefox.

So after all that, I checked my /etc/Wirelss/RT2860STA/RT2860STA.dat was still right as described above and rebooted. 

Bang, the whole lot starts on it's own with no intervention, ready to use on the desktop no apps offline! wpa_supplicant is not running, at least there is no process, so I can only assume the 7728in card through the Ralink 2860 driver simply gets all it needs from the RT2860STA.dat file.

I managed to get all this working on an 8.04 desktop, but I am still not able to get it working yet on a 8.04 server based install. If/when I do I will try to post that too.

love
Fuzzywiggy

---

### Post by krutoileshii on 2008-05-19
Gave it a shot with default install of gutsy followed all the steps but can't seem to get it to connect. still keep getting stupid connected at 1Mbps

Any ideas?

---

### Post by krutoileshii on 2008-05-21
Ok, here is how far i got.

Every time i have to issue a iwconfig ra0 essid "YOU_ESSID" command in order for it to connect to it.
here is a catch. THe RT2860STA.dat file is setup and seems to be working also i'm using the WPA2 TKIP and i think that's were the problem is. i can't seem to be able to get out anywhere.

the link shows that it's connected at 270Mbps to my access point and that's about it. my thought on this is that it might be something to do with my WPA setup.

Can someone help?

---

### Post by krutoileshii on 2008-05-23
Hello everyone. i can confirm that it is possible to get the driver provided by 'Ralink' working.

Haven't figured out how to get it to do it automatically yet.
First thing i had to do was compile and install the driver then i had to manually run a couple iwpriv commands after that i just setup the network i was going to use in the NETWORK tool (So far only un-encrypted) and it connects just fine. currently on it. if someone could give me a hand with getting it to do it automatically and to set it up with WPA2PSK TKIP that would be really helpful.

---

### Post by dpatel on 2008-05-23
Hi - Let me go through what I did and see if it helps (not a tutorial as I'm no expert). I got to the point of making it work with WEP (not WPA). PS - if you email Ralink they do respond! I'm doing this from memory so forgive any errors!

Follow the instructions to compile the driver in the readme file you get with the driver. Don't forget to edit the config.mk as per earlier in this thread.

In a terminal copy the RT2860STA.dat file

```
cp RT2860STA.dat /etc/Wireless/RT2860STA/
```

Of course, you need to be in the directory where the .dat file is for above to work and you may need to first create Wireless and RT2860STA folders using sudo mkdir.

Then move to folder where rt2860sta.ko is:

```
cd os/linux
```

Then insert the module:

```
sudo /sbin/insmod rt2860sta.ko
sudo modprobe rt2860sta
sudo depmod -a
```

Then use iwconfig to check if your wireless card is setup.

```
iwconfig
```

Your wireless card should be listed.

Then you can use ifconfig to start your wireless card:
```

sudo ifconfig ra0 up
```

ra0 maybe different for you but iwconfig will tell you that.

Check with iwconfig again to see if it is now active.

At this point I had to actually disable and re-enable networking to get the wireless card searching: Just right click on the Network icon at the top right of your desktop (two little computers) and uncheck 'Enable Networking' and then right click icon again and re-enable. If you then left click on this icon a few secs later you should see a list of available network access points.

Click on the one you want to connect to and you will get asked for a password (assuming you have enabled WEP on your router). Enter your info and Ubuntu should store this.

Now to get your card to startup on boot:

```
sudo gedit /etc/init.d/rt61up
```

In the file add:

```
#!/bin/sh

sudo ifconfig ra0 up
```

Save and close.

Back in the terminal:

```
cd /etc/init.d
sudo chmod +x rt61up
cd /etc/rcS.d/
sudo ln - s /etc/init.d/rt61up S33rt61up

```

That should about do it. Re-boot and try. It should auto connect to your router on start up.

PS: I have not had to add anything to /etc/network/interfaces for this to work.

I've given up on the WPA unless someone can figure it out!

---

### Post by krutoileshii on 2008-05-23
IWconfig doesn't handle WPA2PSK or WPA for that sence wery well. iwprive does a better job at that. also i think it got something to do with network tool.

---

### Post by arikol on 2008-05-28
I've had to install this card twice now (a kernel update throw out my pretty config)

It turns out to be complex enough for a noob like me, but not really that bad.
I made it work by following a lot of the advice given here, then finding out a few extra things on my own. Linux and I now have a love/hate relationship ;)


Download the driver source from Ralink, and follow their instructions.
When you're in the source directory (wherever you untar'd it) write "sudo make && sudo install" the sudo in both parts is critical and not mentioned in the Ralink readme (they assume you're running as root).
EDIT:
  Above should say "sudo make && sudo  make install"

After that i copied the  RT2860STA.dat file to /etc/Wireless/RT2860STA as directed.
then "sudo /sbin/insmod rt2860sta.ko" EDIT: didn't work the same with the new driver
EDIT: changed case - then "sudo modprobe rt2860sta"  
then reboot

after that my wireless card was seen by "iwlist" as ra0, and "iwlist scanning" showed my router.
I then hand edited my /etc/network/interfaces file ("sudo gedit /etc/network/interfaces")
 this is how I set mine up:

[INDENT]auto lo
iface lo inet loopback


iface ra0 inet dhcp
wireless-essid nameofmyrouter
wireless-key s:mypassword (the s: means it's ascii)
wireless-ap hexnameofmyrouter(got it with "sudo iwlist scanning")
auto ra0 (my network card was labelled ra0 by iwlist)
[/INDENT]



then I hand edited /etc/Wireless/RT2860STA/RT2860STA.dat
use the readme included with the driver source for reference, but the main things that I needed to change or set were:
[INDENT]
CountryRegion=5
CountryRegionABand=7  (these 2 make sure you are using the full channel spectrum, if you know which ones you use you can change this)
SSID:"SSID of my router"

 then lower down in the file (note that I'm only using WEP because of my Nintendo DS)

AuthMode=WEPAUTO (easiest, wepauto does either wep or no encryption)
EncrypType=WEP 
WPAPSK=
DefaultKeyID=1
Key1Type=1 (1 means ascii, 0 means hex)
Key1Str=my asci password

[/INDENT]


After that it's just "sudo ifconfig ra0 down" (substiture ra0 with your interface)
and "sudo ifconfig ra0 up"

wait half a minute (maybe longer, I get impatient...), and presto firefox and opera play nice on the web.

EDIT:
a few fixes, used the new driver (22 may version). Tried the WebUI, that didn't work, used the other one and did it by hand using the above method, worked like a charm and didn't take too long (except catching my own mistakes in this help post ;) )

---

### Post by arikol on 2008-05-28
Deleted double post

---

### Post by xodeus on 2008-05-29
> **arikol said:**
> I've had to install this card twice now (a kernel update throw out my pretty config)

It turns out to be complex enough for a noob like me, but not really that bad.
I made it work by following a lot of the advice given here, then finding out a few extra things on my own. Linux and I now have a love/hate relationship ;)


Download the driver source from Ralink, and follow their instructions.
When you're in the source directory (wherever you untar'd it) write "sudo make && sudo install" the sudo in both parts is critical and not mentioned in the Ralink readme (they assume you're running as root).

After that i copied the  RT2860STA.dat file to /etc/Wireless/RT2860STA as directed.
then "sudo /sbin/insmod rt2860sta.ko"
then "sudo modprobe RT2860STA"
then reboot

after that my wireless card was seen by "iwlist" as ra0, and "iwlist scanning" showed my router.
I then hand edited my /etc/network/interfaces file ("sudo gedit /etc/network/interfaces")
 this is how I set mine up:

[INDENT]auto lo
iface lo inet loopback


iface ra0 inet dhcp
wireless-essid nameofmyrouter
wireless-key s:mypassword (the s: means it's ascii)
wireless-ap hexnameofmyrouter(got it with "sudo iwlist scanning")
auto ra0 (my network card was labelled ra0 by iwlist)
[/INDENT]



then I hand edited /etc/Wireless/RT2860STA/RT2860STA.dat
use the readme included with the driver source for reference, but the main things that I needed to change or set were:
[INDENT]
CountryRegion=5
CountryRegionABand=7  (these 2 make sure you are using the full channel spectrum, if you know which ones you use you can change this)
SSID:"SSID of my router"

 then lower down in the file (note that I'm only using WEP because of my Nintendo DS)

AuthMode=WEPAUTO (easiest, wepauto does either wep or no encryption)
EncrypType=WEP 
WPAPSK=
DefaultKeyID=1
Key1Type=1 (1 means ascii, 0 means hex)
Key1Str=my asci password

[/INDENT]


After that it's just "sudo ifconfig ra0 down" (substiture ra0 with your interface)
and "sudo ifconfig ra0 up"

wait half a minute, and presto firefox and opera play nice on the web.
I'll give this a spin now on the live env. before installing ubuntu. Don't want to install if it isn't working. But nevertheless, I hope that it will, because I'm tired of Vista... 
So there's no possibility to use any tools to connect yet?
What about the make config? What are the answers for the 2 questions? Y or N?

---

### Post by krutoileshii on 2008-05-29
Ok guys Ralink just posted a new driver a couple of days ago and it works out of the box no need to toy around with the RT2860.dat file. network manager cannot handle it well though or it's just me. just configure it manually through the network tool and you will be fine(also recommend WICD as it seems to be working perfectly with it)

---

### Post by Mohhomad on 2008-06-01
I have also been able to get the latest drivers (1.6.1) to work.  Standard configuration, nothing special.  I compiled the drivers then used the make install command.  I edited the RT2860STA.DAT file with my information (still not sure why this needs to be done, anybody have any ideas?) next I ifconfig ra0 up then I set network manager to manual configuration and punched in all the important info and it seems to be working so far.  Though the connection is really slow.  I'll try WICD later tonight and post something if there is a difference.

---

### Post by LAW-Mastermind on 2008-06-04
As many have or had problems with these driver, I joined to help you and tell you what i did to solve all problems I had.

Firts of all grab the new drivers from [ralink]("http://www.ralinktech.com.tw/data/drivers/2008_0522_RT2860_Linux_STA_v1.6.1.0.tar.bz2").
Unpack into a folder. 
```
Edit the file <your_folder_name>/os/linux/config.mk
```
Change the following lines:

```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

now go into the root of your folder and:
```
sudo make && sudo make install
```

To autostart the interface just do the following:
```
sudo gedit /etc/init.d/rt2860up
```

Paste this into the File:
```
#!/bin/sh

sudo ifconfig ra0 up
```

Now do the following:
```
cd /etc/init.d
sudo chmod +x rt2860up
sudo ln - s /etc/init.d/rt2860up /etc/rcS.d/S33rt2860up
```

Last but not least:
```
sudo rm /etc/Wireless/RT2860STA/RT2860STA.dat
```

EDIT:
your /etc/network/interfaces/ should look like this:
```

auto lo
iface lo inet loopback
```

Put a # in front of all other lines

Now everything should work like a charme, no need to use Wicd anymore.

---

### Post by GNUbee40 on 2008-06-05
Hey Mastermind!

Tried to follow your instructions (after trying all kinds of others). D

2 questions:

Why remove the rt2860.dat
What does the last instruction mean? (the one that starts with Edit)

Regards Nino

---

### Post by LAW-Mastermind on 2008-06-06
> **GNUbee40 said:**
> Hey Mastermind!

Tried to follow your instructions (after trying all kinds of others). D

2 questions:

Why remove the rt2860.dat
What does the last instruction mean? (the one that starts with Edit)

Regards Nino

1. The rt2860.dat is not neede anymore. So better remove it, in my case the driver got confused it the file was still present.

2. The last nstruction means you have to make sure that your ```
/etc/network/interfaces 
```
looks like this:
```
auto lo
iface lo inet loopback
```

---

### Post by GNUbee40 on 2008-06-06
Ok thanks RAW-Mastermind.

After following your instructions my Zepto Zpro2 card's LED is now flashing and iwconfig lists it as ra0. But WICD cannot see it at all. Do i have to reinstall Network Manager again?

---

### Post by mmxbass on 2008-06-06
> **LAW-Mastermind said:**
> Now everything should work like a charme, no need to use Wicd anymore.It is still far from working like a charm. Roaming mode doesn't work at all. Every time I do manual settings in network manager it forgets my WPA2 settings. I have to re-enter them every time I reboot. Interestingly, network manager seems to be set back to WPA Personal instead of WPA2 Personal every time I do this.

---

### Post by LAW-Mastermind on 2008-06-06
> **GNUbee40 said:**
> Ok thanks RAW-Mastermind.

After following your instructions my Zepto Zpro2 card's LED is now flashing and iwconfig lists it as ra0. But WICD cannot see it at all. Do i have to reinstall Network Manager again?

Its LAW-Mastermind ;)

I have the same Card. I reinstalled network-manager, wicd cant handle the Driver now, cause now it&#347; optimised for use with network-manager

> **hexnet said:**
> It is still far from working like a charm. Roaming mode doesn't work at all. Every time I do manual settings in network manager it forgets my WPA2 settings. I have to re-enter them every time I reboot. Interestingly, network manager seems to be set back to WPA Personal instead of WPA2 Personal every time I do this.

Did you do everythig, as i mentioned? 
Mine works perfekt now.

---

### Post by xodeus on 2008-06-06
This is just great. tried this on a fresh install of ubuntu hardy, but the performance of the wireless netowrk was very slow, so please mention before doing this on a freash install to update the system with these commands. They require thogh a working internet connection, like wired... :D
```
sudo apt-get update && sudo apt-get upgrade
```
Then reboot
```
sudo reboot
```
then install the last updates and reboot
```
sudo apt-get dist-upgrade && sudo reboot
```
before installing. It's also a requrement to have build-essential package installed.
```
sudo apt-get install build-essential
```
is it okay with you if I steal [your post and blog it]("http://ubuntuforums.org/showpost.php?p=5114684&postcount=41") on my personal blog, of course with your credits... :)

---

### Post by LAW-Mastermind on 2008-06-06
> **xodeus said:**
> This is just great. tried this on a fresh install of ubuntu hardy, but the performance of the wireless netowrk was very slow, so please mention before doing this on a freash install to update the system with these commands. They require thogh a working internet connection, like wired... :D
```
sudo apt-get update && sudo apt-get upgrade
```
Then reboot
```
sudo reboot
```
then install the last updates and reboot
```
sudo apt-get dist-upgrade && sudo reboot
```
before installing. It's also a requrement to have build-essential package installed.
```
sudo apt-get install build-essential
```
is it okay with you if I steal [your post and blog it]("http://ubuntuforums.org/showpost.php?p=5114684&postcount=41") on my personal blog, of course with your credits... :)

Sure, its just information i gathered all over the internet.
I'm happy if my post helps people to get there wireless working.

---

### Post by GNUbee40 on 2008-06-07
Hmmm... Double checked and did everything LAW-mastermind recommended, but still out of luck.
The card is listed, but does not provide any useful ioctls, so it cannot be configured manually by using *Iwpriv* or *iwconfig* or Network Manager. Roaming does not work. No wireless networks listed in Network Manager
Maybe i have to start all over with a new install of Ubuntu...?
Or how could i uninstall the card's driver in order to repeat the procedure. Do i use *Make clean*?

---

### Post by xodeus on 2008-06-08
But I now have rebooted and seem to have the issue that hexnet has. I've to enter my settings manually in network manager on every boot. 
It's even though better than not working at all, but I hope that someone will get a fix for WPA2-PSK soon and so the card can work in roaming mode... :D

---

### Post by xodeus on 2008-06-08
> **GNUbee40 said:**
> 
Or how could i uninstall the card's driver in order to repeat the procedure. Do i use *Make clean*?
To onload the driver invoke these commands:
As descrbed in README_STA #7
```
    
sudo /sbin/ifconfig ra0 down
sudo /sbin/rmmod rt2860sta
```
make clean only clears temporary files from the source dirs, if you have tried or did compile the driver before... It's recommended to run make clean before compiling just to be shure...

Remember to get the driver from the ralink taiwan site, not the global .com site.
LINK: [Ralink Taiwan]("http://www.ralinktech.com.tw/Home/Support/Linux.html")

---

### Post by GNUbee40 on 2008-06-08
Hey Mastermind og Xodeus!

After a clean fresh install and following all of your instructions it now works flawlessly.:guitar: 
All who like me have tried all kinds of other solutions before might consider starting all over with a fresh installation.

Many regards

---

### Post by xodeus on 2008-06-08
What about your encryption? What do you use? Do you have to enter your configuration manually in Network Manager on every boot?
Remember to rebuild the module and delete the .dat file on every kernel update...

I've made a script that rebuilds the module and deletes the .dat file automaticly. Just put the script in the rt2860 source directory, make it executable and run
```

chmod +x rt2860rebuild.sh
sudo rt2860rebuild.sh
```

---

### Post by GNUbee40 on 2008-06-08
Thanks Xodeus!

The information about unloading the driver might come handy some other time.
However i think i used the driver from the global side (the web site was in english). Still seems to work fine though. What's wrong with the global site?

Haven't tried to reboot yet. Hopefully still works. But i don't use WPA2 so...

---

### Post by GNUbee40 on 2008-06-08
Ouch!

After only 1 reboot I am back on wired network. Nothing works anymore :(
Not even manual config, the password is not stored, instead it stores a long key. 

Dont understand...

---

### Post by xodeus on 2008-06-08
> **GNUbee40 said:**
> Thanks Xodeus!


However i think i used the driver from the global side (the web site was in english). Still seems to work fine though. What's wrong with the global site?
The global site is always some weeks late with new drivers.

> **GNUbee40 said:**
> Ouch!

After only 1 reboot I am back on wired network. Nothing works anymore :(
Not even manual config, the password is not stored, instead it stores a long key. 

Dont understand...
That's the issue with our configuration too, then you have to "unlock" Network Manager, then fill it out with needed information and save again. It will then try to get a new IP ( if dhcp) or just connect. 
That's the only issue. I donøt know if it is the driver or the Network Manager that is buggy...

---

### Post by LAW-Mastermind on 2008-06-08
@All that have issues, what does your /etc/network/interfaces look like?
What version of network-manager do you use?

---

### Post by xodeus on 2008-06-08
```
mariusz@mariusz-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface ra0 inet dhcp
wpa-psk 714472606e94848XXXXXXXXXXXXXXXX67279485cc129ca96ff00b05c9f25bdf
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid xodeus.dk

auto ra0
mariusz@mariusz-laptop:~$ 

```
If I clear the file, then it will look like that on next reboot. When I say clear, then I let the 2 upper lines be there and take the rest out.

nm-applet 0.6.6

---

### Post by GNUbee40 on 2008-06-08
> **GNUbee40 said:**
> Ouch!

After only 1 reboot I am back on wired network. Nothing works anymore :(
Not even manual config, the password is not stored, instead it stores a long key. 

Dont understand...

Sorry have to correct my self!

Still works! :) I had turned off the network/Bluetooth switch on my Zepto laptop, because the manual stated, this switch did not work on the Zepto card, which always would be on. Obviously that's not entirely true. If you turn it off, the card will not be correctly initialized at startup. So keep it on, keep it on. 
Now again Roaming works and Password is remembered. Network manager switches back and forth between wired and wireless effortlessly. Nice!
BUT - i do not use WPA2 just WPA with PSK. 

BTW - My etc/Network/Interfaces looks precisely as before - the same two lines you suggested Mastermind. So i find it weird all this login info gets stored in Xodeus'. Isnt there a standard location in Linux where Login info and other network configuration gets stored?

Thanks for all the good advice btw.

---

### Post by LAW-Mastermind on 2008-06-09
> **xodeus said:**
> ```
mariusz@mariusz-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface ra0 inet dhcp
wpa-psk 714472606e94848XXXXXXXXXXXXXXXX67279485cc129ca96ff00b05c9f25bdf
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid xodeus.dk

auto ra0
mariusz@mariusz-laptop:~$ 

```
If I clear the file, then it will look like that on next reboot. When I say clear, then I let the 2 upper lines be there and take the rest out.

nm-applet 0.6.6

Please have a look if your rt2860sta.dat file is still present.
sudo rm /etc/Wireless/RT2860STA/RT2860STA.dat
then remove the lines except the first two in your /etc/network/interfaces file
Maybe you have to reboot and then remove the entrys.

---

### Post by xodeus on 2008-06-09
Hi again. I've reconfigured my router to use WPA instead of WPA2, and everything is working. roaming mode too... So it's the WPA2 part of the driver or wext that's not working properly... :D

---

### Post by GNUbee40 on 2008-06-10
Hi Xodeus! Thanks for the script btw :)

will try with WPA2 one of these days and see what happens.

But according to this Sticky [http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")
WPA2 with Ralink chipsets doesn't work yet. 

Regards

---

### Post by xodeus on 2008-06-10
thank you... But it's great that it is working again... :D
But just for your information. Before the 2.6.24-kernel or lets say in 7.10 rel of ubuntu, the driver worked flawlessly, with WPA2 too...

---

### Post by GNUbee40 on 2008-06-12
Hi again!

I am currently on WPA2-PSK with my Zpro2 card. However there still some instabilities:

[LIST]
Sometimes the card is not started up properly and roaming doesn't work. Mostly a simple script using ifconfig ra0 down and then up will fix this. Sometimes i have to reboot, though.
[/LIST]

[LIST]
WPA2 didn't work after 2nd reboot. AP was seemingly found, but logon failed. Later i discovered that the internet gateway (not same device as the AP) needed a restart. But even after that i still couldn't log on to my roomie's WPA2 AP, while connecting to my other roomie's WPA AP still worked. This morning i again get connected to the WPA2 protected AP. No idea why that is...[/LIST]

Note: Even when the WPA2 logon failed /etc/network/interfaces still did not get modified like it was the case with Xodeus' machine.

---

### Post by xodeus on 2008-06-12
It's strange that your network interfaces file doesn't get modified.
But glad that it's partially working. I'll not change the encrytpion untilll it work out of the box. 
I'm happy that I finally can use the card, and have linux installed on my laptop. I was getting sick and tired of Vista.

---

### Post by GNUbee40 on 2008-06-17
A little annoying:

After the latest kernel update, Wireless was completely dead.

Running lshw showed that the Ralink card was Unclaimed, which i believe means there is no driver loaded.

Xodeus rebuilding script really came in handy here. After rebuilding the driver and once again deleting the Rt2860sta.dat everything works fine again, although i still need to restart the card once in a while.

---

### Post by GNUbee40 on 2008-06-28
Hey Dudes!

After rebuilding the driver because of the kernel update things seemed to work initially, but then wirelless performance dived, and now the card hardly (if ever) can make contact to the two AP's we got. Network manager keeps asking for Passphrases constantly. 
Rebuilding the driver another time did not help. :confused:

---

### Post by Hendrik van den Boogaard on 2008-07-03
Yesterday I received my MSI Wind clone (Medion Akoya) and this laptop is equipped with a RT2860 card. I installed Ubuntu 8.04 (32 bit) with all updates and downloaded the Ralink driver. I followed the guide at page 4 but I cannot get the driver to work, nor in WEP neither in WPA.

I disabled roaming mode in the network manager and selected my Access Point. As soon as I close and keep watching the iwconfig output I can see the ESSID changing from "" to my Access point name. After about 5 seconds the Access point name is cleared again and so on.

Sometimes a key is also listed when the ESSID is not empty but it keeps on changing (maybe this is normal for WPA?) and I cannot ever get an IP address or something. 

Does anyone have this card running under the latest Hardy.

---

### Post by jojop2 on 2008-07-04
@Hendrik van den Boogard:
Try it with ndiswrapper and the driver on your original D-Drive (RECOVER).
Together with Wicd I got mine to work.

Only little problem is that I have to fill in the WPA Password every time again after reboot.

---

### Post by dwellmann on 2008-07-05
Hi,

got it working with the driver's internal WPA - support ( on Ubuntu 8.0.4.1, Kernel 2.6.24-19 ), here's what I've done:

1. Changed os/linux/config.mk 
    HAS_WPA_SUPPLICANT=n
    HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
2. make clean in driver's dir, make and make install
3. the following Script did it for me

```

reload()
{
        pkill -15 avahi-autoipd
        pkill -15 dhclient3

        ifconfig ra0 down
        rmmod rt2860sta
        sleep 1
        modprobe rt2860sta
}


mynetwork ()
{
        ifconfig ra0 up
        iwconfig ra0 essid <your essid here>
        iwpriv ra0 set AuthMode=WPAPSK
        iwpriv ra0 set EncrypType=TKIP
        iwpriv ra0 set WPAPSK=<your passphrase here in plain text>
        iwpriv ra0 set SSID=<your essid here>
        dhclient ra0
}


main()
{
        reload

        if [ "$1" == "mynetwork" ]
        then
             mynetwork
        fi
}


main $*

```

Ok, untill now I only tested WPA-PSK, later I'll test WPA2-PSK.

Update:
Only change AuthMode from WPAPSK to WPA2PSK and it works in WPA2 with TKIP.

Update 20080705/ 3 pm utc:
Forgot to say, that I uninstalled the network-manager. If anyone get this card going with network-manager and wpa_supplicant, give me short hint please.

Dirk

---

### Post by Hendrik van den Boogaard on 2008-07-05
Hello Dirk,

Thank you for your solution. At first it did not work at all but when I tried to connect to my access point in Windows, the same behavior was shown: connecting and disconnecting. I had to hard-reset my access point and set it all up again. When I did that Windows could connect and now it all runs fine in Linux as well!

Can you tell me what kind of language your script is? It looks like a c-shell script but how can I use it?

BTW: I see now that I kept the WPA settings in the config.mk at Y, although you suggest to set both to N

---

### Post by dwellmann on 2008-07-08
Ok, while using the card the above mentioned way I ran into Problems, when I'm in a Roaming - Network with two or more AP'S presenting the same SSID, the card permanent scanns the network, connects a very short period and releases again for scanning. I got no IP via DHCP and communication is not possible.

Even so, if i use a simple Accesspoint and a Rangeextender. In the momemnt the ralink -device detects the Rangeextender and the Accesspoint everything stops working and the card scanns but does not connect to the AP or the Rangeextender!

I think it's a driver bug, or have I something missconfigured? In Networks with a single AP the card works fine (OPEN,WPAPSK,WPA2PSK)


@Hendrik,
its simple bash-script. But it is not intendet for GUI-Users use. It's quite simple but does his job, if you want to use it, a made a quick example [here.]("http://wiki.piponline.net/doku.php?id=ht:installhowtos:ubuntu_on_medion_e1210:ralink_script")

Regards Dirk

Update 20080807/ 11:40 pm:
After setting FastRoaming from 0 to 1 the rt2860 works fine even in roaming situations.

---

### Post by GNUbee40 on 2008-07-08
Hey guyz!

Did you try the simple solution on page 5 of this thread?

Much more simple than all the other solutions - and so far the only one, that worked for me... Even though there are ups and downs...

---

### Post by dwellmann on 2008-07-08
@GNUbee40,

yes, but I had problems to connect with WPA and WPA2 using external wpa_supplicant. It did not work and this way everything is working, but network-manager does not. For me it is no problem I'm one of those "commandline-junkies". 8)

Regards Dirk

---

### Post by ddcc on 2008-07-12
I haven't been able to get WPA/WPA2 working at all with a 2860 chipset (the wireless connects, then drops, then connects, etc) with either the RT2860STA driver or ndiswrapper, so I've given up on it for now, however, I happened to notice that the router log showed a telnetd daemon, from which I telnet'ed in and realized it was a 2.4.30 BusyBox machine, which, even odder, happened to have RT2860.dat and hostapd.ra0.conf (this router is a RT2880). Anyway, in the hopes that they will be helpful, here they are:

RT2860.dat
```

Default
CountryRegion=0
CountryCode=US
WirelessMode=9
BasicRate=15
WmmCapable=1
TxBurst=0
APAifsn=3;7;1;1
APCwmin=4;4;3;2
APCwmax=6;10;4;3
APTxop=0;0;94;47
APACM=0;0;0;0
BSSAifsn=3;7;2;2
BSSCwmin=4;4;3;2
BSSCwmax=10;10;4;3
BSSTxop=0;0;94;47
BSSACM=0;0;0;0
AckPolicy=0;0;0;0
BssidNum=1
SSID=<myssid>
HideSSID=1
AutoChannelSelect=1
BeaconPeriod=100
DtimPeriod=1
RTSThreshold=2346
FragThreshold=2346
HT_MCS=33
TxPreamble=1
TxPower=95
NoForwarding=0
NoForwardingBTNBSSID=1
WiFiTest=1
AuthMode=WPA2PSK
EncrypType=AES
HT_HTC=0
HT_RDG=1
HT_LinkAdapt=0
HT_OpMode=0
HT_MpduDensity=4
HT_AutoBA=1
HT_AMSDU=1
HT_BAWinSize=16
HT_STBC=0
HT_GI=1
HT_BW=1
HT_EXTCHA=1
AccessPolicy0=0

```

hostapd.ra0.conf
```

driver=ralink
eapol_key_index_workaround=0
logger_syslog=0
logger_syslog_level=0
logger_stdout=0
logger_stdout_level=0
debug=0
interface=ra0
bridge=br0
ssid=<myssid>
wpa=2
ieee8021x=0
wps=0
wpa_group_rekey=1500
wpa_pairwise=CCMP
wpa_key_mgmt=WPA-PSK
wpa_passphrase=<mykey>

```

---

### Post by omgwtflol on 2008-07-12
Now do the following:
```
sudo chmod +x rt2860up
sudo ln - s /etc/init.d/rt2860up /etc/rcS.d/S33rt2860up
```

After doing the last line I get this:
ln: target `/etc/rcS.d/S33rt2860up' is not a directory

Im new to Linux.  Why isnt the directory there?

---

### Post by ddcc on 2008-07-12
Try removing the space between - and s (so it reads ln -s <etc>)?

---

### Post by omgwtflol on 2008-07-12
Err, I can see routers, but I cant connect to mine.  I switched to WPA TKIP.  Everytime I change the settings it just connects wired...ly.  :(

---

### Post by aussiebuddha on 2008-07-14
Hi All
I just bought an eee pc 1000h with a ralink 2860 card.
I managed to compile the driver with make, and install it with make install. but after that nothing.
the interface wont go up.

any ideas?
thanks.

---

