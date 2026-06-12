---
title: "HOWTO: Ralink rt2870 (Native) Kernel 2.6.24"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by pandapanda on 2008-04-25
Hi all,

As many people have pointed out the Ralink rt2870 driver will not compile OTB Hardy Heron. I have some simple patch instructions that will allow you to compile the driver ( available from [http://www.ralinktech.com.tw/data/drivers/2007_1220_RT2870_Linux_STA_v1.2.1.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2007_1220_RT2870_Linux_STA_v1.2.1.0.tar.bz2) ) and regain your wifi.

PRE:

- Alter the makefile(s) according to your needs, just as the README_STA states.

STEP 1:

- navigate to /include/rt2870.h and and a NULL terminator to RT2870_USB_DEVICES.

```
#define RT2870_USB_DEVICES	\
{	\
	{USB_DEVICE(0x148F,0x2770)}, /* Ralink */		\
	{USB_DEVICE(0x148F,0x2870)}, /* Ralink */		\
	{USB_DEVICE(0x0B05,0x1731)}, /* Asus */			\
	{USB_DEVICE(0x0B05,0x1732)}, /* Asus */			\
	{USB_DEVICE(0x0B05,0x1742)}, /* Asus */			\
	{USB_DEVICE(0x0DF6,0x0017)}, /* Sitecom */		\
	{USB_DEVICE(0x0DF6,0x002B)}, /* Sitecom */		\
	{USB_DEVICE(0x0DF6,0x002C)}, /* Sitecom */		\
	{USB_DEVICE(0x0DF6,0x002D)}, /* Sitecom */		\
	{USB_DEVICE(0x14B2,0x3C06)}, /* Conceptronic */		\
	{USB_DEVICE(0x14B2,0x3C28)}, /* Conceptronic */		\
	{USB_DEVICE(0x2019,0xED06)}, /* Planex Communications, Inc. */		\
	{USB_DEVICE(0x07D1,0x3C09)}, /* D-Link */		\
	{USB_DEVICE(0x14B2,0x3C07)}, /* AL */			\
	{USB_DEVICE(0x050D,0x8053)}, /* Belkin */		\
	{USB_DEVICE(0x14B2,0x3C23)}, /* Airlink */		\
	{USB_DEVICE(0x14B2,0x3C27)}, /* Airlink */		\
	{USB_DEVICE(0x07AA,0x002F)}, /* Corega */		\
	{USB_DEVICE(0x07AA,0x003C)}, /* Corega */		\
	{USB_DEVICE(0x07AA,0x003F)}, /* Corega */		\
	{USB_DEVICE(0x1044,0x800B)}, /* Gigabyte */		\
	{USB_DEVICE(0x15A9,0x0006)}, /* Sparklan */		\
	{USB_DEVICE(0x083A,0xB522)}, /* SMC */			\
	{USB_DEVICE(0x083A,0xA618)}, /* SMC */			\
	{USB_DEVICE(0x083A,0x7522)}, /* Arcadyan */		\
	{USB_DEVICE(0x0CDE,0x0022)}, /* ZCOM */			\
	{USB_DEVICE(0x0586,0x3416)}, /* Zyxel */		\
	{USB_DEVICE(0x0CDE,0x0025)}, /* Zyxel */		\
	{USB_DEVICE(0x1740,0x9701)}, /* EnGenius */		\
	{USB_DEVICE(0x1740,0x9702)}, /* EnGenius */		\
	{USB_DEVICE(0x0471,0x200f)}, /* Philips */		\
	{USB_DEVICE(0x14B2,0x3C25)}, /* Draytek */		\
	{USB_DEVICE(0x13D3,0x3247)}, /* AzureWave */	\
	{USB_DEVICE(0x083A,0x6618)}, /* Accton */		\
	{USB_DEVICE(0x15c5,0x0008)}, /* Amit */			\
	{USB_DEVICE(0x0E66,0x0001)}, /* Hawking */		\
	{USB_DEVICE(0x0E66,0x0003)}, /* Hawking */		\
	{USB_DEVICE(0x129B,0x1828)}, /* Siemens */		\
	{NULL}	\
}
```

STEP 2:

- navigate to /os/linux/rt_main_dev.c and replace static NDIS_STATUS rt_ieee80211_if_setup(struct net_device *dev, PRTMP_ADAPTER pAd) function with

```
static NDIS_STATUS rt_ieee80211_if_setup(struct net_device *dev, PRTMP_ADAPTER pAd)
{
	NDIS_STATUS Status;
	INT     i=0;
	CHAR    slot_name[IFNAMSIZ];
	struct net_device   *device;


	//ether_setup(dev);
	dev->hard_start_xmit = rt28xx_send_packets;
//	dev->set_multicast_list = ieee80211_set_multicast_list;
//	dev->change_mtu = ieee80211_change_mtu;
#ifdef CONFIG_STA_SUPPORT
#if WIRELESS_EXT >= 12
	dev->wireless_handlers = &rt28xx_iw_handler_def;
#if WIRELESS_EXT < 21
    dev->get_wireless_stats = rt28xx_get_wireless_stats;
#else
	dev->get_stats = rt28xx_get_wireless_stats;
#endif
#endif //WIRELESS_EXT >= 12
#endif // CONFIG_STA_SUPPORT //
	dev->open = rt28xx_open;
	dev->stop = rt28xx_close;
//	dev->uninit = ieee80211_if_reinit;
//	dev->destructor = ieee80211_if_free;
	dev->priv_flags = INT_MAIN;
	dev->do_ioctl = rt28xx_ioctl;
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,24)
	dev->validate_addr = NULL;
#endif


	// find available device name
	for (i = 0; i < 8; i++)
	{
#ifdef MULTIPLE_CARD_SUPPORT
		if (pAd->MC_RowID >= 0)
			sprintf(slot_name, "ra%02d-%d", pAd->MC_RowID, i);
		else
#endif // MULTIPLE_CARD_SUPPORT //
		sprintf(slot_name, "ra%d", i);
	    
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,5,0)
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,24)
		device = dev_get_by_name(dev->nd_net, slot_name);
#else
		device = dev_get_by_name(slot_name);
#endif
		if (device != NULL) dev_put(device);
#else
		for (device = dev_base; device != NULL; device = device->next)
		{
			if (strncmp(device->name, slot_name, 4) == 0)
				break;
		}
#endif
		if(device == NULL)  
			break;
	}
	
	if(i == 8)
	{
		DBGPRINT(RT_DEBUG_ERROR, ("No available slot name\n"));
		Status = NDIS_STATUS_FAILURE;
	} 
	else 
	{
#ifdef MULTIPLE_CARD_SUPPORT
		if (pAd->MC_RowID >= 0)
	        sprintf(dev->name, "ra%02d-%d", pAd->MC_RowID, i);
		else
#endif // MULTIPLE_CARD_SUPPORT //
		sprintf(dev->name, "ra%d", i);
		DBGPRINT(RT_DEBUG_INFO, ("Assign the net device name as %s\n", dev->name));
		Status = NDIS_STATUS_SUCCESS;
	}

	return Status;
	
}

```

STEP 3:

- navigate to /usr/src/linux-headers-2.6.24-16/include/linux/module.h and add #define SET_MODULE_OWNER(dev) do { } while (0) just above #endif /* _LINUX_MODULE_H */

STEP 4:

- navigate back to the drivers root
-make || make install
-cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat

STEP 5:

- navigate to /os/linux
- $/sbin/insmod rt2870sta.ko
- $/sbin/ifconfig ra0 inet YOUR_IP up

I recommend removing/commenting the addition to module.h after installing the driver.

Enjoy. I have only tested this connecting without no encryption so I have no idea if encryption will work. If anyone feels like taking the time to create a script or patch then please do so :) Hope it works for you all.

pandapanda

---

### Post by negora on 2008-04-25
You're my hero LOL. This issue has made me get desperated. I've been using ndiswrapper and the Vista 64 driver this afternoon, until Ralink answered me (I know they sent a patch to some people who asked), but the result has been a disaster: Some times wpa_supplicant worked... Others, the more, this wasn't able to get associated to my AP. I guess that ndiswrapper doesn't handle this Vista 64 driver very well.

I'm just going to try your solution, using WPA-CCMP and publish my results.

---

### Post by pandapanda on 2008-04-25
You will have to restart network to get it associated with network manager. I did this via GUI by right clicking the network manager -> enable networking and once more network manager -> enable network. I believe ifconfig ra0 up will also do the trick - just copied $/sbin/ifconfig ra0 inet YOUR_IP up from the readme :p

---

### Post by negora on 2008-04-25
You've done my day!!! :D I've followed your steps and it worked perfectly! At the beginning I did a stupid mistake, as I was so impatient and happy, that at the Step 3, I simply copied and pasted all the text, with your instruction "just above #endif /* _LINUX_MODULE_H */" included, ha ha ha. But checking the code carefully I realized about it. Ouch! :P

Well, I've a Dlink DWA-140 wireless adaptor and a Dlink DSL-2740B router, configured both to work using WPA2-PSK, and it works flawless, like it did on Ubuntu v. 7.10.

Many many many thanks pandapanda. I really appreciate your help, since this issue was driving me crazy and these people from Ralink, according to some opinions on the Internet, maybe took many days to answer.

Now, every time I see a piece of bamboo, I'll remind that you helped me, he he he. Nah, seriously, many thanks for this great guide ;) .

---

### Post by negora on 2008-04-25
Ops, by the way, maybe I give a second opportunity to the Network Manager, because I HATE this. Maybe it's because I only have used this for WiFi connections, but it never worked properly for me :/ . Everytime I've tested Ubuntu/Kubuntu have ended using Kwlan or none, configuring "/etc/networks" by hand ;) .

---

### Post by matthew.kent on 2008-04-27
Thank you for these instructions! I've moved these changes into an easy to apply patch and attached it here. 

Be sure to backup any existing /etc/Wireless/RT2870STA as the make install (stupidly) rm -rf's it. 

Here's the simplified instructions:
```

wget http://www.ralinktech.com.tw/data/drivers/2007_1220_RT2870_Linux_STA_v1.2.1.0.tar.bz2
tar jxf 2007_1220_RT2870_Linux_STA_v1.2.1.0.tar.bz2
gzip -d rt2870-v1.2.1.0_2.6.24.patch.gz
patch -p0 < rt2870-v1.2.1.0_2.6.24.patch
cd 2007_1220_RT2870_Linux_STA_v1.2.1.0
make && sudo make install

```

Slight addendum: attaching a modified version of the previous patch which disables the insane amount of debug being printed to the kernel ring buffer.

All working great with my Asus WL-160N.

---

### Post by pandapanda on 2008-04-27
Thank you for taking the time to put the instructions into a patch.  It appears that you have chosen to define the deprecated SET_MODULE_OWNER locally in the driver's source which is probably safest for inexperienced users, however, experienced users may wish to compile multiple drivers that made use of the macro and in this case it would be more efficient to add to <linux/module.h>. I believe that many other wireless drivers that are no longer compiling with 2.6.24 (due to similar cause) can be made to work using the same principle of this patch.

---

### Post by El-Doble-O on 2008-04-30
I executed the last line: "make && sudo make install" and this is what I got

[I]make -C tools
make[1]: Entering directory `/home/myloginname/2007_1220_RT2870_Linux_STA_v1.2.1.0/tools'
gcc -g bin2h.c -o bin2h
bin2h.c:28:19: error: stdio.h: No such file or directory
bin2h.c:29:20: error: string.h: No such file or directory
bin2h.c:30:20: error: stdlib.h: No such file or directory
bin2h.c: In function &#8216;main&#8217;:
bin2h.c:34: error: &#8216;FILE&#8217; undeclared (first use in this function)
bin2h.c:34: error: (Each undeclared identifier is reported only once
bin2h.c:34: error: for each function it appears in.)
bin2h.c:34: error: &#8216;infile&#8217; undeclared (first use in this function)
bin2h.c:34: error: &#8216;outfile&#8217; undeclared (first use in this function)
bin2h.c:42: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
bin2h.c:49: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:54: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:57: warning: incompatible implicit declaration of built-in function &#8216;strcat&#8217;
bin2h.c:69: error: expected expression before &#8216;)&#8217; token
bin2h.c:71: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:76: error: expected expression before &#8216;)&#8217; token
bin2h.c:78: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:146: warning: incompatible implicit declaration of built-in function &#8216;sprintf&#8217;
bin2h.c:155: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/myloginname/2007_1220_RT2870_Linux_STA_v1.2.1.0/tools'
make: *** [build_tools] Error 2[/I]

---

### Post by CMasami on 2008-05-02
El-Doble-O,

You have to install header and library files to build any C/C++ programs.
The simplest way is:
$ sudo apt-get install build-essential

---

### Post by Jackie999 on 2008-05-03
I'm extremely wet behind the ears here..only having used linux for a few days.  I'll try and lay out my question so it makes sense.
I followed the above steps (learnt a lot along the way) and *think* I'm almost there....BUT...my Belkin F5D8053 wireless adapter still shows as ndiswrapper - here is my lshw -C network output:
```
 *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:df:31:66:5b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2870 driverversion=1.52+Arcadyan Technology Corpora ip=192.168.0.101 multicast=yes wireless=IEEE 802.11g
```My etc/network/interfaces shows 
```

auto lo
iface lo inet loopback
```So my question..how do I know I followed instructions and it worked..and how do I make it load and the ndiswrapper not load?
Thanks very much..these forums and support staff are invaluable :)

---

### Post by Jackie999 on 2008-05-06
I've been trying for days to get this working..the ndiswrapper is freezing me hourly..so I have to get the native driver installed..
My usb is 1.1 and I wonder if that's my problem - anyone else got the ralink driver installed with the older usb  ?

---

### Post by Alien.col on 2008-05-06
> **Jackie999 said:**
> I've been trying for days to get this working..the ndiswrapper is freezing me hourly..so I have to get the native driver installed..
My usb is 1.1 and I wonder if that's my problem - anyone else got the ralink driver installed with the older usb  ?

Follow this guide: [http://ubuntuforums.org/showthread.php?t=783366](http://ubuntuforums.org/showthread.php?t=783366)

It installs the native rt2570 driver, could work

---

### Post by TLZ on 2008-05-12
**@matthev.kent:** Thanks for posting an easy to apply patch. I've used this with success on a computer with my Dlink DWA-140, however I now need it on another computer. I did the same thing and after I compiled and installed the drivers Ubuntu(8.04) reported that I was using restricted drivers. 

However, that's where the fun stops. My network manager displays a wireless connection but it doesen't do much(not even display networks). So I ran lshw to see if it was there, and it was but it was disabled. It does not show up in Network Tools though. (Only my regular ethernet is there.)

I figured a simple "ifconfig ra0 inet up" would fix it but that returns this:
[PHP]SIOCSIFFLAGS: Operation not permitted[/PHP]

I'm quite a newbie to Ubuntu so sorry if I'm making a stupid mistake here. 

Any help would be appriciated. :)

**Edit: nevermind, I just used ndiswrapper and windows-drivers instead!**

---

### Post by XEQT on 2008-05-20
> **TLZ said:**
> **@matthev.kent:** Thanks for posting an easy to apply patch. I've used this with success on a computer with my Dlink DWA-140, however I now need it on another computer. I did the same thing and after I compiled and installed the drivers Ubuntu(8.04) reported that I was using restricted drivers. 

However, that's where the fun stops. My network manager displays a wireless connection but it doesen't do much(not even display networks). So I ran lshw to see if it was there, and it was but it was disabled. It does not show up in Network Tools though. (Only my regular ethernet is there.)

I figured a simple "ifconfig ra0 inet up" would fix it but that returns this:
[PHP]SIOCSIFFLAGS: Operation not permitted[/PHP]

I'm quite a newbie to Ubuntu so sorry if I'm making a stupid mistake here. 

Any help would be appriciated. :)

**Edit: nevermind, I just used ndiswrapper and windows-drivers instead!**

How did you get the ndiswrapper to work ?
I have the Dlink usb DWA-142 and are looking for a solution.
If you could tell me how i would love to hear that !!

// XEQT

---

### Post by Absurd on 2008-05-22
in my experience, rt2870 works horribly with ndiswrapper

---

### Post by aarnink on 2008-05-23
Hi,

Thanks for this info, I have tried to install my Eminent EM4550 USB WirelessN stick using the 1.3.0 drivers from ralink. I run Ubuntu 8.04 X64.

After setting up network from the Ubuntu menu I notice that iwconfig shows:

ra0       RT2870 Wireless  ESSID:"aarnink_N"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:60:B3:A6:F9:5A   
          Bit Rate=270 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx
          Link Quality=92/100  Signal level:-48 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

so all is well I thought, but I cannot ping, even the router doesnt respond

If I run ifconfig this is the result

ra0       Link encap:Ethernet  HWaddr 00:60:b3:a6:f2:30  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::260:b3ff:fea6:f230/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33703 errors:107 dropped:0 overruns:0 frame:0
          TX packets:1470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6036838 (5.7 MB)  TX bytes:127230 (124.2 KB)

Can anyone help me? Im totally wasted after 2 extensive days of searching for a solution

---

### Post by negora on 2008-05-25
Hi again to you all:

Today I've had to set up my laptop with the last Kubuntu. I also have a RT2870 WiFi USB stick installed on it and I've decided to check the Ralink website to check if something had changed since last time. And I've realized that **they have updated their drivers for Linux.**

I've tryed to compile them with the last version of the Ubuntu kernel (2.6.27) and everything has been done ok. It even seems to connect to my network (or that's what the output messages say). However, wpa_cli isn't able to work with it and there's not connection. Has anyone faced the same problem?

I think I'l try to compile with the v. 2.6.24 headres and try again. Maybe that has something to do...

Salutes.

---

### Post by aarnink on 2008-05-27
Hi negora,

Did you have any succes with the new rt2870 drivers (ver 1.3) on kubuntu 8.04? 

I only managed to get a working connection on a completely open router (no security set). All other attempts failed, even with WEP 64 bit key.

I'd very much appreciate a helping hand...

Richard

---

### Post by negora on 2008-05-27
Hi aarnink!:

Although I'm very busy these days I could try with the headers of the version 2.6.24... And I got the same result :( . The wpa_supplicant application tells that everything is ok and that the connection to the AP was successful. However, executing wpa_cli returns an error because it could not connect.

I haven't had enough time to check what's wrong but, by now, I believe that we can use the old drivers that our partner pandapanda patched for us ;) .

If anyone have news about this issue I would be pleased to listen about it :D .

PD: By the way, I'm trying to connect to a WiFi network with both WPA1 and WPA2 encryption.

---

### Post by aarnink on 2008-05-30
Hi negora,

Finally it works! I received an email with updated drivers from Ralink. I have posted them on this forum, Look here: [http://www.uluga.ubuntuforums.org/showthread.php?t=202834&page=143](http://www.uluga.ubuntuforums.org/showthread.php?t=202834&page=143)

Hopefully it works for you as well

gr, Richard

---

### Post by negora on 2008-05-30
**aarnink:** Thanks for your help ;) . In my case Ralink never answered, ha ha ha. I'll download those and try this afternoon. I also hope that Ralink publish the updated ones on their website so other people don't suffer from the same problem. Again, thank you very much :D .

---

### Post by tatoniss on 2008-06-01
HI im new to ubuntu but i installed hardy harion on a computer ans connected it to a modem to use cox high speed internet. when i type a site in and click go it brings me to a cox instll page, when i click next it says browser or os not supported but it worked on the live cd on another computer. so I am trying to use a usb wirless card, d-link dwa-140 version 2.0,to connect to my wireless but it is not regonized by ubuntu so could you give me instuctions as to why i keep getting directed to cox or how to install the drivers you recently recevied by email, I am having trouble understanding how. thankyou

---

### Post by mpns2mpns2 on 2008-06-15
Hi

I've got this error
Can you help me !
Thanks alot
Marc


>make && sudo make install

make -C tools
make[1]: entrant dans le répertoire « /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/tools »
gcc -g bin2h.c -o bin2h
make[1]: quittant le répertoire « /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/tools »
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.24-17-generic/build SUBDIRS=/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.24-17-generic »
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/md5.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/mlme.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/action.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/ba_action.o
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/ba_action.c: Dans la fonction «convert_reordering_packet_to_preAMSDU_or_802_3_packet» :
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/ba_action.c:1376: attention : assignment makes integer from pointer without a cast
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/eeprom.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../common/dfs.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../sta/assoc.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../sta/aironet.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../sta/auth.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../sta/sync.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../sta/sanity.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../sta/connect.o
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../sta/connect.c: Dans la fonction «MakeIbssBeacon» :
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../sta/connect.c:2468: attention : format «%d» expects type «int», but argument 2 has type «long unsigned int»
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../sta/connect.c:2468: attention : format «%d» expects type «int», but argument 6 has type «long unsigned int»
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../sta/wpa.o
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_linux.o
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_linux.c: Dans la fonction «duplicate_pkt» :
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_linux.c:545: attention : passing argument 1 of «memmove» makes pointer from integer without a cast
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_linux.c:547: attention : passing argument 1 of «memmove» makes pointer from integer without a cast
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_linux.c: Dans la fonction «ClonePacket» :
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_linux.c:631: attention : assignment makes integer from pointer without a cast
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_linux.c: Dans la fonction «update_os_packet_info» :
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_linux.c:653: attention : assignment makes integer from pointer without a cast
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_linux.c: Dans la fonction «wlan_802_11_to_802_3_packet» :
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_linux.c:673: attention : assignment makes integer from pointer without a cast
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_linux.c: Dans la fonction «send_monitor_packets» :
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_linux.c:865: attention : format «%d» expects type «int», but argument 3 has type «long unsigned int»
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_linux.c:912: attention : assignment makes integer from pointer without a cast
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_linux.c:920: attention : assignment makes integer from pointer without a cast
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_profile.o
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_profile.c:223: attention : «rtinet_aton» defined but not used
  CC [M]  /home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_main_dev.o
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_main_dev.c: Dans la fonction «rt_ieee80211_if_setup» :
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_main_dev.c:671: attention : assignment from incompatible pointer type
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_main_dev.c:694: attention : passing argument 1 of «dev_get_by_name» from incompatible pointer type
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_main_dev.c:694: erreur: trop peu d'arguments pour la fonction «dev_get_by_name»
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_main_dev.c: Dans la fonction «rt28xx_probe» :
/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_main_dev.c:1157: erreur: déclaration implicite de la fonction « «SET_MODULE_OWNER» »
make[2]: *** [/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux/../../os/linux/rt_main_dev.o] Erreur 1
make[1]: *** [_module_/home/marc/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0/os/linux] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.24-17-generic »
make: *** [LINUX] Erreur 2
marc@ubuntu-marc:~/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0$ 
marc@ubuntu-marc:~/Bureau/2007_1220_RT2870_Linux_STA_v1.2.1.0$

---

### Post by lukemack on 2008-06-27
Has anyone tried the 2008_0528_RT2870_Linux_STA_v1.3.0.0 version from the ralink site?

I can compile it but get this warning from iwconfig:

Warning: Driver for device ra0 has been compiled with an ancient version
of Wireless Extension, while this program support version 11 and later.
Some things may be broken...


I used the latest version of build-essential on Hardy to compile it.

thanks,

lukemack.

---

### Post by pmorton on 2008-07-22
Yes.  I've got an rt2870 working with the 2008_0528_RT2870_Linux_STA_v1.3.0.0 driver, having used pandapanda's patches at the head of this thread. Only I can't get Network Manager to bring the adapter up. It puts all the right stuff into /etc/network/interfaces, but it won't list the available ESSID's and it won't connect with encryption active. It does connect with no encryption, but that's hardly a long-term option. 

The RT2870 wireless utility RutilT (apt-get install rutilt) does work, though, finding the ESSID's and connecting after asking for a WEP key.  So wifi works but each boot requires  a manual hook-up using RutilT. My conclusion is that it's a Network Manager problem. Does anyone know any different?

---

### Post by lukemack on 2008-07-23
I have it working now too. On boot, I have to disable and enable networking via network manager and then it comes up fine. WPA-PSK encryption works fine (you need to compile the driver with the correct options in the makefile for that).

Didnt know about the rtutil thing, though the driver comes with the equivalent utility on my hackintosh partition ;-)

My guess is the problems are probably a combination of the badly written driver, poor documentation and network-manager, which though I've never had a major problem, people often bitch about. 

Let me know if you want to combine on trying to get a fix for it. I didnt get any response from Ralink technology so the Ubuntu community or these people are probably the best bet:

[http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/)

---

### Post by GepettoBR on 2008-08-30
I got my DWA-140 to work with WPA Personal encryption using these instructions ([http://ubuntuforums.org/showpost.php?p=5400203&postcount=6](http://ubuntuforums.org/showpost.php?p=5400203&postcount=6)) but now I have to run "sudo modprobe rt2780sta" at start-up for it to work. I added the line to /etc/rc.local as a temporary fix, but if memory serves me right there should be a way to make the module load normally with boot. Can anyone help me remember? :)

P.S.: The D-Link website claims to have a Beta Linux driver for the DWA-140, but it looks like all they did was host the 1.2.1 version of the Ralink driver on their own website.
P.S.2: ndiswrapper didn't work at all with the Vista32 driver, and allowed me to access only unencrypted networks with the XP/2k driver. Compiling the ralink driver is just as easy as installing ndisgtk and the Windows driver, and yields far better results.

---

### Post by Jackie999 on 2008-08-30
There is a new driver on the ralink site [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) dated 07/18/2008 which I've tried a few times. 
Can anyone who's gotten it working tell me what changes, if any, are required to compile/install on Hardy 2.6.24 ?
I've tried a few times and it appears to compile okay but still I don't have a device in iwconfig. Could somebody let me know if there are changes I need to make in /etc/network/interface or /etc/modules - or should the 'make install' have made changes (mine didn't)
Thanks.

---

### Post by GepettoBR on 2008-08-30
> **Jackie999 said:**
> There is a new driver on the ralink site [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) dated 07/18/2008 which I've tried a few times. 
Can anyone who's gotten it working tell me what changes, if any, are required to compile/install on Hardy 2.6.24 ?
I've tried a few times and it appears to compile okay but still I don't have a device in iwconfig. Could somebody let me know if there are changes I need to make in /etc/network/interface or /etc/modules - or should the 'make install' have made changes (mine didn't)
Thanks.

This is exactly what happened to me. See my previous post for how I solved it (it's actually very simple, though I suspect there should be a better way to do it):
> **GepettoBR said:**
> I got my DWA-140 to work with WPA Personal encryption using these instructions ([http://ubuntuforums.org/showpost.php?p=5400203&postcount=6](http://ubuntuforums.org/showpost.php?p=5400203&postcount=6)) but now I have to run "sudo modprobe rt2780sta" at start-up for it to work. I added the line to /etc/rc.local as a temporary fix, but if memory serves me right there should be a way to make the module load normally with boot. Can anyone help me remember? :)

I followed the linked instructions, but using the latest drivers from the Ralink website (I did this today) and rebooted. ifconfig would only display eth0 and the loopback interface, but upon running ```
modprobe rt2780sta
``` as root, ra0 appeared. By adding the modprobe line to /etc/rc.local (before the line that says "ifconfig ra0 up", naturally) I managed to get it working on every successive boot, of which there were a total of seven so far. I get high up/down speeds on Transmission, I can connect to other machines on the LAN, and all the while using WPA/WPA2 encryption.

AFAIK the /etc/rc.local file which I wrote these lines to is something of a list of extra commands Ubuntu runs as root right after booting up, or right after logging in, so adding a command to the file would be like adding it to Preferences>Sessions, except it gets run by the root account (which is necessary to load kernel modules and activate network interfaces).

On a sidenote, the driver thus compiled works much better than the Windows driver *on Windows*. The same computer running XP loses the connection every ten minutes or so, and under Ubuntu my uptimes so far have been as long as the computer was on.

---

### Post by Jackie999 on 2008-08-30
Thanks for the pointers GepettoBR ..but still no go...I did a fresh format/reinstall and followed your instructions on the linked post with these results:
I did a few things differently, for example, the ralink driver I used was 07/18/2008 - I think you used one from May (which I've used as well with same failure)
Your post shows "make" and "make install" I did "sudo make" and "sudo make install"
I also navigated to the "2008_0718_RT2870_Linux_STA_v1.3.1.0/os/linux/" and typed 
```
sudo /sbin/insmod rt2870sta.ko
```When I typed the following I got the error
```
jackie@ubuntu:~$ sudo ifconfig ra0 up
ra0: ERROR while getting interface flags: No such device
jackie@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

```I tried sudo modprobe rt2870sta then the sudo ifconfig ra0 up ...but the device isn't in the iwconfig list and I don't know how to get it there :(

---

### Post by GepettoBR on 2008-08-30
I used the Ralink_2008_0718_RT2870_Linux_STA_v1.3.1.0 driver, which I downloaded this morning. From the filename, it's the same date as yours. I'm quite sleepy now, but I can think of four noteworthy points. I'll try and help more tomorrow.

You're correct to use "sudo" before those commands, the poster just happened to be in a root shell already. As for the other thing you did different, did you run that command from the folder that contains rt2870sta.ko? It seems obvious, but we do sometimes forget.

The post I linked to mentioned not having to copy a certain .dat file; yet when I followed his instructions I found that the .dat file was already where it was supposed to be. Maybe you should check on that.

I had to do a similar fix with a DWL-G122 in Gutsy (supported OOTB in Hardy) and the instructions also mentioned ra0, but mine came up as eth1. With ndiswrapper, the DWA-140 was wlan1, with the current fix it's ra0. Maybe the interface name is just messed up. What's your irda0 supposed to represent?

Finally, mine only worked after rebooting. Did you try rebooting before running iwconfig?

---

### Post by Jackie999 on 2008-08-31
Thanks for the help GepettoBR, you asked where I ran the rt2870sta.ko from - I was in the "2008_0718_RT2870_Linux_STA_v1.3.1.0/os/linux/" folder, which I think is correct.
As for the irda0 - I'm guessing that's the infrared on the lappy (for printer?) which has never been used.
And the .dat file you mentioned, I think I've tried installing this driver at least 6 times now and that RT2870STA.dat file is always in the /etc/Wireless/RT2870STA/ folder where it belongs - I've never done anything there.

---

### Post by GepettoBR on 2008-08-31
That's very strange, it seems we've done the exact same thing and have achieved very diffeent results. Maybe it's a firmware problem. My DWA-140 is HW version B1 and Firmware version 1.11 (it's written in the back of the device). I do remember that my 802.11g adapter (also from D-Link) had different fixes for each HW version on the WifiDocs. Some worked OOTB, some required ndiswrapper or compiling drivers and one didn't work at all - at the time.

If you've tried using the ndiswrapper method before doing this, then did you uninstall the Windows driver? Conflicting drivers may be what's keeping your computer from recognizing the device.

Even though the wireless interface doesn't show up in iwconfig, does the device appear when you type ```
lsusb
``` in a terminal?

---

### Post by Jackie999 on 2008-08-31
Yes, the ndiswrapper enabled me to use the usb stick (mine is the Belkin F5D8053 v3  - 802.11n ) but the ndiswrapper caused so many freezes that it rendered the computer useless. As for conflicting drivers ..thats why I reformatted and tried again yesterday..with the same failure :(
I've just started fresh again..this time with Fedora 9 - hopefully I'll have better luck.
Thanks again for all your help it's very much appreciated.

---

### Post by GepettoBR on 2008-08-31
Well, I'm just sorry I couldn't help you make it work. And there's no entry for your adapter on WifiDocs either...

With ndiswrapper, did you try with all the available Windows drivers (For Windows Vista, XP, 2000, etc)? Like I mentioned earlier, I could get some functionality with the XP/2000 drivers but none with Vista; maybe under a different Windows driver you'll be able to satisfactorily use ndiswrapper with your card.

---

### Post by Jackie999 on 2008-08-31
Wellllll.....I didn't try the other windows drivers, only the one that came with the device.  But to be honest..the reason I moved to linux was to get away from all things windows :) so..to fight with the windows drivers in linux (i.e. ndiswrapper) didn't seem worthwhile..I figured my time was better spent trying distros.

---

### Post by GepettoBR on 2008-08-31
> **Jackie999 said:**
> Wellllll.....I didn't try the other windows drivers, only the one that came with the device.  But to be honest..the reason I moved to linux was to get away from all things windows :) so..to fight with the windows drivers in linux (i.e. ndiswrapper) didn't seem worthwhile..I figured my time was better spent trying distros.

Yeah, I feel the same way... but after spending money on a usb stick it kind of sucks to not be able to use it. I'll keep scavenging the interwebs and if I find something I'll let you know. Until the, best of luck to you! :)

---

### Post by Jackie999 on 2008-08-31
Thanks ...who knows..I may be back on Hardy by tomorrow :) The driver doesn't even compile under Fedora ...so so much for that ...there is always SUSE though ...:)

---

### Post by GepettoBR on 2008-08-31
Did you remember to install build-essentials before trying to compile the driver in Fedora?

---

### Post by Jackie999 on 2008-09-01
Yep..I did the 

# yum install gcc gcc-c++ make kernel-headers kernel-devel 
then got a load of errors and asked for help and was told "it appears that the driver you are attempting to compile isn't compatible with the kernel version you have"

So now I'm back to Ubuntu..this time I'm trying the 8.10 alpha 4 Intrepid Ibex version :)
which doesn't work with the wireless either..but I'm used to that.

---

### Post by aextance on 2008-09-30
I am coming up against an "Invalid module error" with this, both when doing a modprobe, and also when trying to follow the instructions in the Ralink readme on loading the driver. 

Watching the install process, although the build file is in /lib/modules/2.6.24-19-generic, the driver is installed to /lib/modules/2.6.24-19-386. Is this likely to be an issue?

When I look at "hardware drivers" under the system administration menu it shows the RT2870 driver as being installed, lsusb shows that the device is a RT2870 adaptor, but ifconfig ra0 up fails to show anything and sudo modprobe RT2870.sta gives a fatal, invalid module error. 

Can anyone explain what's wrong?

---

### Post by GepettoBR on 2008-10-01
This may sound stupid, but did just copying the files from /lib/modules/2.6.24-19-386  to /lib/modules/2.6.24-19-generic work?

Do you have both versions of the kernel or only the generic version? If you have both, does booting with the 2.6.24-19-386 kernel allow the driver to work?

There may be some parameter in the makefile where you can specify your kernel version before installing.

---

### Post by Jackie999 on 2008-10-01
aextance, my problem was it seemed to compile fine..but when all was done..there was no ra0 listed in iwconfig.

The answer was that my device was missing from the driver and I'll post a link of how I was advised to fix it ...also how I used the newest driver 1.4.0.0.

[http://ubuntuforums.org/showthread.php?t=919044](http://ubuntuforums.org/showthread.php?t=919044)

Hope this helps ...this linux wireless battle can keep you awake nights :)

Oh..and by the way
> but ifconfig ra0 up fails to show anything and sudo modprobe **RT2870.sta** gives a fatal, invalid module error. 


There is no period in that ..should be - sudo modprobe rt2870sta

---

### Post by primaxx on 2008-10-02
I just want to inform you that Ralink has published a new driver (Version 1.4.0.0).
[http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")

When following the included instructions, it worked like a charm for me.

---

### Post by GepettoBR on 2008-10-02
> **primaxx said:**
> I just want to inform you that Ralink has published a new driver (Version 1.4.0.0).
[http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")

When following the included instructions, it worked like a charm for me.

Did anyone who had already gotten the previous driver to work test this and notice any improvements? I might give it a whirl this weekend (though I'm really hoping that the Intrepid beta will have this working out of the box).

---

### Post by GepettoBR on 2008-10-03
Hello, all, posting from the Intrepid Beta!

My D-Link DWA-140 was not recognized OOTB (it didn't even appear in lsusb), but installing the ralink driver version 1.4.0.0 following [these instructions](http://ubuntuforums.org/showpost.php?p=5400203&postcount=6) (except I did not have to add anything to /etc/rc.local, and roaming mode does not need to be disabled) got me working perfectly: I can manage the interface with Network Manager, connect to WPA-encrypted networks in Wireless N mode and my speed is as high as it should be.

---

### Post by Nutt's on 2008-10-06
hello,
using the newest driver 1.4.0.0. I also have a problem when doing the "insmod" or "modprobe".

In fact, during the "make" I have a warning:
```
cnuttens@ubuntuCN:~/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0$ sudo make
sudo: unable to resolve host ubuntuCN
[sudo] password for cnuttens: 
make -C tools
make[1]: entrant dans le répertoire « /home/cnuttens/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools »
gcc -g bin2h.c -o bin2h
make[1]: quittant le répertoire « /home/cnuttens/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools »
/home/cnuttens/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/cnuttens/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.24-19-rt/build SUBDIRS=/home/cnuttens/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.24-19-rt »
  CC [M]  /home/cnuttens/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_init.o
  LD [M]  /home/cnuttens/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "there_is_no_init_MUTEX_LOCKED_for_RT_semaphores" [/home/cnuttens/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.ko] undefined!
  LD [M]  /home/cnuttens/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.ko
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.24-19-rt »
cp -f /home/cnuttens/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.ko /tftpboot
```

But after that, it seems to have no problem with the "make install":
```
cnuttens@ubuntuCN:~/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0$ sudo make install
sudo: unable to resolve host ubuntuCN
make -C /home/cnuttens/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux -f Makefile.6 install
mkdir: ne peut créer le répertoire `/etc/Wireless': Le fichier existe
make[1]: entrant dans le répertoire « /home/cnuttens/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux »
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/cnuttens/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.24-19-rt
make[1]: quittant le répertoire « /home/cnuttens/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux »

```

But after, the problems come back:
```
cnuttens@ubuntuCN:~/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0$ sudo insmod os/linux/rt2870sta.ko 
sudo: unable to resolve host ubuntuCN
insmod: error inserting 'os/linux/rt2870sta.ko': -1 Unknown symbol in module

```

So I tried the modprobe:
```
cnuttens@ubuntuCN:~/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0$ sudo modprobe rt2870sta
sudo: unable to resolve host ubuntuCN
FATAL: Error inserting rt2870sta (/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/rt2870sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

As it advises to see dmesg:
```

cnuttens@ubuntuCN:~/Desktop/rt2870/2008_0925_RT2870_Linux_STA_v1.4.0.0$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Linux version 2.6.24-19-rt (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP PREEMPT RT Wed Aug 20 20:13:12 UTC 2008 (Ubuntu 2.6.24-4.6-generic)
....
[ 7937.030160] rt2870sta: Unknown symbol there_is_no_init_MUTEX_LOCKED_for_RT_semaphores

```

And we find again the "there_is_no_init_MUTEX_LOCKED_for_RT_semaphores" as in the "make" and I don't know how to solve it. I looked in the different files from "2008_0925_RT2870_Linux_STA_v1.4.0.0" for this expression "there_is_no_init_MUTEX_LOCKED_for_RT_semaphores" but I didn't find it..

Does someone could help me?
thanks

sorry for my English I'm French-speaking.

---

### Post by aextance on 2008-10-07
I'm about to try the new September Ralink driver, but Nutt's problem looks similar to what I got when I tried to make without changing the make file to point at the right "build" folder. 

From what I can tell, the MUTEX_LOCKED file is a kernel file like the Build files - is there definitely one in the folder that the make file's pointing at (possibly /usr/src/linux-headers-2.6.24-19-rt from your entry)? 

Also, could the "sudo: unable to resolve host ubuntuCN" message be part of the problem? 

Maybe try the following thread for that, and then try sudo make again?

[http://ubuntuforums.org/showthread.php?t=723361]("http://ubuntuforums.org/showthread.php?t=723361")

---

### Post by aextance on 2008-10-07
Arrgh - the new driver gives me a new problem!

When going through the make process, I get the following output:

andy@andyslaptop:~/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870$ sudo make
make -C tools
make[1]: Entering directory `/home/andy/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/andy/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870/tools'
/andy/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870/tools/bin2h
make: /andy/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870/tools/bin2h: Command not found
make: *** [build_tools] Error 127
andy@andyslaptop:~/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870$

I think I'm getting to grips with Ralink's info in the driver readme, but can anybody help me with what the following means please?:

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS

I'm not sure that has anything to do with the "Error 127", but I thought I should ask while I'm posting. 

Any suggestions would be much appreciated!

---

### Post by GepettoBR on 2008-10-07
> **aextance said:**
> Arrgh - the new driver gives me a new problem!

When going through the make process, I get the following output:

andy@andyslaptop:**~/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870**$ sudo make
make -C tools
make[1]: Entering directory `/home/andy/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/andy/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870/tools'
/andy/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870/tools/bin2h
make: /andy/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870/tools/bin2h: Command not found
make: *** [build_tools] Error 127
andy@andyslaptop:~/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870$

I think I'm getting to grips with Ralink's info in the driver readme, but can anybody help me with what the following means please?:

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS

I'm not sure that has anything to do with the "Error 127", but I thought I should ask while I'm posting. 

Any suggestions would be much appreciated!

That's not the driver, it's the WebUI. I have no idea why you'd need a WebUI for the client end of the wireless connection, though. The driver download is right beneath the WebUI download in Ralink's web page.

---

### Post by aextance on 2008-10-07
Ah yes, good point. I thought just unzipping the driver out of the WebUI would work but I was wrong. :oops:

So, now I'm back to the

FATAL: Error inserting rt2870sta (/lib/modules/2.6.24-19-386/kernel/drivers/net/wireless/rt2870sta.ko): Invalid module format

error on sudo modprobe rt2870sta. Could it have something to do with the os/linux/config.mk file do you think? The readme says I should tell it about GCC and LD, but I'm not sure what to tell it?

---

### Post by GepettoBR on 2008-10-07
I don't know, the only things I changed on my config.mk file were
HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
Are you sure that the TARGET in the Makefile is set to LINUX?

---

### Post by Domas on 2008-10-09
Hi all,

Can someone help me to get module working on boot? I did "sudo make install", added "alias ra0 rt2870sta" to /etc/modules, but still no luck to load module. Everytime after reboot I have to go to /os/linux and sudo /sbin/insmod rt2870sta.ko to load it. :(

---

### Post by Domas on 2008-10-09
Ok, got it work, just had to change "alias ra0 rt2870sta" to "rt2870sta", but got another issue. After reboot Ubuntu crashes: 

ct  9 22:45:31 community /usr/sbin/cron[5357]: (CRON) INFO (Running @reboot jobs)
Oct  9 22:45:32 community kernel: [   48.096939] [drm] Initialized drm 1.1.0 20060810
Oct  9 22:45:32 community kernel: [   48.101277] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct  9 22:45:32 community kernel: [   48.101287] PCI: Setting latency timer of device 0000:00:02.0 to 64
Oct  9 22:45:32 community kernel: [   48.101378] [drm] Initialized i915 1.6.0 20060119 on minor 0
Oct  9 22:45:33 community dhclient: DHCPREQUEST of 192.168.1.3 on ra0 to 255.255.255.255 port 67
Oct  9 22:45:44 community dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
Oct  9 22:45:51 community kernel: [   67.078573] NET: Registered protocol family 10
Oct  9 22:45:51 community kernel: [   67.079054] lo: Disabled Privacy Extensions
Oct  9 22:45:52 community dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
Oct  9 22:45:53 community avahi-daemon[4956]: Registering new address record for fe80::20e:3bff:fe0c:955 on ra0.*.
Oct  9 22:46:01 community dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
Oct  9 22:46:02 community kernel: [   77.882596] ra0: no IPv6 routers present
Oct  9 22:46:04 community anacron[5824]: Anacron 2.3 started on 2008-10-09
Oct  9 22:46:04 community anacron[5824]: Normal exit (0 jobs run)
Oct  9 22:46:13 community gdm[5317]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

So I have to login one more time and then boots ok. Is there any way to make module load after a while, just when Ubuntu is booted?

---

### Post by GepettoBR on 2008-10-09
I'd say remove the line from /etc/modules first to revert this crash (since it started when you added the line, right?) and run "modprobe rt2870sta" as root. This *should* make the driver load on boot but maybe not (read below).

With a previous version of the driver, I had the same problem of it not loading at boot. I added the modprobe line above to /etc/rc.local and it worked.

---

### Post by Nutt's on 2008-10-11
hello,
I come back with a very good new! Problem solved!! for months I've been fighting with it but now it's ok!

So, in fact with "-rt" kernels the problem seems to come regularly, and I found the post of someone with the same warning during the installation of his webcam.
The only thing I had to do is: 
to edit "2008_0925_RT2870_Linux_STA_v1.4.0.0./include/rtmp.h" and 
to change "struct semaphore" into "struct compat_semaphore" on the lines 2716, 2717, 2718 and 2720.

I'm so Happy! :-D

I hope it'll solve aextance's problem too!
 
and thx for your help!
(ps: I also solved my "sudo" problem with the link of aextance!)

---

### Post by aextance on 2008-10-19
Interestingly enough, Nutt's modification was useful to me in that it enabled me to see the Ralink driver in System>Admin>Hardware Drivers, which I had been able to do with the previous drivers, but not 1.4.0.0. 

Still, sudo modprobe rt2870sta is still coming up against the same invalid module format error. 

And Gepetto, yes the target in the Makefile is set to Linux. Copying the driver files from /lib/modules/2.6.24-19-386 to /lib/modules/2.6.24-19-generic did not work - the references in the makefile for the build files refer to generic, but the rest refers to 386 - the build files are normally all that are in my generic folder. I only have the 2.6.24-19-386 kernel. 

My next plans are:
1) To try ndiswrapper, to see if that tells me anything else
2) The invalid module format error seems to mean that there is some mismatch between my makefile and my kernel, so I will try and go through these with a fine-tooth-comb - as much as I can with my limited knowledge - to look for a reason.
3) Upgrade to Intrepid Ibex - apart from the appearance, how is that going Gepetto?

---

### Post by GepettoBR on 2008-10-20
> **aextance said:**
> 3) Upgrade to Intrepid Ibex - apart from the appearance, how is that going Gepetto?

Very well, actually. On my Hardy box, while the 1.4.0.0 driver does work, it requires setting the network interface to "manual" on Network Manager, so no roaming mode or wardriving. My Intrepid install still required me to manually compile the driver for the 2.6.27-4-generic kernel, but then it worked great with open, WEP, WPA and WPA2 networks, was manageable from Network Manager and the driver showed up in Hardware Drivers.

I have yet to test the 2.6.27-7-generic kernel, since the machine I'm testing Intrepid on has a wired connection to my router. I'll do it today if I have the time and post the results.

---

### Post by GepettoBR on 2008-10-20
As promised, here are the instructions for installing the Ralink rt2870 driver version 1.4.0.0 on kernel version 2.6.27-7-generic (on the Ubuntu 8.10 Intrepid Ibex beta):

1)Download the driver from Ralink's website: [[Direct link to file](http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2)] or [[Link to download page](http://www.ralinktech.com/ralink/Home/Support/Linux.html)]

2)Extract the archive and enter the directory.

3)gedit ./os/linux/config.mk #if running on KDE, do kate ./os/linux/config.mk instead
Change the following values from _n_ to _y_:
HAS_WPA_SUPPLICANT
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT

**4, 5 and 6 must be done as root**

4)make #see notes below

5)make install

6)insmod ./os/linux/rt2870sta.ko

7)ifconfig ra0 up

After a few seconds, Network Manager will display the available wireless networks.

**Additional notes**[list]
[*]Before installing the driver, the device (mine is the D-Link DWA-140, revision B1) was correctly identified in lsusb, but did not show up as a network interface. After installing, the driver name was appended to the lsusb information: ```
Bus 001 Device 004: ID 07d1:3c09 D-Link System DWA-140 802.11n Adapter [ralink rt2870]
```

[*]Injecting and other similar features were not tested. I might run a WEP cracking test later.

[*]During step 4 (make), I ran into an error message. This did not affect the installation. Here's the snippet: ```

 Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: Found 1 section mismatch(es).
```

[*]I obtained a connection speed of 270 Mb/s on a computer sitting next to the router (~50cm with the monitor and the PC itself as the only physical obstacles), I expected a full 300 Mb/s, since at the time of the test this was the only wireless client.

[*]Hotplugging works, no need to enable/disable networking or repeating ifconfig ra0 up like with previous versions.

[*]The interface is up on reboot and attempts to connect to a network. For some reason, the nm-applet only displayed the signal strength on the taskbar after the first reboot (before that it simply displayed the two computers "connected" icon).

[*]This procedure worked for me, but I do not guarantee it will work for you.[/list]

---

### Post by newsman1970 on 2008-10-22
hi, GepettoBR
is this guid will work with the asus WL-160N USB, that is what i have, and i still have the 2.6.24 kernel. i am still new to ubuntu and trying to learn.
please and thank you,

---

### Post by MichaelSM on 2008-10-23
Bye.

---

### Post by GepettoBR on 2008-10-23
> **newsman1970 said:**
> hi, GepettoBR
is this guid will work with the asus WL-160N USB, that is what i have, and i still have the 2.6.24 kernel. i am still new to ubuntu and trying to learn.
please and thank you,

Yes, this should work on the 2.6.24 kernel and for any device that uses the rt2870 chipset, and according to Google your does. Let us know if you have any problems, and we'll try to help you.

---

### Post by GepettoBR on 2008-10-23
> **MichaelSM said:**
> RALink chipset supported in Hardy.

Having updated to Hardy (Linux Mint 5 (Elyssa) well, Hmm. Looks like Hardy even with Network Manager finds a home for RALINK chipsets. 

One can buy as I did a TP-Link TL-WN321G USB WIFI unit for $16 which is cheap.

Works out of the box. 

Buggered if I know why.

No need for wcid.

Plug it in, configure wireless. Done.

Mike.
Hello, Mike. Either you're posting in the wrong thread or you didn't pay much attention to what's going on here. :)

Ralink is a manufacturer, they make lots of chipsets. Some are supported out of the box by the current kernels, and some aren't.

The device you mentioned uses the rt73 chipset, which is supported OOTB since Hardy (my DWL-G122 rev C1 from D-Link, for example, uses the same chipset), however the rt2870 drivers, for now, have to be compiled manually. That's what this thread is for - not for debating which adapter we should buy or discussing which one works best.

Also, this thread is about drivers, not network managers. WICD does not affect how a driver works, it simply helps manage the network interface - which will only exist if the driver is properly installed.

Paulo.

---

### Post by thor240z on 2008-10-23
I'm running on Hardy, and I'm fairly certain I have the driver installed properly as per the directions earlier in the thread.  The problem I'm having is that in the Network Manager, it detects the networks in the area, but won't connect to them.

I did notice that when I run lsusb, it incorrectly detects my USB adapter as being Atheros.  I'm using an Airlink AWLL6080(USB) and verified it uses the RT2870F chipset by taking apart the enclosure.

Is there a default driver I need to deactivate?  Or a way to force the RT2870 driver?  Any other thoughts/suggestions?

---

### Post by MichaelSM on 2008-10-23
[QUOTE=MichaelSM;6018078]RALink chipset supported in Hardy.



Post removed by author.

---

### Post by GepettoBR on 2008-10-24
> **thor240z said:**
> I'm running on Hardy, and I'm fairly certain I have the driver installed properly as per the directions earlier in the thread.  The problem I'm having is that in the Network Manager, it detects the networks in the area, but won't connect to them.

I did notice that when I run lsusb, it incorrectly detects my USB adapter as being Atheros.  I'm using an Airlink AWLL6080(USB) and verified it uses the RT2870F chipset by taking apart the enclosure.

Is there a default driver I need to deactivate?  Or a way to force the RT2870 driver?  Any other thoughts/suggestions?

I suggest looking at the output of lsmod to see if there are any Atheros drivers loaded. If so, you can blacklist them by adding a line to /etc/modprobe.d/blacklist that reads "blacklist <driver's name>". Then, you can try to insmod rt2870sta again.

---

### Post by thor240z on 2008-10-24
Here's my lsusb & lsmod output.  I can't find any Atheros drivers there:

xbmc@xbmc-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 413c:3012 Dell Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1784:0008  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 14b2:3c23 Atheros Communications Inc 
Bus 001 Device 001: ID 0000:0000  
xbmc@xbmc-desktop:~$ lsmod
Module                  Size  Used by
rt2870sta             499796  1 
snd_rtctimer            4640  0 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
ipv6                  267780  18 
speedstep_lib           6532  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
video                  19856  0 
output                  4736  1 video
battery                14212  0 
af_packet              23812  2 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
lp                     12324  0 
rfkill_input            5760  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
b43                   144548  0 
rfkill                  8596  3 rfkill_input,b43
mac80211              165652  1 b43
lirc_mceusb2           14980  1 
cfg80211               15112  1 mac80211
lirc_dev               15732  1 lirc_mceusb2
usbhid                 32128  0 
led_class               6020  1 b43
hid                    38784  1 usbhid
input_polldev           5896  1 b43
nvidia               7825536  24 
snd_hda_intel         344856  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
i2c_core               24832  1 nvidia
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  18 snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
intel_agp              25492  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 nvidia,intel_agp
evdev                  13056  4 
soundcore               8800  1 snd
pcspkr                  4224  0 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
ata_generic             8324  0 
ata_piix               19588  2 
pata_acpi               8320  0 
ohci1394               33584  0 
floppy                 59588  0 
ssb                    34308  1 b43
libata                159344  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151436  4 sbp2,sg,sd_mod,libata
uhci_hcd               27024  0 
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
e1000                 126016  0 
usbcore               146412  6 rt2870sta,lirc_mceusb2,usbhid,uhci_hcd,ehci_hcd
thermal                16796  0 
processor              37384  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

Anywhere else I can look?

---

### Post by GepettoBR on 2008-10-25
thor240z, the rt2870sta driver appears to be properly installed and loaded. If the device is working properly, I don't think it's a problem that lsusb has got the wrong name for it.

Network Manager 0.7 (the Intrepid version) can manage the rt2870 devices in roaming mode, but 0.6.6 (the current Hardy version) can't. In my case, I got my connection up by manually configuring the connection settings for one specific network (my home network). Here's how you can do that:

1. Click the nm-applet in your taskbar and select "Manual configuration" to open the Network Settings window. Then, click "Unlock" at the bottom of the window and enter your password.

2. Select your wireless connection and click the "Properties" button.

3. Now, uncheck the "Enable roaming mode" box and select your access point's ESSID from the drop-down list (or enter it manually).

4. Select your password type (WEP ascii, WEP hex, WPA or WPA2) and enter your password.

5. Fill in your connection settings. If you don't know what they are, select Automatic configuration (DHCP).[color=white]

6. ?????

7. PROFIT![/color]

You may need to disable and re-enable networking by right-clicking nm-applet for this to take effect.

Hope this helps,

Paulo

---

### Post by GepettoBR on 2008-11-05
There's a firmware update at the Ralink page, does anyone know how I can go about applying it?

---

### Post by mestrini on 2008-12-07
> **aextance said:**
> Arrgh - the new driver gives me a new problem!

When going through the make process, I get the following output:

andy@andyslaptop:~/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870$ sudo make
make -C tools
make[1]: Entering directory `/home/andy/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/andy/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870/tools'
/andy/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870/tools/bin2h
make: /andy/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870/tools/bin2h: Command not found
make: *** [build_tools] Error 127
andy@andyslaptop:~/rt2870/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0/RT2870$

I think I'm getting to grips with Ralink's info in the driver readme, but can anybody help me with what the following means please?:

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS

I'm not sure that has anything to do with the "Error 127", but I thought I should ask while I'm posting. 

Any suggestions would be much appreciated!

I believe the issue is with the path

I had the same error message until i followed this guide: [http://ubunturt2870.pbwiki.com/FrontPage](http://ubunturt2870.pbwiki.com/FrontPage)

remember that unix systems are case sensitive and you have a folder called "RT2870" when should be rt2870

hope it helps

cheers

---

### Post by gyzzofytal on 2009-01-02
Hi, Gepettobr
In the common directory of the drivers (1.4.0.0) exist a file called rt2870.bin.
If you download the firmware (07/10/2008) this file is found here but isn't the same version... Should replace it?

forgive my English

---

### Post by gyzzofytal on 2009-01-02
Another question,
if I want to install the driver for rt2870 chipset is neccessary to install ubuntu or I can use the live cd?

---

### Post by GepettoBR on 2009-01-03
> **gyzzofytal said:**
> Hi, Gepettobr
In the common directory of the drivers (1.4.0.0) exist a file called rt2870.bin.
If you download the firmware (07/10/2008) this file is found here but isn't the same version... Should replace it?

forgive my English

> **gyzzofytal said:**
> Another question,
if I want to install the driver for rt2870 chipset is neccessary to install ubuntu or I can use the live cd?

Hi, sorry I took long to respond, I was on vacation and away from the internet for two weeks until today.

I don't actually know how to install the firmware update. The driver installation is for the OS (in this case, Ubuntu or any other distro based on Linux 2.6.24 and above). It does work on the LiveCD environment since it doesn't require a reboot, but when you do reboot the LiveCD won't save your changes and you'll have to compile the driver again. However it is the firmware installation works, though, I don't se why it couldn't be done from a LiveCD as well as a regular install, provided you have access to all the necessary software.

---

### Post by aextance on 2009-01-11
> **mestrini said:**
> I believe the issue is with the path

I had the same error message until i followed this guide: [http://ubunturt2870.pbwiki.com/FrontPage](http://ubunturt2870.pbwiki.com/FrontPage)

remember that unix systems are case sensitive and you have a folder called "RT2870" when should be rt2870

hope it helps

cheers
Well, in the end I upgraded to Intrepid, followed that Howto and had no problems at all. Now posting through the RT2870 adapter card in question!

A guy I know suggested that my problems may have been caused by upgrading to Hardy through Ubuntu's automatic software upgrade system rather than clean installing. I had only intended to clean install hardy, but created an Intrepid disk my mistake. Seems good so far, though I switched back to the Hardy wallpaper 'cos it's much prettier. 

Thanks all.

---

### Post by cloud9ine on 2009-01-19
I followed the steps and installed the driver. I can now see networks but cannot connect. Even to an unsecured network, it asks me to select credentials.

With WEP or WPA-PSK, it is doing an ASCII to hex conversion, so if my key is 13579, the key it displays is 3133353739 . Even for my WPA key, it does the same. It simply fails to connect.

---

### Post by GepettoBR on 2009-01-25
> **cloud9ine said:**
> I followed the steps and installed the driver. I can now see networks but cannot connect. Even to an unsecured network, it asks me to select credentials.

With WEP or WPA-PSK, it is doing an ASCII to hex conversion, so if my key is 13579, the key it displays is 3133353739 . Even for my WPA key, it does the same. It simply fails to connect.

This is odd. My password is also stored in hex, but I can connect nonetheless. Are you sure you installed the latest build of the driver?

---

### Post by t_virus on 2009-03-31
hello,
i did all described in the previous page at ubuntu wiki but i cant 'make'

can someone help me with this?
thanks

> 

root@mauro-laptop:/home/mauro/rt2870# make
make -C tools
make[1]: Entrando no diretório `/home/mauro/rt2870/tools'
gcc -g bin2h.c -o bin2h
make[1]: Saindo do diretório `/home/mauro/rt2870/tools'
/home/mauro/rt2870/tools/bin2h
cp -f os/linux/Makefile.6 /home/mauro/rt2870/os/linux/Makefile
make  -C  /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/mauro/rt2870/os/linux modules
make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/mauro/rt2870/os/linux/../../common/crypt_md5.o
In file included from /home/mauro/rt2870/include/rtmp_chip.h:47,
                 from /home/mauro/rt2870/include/rt_config.h:47,
                 from /home/mauro/rt2870/include/crypt_md5.h:47,
                 from /home/mauro/rt2870/os/linux/../../common/crypt_md5.c:27:
/home/mauro/rt2870/include/chip/rt2870.h:33:2: error: #error "For RT2870, you should define the compile flag -DRTMP_USB_SUPPORT"
/home/mauro/rt2870/include/chip/rt2870.h:37:2: error: #error "For RT2870, you should define the compile flag -DRTMP_MAC_USB"
In file included from /home/mauro/rt2870/include/chip/rt2870.h:41,
                 from /home/mauro/rt2870/include/rtmp_chip.h:47,
                 from /home/mauro/rt2870/include/rt_config.h:47,
                 from /home/mauro/rt2870/include/crypt_md5.h:47,
                 from /home/mauro/rt2870/os/linux/../../common/crypt_md5.c:27:
/home/mauro/rt2870/include/chip/mac_usb.h:171: error: &#8216;MAX_TXBULK_SIZE&#8217; undeclared here (not in a function)
/home/mauro/rt2870/include/chip/mac_usb.h:184: error: expected specifier-qualifier-list before &#8216;PURB&#8217;
/home/mauro/rt2870/include/chip/mac_usb.h:210: error: expected specifier-qualifier-list before &#8216;PURB&#8217;
/home/mauro/rt2870/include/chip/mac_usb.h:240: error: expected specifier-qualifier-list before &#8216;PIRP&#8217;
In file included from /home/mauro/rt2870/include/rt_config.h:56,
                 from /home/mauro/rt2870/include/crypt_md5.h:47,
                 from /home/mauro/rt2870/os/linux/../../common/crypt_md5.c:27:
/home/mauro/rt2870/include/rtmp.h:645: error: &#8216;TX_RING_SIZE&#8217; undeclared here (not in a function)
/home/mauro/rt2870/include/rtmp.h:653: error: &#8216;RX_RING_SIZE&#8217; undeclared here (not in a function)
/home/mauro/rt2870/include/rtmp.h:661: error: &#8216;MGMT_RING_SIZE&#8217; undeclared here (not in a function)
make[2]: ** [/home/mauro/rt2870/os/linux/../../common/crypt_md5.o] Erro 1
make[1]: ** [_module_/home/mauro/rt2870/os/linux] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.27-11-generic'
make: ** [LINUX] Erro 2
root@mauro-laptop:/home/mauro/rt2870# 


---

### Post by t_virus on 2009-03-31
i did install it after my previous replay with 
[https://launchpad.net/~henrik-hw0/+archive/ppa](https://launchpad.net/~henrik-hw0/+archive/ppa)

but in the network manager sais its 'unmanaged'. i tried ifconfig ra0 up and nothing...

network restart wont do:

> mauro@mauro-laptop:/etc/init.d$ network restart
bash: network: command not found
mauro@mauro-laptop:/etc/init.d$ 

---

### Post by GepettoBR on 2009-03-31
IIRC I got past Error 2 in make by runing it as root. That shouldn't be necessary, but for some reason it worked. I can't remember if it was with ALSA or this driver, though.

Anyways, try "sudo make" instead of "make".

---

### Post by t_virus on 2009-03-31
> **t_virus said:**
> i did install it after my previous replay with 
[https://launchpad.net/~henrik-hw0/+archive/ppa](https://launchpad.net/~henrik-hw0/+archive/ppa)

but in the network manager sais its 'unmanaged'. i tried ifconfig ra0 up and nothing...

network restart wont do:



thankx for the replay. i installed this driver instead. i only cant manage it. can u help me? 
iwconfig says 'mode=auto' and sould be 'managed'. right?

---

### Post by GepettoBR on 2009-03-31
> **t_virus said:**
> thankx for the replay. i installed this driver instead. i only cant manage it. can u help me? 
iwconfig says 'mode=auto' and sould be 'managed'. right?

just run "sudo iwconfig ra0 mode managed" to change the mode to managed.

---

### Post by t_virus on 2009-03-31
sorry again gepettoBR

this is what i got:

> mauro@mauro-laptop:~$ sudo iwconfig ra0 mode managed
[sudo] password for mauro: 
mauro@mauro-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


obrigado pla paciencia GepettoBR:D

---

### Post by GepettoBR on 2009-03-31
Odd, it looks like your command was just ignored. Can you pleas epost the output of ifconfig as well as iwconfig?

Não há de quê :)

---

### Post by olddave1 on 2009-04-01
Hi,

Glad I found this thread. I have an RT2870 in the form of a Tendo Mini 11n. But I do not get as far as any of you have. The 'sudo make' fails. Initially with:
```

make  -C /lib/modules/2.6.27-7-server/build SUBDIRS=/home/dwynter/2009_0302_RT2870_Linux_STA_v2.1.0.0/os/linux modules
make: *** /lib/modules/2/6/27-7-server/build: No such file or directory. Stop.

```

Then I added the /lib/modules/2.6.27-7-server/build directory and get
```

make  -C /lib/modules/2.6.27-7-server/build SUBDIRS=/home/dwynter/2009_0302_RT2870_Linux_STA_v2.1.0.0/os/linux modules
make[1]: Entering directory `/lib/modules/2.6.27-7-server/build'
make[1]: *** No rule to make target `modules'. Stop

```

Not familiar with make so not sure what to do. I tried this previously with V1.4.0.0 with the same results.

Thx.

David

---

### Post by olddave1 on 2009-04-01
Hi,

I found another thread on installing the linux headers and altering the makefile to point to them, as the supplied one doe snot suit Ubuntu's std palce for them. So now built and installed.

Are there instructions on setting up the connection (WEP) viw the cmd line? I prefer to do that then, once I have a internet connection instal a lightweight GUI.

thx.

David

---

### Post by t_virus on 2009-04-01
hello GepettoBR,

iwconfig:

```
mauro@mauro-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"SMC"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:F7:80:B3:72   
          Bit Rate:18 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=12/70  Signal level=-84 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vnet0     no wireless extensions.

pan0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig:

```
mauro@mauro-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:af:71:b0:75  
          inet addr:192.168.2.120  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe71:b075/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2315902 (2.3 MB)  TX bytes:194687 (194.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:8c:e8:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:577 (577.0 B)  TX bytes:577 (577.0 B)

ra0       Link encap:Ethernet  HWaddr 00:13:f7:f3:ed:06  
          inet6 addr: fe80::213:f7ff:fef3:ed06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1644 (1.6 KB)  TX bytes:9808 (9.8 KB)

ra0:avahi Link encap:Ethernet  HWaddr 00:13:f7:f3:ed:06  
          inet addr:169.254.8.173  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

vnet0     Link encap:Ethernet  HWaddr aa:e9:c4:b4:71:ee  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::a8e9:c4ff:feb4:71ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:5788 (5.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-AF-71-B0-75-31-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5211 errors:0 dropped:0 overruns:0 frame:1691
          TX packets:1835 errors:19 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:2173083 (2.1 MB)  TX bytes:255136 (255.1 KB)
          Interrupt:19 

```

---

### Post by olddave1 on 2009-04-01
Hi,

Seems I am not out of the woods yet.

I run the insmod and lsmod shows Module - rt2870sta Size - 547160 Used by - 0.

But running "sudo ifconfig ra0 up" returns "ra0: ERROR while getting interface flags: No such device". Is there another step required?

Thx.

David

---

### Post by olddave1 on 2009-04-02
Hi,

Just spent another day trying to get this to work.

I followed the instructions at the bottom of this thread
[http://ubuntuforums.org/archive/index.php/t-907809.html](http://ubuntuforums.org/archive/index.php/t-907809.html)

As I am getting a very similar error

# $/sbin/ifconfig ra0 inet YOUR_IP up
I am getting this error:

linux # sudo ifconfig ra0 inet 192.168.0.22 up
SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device

One thing I don't understand in the README_STA is in step 3 of the build instructions. I set the two supplicant flag to 'y' in config.mk. But what do they mean by these instructions?
```

=> #>cd wpa_supplicant-x.x
=> #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d

```

There is no directory of the name wpa_supplicant-x.x or any with a similar name.

When I ran the second command from the 2009_0302_RT2870_Linux_STA_v2.1.0.0 directory. It looks for a non existant wpa_supplicant.conf file in that directory. So I did 
```
sudo find / -name wpa_supplicant.conf
```
and found one in /etc/dbus-1/system.d directory, so changed to that directory and ran the wpa_supplicant command from there, it had lots of error meesages about invalid commands.

Where to now? Why is this so difficult to achieve? 

Somewhere they should list a list of devices that work with which kernel, this would save me days of work, just by buying a device I know is supported.

Thx.

David

---

### Post by GepettoBR on 2009-04-02
I'm still using the 1.4.0.0 driver. I'll attempt to compile the new 2.1.0.0 later today and see if I can find the problem.

---

### Post by GepettoBR on 2009-04-02
Alright, I've played around with the 2.1.0.0 driver. I couldn't get it to work:

The installation itself went fine, from changing the settings in Makefile and os/linux/config.mk all the way to running insmod. Then, when it was time to activate the network interface I got the same error as olddave1: 
ra0: ERROR while getting interface flags: No such device

Reboot, now ifconfig ra0 up works. The wireless networks appear. I am unable to connect to any network, protected or not. After reinstalling the driver and rebooting yet again, I manage to connect to my WPA-encrypted home network. In under 30 seconds, the connection was lost and after another 40 minutes of being unable to reconnect I lost my temper.

I'm back to using the 1.4.0.0 driver once more. Installation was flawless, did not require a reboot and the connection works as it should.

---

### Post by t_virus on 2009-04-02
hey GepettoBR thanks for your help:guitar:

i just clean instaled ubunto again. sucks lol
but now with the driver 1.4.0.0 i got it working. thank you man.
i dont know why but seems to be some incompatibility with my 2 drivers (rt2870 and ar25xx (atheros 5007eg)). but its working allmost fine. need to do some more tests with these two.
thank you Gepetto.

---

### Post by GepettoBR on 2009-04-02
I didn't do that much for you, but you're welcome. I hope you sort out all of your problems.

---

### Post by olddave1 on 2009-04-03
Hi,

I solved my problem by buying a USD wireless dongle that works out of the box with Ubuntu 8.10. Sold by [www.linuxemporium.co.uk](www.linuxemporium.co.uk) and took less than a day to get here. It is a EDIMax Wireless 802.1 b/g Turbo Mode High-Gain USB Adapter. So at least I can get on woth my real work now.

If I ever get some leisure time I might get the RT2870sta working using the information you have given in this thread, so thx..

David

---

### Post by t_virus on 2009-04-03
> **t_virus said:**
> hey GepettoBR thanks for your help:guitar:

i just clean instaled ubunto again. sucks lol
but now with the driver 1.4.0.0 i got it working. thank you man.
i dont know why but seems to be some incompatibility with my 2 drivers (rt2870 and ar25xx (atheros 5007eg)). but its working allmost fine. need to do some more tests with these two.
thank you Gepetto.

IT&#346; SOLVED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 
FOR EVERYONE!!!!!!!!!!!!

The deal is this:

instal madwifi-hal -> install rt2870 -> reboot (only rt2870 will work) -> reinstall madwifi-hal (dont make clean) -> atheros is working -> with the computer on insert rt2870 USB DEVICE -> 

[COLOR="Red"]AND DONT FORGET TO REMOVE THE USB RT2870 BEFORE SHUTTING DOWN[/COLOR]

[COLOR="Red"]PUT IN WITH YOUR PC ON AND REMOVE IT WITH YOUR PC ON[/COLOR]

---

### Post by draenor on 2009-05-22
It seems that the ralink 2x drivers have built in WPA support. I at least did not manage to use this in conjunction with wpa_supplicant. 



However, what did work (Kernver 2.6.27-8):

```

edit the file: /etc/Wireless/RS2870STA/RS2870STA.dat

Channel=0
AuthMode=WPAPSK
EncryptType=TKIP
WPAPSK="your key as generated by the wpa_passphrase tool"

```

This was using the driver compiled with the options 
```

WPA_SUPPLICANT=y and HAS_WPA_SUPPLICANT_SUPPORT=y

```

Finally
```

ifconfig ra0 up
iwconfig ra0 essid "my_essid"
dhcpcd ra0

```


Note, it's assumed that the driver were successfully compiled and installed, and that the module (rt2870sta) was properly loaded (by modprobe rt2870sta). No further intervention was needed in the Makefile either.

---

### Post by GepettoBR on 2009-05-22
I didn't need to edit that file at all - on-the-fly GUI configuration via Network Manager is working, which means I can connect to any network in range provided I have the password jsut by clivking and typing said password. If you edit RS2870STA.dat you'll have to change the file every time you wish to connect to a different network.

I suppose it won't matter for most people using this chipset, since it's made for desktop PCs that generally stay put in one place, but I'm just throwing it out there.

---

### Post by Jackie999 on 2009-06-15
My usb stick is the F5D8053_V3.  I've been running the 1.4.0.0 for quite a while..but due to the occasional disconnect I thought I'd try the 2.1.2.0 ...unfortunately I had no luck with it either.
I wasn't able to find the /include/rt870.h file in order to add my lsusb device "ID 050d:815c Belkin Components' ...that was the only way I could get 1.4.0.0 to work and the file doesn't seem to be in the newer version.

---

### Post by hotice_z on 2009-06-19
> **Jackie999 said:**
> My usb stick is the F5D8053_V3.  I've been running the 1.4.0.0 for quite a while..but due to the occasional disconnect I thought I'd try the 2.1.2.0 ...unfortunately I had no luck with it either.
I wasn't able to find the /include/rt870.h file in order to add my lsusb device "ID 050d:815c Belkin Components' ...that was the only way I could get 1.4.0.0 to work and the file doesn't seem to be in the newer version.


try to look at /os/linux/usb_main_dev.c, i think your device already there :
```
 {USB_DEVICE(0x050d,0x815c)}, /* Belkin F5D8053 */ 
```fyi, i also use ver 2.1.2.0 for my airlink101 AWLL6070, and everything seems alright on my jaunty.

CMIIW

---

### Post by Jackie999 on 2009-06-20
Thanks hotice_z ):P

Worked like a charm that time..not sure why it didn't the first time. I'm on intrepid btw.

---

### Post by SlvrDragon50 on 2009-07-25
Could someone help me???

I've tried running the patch yet when I type sudo apt-get patch, it says it cannot find the file!

---

### Post by GepettoBR on 2009-07-26
> **SlvrDragon50 said:**
> Could someone help me???

I've tried running the patch yet when I type sudo apt-get patch, it says it cannot find the file!

Exactly what patch are you talking about? No patching is necessary here.

---

### Post by Clochard on 2009-08-19
I've been able to get this working with the 1.4.0.0 driver from ralink.  However it seemed to cause network drops and was what I would call "flakey".

I decided to try the latest ralink driver - 2.1.2.0.  I'm able to compile it and get the module to load when I plug in the device.  What I can't do though is make Network Manager play with it at all - it doesn't even see the device.

Can anyone confirm that they've got NM working with the 2.1.2.0 version of the driver?  If so, are there special steps to take?

---

### Post by n00ne on 2009-09-24
I hope some one still reades this post.

I'm trying to install this drivers to work with my d-link dwa 140
on Intrepid.
I followed the instractions in this post with the new version on ralink site (v2.2). every thing seemed to compile ok and I managed to connect to unsecured wireless networks. but I can't connect to WPA2 secured network ( nm just shows the green circles of connecting and fails after few minutes asking for password again).
I also tried to set the /etc/Wireless/RT2870STA/RT2870STA.dat
to support my security settings but still I get the same  problem.

any help would be appreciated.

here is my dat file content -
```

#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=11n-AP
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=(my wirless password generated with wpa_passphrase)
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4

```

---

### Post by t_virus on 2009-09-24
follow all instructions here:

[http://forums.remote-exploit.org/bt4beta-non-working-hardware/20408-wirelesscards-rt2870-2860-chipsets-3.html](http://forums.remote-exploit.org/bt4beta-non-working-hardware/20408-wirelesscards-rt2870-2860-chipsets-3.html)

---

### Post by Jackie999 on 2009-09-24
n00ne, I haven't tried this driver on 9.04, I'm just about to...but I remember in the original files you had to make a few changes in the /os/linux/config.mx
```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

```I don't know if this change is still needed...but it's something you can try...
Jackie.

---

### Post by GepettoBR on 2009-09-24
> **Jackie999 said:**
> n00ne, I haven't tried this driver on 9.04, I'm just about to...but I remember in the original files you had to make a few changes in the /os/linux/config.m[color=red]k[/color]
```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=[color=red]y[/color]

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[color=red]y[/color]

```I don't know if this change is still needed...but it's something you can try...
Jackie.

Fixed.

---

### Post by n00ne on 2009-09-25
10x t_virus but I could'nt find any hing helpful in the link you sent me.

Jackie and Gepetto - i've changed both this settings to y before compiling, so I guess this is not the problem.

is there any way for me to see whats going on behind the scene when it tried to connect to seured network ?

10x

---

### Post by Jackie999 on 2009-09-27
I'm unable to get it working either n00ne.
I can see the device
```
ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```I can't get it into managed mode.

On a good note, I have a AWUS036H (rtl8187) device that is working 'out of the box' with this version..

---

### Post by n00ne on 2009-09-28
ok.
I've installed now ubuntu 9.04 on another laptop I have
and the card worked automatically, had to download wicd network manager to from the D-link card only and not the built in card.
but every thing seems to work now (only tested connection to wpa network and not wpa2) so I guess I'll just upgrade my system soon 
( wanted to make a fresh install for a long time now )

---

### Post by GepettoBR on 2009-09-28
> **n00ne said:**
> ok.
I've installed now ubuntu 9.04 on another laptop I have
and the card worked automatically, had to download wicd network manager to from the D-link card only and not the built in card.
but every thing seems to work now (only tested connection to wpa network and not wpa2) so I guess I'll just upgrade my system soon 
( wanted to make a fresh install for a long time now )

If you want to make a fresh install I recommend you wait until the end of October and install 9.10. It's less updating to do, and you get GRUB 2 and ext4 from the get-go, not to mention a newer kernel.

---

### Post by arrrghhh on 2009-10-12
I just installed 9.10 beta, and I have a card that uses the RT2870 chipset...and I can't get it to work at all.  I am able to get it to list networks now, but it'll never connect - and it certainly doesn't list all available networks, my laptop using a 2200bg card shows many more networks.  Sometimes even the AP right next to me doesn't show up, but some very weak neighbor's network shows.  I've tried turning off WPA2 on my router, and it doesn't make a difference...

So I'm assuming it's the kernel that's being used... I don't know how to fix it tho.  Does this fix apply to the 2.6.31 kernel as well, or has the method for patching to make this driver work changed?  Blacklisting the rt2800 driver was what I think made the card at least show some networks in network-manager, but wicd does the same thing - only shows a few networks, sometimes not even mine, and won't connect to anything.

I appreciate any assistance/experience people have with the new version of Ubuntu!  I was really hoping 9.10 would work with this card w/o any fuss... c'est la vie.

---

### Post by nickmcg on 2009-10-13
> **arrrghhh said:**
> I just installed 9.10 beta, and I have a card that uses the RT2870 chipset...and I can't get it to work at all.  I am able to get it to list networks now, but it'll never connect - and it certainly doesn't list all available networks, my laptop using a 2200bg card shows many more networks.  Sometimes even the AP right next to me doesn't show up, but some very weak neighbor's network shows.  I've tried turning off WPA2 on my router, and it doesn't make a difference...

So I'm assuming it's the kernel that's being used... I don't know how to fix it tho.  Does this fix apply to the 2.6.31 kernel as well, or has the method for patching to make this driver work changed?  Blacklisting the rt2800 driver was what I think made the card at least show some networks in network-manager, but wicd does the same thing - only shows a few networks, sometimes not even mine, and won't connect to anything.

I appreciate any assistance/experience people have with the new version of Ubuntu!  I was really hoping 9.10 would work with this card w/o any fuss... c'est la vie.

The only work-round I've found is to add the line ```
blacklist rt2800usb
``` in the file /etc/modprobe.d/blacklist.conf

HTH

Nick

---

### Post by OliW on 2009-10-15
> **nickmcg said:**
> The only work-round I've found is to add the line ```
blacklist rt2800usb
``` in the file /etc/modprobe.d/blacklist.conf


Just bought two of these (should really do the research first, eh?!) and I'm on karmic.

Do I just need to blacklist or do I need to do other things (ie, the rest of the thread) too?


Edit: I've no idea why this worked, but I just ran ```
sudo rmmod rt2800usb
``` and replugged the dongle and it works. That's magic! No idea which driver it's using now...

---

### Post by freek_zero on 2009-10-27
Had my WUSB600N working fine until I got the kernel update to 2.6.28-16 a few days ago. Upon booting the new kernel I rebuilt the rt2870usb driver from Ralink as I have to every time... but this time, it doesn't work. Symptoms are same I've read in this thread and others before: scans fine, see the network(s), connects to the network, but doesn't get an IPv4 address. Rebooting to the -15 kernel works fine.

Anyone been able to get this to work with 2.6.28-16?

---

### Post by nickmcg on 2009-10-29
> **OliW said:**
> Just bought two of these (should really do the research first, eh?!) and I'm on karmic.

Do I just need to blacklist or do I need to do other things (ie, the rest of the thread) too?


Edit: I've no idea why this worked, but I just ran ```
sudo rmmod rt2800usb
``` and replugged the dongle and it works. That's magic! No idea which driver it's using now...

All you need to do is blacklist - that just prevents rt2800usb loading, rmmod simply unloads the module if it's loaded.

---

### Post by cufflinks on 2009-10-30
> **nickmcg said:**
> The only work-round I've found is to add the line ```
blacklist rt2800usb
``` in the file /etc/modprobe.d/blacklist.conf

HTH

Nick

Thank you Oh-So-Kindly... I was going nuts trying to figure out why my wireless card which worked with 9.04 isn't working anymore.  I'm actually not sure why that even worked, seeing as that should be the driver that works with my card.  I had even downloaded the driver from RaLink only to find it won't compile with 2.6.3 kernels!  I almost considered going back to 9.04... or maybe the bridged connection I've setup on the laptop to try and get the wireless on this desktop back up isn't so bad :P

Anyways... hopefully others with the same problem will find your post more quickly.

---

### Post by freek_zero on 2009-11-25
Just upgraded to 9.10 (kernel 2.6.31-15) and the issue persists, except now I can't simply select an older kernel to get it to work. Had to apply a .31-specific patch to get the driver to build. Blacklisting rt2800usb just gets me back to where i was in 28-16, which is a solid connection but no IPv4 address (ifconfig showed an IPv6 address until I disabled IPv6). dhclient reports no dhcp offers received.

---

### Post by GepettoBR on 2009-11-25
In Karmic I no longer have to compile the driver. All it takes is blacklisting rt2800usb and running "modprobe rt2870sta" once. After that , my device was automatically recognized at every boot. Which is great, since I can no longer compile the driver provided by Ralink due to a mess of gcc errors.

---

### Post by freek_zero on 2009-11-26
Compiling ralink driver requires a patch for the 2.6.31 kernel. It compiled fine for me after that (but still didn't work).

When you say it is recognized at every boot... what _exactly_ do you mean by that? You mean you boot, login, and networkmanager connects? Or do you mean as soon as you boot (before you log in) it already connects? The latter is how I've had it set up till now (doesn't use networkmanager).

And you using WPA? WPA2? open?

---

### Post by freek_zero on 2009-11-26
Several hours later, the only way I can get this to work is using the version of rt2870sta provided with 9.10 (which I believe is v1.4 from RaLink). Doesn't provide 5GHz access however.

---

### Post by GepettoBR on 2009-11-27
> **freek_zero said:**
> Compiling ralink driver requires a patch for the 2.6.31 kernel. It compiled fine for me after that (but still didn't work).

When you say it is recognized at every boot... what _exactly_ do you mean by that? You mean you boot, login, and networkmanager connects? Or do you mean as soon as you boot (before you log in) it already connects? The latter is how I've had it set up till now (doesn't use networkmanager).

And you using WPA? WPA2? open?

I mean the first option. I'm using WPA2 encryption.

---

### Post by jh55chn on 2009-11-27
Freeze, try this one, maybe it helps.

  	 	 	 	 	 	  Wireless usb : Asus USB-N11
 Chip : Ralink rt2870
 Dual OS : Vista + karmic (via Wubi)  
 

To make your wireless dectectable. 

Important : Don't plug the usb before going thru the steps.
 

 Step 0 : At terminal, [COLOR=#000080]_[EMAIL="aaa@ubuntu"]aaa@ubuntu[/EMAIL]_[/COLOR]:~$ sudo gedit /etc/modprobe.d/blacklist.conf
 	 Add “blacklist rt2800usb” without quote at the end of the file, then save it.
 

 Step 1 : Download the latest rt2870 driver ( 2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2 )  from Ralink.
 

 Step 2 : Untar the file and save to your home folder, and name it (my folder is rt2870).
 

 Step 3 : Don't plug your wireless usb at this moment, at terminal [COLOR=#000080]_[EMAIL="aaa@ubuntu"]aaa@ubuntu[/EMAIL]_[/COLOR]:~$ type lsusb.
 

 Step 4 : Now plug in your wireless usb to the computer, type lsusb again, you will find your wireless usb ID (8 digits). Write it down, and unplug the usb.
 

 Step 5 : At aaa@ubuntu:~/rt2870/os/linux$, sudo gedit usb_main_dev.c, check your usb device is included, if not, add your wireless usb ID. Save the file.  It is quite interesting for my asus usb ID, I have to add two lines.
 [COLOR=#800000]	{USB_DEVICE(0x0B05,0x1761)}, /* Asus */[/COLOR]
 [COLOR=#800000]	{USB_DEVICE(0x1761,0x0B05)}, /* Asus */[/COLOR]
    
 

Step 6 : At same terminal , sudo gedit config.mk, and change two settings.
 	[COLOR=#800000]# Support Wpa_Supplicant [/COLOR] 
 [COLOR=#800000]	HAS_WPA_SUPPLICANT=n &#8594; y [/COLOR] 
 

 [COLOR=#800000]	# Support Native WpaSupplicant for Network Maganger [/COLOR] 
 [COLOR=#800000]	HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n &#8594; y[/COLOR]
 

 Step 7 : At aaa@ubuntu:~/rt2870$, sudo gedit Makefile, check the folllowing at the top of the file:
 	[COLOR=#800000]RT28xx_MODE = STA[/COLOR]
 [COLOR=#800000]	TARGET = LINUX[/COLOR]
 [COLOR=#800000]	CHIPSET = 2870[/COLOR]
 

 	If ok, close the file. If not, change the setting as above.
 

 Step 8: rt2870 2.2.00 version do not support kernel 2.6.31-14-generic, so you have to do a patch.
 Googling RT2870-2.6.31.patch, download it to rt2870 folder, then do the patch.  If you get a message of unable to patch, then download  and install Patch_2.5.9-5_amd64.deb.  You will then able to patch RT2870-2.6.31.patch
 	At [COLOR=#000080]_[EMAIL="aaa@ubuntu"]aaa@ubuntu[/EMAIL]_[/COLOR]:~/rt2870$ patch -p1 < rt2870-2.6.31.patch
 

 Step 9 : At [COLOR=#000080]_[EMAIL="aaa@ubuntu"]aaa@ubuntu[/EMAIL]_[/COLOR]:~/rt2870$, do the compilation.
 	sudo make uninstall
 	sudo make clean
 	sudo make
 	sudo make install
 

 Step 10 : At [COLOR=#000080]_[EMAIL="aaa@ubuntu"]aaa@ubuntu[/EMAIL]_[/COLOR]”~$ sudo gedit /etc/rc.local, add following two lines prior to exit0.
 	 ifconfig ra0 up
 	pkill NetworkManager
 

 	save it, then at same terminal, sudo gedit /etc/modules, add rt2870sta, then save the file.
 

 Step 11 : Now turn off your PC, plug in the usb, and restart.
 

 Step 12 : Now configure networkmanager, use wep instead of wpa-psk or wpa2-psk.  Your wireless will be detected ,and be able to connect to the internet.  
 

 p.s. I just upgrade to kernel 2.6.31-15-generic, and only to do step 9. the wireless still works. ( don't forget to unplug the usb before doing the compilation)

---

### Post by SpiderTex on 2009-11-27
I'm stumped...
modprobe rt2870stq

when checking log:
rtusb init -->
usbcore: registered new interface driver rt2870

ifconfig however doesn't show ra0 ..  just the usual suspects eth0 l0 and wlan0

already tried without my pci wlan card...  nothing..

I do have a new WUSR600n   any gotchas there?

many thx

---

### Post by SpiderTex on 2009-11-27
> **jh55chn said:**
> Freeze, try this one, maybe it helps.

                                 Wireless usb : Asus USB-N11
 Chip : Ralink rt2870
 Dual OS : Vista + karmic (via Wubi)  
 

To make your wireless dectectable. 

Important : Don't plug the usb before going thru the steps.
 

 Step 0 : At terminal, [COLOR=#000080]_aaa@ubuntu_[/COLOR]:~$ sudo gedit /etc/modprobe.d/blacklist.conf
      Add &#8220;blacklist rt2800usb&#8221; without quote at the end of the file, then save it.
 >>> stuff deleted >>>
Step 12 : Now configure networkmanager, use wep instead of wpa-psk or wpa2-psk. Your wireless will be detected ,and be able to connect to the internet. 
 

 p.s. I just upgrade to kernel 2.6.31-15-generic, and only to do step 9. the wireless still works. ( don't forget to unplug the usb before doing the compilation)

followed step by step...

my wusb600n is still not visible.

Note: I did had to add 1737:0079 to the usb_main_dev.c file

apparently the "old" wusb600n had a different identifier

* checking dmesg | grep rt2 shows
rt2870sta: module is from the staging directory.....
usbcore: registered new interface driver rt2870

---

### Post by freek_zero on 2009-11-27
SpiderTex, you have WUSB600n v2, which doesn't seem to be supported at all (so far). There is a discussion going on here: [WUSB600n v2]("http://ubuntuforums.org/showthread.php?t=972060&page=8")

---

### Post by SpiderTex on 2009-11-28
> **freek_zero said:**
> SpiderTex, you have WUSB600n v2, which doesn't seem to be supported at all (so far). There is a discussion going on here: [WUSB600n v2]("http://ubuntuforums.org/showthread.php?t=972060&page=8")

many thx Freek, will follow there.

---

### Post by astroorion on 2009-11-29
Hello I am still having some trouble with my wireless on startup it doesn't see the network the only way I can get it to see it is by unplugging the usb and going to the terminal typing sudo rmmod rt2800usb 
I need to know how to blacklist it to get the card to recognize the network on startup can someone help me.
thank You

---

### Post by astroorion on 2009-11-29
Never mind I figured it out ;)

---

### Post by kleeman on 2009-12-04
Thanks jh55chn. Worked for me on two machines (64bit and 32bit) with wpa2 encryption. The blacklist of rt2800usb caused it to partially work in that certain APs were not visible. The recompile of the module with the patch meant I now can see and connect to all APs.
My usb connector is a D-link DWA-140

Ubuntu works for me. :popcorn::D:D

---

### Post by crich on 2009-12-11
Reading all the great help on this topic. :D

I just got a Engenius 9703 USB adapter. Very small and very cheap ($20). 

I blacklisted the rt2800usb driver and can now see my (and other networks) but I cannot attach. I see periodic (every few seconds) logs about scanning channel 1 (doesn't seem to use any other channel). I also saw a RT2870STA.dat file error message.

I'd like to try the steps to compile the RT driver, but I can't find the tar file at any of the sites (ralink or serialmonkey). Google didn't turn up any alternatives either.

Can someone send it or tell me where I can find it?


I am on the 2.6.31-16-generic kernel.

Thanks.

---

### Post by crich on 2009-12-13
> **crich said:**
> Reading all the great help on this topic. :D

I just got a Engenius 9703 USB adapter. Very small and very cheap ($20). 

I blacklisted the rt2800usb driver and can now see my (and other networks) but I cannot attach. I see periodic (every few seconds) logs about scanning channel 1 (doesn't seem to use any other channel). I also saw a RT2870STA.dat file error message.

I'd like to try the steps to compile the RT driver, but I can't find the tar file at any of the sites (ralink or serialmonkey). Google didn't turn up any alternatives either.

Can someone send it or tell me where I can find it?


I am on the 2.6.31-16-generic kernel.

Thanks.



OK. I found a RT2870USB version 2.2.0 ([http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1EQTVMekE0THpJMEwyUnZkMjVzYjJGa01ERTJNekE1TkRRNE5TNWllakk5UFQweU1EQTVYekE0TWpCZlVsUXlPRGN3WDFOVVFWOVhaV0pWU1Y5Mk1pNHlMakF1TUM1MFlYST1D](http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1EQTVMekE0THpJMEwyUnZkMjVzYjJGa01ERTJNekE1TkRRNE5TNWllakk5UFQweU1EQTVYekE0TWpCZlVsUXlPRGN3WDFOVVFWOVhaV0pWU1Y5Mk1pNHlMakF1TUM1MFlYST1D)) and RT2870WebUI version 2.3.0 of the driver ([http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1EQTVMekV5THpBM0wyUnZkMjVzYjJGa05UVTFNalF6TVRVeE5TNTBaM285UFQxU1ZESTROekJmVEdsdWRYaFRWRUZmVmpJdU15NHdMakJmTWpBd09URXlNRFE9Qw%3D%3D](http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1EQTVMekV5THpBM0wyUnZkMjVzYjJGa05UVTFNalF6TVRVeE5TNTBaM285UFQxU1ZESTROekJmVEdsdWRYaFRWRUZmVmpJdU15NHdMakJmTWpBd09URXlNRFE9Qw%3D%3D))

Version 2.3.0 builds and installs fine - but now the device doesn
't seem to even scan. Here are the logs:

Dec 13 14:30:28 firefly kernel: [   24.609400] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
Dec 13 14:30:28 firefly kernel: [   24.629871] rtusb init --->
Dec 13 14:30:28 firefly kernel: [   24.629957] usbcore: registered new interface driver rt2870

Those are the only logs for the device or interface - network manager doesn't seem to even see the device - even after a reboot.

Version 2.2.0 wont compile. Looks like I need to apply the patch mentioned in a previous post. 

My question is: should I be using the 2.3.0 version anyway for the 2.6.31 kernel and trying to figure out why it's not working?

Thanks.
Chris.

---

### Post by aextance on 2010-01-03
I don't know whether anyone is still following this thread, but what the hell, here goes. 

crich - I'm not sure you really *need* the Ralink drivers anymore. I used to follow the instructions on this thread and use either no, or WEP encryption. I then tried to upgrade to WPA2 encryption, and the old Ralink drivers that I used didn't support it. However, using the approach at the link below has worked with WPA2, off and on, and I suspect it will be useful for unencrypted or WEP also.

[http://art.ubuntuforums.org/showthread.php?t=1342593](http://art.ubuntuforums.org/showthread.php?t=1342593)

Why don't you give it a go? Peepingtom is clearly very responsive.

I'm really curious to hear whether GepettoBR can tell us how he got his WPA working so smooth. There is a bug in the network manager which is being worked on to help with this for the RT2870 and other chipsets, but I would welcome any tips for improving WPA2 encryption with the RT2870 in the meantime.

---

### Post by GepettoBR on 2010-01-03
> **aextance said:**
> I'm really curious to hear whether GepettoBR can tell us how he got his WPA working so smooth. There is a bug in the network manager which is being worked on to help with this for the RT2870 and other chipsets, but I would welcome any tips for improving WPA2 encryption with the RT2870 in the meantime.

In Karmic, I just blacklisted the rt2800usb module and then manually loaded the rt2870sta module already supplied with the default kernel. After manually loading it once, it was automatically loaded whenever I plugged in my device or turned on th PC with it already plugged in. My home network uses WPA2 encryption, and it connected without a hitch.

---

### Post by aextance on 2010-01-04
Oh - with the "modprobe rt2870sta"? I thought there might be more to it than that. 

Still mine does generally connect eventually. I wonder why it doesn't run as smoothly?

---

### Post by GepettoBR on 2010-01-04
> **aextance said:**
> Oh - with the "modprobe rt2870sta"? I thought there might be more to it than that. 

Still mine does generally connect eventually. I wonder why it doesn't run as smoothly?

Yes, just that. I don't know why you'd have trouble connecting.

---

### Post by aextance on 2010-02-15
Just out of interest, what do you get when you run lshw -C network in a terminal, Gepetto? I don't think my device is loading a driver, there's nothing saying "driver=" next to the configuration entry when I run this.

---

### Post by GepettoBR on 2010-02-17
> **aextance said:**
> Just out of interest, what do you get when you run lshw -C network in a terminal, Gepetto? I don't think my device is loading a driver, there's nothing saying "driver=" next to the configuration entry when I run this.

Here's the relevant section of the output: ```
 *-network:0
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:1c:f0:9d:ac:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.101 multicast=yes wireless=RT2870 Wireless

```

---

### Post by info@tacowitte.nl on 2010-06-11
> **aextance said:**
> Oh - with the "modprobe rt2870sta"? I thought there might be more to it than that. 

Still mine does generally connect eventually. I wonder why it doesn't run as smoothly?

I just installed 10.04 on a computer that uses this wireless network adapter. It didn't connect either. Blacklisting rt2800usb solved the problem. Now it connects without any problem.

It would be nice if the rt2800usb module would somehow be blacklisted in the next release so it works out of the box.

---

