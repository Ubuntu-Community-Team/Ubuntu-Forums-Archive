---
title: "Install linux drivers for ralink rt2870"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by nilsa5 on 2008-10-27
Installing Linux to Ralink RT2870 driver
Mess very much with this myself and found out how it should be done:

1. Downloading the latest drivers [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
(As of this writing, while [http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2)

2. Extract the archive you downloaded.

3. Open a terminal.

4. Go into the folder you extracted (For me 2008_0925_RT2870_Linux_STA_v1.4.0.0 cd)

5. Use gedit or nano (the text you like) and open Make File.

6. Watch where the MODE is set to STA (MODE = STA) TARGET is set to LINUX (TARGET = LINUX) save and close.

7. Visit the os / linux (cd os / linux)

8. Open config.mk (with the text you like)

9. Changing these from
Quote
# Support wpa_supplicant
HAS_WPA_SUPPLICANT = n

# Support for Native WpaSupplicant Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = n
to
Quote
# Support wpa_supplicant
HAS_WPA_SUPPLICANT = y

# Support for Native WpaSupplicant Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = y

10. Save and Close.

11. Return to 2008_0925_RT2870_Linux_STA_v1.4.0.0.
12. Run make. (Can you mail error messages back).
13. Run make install as root (sudo make install, send feedback here also love)
14. Visit the os / linux (cd os/linux)
15. Run insmod rt2870sta.ko
16. When will all work after my experience, if not follow the next step.
17. Open /etc/network/interfaces (gedit /etc/network/interfaces).
18. Please enter the first sentence
auto ra0
, Also the other

iface ra0 inet dhcp
(dhcp is standard, you need only change to what suits you love.
19. Then all the work, use encryption, you can configure it with the System> Administration> Network, or network-admin in the terminal.
20. Almost forgot that you must install build-essential (apt-get install build-essential).
21. build-essential to be on CD you installed ubuntu with.
22. How to install build-essential CD.
23. Open the Terminal (Applications> Accessories> Terminal)
24. Run apt-cdrom add-d / cdrom (replace / cdrom with the path cdrom is mounted with you)
25. Run apt-get update.
26. And run apt-get install build-essential.

And as already said please respond to this post, or send a mail to [email]nilsa5@tele2.no[/email]:):):)

---

### Post by rotting68 on 2008-12-08
Thank you so much!! Finally something that works and easily to understand for a newby.

---

### Post by christoph88 on 2009-01-17
very nice tutorial :D finally wireless working without any hassle

---

### Post by robertki on 2009-01-18
Well, this procedure is working just partially for me. But they are a bit different from those provided by RALINK.
 The card is not found at startup and the system also freezes then, but it works if I plug it in afterwards....

According to ralink you just have to write *make*, not *make install.*afterwards. Why this difference?

Anybody knowing whether there will be automatic support for this chip/card in the future?

---

### Post by nick77 on 2009-01-22
I'm happy to confirm your method. I was trying a couple of different ways to compile the module, but none worked; when I tried out wicd (after uninstalling the gnome network manager) I saw, my USB Stick is being recognized though (ie, the module worked!), but I couldn't connect. This reminded me, that wpa_supplicant wasn't enabled in my /os/linux/config.mk as you described file :roll:

I first had troubles doing the build process on Intrepid. As I have a Buffalo WLI-UC-G300N USB Wireless Adaptor (Ralink 2870, usb ), I followed a short how-to on a [Japanese Blog]("http://largefield.air-nifty.com/blog/2008/05/wliucg300n_with.html"). Moving the extracted driver files to /usr/src/ solved the problems building it (plus #sudo make).

Further, I added the Device number from the lsusb output: "Bus 002 Device 004: ID 0411:00e8 MelCo., Inc." as line ca 186 in /include/rt2870.h ```
	{USB_DEVICE(0x0411,0x00e8)}, /* Buffalo */		\
```

That's it, now I have a connection - however, it shows only 1 Mb/s.... Basestation is a fritz!box fon 7270 with wlan n switched on (as well as g)

Any ideas about the connection speed improvements? My Reception is between 96-100%....

Thanks anyway

Nick

Edit: my speed is now shown as 108 Mbit/s in the base station, as 243 Mbit/s in the network manager info dialog; seems to be perfect!

---

### Post by RaZoR1394 on 2009-01-25
I posted this wiki a while ago during the Intrepid beta. It works for me under both Intrepid and Jaunty alpha.

[http://ubunturt2870.pbwiki.com/FrontPage](http://ubunturt2870.pbwiki.com/FrontPage)

I have cleaned it up a bit.

---

### Post by abibabou on 2009-01-25
Hi,

I have tried every thing. After a fresh install of ubuntu 8.10 and updated I follow the procedure it works but the minute  I reboot the machine no wireless connection although the led on the usb adaptor blinks

My problem is the following when I compile and install:

make -C tools
make[1]: Entering directory `/home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
/home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/md5.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/mlme.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/action.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.o
/home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.c: In function &#8216;RTMP_FillTxBlkInfo&#8217;:
/home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.c:713: warning: label &#8216;FillTxBlkErr&#8217; defined but not used
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/eeprom.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/dfs.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/spectrum.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/assoc.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/aironet.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/auth.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sanity.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/connect.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/wpa.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/ba_action.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/2870_main_dev.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/2870_rtmp_init.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtusb_io.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtusb_data.o
  CC [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data_2870.o
  LD [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.mod.o
  LD [M]  /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
cp -f /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.ko /tftpboot
make -C /home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux'
rm -rf /etc/Wireless/RT2870STA
rm: cannot remove `/etc/Wireless/RT2870STA/RT2870STA.dat': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/gordon/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux'
make: *** [install] Error 2



Could any body help me there please , the kernel is 2.6.27-9-generic?

---

### Post by RaZoR1394 on 2009-01-25
Look on my wiki. You need to use sudo for both make and make install.

```

sudo make
sudo make install

```

Usually you don't have to use sudo when compiling but now you do.

---

### Post by abibabou on 2009-01-26
Thhank you for this prompt reply, but one problem still remains: 

After a fresh install of ubuntu 8.10 and updated I follow the procedure it works but the minute I reboot the machine, no wireless connection although the led on the usb adaptor blinks, cannot see any wireless network from the desktop only a wired connection works although like I said before the usb adaptor led blinks.

It seems the gnoome-network-admin hangs!

Any advice?

---

### Post by AlanRick on 2009-01-26
Hi RaZoR1394,
Make works perfectly. :D

One very minor improvement in your wiki which I didn't dare make:
after
> You need to change some inf....
> cd os/linux

Problem is although the light on my logilink usb blinks I don't see the network manager's green orbiting dots followed by the blue wifi bars when I boot or when I insert the wifi usb. 

However, if I insert another wifi usb (siemens) the green dots appear and then the blue bars and when I swap the usb sticks then the logilink does work. I verified this with connection info and it does really use 802.11n. 

Any idea why I have to insert the other usb stick first in order to "jumpstart" the network manager?

---

### Post by AlanRick on 2009-02-19
Just to say that I finally got this working by installing WICD and under preferences setting the wireless connection to ra0.

---

### Post by jellylogix on 2009-02-19
I am forever in your debt!

Worked perfectly!! :D :D :D

---

### Post by mexus on 2009-02-27
Add 
```
{USB_DEVICE(0x0411,0x012e)}, /* Buffalo */		\
```

for Buffalo WLI-UC-AG300N

---

### Post by mexus on 2009-03-19
This installs the driver, but cannot connect to a wireless network. It also stopped mad-wifi from connecting with my other wirless adapter AR5007EG....

---

### Post by Brausepaul on 2009-03-22
Hi,

this description works like a charm with one exception for me: after a reboot I have to run sudo insmod rt2870sta.ko manually for my WLAN device to work and to show wireless networks. Any idea what causes this or how I can automate this?

---

### Post by wangsuda on 2009-03-22
> **Brausepaul said:**
> Hi,

this description works like a charm with one exception for me: after a reboot I have to run sudo insmod rt2870sta.ko manually for my WLAN device to work and to show wireless networks. Any idea what causes this or how I can automate this?

 to load the module automatically on each reboot, add rt2860sta to /etc/modules

sudo gedit /etc/modules

- add the following line to the end of the /etc/modules file:
rt2860sta

- reboot and retest wireless

---

### Post by wangsuda on 2009-03-22
There is another way to install Ralink drivers, and this is the one that I used. Works great!

- Download rt2860-source_1.8.0.0-3_all.deb from

[http://packages.debian.org/sid/all/rt2860-source/download](http://packages.debian.org/sid/all/rt2860-source/download)

```
wget [http://http.us.debian.org/debian/pool/non-free/r/rt2860-source/rt2860-source_1.8.0.0-3_all.deb](http://http.us.debian.org/debian/pool/non-free/r/rt2860-source/rt2860-source_1.8.0.0-3_all.deb)
```

- install source .deb:

```
sudo dpkg -i rt2860-source_1.8.0.0-3_all.deb
```

- compile
```
sudo aptitude install debhelper module-assistant
```
```
sudo module-assistant auto-install rt2860
```

- install the module
```
sudo modprobe rt2860sta
```
this should activate the new wireless interface without reboot

---

### Post by Brausepaul on 2009-03-22
wangsuda, right now my /etc/modules contains

alias ra0 rt2870sta

This should work the same way like your proposal, or am I wrong? Or do you want me to add your line in addition?

---

### Post by wangsuda on 2009-03-22
> **Brausepaul said:**
> wangsuda, right now my /etc/modules contains

alias ra0 rt2870sta

This should work the same way like your proposal, or am I wrong? Or do you want me to add your line in addition?

All you need is the name of the driver module for it to boot automatically, hence just ```
rt2860sta
``` added to the /etc file.

---

### Post by Brausepaul on 2009-03-23
I changed my /etc/modules file to

fuse
lp
rtc
#alias ra0 rt2870sta
rt2860sta

but I still have to run sudo insmod rt2870sta.ko manually to get my wireless to work.

---

### Post by RaZoR1394 on 2009-03-23
What has rt2860 to do with rt2870? They are different. The first is the PCI version, the other USB. There is a reason different drivers are provided by Ralink.

---

### Post by wangsuda on 2009-03-23
Perhaps if you delete
```
#alias ra0 rt2870sta
```
it will automatically boot. I am not sure, though.

---

### Post by t_virus on 2009-03-27
sorry but this didnt work for me:

mauro@mauro-laptop:~/rt2870$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:21338  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mauro@mauro-laptop:~/rt2870$ ifconfig ath0 down
SIOCSIFFLAGS: Permissão negada
mauro@mauro-laptop:~/rt2870$ sudoifconfig ath0 down
bash: sudoifconfig: command not found
mauro@mauro-laptop:~/rt2870$ sudoi fconfig ath0 down
bash: sudoi: command not found
mauro@mauro-laptop:~/rt2870$ sudo fconfig ath0 down
sudo: fconfig: command not found
mauro@mauro-laptop:~/rt2870$ sudo ifconfig ath0 down
mauro@mauro-laptop:~/rt2870$ sudo wlanconfig ath0 destroy
mauro@mauro-laptop:~/rt2870$ sudo wlanconfig ra0 create wlandev wifi0 wlanmode sta
ra0
mauro@mauro-laptop:~/rt2870$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

pan0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mauro@mauro-laptop:~/rt2870$ iwlist ra0 scan
ra0       No scan results

mauro@mauro-laptop:~/rt2870$

---

### Post by csumm101 on 2009-03-29
> **Brausepaul said:**
> I changed my /etc/modules file to

fuse
lp
rtc
#alias ra0 rt2870sta
rt2860sta

but I still have to run sudo insmod rt2870sta.ko manually to get my wireless to work.



I did exactly the way that wangsuda said. I just simply added rt2870sta and it worked perfectly. It loaded automatically at boot

But, if for some reason, that doesn't work, try adding your insmod command (exactly the way you type it in the terminal without, but without the "sudo" prefix) to /etc/rc.local before "exit 0"

---

### Post by alfitch0619 on 2009-03-31
Hello - I just purchased the D-Link DWA-140 (ralink rt2870) and Jaunty beta picked it right up.  However, the connection is showing only 54Mb/s and I have a "N" Linksys router set to mixed mode.  Any ideas on how to increase the speed?  I also finally got a linksys WMP300N working in both Intrepid and Jaunty beta and it will show 270Mb/s.

Thanks for any help on the D-link.

---

### Post by RaZoR1394 on 2009-03-31
> **alfitch0619 said:**
> Hello - I just purchased the D-Link DWA-140 (ralink rt2870) and Jaunty beta picked it right up.  However, the connection is showing only 54Mb/s and I have a "N" Linksys router set to mixed mode.  Any ideas on how to increase the speed?  I also finally got a linksys WMP300N working in both Intrepid and Jaunty beta and it will show 270Mb/s.

Thanks for any help on the D-link.

Ubuntu forums crashed...

I was mildly stunned to see that rt2870sta sets my speed to 54/Mb/s with both my Netgear WNR854T and my WRVS4400N router... It was usually 130Mb/s with the WRVS4400N and 270Mb/s with Netgear WNR854T on Jaunty alpha, but I'm on beta now. I need to investigate...

I never get speeds close to 270Mb/s... It's very rare you get over 50% of the set speed. Usually people who use 802.11n draft 2.0 300Mb/s don't reach over 100Mb/s.

I managed to reach 8MB/s by having the router just a few meters away. Usually with my current distance I reach about 4-6MB/s. I have two RP-SMA antennas that can be twisted and turned and I think it could be of some help.

Usually the best approach would be to skip USB and go for miniPCI, PCI or PCI-E. It's a cleaner solution. Usually these cards come with three antennas.

---

### Post by t_virus on 2009-03-31
ok very nice!!!:D its installed but there is a problem:

the wireless adapter is 'unmanaged' and i cant change the mode from 'auto' to 'managed'

see this:


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



any help about this??? i'm allmost done!!!!:D
thankx guys

---

### Post by RaZoR1394 on 2009-03-31
> **alfitch0619 said:**
> Hello - I just purchased the D-Link DWA-140 (ralink rt2870) and Jaunty beta picked it right up.  However, the connection is showing only 54Mb/s and I have a "N" Linksys router set to mixed mode.  Any ideas on how to increase the speed?  I also finally got a linksys WMP300N working in both Intrepid and Jaunty beta and it will show 270Mb/s.

Thanks for any help on the D-link.

I managed to get 130Mb/s set with my Linksys WRVS4400N after fiddling with /etc/Wireless/RT2870STA/RT2870STA.dat

Actually what I did was to try and install the new driver from 20090302 but it resulted in high instability so I had to revert to the old one (provided with Ubuntu) but kept my new .DAT file.

> #The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=*CENSOR*
NetworkType=Infra
WirelessMode=9
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
AuthMode=WPA2
EncrypType=AES
WPAPSK=
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
HT_BADecline=0
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

20090302 crapped out for me very badly so I have to stay at 1.4.0.0 until I've found the cause.

---

### Post by mizunoX on 2009-04-27
> **alfitch0619 said:**
> Hello - I just purchased the D-Link DWA-140 (ralink rt2870) and Jaunty beta picked it right up.  However, the connection is showing only 54Mb/s and I have a "N" Linksys router set to mixed mode.  Any ideas on how to increase the speed?  I also finally got a linksys WMP300N working in both Intrepid and Jaunty beta and it will show 270Mb/s.

Thanks for any help on the D-link.


I'm having the same issue with a ralink 2870 and a fresh Jaunty install.
It finds the card and works without any additional driver compiling/installing however it maxes out at 54Mb/s.   I achieved much higher with the same card and Intrepid (though I had to compile and install a driver as above)

-- EDIT -- I followed someone else's instructions to download the new ralink driver from their website: [http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz]("http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz")
Extract to a folder, enter the folder and 'sudo make', 'sudo make install', reboot and voila.  It's connecting to 5Ghz networks at 300Mb/s.

---

### Post by wendavid on 2009-05-07
This is a very helpful instruction.  My dwa-140 never worked in ubuntu 8.1 but worked immediately in 9.04 after I  followed your procedure.  Thanks a lot

---

### Post by Ultracrat on 2009-05-07
> **Brausepaul said:**
> I changed my /etc/modules file to

fuse
lp
rtc
#alias ra0 rt2870sta
rt2860sta

but I still have to run sudo insmod rt2870sta.ko manually to get my wireless to work.

I had this exact problem with my EDIMAX EW-7717Un USB adapter, and it took me a while to find the cause.  I was able to build the driver from the Ralink website's source without issue, and using the insmod command worked perfectly, but modprobe didn't seem to do anything.

It turned out that Jaunty already has an rt2870sta module installed under /lib/modules/`uname -r`/kernel/drivers/staging/rt2870, so the modprobe command was picking up the wrong module!  I renamed the rt2870sta.ko in that folder to "rt2870sta.ko.disabled", and after that the "modprobe rt2870sta" command started working for me.

I didn't need the "alias ra0 rt2870sta" line in /etc/modules.  I also have to thank whoever mentioned WICD as a replacement for Network Manager -- that turned out to be a very simple way to get rid of the password prompt at bootup.

Hope this helps.

- Keith

---

### Post by adamruck on 2009-06-19
> **Ultracrat said:**
> I had this exact problem with my EDIMAX EW-7717Un USB adapter, and it took me a while to find the cause.  I was able to build the driver from the Ralink website's source without issue, and using the insmod command worked perfectly, but modprobe didn't seem to do anything.

It turned out that Jaunty already has an rt2870sta module installed under /lib/modules/`uname -r`/kernel/drivers/staging/rt2870, so the modprobe command was picking up the wrong module!  I renamed the rt2870sta.ko in that folder to "rt2870sta.ko.disabled", and after that the "modprobe rt2870sta" command started working for me.

I didn't need the "alias ra0 rt2870sta" line in /etc/modules.  I also have to thank whoever mentioned WICD as a replacement for Network Manager -- that turned out to be a very simple way to get rid of the password prompt at bootup.

Hope this helps.

- Keith

Yup, I just discovered this as well. In my opinion modprobe should generate a warning message if two modules have the same name in the same kernel version.

---

### Post by paulcartman on 2009-06-24
GREAT GREAT GREAT THANKS!!!

I've got 'sex' with Asus USB-N11 and Ubuntu 9.04 for 2 days (read many manuals, user-guides and other stuff). But you guide is realy cool, correct and it's work!

Linux is great, but linux-community is better!!! Thank you very much!

---

### Post by etdwh on 2009-06-24
> **Ultracrat said:**
> I had this exact problem with my EDIMAX EW-7717Un USB adapter, and it took me a while to find the cause.  I was able to build the driver from the Ralink website's source without issue, and using the insmod command worked perfectly, but modprobe didn't seem to do anything.

It turned out that Jaunty already has an rt2870sta module installed under /lib/modules/`uname -r`/kernel/drivers/staging/rt2870, so the modprobe command was picking up the wrong module!  I renamed the rt2870sta.ko in that folder to "rt2870sta.ko.disabled", and after that the "modprobe rt2870sta" command started working for me.

Well, that is very useful information. Took me days trying to figure out why the drivers worked in 8.10 but not 9.04. Now it works correctly :D

Anyway, i have a Belkin N+ USB adapter (F5D8055v1).
Steps to get it working for me:

1) Download drivers from Ralink ([http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)). Right now, its 2009_0521_RT2870_Linux_STA_V2.1.2.0.tgz

2) Extract drivers. I extracted to /usr/src.

3) Delete existing rt2870sta driver. Refer to quote above for exact location

4) Edit os/linux/config.mk. Change values of 
HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

5) Edit os/linux/usb_main_dev.c

6) Look for line: {USB_DEVICE(0x050d,0x815c)}, /* Belkin F5D8053 */

7) Add new line below the above: {USB_DEVICE(0x050d,0x825a)}, /* Belkin F5D8055 */

8 ) Save and close file

9) sudo make && sudo make install

10) sudo modprobe rt2870sta
Network manager should now start scanning for wireless networks

To load module at startup...
11) edit /etc/modules. Add new line: rt2870sta

That it :D

---

### Post by gvansickle1 on 2009-06-24
> **mizunoX said:**
> I'm having the same issue with a ralink 2870 and a fresh Jaunty install.
It finds the card and works without any additional driver compiling/installing however it maxes out at 54Mb/s.   I achieved much higher with the same card and Intrepid (though I had to compile and install a driver as above)

-- EDIT -- I followed someone else's instructions to download the new ralink driver from their website: [http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz]("http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz")
Extract to a folder, enter the folder and 'sudo make', 'sudo make install', reboot and voila.  It's connecting to 5Ghz networks at 300Mb/s.
I too have the D-Link DWA-140 (ralink rt2870) and Jaunty 9.04 and am only getting 54Mb/s on on 9.04 with "n" series router (getting 270 off XP). I'm bettin that the new driver would solve my problem as well but being new to Ubuntu (1 week) I'm also bettin that there are some details beyond "Extract to a folder, enter the folder and 'sudo make', 'sudo make install', reboot and voila". ANybody give me some additional info RE "sudo make" and "sudo make install"? Do I cd to a specific folder? What are the specific command lines I need to enter? Any switches to be used, etc? 

I'm new to Ubuntu but lovin it! Already wiped W2K, XP and Vista Home off of the 6 systems at home and have installed and running Ubuntu 9.04 on 3, Xbuntu 8.10 on 1, Kubuntu 9.04 on 1 and Mythbuntu 9.04 on the 6th. It's great to see some daylight...

---

### Post by SilverWave on 2009-07-02
> **mizunoX said:**
> ...
Extract to a folder, enter the folder and 'sudo make', 'sudo make install', reboot and voila.  It's connecting to 5Ghz networks at 300Mb/s.

Thanks for that I went here:
[Linux](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

And downloaded to my Desktop:
2009_0521_RT2870_Linux_STA_V2.1.2.0.tgz
Extracted and followed the instructions quoted...

sudo make
sudo make install

Restarted and I am getting 270Mb/s with a broadband Linksys Wrt160n router set to:

Network Mode:        Mixed	
Radio Band: 	     Wide - 40MHz Channel
Wide Channel: 	     6
Standard Channel:    4 - 4.247GHZ

Tenda Wireless-N USB Adapter
 
Cheers guys and thanks for the help!

---

### Post by daniel.pool on 2009-07-11
> **etdwh said:**
> Well, that is very useful information. Took me days trying to figure out why the drivers worked in 8.10 but not 9.04. Now it works correctly :D

Anyway, i have a Belkin N+ USB adapter (F5D8055v1).
Steps to get it working for me:

1) Download drivers from Ralink ([http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)). Right now, its 2009_0521_RT2870_Linux_STA_V2.1.2.0.tgz

2) Extract drivers. I extracted to /usr/src.

3) Delete existing rt2870sta driver. Refer to quote above for exact location

4) Edit os/linux/config.mk. Change values of 
HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

5) Edit os/linux/usb_main_dev.c

6) Look for line: {USB_DEVICE(0x050d,0x815c)}, /* Belkin F5D8053 */

7) Add new line below the above: {USB_DEVICE(0x050d,0x825a)}, /* Belkin F5D8055 */

8 ) Save and close file

9) sudo make && sudo make install

10) sudo modprobe rt2870sta
Network manager should now start scanning for wireless networks

To load module at startup...
11) edit /etc/modules. Add new line: rt2870sta

That it :D

I've been battling against this issue all day, this post pretty much got me there so thanks etdwh. Just as a note though, having added the drivers I was unable to perform any scan from iwlist. I'd get a message saying the network was down when run under root. The command ifconfig nnn up (where nnn is your adapter name found by running iwconfig) will turn the adapter on.

Thought I'd post just in case it helps anyone else.

---

### Post by pogush on 2009-07-13
> **etdwh said:**
> Well, that is very useful information. Took me days trying to figure out why the drivers worked in 8.10 but not 9.04. Now it works correctly :D

Anyway, i have a Belkin N+ USB adapter (F5D8055v1).
Steps to get it working for me:

1) Download drivers from Ralink ([http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)). Right now, its 2009_0521_RT2870_Linux_STA_V2.1.2.0.tgz

2) Extract drivers. I extracted to /usr/src.

3) Delete existing rt2870sta driver. Refer to quote above for exact location

4) Edit os/linux/config.mk. Change values of 
HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

5) Edit os/linux/usb_main_dev.c

6) Look for line: {USB_DEVICE(0x050d,0x815c)}, /* Belkin F5D8053 */

7) Add new line below the above: {USB_DEVICE(0x050d,0x825a)}, /* Belkin F5D8055 */

8 ) Save and close file

9) sudo make && sudo make install

10) sudo modprobe rt2870sta
Network manager should now start scanning for wireless networks

To load module at startup...
11) edit /etc/modules. Add new line: rt2870sta

That it :D

Thank you so much! this worked pretty well :)

---

### Post by SlvrDragon50 on 2009-07-25
> **etdwh said:**
> Well, that is very useful information. Took me days trying to figure out why the drivers worked in 8.10 but not 9.04. Now it works correctly :D

Anyway, i have a Belkin N+ USB adapter (F5D8055v1).
Steps to get it working for me:

1) Download drivers from Ralink ([http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)). Right now, its 2009_0521_RT2870_Linux_STA_V2.1.2.0.tgz

2) Extract drivers. I extracted to /usr/src.

3) Delete existing rt2870sta driver. Refer to quote above for exact location

4) Edit os/linux/config.mk. Change values of 
HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

5) Edit os/linux/usb_main_dev.c

6) Look for line: {USB_DEVICE(0x050d,0x815c)}, /* Belkin F5D8053 */

7) Add new line below the above: {USB_DEVICE(0x050d,0x825a)}, /* Belkin F5D8055 */

8 ) Save and close file

9) sudo make && sudo make install

10) sudo modprobe rt2870sta
Network manager should now start scanning for wireless networks

To load module at startup...
11) edit /etc/modules. Add new line: rt2870sta

That it :D
Could someone help me?

I'm getting an error during extraction to usr/src

It says:
You don't have the right permissions to extract archives in the folder "file:///usr/src"

I am the only account on this computer as well.

---

### Post by SilvaRizla on 2009-07-27
I installed some updates and lost my wireless, I have tried reinstalling and get this on sudo make && sudo make install


make -C tools                                                                     
make[1]: Entering directory `/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/tools'
gcc -g bin2h.c -o bin2h                                                           
make[1]: Leaving directory `/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/tools' 
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/tools/bin2h                        
cp -f os/linux/Makefile.6 /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'                                                
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/crypt_md5.o                            
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/crypt_sha2.o                           
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/crypt_hmac.o                           
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/mlme.o                                 
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_wep.o                              
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/action.o                               
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_data.o                             
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/rtmp_init.o                            
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_tkip.o                             
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_aes.o                              
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_sync.o                             
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/eeprom.o                               
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_sanity.o                           
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_info.o                             
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_cfg.o                              
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_wpa.o                              
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/dfs.o                                  
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/spectrum.o                             
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/spectrum.c:1898: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’                                                                                                                              
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/rtmp_timer.o                                                         
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/rt_channel.o                                                         
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_profile.o                                                        
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_asic.o                                                           
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/assoc.o                                                                 
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/auth.o                                                                  
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/auth_rsp.o                                                              
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/sync.o                                                                  
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/sanity.o                                                                
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/rtmp_data.o                                                             
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/connect.o                                                               
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/wpa.o                                                                   
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.o                                                         
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:                                     
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:525: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast                                                                                                                               
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:527: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast                                                                                                                               
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:                                       
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:586: warning: assignment makes integer from pointer without a cast
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:                             
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:608: warning: assignment makes integer from pointer without a cast
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:                       
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:628: warning: assignment makes integer from pointer without a cast
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:                              
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:835: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’                                                                                                                             
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_profile.o                                                       
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_main_dev.o                                                      
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/sta_ioctl.o                                                        
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/ba_action.o                                                          
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:                                                                                                                                                  
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/ba_action.c:1509: warning: assignment makes integ
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/usb_main_dev.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_usb.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_mac_usb.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/rtusb_io.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/rtusb_data.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/ee_prom.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/rt2870sta.mod.o
  LD [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/rt2870sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
cp -f /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/rt2870sta.ko /tftpboot
make -C /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.28-13-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.28-13-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.28-13-generic
make[1]: Leaving directory `/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux'

this is the modprobe and then iwconfig

dave@desktop:~/2009_0521_RT2870_Linux_STA_V2.1.2.0$ sudo modprobe rt2870sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
dave@desktop:~/2009_0521_RT2870_Linux_STA_V2.1.2.0$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


Can anybody help?

---

### Post by RaZoR1394 on 2009-07-27
You forgot:

> 
sudo ifconfig ra0 inet up


?

---

### Post by SilvaRizla on 2009-07-27
I installed some updates and lost my wireless, I have tried reinstalling and get this on sudo make && sudo make install


make -C tools                                                                     
make[1]: Entering directory `/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/tools'
gcc -g bin2h.c -o bin2h                                                           
make[1]: Leaving directory `/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/tools' 
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/tools/bin2h                        
cp -f os/linux/Makefile.6 /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'                                                
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/crypt_md5.o                            
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/crypt_sha2.o                           
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/crypt_hmac.o                           
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/mlme.o                                 
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_wep.o                              
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/action.o                               
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_data.o                             
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/rtmp_init.o                            
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_tkip.o                             
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_aes.o                              
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_sync.o                             
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/eeprom.o                               
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_sanity.o                           
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_info.o                             
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_cfg.o                              
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_wpa.o                              
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/dfs.o                                  
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/spectrum.o                             
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/spectrum.c:1898: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’                                                                                                                              
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/rtmp_timer.o                                                         
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/rt_channel.o                                                         
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_profile.o                                                        
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_asic.o                                                           
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/assoc.o                                                                 
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/auth.o                                                                  
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/auth_rsp.o                                                              
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/sync.o                                                                  
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/sanity.o                                                                
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/rtmp_data.o                                                             
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/connect.o                                                               
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../sta/wpa.o                                                                   
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.o                                                         
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:                                     
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:525: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast                                                                                                                               
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:527: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast                                                                                                                               
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:                                       
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:586: warning: assignment makes integer from pointer without a cast
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:                             
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:608: warning: assignment makes integer from pointer without a cast
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:                       
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:628: warning: assignment makes integer from pointer without a cast
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:                              
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:835: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’                                                                                                                             
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_profile.o                                                       
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_main_dev.o                                                      
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/sta_ioctl.o                                                        
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/ba_action.o                                                          
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:                                                                                                                                                  
/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/ba_action.c:1509: warning: assignment makes integ
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/usb_main_dev.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_usb.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_mac_usb.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/rtusb_io.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/rtusb_data.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/ee_prom.o
  CC [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/rt2870sta.mod.o
  LD [M]  /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/rt2870sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
cp -f /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/rt2870sta.ko /tftpboot
make -C /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.28-13-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.28-13-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.28-13-generic
make[1]: Leaving directory `/home/dave/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux'

this is the modprobe and then iwconfig

dave@desktop:~/2009_0521_RT2870_Linux_STA_V2.1.2.0$ sudo modprobe rt2870sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
dave@desktop:~/2009_0521_RT2870_Linux_STA_V2.1.2.0$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


Can anybody help?

---

### Post by SilvaRizla on 2009-07-27
sudo ifconfig ra0 inet up
ra0: ERROR while getting interface flags: No such device

---

### Post by SilvaRizla on 2009-07-27
rebooted again and miraculously sorted, nvm

---

### Post by g_lopp on 2009-08-05
Slightly different problem, but with the same device...

I've compiled, installed, etc the rt2870sta module (a linksys WUSB100 and had to add a usb id for it), but I can't seem to get the network settings set.  I tried directly in /etc/Wireless/RT2870STA/RT2870STA.dat and again using wifi-radar : 

$ sudo wifi-radar
[sudo] password for greg: 
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device ra0 ; Invalid argument.
There is already a pid file /var/run/dhclient.ra0.pid with pid 4092
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/run/dhclient.ra0.leases: Permission denied
Listening on LPF/pan0/42:00:db:8d:de:d8
Sending on   LPF/pan0/42:00:db:8d:de:d8
Listening on LPF/ra0/00:1e:e5:e9:f3:d6
Sending on   LPF/ra0/00:1e:e5:e9:f3:d6
Listening on LPF/eth0/00:24:8c:70:ed:6b
Sending on   LPF/eth0/00:24:8c:70:ed:6b
Sending on   Socket/fallback
Unsupported driver '-P'.

SIOCSIFNETMASK: Cannot assign requested address
SIOCADDRT: Invalid argument


I will confess to using WEP (I know, I know, bad greg) as I know that is germane to which settings I need to fiddle with.

---

### Post by NeedSomeHelp on 2009-08-10
Hi ,

I tried to install my WUSB600N USB wireless card on my ubuntu8.04 32 bit Desktop. I followed the instruction on nilsa5's post from step 1 up to step 15. But the LED light on USB Card didn't blink at all . I did some diagnostic .
1.#lsusb
Bus 005 Device 002:ID 1737:0079
.......................
.......................
Seems computer recognized the USB Stick .

2.#dmesg:
[241.971014]rtusb init --->
[241.971438]usbcore:registered new interface driver rt2870
.....................
.....................
Seems the Ralink rt2870 driver loaded successfully.

3.#iwconfig 
lo no wireless extensions
eth0 no wireless extensions

Then I did step 16 to step 19. Still iwconfig shows the same result , the computer can't pick up the WUSB600N USB stick at alll and the WUSB600N USB stick didn't blink at all. I don't know what  to do now and what's wrong with my installation. 

Any help would be greatly appreciated. :(

---

### Post by deankovell on 2009-08-11
I had the same problem, but made a little headway with it.

> 1.#lsusb
Bus 005 Device 002:ID 1737:0079
.......................
.......................
Seems computer recognized the USB Stick .
try gedit /os/linux/usb_main_dev.c 
It should show a list of wireless cards with the rt2870 chip in them that the driver works for. I noticed that the wusb600n is listed, but the device id number is different than what lsusb showed on my computer.the entry on the file looks like this.

"{USB_DEVICE(0x1737,0x0071)}, /* WUSB600N */ " That may not be exactly what it said (I can't get to that computer right now) but I tried changing the 0071 to 0079 before I compiled the driver, and it sort of worked. The light on the adapter came on (solid, no flashing) with "sudo modprobe rt2870sta" and "sudo ifconfig ra0 up". however I still can't get "iwlist ra0 scan" to bring back any results. 

see post #5 if you're using an older version of the driver

I still pretty new to this sort of thing, and I'm still having problems with this, so I don't know if I'd recomend making that change or not, but maybe someone that does know what they're doing will see this and tell you if you should do it. 
also try this thread. There's a lot of people that have gotten the adapter to work.
[http://ubuntuforums.org/showthread.php?t=766850](http://ubuntuforums.org/showthread.php?t=766850)

---

### Post by Huufarted on 2009-08-12
I had the issue where it does not work after compiling fresh drivers.  After you rename the rt2870sta.ko file from the existing 2.6.27 (or whatever) kernel, to use the file that you just built from your new driver download/compilation, make sure you cd os/linux in the driver source directory and THEN 'sudo modprobe rt2870sta'.

---

### Post by deankovell on 2009-08-13
> I had the issue where it does not work after compiling fresh drivers. After you rename the rt2870sta.ko file from the existing 2.6.27 (or whatever) kernel, to use the file that you just built from your new driver download/compilation, make sure you cd os/linux in the driver source directory and THEN 'sudo modprobe rt2870sta'.

I got that part of it right, actually, and then "sudo ifconfig ra0 up " turns the light on on the adapter, but it doesn't flash like everyone else describes. iwconfig shows it's there, but shows it at 1Mb/s and  "sudo iwlist ra0 scan" brings back no results, when I know that 7 or 8 different people's routers would have showed up with a scan in windows.

---

### Post by Huufarted on 2009-08-14
> **deankovell said:**
> I got that part of it right, actually, and then "sudo ifconfig ra0 up " turns the light on on the adapter, but it doesn't flash like everyone else describes. iwconfig shows it's there, but shows it at 1Mb/s and  "sudo iwlist ra0 scan" brings back no results, when I know that 7 or 8 different people's routers would have showed up with a scan in windows.

I'm seeing identical results to you, bud.  2 SSID's here at work and no less than 8 when I'm at home in my apartment and I can't get any networks to show up at all.  This is with network-manager or WICD.

---

### Post by deankovell on 2009-08-15
Hey, huufarted!!! that stinks!!

 I just found a bug report on this adapter. I assume you have v2 also.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165)

Edit: 
Sad to say that I gave up on the wusb600Nv2. traded it in for a belkin adapter with the same chipset and everything is working perfectly. I will still try to relay the problem to canonical staff if that's the proper way to handle the bug.

---

### Post by NeedSomeHelp on 2009-08-15
I made changes in the code as deankovell suggested as his post in the usb_main_dev.c, recompiled the driver, now the light is on , but solid, with no blinks, my # iwlist ra0 scanning show no results as well, Now I am confused as your guys and I don't know waht to do next. 

Hope somebody can save us from this. 

Many thanks.

---

### Post by allquixotic on 2009-08-20
Hi,

I'm the one who reported Bug 408165 on this adapter. It's been weeks and no one has replied to the bug. It seems like there is no clear resolution path to this issue right now. I'm having the same difficulties as you guys with the WUSB600N v2. (Just to be clear, the USB ID of a "v2" card is 1737 : 0079. The v1, which works, is 1737 : 0071.)

Since rt2870 is now part of the Linux kernel, technically "the Linux kernel maintainers" are the ones who are supposed to "fix" this for us. But Ralink engineers are the primary driving force in improving that module. This card has been on the market for months without any driver support. I also tried Ndiswrapper to no avail.

I think getting in touch with Canonical staff would be the best resolution path; when they put their mind to it, they have an excellent way of "convincing" manufacturers to support their stuff. I'm not sure if they should look to Linksys or Ralink, but between them they should be able to get this ready for Karmic, or at LEAST Karmic+1. Ideally any required changes to rt2870 would be merged back into mainline.

---

### Post by Danneman on 2009-08-21
Could someone with an installed Karmic tell me which version of this module is included in the kernel? I need at least version 2.1.2.0 (or even better 2.2.0.0, as found on [Ralinks site]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")) for my network card.

Last time I looked Karmic came with 1.4.0.0 and 2.1.2.0 (which was the latest at the time) refused to compile...

/Daniel

---

### Post by thecow on 2009-08-23
Ah so this is an established problem.  Ive been trying for a while now to see if theres some extra little piece of code that needs to work to get V2 of the WUSB600N to scan.  Just a constant light like all of you I guess

---

### Post by viper3500 on 2009-08-29
hey ive been trying to follow ur steps but i have run into a problem. since i am unable to get on the internet from my ubuntu computer i had to go on to my laptop and download the file to a usb drive and and then move it to my computer with ubuntu. the problem i am having is when i am trying to ralink file from my flash drive to my usr/src folder it says permision denied. how do i get aroud that

---

### Post by daniel.pool on 2009-08-30
I recently had cause to rebuild my ubuntu media server which I connect to a local NAS using a the Belkin N+ USB F5D8055v1.

> **etdwh said:**
>  Anyway, i have a Belkin N+ USB adapter (F5D8055v1).

Previously I'd been able to follow etdwh's instructions without any problems as he has exactly the same adapter as me. However, instead of downloading the 2.1.2.0 drivers ralink have now made available the 2.2.0.0 version which I downloaded and installed as normal.

However, nothing I did would make the card connect. As far as I could see the config was identical to my previous working config. I therefore rolled back to the 2.1.2.0 drivers and tried those and got my wireless connection back. Not sure what was wrong or why it wouldn't connect, but there you go.

Has anyone else tried the 2.2.0.0 version with any luck?

A few things I have noticed:
2.1.2 connects only at 54Mbps, not the 130Mbps supported by my router
both versions complain about not being able to start the wpa_supplicant daemon on a /etc/init.d/networking restart
both versions will report invalids on the receiving when running an iwconfig:

```
ra0       RT2870 Wireless  ESSID:"[Detail removed]"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:22:69:2A:C8:1B
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-52 dBm  Noise level:-71 dBm
          **Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0**
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```despite the 2.1.2 giving me a working connection.

---

### Post by rkwong on 2009-09-04
I recently purchased the Belkin wireless usb adapter f5d8055 v2. It has an ID of 0x050d,0x825b. I followed exactly the same procedure as described for f5d8055 v1, changing only the usb ID to 0x050d,0x825b. The rt2870sta module compiled with no difficulty. However, while the wireless adapter is detected as ra0, it does not scan and cannot connect. I have tried using 2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2, 2009_0521_RT2870_Linux_STA_V2.1.2.0.tgz, as well as version 2.1.1 and 1.4. All of them compiled but none of them worked. It does not work with ndiswrapper either. I have also tried the module in hardy, intrepid, and jaunty, without any success. The adapter does work under Windows XP.

Does anyone have any experience with the Belkin f5d8055 v2 under linux?

---

### Post by wesswei on 2009-09-04
Well, add me to the dazed and confused list. I'm trying to compile the driver to work for the Asus USB-N11 wireless usb card, but it is giving me the darnedest time! 

This is not a simple make and compile here. Device IDs and vendor IDs are missing. IF this is part of the kernel already, there needs to be a fix!!!

What happened to rt2x00 project? Do they cover rt2870? My Linksys wusb54g worked great out of the box... that is after a couple of years of compiling the drivers from source and two new ubuntus later.

Stuck with G for now on ubuntu, until there is a decent fix for this. I'm filing a bug too!

---

### Post by qhaz on 2009-09-07
> **Danneman said:**
> Could someone with an installed Karmic tell me which version of this module is included in the kernel? I need at least version 2.1.2.0 (or even better 2.2.0.0, as found on [Ralinks site]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")) for my network card.

Last time I looked Karmic came with 1.4.0.0 and 2.1.2.0 (which was the latest at the time) refused to compile...

/Daniel

Hey Daniel, I'm running Karmic with kernel 2.6.31-7-generic and have tried to get my Belkin USB N1 F5D8051 to work.  I can confirm that the rt2870sta driver that loads when I attach the modem is version 1.4.0.0
. . . and unfortunately I've been unable to get it to work.  It recognises my home pc AP but fails to connect with a "Unable to get IP" thingy error.
The module is loaded from the "staging" lib/modules directory and due warnings are given about the reliability of it ;-(


cheers

---

### Post by nickmcg on 2009-09-09
Have you blacklisted rt2800usb?

Karmic seems to try and load rt2870sta AND rt2800usb, and I can't get rt2800usb to work.

Put the line 'blacklist rt2800usb' in /etc/modprobe.d/blacklist.conf and you should be able to use wireless.

If anyone knows how to get rt2800usb working, I'd love to know as it's supposed to be the new version.

Nick

---

### Post by elmo88 on 2009-09-10
> **rkwong said:**
> I recently purchased the Belkin wireless usb adapter f5d8055 v2. It has an ID of 0x050d,0x825b. I followed exactly the same procedure as described for f5d8055 v1, changing only the usb ID to 0x050d,0x825b. The rt2870sta module compiled with no difficulty. However, while the wireless adapter is detected as ra0, it does not scan and cannot connect. I have tried using 2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2, 2009_0521_RT2870_Linux_STA_V2.1.2.0.tgz, as well as version 2.1.1 and 1.4. All of them compiled but none of them worked. It does not work with ndiswrapper either. I have also tried the module in hardy, intrepid, and jaunty, without any success. The adapter does work under Windows XP.

Does anyone have any experience with the Belkin f5d8055 v2 under linux?
Let me know if someone got this working for Belkin wireless usb adapter f5d8055 v2 too!
I recently got the v2 stick instead of v1 stick (not available anymore).
I followed the same setup procedure for v1, but changed the USB id code from 0x050d,0x825a to  0x050d,0x825b.

"sudo ifconfig ra0 up" glows up the blue signal light on the stick, but I don't think it's operational.  It doesn't scan for AP....

Thanks!

---

### Post by verto8 on 2009-09-17
I tried to install the driver for my Buffalo WLI-UC-GN Wireless Adapter (USB dongle) but it seems like the device is still not getting recongized by the OS. I am using Linux Mint 7 and here is the log from terminal:

```
s@s ~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0 $ sudo make
make -C tools
make[1]: Entering directory `/home/s/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/s/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools'
/home/s/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/s/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/s/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/s/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/s/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/s/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
cp -f /home/s/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.ko /tftpboot
s@s ~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0 $ sudo make install
make -C /home/s/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/s/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/s/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.28-11-generic
make[1]: Leaving directory `/home/s/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux'
s@s ~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0 $ sudo insmod rt2870sta.ko
insmod: can't read 'rt2870sta.ko': No such file or directory
s@s ~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0 $ sudo modprobe rt2870sta
s@s ~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0 $ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ra0.

```Any help is greatly appreciated. Thanks.

---

### Post by nickmcg on 2009-09-18
I cannot understand why is your insmod command failing, yet your modprobe command seems to be working.

what does lsusb show?

What does iwconfig show?

Nick

---

### Post by verto8 on 2009-09-18
Hi **nickmcg**, thanks for the reply. It is a strange issue indeed because the USB device LED light is on and is being seen by the OS as "Bus 001 Device 004: ID 0411:015d MelCo., Inc. " but something is wrong somewhere. I have rebooted and re-tried the installation and then rebooted it again with no results.

```

s@s ~ $ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:0716 Genesys Logic, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0411:015d MelCo., Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0461:4d42 Primax Electronics, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
s@s ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

```

---

### Post by nickmcg on 2009-09-18
If you google '0411:015d' there appear to be a lot of problems with this device.

Out of interest, what do you get from ```
dmesg | grep rt2
```?

Nick

---

### Post by verto8 on 2009-09-18
So the device is now being picked up?

```

s@s ~ $ dmesg | grep rt2
[   10.485759] usbcore: registered new interface driver rt2870

```

---

### Post by nickmcg on 2009-09-18
What happens if you ```
sudo modprobe -vr rt2870sta
```
then ```
sudo modprobe -v rt2870sta
```

Follow that with ```
iwconfig
ifconfig
```

This is very puzzling

Nick

---

### Post by verto8 on 2009-09-18
Hey Nick, thanks for continuing to follow up on this. I do have 'rt2870sta' line added to the /etc/modules and I have also added 'auto ra0 && iface ra0 inet dhcp' to /etc/network/interfaces.

```

s@s ~ $ sudo modprobe -vr rt2870sta
s@s ~ $ sudo modprobe -v rt2870sta
insmod /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rt2870sta.ko 
s@s ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

s@s ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:d8:a8:XX  
          inet addr:10.X.X.X  Bcast:10.X.X.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fed8:a8XX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:151897 (151.8 KB)  TX bytes:56324 (56.3 KB)
          Interrupt:253 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:21:27:e0:0d:XX  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

```

---

### Post by nickmcg on 2009-09-21
It looks as though the either the module is not being loaded or the interface is not being recognised.

What do  you get from ```
lsmod | grep rt2
```

If rt2870 shows up, you could try ```
sudo depmod -a
```

After that, I'm out of ideas.

Nick

---

### Post by verto8 on 2009-09-21
Hi Nick thanks again for the reply. I am very confused as to what is the problem is. It seems like the USB is detected but not the wireless adapter part.

Check this out:
```

s@s /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless $ ls
adm8211.ko   atmel.ko       ipw2100.ko     orinoco.ko         ray_cs.ko       strip.ko
airo_cs.ko   atmel_pci.ko   ipw2200.ko     orinoco_nortel.ko  rndis_wlan.ko   wavelan_cs.ko
airo.ko      b43            iwlwifi        orinoco_pci.ko     rt2870sta.ko    wavelan.ko
arlan.ko     b43legacy      libertas       orinoco_plx.ko     rt2x00          wl3501_cs.ko
ath5k        hermes_dld.ko  libertas_tf    orinoco_tmd.ko     rtl8180.ko      zd1201.ko
ath9k        hermes.ko      netwave_cs.ko  p54                rtl8187.ko      zd1211rw
atmel_cs.ko  hostap         orinoco_cs.ko  prism54            spectrum_cs.ko
s@s /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless $ sudo insmod rt2870sta.ko
insmod: error inserting 'rt2870sta.ko': -1 File exists
s@s /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless $ lsmod | grep rt2
rt2870sta             548588  0 
s@s /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless $ sudo depmod -a
s@s /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless $ 

```

---

### Post by vordme34 on 2009-09-21
When I run: "insmod rt2870sta.ko" I get: "insmod: error inserting 'rt2870sta.ko': -1 Operation not permitted"
even with: "sudo insmod rt2870sta.ko" I get: "insmod: error inserting 'rt2870sta.ko': -1 File exists"
Any ideas?
Did anything else you advise, will try to see if the chip gets up..

---

### Post by crtaylor1970 on 2009-09-21
Hey all, after spending much too long fighting various windows OS, I decided to go with Kubuntu. Due to new living conditions I need to go wireless on my desktop pc. My wireless of choice is the linksys wusb54gc v.3  After spending the last 5 days trying to get it working, I have gotten nowheres. No light on the adapter itself. I get this:

chuck@chuck-desktop:~$ sudo modprobe -vr rt2870sta
[sudo] password for chuck: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rmmod /lib/modules/2.6.28-15-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
chuck@chuck-desktop:~$ sudo modprobe -v rt2870sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
insmod /lib/modules/2.6.28-15-generic/kernel/drivers/staging/rt2870/rt2870sta.ko 
chuck@chuck-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

virbr0    no wireless extensions.

pan0      no wireless extensions.

chuck@chuck-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:21:10:56:92  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:fe10:5692/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12585862 (12.5 MB)  TX bytes:2374770 (2.3 MB)
          Interrupt:252 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21186 (21.1 KB)  TX bytes:21186 (21.1 KB)

virbr0    Link encap:Ethernet  HWaddr e2:40:30:b9:70:42  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::e040:30ff:feb9:7042/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:5456 (5.4 KB)

chuck@chuck-desktop:~$ 


I cannot seem to find a driver to download that will work with this. Anyone give me a hand with this, please?

---

### Post by Caracal17 on 2009-09-22
[http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html") Seems to be down. Could somebody possibly send me a copy of the driver I need for a x86 platform? Or maybe provide a different link?
Thanks!

---

### Post by nickmcg on 2009-09-23
You always need to run insmod or modprobe as root ```
sudo insmod ....
```otherwise you will get permission denied

Nick

---

### Post by nickmcg on 2009-09-23
> **Caracal17 said:**
> [http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html") Seems to be down. Could somebody possibly send me a copy of the driver I need for a x86 platform? Or maybe provide a different link?
Thanks!
It looks like they've had a major redesign - try [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Nick

---

### Post by t_virus on 2009-09-23
search no more:

[http://forums.remote-exploit.org/bt4beta-non-working-hardware/20408-wirelesscards-rt2870-2860-chipsets-3.html](http://forums.remote-exploit.org/bt4beta-non-working-hardware/20408-wirelesscards-rt2870-2860-chipsets-3.html)

injection suport

---

### Post by oblio on 2009-09-25
> **Caracal17 said:**
> [http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html") Seems to be down. Could somebody possibly send me a copy of the driver I need for a x86 platform? Or maybe provide a different link?
Thanks!

it's now:

[http://eng.ralinktech.com.tw/support.php?s=2](http://eng.ralinktech.com.tw/support.php?s=2)

oblio

---

### Post by king20878 on 2009-09-29
> **nickmcg said:**
> Have you blacklisted rt2800usb?

Karmic seems to try and load rt2870sta AND rt2800usb, and I can't get rt2800usb to work.

Put the line 'blacklist rt2800usb' in /etc/modprobe.d/blacklist.conf and you should be able to use wireless.

If anyone knows how to get rt2800usb working, I'd love to know as it's supposed to be the new version.

Nick


FWIW blacklisting rt2800usb is all it took to get my Linksys wusb100 working with 9.1 b5.

---

### Post by daglamier on 2009-10-02
I have already performed all the steps in this thread and still having troubles getting my Belkin f6d4050 v2 working in ubuntu 9.04.  I have gotten it working in 8.04 previously with ndiswrapper but it would freeze up every 5 minutes to a couple hours and require a reboot.
 
lsusb shows the belkin device
lsmod shows rt2870sta loaded
the light on my usb device blinks occasionally
network manager does not show wireless networking as an option, only a disconnected wired connection
 
any thoughts or other information you need me to post? I'm posting on a seperate computer as the main computer is too far away from router to hardwire
 
Thanks

---

### Post by daglamier on 2009-10-03
btw, using 64bit ubuntu, and more info on my usb card:     050d:935b


iwlist ra0 scan doesn't come up with any wireless network but i now got network manager to actually show that there is a wireless connection there, but its all greyed out with no networks listed


not a problem with my router or signal because with ndiswrapper it does see and connect to the network, just trying not to go back to ndiswrapper


any ideas?

---

### Post by thecow on 2009-10-04
> **nickmcg said:**
> Have you blacklisted rt2800usb?

Karmic seems to try and load rt2870sta AND rt2800usb, and I can't get rt2800usb to work.

Put the line 'blacklist rt2800usb' in /etc/modprobe.d/blacklist.conf and you should be able to use wireless.

If anyone knows how to get rt2800usb working, I'd love to know as it's supposed to be the new version.

Nick

This worked for me.  However I can only connect to a 'G' network and not the 'N' I so happily paid money for.  Im about to give up Linux after a few years as honestly enough annoyances have built up over the past few weeks that I just cant hang man.  This not working with N is baffling to me.  I use WPA2 which I guess is too much to handle

---

### Post by nickmcg on 2009-10-04
> **thecow said:**
> This worked for me.  However I can only connect to a 'G' network and not the 'N' I so happily paid money for.  Im about to give up Linux after a few years as honestly enough annoyances have built up over the past few weeks that I just cant hang man.  This not working with N is baffling to me.  I use WPA2 which I guess is too much to handle

If I don't blacklist rt2800usb, then I can only see G networks, if I do blacklist it, then I can connect to my N network (this one)

Nick

---

### Post by thecow on 2009-10-04
Are you running WPA?  I guess too many Linux things hit me all at one time, anyways Ive made amends with it.  Just seems odd to me that I can connect to my G/N network, but if I set it to only be an N network it won't connect.  Im using a Linksys WUSB600N, Im almost positive it can utilize 2 and 5 GHz bands with N

---

### Post by chiefchimp on 2009-10-08
> **SlvrDragon50 said:**
> Could someone help me?

I'm getting an error during extraction to usr/src

It says:
You don't have the right permissions to extract archives in the folder "file:///usr/src"

I am the only account on this computer as well.

I'm probably too late but I didn't see a reply to this so here goes.

Use sudo tar ......

---

### Post by nickmcg on 2009-10-08
> **thecow said:**
> Are you running WPA?  I guess too many Linux things hit me all at one time, anyways Ive made amends with it.  Just seems odd to me that I can connect to my G/N network, but if I set it to only be an N network it won't connect.  Im using a Linksys WUSB600N, Im almost positive it can utilize 2 and 5 GHz bands with N

Yes, I'm using WPA

---

### Post by gizmobay on 2009-10-11
I bought a Belkin USB wifi 050d:935a . I followed the directions and I compile the drivers and when I modprobe a ra0 link is created. I then do a sudo ifconfig ra0 up and I can see the device but when I try to scan I get no results also networkmanager can't even see the ra0 interface. Anyone have any insight?

---

### Post by deankovell on 2009-10-13
I can't answer any of the above questions. Sorry. but, I  wanted to show a little bit different way I went about getting this driver to load on boot. 
added the rt2870sta line to /etc/modules
changed the name of the built in rt2870sta.ko to rt2870sta.ko.disabled
created a symlink to the compiled driver I downloaded from ralink. 
for me I did it like this
```
sudo ln -s /usr/src/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/rt2870sta.ko /lib/modules/2.6.28-15-generic/kernel/drivers/staging/rt2870/rt2870sta.ko

```

It now loads at boot.

---

### Post by nusntu on 2009-10-13
> **gizmobay said:**
> I bought a Belkin USB wifi 050d:935a . I followed the directions and I compile the drivers and when I modprobe a ra0 link is created. I then do a sudo ifconfig ra0 up and I can see the device but when I try to scan I get no results also networkmanager can't even see the ra0 interface. Anyone have any insight?
 I have the same problem. My dongle is Linksys WUSB54GC. From the dmesg i can see the driver is keep scanning and always returns 0 BSS. The network manager is unable to detect  my dongle, i checked the syslog and it said:
NetworkManager: <WARN> wireless_get_range(): (ra0) : couldn't get driver range information (100).
NetworkManager: <WARN> constructor(): (ra0) : Device unsupoorted, ignoring.
 
 
Any idea?

---

### Post by rabbyte on 2009-10-14
I have a WUSB600Nv2 ( 1737:0079 ). After a few hours of searching this thread was the most informative on the web (thanks!) and also slightly disappointing as there is no resolution yet.

What happens next?
Is it reasonable to believe a fix will be available within a month or two?
Is there a URL I should bookmark to check for progress updates besides this thread?

Thanks again.

---

### Post by thecow on 2009-10-14
Could someone post the compiled 2.2.0.0 .ko module here?  I cant seem to build it from source using Karmic Beta.

---

### Post by Apolonios on 2009-10-16
[FONT=Arial]Hello:

I recently installed Ubuntu 9.04 and I'm using a Belkin USB Wireless G adapter.

From a fresh install Ubuntu recognizes the wireless card but Internet navigation is really slow plus the LED on the card does not light up or flash.

I tried installing the rt2870 drivers using the method mentioned on this post and in this link: [http://en.gentoo-wiki.com/wiki/Ralink_RT2870](http://en.gentoo-wiki.com/wiki/Ralink_RT2870)

Now I did everything up to adding the following line to the "[/FONT]/etc/conf.d/modules[FONT=Arial]" file
[/FONT][FONT=Arial][FONT=Courier New]# Ralink Wireless Driver for Belkin USB adapter.
modules="rt2870sta"[/FONT]

I rebooted the PC and the wireless light is still not lighting up and it's still very slow.

How do I know if Ubuntu is even using the driver I just compiled??

Does this driver support WPA2?[/FONT]

---

### Post by raidmin on 2009-10-17
Hello,

today I got a WNC-0600USB from Level1 to replace my old 802.11g one.
With all of the information in this thread I was able to install the driver and got a connection to my AP, but I have a problem with the speed.
I tested it on speedcheck website with my old WLAN connection and it was about 8200 kbit down and 980 kbit up. Now with the new one i got 14500 kbit down but only 3 kbit up.
There is no firewall or something that could block the upload and when I use the old one, it will comes up to 980 kbit as before.
I also tried on Windows to be sure its not broken.
It works without problems and with the full speed.
At least I changed the USB-Port without success.
Is this a known "3 kbit bug" or something or how can I fix it?

Thanks,
raidmin

---

### Post by Ghiepo on 2009-10-22
Following the wiki of Razor1394 now the wifi works on Jaunty, I was wondering, in XP I can use this WiFi (that is onboard on my Asus) as Access Point, is it possible to make the same on Ubuntu?
Thank you, bye.

---

### Post by RaZoR1394 on 2009-10-22
> **Ghiepo said:**
> Following the wiki of Razor1394 now the wifi works on Jaunty, I was wondering, in XP I can use this WiFi (that is onboard on my Asus) as Access Point, is it possible to make the same on Ubuntu?
Thank you, bye.

I've been trying that on my Bubba|TWO but I've been unsuccesfull as I can't even start the interface. I guess things are different on PowerPC. I saw a reference to using the rt2870 as accesspoint on the Gentoo wiki but that's about it. It should be possible however.

---

### Post by RaZoR1394 on 2009-10-22
> **Apolonios said:**
> [FONT=Arial]Hello:

I recently installed Ubuntu 9.04 and I'm using a Belkin USB Wireless G adapter.

From a fresh install Ubuntu recognizes the wireless card but Internet navigation is really slow plus the LED on the card does not light up or flash.

I tried installing the rt2870 drivers using the method mentioned on this post and in this link: [http://en.gentoo-wiki.com/wiki/Ralink_RT2870](http://en.gentoo-wiki.com/wiki/Ralink_RT2870)

Now I did everything up to adding the following line to the "[/FONT]/etc/conf.d/modules[FONT=Arial]" file
[/FONT][FONT=Arial][FONT=Courier New]# Ralink Wireless Driver for Belkin USB adapter.
modules="rt2870sta"[/FONT]

I rebooted the PC and the wireless light is still not lighting up and it's still very slow.

How do I know if Ubuntu is even using the driver I just compiled??

Does this driver support WPA2?[/FONT]

modinfo rt2870sta

in a terminal should give you some info about the module

---

### Post by WiseGuy1020 on 2009-10-22
I just installed 9.10 RC and all it took was blacklisting rt2800usb. I am using a D-link DWA-160.

```
dman@Dman-Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"JDubs"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:24:01:37:F7:B4   
          Bit Rate=270 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-49 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by Ghiepo on 2009-10-23
About Access Point I just create a new network, choosen WPA WPA2 Personal for the security, and I tried to connect with my I-Pod Touch and I was able to navigate the Web but I had only one problem....when I joined the network with the I-Pod I didn't received any request for WPA Key, I was absolutely free to join the network!!! how is it possible?:confused:

---

### Post by aldolat on 2009-10-23
Hi there. :)

I have the same problem as others: on Karmic RC, my Belkin F5D8055 USB adapter is recognized but it can detect only G networks. If I setup my router Belkin on G network only, my adapter tries to connect without success.

I tried to recompile the driver but I got errors, even if in Jaunty I compiled and used it successfully.

> **WiseGuy1020 said:**
> I just installed 9.10 RC and all it took was blacklisting rt2800usb. I am using a D-link DWA-160.

About this, if I blacklist rt2800usb, the adapter's light stops flashing.

Any help? :confused:

---

### Post by AlanRick on 2009-10-23
Rats. ](*,)

Today's Hardy LTS security update has killed my wlan. :( Now I'll have to find time at the weekend to go through the whole rigmarole of downloading (from windows xp - long live dual boot), compiling, and trying to get it up and running again.

---

### Post by SilverWave on 2009-10-23
> **WiseGuy1020 said:**
> I just installed 9.10 RC and all it took was blacklisting rt2800usb. I am using a D-link DWA-160.

```
dman@Dman-Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"JDubs"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:24:01:37:F7:B4   
          Bit Rate=270 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-49 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

OK blacklisting rt2800usb worked for me as well...

> Karmic seems to try and load rt2870sta AND rt2800usb, and I can't get rt2800usb to work.

Put the line 'blacklist rt2800usb' in /etc/modprobe.d/blacklist.conf and you should be able to use wireless.

```
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"Knight"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.427 GHz  Access Point: 00:21:29:77:57:2D   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-53 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
```

but "Bit Rate=54 Mb/s" :(

Making progress but what have I missed?

Details:
Tenda W322U 11N Wireless USB Adapter
Ubuntu Karmic RC

---

### Post by AlanRick on 2009-10-24
> **AlanRick said:**
> Rats. ](*,)

Today's Hardy LTS security update has killed my wlan. :( Now I'll have to find time at the weekend to go through the whole rigmarole of downloading driver source (from windows xp - long live dual boot), compiling, and trying to get it up and running again.
Well, thanks to Razor's [wiki]("http://ubunturt2870.pbwiki.com/FrontPage") this only wasted two hours of my weekend.
Observations:
1. The wiki works well for Hardy however the downloaded make file did not work this time round. Somehow the libraries weren't found. However, I followed the instructions to change the original ralink make file and then it worked fine.

2. I somehow messed things up after I'd got it working ](*,) I'm not sure if that was to do with installing from a multi-user pc or what. 
I got out of the mess by copying the source files to my *opt* folder before compiling (instead of a user's home), following the whole process until *"Networkmanager should see your available networks within one minute."*. At that point I waited a minute or two before rebooting (even though wlan hadn't reacted) without trying out the mount/unmount instructions. After the boot everything works ok for all pc users.

Many thanks Razor for this wiki,
Alan

---

### Post by sauroman on 2009-10-24
Hi, 

I seem to be getting the same problems as verto8 in earlier posts. My Belkin N+ (F5D8055 v1) wireless adapter in which I just bought the other day from Play.com is not being recognized in iwconfig or ifconfig.  

I am using the latest drivers downloaded from the ralink mentioned in the earlier posts and have renamed the old rt2870sta.ko to rt2879sta.ko.old.

```

lsmod | grep rt2
rt2870sta             544364  0

modprobe -v rt2870sta 
insmod /lib/modules/2.6.28-15-generic/kernel/drivers/net/wireless/rt2870sta.ko 

lsusb 
Bus 001 Device 011: ID 050d:825a Belkin Components

dmesg | grep rt2 
usbcore: registered new interface driver rt2870

```

I have noticed that when I remove the usb adapter and replace it I get this -
```
 
dmesg
[ 4098.100020] usb 1-1: new high speed USB device using ehci_hcd and address 10
[ 4098.248214] usb 1-1: configuration #1 chosen from 1 choice

```

There seems to be no sign of registering it as a rt2870 device or a wireless device, or is this correct?

Any help on this would be greatly appreciated.

Btw, I am using kubuntu 9.04 KDE 4.3, i386  - kernel 2.6.28-15-generic

---

### Post by SilverWave on 2009-10-25
I have posted a bug report on launchpad.

Karmic RC tries to load rt2870sta AND rt2800usb. Results in no WiFi 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323)

Karmic seems to try and load rt2870sta AND rt2800usb.
Breaks wireless connectivity.
Worked in Ubuntu 9.04 - Jaunty.

Confirmed Workaround:
Put the line 'blacklist rt2800usb' in /etc/modprobe.d/blacklist.conf and you are able to use wireless.

Details:
Tenda W322U 11N Wireless USB Adapter
Ubuntu 9.10 RC - Karmic

Linux neon 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
Ubuntu 2.6.31-14.48-generic
Bus 001 Device 002: ID 148f:2870 Ralink Technology, Corp.

---

### Post by njparton on 2009-10-29
> **SilverWave said:**
> I have posted a bug report on launchpad.
 
Karmic RC tries to load rt2870sta AND rt2800usb. Results in no WiFi 
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323)
 
Karmic seems to try and load rt2870sta AND rt2800usb.
Breaks wireless connectivity.
Worked in Ubuntu 9.04 - Jaunty.
 
Confirmed Workaround:
Put the line 'blacklist rt2800usb' in /etc/modprobe.d/blacklist.conf and you are able to use wireless.
 
Details:
Tenda W322U 11N Wireless USB Adapter
Ubuntu 9.10 RC - Karmic
 
Linux neon 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
Ubuntu 2.6.31-14.48-generic
Bus 001 Device 002: ID 148f:2870 Ralink Technology, Corp.
 
Well that doesn't work for me unfortunately.
 
I'm using 9.10 x64 (final release) with an Edimax 7718Un USB adapter.
 
I've subscribed to you launchpad bud report in the hope that this is fixed sometime soon...

---

### Post by nick77 on 2009-10-29
I think one part of the problem is, that the 2870 module is at V 1.4.0.0 only (the actual one on ralink website is 2.2...). For example, my USB ID of my device (Buffalo WLI--UC-G300N isn't included yet in this version, however by default in 2.2

As a result, even after blacklisting I won't be able to connect as the correct driver won't be loaded.

There is only one way to get that working in my eyes: we need to be able to compile the original ralink source which won't compile at the moment. Unfortunately, I don't neither why nor how to fix it...

I hope either Ralink or Ubuntu will provide us with an updated version very soon - and in the meantime I wouldn't mind some geeky work-arounds if anybody has one to share!

Nick

---

### Post by njparton on 2009-10-29
In theory could I swap out my usb adapter for a wireless access point connected via ethernet (and therefore not requiring drivers)?

---

### Post by ff8jake on 2009-10-30
Hi Guys!

Would just like to confirm I have D-Link DWA-140 working by adding 'rt2800usb' to the /etc/modprobe.d/blacklist.conf - then adding rt2870sta to /etc/modules.

Cheers!:popcorn:

---

### Post by njparton on 2009-10-30
> **ff8jake said:**
> ...then adding rt2870sta to /etc/modules.

Cheers!:popcorn:

Aha! I didn't think of trying that...

---

### Post by njparton on 2009-10-30
Well that didn't work unfortunately. I'm contributing to the related bug over at:

[https://bugs.launchpad.net/bugs/460323](https://bugs.launchpad.net/bugs/460323)

Any other ideas appreciated!

---

### Post by ff8jake on 2009-10-30
Hmm, while it is working again it seems to be doing so very flaky compared to how it was running in 9.04. I've noticed initial requests (i.e., going to ebay.com for the first time) are delayed by about 4 seconds - but all requests after the fact seem to work full speed.

Any ideas if this may be related to using the rt2870sta module? :popcorn:

---

### Post by adenewton on 2009-10-30
I have the 2860 driver and I'm having issues with disconnections when downloading torrents. I was hoping this would be resolved in 9.10 but it's not. I have used network-manager and wicd and get the same issue.

I've downloaded the latest driver from ralink, to see if this is the issue but get the following error message when typing sudo make at the terminal. Can anyone help me out with what I have done wrong?

I am on 9.10 and have the 64bit version.

make -C tools
make[1]: Entering directory `/home/ade/RT2860/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/ade/RT2860/tools'
/home/ade/RT2860/tools/bin2h
cp -f os/linux/Makefile.6 /home/ade/RT2860/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/ade/RT2860/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/ade/RT2860/os/linux/../../common/crypt_md5.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/crypt_aes.o
/home/ade/RT2860/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/home/ade/RT2860/os/linux/../../common/crypt_aes.c:1450: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/ade/RT2860/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/home/ade/RT2860/os/linux/../../common/crypt_aes.c:1539: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
  CC [M]  /home/ade/RT2860/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/mlme.o
/home/ade/RT2860/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/ade/RT2860/os/linux/../../common/mlme.c:810: warning: cast from pointer to integer of different size
/home/ade/RT2860/os/linux/../../common/mlme.c:810: warning: cast from pointer to integer of different size
/home/ade/RT2860/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/ade/RT2860/os/linux/../../common/mlme.c:4562: warning: the frame size of 1584 bytes is larger than 1024 bytes
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_wep.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/action.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_data.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/rtmp_init.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_aes.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_sync.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/eeprom.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_info.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/dfs.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/spectrum.o
/home/ade/RT2860/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/ade/RT2860/os/linux/../../common/spectrum.c:1910: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/ade/RT2860/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/rt_channel.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_profile.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_asic.o
/home/ade/RT2860/os/linux/../../common/cmm_asic.c: In function ‘AsicBBPAdjust’:
/home/ade/RT2860/os/linux/../../common/cmm_asic.c:701: warning: the frame size of 1872 bytes is larger than 1024 bytes
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/ade/RT2860/os/linux/../../sta/assoc.o
  CC [M]  /home/ade/RT2860/os/linux/../../sta/auth.o
  CC [M]  /home/ade/RT2860/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/ade/RT2860/os/linux/../../sta/sync.o
/home/ade/RT2860/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/ade/RT2860/os/linux/../../sta/sync.c:1503: warning: the frame size of 1424 bytes is larger than 1024 bytes
/home/ade/RT2860/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/ade/RT2860/os/linux/../../sta/sync.c:679: warning: the frame size of 1344 bytes is larger than 1024 bytes
/home/ade/RT2860/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/ade/RT2860/os/linux/../../sta/sync.c:958: warning: the frame size of 1392 bytes is larger than 1024 bytes
/home/ade/RT2860/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/ade/RT2860/os/linux/../../sta/sync.c:548: warning: the frame size of 1088 bytes is larger than 1024 bytes
  CC [M]  /home/ade/RT2860/os/linux/../../sta/sanity.o
  CC [M]  /home/ade/RT2860/os/linux/../../sta/rtmp_data.o
/home/ade/RT2860/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxMgmtFrame’:
/home/ade/RT2860/os/linux/../../sta/rtmp_data.c:689: warning: unused variable ‘pRxD’
  CC [M]  /home/ade/RT2860/os/linux/../../sta/connect.o
/home/ade/RT2860/os/linux/../../sta/connect.c: In function ‘InitChannelRelatedValue’:
/home/ade/RT2860/os/linux/../../sta/connect.c:2840: warning: the frame size of 1056 bytes is larger than 1024 bytes
/home/ade/RT2860/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/ade/RT2860/os/linux/../../sta/connect.c:310: warning: the frame size of 1632 bytes is larger than 1024 bytes
  CC [M]  /home/ade/RT2860/os/linux/../../sta/wpa.o
  CC [M]  /home/ade/RT2860/os/linux/../../os/linux/rt_linux.o
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:547: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:549: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:651: warning: assignment makes integer from pointer without a cast
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:673: warning: assignment makes integer from pointer without a cast
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:693: warning: assignment makes integer from pointer without a cast
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:935: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:1689: error: ‘struct net_device’ has no member named ‘open’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:1690: error: ‘struct net_device’ has no member named ‘stop’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:1691: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:1692: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:1702: error: ‘struct net_device’ has no member named ‘get_stats’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:1736: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/ade/RT2860/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/ade/RT2860/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2

---

### Post by WiseGuy1020 on 2009-11-01
Here is what I did to get the rt2870 (Dlink DWA-160) working in Karmic at 270mb/s. This worked on a Dell Inspiron 1520, a HP Pavillion dv9000, and an Acer Revo 3600.





1. First a clean install of ubuntu 9.10 final. DO NOT CONNECT YOUR rt2870 USB wireless while you install or after.

2. After install "sudo gedit /etc/modprobe.d/blacklist.conf" Then add "blacklist rt2800usb" to the bottom. Save it.

3. Reboot. Plug in your rt2870 usb and connect to your access point. I was using WPA2 on a mixed g/n network and it connected fine. But it will only connect at 54 mb/s.

4. Install "build-essential" make sure you "sudo apt-get update" first.

5. Download the rt2870 driver from Ralink's website. Sometimes the site is down. Be patient and try again later.

6. Extract the bz2 file. Open the resulting folder. Open the folder labeled "os", then the one labeled "linux."

7.Open the "config.mk" file with gedit. 
Change ```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
``` to ```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

8.Save it.

9. In a terminal cd into the original extracted folder "cd /home/yourname/2009_0820_RT2870_Linux_STA_V2.2.0.0" or where ever you extracted it.

10. Run "sudo make" You will get some errors and it will end in an error. Don't worry about it.

11. Run "sudo make install" This will also give you some errors and it will exit real quick. Don't worry.

12. Reboot. Believe it or not everything should work. Thats what worked for me. No other steps in between.

```
dman@dman-desktop:~$ iwconfig ra0
ra0       RT2870 Wireless  ESSID:"JDubs"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point:   
00:24:01:XX:XX:XX   
          Bit Rate=270 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-47 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Hope it helps someone.

---

### Post by simon82 on 2009-11-01
> **WiseGuy1020 said:**
> Here is what I did to get the rt2870 (Dlink DWA-160) working in Karmic at 270mb/s. This worked on a Dell Inspiron 1520, a HP Pavillion dv9000, and an Acer Revo 3600.





1. First a clean install of ubuntu 9.10 final. DO NOT CONNECT YOUR rt2870 USB wireless while you install or after.

2. After install "sudo gedit /etc/modprobe.d/blacklist.conf" Then add "blacklist rt2800usb" to the bottom. Save it.

3. Reboot. Plug in your rt2870 usb and connect to your access point. I was using WPA2 on a mixed g/n network and it connected fine. But it will only connect at 54 mb/s.

4. Install "build-essentials" make sure you "sudo apt-get update" first.

5. Download the rt2870 driver from Ralink's website. Sometimes the site is down. Be patient and try again later.

6. Extract the bz2 file. Open the resulting folder. Open the folder labeled "os", then the one labeled "linux."

7.Open the "config.mk" file with gedit. 
Change ```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
``` to ```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

8.Save it.

9. In a terminal cd into the original extracted folder "cd /home/yourname/2009_0820_RT2870_Linux_STA_V2.2.0.0" or where ever you extracted it.

10. Run "sudo make" You will get some errors and it will end in an error. Don't worry about it.

11. Run "sudo make install" This will also give you some errors and it will exit real quick. Don't worry.

12. Reboot. Believe it or not everything should work. Thats what worked for me. No other steps in between.

```
dman@dman-desktop:~$ iwconfig ra0
ra0       RT2870 Wireless  ESSID:"JDubs"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point:   
00:24:01:XX:XX:XX   
          Bit Rate=270 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-47 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Hope it helps someone.


Works like a charm on my 2 D-LINK DWA-140 cards aswell. Thx alot!

---

### Post by ff8jake on 2009-11-01
Hmm, using the above steps did increase my connection speed from 54mbps to 130mbps (max supported by DWA-140 to my knowledge) - but I am still having horrendous lag times on initial connections. For instance:

```
ff8jake@machine:~$ telnet ubuntuforums.org 80


*** INSERT 10 SECOND LAG HERE ***


Trying 91.189.94.12...
Connected to ubuntuforums.org.
Escape character is '^]'.
^]

telnet> quit
Connection closed.
ff8jake@machine:~$
```Anyone have any ideas if this is related to this driver issue or not? Anyone know any steps I could take to diagnose what is happening? Once the connection is established or has been recently established (i.e. coming here. I go to ubuntuforums.org, lag for 10 seconds or so) I can jump page to page no problems.

EDIT: Would like to add, this does not appear to affect local connections. Doing a telnet test to localhost:22 works just fine, so this appears to only affect things travelling out the wireless adapter.

---

### Post by ff8jake on 2009-11-01
Finally have all of this working correctly. Using WiseGuy1020's steps above, I am now connected at 130mbps. The lag issue I was experiencing was NOT caused by this driver issue, but apparently due to Ubuntu using my router as a DNS provider as well as automatically picking up Comcast as a search provider. After removing these and specifying OpenDNS in my resolv.conf, everything began working correctly immediately.

Cheers :popcorn:

---

### Post by gigurra on 2009-11-01
I'm trying to install a Belkin N150 usb adapter with rt2870 chipset,
but when trying to compile the latest drivers I initially had to get a kernel-31
patch for the drivers for them to compile.

Then i compiled and installed them, modprobe worked fine BUT no wireless networks
are detected. I can see the device is on, it detects networks in win7, but in ubuntu 9.10
nope, no networks. if I do iwconfig or ifconfig the device is there, but....

Im a n00b that is lost. Spent many hours on this now but starting to feel it's hopeless.
This is my second wireless adapter i try to get working in ubuntu =/

---

### Post by WiseGuy1020 on 2009-11-02
Jake & Simon: I am really stoked that I could help you guys out.

gigurra: My only advice is that I think you plugged in your USB wireless BEFORE you blacklisted rt2800usb. Are you sure you blacklisted rt2800usb in /etc/modprobe.d/blacklist.conf? I could not compile and install completely when I tried but it still worked. Whenever I had problems I noticed that I had plugged in my Dlink before I blacklisted the other driver.

---

### Post by nick77 on 2009-11-02
I just reinstalled Ubuntu 9.10, blacklisted without my Buffalo WLI-UC-300N plugged in following above tutorial very strictly - to no avail. 

My usb stick gets recognized by the built-in usb driver, it even displays the available networks - however, it wouldn't be able to connect.

As the sta module is v1.4, it doesn't include my wifi card's usb keynumber (Bus 001 Device 005: ID 0411:00e8 MelCo., Inc.)

Apparently, WiseGuy's howto helps people with already working cards stuck at 54 Mbit to improve the speed but not non-working cards...

Did anybody find a fix how to be able to compile the driver from the website with the latest kernel 2.6.31-14-generic?

Thanks for your help!

Nick

---

### Post by grantjohnston on 2009-11-02
> **WiseGuy1020 said:**
> Here is what I did to get the rt2870 (Dlink DWA-160) working in Karmic at 270mb/s. This worked on a Dell Inspiron 1520, a HP Pavillion dv9000, and an Acer Revo 3600.





1. First a clean install of ubuntu 9.10 final. DO NOT CONNECT YOUR rt2870 USB wireless while you install or after.

2. After install "sudo gedit /etc/modprobe.d/blacklist.conf" Then add "blacklist rt2800usb" to the bottom. Save it.

3. Reboot. Plug in your rt2870 usb and connect to your access point. I was using WPA2 on a mixed g/n network and it connected fine. But it will only connect at 54 mb/s.

4. Install "build-essentials" make sure you "sudo apt-get update" first.

5. Download the rt2870 driver from Ralink's website. Sometimes the site is down. Be patient and try again later.

6. Extract the bz2 file. Open the resulting folder. Open the folder labeled "os", then the one labeled "linux."

7.Open the "config.mk" file with gedit. 
Change ```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
``` to ```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

8.Save it.

9. In a terminal cd into the original extracted folder "cd /home/yourname/2009_0820_RT2870_Linux_STA_V2.2.0.0" or where ever you extracted it.

10. Run "sudo make" You will get some errors and it will end in an error. Don't worry about it.

11. Run "sudo make install" This will also give you some errors and it will exit real quick. Don't worry.

12. Reboot. Believe it or not everything should work. Thats what worked for me. No other steps in between.

```
dman@dman-desktop:~$ iwconfig ra0
ra0       RT2870 Wireless  ESSID:"JDubs"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point:   
00:24:01:XX:XX:XX   
          Bit Rate=270 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-47 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Hope it helps someone.



You sir kick ***! Works for me too!

---

### Post by TVAbuntu on 2009-11-03
Simply blacklisting the rt2800usb worked perfectly for me! I didn't try to improve speed as my wireless network is only 54Mb. My stick would *not* work prior to blacklisting, so I believe it is a valid workaround for some.

---

### Post by ctsdownloads on 2009-11-05
Nope, nope and more nope. Not only does the make-install give me a 
make: *** [install] Error 2

But merely blacklisting does squat here with the Edimax EW7718un using the rt2870 chipset. Yet, Puppy Linux magically supports it out of the box at full N speeds. What the hell is up with that?  :mad:

---

### Post by WiseGuy1020 on 2009-11-05
ctsdownloads: Did you try it with a fresh install? I get that same error when I run "sudo make." And then "sudo make install" also gives me errors. But after a reboot everything works at full n speeds.

 I noticed that if I tried to plug in the NIC before I blacklisted rt2800usb AND before I rebooted then I could never connect to any networks, at any speed. No matter how I compiled or what flags I modified, after make and install I could see networks but not connect. 

I reinstalled and blacklisted the rt2800usb first, rebooted and then I could connect to networks, but only at 54mb/s. But this is the same situation in Jaunty after a fresh install. In Karmic when I download and install the driver get those same errors as you when I make and install. But If I reboot again it works. 

The 54mbps vs N-speeds out-of-the-box was an issue in Jaunty as well, but there was no need to blacklist rt2800usb. And compiling and installing did not end in errors.

---

### Post by ctsdownloads on 2009-11-05
> **WiseGuy1020 said:**
> ctsdownloads: Did you try it with a fresh install? I get that same error when I run "sudo make." And then "sudo make install" also gives me errors. But after a reboot everything works at full n speeds.

 I noticed that if I tried to plug in the NIC before I blacklisted rt2800usb AND before I rebooted then I could never connect to any networks, at any speed. No matter how I compiled or what flags I modified, after make and install I could see networks but not connect. 

I reinstalled and blacklisted the rt2800usb first, rebooted and then I could connect to networks, but only at 54mb/s. But this is the same situation in Jaunty after a fresh install. In Karmic when I download and install the driver get those same errors as you when I make and install. But If I reboot again it works. 

The 54mbps vs N-speeds out-of-the-box was an issue in Jaunty as well, but there was no need to blacklist rt2800usb. And compiling and installing did not end in errors.

I gave up on all that, settled (unhappily) for using ndis"crapper. I hate this thing as it just ensures that hardware vendors continue kissing Microsoft's butt by putting their drivers first, us dead last.

Blacklisted both rt2870sta and rt2800usb, modprobed ndiswrapper and it gives me 54mbps (which blows). But it's better than using the dongle for target practice. 

For those unfortunate souls who own an Edimax EW7717uN adapter, I have attached the needed inf and sys files for it. Good luck finding them on Google - had to install it on Windows, then fish for it.

---

### Post by honestguvnor on 2009-11-07
In my case I blacklisted both the rt2800usb and rt3070sta which got installed by Ubuntu 9.10. The rt2870sta driver failed to work with WPA but did run at g-speed with security turned off. I am using the default NetworkManager.

As others have reported, downloading the driver, setting the n and WPA parameters and compiling results in compilation errors. I have reported the situation to Ralink.

I can live with the g-speed since I do not need to stream at n-speed for a few weeks but I cannot use the network without WPA.

Are people successfully using the driver with WPA and 9.10 and, if so, how did they achieve this?

Other suggestions for me to try?

---

### Post by Tomatosoup on 2009-11-07
@WiseGuy1020:

Using your method, the bit-rate does says 135 Mb/s now instead of 54 Mbps. But it only copies files over our LAN with 54 Mbps speed, or something... It doesn't really go any faster than 2,8 MBytes/s.

Correction: it DOES work. See post below :)
Thanks.

---

### Post by Tomatosoup on 2009-11-07
Sorry, correction!:

I does work! I can now transfer files up to about 6,2 MB/s! :)
(I was connected via the integrated wireless card and the 300N-XR USB wireless device, and that was a bad 'idea' ;))

Thanks, WiseGuy1020 :)

Though I hope they will update things to make it the full 300 Mbit/s...
Because it's a pity not being able to get full speed.

Though this helps :)

Edit:
Only I couldn't install build-essentials. Ubuntu and I couldn't find it ;)
But that didn't seem to be necessary.

---

### Post by colmode on 2009-11-08
I posted a patch for 2009_0820_RT2870_Linux_STA_V2.2.0.0 vs kernel 2.6.31:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323/comments/15](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323/comments/15)

"Here's a patch based on rt3070-2.6.31-compile.patch, which I found by googling. The rt2870 code is almost identical; I fixed up the first hunk for rt_linux.c.

Edimax EW-7718Un now works for me under 2.6.31 (Karmic). Incidentally, another workaround is just to boot an older kernel and compile the unpatched driver."

---

### Post by Tomatosoup on 2009-11-08
> **colmode said:**
> I posted a patch for 2009_0820_RT2870_Linux_STA_V2.2.0.0 vs kernel 2.6.31:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323/comments/15](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323/comments/15)

"Here's a patch based on rt3070-2.6.31-compile.patch, which I found by googling. The rt2870 code is almost identical; I fixed up the first hunk for rt_linux.c.

Edimax EW-7718Un now works for me under 2.6.31 (Karmic). Incidentally, another workaround is just to boot an older kernel and compile the unpatched driver."

Hello colmode. I've followed WiseGuys steps and got 135 Mb/s for my 300N-XR USB.

Would this patch work for the 300N-XR USB?

And how do I apply this patch?

---

### Post by Tomatosoup on 2009-11-08
Hm. Found I should use the *patch* utility. But he asks for which file to patch... What should I do?

---

### Post by Tomatosoup on 2009-11-08
Ah, I found out how to patch it...

Download and extract the rt2870 driver. Go to the extracted folder. Then run: ```
patch -p1 < rt2870-2.6.31.patch
```

Now to compile the module...

---

### Post by Tomatosoup on 2009-11-08
Damn, compiled (and installed) after applying the patch, but it showed no improvement of speed. I've still got 135 Mb/s. No 300 Mb/s.

---

### Post by colmode on 2009-11-08
I don't have an N AP yet so can't test for speed.  Was just trying to get the adapter working again after upgrading to 2.6.31

---

### Post by honestguvnor on 2009-11-08
colmode:
Thanks for the patch but did you link to the right file? The patch I downloaded did not appear to be changing the correct files and the 3rd chunk of changes did not seem to quite match the set of files I had downloaded.

Whatever, after backing up the original module, I modified by hand what I thought the patch intended and it compiled and installed without complaint. WPA now works (unlike the original module) and it is running in n-mode. Too slowly unfortunately for my needs but at least I can now play with some parameters to determine if things can be improved. Thanks again.


Tomatosoup:
Where are you getting the figure of 135 Mbps from? Measuring the rate of data transferred or a rate reported by a program like iwconfig?

---

### Post by Tomatosoup on 2009-11-08
> **honestguvnor said:**
> Tomatosoup:
Where are you getting the figure of 135 Mbps from? Measuring the rate of data transferred or a rate reported by a program like iwconfig?

From 'iwconfig' yes.
But I also measured the speed of transferring files across our LAN. It's about 4 MB/s - 6,2 MB/s. Mostly 4.0-4.4 MB/s. It's better than before: about 2,2 MB/s. But it's still not the speed with which it should function... 

It would be nice if I would be able to transfer 720p Xvid episodes of 42 minutes (~1,2 GB) a bit faster than that.

This is the output that 'iwconfig' gives me:
```
ra0       RT2870 Wireless  ESSID:"<removed by me>"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: <removed by me>   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-54 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by honestguvnor on 2009-11-08
colmode:
I think I fooled myself in my first test although I am not sure how. Possibly by not unloading the original module. I am reasonably confident all I achieved was changing the environment and not the binary linked to the kernel. As best I can determine, the module I built is bad and prevents the computer from booting when the wi-fi dongle is present.

The original module is now working at n-speed, with WPA and using NetworkManager. One change to the environment in my case is the presence of the file in /etc/Wireless/... which is read when the rt2870sta module first loads. Perhaps this was all that was ever needed.


Tomatosoup:
I am not sure what the iwconfig number means but the reported rate is close to twice the actual data rate transferred. In my case it tends to jump between 54 and 81 when transferring and report 270 when it is not.

I copied a 1GB file with WPA and it went at a rate of 4.8 MB/s. My router reported a rate of 39 Mb/s which agrees with this. I would like to double the speed but would not expect a real world rate approaching 300 Mb/s.

---

### Post by Tomatosoup on 2009-11-08
> **honestguvnor said:**
> I would like to double the speed but would not expect a real world rate approaching 300 Mb/s.

No, but I know I can get at least something as 14 MB/s with my wireless device (using Windows Vista). So it should be able to get at least a real 112 Mbit/s. (Yes, it reports to be 135 Mbit/s bitrate, but that seems not to be correct, though it is faster than it was before.)

---

### Post by Tomatosoup on 2009-11-08
> **honestguvnor said:**
> In my case it tends to jump between 54 and 81 when transferring and report 270 when it is not.

...checked iwconfig now while transferring a file. And it also jumps between 54 Mbit/s and 81 Mbit/s here when transferring...

---

### Post by jonathan.bridges on 2009-11-09
I'm on 9.10 and I get the same error that adenewton described earlier. 

> **adenewton said:**
> 

make -C tools
make[1]: Entering directory `/home/ade/RT2860/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/ade/RT2860/tools'
/home/ade/RT2860/tools/bin2h
cp -f os/linux/Makefile.6 /home/ade/RT2860/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/ade/RT2860/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/ade/RT2860/os/linux/../../common/crypt_md5.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/crypt_aes.o
/home/ade/RT2860/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/home/ade/RT2860/os/linux/../../common/crypt_aes.c:1450: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/ade/RT2860/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/home/ade/RT2860/os/linux/../../common/crypt_aes.c:1539: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
  CC [M]  /home/ade/RT2860/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/mlme.o
/home/ade/RT2860/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/ade/RT2860/os/linux/../../common/mlme.c:810: warning: cast from pointer to integer of different size
/home/ade/RT2860/os/linux/../../common/mlme.c:810: warning: cast from pointer to integer of different size
/home/ade/RT2860/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/ade/RT2860/os/linux/../../common/mlme.c:4562: warning: the frame size of 1584 bytes is larger than 1024 bytes
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_wep.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/action.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_data.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/rtmp_init.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_aes.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_sync.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/eeprom.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_info.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/dfs.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/spectrum.o
/home/ade/RT2860/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/ade/RT2860/os/linux/../../common/spectrum.c:1910: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/ade/RT2860/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/rt_channel.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_profile.o
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_asic.o
/home/ade/RT2860/os/linux/../../common/cmm_asic.c: In function ‘AsicBBPAdjust’:
/home/ade/RT2860/os/linux/../../common/cmm_asic.c:701: warning: the frame size of 1872 bytes is larger than 1024 bytes
  CC [M]  /home/ade/RT2860/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/ade/RT2860/os/linux/../../sta/assoc.o
  CC [M]  /home/ade/RT2860/os/linux/../../sta/auth.o
  CC [M]  /home/ade/RT2860/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/ade/RT2860/os/linux/../../sta/sync.o
/home/ade/RT2860/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/ade/RT2860/os/linux/../../sta/sync.c:1503: warning: the frame size of 1424 bytes is larger than 1024 bytes
/home/ade/RT2860/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/ade/RT2860/os/linux/../../sta/sync.c:679: warning: the frame size of 1344 bytes is larger than 1024 bytes
/home/ade/RT2860/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/ade/RT2860/os/linux/../../sta/sync.c:958: warning: the frame size of 1392 bytes is larger than 1024 bytes
/home/ade/RT2860/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/ade/RT2860/os/linux/../../sta/sync.c:548: warning: the frame size of 1088 bytes is larger than 1024 bytes
  CC [M]  /home/ade/RT2860/os/linux/../../sta/sanity.o
  CC [M]  /home/ade/RT2860/os/linux/../../sta/rtmp_data.o
/home/ade/RT2860/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxMgmtFrame’:
/home/ade/RT2860/os/linux/../../sta/rtmp_data.c:689: warning: unused variable ‘pRxD’
  CC [M]  /home/ade/RT2860/os/linux/../../sta/connect.o
/home/ade/RT2860/os/linux/../../sta/connect.c: In function ‘InitChannelRelatedValue’:
/home/ade/RT2860/os/linux/../../sta/connect.c:2840: warning: the frame size of 1056 bytes is larger than 1024 bytes
/home/ade/RT2860/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/ade/RT2860/os/linux/../../sta/connect.c:310: warning: the frame size of 1632 bytes is larger than 1024 bytes
  CC [M]  /home/ade/RT2860/os/linux/../../sta/wpa.o
  CC [M]  /home/ade/RT2860/os/linux/../../os/linux/rt_linux.o
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:547: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:549: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:651: warning: assignment makes integer from pointer without a cast
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:673: warning: assignment makes integer from pointer without a cast
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:693: warning: assignment makes integer from pointer without a cast
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:935: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:1689: error: ‘struct net_device’ has no member named ‘open’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:1690: error: ‘struct net_device’ has no member named ‘stop’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:1691: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:1692: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:1702: error: ‘struct net_device’ has no member named ‘get_stats’
/home/ade/RT2860/os/linux/../../os/linux/rt_linux.c:1736: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/ade/RT2860/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/ade/RT2860/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2

Can anyone help?

---

### Post by Tomatosoup on 2009-11-10
Don't know what the above means.


Here it's not working anymore... Don't know if it was the patch I applied. I tried to compile/install the original again, but something is still changed...

So now I'm using the integrated one... This sucks.

Now it's barely going at 1 MB/sec...(network file transfers)

And the connection is not even displayed in iwconfig. Not correct at least...

Real bugged!

Edit:
Turns out there was too much distance or something? But my brother's laptop did have a connection...
Not strong enough USB wireless module?

---

### Post by honestguvnor on 2009-11-10
> Can anyone help?

Assuming you want the rt2870 and not the rt2860 then I would suggest blacklisting all the conflicting modules, installing the file that dmesg complains about (possibly after using a failed compilation to write it) and rebooting the machine.

> Here it's not working anymore... Don't know if it was the patch I applied. I tried to 
> compile/install the original again, but something is still changed...

The patch does not make much sense to me. Assuming you actually built a module (many of the previous "installations" did not)  it will get installed in a different part of /lib/modules to where Ubuntu stored the original. So you will now have two modules with the same name and I am not sure what will happen. I doubt the patched one works but you should remove one of them and rerun depmod. You do not have to delete it, just change its name so that it does not look like a module.

You do understand that the module will part of the Linux kernel when loaded and if something is a bit wrong it could completely break your system. For example, when I modified the patch so that it made some sort of sense it produced a broken module which, when it was loaded during boot, caused the kernel to see a broken file system and prompt me to ask if I wanted to fix it. Since the file system was not broken had I said yes it would very likely have actually broken the file system possibly losing everything. 

> So now I'm using the integrated one... This sucks.

Integrated what? Module? Wi-fi chip?

---

### Post by zwucko on 2009-11-12
hi everyone...

this is very disgusting...

i´ve done a fresh and clean install of ubuntu 9.10 x86 (no errors, checksum OK...)

now i want to compile it.

i´ve done the editing and made #make

it starts to compile and suddenly it throws ""has no member named" fsgid" errors

make[2]: *** [.../os/linux/../../os/linux/rt_profile.o] Error2
make[2]: *** [.../os/linux/../../os/linux] Error 2
make[1]: Leaving directory 'usr/src/linux-2.6.31-r14-generic'
make: *** [LINUX] Error2
root@zwucktop#

the problem exists on 2008_0925_RT2870_STA_v1.4.0.0
and on
2009_0820_RT2870_STA_v2.2.0.0

allways the same...

may it depends on that that i unpacked it via archivemanager and did all from sudo -s??

sorry for being so short with the errormessage but i have to type it in by hand....

PS reinstall had to be done cause of migration from 7.04 -7.10-8.04-8.10-9.04 and finally to 9.10 broke my system :D

---

### Post by onedemian on 2009-11-12
Having the same problem.

**My system:** ubuntu 9.10, kernel 2.6.31
**My device:** encore enuwi-n3 

[B]My initial condition:
[/B]I was getting my devices listed as wlan0, but it was unable to find networks.

[B]What I did first:
[/B]
1. Blacklisted both rt2780sta and rt2800usb
-> NO Wireless at ALL

[B]What I did later:
[/B]
1. Tried to compile new rt2870 driver
-> Compiler errors

[B]And then:
[/B]
1. Blacklisted rt2800usb driver
2. Load rt2780sta
-> NO Wireless at ALL

[B]And finally:
[/B]
1. Blacklisted rt2800usb driver
3. Compile rt2870 with patch applied (success)
2. Load rt2780sta
-> NO Wireless at ALL

Now there is only a chance to try: reinstall the WHOLE system as indicated by WiseGuy1020.. 

But is this really necessary??? I am thinking in buying several meters of UTP cable instead...

Please help.

---

### Post by zwucko on 2009-11-12
Well i've Done a new install. Are there any Problems with ext4???
I had it Running on an older kernel and done a Backup. 

I can use the old one but wont have full audiosupport

---

### Post by Tomatosoup on 2009-11-13
With me (I use rt2870sta, the compiled version from the Ralink website), it turns out I was having a distance between router and USB wireless device problem. So that affected the speed...

When I'm in the same room as my router, I just now got 6,9 MB/s during file transfer, which is okay. Maybe it could be more, it could depend on the file I was transferring ;)

My iwconfig then jumps between 108 Mbit/s and 121,5 Mbit/s. If it's not transferring it goes back to 135 Mbit/s.

I have a 100% reach in this room.

Maybe I'll test later with some more files...

Anyway, the speed is acceptable... :)

---

### Post by rkwong on 2009-11-14
If you compile your own, you need to downgrade the kernel to 2.6.30. The 2.6.31 kernel is not compatible with the code from the ralink website. Ubuntu 9.10 does come with a working rt2870sta module (version 1.4). I assume it was patched to work with the 2.6.31 kernel.

To install a 2.6.30 kernel compatible with ubuntu 9.10, go to the ppa mainline kernel site and download the latest 2.6.30 kernel. You need to download both linux-headers files as well as the linux-image file. You need to install the linux-headers in the right order as per the website installation instructions. After proper installation of the 2.6.30 kernel and headers, you should be able to compile the rt2870sta module.

Good luck!

> **zwucko said:**
> hi everyone...

this is very disgusting...

i´ve done a fresh and clean install of ubuntu 9.10 x86 (no errors, checksum OK...)

now i want to compile it.

i´ve done the editing and made #make

it starts to compile and suddenly it throws ""has no member named" fsgid" errors

make[2]: *** [.../os/linux/../../os/linux/rt_profile.o] Error2
make[2]: *** [.../os/linux/../../os/linux] Error 2
make[1]: Leaving directory 'usr/src/linux-2.6.31-r14-generic'
make: *** [LINUX] Error2
root@zwucktop#

the problem exists on 2008_0925_RT2870_STA_v1.4.0.0
and on
2009_0820_RT2870_STA_v2.2.0.0

allways the same...

may it depends on that that i unpacked it via archivemanager and did all from sudo -s??

sorry for being so short with the errormessage but i have to type it in by hand....

PS reinstall had to be done cause of migration from 7.04 -7.10-8.04-8.10-9.04 and finally to 9.10 broke my system :D

---

### Post by jastonas on 2009-11-14
> **Tomatosoup said:**
> With me (I use rt2870sta, the compiled version from the Ralink website), it turns out I was having a distance between router and USB wireless device problem. So that affected the speed...


When you say compiled, you mean deb files? I have only found drivers that need to be compiled on the site, who dont work for me.

---

### Post by gearond on 2009-11-15
I had it all working with the previous version to 9.1. Then I made the mistake of accepting the upgrade. Postgres and wireless disappeared.

I downgraded to 8.04, then back up to 8.1, but didn't fix it. So searched and fianally found chipset id/ chipnumber, got here. Anyone give me directions on how to get it working again?

RALink doesn't seem to have the download anymore. And all of you seem to have troubles getting it to work in the compile version. I don't remember having to compile anything to get it to work before. Must have downloaded a kernel module or something.

Ubuntu 9.1 is a dream, FAST, nice looking, GREAT features out of the box, but I can't use it, nor even my old system now. :-(

---

### Post by calvinwels on 2009-11-15
I've gone back to using an old D-Link g adaptor since my Buffalo WLI-UC-G300N isn't functioning with the new kernel in Ubuntu 9.10.  From what I've gleaned from previous posts is that the Ralink 2870 "may" work if you do a clean install of 9.10 without the adaptor, blacklist the junky rt2800usb driver and then restart with with RT2870 drivers.  I haven't done another clean install to find out if this works because for now I'm resigned to limping along using the g adaptor.  But I will be very happy if Ralink or Linux developers get this driver to work with the new kernel.

---

### Post by rkwong on 2009-11-17
There is patch of the rt2870sta code for the 2.6.31-14-generic kernel which will allow you to compile the rt2870sta.ko module for the 2.6.31-14-generic kernel. I have tried it and it works, although I have not done a lot of testing. You can find the instructions at
[http://forum.notebookreview.com/showthread.php?p=5509307](http://forum.notebookreview.com/showthread.php?p=5509307).

Good luck!

> **rkwong said:**
> If you compile your own, you need to downgrade the kernel to 2.6.30. The 2.6.31 kernel is not compatible with the code from the ralink website. Ubuntu 9.10 does come with a working rt2870sta module (version 1.4). I assume it was patched to work with the 2.6.31 kernel.

To install a 2.6.30 kernel compatible with ubuntu 9.10, go to the ppa mainline kernel site and download the latest 2.6.30 kernel. You need to download both linux-headers files as well as the linux-image file. You need to install the linux-headers in the right order as per the website installation instructions. After proper installation of the 2.6.30 kernel and headers, you should be able to compile the rt287http://forum.notebookreview.com/showthread.php?p=55093070sta module.

Good luck!

---

### Post by paulsmith99 on 2009-11-17
Works as described for D-link DWA140 on Kubuntu 9.10.

uname -a shows:
Linux ******-pc 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

iwconfig shows:
ra0       RT2870 Wireless  ESSID:"********** Network"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:##:##:##:##:06
          Bit Rate=270 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-25 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I got error[2] on make and make install but stuck with the instructions. Rebooted and it was working. :D

Got a feeling though that as soon as a newer kernel is available on an update, I'll have to compile again - won't I?

UPDATE - it was working, for a short time, somehow. No I get it connecting for a short time and disconnecting. Last resort was to try in Windows and it works perfectly :-(

---

### Post by freek_zero on 2009-11-26
Anyone else having a helluva time getting this to work? It's always worked fine with ralink's drivers for me under 2.6.28-16 came out, at which point it would associate with the network fine, but wouldn't get an IP. Same behaviour with 2.6.31-15. No DHCP offers received. Changing to static IP doesn't help (ifconfig lists the IP but no connection is created). Tried rt2800usb and rt2870sta (v2.2, patched for 2.6.31 and with the config.mk WPA tweaks). Tried setting up via wpa-* directives in /etc/network/interfaces, tried using the iwpriv approach in /etc/rc.local, and tried with networkmanager. Nada on all counts (using WPA). An open connection worked fine. Followed every suggestion I could find in these forums to no avail. What the hell am I missing? I can't waste another 10 hours on this.

---

### Post by freek_zero on 2009-11-26
Another half day later, only way this thing will work with anything other than an open connection is with rt2870sta v1.4, which came with 9.10. It works, even providing WPA2, but no access to 5GHz band and doesn't seem to provide N mode for me (tho it does for others it seems, so it's probably just a setting I've buggered somewhere).

Here's hoping RaLink gets their 2.2 driver working with 9.10 real soon (and gets it working with WPA 2, as I could never get it to support anything past WPA(1)) or rt2x00 hits maturity, supporting 5GHz and encryption thru WPA2. I understand a rep from RaLink is on the rt2x00 project now, so there's some hope.

You know, I would MUCH rather have paid for Ubuntu like I would for Windows than lose a whole day's work (which costs me a fair bit more than the cost of windows... every time this happens). (not meant as a slight to those who work on Ubunutu and drivers for free... but most component manufacturers REALLY need to step up their driver support for linux in a big way).

---

### Post by Rounin on 2009-12-03
A solution for WUSB600Nv2 that works for at least some users was posted by a Daan Kets at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165) . It consists of the following steps:

1. Install the utility "Windows Wireless Drivers" (I believe this is the same as "ndisgtk)

2. Download and extract the Windows XP driver from the Linksys site (WUSB600Nv2_XP_1.4.4.0.zip)

3. Unplug the device. (I'm not sure if I did this, but this is what he did, at any rate.)

4. In the Windows Wireless Drivers utility, install the driver by opening the .inf file in the WinXP64 folder. (32-bit users should presumably try the 32-bit driver, but we're both on 64-bit.) Keep the dialogue open and insert the device.

He also warns against removing the stick while the system is running.

---

### Post by apprentice007 on 2009-12-04
followed this tutorial, but still stuck, i get the driver loaded but when i try to load ra0 up there is nothing there, i have a few pix attached any help would be great, i have blacklisted rt2800, rt2800usb etc cant seen to get it to work

---

### Post by lab1301@gmail.com on 2009-12-05
Ubuntu 9.10 *Karmic Kola *(32bit) on ASRock ION 330
Edimax EW-7711UTn Wireless nLite USB adaptor (RT2870)


I've deleted the contents here as I've started a new thread for this issue as *"Errors compiling drivers for ralink RT2870 (no member named &#8216;fsuid&#8217;)*"

Regards

Lakshman

---

### Post by Tyx on 2009-12-05
> **Rounin said:**
> A solution for WUSB600Nv2 that works for at least some users was posted by a Daan Kets at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165) . It consists of the following steps:

1. Install the utility "Windows Wireless Drivers" (I believe this is the same as "ndisgtk)

2. Download and extract the Windows XP driver from the Linksys site (WUSB600Nv2_XP_1.4.4.0.zip)

3. Unplug the device. (I'm not sure if I did this, but this is what he did, at any rate.)

4. In the Windows Wireless Drivers utility, install the driver by opening the .inf file in the WinXP64 folder. (32-bit users should presumably try the 32-bit driver, but we're both on 64-bit.) Keep the dialogue open and insert the device.

He also warns against removing the stick while the system is running.


FINALLY. THANK YOU SOOOOO MUCH for this! I have been trying for endless hours to get this stick working with my newly installed Karmic Koala 64-bit. 
Now my WUSB600N v2 stick is working on both my Windows 7 x64 and Ubuntu x64. 
Thanks again. *sigh of relief*.

---

### Post by deadite66 on 2009-12-06
i tried ndiswrapper it worked but was limited to 802.11g speeds (54Mbps) not the 270Mbps i get in windows.

---

### Post by moloth on 2009-12-08
Works for my Netcomm Power N Mini. I was getting 65mb/s then changed my router to do Auto 20mhz/40mhz wideband and can now get 135mb/s. Anyone know how to get 300mb/s?

You can download the RT2870USB(RT2870/RT2770) 2.3.0.0 source from: [http://www.ralinktech.com/support.php?s=2]("http://www.ralinktech.com/support.php?s=2")

> **etdwh said:**
> Well, that is very useful information. Took me days trying to figure out why the drivers worked in 8.10 but not 9.04. Now it works correctly :D

Anyway, i have a Belkin N+ USB adapter (F5D8055v1).
Steps to get it working for me:

1) Download drivers from Ralink ([http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)). Right now, its 2009_0521_RT2870_Linux_STA_V2.1.2.0.tgz

2) Extract drivers. I extracted to /usr/src.

3) Delete existing rt2870sta driver. Refer to quote above for exact location

4) Edit os/linux/config.mk. Change values of 
HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

5) Edit os/linux/usb_main_dev.c

6) Look for line: {USB_DEVICE(0x050d,0x815c)}, /* Belkin F5D8053 */

7) Add new line below the above: {USB_DEVICE(0x050d,0x825a)}, /* Belkin F5D8055 */

8 ) Save and close file

9) sudo make && sudo make install

10) sudo modprobe rt2870sta
Network manager should now start scanning for wireless networks

To load module at startup...
11) edit /etc/modules. Add new line: rt2870sta

That it :D

---

### Post by eazylip on 2009-12-10
Sorry for the dumb ?, but how do I run the make file?  I'm using 8.10

---

### Post by eazylip on 2009-12-10
RaZoR1394 - your are the business.  I've been trying to figure this out for about a month now and finally got my wireless usb device working with the help of your wiki link.  Thanks to you and the Ubuntu community.  Death to Microsoft and the criminal monopoly!!!!!

---

### Post by AlanRick on 2009-12-12
Rats! ](*,) 
I Just tried to install karmic on my new dell pc and this problem still exists. So I'm back on Windows (7) and hope this will be fixed in the next LTS ubuntu :-(

Only consolation is that at least I now have picasa and thunderbird 3.

---

### Post by oblio on 2009-12-12
The new V2.3.0 source for RT2870sta from ralinktech can be perfectly compiled/checkinstalled using kernel 2.6.32 (from Mepis and Sidux).
One needs to blacklist the rt2800usb module and remove the rt2870sta driver in staging, add rt2870sta to /etc/modules.  Then run make and checkinstall on the untarred source.  Modprobe rt2870sta and you're in business

Reboot .

---

### Post by AlanRick on 2009-12-12
> **oblio said:**
> 0 Modprobe rt2870sta and you're in business

Problem is when there's a security update or something that overwrites this and then:
[LIST]

[*] (best case) you go through the whole procedure again
[*](worst case) the rest of the family are without internet for a few days until you've got time  to go through the whole procedure again 
[/LIST]
Been there once - never again.

---

### Post by oblio on 2009-12-12
> **AlanRick said:**
> Problem is when there's a security update or something that overwrites this and then:
[LIST]

[*] (best case) you go through the whole procedure again
[*](worst case) the rest of the family are without internet for a few days until you've got time  to go through the whole procedure again 
[/LIST]
Been there once - never again.Security update of what? 
With kernel 2.6.31 I was also succesful getting the DWA-140 to work well by using a 2.6.31-kernel-specific patch to the v.2.2.0 Ralinktech source code. That was with a liquorix kernel.

Did you actually try the (very recently (dec.4) released) RT2870sta v.2.3.0 source code from Ralinktech? 
It does support the 2.6.31 kernel; Karmic uses a 2.6.31 kernel and Lucid uses a 2.6.32 kernel, so I'm pretty sure that it would work. 
It tried it with the 2.6.32-0mepis5 kernel and it works fine.

* best case : it works well. It does here: my DWA-140 wireless speed is nearly as good as my wired speed: 55-60 Mbps.
* worst case: you loose wireless, so you connect an utp cable for a while, until you succeed. 

By the way: The rt2870sta v.2.1.2 source from Ralinktech can be compiled/checkinstalled successfully in Hardy (which you seem to be using).

Ko

---

### Post by nilsa5 on 2009-12-22
Thanks for all good response, have never thought that my guide would got so many replies, I don't know if the driver supports the Server Editon I tried to install on the first time. And remember to send me emails if you got problems and I will try to find a solution.

Best regards
Nils Andreas Svee

---

### Post by chronos1 on 2009-12-24
done what oblio explained in his post. so far so well but no effect my Linksys WUSB600N is not responding in any way. (No lights nothing.)
The module is loaded but the device is not responding :S. Ohh yeahit works well under win xp / vista and 7. Someone have any ideas ?
They are really appricieated.

---

### Post by Hanto on 2009-12-25
[SIZE=4]Apologies

[/SIZE]

---

### Post by internaut19 on 2010-01-01
I managed to get it working even if the install wasn't a fresh one and I fulled around with other ways to get it to work.
Thanks,
Cristian.

---

### Post by azagaros on 2010-01-02
I don't know where to begin with this mess.

I have this linksys card that is mentioned here and looking for the Linux driver mentioned here, In any form.  It appears that all links are dead, except the header file.

The situation that I have is in Ubuntu 9.1, the device is seen recognized and given wlan spot.  The device is however asleep,  Power management mode.  Orininally I had this this device not managed, which it wasn't managed in the power management schema.  I figure if I can get the device awake I am some where closer to where I was than before.

It doesn't matter to me if the light blinks as long as it can perform the tasks to getting to connectivity, which is waking the device up and using it.

Any help would be useful, while I still look for the info.

---

### Post by wah fun on 2010-01-09
internaut19,

Could you post how you got yours to work? I have a similar problem with a Belkin N150 wireless usb adapter and your solution might help.

thx

---

### Post by bbriand on 2010-02-09
Hi,
 
I was experiencing the problem of being able to compile and blacklisting the other modules with no success. ra0 would not show up under iwconfig.
 
I downloaded the latest driver release for my Buffalo Wireless N USB adapter; "0411:015d"
 
I am using Karmic 9.10 with the latest updates (2.6.31-19-generic).
 
If I executed dmesg and greped for rt2870 I got something similar to:
"module is from the staging directory, the quality is unknown, you have been warned."
 
After many recompiles and much googling I found the answer for me on another Ubuntu site.
 
Hopefully this helps someone:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1285828](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1285828)
 
Look at the section titled:
"**Update 2**: If when you are trying to load the module you receive the following (on Karmic):"
 
Of course instead of using rt3070sta I changed that to rt2870sta
 
after this my usb adapter was immediately displayed in the list.
 
I hope hotlinking that site is ok. If not please notify me and I will change it.
 
Hope this helps someone.
 
Cheers,
Bill

---

### Post by Rothstei on 2010-02-20
After a lot of figuring, I've gotten the driver compiled with the correct settings, installed, and even  done modprobe, and modinfo on rt2870sta, so I know it is there, and installed.

My next guess is that I need to add the USB ID to /etc/os/linux/usb_main_dev.c, as several have suggested.

I'm trying to use a Buffalo Nfiniti WLI-UC-GN, and by using lsusb I've found the code as 0411:015d.

But for the life of me, I cannot find where to add this into usb_main_dev.c! 

Another forum suggested adding it into /include/rt2870sta.h, but I'm not finding that file at all.

I'm using 9.10, and version 3.0.0 of the driver. I have a feeling that there is a new place to add this in 3.0.0, but after aimlessly wandering the halls for an hour, I can't seem to see anything listing anything like "USB_DEVICE" and USB IDs. 

Is there a new place to find this, or alternatively, a place to download a previous version of the driver?

Everything else seems in place, but ifconfig gives me no ra0. 

Oh this too: after unloading and loading the drivers again, and trying 

/etc/init.d/networking restart

I got:

Reconfiguring networking interfaces...
[DHCP Client version info... etc]

SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device
Bind socket to interface: no such device
Failed to bring up ra0.


Other than my suspicions about the USB ID, that's the only clue I have.

I can almost taste the Wifi! Any help would be awesome, as this thread has almost gotten me all the way home.

(the other thread I was looking at, btw, is [http://www.apfelkraut.org/2009/02/howto-wlan-ralink-rt2870-usb-stick-kubuntu-810/](http://www.apfelkraut.org/2009/02/howto-wlan-ralink-rt2870-usb-stick-kubuntu-810/) )

Thanks

Edit: Also, I forgot to mention I did do the blacklist of theRT2800USB driver, and it seemed to work, though I'm not sure how to verify this, other than that I got no errors when I did so.

---

### Post by tvrtuscan on 2010-02-21
In version 3 of the ralink drivers the device id's are listed in the common/rtusb_dev_id.c file.

I've got a Belkin 8055v2 and I've managed to get ra0 displayed in ifconfig and iwconfig by changing the above file.  Unfortunately I've still not managed to connect to my router.  I have previously managed to get a scan showing the devices but for the life of me I can't get this working now.

Has anyone managed to get the 8055v2 working?  I've installed wicd as I believe this was installed when I had the scan working.

Currently iwlist scan just displays 'No scan results' for ra0.  Any suggestions welcome.  I believe the driver is now working but still no connection

---

### Post by GrandTheft on 2010-02-21
Thanks tvrtuscan, 

that worked, successfully compiled the driver and the usb wlan is now recognized. Unfortunately I can not connect to my wireless. Networkmanager does not see any networks and when I connect "to a hidden wireless network" it also does not work.

However, one step closer !

Edit: network-manager keeps askin and askin for the WPA2 password.... dont know why

Thanks guys,
GT

---

### Post by GrandTheft on 2010-02-22
well.
I found out why I cannot configure my WUSB100 (rt2870sta). The README in the driver package says there are three ways to configure the device. None of it is via network-manager. 

There is a configuration file in /etc/Wireless/RT2870STA/ called RT2870STA, which I managed to configure, and I can get the interface up so that it is sending packages. I can not make contact with my router, but still, there seems to be a little light at the end of the tunnel. 

G'night guys,
GT

---

### Post by AFI420 on 2010-02-26
the new kernel supports the rt2870. when you go to network devices, change the driver to 3070 or 2870 and reboot. should work

---

### Post by GrandTheft on 2010-02-26
Hey, 

which one exactly is "the new kernel" ?

And, could you explain how you "go to network devices" !?

Thanks.
GT

---

### Post by GrandTheft on 2010-02-28
Hey guys, 

it works !

Totally different solution:

[http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)

solved it for me. 

Namely 

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

Finally.

Best regards,
GT

PS: No compiling of kernel or from driver source. Just added the dev ID with the above command using 2.6.32-19-generic

---

### Post by nick77 on 2010-04-11
This driver/hardware/distribution combination s*cks.... It's been already about 3 years since I bought the Buffalo USB WLAN N stick instead of a US robotics PCI card, because the chip was said to be 100% natively supported by Linux... Still today, I'm heading over the forum after each upgrade of ubuntu (sometimes even during the use of the same version when the kernel gets upgraded....)

Finally, after about half an year it's working again now. However, it didn't with the solution mentioned one post before, but with the old compiling one.

A short summary of my problems on Ubuntu 10.4 Beta 2
- USB stick gets recognized and module rt2x00 is being fired up.
- Network-Manager shows all the available networks, but cannot connect to my wpa2 enabled network (re-iterates asking for the password over and over again.

A short summary of the way I solved it:
- blacklisting of the rt2x00 module in /etc/modprobe.d/blacklist.conf ```
blacklist rt2800usb
```
- downloading v2.3 from the ralink website [http://www.ralinktech.com/support.php?s=2]("http://www.ralinktech.com/support.php?s=2")
- changed in the config.mk ```

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```
- in the Makefile I changed the install path to fit ubuntu: ```
ifeq ($(PLATFORM),PC)
# Linux 2.6
LINUX_SRC = /lib/modules/$(shell uname -r)/build
# Linux 2.4 Change to your local setting
#LINUX_SRC = /usr/src/linux-2.4
LINUX_SRC_MODULE = /lib/modules/$(shell uname -r)/kernel/drivers/staging/rt2870/
CROSS_COMPILE = 
endif

```

compiling with #sudo make and installing with #sudo make install went like a breeze afterwards and finally my usb stick was up&running again:guitar:

However, as stated before, I can't really understand what's so difficult in making this driver work right out of the box for all kinds of usb-sticks being around for already 3 yrs or maybe even more...

Nick

---

### Post by tabays on 2010-04-14
I have a problem. I am trying to get build-esential installed so that I can compile the ralink rt2870 driver, so that I can get my ubuntu machine connected to the internet, through my Linksys WUSB100 card. So far, everyone is pre-supposing that you already have an internet connection, and tell you to use get apt command so that ubuntu will do it automatically. That's the problem! I am not connected with the ubuntu side of my computer. I am connecting with Windows XP, and transporting the files manually so I can install them in ubuntu. I have been installing all of the programs dealing with the dependancy issues. then I hit a brick wall! It is telling me that **g++-4.1_4.1.1-21** needs **libstdc++6-4.1-dev (= 4.1.1-21)** before I can install it. Also, **libstdc++6-4.1-dev (= 4.1.1-21)** is saying it needs **g++-4.1_4.1.1-21** to be installed first, before I can install it! 
 
Is there a way to force one of them to install, so that I can install the other one? I can't install them both at the same time! One of them should be first, but they both need the other one previous to install. It's a catch 22! How can I fix this problem?

---

### Post by chili555 on 2010-04-14
> I can't install them both at the same time!You can't? Doesn't this do it?```
sudo dpkg -i libstdc++6-4.1-dev.foo.deb g++-4.1_4.1.1-21.blah.deb
```You might also try:```
sudo dpkg -i --ignore-depends=g++ libstdc++6-4.1-dev.foo.deb
```Then do the other.

Finally, isn't *build-essential* on the install CD and therefor installable in Synaptic after you enable the CD as a source?

---

### Post by auroral on 2010-05-02
After making the required and highlighted modifications, and when I try to compile by* sudo make*, I run into errors. Any fix? Thanks!

Oh, and I'm running the Lucid Lynx 10.04

make[1]: Entering directory `/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools'
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.32-21-generic/build SUBDIRS=/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.o
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;duplicate_pkt&#8217;:
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:537: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast
/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/string_64.h:58: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:539: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast
/usr/src/linux-headers-2.6.32-21-generic/arch/x86/include/asm/string_64.h:58: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;ClonePacket&#8217;:
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:632: warning: assignment makes integer from pointer without a cast
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;update_os_packet_info&#8217;:
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:654: warning: assignment makes integer from pointer without a cast
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;wlan_802_11_to_802_3_packet&#8217;:
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:674: warning: assignment makes integer from pointer without a cast
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;send_monitor_packets&#8217;:
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:912: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217;
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSIRQRequest&#8217;:
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1068: warning: unused variable &#8216;net_dev&#8217;
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSTaskAttach&#8217;:
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1282: warning: unused variable &#8216;pid_number&#8217;
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevAttach&#8217;:
[B]/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1624: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1625: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1626: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1627: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1633: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1667: error: &#8216;struct net_device&#8217; has no member named &#8216;validate_addr&#8217;
make[2]: *** [/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/user/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [LINUX] Error 2[/B]

---

### Post by chili555 on 2010-05-03
> Any fix?Is the native rt2870sta driver not working? You may need to blacklist a few things, but it ought to work better than a compiled (9-month old) version.

---

### Post by negora on 2010-05-03
I've downloaded the official Ralink drivers, version 3.0.0, and this has been one of the few times (maybe the first one) that the compilation has worked fine without the need of any patch (having installed the package "build-essential" and blacklisted the module "rt2800usb" first, of course).

I got Ubuntu 10.04 64-bit. In case that it's of any help to others, the compiled driver can be downloaded from [here]("http://negora.com/ubuntu/rt2870sta.ko") .

PD: By the way, I've needed to compile the driver because the one which is bundled into Ubuntu 10.04 64-bit is unable to connect to a WPA2 network. It's a step back with regard to Ubuntu 9.10, as it worked flawless just after its installation.

PD2: My network interface is a D-Link DWA-140.

PD3: By the way, one of my mistakes before was not to copy the file RT2870STA.dat to /etc/Wireless/RT2870STA . Thanks to an answer from chili555 in another thread I realized that was the reason behind my head aches ;) .

---

### Post by Eandril on 2010-05-14
Hi, I am completely new to Ubuntu basically, toying with it for two weeks or so. I just bought Edimax EW7711Usn (ralink rt2870) wireless stick and having problems to make it work. 

I read through this thread and tried to follow suggested procedures. The system itself first detected it with built in set of 2800usb drivers, but I  was unable to make it search for networks. So, according to hints and tips here I blacklisted 2800line of mods and proceeded to install drivers. 
Only one which seemed to compile good was RT2870_LinuxSTA_V2.3.0.0.tar.tar.bz2. Even "make install" did not give me any errors. (compared to driver which was directly on cd provided by edimax and which failed to even compile for some reason O.O) 
Though stick itself is not even detected now and small light is not blinking but just permanently lit on. Also, I read that raO device should pop up for me when properly installed when running iwconfig but its not there. With 2800usb drivers it was shown as "wlan1" there. I am open to any suggestions how to make it work and will try to provide needed terminal output:) 

Thanks in advance

Edit: using Lucid 10.04

---

### Post by chili555 on 2010-05-14
How about letting us see:```
lsmod | grep rt2
dmesg | grep rt2
```Thanks.

---

### Post by Eandril on 2010-05-16
oh sorry for the delay, here it is ```
eandy@eandy-laptop:~$ lsmod | grep rt2
rt2870sta             554993  0 
eandy@eandy-laptop:~$ dmesg | grep rt2
[   17.970867] usbcore: registered new interface driver rt2870
eandy@eandy-laptop:
```

---

### Post by Eandril on 2010-05-16
oh consider me solved :) found out that I need to use 3070 driver with this usb stick, after some time I finally made it work

---

### Post by RussianNeuroMancer on 2010-05-17
Easy way to install all rt3070 devices in Ubuntu.
1. Add ppa:logari81/ppa
2. Install rt3070 package.
3. That's all! :)

---

### Post by BoneKracker on 2010-05-17
> **Eandril said:**
> oh consider me solved :) found out that I need to use 3070 driver with this usb stick, after some time I finally made it work

The 2870sta driver and the 3070sta driver are one and the same.

I have a 2870-based USB wireless adapter.  I remember when I first tried to set it up way back, my troubleshooting showed that, even though I had a 2870-based device, it was looking for the file "/etc/Wireless/RT3070STA/RT3070STA.dat".  (I don't recall how I determined that.)

I figured that the kernel developers had hosed something up while hastily merging the 2870sta and 3070sta drivers into one.  
[http://lwn.net/Articles/348354/](http://lwn.net/Articles/348354/)

So I got mine working by creating what it was looking for, but providing a symlink to /etc/Wireless/RT2870/RT2870STA.dat.  My rationale was that they'd probably eventually fix this, so I wanted to have everything properly referred to (as RT2870 not as RT3070), and at that time the symlink would simply become superfluous.

In other "words":```
etc # ls -lR Wireless/
Wireless/:
total 8
drwxr-xr-x 2 root root 4096 May 17 02:54 RT2870STA
drwxr-xr-x 2 root root 4096 Jan 30 14:54 RT3070STA

Wireless/RT2870STA:
total 4
-rw-r--r-- 1 root root 115 Sep  3  2009 RT2870STA.dat

Wireless/RT3070STA:
total 0
lrwxrwxrwx 1 root root 26 Jan 30 14:54 RT3070STA.dat -> ../RT2870STA/RT2870STA.dat
```

---

### Post by BoneKracker on 2010-05-17
rt2870sta was working fine under 2.6.32, but did not work for me (when I first tried it) in kernel 2.6.33.

I haven't read this whole thread, but does it work in 2.6.33 (or 2.6.34)?  Does the driver from the Ralink site work under 2.6.33?

---

### Post by ctdragon on 2010-05-26
There seems to be a lot of confusion about how to get this WUSB600N to work which is why I wanted to post a simpler solution [-here-]("http://stu.westga.edu/~cslappe1/My%20Website/Pages/Contact%20Info/Pages/News%20and%20Interests/index.html#Ubunt: WUSB600N Fix") so that people can just follow the 3 steps and not worry about it anymore.

The only difference between this and the rt3572 driver mod is that I already found the correct driver and modded it for you.

Download it and follow the instructions here:

[http://stu.westga.edu/~cslappe1/My%20Website/Pages/Contact%20Info/Pages/News%20and%20Interests/index.html#Ubunt: WUSB600N Fix]("http://stu.westga.edu/~cslappe1/My%20Website/Pages/Contact%20Info/Pages/News%20and%20Interests/index.html#Ubunt: WUSB600N Fix")

---

### Post by BoneKracker on 2010-05-26
> **ctdragon said:**
> The only difference between this and the rt3572 driver mod is that I already found the correct driver and modded it for you.
Thank you for modding it for me.

I know you can't possibly know what architecture I am running on, so I am left to assume that this will run on any architecture.  Have you tested it on many architectures?

---

### Post by hellion_fi on 2010-06-25
Anybody got the new archive (2.4.0.0, dated today, downloaded from the ralink's site) opened? My archive manager just complains that it is not a bzip2-archive.

UPDATE: Succeeded to unpack the archive by renaming the extension from tar.bz2 to .zip

BoneKracker: I'm running 2.6.34-kernel, and read the whole thread, but at least as of yet no-one has said anything about the driver working or not with post-.32 -kernels. As for the record, I haven't been able to get it to work (yet, at least).

EDIT: Managed to get the wireless working (using the .34 -kernel) - but not with rt2870sta driver. Apparently the driver that ships with my wireless adapter was for the rt2870, but the chip actually used within the adapter is rt3070. Even though there has been some information that the two drivers are essentially one and the same, there still seems to be enough differences so that at least the 2870 driver doesn't quite work for the 3070-chip.

---

### Post by calvinwels on 2010-07-08
I've tried the RA2870 v2.4 release and cannot get it to show up in network manager after several tries.  I've gone back to the 2.3 driver which has been working very well.

---

### Post by eric512 on 2010-07-11
I have the error - with my WUSB600N v1 on 2.6.32 kernel. Using the staging RT2870sta drivers - I get "--> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat" in the message log.

In the modinfo I see 

alias:     rt3070sta
version: 2.0.1.0

Maybe that is why the 2870 looks for the 3070sta.dat.

> **BoneKracker said:**
> The 2870sta driver and the 3070sta driver are one and the same.

I have a 2870-based USB wireless adapter.  I remember when I first tried to set it up way back, my troubleshooting showed that, even though I had a 2870-based device, it was looking for the file "/etc/Wireless/RT3070STA/RT3070STA.dat".  (I don't recall how I determined that.)

I figured that the kernel developers had hosed something up while hastily merging the 2870sta and 3070sta drivers into one.  
[http://lwn.net/Articles/348354/](http://lwn.net/Articles/348354/)

So I got mine working by creating what it was looking for, but providing a symlink to /etc/Wireless/RT2870/RT2870STA.dat.  My rationale was that they'd probably eventually fix this, so I wanted to have everything properly referred to (as RT2870 not as RT3070), and at that time the symlink would simply become superfluous.

In other "words":```
etc # ls -lR Wireless/
Wireless/:
total 8
drwxr-xr-x 2 root root 4096 May 17 02:54 RT2870STA
drwxr-xr-x 2 root root 4096 Jan 30 14:54 RT3070STA

Wireless/RT2870STA:
total 4
-rw-r--r-- 1 root root 115 Sep  3  2009 RT2870STA.dat

Wireless/RT3070STA:
total 0
lrwxrwxrwx 1 root root 26 Jan 30 14:54 RT3070STA.dat -> ../RT2870STA/RT2870STA.dat
```

---

### Post by Drewkman on 2010-07-28
I'm on a newb on a totally fresh install of 10.04, trying to get a D-Link DWA-140 to work. The internet brought me here.

I went through the procedures in the first post of this thread, and all seemed to go well apart from some complaints about clock skew... which I assumed were inconsequential.

And yet lo and behold, nothing changes. Reboot. Nothing. The computer doesn't even list wlan as a network device, despite my modification of the network interfaces text file. Just loopback interface and ethernet interface...

Argh. This is the second time I've had a go at this. The last time was a few months ago with 9.10;  I wasted many hours on the issue with no results whatsoever, before deciding I'd come back when 10.04 was released and I'd have a clean slate.

I don't want to give up on Ubuntu, but at the moment I'm getting urges to run back to my warm, friendly and fully internet capable Macbook and never look back from OS X again. =__=

---

### Post by negora on 2010-07-28
**Drewkman:** I've the same model and it works smoothly after compiling. Don't forget these steps:

[LIST=1]
[*] Blacklisting the "rt2800usb" module at /etc/modprobe.d/blacklist.conf .
[*] Copying the rt2870sta.ko module to /lib/modules/2.6.32-24-generic/kernel/drivers/staging/rt2870 (or equivalent).
[*] Copying the RT2870STA.dat file to /etc/Wireless/RT2870STA .
[/LIST]

---

### Post by rmamrick on 2010-07-28
when I do step 15, insmod /home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux/rt3572sta.ko
 I get a response file is busy.  When I go to open the file it has a lock on it.  How do I resolve this?
 

 When I do steps 17 and 18, I can see that auto ra0 is the 1st line, iface ra0 inet dhcp is the second line in etc/network/interfaces, but when I run iwconfig, I do not see ra0 or iface ra0.  I have no wireless extensions.   
 

 My build-essential is the most up to date.  Are steps 21 to 24 necessary/essential?

---

### Post by rmamrick on 2010-07-28
above I am referring to instructions:

14. Visit the os / linux (cd os/linux)
15. Run insmod rt2870sta.ko
16. When will all work after my experience, if not follow the next step.
17. Open /etc/network/interfaces (gedit /etc/network/interfaces).
18. Please enter the first sentence
auto ra0
, Also the other

iface ra0 inet dhcp
(dhcp is standard, you need only change to what suits you love.
19. Then all the work, use encryption, you can configure it with the  System> Administration> Network, or network-admin in the terminal.
20. Almost forgot that you must install build-essential (apt-get install build-essential).
21. build-essential to be on CD you installed ubuntu with.
22. How to install build-essential CD.
23. Open the Terminal (Applications> Accessories> Terminal)
24. Run apt-cdrom add-d / cdrom (replace / cdrom with the path cdrom is mounted with you)
25. Run apt-get update.
26. And run apt-get install build-essential.

---

### Post by negora on 2010-07-29
**rmamrick:** When installing a new module, try to stop any software which may be using the old version to replace. In this case, I always need to stop the Network Manager to install the new module rt2870sta.ko (right-click on the icon of the task-bar and, then, click on "Enable Networking").

PD: Don't forget to copy the default file RT2870STA.dat to /etc/Wireless/RT2870STA . Although you use Network Manager, the module RT2870STA.ko seems to need to locate this file in order to work properly.

---

### Post by Drewkman on 2010-07-29
*negora:* Thanks very much for the speedy reply, but nope. Nothing. The adatper still isn't showing any signs of life at all, and Ubuntu still doesn't list any WLAN interface anywhere. 

I am having another issue, which has been present for a while, since before I installed this 10.04. Whenever Ubuntu is booting up, it tells me it is 'disabling IRQ #7', several times. It takes quite a while. I have no idea what this means, but considering the only things I've done to this system since install have been follow this thread's original tutorial, plus the three steps you recommended, I'm thinking it might have something to do with my problems?

---

### Post by mramaciel on 2010-09-10
I use post from [etdwh]("http://ubuntuforums.org/member.php?u=857494") and adapted to my card:

UBUNTU 10.04 with ralink RT8070/RT3070USB: 

lsusb:
Bus 001 Device 002: ID 1d4d:0002

1) Download drivers RT8070/RT3070USB(RT307x) from Ralink ([http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)). Right now, its 2010_0709_RT2870_Linux_STA_v2.4.0.1

2) Extract drivers. I extracted to /opt.

3) Delete existing rt2870sta driver. Refer to quote above for exact location

4) Edit os/linux/config.mk. Change values of
HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

5) Edit ./common/rtusb_dev_id.c

6) Look for line: {USB_DEVICE(0x148F,0x2870)}, /* Ralink */

7) Add new line below the above: {USB_DEVICE(0x1d4d,0x0002)}, /* Ralink - from lsusb */

8 ) Save and close file

9) sudo make && sudo make install

10) Download firmware RT8070/RT3070USB from Ralink ([http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)). Right now, its RT2870_Firmware_V22

11) extract firmware and copy to /lib/firmware/.

12) sudo modprobe rt2870sta
Network manager should now start scanning for wireless networks

To load module at startup...
13) edit /etc/modules. Add new line: rt2870sta

14) add to /etc/modprobe.d/blacklist.conf 
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

see ya

---

### Post by djahjah on 2010-09-17
i was trying to fix this issue for days with a rt2870 chipset. on kernel 2.6.32.21-generic on ubuntu 10.4, 

the ra0 interface was uploaded an it could scan the networks, but it was impossible to connect.

I finnaly made it by leaving the RT2870STA.dat empty (with a #) and rebooting the system.

now it works fine...
finally

damn ralink, horrible driver....

---

### Post by djahjah on 2010-09-17
oh,

the RT2870STA.dat file is at /etc/Wireless/RT2870STA/

---

### Post by Johnny Golden on 2010-10-02
I used the instructions in this thread to get my TR2870-based Draytek N61 USB adapter connecting in Lucid, but it would only connect to my 802.11n router at 54Mbps - not 270Mbps.

This is what fixed it for me:

1) Open /etc/Wireless/RT2870ST:
```
sudo gedit /etc/Wireless/RT2870ST
```

2) Change WirelessMode to 7:
```
WirelessMode=7
```

3) Save, exit and restart.

---

### Post by zipeppe on 2010-10-18
No way for me to get rt2870sta working :(

The default **rt2870sta** modules is the following guy:

```
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/RT3070 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin
srcversion:     93E93E3E336F412601AF0FA

```

Unfortunately it doesn't work because of the recursive error:

```
Oct 18 20:04:52 ibm kernel: [ 3919.944421] <==== rt28xx_init, Status=0
Oct 18 20:04:52 ibm kernel: [ 3919.956410] 0x1300 = 00073200
Oct 18 20:04:53 ibm kernel: [ 3920.285507] ---> RTMPFreeTxRxRingMemory
Oct 18 20:04:53 ibm kernel: [ 3920.285564] <--- RTMPFreeTxRxRingMemory
Oct 18 20:04:55 ibm kernel: [ 3922.369737] <-- RTMPAllocTxRxRingMemory, Status=0
Oct 18 20:04:55 ibm kernel: [ 3922.381166] -->RTUSBVenderReset
Oct 18 20:04:55 ibm kernel: [ 3922.382170] <--RTUSBVenderReset
Oct 18 20:04:57 ibm kernel: [ 3924.677950] 1. Phy Mode = 0
Oct 18 20:04:57 ibm kernel: [ 3924.677955] 2. Phy Mode = 0
Oct 18 20:04:57 ibm kernel: [ 3924.792950] 3. Phy Mode = 0
Oct 18 20:04:57 ibm kernel: [ 3924.832970] MCS Set = 00 00 00 00 00
Oct 18 20:04:57 ibm kernel: [ 3924.895939] <==== rt28xx_init, Status=0
Oct 18 20:04:57 ibm kernel: [ 3924.907934] 0x1300 = 00073200
Oct 18 20:04:58 ibm kernel: [ 3925.231942] BIRIdx(0): RXDMALen not multiple of 4.[14386], BulkInBufLen = 72)
Oct 18 20:05:02 ibm kernel: [ 3929.957361] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 144
Oct 18 20:05:23 ibm kernel: [ 3949.984712] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 144
Oct 18 20:05:53 ibm kernel: [ 3979.984428] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 144
Oct 18 20:06:33 ibm kernel: [ 4019.989187] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 144
```


So, I decided to install on my Ubuntu box (10.10) kernel v. **2.6.35-22-generic** the following drivers & firmware:

**2010_0709_RT2870_Linux_STA_v2.4.0.1**
**RT2870_Firmware_V22**

The USB dongle to be connected is the following:

[B]Bus 002 Device 004: ID 083a:7522 Accton Technology Corp. Arcadyan 802.11N Wireless Adapter
[/B]

Followed the steps as reported by **mramaciel**, compilations stops with the errors:

```

make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocUsbBulkBufStruct&#8217;:
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function &#8216;usb_buffer_alloc&#8217;
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeUsbBulkBufStruct&#8217;:
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function &#8216;usb_buffer_free&#8217;
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeTxRxRingMemory&#8217;:
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function &#8216;NICInitTransmit&#8217;:
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocTxRxRingMemory&#8217;:
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;UCHAR **&#8217;
make[2]: *** [/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/opt/Ralink/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2


```

Any idea?

---

### Post by negora on 2010-10-18
**zipeppe:** I believe you must wait until Ralink releases a new version fixed for the newest kernels. I suffer from the same problem, despite that it compiled well with the last kernel on 10.04.

---

### Post by chili555 on 2010-10-18
@zipeppe

I believe the built-in rt2870sta will work fine after you blacklist rt2800usb, rt2x00usb and rt2x00lib. Please see:```
$ modinfo rt2870sta | grep 7522
alias:          usb:v[COLOR="Red"]083A[/COLOR]p[COLOR="Red"]7522[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```Post back if I can help you.

---

### Post by zipeppe on 2010-10-18
> **chili555 said:**
> @zipeppe

I believe the built-in rt2870sta will work fine after you blacklist rt2800usb, rt2x00usb and rt2x00lib. Please see:```
$ modinfo rt2870sta | grep 7522
alias:          usb:v[COLOR="Red"]083A[/COLOR]p[COLOR="Red"]7522[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```Post back if I can help you.

Tnx guys,

the question is that using the Live distro, everything is working fine, while installed 10.10 the module doesn't play the game since it connect/disconnect quite often.

Here's my blacklist as read from /etc/modprobe.d/blacklist.conf :

```
#Ralink wireless adapter
blacklist rt2x00usb 
blacklist rt2x00lib 
blacklist rt2800usb
blacklist rt2800lib

```

After boot the kernel loads only **rt2870sta** module. The fake one :(

and here's the modinfo required:

```
modinfo rt2870sta | grep 7522
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
```

May I provide further infos about my system?

---

### Post by chili555 on 2010-10-18
> The fake oneFake? In what respect?> May I provide further infos about my system?Yes, with the "fake" one loaded, show me:```
iwconfig
dmesg | grep rt2
```Thanks.

---

### Post by zipeppe on 2010-10-19
> **chili555 said:**
> Fake? In what respect?Yes, with the "fake" one loaded, show me:```
iwconfig
dmesg | grep rt2
```Thanks.

Fake with respect the module loaded during the Live session, which is working fine :popcorn:

Here'e dmesg output:

```
[   10.303989] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   10.319367] usbcore: registered new interface driver rt2870
[   25.728191] <==== rt28xx_init, Status=0
[   30.879748] <==== rt28xx_init, Status=0

```

---

### Post by chili555 on 2010-10-19
Please let us see:```
iwconfig
ls /etc/Wireless
ls /etc/Wireless/RT2870STA
```If you do not have a file RT2870STA.dat, please do:```
sudo mkdir /etc/Wireless/RT2870STA
sudo gedit /etc/Wireless/RT2870STA/RT2870STA.dat
```Add a single line:```
Default
```Proofread, save and close gedit. Now, please do:```
sudo rmmod -f rt2870sta
sudo modprobe rt2870sta
iwconfig
sudo iwlist wlan0 scan
```Is it working now?

---

### Post by ErkSmeijer on 2010-10-20
I think we have some un-clear communication here.

**Ubuntu 10.04**
Most of the previous solutions refer to the rt2870 driver with Ubuntu 10.04. 
Blacklisting the rt28xx driver as described before, and compiling your own driver works here, although you need to compile again after each kernel update.

As of kernel 2.6.33-xx it should be built in.

**Ubuntu 10.10**
Ubuntu 10.10 has the rt2870 driver built into the kernel, with 2 problems:
- You stil need to blacklist the rt28xx drivers as @chili555 points out
- You can only make a connection at 'g-speed' (max 54mpbs), no 'n-speed' (270/300 mbps) as @zipeppe found out

Compiling your own kernel to solve this problem, results in a lot of compiling errors.  
Putting /etc/Wireless/RT2870STA/ into  /etc/Wireless/RT2870STA/RT2870STA.dat does not solve it either. 
It seems we indeed have to wait for RalinkTech to publish a new driver as @negora suggests ...

---

### Post by tvrtuscan on 2010-10-20
I've managed to get the ralink DPO_RT3070_LinuxSTA_V2.3.0.2_20100412 driver compiling by replacing all occurrences of usb_buffer_alloc with usb_alloc_coherent and usb_buffer_free with usb_free_coherent.  These are in the include/os/rt_linux.h and os/linux/rt_usb_util.c.

This now works at n speeds.  I believe this fix should also work with the rt2870 drivers.

This was taken from another thread which I can't locate at the moment.  If anyone wants it linked I'll look a bit harder.

---

### Post by zipeppe on 2010-10-20
> **tvrtuscan said:**
> I've managed to get the ralink DPO_RT3070_LinuxSTA_V2.3.0.2_20100412 driver compiling by replacing all occurrences of usb_buffer_alloc with usb_alloc_coherent and usb_buffer_free with usb_free_coherent.  These are in the include/os/rt_linux.h and os/linux/rt_usb_util.c.

This now works at n speeds.  I believe this fix should also work with the rt2870 drivers.

This was taken from another thread which I can't locate at the moment.  If anyone wants it linked I'll look a bit harder.

Yes, of course: replacing with *coherent make the driver to compile successfully. That's ok.

The module rt2870sta loads with no troubles and the interface **wlan0** has been replaced by **ra0** as expected.

Nevertheless the wifi is not working, the error caught by wicd is "Bad password" after a lot of attempts to validate the authentication.
This is the file /var/log/messages as read:


> 
Oct 20 20:32:57 ibm kernel: [  601.844825] <==== rt28xx_init, Status=0
Oct 20 20:32:57 ibm kernel: [  601.856830] 0x1300 = 00064300
Oct 20 20:32:57 ibm kernel: [  602.223831] BIRIdx(0): RXDMALen not multiple of 4.[14386], BulkInBufLen = 80)
Oct 20 20:32:58 ibm kernel: [  603.613991] pci 0000:02:1d.0: wake-up capability enabled by ACPI
Oct 20 20:32:58 ibm kernel: [  603.635137] pci 0000:02:1d.0: wake-up capability disabled by ACPI
Oct 20 20:32:58 ibm kernel: [  603.652551] tg3 0000:03:01.0: BAR 0: set to [mem 0xfb100000-0xfb10ffff 64bit] (PCI address [0xfb100000-0xfb10ffff]
Oct 20 20:32:58 ibm kernel: [  603.770926] ADDRCONF(NETDEV_UP): eth1: link is not ready
Oct 20 20:33:00 ibm kernel: [  605.375326] tg3 0000:03:01.0: eth1: Link is up at 100 Mbps, full duplex
Oct 20 20:33:00 ibm kernel: [  605.375331] tg3 0000:03:01.0: eth1: Flow control is on for TX and on for RX
Oct 20 20:33:01 ibm kernel: [  606.248474] -->RTUSBVenderReset
Oct 20 20:33:01 ibm kernel: [  606.249473] <--RTUSBVenderReset
Oct 20 20:33:03 ibm kernel: [  608.559789] Key1Str is Invalid key length(0) or Type(0)
Oct 20 20:33:03 ibm kernel: [  608.559824] Key2Str is Invalid key length(0) or Type(0)
Oct 20 20:33:03 ibm kernel: [  608.559858] Key3Str is Invalid key length(0) or Type(0)
Oct 20 20:33:03 ibm kernel: [  608.559892] Key4Str is Invalid key length(0) or Type(0)
Oct 20 20:33:03 ibm kernel: [  608.560511] 1. Phy Mode = 5
Oct 20 20:33:03 ibm kernel: [  608.560514] 2. Phy Mode = 5
Oct 20 20:33:03 ibm kernel: [  608.655283] phy mode> Error! The chip does not support 5G band 1!
Oct 20 20:33:03 ibm kernel: [  608.655395] RTMPSetPhyMode: channel is out of range, use first channel=1 
Oct 20 20:33:03 ibm kernel: [  608.742273] 3. Phy Mode = 9
Oct 20 20:33:03 ibm kernel: [  608.806271] MCS Set = ff ff 00 00 01
Oct 20 20:33:03 ibm kernel: [  608.821246] <==== rt28xx_init, Status=0
Oct 20 20:33:04 ibm kernel: [  608.833262] 0x1300 = 00064300
Oct 20 20:33:04 ibm kernel: [  608.834392] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Oct 20 20:33:04 ibm kernel: [  609.084269] BIRIdx(0): RXDMALen not multiple of 4.[14386], BulkInBufLen = 80)
Oct 20 20:33:06 ibm kernel: [  611.009185] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=2)
Oct 20 20:33:06 ibm kernel: [  611.365262] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 144
Oct 20 20:33:06 ibm kernel: [  611.365276] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 144
Oct 20 20:33:06 ibm kernel: [  611.365614] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
Oct 20 20:33:44 ibm kernel: [  648.901034] -->RTUSBVenderReset
Oct 20 20:33:44 ibm kernel: [  648.902026] <--RTUSBVenderReset
Oct 20 20:33:46 ibm kernel: [  651.204364] Key1Str is Invalid key length(0) or Type(0)
Oct 20 20:33:46 ibm kernel: [  651.204399] Key2Str is Invalid key length(0) or Type(0)
Oct 20 20:33:46 ibm kernel: [  651.204434] Key3Str is Invalid key length(0) or Type(0)
Oct 20 20:33:46 ibm kernel: [  651.204468] Key4Str is Invalid key length(0) or Type(0)
Oct 20 20:33:46 ibm kernel: [  651.205135] 1. Phy Mode = 5
Oct 20 20:33:46 ibm kernel: [  651.205140] 2. Phy Mode = 5
Oct 20 20:33:46 ibm kernel: [  651.284843] phy mode> Error! The chip does not support 5G band 1!
Oct 20 20:33:46 ibm kernel: [  651.284950] RTMPSetPhyMode: channel is out of range, use first channel=1 
Oct 20 20:33:46 ibm kernel: [  651.350843] 3. Phy Mode = 9
Oct 20 20:33:46 ibm kernel: [  651.416043] MCS Set = ff ff 00 00 01
Oct 20 20:33:46 ibm kernel: [  651.430822] <==== rt28xx_init, Status=0
Oct 20 20:33:46 ibm kernel: [  651.445850] 0x1300 = 00064300



and this is a part of dmesg output:

> 
[  699.682948] -->RTUSBVenderReset
[  699.683929] <--RTUSBVenderReset
[  701.981433] Key1Str is Invalid key length(0) or Type(0)
[  701.981479] Key2Str is Invalid key length(0) or Type(0)
[  701.981525] Key3Str is Invalid key length(0) or Type(0)
[  701.981571] Key4Str is Invalid key length(0) or Type(0)
[  701.982347] 1. Phy Mode = 5
[  701.982353] 2. Phy Mode = 5
[  702.058747] phy mode> Error! The chip does not support 5G band 1!
[  702.058872] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  702.124740] 3. Phy Mode = 9
[  702.189735] MCS Set = ff ff 00 00 01
[  702.204698] <==== rt28xx_init, Status=0
[  702.217739] 0x1300 = 00064300
[  702.337710] ERROR!!! RTMPSetTimer failed, Halt in Progress!
[  704.676539] -->RTUSBVenderReset
[  704.677529] <--RTUSBVenderReset
[  706.972847] Key1Str is Invalid key length(0) or Type(0)
[  706.972882] Key2Str is Invalid key length(0) or Type(0)
[  706.972916] Key3Str is Invalid key length(0) or Type(0)
[  706.972951] Key4Str is Invalid key length(0) or Type(0)
[  706.973624] 1. Phy Mode = 5
[  706.973627] 2. Phy Mode = 5
[  707.048354] phy mode> Error! The chip does not support 5G band 1!
[  707.048460] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  707.114335] 3. Phy Mode = 9
[  707.179333] MCS Set = ff ff 00 00 01
[  707.194304] <==== rt28xx_init, Status=0
[  707.206326] 0x1300 = 00064300
[  708.936466] tg3 0000:03:01.0: PME# enabled
[  708.936487] pci 0000:02:1d.0: wake-up capability enabled by ACPI
[  708.958696] pci 0000:02:1d.0: wake-up capability disabled by ACPI
[  708.958705] tg3 0000:03:01.0: PME# disabled
[  708.973023] tg3 0000:03:01.0: BAR 0: set to [mem 0xfb100000-0xfb10ffff 64bit] (PCI address [0xfb100000-0xfb10ffff]
[  709.090564] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  710.796820] tg3 0000:03:01.0: PME# enabled
[  710.796845] pci 0000:02:1d.0: wake-up capability enabled by ACPI
[  710.814162] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 388
[  710.867993] pci 0000:02:1d.0: wake-up capability disabled by ACPI
[  710.868011] tg3 0000:03:01.0: PME# disabled
[  710.884548] tg3 0000:03:01.0: BAR 0: set to [mem 0xfb100000-0xfb10ffff 64bit] (PCI address [0xfb100000-0xfb10ffff]
[  711.003046] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  712.670766] tg3 0000:03:01.0: eth1: Link is up at 100 Mbps, full duplex
[  712.670771] tg3 0000:03:01.0: eth1: Flow control is on for TX and on for RX
[  712.670934] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  714.791912] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 249
[  717.714478] ra0: no IPv6 routers present


And, of course, the PSK is correct. In my experience this happens when there is a mismatch between driver and kernel.

I think we really need to wait next drive release from Ralink.

---

### Post by chili555 on 2010-10-20
> Nevertheless the wifi is not working, the error caught by wicd is "Bad password" after a lot of attempts to validate the authentication.Did you set the encryption details in /etc/Wireless/RT2870STA/RT2870STA.dat?> AuthMode=OPEN[COLOR="Red"]???[/COLOR]
EncrypType=NONE[COLOR="Red"]???[/COLOR]
WPAPSK=[COLOR="Red"]???[/COLOR]
DefaultKeyID=1
Key1Type=0
Key1Str=[COLOR="Red"]???[/COLOR]Please see the README in the package from which you compiled.

---

### Post by zipeppe on 2010-10-20
> **chili555 said:**
> Did you set the encryption details in /etc/Wireless/RT2870STA/RT2870STA.dat?Please see the README in the package from which you compiled.

Well, I think the *.dat file is ok.

The good news is that with network-manager the connection does work properly, while using wicd it does not.  I will investigate further details later.

Thank to everybody for any effort.

---

### Post by ErkSmeijer on 2010-10-21
> **tvrtuscan said:**
> I've managed to get the ralink DPO_RT3070_LinuxSTA_V2.3.0.2_20100412 driver compiling by replacing all occurrences of usb_buffer_alloc with usb_alloc_coherent and usb_buffer_free with usb_free_coherent.  These are in the include/os/rt_linux.h and os/linux/rt_usb_util.c.
This now works at n speeds.  I believe this fix should also work with the rt2870 drivers.

I can confirm that this works for a rt2870 chip, now at 'n-speed', I am happy again. 

This might be a time to make a summary of this topic into a sticky, for after each update/upgrade the topic comes up in many threads.

---

### Post by Zaruman on 2010-10-21
I also managed to get my rt2870 based buffalo usb work again. I found two things that "broke" my connection:
1. I was not able to compile drivers properly due to changes in ralinks updated driver.
2. New release of Ubuntu seemed to have similarly named driver (rt2870sta.ko) in staging folder and my ubuntu loaded that instead of ralinks driver.

Here's what I did:

1. Downloaded and extracted latest drivers to usb drive (with another computer)

2. Added rt2800usb to blacklist

3. Renamed **rt2870sta.ko** in folder */lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2870* to **rt2870sta.ko.default**

4. Opened ralinks driver folder and replaced lines 1077 and 1078 in */include/os/rt_linux.h* with these:
line 1077:
```

#define RTUSB_URB_ALLOC_BUFFER(pUsb_Dev, BufSize, pDma_addr)                            usb_alloc_coherent(pUsb_Dev, BufSize, GFP_ATOMIC, pDma_addr)
```
line 1078:
```
#define RTUSB_URB_FREE_BUFFER(pUsb_Dev, BufSize, pTransferBuf, Dma_addr)        usb_free_coherent(pUsb_Dev, BufSize, pTransferBuf, Dma_addr)
```

5. Edited **config.mk** in the root of the ralinks driver folder as follows::
```
HAS_WPA_SUPPLICANT=n to HAS_WPA_SUPPLICANT=y
and
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n to HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

6. Compiled as normal

7. Added rt2870sta module to load at startup.

8. Reboot

---

### Post by steffen on 2010-10-24
I did a fresh install of Ubuntu Maverick, and inserted a USB dongle from Jensen identified as Ralink 3070/2780. It was able to find all networks straight away, but was not able to connect. It simply stalls for several minutes before password fails.

I then downloaded the newest 3070 driver from Ralink website and did the > compiling by replacing all occurrences of usb_buffer_alloc with usb_alloc_coherent and usb_buffer_free with usb_free_coherent. These are in the include/os/rt_linux.h and os/linux/rt_usb_util.c. as tvrtuscan recommends. It compiled well on Maverick, and after blacklisting rt2870sta, I had ra0 in iwconfig, and it was also able to find my SSID on iwlist, but NetworkManager was not able to find anything, and I wasn't able to associate with the network using WEP. Essentially, I am now back to where I was with a fresh Ubuntu install.

I'm not sure where to start digging on this, but I'm wondering what effect the RT2870.dat file that now exists under /etc/Wireless/RT2870/ has. Is this where the settings are grabbed from, and can I not use NetworkManager any more to manage my networks? 

Since I am using the newest version of Ubuntu, with a chipset that has GPLed drivers and firmware, I'd say everything should be in place for this driver to work out of the box. I haven't fiddled with Linux WiFi drivers since Breezy, and thought those days were gone. This thread is now more than two years old, and still people have trouble with the chipset. It's time to blacklist the chipset on [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by chili555 on 2010-10-24
> I had ra0 in iwconfig, and it was also able to find my SSID on iwlist, but NetworkManager was not able to find anything, and I wasn't able to associate with the network using WEP. May we please see:```
cat /etc/network/interfaces
dmesg | grep rt2
```Thanks.

---

### Post by MooPi on 2010-10-24
I recently purchased a Rosewill RNX-N2X IEEE 802.11b/g/n USB2 adapter. It uses the ralink 2870 chip and it works with both 10.04 & 10.10. With the later having a better connection and scan ability. The key to this device is the blacklisting of rt2800usb in /etc/modprobe.d/blacklist.conf.
For 10.10 i blacklisted rt2800usb, rt2800lib, rt2800pci and the device works superb. Under 10.04 i only blacklisted rt2800usb to achieve a stable connection. If you don't blacklist the device won't connect under 10.04 and looses connection under 10.10. I highly recommend the adapter for not only the strong signal but also the extended range.

---

### Post by duiliobn on 2010-11-06
result for 
cat /etc/network/interfaces
auto lo
iface lo inet loopback


result for

dmesg | grep rt2
[   44.400479] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   44.407300] usbcore: registered new interface driver rt2870
[   45.091135] <==== rt28xx_init, Status=0
[   45.981569] <==== rt28xx_init, Status=0
[   79.126435] <==== rt28xx_init, Status=0
[  158.636366] <==== rt28xx_init, Status=0
[  293.893637] <==== rt28xx_init, Status=0
[  383.336070] <==== rt28xx_init, Status=0
[  511.762543] <==== rt28xx_init, Status=0
[  512.653106] <==== rt28xx_init, Status=0
[  893.652079] <==== rt28xx_init, Status=0
[ 1058.540380] <==== rt28xx_init, Status=0
[ 1088.484453] <==== rt28xx_init, Status=0

still not working... 5ghz or 2.4ghz... using ubuntu 10.10... somebody pleeeeeease help us all!!

---

### Post by leppel on 2010-11-06
Has anybody had any luck with finding/getting working drivers for the belkin play usb adapter? sorry, new to linux/ubuntu, and not sure even exactly what the ralink driver supports. I would greatly appreciate ANY help whatsover! :P

---

### Post by Nickster74 on 2010-11-08
If you all love using Ubuntu why not try using Zorin O/S 3, based on ubuntu 10.04 but comes with all proprietary drivers and flash, very fast, just like ubuntu and so far suuports my dwa-140 dlink, edimax 7727in wireless PCI, Belkin N1 express card, nvidia and ATI cards.
 
once you tried it you can't go back!
 
Nickster

---

### Post by noran on 2010-11-08
Hello,

I have a Linksys WUSB100, which is why I'm trying to install the Ralink RT2870 drivers. It's been a hassle, so thank you very much for posting this!

However, I'm stuck at the make step. I get this error:

```

make
make -C tools
make[1]: Entering directory `/home/noran/Downloads/Ralink/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/noran/Downloads/Ralink/tools'
/home/noran/Downloads/Ralink/tools/bin2h
make: execvp: /home/noran/Downloads/Ralink/tools/bin2h: Permission denied
make: *** [build_tools] Error 127

```

I have Ubuntu 10.04.

Thanks, appreciate any help on this,

Noran

---

### Post by duiliobn on 2010-11-10
[Nickster74]("http://ubuntu-virginia.ubuntuforums.org/member.php?u=1110072") just tried... but no success with my wusb600n v1 with ralink 2870 =/

---

### Post by duiliobn on 2010-11-13
added to "/etc/modules" this line : ra2870sta, now when I try to start the computer I get this error: usb 2-6 device decriptor read/64, error 110
               usb 2-6 device decriptor read/8, error 110 ....
               unable to enumerate USB on port 6...

and it keeps showing it till I "ctrl del" a few time and unplugged the device

---

### Post by duiliobn on 2010-11-22
found a step-by-step, wich has many things described in this thread, and I got mine working on maverick... :-({|=

[http://www.smachado.com/2010/11/how-to-make-ralink-rt2870-driver-work-on-ubuntu-10-10/](http://www.smachado.com/2010/11/how-to-make-ralink-rt2870-driver-work-on-ubuntu-10-10/)

hope this help you all !
best regards

---

### Post by TenGees on 2010-12-04
Thanks MooPi, this worked great for me on Ubuntu 10.10 with a Belkin FSD8053 rev.3001. I didn't do any compiling or installing, just blacklisting as you said. Note that not all versions of the Belkin 8053 use these chips, some are Realtecs I think. This stick is the best I've run into so far - after sorting it out. Working in Mac OS X too.

---

### Post by cornflayke on 2010-12-28
Hey,

thank you that works perfectly fine **until the point** at which I try to connect to my wlan at home.
The dongle simply is not able to connect to that wlan but a stick based on RT2501USB is able to connect to it.

I described the issue under:
[http://ubuntuforums.org/showthread.php?p=10288191#post10288191](http://ubuntuforums.org/showthread.php?p=10288191#post10288191)

But I didn't get any response.

Any idea?

Best regards 
cornflayke

---

### Post by Luca79 on 2010-12-29
hi all I am a new user of the forum.
I used this procedure on my desktop (HPE-020it with a ralink rt2860) but it doesn't work. It find the wifi card, find the network i'd like to connect to, but ask me password over and over and i waited long time but no connection.
any advices?
thx a lot

---

### Post by cornflayke on 2010-12-30
I think that my problem is similar to the one of Luca79.

It is very weird for me, that the two Usb - Wlan - sticks get recognized differently:

```

$lsusb | grep Ralink
Bus 002 Device 005: ID 148f:3070 Ralink Technology, Corp. 
Bus 002 Device 004: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

```Has nobody a suggestion to solve this one?

I'd appreciate any help.

---

### Post by chili555 on 2010-12-30
> **cornflayke said:**
> I think that my problem is similar to the one of Luca79.

It is very weird for me, that the two Usb - Wlan - sticks get recognized differently:

```

$lsusb | grep Ralink
Bus 002 Device 005: ID 148f:3070 Ralink Technology, Corp. 
Bus 002 Device 004: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

```Has nobody a suggestion to solve this one?

I'd appreciate any help.It's because they ***are*** different. Which one are you trying to activate?

---

### Post by cornflayke on 2010-12-30
The first one. It recognizes the network but just won't connect to it just like Luca described.

The second one works fine.

My lsmod | grep rt looks like:
```

rt73usb                22434  0
crc_itu_t               1371  1 rt73usb
rt2500usb              18141  0
rt2x00usb               9703  2 rt73usb,rt2500usb
rt2x00lib              27509  3 rt73usb,rt2500usb,rt2x00usb
mac80211              205402  2 rt2x00usb,rt2x00lib
cfg80211              126528  2 rt2x00lib,mac80211
rt2870sta             461811  0
led_class               2864  2 rt2x00lib,sdhci
agpgart                31724  2 intel_agp,nvidia
parport                32635  2 ppdev,lp

```
I thought the problem would be having rt2870sta additionally to the others, but removing modules like rt73usb or rt2500usb just removes the possibility of being able to recognize the network at all with the RT2501 Adapter.

---

### Post by chili555 on 2010-12-30
You are on the right track. rt73usb is the correct driver for the second device:> 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapterrt2500usb is a conflicting driver. Let's take care of that first:```
sudo su
echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist.conf
exit
```Remove both devices and do:```
sudo rmmod -f rt73usb
sudo rmmod -f rt2500usb
lsmod | grep rt
```Remove any rt2xxx drivers that may remain. Now reinsert the first device:> 148f:3070 Ralink Technology, Corp.Please do:```
sudo modprobe rt2870sta
dmesg | grep 287
```Post the result and we'll proceed.

---

### Post by cornflayke on 2010-12-30
$dmesg | grep 287
```

[    0.172879] ACPI: EC: Look up EC in DSDT
[   36.172870] type=1505 audit(1293728237.042:6):  operation="profile_replace" pid=930 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[  608.239874] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  608.246540] usbcore: registered new interface driver rt2870
[  947.287161] device disconnected

```with $lsmod | grep rt
```

rt2870sta             461811  0 
agpgart                31724  2 nvidia,intel_agp
parport                32635  2 ppdev,lp

```left. Still not being able to connect to the network.

---

### Post by chili555 on 2010-12-30
> **cornflayke said:**
> $dmesg | grep 287
```

[    0.172879] ACPI: EC: Look up EC in DSDT
[   36.172870] type=1505 audit(1293728237.042:6):  operation="profile_replace" pid=930 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[  608.239874] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  608.246540] usbcore: registered new interface driver rt2870
[  947.287161] device disconnected

```with $lsmod | grep rt
```

rt2870sta             461811  0 
agpgart                31724  2 nvidia,intel_agp
parport                32635  2 ppdev,lp

```left. Still not being able to connect to the network.All of this looks pretty healthy! Does Network Manager see your network? Is the ethernet detached as you try to connect? Are there any signs of an attempt to connect? What does this say?```
dmesg | grep wlan
```

---

### Post by cornflayke on 2011-01-02
> **chili555 said:**
> All of this looks pretty healthy! Does Network Manager see your network? Is the ethernet detached as you try to connect? Are there any signs of an attempt to connect? What does this say?```
dmesg | grep wlan
```

Network Manager sees the network and attemps to connect but just asks me for the password over again after some time.
Eathernet is detached.

$dmesg | grep wlan
```

[  125.020133] wlan0: no IPv6 routers present

```

---

### Post by chili555 on 2011-01-02
Either your driver, Network Manager or wpa_supplicant have problems in two areas. I don't know which. First, it can be troublesome to connect to SSIDs with a space, such as "Chili House." If yours has a space, try changing to something else, such as, "ChiliHouse."

Second, many routers have a mixed WPA and WPA2 mode. The intent, I believe, is to be backwards compatible with older hardware that may not be WPA2 capable. If yours is so configured, you will have better luck with WPA *or* WPA2; not both.


Finally, have you double-checked the password? Does it work seamlessly in other computers on the network?

---

### Post by cornflayke on 2011-01-02
Hey, I changed the WPA/WPA2 mode to WPA2 only and now it works.

Thank you very much chili, you just made my day. 

Best regards 
- cornflayke

---

### Post by chili555 on 2011-01-02
Awesome! I suspect you have helped some searchers, too. Thanks for posting back.

---

### Post by Bellboy on 2011-01-05
Hi All

Wonder if someone can help.

I have followed the steps to install the latest RT2870STA driver downloaded direct from ralink.

Problem I have is no wireless device is found in IFCONFIG.

I was expecting the default wlan0 to become ra0 .... but there is nothing.

lsmod shows the rt2870dta driver is present. I had to include in /etc/modules to load at boot.

Any ideas?

lsusb shows the device still present.

My next step is to reverse my change and see if the old drivers fix the problem.

Thanks for your time.

---

### Post by chili555 on 2011-01-05
> **Bellboy said:**
> Hi All

Wonder if someone can help.

I have followed the steps to install the latest RT2870STA driver downloaded direct from ralink.

Problem I have is no wireless device is found in IFCONFIG.

I was expecting the default wlan0 to become ra0 .... but there is nothing.

lsmod shows the rt2870dta driver is present. I had to include in /etc/modules to load at boot.

Any ideas?

lsusb shows the device still present.

My next step is to reverse my change and see if the old drivers fix the problem.

Thanks for your time.Please start a new thread. Please post:```
lspci -nn
dmesg | grep -i rt2
modinfo rt2870sta | grep -i version
```Send me a private message with the link. Thanks.

---

### Post by Bellboy on 2011-01-07
Thanks Chilli

For reference, new thread:-

[http://ubuntuforums.org/showthread.php?p=10329720#post10329720](http://ubuntuforums.org/showthread.php?p=10329720#post10329720)

---

### Post by rlgoddard on 2011-01-20
Hi,

I recently acquired a 802.11n RT2870 USB stick.  I blacklisted the rt2800 and rt2x00 modules, and under 2.6.35-22, it works flawlessly.  However, under 2.6.35-24, it does not work.  The strange part is that I compiled the RT2870 driver made available at the RaLink website while running 2.6.35-24, and it does not work, but did nothing while running 2.6.35-22, and it works.  Any guidance is appreciated!

---

### Post by rlgoddard on 2011-01-20
Hi,

I recently acquired a 802.11n RT2870 USB stick.  I blacklisted the rt2800 and rt2x00 modules, and under 2.6.35-22, it works flawlessly.  However, under 2.6.35-24, it does not work.  The strange part is that I compiled the RT2870 driver made available at the RaLink website while running 2.6.35-24, and it does not work, but did nothing while running 2.6.35-22, and it works.  Any guidance is appreciated!

---

### Post by rlgoddard on 2011-01-20
Hi,

I recently acquired a 802.11n RT2870 USB stick.  I blacklisted the rt2800 and rt2x00 modules, and under 2.6.35-22, it works flawlessly.  However, under 2.6.35-24, it does not work.  The strange part is that I compiled the RT2870 driver made available at the RaLink website while running 2.6.35-24, and it does not work, but did nothing while running 2.6.35-22, and it works.  Any guidance is appreciated!

---

### Post by chili555 on 2011-01-20
It should not be necessary to compile rt2870sta; it's included in the kernel. Please boot into 2.6.35-**24** and run and post:```
lsmod | grep rt2
demsg | grep -i rt2
```Thanks.

---

### Post by rlgoddard on 2011-01-20
> **chili555 said:**
> It should not be necessary to compile rt2870sta; it's included in the kernel. Please boot into 2.6.35-**24** and run and post:```
lsmod | grep rt2
demsg | grep -i rt2
```Thanks.

Alrighty, here it is:

lsmod | grep rt2

```
rt2870sta             565092  0 
```

dmesg | grep -1 rt2

```
[   14.527090] <-- RTMPAllocAdapterBlock, Status=0
[   14.579022] usbcore: registered new interface driver rt2870
[   14.980199] nvidia: module license 'NVIDIA' taints kernel.
```

When I go to the Connection Information by right clicking on the WiFi icon next to the power icon, it says that the driver being used is "usb".  Under -24, the same screen says that the rt2800usb driver is being used (before blacklisting the rt2800usb, rt2800lib, rt2x00usb, and rt2x00lib drivers).

---

### Post by chili555 on 2011-01-20
That actually looks fairly healthy! Let's see which version it is; compiled or native:```
modinfo rt2870sta | grep version
lsusb
```Thanks.

---

### Post by rlgoddard on 2011-01-21
> **chili555 said:**
> That actually looks fairly healthy! Let's see which version it is; compiled or native:```
modinfo rt2870sta | grep version
lsusb
```Thanks.

modinfo rt2870sta | grep version:

```
version:        2.4.0.0
srcversion:     5598BFE60F8B720D8D64062
vermagic:       2.6.35-24-generic SMP mod_unload modversions 686 
```lsusb:

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c05a Logitech, Inc. 
Bus 003 Device 002: ID 03f0:6104 Hewlett-Packard DeskJet 5650c
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 148f:2870 Ralink Technology, Corp. RT2870 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by chili555 on 2011-01-21
There has been a report that the -24 linux-image itself is the issue. Please see:

[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/695509](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/695509)

If it's working flawlessly in -22, I'd just boot into -22, remove -24 and be happy. I don't see anything obviously wrong, that is, something to fix in your -24 dmesg and lsmod.

I myself have removed -24.

---

### Post by rlgoddard on 2011-01-21
> **chili555 said:**
> There has been a report that the -24 linux-image itself is the issue. Please see:
 
[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/695509](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/695509)
 
If it's working flawlessly in -22, I'd just boot into -22, remove -24 and be happy. I don't see anything obviously wrong, that is, something to fix in your -24 dmesg and lsmod.
 
I myself have removed -24.
 
Alrighty, thanks!  What would be the proper procedure to remove -24?  And do I keep -22 or upgrade to -23?  Also, do I still need to keep rt2800usb, rt2800lib, rt2x00usb, and rt2x00lib blacklisted?

---

### Post by chili555 on 2011-01-21
> **rlgoddard said:**
> Alrighty, thanks!  What would be the proper procedure to remove -24?  And do I keep -22 or upgrade to -23?  Also, do I still need to keep rt2800usb, rt2800lib, rt2x00usb, and rt2x00lib blacklisted?Boot into -22. Remove -24 and install -23 through Synaptic. Let the blacklists remain and when you reboot, you should be in -23 with a working rt2870sta with no need to compile. Please post back and let us know your result for the benefit of the searchers.

---

### Post by rlgoddard on 2011-01-21
> **chili555 said:**
> Boot into -22. Remove -24 and install -23 through Synaptic. Let the blacklists remain and when you reboot, you should be in -23 with a working rt2870sta with no need to compile. Please post back and let us know your result for the benefit of the searchers.

Done all that just now, and in -23, my wireless adapter still works!  Thanks a lot for your patience and help!

Another question... when looking at the connection information in Network Manager, I noticed that the link speed is 54 Mbps.  The wireless adapter is 802.11n compatible capable of up to 300 Mbps.  How can I turn on n-speed in Ubuntu?

---

### Post by chili555 on 2011-01-21
Since you didn't compile the driver for this kernel, the only thing I can suggest for the native driver is to force it:```
sudo iwconfig wlan0 rate auto
```Or:```
sudo iwconfig wlan0 rate 300M
```Does scanning confirm that the router is broadcasting at those speeds?```
sudo iwlist wlan0 scan
```If one of these works, we can drop a line into /etc/rc.local so it runs at boot.

---

### Post by rlgoddard on 2011-01-21
> **chili555 said:**
> Since you didn't compile the driver for this kernel, the only thing I can suggest for the native driver is to force it:```
sudo iwconfig wlan0 rate auto
```Or:```
sudo iwconfig wlan0 rate 300M
```Does scanning confirm that the router is broadcasting at those speeds?```
sudo iwlist wlan0 scan
```If one of these works, we can drop a line into /etc/rc.local so it runs at boot.

I ran the first command, then did sudo iwlist wlan0 scan, and got this:

```
Bit Rates:300 Mb/s
```Network Manager continues to show that speed is 54 Mb/s.

---

### Post by chili555 on 2011-01-21
Any improvement with?```
sudo iwconfig wlan0 rate 300M
```

---

### Post by rlgoddard on 2011-01-21
> **chili555 said:**
> Any improvement with?```
sudo iwconfig wlan0 rate 300M
```

Nope.  Still shows 54mb/s.

---

### Post by chili555 on 2011-01-21
I'm out of ideas. I suggest a search of the forum for rt2870sta and N. Sorry I couldn't be more help.

---

### Post by rlgoddard on 2011-01-21
> **chili555 said:**
> I'm out of ideas. I suggest a search of the forum for rt2870sta and N. Sorry I couldn't be more help.

That's okay.  Thanks for all your help, and I will look elsewhere here for tips on getting N speed out of my new wireless adapter.

---

### Post by ilna on 2011-02-02
Ralink has released rt2870sta driver v.2.4.0.1 an age ago, 

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

but Ubuntu still has ancient v.2.1.0 one: 

```
~$ sudo modinfo rt2870sta | grep -i 'version:'
version:        2.1.0.0
srcversion:     93E93E3E336F412601AF0FA
```

Probably last version has N support. Does anybody know exactly?

BYW, rt2870sta v.2.1.0 does work fine for me - at G mode (54Mb/s), of course - without disconnections or any other trubles at all.

---

### Post by ilna on 2011-02-05
Unfortunately, nutty still has ancient 2.1.0 rt2870sta driver :( - have tried alpha 2 under VirtualBox and looked in modinfo.

---

### Post by jtpoole99 on 2011-02-16
I've tried everything in this thread and I still can't get my usb wifi adapter working.  The driver finally installed and I have the 2.4.0 version driver and now when I try to see if it's working, I get the error messages:

johnpoole@samba845gv-linux:~$ sudo ifconfig ra0 up
ra0: ERROR while getting interface flags: No such device

johnpoole@samba845gv-linux:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

Also, when I perform the ***lsmod*** command, it shows the driver, but it's not connected to anything.

johnpoole@samba845gv-linux:~$ lsmod | grep rt

rt2870sta             545222  0 

Can someone tell me what I'm doing wrong or should I just break down and buy a different adapter?  Any help will be appreciated...

John

---

### Post by chili555 on 2011-02-16
Are you quite sure rt2870sta is correct for your device? Is it a USB device? Please post:```
lsusb
dmesg | grep -i rt2
```Thanks.

---

### Post by newubies on 2011-02-17
> **duiliobn said:**
> found a step-by-step, wich has many things described in this thread, and I got mine working on maverick... :-({|=

[http://www.smachado.com/2010/11/how-to-make-ralink-rt2870-driver-work-on-ubuntu-10-10/](http://www.smachado.com/2010/11/how-to-make-ralink-rt2870-driver-work-on-ubuntu-10-10/)

hope this help you all !
best regards

This one worked beautifully one my newly install 10.10!
thanks a lot!

---

### Post by duiliobn on 2011-04-01
have anyone tested it on the 11.04 ? is it solved ?:confused:

---

### Post by jawilljr on 2011-04-01
> **rlgoddard said:**
> That's okay.  Thanks for all your help, and I will look elsewhere here for tips on getting N speed out of my new wireless adapter.

If you want Wireless N speeds you will have to compile and install the [latest version of compat-wireless]("http://wireless.kernel.org/en/users/Download/stable/") drivers.  That is what I am using for my RT3070 device.

If you do install those drivers then you have un-blacklist these drivers:

rt2800usb
rt2800lib
rt2x00usb
rt2x00lib

Then blacklist rt2870sta

And in my case I had to uninstall Network-Manager and install WICD in its place.

BTW here is my iwconfig.

```
wlan0     IEEE 802.11bgn  ESSID:"KJAW"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:C1:C0:38:4F:31   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0
```Note the Bit Rate.

Jerry

---

### Post by Uri Stamonov on 2011-05-12
The driver in 11.04 seems to offer up to 150mbit link speeds, but signal quality and network performance is all over the place :|

---

### Post by MooPi on 2011-05-13
> **duiliobn said:**
> have anyone tested it on the 11.04 ? is it solved ?:confused:
I have a usb device listed as > Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
I simply blacklisted rt2800usb, rt2800lib, rt2x00usb, rt2x00lib, and I get a strong consistent signal. Before blacklisting it would locate the wireless signal but never connect.

---

### Post by negora on 2011-05-14
In theory, blacklisting rt2800usb is enough.

---

### Post by Sentello on 2011-07-13
Hello,
how i can in RT2870 set country mode?

---

### Post by chili555 on 2011-07-13
Do you have a file called /etc/Wireless/RT2870STA/RT2870STA.dat? I think you will find country in there. You might edit the file and change the country/region channel number to the one that corresponds to your network:
        0: channels 1 through 11
        1: channels 1 through 12
        2: channels 10 and 11 (according to ralink)
        3: channels 10 through 13
        4: channel 14
        5: channels 1 through 14
        6: channels 3 through 9
        7: channels 5 through 13 

Post back so we and the searchers will learn the result.

---

### Post by Sentello on 2011-07-14
Hi, I have Ubuntu 10.04. and i copied file to /etc/Wireless/RT2870STA/

> #The word of "Default" must not be removed
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
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
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
HT_OpMode=0
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
HT_STBC=0
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
PSP_XLINK_MODE=0

But iwlist show only 11 channels

sentello@sentello-laptop ~ $ iwlist wlan0 channel 
wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.437 GHz (Channel 6)
:confused:

---

### Post by chili555 on 2011-07-14
I found a more extensive guide to the settings in the .dat file: > @> CountryRegion=value                                 
	value
		0: use 1 ~ 11 Channel
		1: use 1 ~ 13 Channel
		2: use 10 ~ 11 Channel
		3: use 10 ~ 13 Channel
		4: use 14 Channel
		5: use 1 ~ 14 Channel
		6: use 3 ~ 9 Channel
		7: use 5 ~ 13 Channel
	   31: use 1 ~ 14 Channel (ch1-11:active scan, ch12-14 passive scan)
   	 	                                      
@> CountryRegionABand=value      							
	value	
		0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel
		1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel
		2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel
		3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel
		4: use 149, 153, 157, 161, 165 Channel
		5: use 149, 153, 157, 161 Channel
		6: use 36, 40, 44, 48 Channel
		7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel
		8: use 52, 56, 60, 64 Channel
		9: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 132, 136, 140, 149, 153, 157, 161, 165 Channel
	   10: use 36, 40, 44, 48, 149, 153, 157, 161, 165 Channel
	   11: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 149, 153, 157, 161 Channel

@> CountryCode=value
	value
		AG, AR, AW, AU, AT, BS, BB, BM, BR, BE, BG, CA, KY, CL, CN, CO, CR, CY, CZ, DK, DO, EC, SV, FI, FR, DE, 
		GR, GU, GT, HT, HN, HK, HU, IS, IN, ID, IE, IL, IT, JP, JO, LV, LI, LT, LU, MY, MT, MA, MX, NL, NZ, NO,
		PE, PT, PL, RO, RU, SA, CS, SG, SK, SI, ZA, KR, ES, SE, CH, TW, TR, GB, UA, AE, US, VE
		"" => using default setting: 2.4 G - ch 1~11; 5G - ch 52~64, 100~140, 149~165

---

### Post by Sentello on 2011-07-15
@ chili555, is my /etc/Wireless/RT2870STA/RT2870STA.dat correct?

---

### Post by chili555 on 2011-07-15
> **Sentello said:**
> @ chili555, is my /etc/Wireless/RT2870STA/RT2870STA.dat correct?I don't see your country code and I don't know what you are trying to achieve that you don't have now. In your previous post, you said you only have eleven channels; how many do you think you are supposed to have?

---

### Post by Sentello on 2011-07-15
My wifi card has only 11 channels and since i live in Europe i would like to use 13 channels.At the moment i can not find any network in 5ghz frequency.Please can you help me with this problem

---

### Post by chili555 on 2011-07-15
> #The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
[COLOR="Red"]CountryCode=[/COLOR]
ChannelGeography=1A blank here is default values:> "" => using default setting: 2.4 G - [COLOR="Red"]ch 1~11[/COLOR]; 5G - ch 52~64, 100~140, 149~165 If your country code is here, or one next to you in Europe, I'd edit the .dat file to add it and reboot.> @> CountryCode=value
value
AG, AR, AW, AU, AT, BS, BB, BM, BR, BE, BG, CA, KY, CL, CN, CO, CR, CY, CZ, DK, DO, EC, SV, FI, FR, DE,
GR, GU, GT, HT, HN, HK, HU, IS, IN, ID, IE, IL, IT, JP, JO, LV, LI, LT, LU, MY, MT, MA, MX, NL, NZ, NO,
PE, PT, PL, RO, RU, SA, CS, SG, SK, SI, ZA, KR, ES, SE, CH, TW, TR, GB, UA, AE, US, VE
"" => using default setting: 2.4 G - ch 1~11; 5G - ch 52~64, 100~140, 149~165

---

### Post by alliance1975 on 2011-07-15
> **ilna said:**
> Ralink has released rt2870sta driver v.2.4.0.1 an age ago, 

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

but Ubuntu still has ancient v.2.1.0 one: 

```
~$ sudo modinfo rt2870sta | grep -i 'version:'
version:        2.1.0.0
srcversion:     93E93E3E336F412601AF0FA
```

Probably last version has N support. Does anybody know exactly?

BYW, rt2870sta v.2.1.0 does work fine for me - at G mode (54Mb/s), of course - without disconnections or any other trubles at all.

An old tutorial I followed worked for Ubuntu 9.x and 10.x but not for 11. It stated that after sudo make install there existed 2 versions of rt2870sta.ko. One in net/wireless/ and another in staging/rt2870/. The tutorial said the one in staging, (54mbs), had to be deleted to force the net/wireless to be used, (135 mbs). After doing so in 11.04 I got nothing. After copying the net/wireless file to the staging directory it worked.

---

### Post by chili555 on 2011-07-15
> After copying the net/wireless file to the staging directory it worked.Please clarify and confirm; it works at N speeds?

---

### Post by alliance1975 on 2011-07-15
> **chili555 said:**
> Please clarify and confirm; it works at N speeds?

I've never gotten 300 mbs but 135 to 150 mbs is typical. Again the main change in the old tutorial was copying the Railink compiled driver, (/net/wireless/ directory) over the Ubuntu supplied driver, (staging/rt2870 directory).

The old tutorial I follow reads:

> In terminal: 
Code:
cd ~/Desktop/*2870*
(If you're trying to compile a second time, please note: Run "make clean" before running "make" to remove your previous attempt.)
make
sudo make install
This installs the module rt2870sta.ko, but now you have 2 copies of it: 
one in /lib/modules/`uname -r`/kernel/drivers/net/wireless and another at /lib/modules/`uname -r`/kernel/drivers/staging/rt2870. The one in the staging directory is the one that came with Ubuntu, which obviously doesn't work for you. 

Before you delete your old driver, run the following commands to see if your newly compiled driver actually functions with your USB device. 
Code:
sudo modprobe -r rt2870sta
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko
sudo /etc/init.d/networking restart
sudo restart network-manager
If NetworkManager now works, congratulations.

Then delete the version of the rt2870sta module that came with Ubuntu (there might be better ways to do this, but it will allow the newly compiled one will load by default). 
Code:
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/staging/rt2870
Otherwise, you will have to run the above commands whenever you want to use the new driver. You will need to recompile this module every time a new Linux kernel is installed.


Deleting staging rt2870 showed no usb devices at all. That's when I copied the compiled driver into staging/rt2870 and 135 to 150 mbs.

---

### Post by Sentello on 2011-07-15
[chili555]("http://ubuntuforums.org/member.php?u=35909"): thx, for reply. But i still have same problem.

I add to blnak field CZ. [COLOR=Red]CountryCode=CZ[/COLOR]

sentello@sentello-laptop ~ $ iwlist wlan0 channel 
wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.437 GHz (Channel 6)   
:confused: Ubuntu 10.04

---

### Post by chili555 on 2011-07-15
Did you unload and reload the module or reboot?```
sudo rmmod -f rt2870sta
sudo modprobe rt2870sta
```If you tried both and the result is the same, I'd look in dmesg to see if there are any interesting clues:```
dmesg | less
```

---

### Post by Sentello on 2011-07-16
I restart my computer many times, but no change.

When I am trying remove module, system is giving error

sentello@sentello-laptop ~ $ sudo rmmod -f rt2870sta 
ERROR: Removing 'rt2870sta': Resource temporarily unavailable
sentello@sentello-laptop ~ $ sudo modprobe rt2870sta
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
_____________________________________________________
dmesg | less

> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32.15+drm33.5dh (root@ubuntu) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #1 SMP Thu Jun 17 11:31:12 EEST 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005bfef000 (usable)
[    0.000000]  BIOS-e820: 000000005bff0000 - 000000005bffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000005bffffc0 - 000000005c000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x5bfef max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FF0000000 write-back
[    0.000000]   2 base 050000000 mask FF8000000 write-back
[    0.000000]   3 base 058000000 mask FFC000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000005bfef000 (usable)
[    0.000000]  modified: 000000005bff0000 - 000000005bffffc0 (ACPI data)
[    0.000000]  modified: 000000005bffffc0 - 000000005c000000 (ACPI NVS)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 372c6000 - 37fefad3
[    0.000000] Allocated new RAMDISK: 008cd000 - 015f6ad3
[    0.000000] Move RAMDISK from 00000000372c6000 - 0000000037fefad2 to 008cd000 - 015f6ad2
[    0.000000] ACPI: RSDP 000e6010 00014 (v00 OID_00)
[    0.000000] ACPI: RSDT 5bffbe80 00030 (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: FACP 5bfffb10 00074 (v01 INSYDE FACP_000 00000100 0000 00010200)
[    0.000000] ACPI: Override [DSDT-8650____], this is unsafe: tainting kernel
[    0.000000] Disabling lock debugging due to kernel taint
[    0.000000] ACPI: DSDT @ 0x5bffc400 Table override, replaced with:
[    0.000000] ACPI: DSDT c076ae7c 030D2 (v01 MTC___ 8650____ 00001000 INTL 20081204)
[    0.000000] ACPI: FACS 5bffffc0 00040
[    0.000000] ACPI: APIC 5bfffba0 0005A (v01 INSYDE APIC_000 30303030 0000 00010200)
[    0.000000] ACPI: SSDT 5bffbeb0 003B0 (v01  PmRef  Cpu0Ist 00003000 INTL 20030522)
[    0.000000] ACPI: DMI BIOS year==0, assuming ACPI-capable machine
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 583MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008c8e98]    TEXT DATA BSS ==> [0000100000 - 00008c8e98]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008c9000 - 00008cc108]              BRK ==> [00008c9000 - 00008cc108]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008cd000 - 00015f6ad3]      NEW RAMDISK ==> [00008cd000 - 00015f6ad3]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Reserving 64MB of memory at 32MB for crashkernel (System RAM: 1471MB)
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0005bfef
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0005bfef
[    0.000000] On node 0 totalpages: 376714
[    0.000000] free_area_init_node: node 0, pgdat c0787800, node_mem_map c6000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1168 pages used for memmap
[    0.000000]   HighMem zone: 148321 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 5c000000 (gap: 5c000000:a3f80000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c6c00000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 373770
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32.15+drm33.5dh root=UUID=78d840de-b236-468a-aa0a-b5c515ea0002 ro crashkernel=384M-2G:64M,2G-:128M quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 7536300 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0005bfef)
[    0.000000] Memory: 1398920k/1507260k available (4627k kernel code, 107052k reserved, 2099k data, 656k init, 597956k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0836000   ( 656 kB)
[    0.000000]       .data : 0xc0584f4f - 0xc0791f08   (2099 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0584f4f   (4627 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1691.527 MHz processor.
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 3383.05 BogoMIPS (lpj=6766108)
[    0.004042] Security Framework initialized
[    0.008054] AppArmor: AppArmor initialized
[    0.008068] Mount-cache hash table entries: 512
[    0.008291] Initializing cgroup subsys ns
[    0.008300] Initializing cgroup subsys cpuacct
[    0.008306] Initializing cgroup subsys memory
[    0.008319] Initializing cgroup subsys devices
[    0.008323] Initializing cgroup subsys freezer
[    0.008327] Initializing cgroup subsys net_cls
[    0.008364] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008368] CPU: L2 cache: 2048K
[    0.008376] mce: CPU supports 5 MCE banks
[    0.008391] CPU0: Thermal monitoring enabled (TM1)
[    0.008411] Performance Events: p6 PMU driver.
[    0.008423] ... version:                0
[    0.008425] ... bit width:              32
[    0.008427] ... generic registers:      2
[    0.008430] ... value mask:             00000000ffffffff
[    0.008433] ... max period:             000000007fffffff
[    0.008435] ... fixed-purpose events:   0
[    0.008437] ... event mask:             0000000000000003
[    0.008445] Checking 'hlt' instruction... OK.
[    0.025238] SMP alternatives: switching to UP code
[    0.033918] Freeing SMP alternatives: 19k freed
[    0.033931] ACPI: Core revision 20090903
[    0.040013] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040021] ftrace: allocating 20524 entries in 41 pages
[    0.044108] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.048561] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.088269] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 06
[    0.092001] Brought up 1 CPUs
[    0.092001] Total of 1 processors activated (3383.05 BogoMIPS).
[    0.092001] CPU0 attaching NULL sched-domain.
[    0.092001] devtmpfs: initialized
[    0.092001] regulator: core version 0.5
[    0.092001] Time:  9:43:41  Date: 07/16/11
[    0.092001] NET: Registered protocol family 16
[    0.092001] EISA bus registered
[    0.092001] ACPI: bus type pci registered
[    0.092001] PCI: PCI BIOS revision 2.10 entry at 0xe9c04, last bus=1
[    0.092001] PCI: Using configuration type 1 for base access
[    0.092001] bio: create slab <bio-0> at 0
[    0.092001] ACPI: EC: Look up EC in DSDT
[    0.092467] ACPI: Executed 1 blocks of module-level executable AML code
[    0.094935] ACPI: Interpreter enabled
[    0.094953] ACPI: (supports S0 S3 S4 S5)
[    0.094979] ACPI: Using IOAPIC for interrupt routing
[    0.104867] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
[    0.105048] ACPI: No dock devices found.
[    0.105176] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.105235] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xa0000000-0xa7ffffff]
[    0.105599] pci 0000:00:01.0: supports D1
[    0.105648] pci 0000:00:06.0: reg 10 32bit mmio: [0x000000-0x00ffff]
[    0.105742] pci 0000:00:09.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.105765] pci 0000:00:09.0: supports D1 D2
[    0.105768] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.105774] pci 0000:00:09.0: PME# disabled
[    0.105842] pci 0000:00:10.0: reg 20 io port: [0x1200-0x121f]
[    0.105873] pci 0000:00:10.0: supports D1 D2
[    0.105876] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.105881] pci 0000:00:10.0: PME# disabled
[    0.105940] pci 0000:00:10.1: reg 20 io port: [0x1220-0x123f]
[    0.105972] pci 0000:00:10.1: supports D1 D2
[    0.105974] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.105980] pci 0000:00:10.1: PME# disabled
[    0.106038] pci 0000:00:10.2: reg 20 io port: [0x1240-0x125f]
[    0.106070] pci 0000:00:10.2: supports D1 D2
[    0.106073] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.106078] pci 0000:00:10.2: PME# disabled
[    0.106116] pci 0000:00:10.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.106168] pci 0000:00:10.3: supports D1 D2
[    0.106171] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.106176] pci 0000:00:10.3: PME# disabled
[    0.106255] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.106262] pci 0000:00:11.0: quirk: region 1000-107f claimed by vt8235 PM
[    0.106267] pci 0000:00:11.0: quirk: region 1400-140f claimed by vt8235 SMB
[    0.106347] pci 0000:00:11.1: reg 20 io port: [0x1100-0x110f]
[    0.106423] pci 0000:00:11.5: reg 10 io port: [0xe000-0xe0ff]
[    0.106477] pci 0000:00:11.5: supports D1 D2
[    0.106517] pci 0000:00:11.6: reg 10 io port: [0xe100-0xe1ff]
[    0.106609] pci 0000:00:12.0: reg 10 io port: [0xe200-0xe2ff]
[    0.106618] pci 0000:00:12.0: reg 14 32bit mmio: [0xd0000000-0xd00000ff]
[    0.106666] pci 0000:00:12.0: supports D1 D2
[    0.106669] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.106674] pci 0000:00:12.0: PME# disabled
[    0.106740] pci 0000:01:00.0: reg 10 32bit mmio pref: [0x90000000-0x93ffffff]
[    0.106748] pci 0000:01:00.0: reg 14 32bit mmio: [0xc0000000-0xc0ffffff]
[    0.106772] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[    0.106793] pci 0000:01:00.0: supports D1 D2
[    0.106838] pci 0000:00:01.0: bridge io port: [0xc000-0xdfff]
[    0.106844] pci 0000:00:01.0: bridge 32bit mmio: [0xc0000000-0xcfffffff]
[    0.106850] pci 0000:00:01.0: bridge 32bit mmio pref: [0x90000000-0x9fffffff]
[    0.106879] pci_bus 0000:00: on NUMA node 0
[    0.106885] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.121589] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[    0.121683] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *7 10 11 14 15)
[    0.121775] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[    0.121867] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 14 15)
[    0.121950] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.122034] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.122118] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.122201] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.122301] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[    0.122411] ACPI: PCI Interrupt Link [ALKB] (IRQs 23) *11
[    0.122560] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *5, disabled.
[    0.122647] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *0
[    0.122759] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.122762] vgaarb: loaded
[    0.122916] SCSI subsystem initialized
[    0.122978] libata version 3.00 loaded.
[    0.123067] usbcore: registered new interface driver usbfs
[    0.123083] usbcore: registered new interface driver hub
[    0.123114] usbcore: registered new device driver usb
[    0.123263] ACPI: WMI: Mapper loaded
[    0.123266] PCI: Using ACPI for IRQ routing
[    0.123464] NetLabel: Initializing
[    0.123466] NetLabel:  domain hash size = 128
[    0.123469] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.123487] NetLabel:  unlabeled traffic allowed by default
[    0.123536] Switching to clocksource tsc
[    0.124001] AppArmor: AppArmor Filesystem Enabled
[    0.124001] pnp: PnP ACPI init
[    0.124001] ACPI: bus type pnp registered
[    0.126903] pnp: PnP ACPI: found 9 devices
[    0.126906] ACPI: ACPI bus type pnp unregistered
[    0.126912] PnPBIOS: Disabled by ACPI PNP
[    0.126930] system 00:05: iomem range 0xe0000-0xfffff could not be reserved
[    0.126935] system 00:05: iomem range 0xfff80000-0xffffffff has been reserved
[    0.126938] system 00:05: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.126942] system 00:05: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.126949] system 00:07: ioport range 0x330-0x331 has been reserved
[    0.126953] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.126957] system 00:07: ioport range 0x1000-0x107f has been reserved
[    0.126960] system 00:07: ioport range 0x1400-0x140f has been reserved
[    0.161708] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.161712] pci 0000:00:01.0:   IO window: 0xc000-0xdfff
[    0.161719] pci 0000:00:01.0:   MEM window: 0xc0000000-0xcfffffff
[    0.161725] pci 0000:00:01.0:   PREFETCH window: 0x90000000-0x9fffffff
[    0.161734] pci 0000:00:09.0: CardBus bridge, secondary bus 0000:02
[    0.161736] pci 0000:00:09.0:   IO window: 0x001800-0x0018ff
[    0.161742] pci 0000:00:09.0:   IO window: 0x001c00-0x001cff
[    0.161748] pci 0000:00:09.0:   PREFETCH window: 0x5c000000-0x5fffffff
[    0.161754] pci 0000:00:09.0:   MEM window: 0x60000000-0x63ffffff
[    0.161774] pci 0000:00:01.0: setting latency timer to 64
[    0.161786]   alloc irq_desc for 17 on node -1
[    0.161789]   alloc kstat_irqs on node -1
[    0.161796] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.161808] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.161811] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.161814] pci_bus 0000:01: resource 0 io:  [0xc000-0xdfff]
[    0.161818] pci_bus 0000:01: resource 1 mem: [0xc0000000-0xcfffffff]
[    0.161821] pci_bus 0000:01: resource 2 pref mem [0x90000000-0x9fffffff]
[    0.161824] pci_bus 0000:02: resource 0 io:  [0x1800-0x18ff]
[    0.161827] pci_bus 0000:02: resource 1 io:  [0x1c00-0x1cff]
[    0.161831] pci_bus 0000:02: resource 2 pref mem [0x5c000000-0x5fffffff]
[    0.161834] pci_bus 0000:02: resource 3 mem: [0x60000000-0x63ffffff]
[    0.161876] NET: Registered protocol family 2
[    0.161990] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.162406] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.164051] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.165188] TCP: Hash tables configured (established 131072 bind 65536)
[    0.165194] TCP reno registered
[    0.165380] NET: Registered protocol family 1
[    0.165418] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.165480] pci 0000:01:00.0: Boot video device
[    0.165763] cpufreq-nforce2: No nForce2 chipset.
[    0.165820] Scanning for low memory corruption every 60 seconds
[    0.166023] audit: initializing netlink socket (disabled)
[    0.166050] type=2000 audit(1310809421.164:1): initialized
[    0.178119] Trying to unpack rootfs image as initramfs...
[    0.192791] highmem bounce pool size: 64 pages
[    0.192800] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.194699] VFS: Disk quotas dquot_6.5.2
[    0.194780] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.200549] fuse init (API version 7.13)
[    0.200684] msgmni has been set to 1566
[    0.201001] alg: No test for stdrng (krng)
[    0.201082] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.201086] io scheduler noop registered
[    0.201089] io scheduler anticipatory registered
[    0.201091] io scheduler deadline registered
[    0.201146] io scheduler cfq registered (default)
[    0.201317] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.201347] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.204605] ACPI: AC Adapter [AC] (on-line)
[    0.204707] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.207669] ACPI: Lid Switch [LID]
[    0.207755] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.207764] ACPI: Sleep Button [SBTN]
[    0.207818] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.207821] ACPI: Power Button [PBTN]
[    0.207888] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.207892] ACPI: Power Button [PWRF]
[    0.208287] processor LNXCPU:00: registered as cooling_device0
[    0.216756] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.218356] brd: module loaded
[    0.218940] loop: module loaded
[    0.219045] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.219339] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[    0.219400] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    0.219403] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    0.219411]   alloc irq_desc for 20 on node -1
[    0.219414]   alloc kstat_irqs on node -1
[    0.219426] pata_acpi 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.219490] pata_acpi 0000:00:11.1: PCI INT A disabled
[    0.219869] Fixed MDIO Bus: probed
[    0.219913] PPP generic driver version 2.4.2
[    0.219971] tun: Universal TUN/TAP device driver, 1.6
[    0.219974] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.220074] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.220098] ehci_hcd 0000:00:10.3: enabling device (0000 -> 0002)
[    0.220195] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 21
[    0.220198] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 21
[    0.220202]   alloc irq_desc for 21 on node -1
[    0.220205]   alloc kstat_irqs on node -1
[    0.220211] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    0.220236] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    0.220279] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    0.220353] ehci_hcd 0000:00:10.3: irq 21, io mem 0x64011000
[    0.223853] isapnp: Scanning for PnP cards...
[    0.229396] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    0.229538] usb usb1: configuration #1 chosen from 1 choice
[    0.229576] hub 1-0:1.0: USB hub found
[    0.229588] hub 1-0:1.0: 6 ports detected
[    0.229670] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.229692] uhci_hcd: USB Universal Host Controller Interface driver
[    0.229755] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    0.229763] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.229803] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.229830] uhci_hcd 0000:00:10.0: irq 21, io base 0x00001200
[    0.229931] usb usb2: configuration #1 chosen from 1 choice
[    0.229969] hub 2-0:1.0: USB hub found
[    0.229978] hub 2-0:1.0: 2 ports detected
[    0.230036] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    0.230044] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.230078] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.230100] uhci_hcd 0000:00:10.1: irq 21, io base 0x00001220
[    0.230204] usb usb3: configuration #1 chosen from 1 choice
[    0.230239] hub 3-0:1.0: USB hub found
[    0.230248] hub 3-0:1.0: 2 ports detected
[    0.230301] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    0.230309] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.230348] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.230370] uhci_hcd 0000:00:10.2: irq 21, io base 0x00001240
[    0.230484] usb usb4: configuration #1 chosen from 1 choice
[    0.230514] hub 4-0:1.0: USB hub found
[    0.230523] hub 4-0:1.0: 2 ports detected
[    0.230632] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.243247] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.316222] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.316235] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.318875] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.318906] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.318932] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.319128] mice: PS/2 mouse device common for all mice
[    0.319401] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.319458] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.319625] device-mapper: uevent: version 1.0.3
[    0.320904] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.324680] device-mapper: multipath: version 1.1.0 loaded
[    0.324685] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.324891] EISA: Probing bus 0 at eisa.0
[    0.324901] Cannot allocate resource for EISA slot 1
[    0.324934] EISA: Detected 0 cards.
[    0.327971] cpuidle: using governor ladder
[    0.327974] cpuidle: using governor menu
[    0.328555] TCP cubic registered
[    0.328755] NET: Registered protocol family 10
[    0.329292] lo: Disabled Privacy Extensions
[    0.329662] NET: Registered protocol family 17
[    0.343391] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.404101] Using IPI No-Shortcut mode
[    0.404294] PM: Resume from disk failed.
[    0.404313] registered taskstats version 1
[    0.404679]   Magic number: 3:844:727
[    0.404700] block loop7: hash matches
[    0.404838] rtc_cmos 00:03: setting system clock to 2011-07-16 09:43:42 UTC (1310809422)
[    0.404843] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.404845] EDD information not available.
[    0.408283] ACPI: Battery Slot [BAT0] (battery present)
[    0.840035] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    0.928433] isapnp: No Plug & Play device found
[    1.021875] usb 1-2: configuration #1 chosen from 1 choice
[    1.035318] Freeing initrd memory: 13478k freed
[    1.053923] Freeing unused kernel memory: 656k freed
[    1.054970] Write protecting the kernel text: 4628k
[    1.055014] Write protecting the kernel read-only data: 1808k
[    1.075558] udev: starting version 151
[    1.264122] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.283717] uvesafb: , , , OEM: VIA PN800/PN880 
[    1.283723] , VBE v3.0
[    1.284977] uvesafb: protected mode interface info at c000:a81f
[    1.284982] uvesafb: pmi: set display start = c00ca86d, set palette = c00ca8de
[    1.285009] uvesafb: VBIOS/hardware supports DDC2 transfers
[    1.297976] pata_via 0000:00:11.1: version 0.3.4
[    1.298004] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.298257] Linux agpgart interface v0.103
[    1.298269] scsi0 : pata_via
[    1.305923] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:00/LNXVIDEO:00/input/input6
[    1.306042] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)
[    1.306167] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.306194] scsi1 : pata_via
[    1.309301] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    1.309305] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    1.309721] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 11, using IRQ 23
[    1.309725] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 23
[    1.309732]   alloc irq_desc for 23 on node -1
[    1.309735]   alloc kstat_irqs on node -1
[    1.309745] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKB] -> GSI 23 (level, low) -> IRQ 23
[    1.320924] eth0: VIA Rhine II at 0xd0000000, 00:40:d0:90:8a:97, IRQ 23.
[    1.321640] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
[    1.324113] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[    1.340374] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xa0000000
[    1.441867] usb 2-1: configuration #1 chosen from 1 choice
[    1.448865] uvesafb: no monitor limits have been set, default refresh rate will be used
[    1.457484] uvesafb: scrolling: ywrap using protected mode interface, yres_virtual=4320
[    1.459065] uvesafb: framebuffer at 0x90000000, mapped to 0xf8100000, using 21600k, total 65536k
[    1.459071] fb0: VESA VGA frame buffer device
[    1.472565] ata1.00: ATA-7: FUJITSU MHV2080AT, 000000A0, max UDMA/100
[    1.472570] ata1.00: 156301488 sectors, multi 16: LBA 
[    1.488411] ata1.00: configured for UDMA/100
[    1.488602] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2080A 0000 PQ: 0 ANSI: 5
[    1.488778] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.489150] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.489205] sd 0:0:0:0: [sda] Write Protect is off
[    1.489209] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.489238] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.489402]  sda: sda1 sda2 < sda5 > sda3 sda4
[    1.580824] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.652442] ata2.00: ATAPI: _NEC DVD_RW ND-6750A, 2.42, max UDMA/33
[    1.668326] ata2.00: configured for UDMA/33
[    1.670316] scsi 1:0:0:0: CD-ROM            _NEC     DVD_RW ND-6750A  2.42 PQ: 0 ANSI: 5
[    1.673520] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.673525] Uniform CD-ROM driver Revision: 3.20
[    1.673618] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.673670] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.017608] usbcore: registered new interface driver hiddev
[    3.037129] input: Genius       NetScroll+Mini Traveler as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input7
[    3.037266] generic-usb 0003:0458:0036.0001: input,hidraw0: USB HID v1.10 Mouse [Genius       NetScroll+Mini Traveler] on usb-0000:00:10.0-1/input0
[    3.037292] usbcore: registered new interface driver usbhid
[    3.037294] usbhid: v2.6:USB HID core driver
[    3.276157] Console: switching to colour frame buffer device 160x50
[    3.897148] xor: automatically using best checksumming function: pIII_sse
[    3.916006]    pIII_sse  :  4396.000 MB/sec
[    3.916009] xor: using function: pIII_sse (4396.000 MB/sec)
[    3.921125] device-mapper: dm-raid45: initialized v0.2594b
[    4.114326] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   28.845025] udev: starting version 151
[   28.904431] Adding 249848k swap on /dev/sda4.  Priority:-1 extents:1 across:249848k 
[   28.963249] lp: driver loaded but no devices found
[   29.315178] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.437779] irda_init()
[   29.437802] NET: Registered protocol family 23
[   29.508069] cfg80211: Calling CRDA to update world regulatory domain
[   29.521922] cfg80211: World regulatory domain updated:
[   29.521927]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.521931]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.521934]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.521938]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.521941]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.521944]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.658445] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   29.696803] vga16fb: initializing
[   29.696811] vga16fb: mapped to 0xc00a0000
[   29.696818] vga16fb: not registering due to another framebuffer present
[   29.720898] yenta_cardbus 0000:00:09.0: CardBus bridge found [1734:10ab]
[   29.720926] yenta_cardbus 0000:00:09.0: Using CSCINT to route CSC interrupts to PCI
[   29.720929] yenta_cardbus 0000:00:09.0: Routing CardBus interrupts to PCI
[   29.720935] yenta_cardbus 0000:00:09.0: TI: mfunc 0x01001002, devctl 0x44
[   29.721355] rtusb init --->
[   29.721732] 
[   29.721733] 
[   29.721734] === pAd = f98dd000, size = 566748 ===
[   29.721735] 
[   29.721737] <-- RTMPAllocAdapterBlock, Status=0
[   29.723377] usbcore: registered new interface driver rt2870
[   29.956458] yenta_cardbus 0000:00:09.0: ISA IRQ mask 0x0cf8, PCI irq 17
[   29.956464] yenta_cardbus 0000:00:09.0: Socket status: 30000006
[   29.961375] ACPI: resource vt596_smbus [0x1400-0x1407] conflicts with ACPI region SM06 [0x1406-0x1406]
[   29.961379] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   29.961427] ath5k 0000:00:06.0: enabling device (0000 -> 0002)
[   29.961439]   alloc irq_desc for 19 on node -1
[   29.961442]   alloc kstat_irqs on node -1
[   29.961453] ath5k 0000:00:06.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   29.961518] ath5k 0000:00:06.0: registered as 'phy0'
[   30.553505] ath: EEPROM regdomain: 0x60
[   30.553511] ath: EEPROM indicates we should expect a direct regpair map
[   30.553517] ath: Country alpha2 being used: 00
[   30.553520] ath: Regpair used: 0x60
[   30.561270] phy0: Selected rate control algorithm 'minstrel'
[   30.562146] ath5k phy0: Atheros AR5213A chip found (MAC: 0x59, PHY: 0x43)
[   30.562151] ath5k phy0: RF5112B multiband radio found (0x36)
[   30.562626] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
[   30.562772] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 5, using IRQ 22
[   30.562775] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   30.562784]   alloc irq_desc for 22 on node -1
[   30.562787]   alloc kstat_irqs on node -1
[   30.562798] VIA 82xx Modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   30.565830] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   30.687360] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[   30.731047] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   30.733263] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   30.734187] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   30.734954] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   30.735903] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   30.743014] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input8
[   31.073224] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
[   31.073253] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
[   31.073270] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   31.073424] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   31.327370] ADDRCONF(NETDEV_UP): wlan1_rename: link is not ready
[   31.674473] <-- RTMPAllocTxRxRingMemory, Status=0
[   31.692065] -->RTUSBVenderReset
[   31.692390] <--RTUSBVenderReset
[   32.028535] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat
[   32.028541] 1. Phy Mode = 0
[   32.028543] 2. Phy Mode = 0
[   32.063799] 3. Phy Mode = 0
[   32.068552] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   32.068557] MCS Set = 00 00 00 00 00
[   32.078301] <==== RTMPInitialize, Status=0
[   32.079921] 0x1300 = 000a4200
[   32.088500] eth0: link down
[   32.088755] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.953509] ppdev: user-space parallel port driver
[   37.160304] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1574
[   41.100281] DRS: unkown mode,default use 11N 1S AP 
[   41.100291] DRS: unkown mode (SupRateLen=0, ExtRateLen=0, MCSSet[0]=0x0, MCSSet[1]=0x0)
[   42.260016] wlan0: no IPv6 routers present
[   50.304164] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1155
[   50.304541] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[   50.677945] DRS: unkown mode,default use 11N 1S AP 
[   50.677957] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[   52.860088] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 1)
[   52.860133] wlan1_rename: deauthenticating from 00:1f:cf:10:5a:66 by local choice (reason=3)
[   52.860166] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 1)
[   53.060056] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 2)
[   53.260044] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 3)
[   53.460034] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 timed out
[   63.048052] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 1)
[   63.248033] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 2)
[   63.448029] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 3)
[   63.598920] wlan1_rename: direct probe responded
[   63.598928] wlan1_rename: authenticate with AP 00:1f:cf:10:5a:66 (try 1)
[   63.770330] wlan1_rename: authenticated
[   63.770367] wlan1_rename: associate with AP 00:1f:cf:10:5a:66 (try 1)
[   63.890217] wlan1_rename: RX AssocResp from 00:1f:cf:10:5a:66 (capab=0x421 status=0 aid=13)
[   63.890223] wlan1_rename: associated
[   63.891052] ADDRCONF(NETDEV_CHANGE): wlan1_rename: link becomes ready
[   63.891141] cfg80211: Calling CRDA for country: BG
[   63.906215] cfg80211: Received country IE:
[   63.906221] cfg80211: Regulatory domain: BG
[   63.906223]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   63.906227]     (2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   63.906230] cfg80211: CRDA thinks this should applied:
[   63.906232] cfg80211: Regulatory domain: BG
[   63.906234]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   63.906238]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   63.906241]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2300 mBm)
[   63.906244]     (5250000 KHz - 5290000 KHz @ 40000 KHz), (N/A, 2300 mBm)
[   63.906247]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[   63.906250] cfg80211: We intersect both of these and get:
[   63.906252] cfg80211: Regulatory domain: 98
[   63.906254]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   63.906257]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   63.906265] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[   63.906268] cfg80211: Leaving channel 5180 MHz intact on phy0 - no rule found in band on Country IE
[   63.906272] cfg80211: Leaving channel 5200 MHz intact on phy0 - no rule found in band on Country IE
[   63.906275] cfg80211: Leaving channel 5220 MHz intact on phy0 - no rule found in band on Country IE
[   63.906278] cfg80211: Leaving channel 5240 MHz intact on phy0 - no rule found in band on Country IE
[   63.906281] cfg80211: Leaving channel 5260 MHz intact on phy0 - no rule found in band on Country IE
[   63.906285] cfg80211: Leaving channel 5280 MHz intact on phy0 - no rule found in band on Country IE
[   63.906288] cfg80211: Leaving channel 5300 MHz intact on phy0 - no rule found in band on Country IE
[   63.906291] cfg80211: Leaving channel 5320 MHz intact on phy0 - no rule found in band on Country IE
[   63.906294] cfg80211: Leaving channel 5500 MHz intact on phy0 - no rule found in band on Country IE
[   63.906298] cfg80211: Leaving channel 5520 MHz intact on phy0 - no rule found in band on Country IE
[   63.906301] cfg80211: Leaving channel 5540 MHz intact on phy0 - no rule found in band on Country IE
[   63.906304] cfg80211: Leaving channel 5560 MHz intact on phy0 - no rule found in band on Country IE
[   63.906307] cfg80211: Leaving channel 5580 MHz intact on phy0 - no rule found in band on Country IE
[   63.906311] cfg80211: Leaving channel 5600 MHz intact on phy0 - no rule found in band on Country IE
[   63.906314] cfg80211: Leaving channel 5620 MHz intact on phy0 - no rule found in band on Country IE
[   63.906317] cfg80211: Leaving channel 5640 MHz intact on phy0 - no rule found in band on Country IE
[   63.906321] cfg80211: Leaving channel 5660 MHz intact on phy0 - no rule found in band on Country IE
[   63.906324] cfg80211: Leaving channel 5680 MHz intact on phy0 - no rule found in band on Country IE
[   63.906327] cfg80211: Leaving channel 5700 MHz intact on phy0 - no rule found in band on Country IE
[   63.906330] cfg80211: Leaving channel 5745 MHz intact on phy0 - no rule found in band on Country IE
[   63.906334] cfg80211: Leaving channel 5765 MHz intact on phy0 - no rule found in band on Country IE
[   63.906337] cfg80211: Leaving channel 5785 MHz intact on phy0 - no rule found in band on Country IE
[   63.906340] cfg80211: Leaving channel 5805 MHz intact on phy0 - no rule found in band on Country IE
[   63.906343] cfg80211: Leaving channel 5825 MHz intact on phy0 - no rule found in band on Country IE
[   63.906356] cfg80211: Current regulatory domain updated by AP to: BG
[   63.906359]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   63.906362]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   74.052024] wlan1_rename: no IPv6 routers present
[   88.011367] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1232
[   93.872059] Marking TSC unstable due to cpufreq changes
[   93.872524] Switching to clocksource acpi_pm
[  108.836483] wlan1_rename: deauthenticating from 00:1f:cf:10:5a:66 by local choice (reason=3)
[  127.917023] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1327
[  187.909320] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1574
[  256.387500] wlan1_rename: deauthenticating from 00:1f:cf:10:5a:66 by local choice (reason=3)
[  256.739593] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 1)
[  256.936079] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 2)
[  257.136064] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 3)
[  257.336046] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 timed out
[  266.546026] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 1)
[  266.744053] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 2)
[  266.944358] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 3)
[  267.144063] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 timed out
[  267.909714] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1327
[  276.625039] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 1)
[  276.824075] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 2)
[  277.024097] wlan1_rename: direct probe to AP 00:1f:cf:10:5a:66 (try 3)
[  277.138145] wlan1_rename: direct probe responded
[  277.138164] wlan1_rename: authenticate with AP 00:1f:cf:10:5a:66 (try 1)
[  277.285163] wlan1_rename: authenticated
[  277.285220] wlan1_rename: associate with AP 00:1f:cf:10:5a:66 (try 1)
[  277.425731] wlan1_rename: RX AssocResp from 00:1f:cf:10:5a:66 (capab=0x421 status=0 aid=6)
[  277.425743] wlan1_rename: associated
[  367.908900] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1301
[  467.913299] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1507
[  567.912819] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1558

---

### Post by chili555 on 2011-07-16
Here is all I see that's remarkable:> [ 30.553517] ath: Country alpha2 being used: 00

[ 32.028535] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat

[ 63.891141] cfg80211: Calling CRDA for country: BG
[ 63.906215] cfg80211: Received country IE:
[ 63.906221] cfg80211: Regulatory domain: BG

[ 63.906268] cfg80211: Leaving channel 5180 MHz intact on phy0 - no rule found in band on Country IE

[ 63.906356] cfg80211: Current regulatory domain updated by AP to: BGAll I can say is WOW!!!

Let's discuss each one in turn. First, it appears that you have another working wireless card, an Atheros ath5k series. I have a strong suspicion that it calls for what it thinks is the proper country code and may be interfering with the rt2870sta. I wonder why you are not using it. If it is unstable, you ought to disable it by blacklisting its drivers.

Next, let's fix the RT3070sta issue:```
sudo mkdir /etc/Wireless/RT3070STA
sudo cp /etc/Wireless/RT2870STA/RT2870STA.dat /etc/Wireless/RT3070STA/RT3070STA.dat
```I have no idea where country code BG is coming from. I wonder if this means that the Access Point; i.e. router, has asked your wireless card to use country code BG. This may be helpful: [http://linuxwireless.org/en/developers/Documentation/cfg80211](http://linuxwireless.org/en/developers/Documentation/cfg80211)> If an AP supports sending the Country IE it will send the country IE appended on every beacon. Since we have an initial regulatory setting (set by the user, driver, or core) we don't pay attention to the country IE until we try to associate to the AP. Upon association we will parse the country IE, convert it to a cfg80211 regulatory domain structure and pass it up as a country IE regulatory hint to the wireless core. All cfg80211 drivers can use this, they must call regulatory_hint_11d(). mac80211 does this for its drivers when processing the country IEs on a beacon. regulatory_hint_11d() is optimized to ignore hints from the same AP or that match the same country IE checksum. This suggests even more reason to blacklist ath5k; it depends on cfg80211; rt2870sta does not.

Last, let's try to fix this:> WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.May we see the file? ```
cat /etc/modprobe.d/options
```After we work on these things, we'll reboot and look at dmesg again.

---

### Post by Sentello on 2011-07-16
thank you for your response. I really appreciate the advice you have given me.
I have two wifi cards,atheros and ralink. I use both cards, becouse Ralink does not have 5 Ghz and WPA support.



now /etc/modprobe.d/options is empty

---

### Post by chili555 on 2011-07-16
If the options file is empty, I'd remove it:```
sudo rm /etc/modprobe.d/options
```That will stop the modprobe issues.> I have two wifi cards,atheros and ralink. I use both cards, I'm not sure how else I can help you. When ath5k loads, it loads cfg80211 which gets the country code from the access point of BG. I am unaware of any other method to simultaneously use rt2870sta and call some other country code, aside from the .dat file as I've already discussed.

---

### Post by Sentello on 2011-07-17
Okay, no problem. So I'll add ath5k to the blacklist.
&#8220;sudo gedit /etc/modprobe.d/blacklist.conf&#8221; and type "blacklist ath5k", right?


Now is the Ralink USB fully operational?

---

### Post by chili555 on 2011-07-17
> **Sentello said:**
> Okay, no problem. So I'll add ath5k to the blacklist.
“sudo gedit /etc/modprobe.d/blacklist.conf” and type "blacklist ath5k", right?


Now is the Ralink USB fully operational?It certainly should be. Now is there any change in:```
sudo iwlist wlan1 channel
dmesg | grep -i rt2
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by Sentello on 2011-07-17
hahahah :D it works
```
sentello@sentello-laptop ~ $ iwlist wlan0 channel 
wlan0     38 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Current Frequency:2.437 GHz (Channel 6)

```

```
sentello@sentello-laptop ~ $ dmesg | grep -i rt2
[   29.919615] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   29.966615] usbcore: registered new interface driver rt2870

```

```
sentello@sentello-laptop ~ $ lsmod | grep -e rt2 -e rt3
rt2870sta             460370  1 

```

[SIZE=2]**Thank you very much**[/SIZE]


EDIT:It is possible to get working WPA encryption ?

---

### Post by chili555 on 2011-07-17
> EDIT:It is possible to get working WPA encryption ?There is usually no trouble at all with WPA or WPA2. What is troublesome is routers set to WPA and WPA2 mixed mode. Does it try and time out? Are the details set in RT2870STA.dat?> #The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=[COLOR="Red"]???[/COLOR]
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
AuthMode=[COLOR="Red"]???[/COLOR]
EncrypType=[COLOR="Red"]???[/COLOR]
WPAPSK=[COLOR="Red"]???[/COLOR]

---

### Post by Sentello on 2011-07-17
so I must set wifi network in RT2870STA.dat? Not in NetworkManager?

---

### Post by chili555 on 2011-07-17
Not usually. However, if you compiled rt2870sta from source, you may have omitted the switch to use Network Manager. We can rebuild the module; we could remove it and let the built-in do the job or we could try amending the .dat file. It's your choice. I will be happy to help in any way.

---

### Post by Sentello on 2011-07-17
Now I have last driver from Ralink website.  I can connect to an unsecured network via networkManager, but not to wpa2 or wpa enabled network.
Mabe I have old kernel with this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543836)

---

### Post by chili555 on 2011-07-17
What kernel do you have?```
uname -r
```Do you still have the Ralink file you downloaded on your desktop or somewhere?

---

### Post by Sentello on 2011-07-17
Yes I still have file from Ralink :D

Becouse is my notebook old and have some problem with dsdt i must make my own kernel...
uname -r
2.6.32.15+drm33.5dh

---

### Post by chili555 on 2011-07-17
Please check in the Ralink file and be sure you did this:> 3> In os/linux/config.mk 
	modify to meet your need.
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.If not, please do so and then rebuild the module:```
cd Desktop/DPO_whatever
```Obviously, substitute the location where the downloaded files are.```
sudo su
rmmod -f rt2870sta
make clean
make
make install
modprobe rt2870sta
exit
```

---

### Post by Sentello on 2011-07-18
Thank you for your reply.
My config.mk is alredy set HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y. 
I compiled it again, but the WPA does not work. NetworkManager requires a password over and over.

---

### Post by chili555 on 2011-07-18
Did you ever try the built-in rt2870sta? Did it recognize your wireless device? We could remove the compiled version and see what happens.

---

### Post by Sentello on 2011-07-18
I Don't know.
When I buy this card, seller gives me CD with this tutorial:  [http://www.megaupload.com/?d=W3AUHTI6](http://www.megaupload.com/?d=W3AUHTI6)
I follow, step-by-step instructions, WPA and 5ghz channel does not work. Up to now, thanks to you it works 1-14 channel at 5GHz

---

### Post by chili555 on 2011-07-18
It's a pretty good tutorial. I am sure they found it on the web and copied it. It even shows a few newbie errors, none of which are significant. I suppose that the manufacturer made changes in the file, such as 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. 

You said:> Now I have last driver from Ralink website.Would you want to try to compile it?

I have no idea why the version you got on the disk, 2.3.0.0, doesn't want to do WPA. Version 2.1.0.0 in the kernel does so just fine.

If you are going to try the easiest way first, I'd make changes to the .dat file as I highlighted above. Unload and reload the module and see if it helps.

---

### Post by Sentello on 2011-07-18
> Would you want to try to compile it?
I think that this would be the best

> I have no idea why the version you got on the disk, 2.3.0.0
The last driver that I installed is 2010_0709_RT2870_Linux_STA_**[COLOR=DarkRed]v2.4.0.1[/COLOR]**  :( When I had version 2.3.0.0 I also have problem with WPA

---

### Post by chili555 on 2011-07-18
> **Sentello said:**
> I think that this would be the best


The last driver that I installed is 2010_0709_RT2870_Linux_STA_**[COLOR=DarkRed]v2.4.0.1[/COLOR]**  :( When I had version 2.3.0.0 I also have problem with WPAIs it on your desktop? If you have not already, right-click it and select Extract Here. Now do this change:```
3> In os/linux/config.mk
modify to meet your need.
** Build for being controlled by NetworkManager or wpa_supplicant wext functions
Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. 
```Now open a terminal and do:```
cd Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1
sudo su
cp /etc/Wireless/RT2870STA/RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat.bak
make
make install
rmmod -f rt2870sta
modprobe rt2870sta
modinfo rt2870sta
exit 
```When you did the modinfo step, does it confirm it installed version 2.4.0.1? Does it connect?

We may need to restore your fine-tuned .dat file.

---

### Post by Sentello on 2011-07-19
modinfo say version:        2.0.1.0 strange

```
sentello-laptop 2010_0709_RT2870_Linux_STA_v2.4.0.1 # ifconfig wlan0 down
sentello-laptop 2010_0709_RT2870_Linux_STA_v2.4.0.1 # rmmod -f rt2870sta
sentello-laptop 2010_0709_RT2870_Linux_STA_v2.4.0.1 # modprobe rt2870sta
sentello-laptop 2010_0709_RT2870_Linux_STA_v2.4.0.1 # modinfo rt2870sta 
filename:       /lib/modules/2.6.32.15+drm33.5dh/kernel/drivers/staging/rt2870/rt2870sta.ko
alias:          rt3070sta
version:        2.0.1.0
license:        GPL
description:    RTxx70 Wireless LAN Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     169A56F8E0E6AA9C2B2FD02
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED14d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
staging:        Y
vermagic:       2.6.32.15+drm33.5dh SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

```

---

### Post by chili555 on 2011-07-19
Please reboot and then show us:> sudo updatedb
locate rt2870sta.ko
modinfo rt2870sta | grep versionThanks.

---

### Post by Sentello on 2011-07-20
Here:

sentello@sentello-laptop ~ $ **sudo updatedb**
sentello@sentello-laptop ~ $ **locate rt2870sta.ko**
/home/sentello/.local/share/Trash/files/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/.rt2870sta.ko.cmd
/home/sentello/.local/share/Trash/files/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/rt2870sta.ko
/home/sentello/Plocha/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/.rt2870sta.ko.cmd
/home/sentello/Plocha/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/rt2870sta.ko
/home/sentello/RT2870_LinuxSTA_V2.3.0.0/os/linux/.rt2870sta.ko.cmd
/home/sentello/RT2870_LinuxSTA_V2.3.0.0/os/linux/rt2870sta.ko
/lib/modules/2.6.32.15+drm33.5dh/kernel/drivers/net/wireless/rt2870sta.ko
/lib/modules/2.6.32.15+drm33.5dh/kernel/drivers/staging/rt2870/rt2870sta.ko
sentello@sentello-laptop ~ $ **modinfo rt2870sta | grep version**
version:        2.0.1.0
srcversion:     169A56F8E0E6AA9C2B2FD02
vermagic:       2.6.32.15+drm33.5dh SMP mod_unload modversions 586

---

### Post by abbbottt on 2011-07-20
Hi All,

Having real issues with the setup of a WUSB100 (1737:0078). I must have read nearly every page on the topic and feel like I am going round in circles. I've had success previously with 10.04 and 10.10 (Server Editions) by adding the id to the rt2870 driver, as below:

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf

Wouldn't say speed has ever been great but it's got me by. 11.04 is a different story though. It seems to detect the device and I can even connect but that's as far as it goes. No actual connection, can't ping, etc. I am using WPA, configured through /etc/network/interfaces.

My question really is whether or not there is a recommended method for this particular hardware. I've used the solution above but have also heard the following:

2) Compile from source, 3070 driver downloaded and edited from Railink.

3) Blacklisting some combination of drivers.

I would really appreciate it if somebody could point me in a direction!

Thank you.

---

### Post by chili555 on 2011-07-20
@Sentello--
This is the version I believe you compiled:
> /lib/modules/2.6.32.15+drm33.5dh/[COLOR="Red"]kernel/drivers/net[/COLOR]/wireless/rt2870sta.koBut this is the one that loads:> filename:       /lib/modules/2.6.32.15+drm33.5dh/[COLOR="Red"]kernel/drivers/staging[/COLOR]/rt2870/rt2870sta.ko
alias:          rt3070sta
version:        2.0.1.0
license:        GPLLet's try a little surgery. First, we back up the version 2.0.1.0:```
sudo mv /lib/modules/2.6.32.15+drm33.5dh/kernel/drivers/staging/rt2870/rt2870sta.ko /lib/modules/2.6.32.15+drm33.5dh/kernel/drivers/staging/rt2870/rt2870sta.bak
```Now we copy over the compiled version:```
sudo cp /lib/modules/2.6.32.15+drm33.5dh/kernel/drivers/net/wireless/rt2870sta.ko /lib/modules/2.6.32.15+drm33.5dh/kernel/drivers/staging/rt2870/
```Now unload the old driver and reload the new:```
sudo rmmod -f rt2870sta
sudo modprobe rt2870sta
```Check to see the version loaded:```
modinfo rt2870sta
```I look forward to your report.

---

### Post by chili555 on 2011-07-20
> **abbbottt said:**
> Hi All,

Having real issues with the setup of a WUSB100 (1737:0078). I must have read nearly every page on the topic and feel like I am going round in circles. I've had success previously with 10.04 and 10.10 (Server Editions) by adding the id to the rt2870 driver, as below:

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf

Wouldn't say speed has ever been great but it's got me by. 11.04 is a different story though. It seems to detect the device and I can even connect but that's as far as it goes. No actual connection, can't ping, etc. I am using WPA, configured through /etc/network/interfaces.

My question really is whether or not there is a recommended method for this particular hardware. I've used the solution above but have also heard the following:

2) Compile from source, 3070 driver downloaded and edited from Railink.

3) Blacklisting some combination of drivers.

I would really appreciate it if somebody could point me in a direction!

Thank you.Please show us:```
cat /etc/modprobe.d/blacklist.conf
lsmod | grep rt2
```Thanks.

---

### Post by abbbottt on 2011-07-20
Hi Chili555. Thanks for your quick response!

```

############### blacklist.conf

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

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

```

############### lsmod

rt2870sta             410104  0 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211

```

Thanks again!

---

### Post by chili555 on 2011-07-20
Let's try a quick fix:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and give us your report.

---

### Post by abbbottt on 2011-07-20
Wow. Signal up to MAX. Working GREAT. I've tried so many things I don't know how I missed this one - or maybe I applied it to a system I'd already broken...

Thank you so much.

Chris

---

### Post by chili555 on 2011-07-20
> Signal up to MAX.Meaning N speeds? At any rate, I'm glad it's working.

---

### Post by abbbottt on 2011-07-20
Signal's Max. Speed is 54MB/s, so about g.

---

### Post by Sentello on 2011-07-22
**@chili555**
Hahahahhaa
[COLOR=Red]**Thank you for helping me.**[/COLOR] :popcorn:

it seems to be ok now. 

```
sentello@sentello-laptop ~ $ modinfo rt2870sta
filename:       /lib/modules/2.6.32.15+drm33.5dh/kernel/drivers/staging/rt2870/rt2870sta.ko
[COLOR=Red]**version:        2.4.0.0**[/COLOR]
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     5598BFE60F8B720D8D64062
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.32.15+drm33.5dh SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

```both card working at same time, amazing! (with diferent country region)
***Atheros:***
```
sentello@sentello-laptop ~ $ iwlist wlan0 channel 
wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.437 GHz (Channel 6)

```***Ralink:***
```
sentello@sentello-laptop ~ $ iwlist ra0 channel 
ra0       40 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Current Frequency:2.412 GHz (Channel 1)

```

**Thanks, once again**

---

### Post by chili555 on 2011-07-22
Glad to hear it! You will have helped some searchers, too. Remember when a newer kernel version is installed by Update Manager, you'll need to rebuild the module:```
cd Desktop/2870file_wherever
sudo su
[COLOR="Red"]make clean[/COLOR]
make 
sudo make install
modprobe rt2870sta
exit
```

---

### Post by sandy8925 on 2011-07-24
Just thought you should all know, the driver for rt2870 is in the kernel (I think). So it should work out of the box on newer distros. My Linksys WUSB54GC works out of the box on Ubuntu 11.04

---

### Post by chili555 on 2011-07-24
> the driver for rt2870 is in the kernel (I think).Quite correct. The only very slight hitch is that new devices are sold for which the rt2870sta driver is unaware. That can be fixed with a little magic or one can compile the latest version from source.

---

### Post by lordjj on 2011-08-25
Hello, I'm running Ubuntu 10.04
Here's what I did:

In Makefile:
Made sure (RT28xx_MODE = STA) and (TARGET = LINUX)

In os/linux/config.mk:

Changed these from:
# Support wpa_supplicant
HAS_WPA_SUPPLICANT = n

# Support for Native WpaSupplicant Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = n

To:

# Support wpa_supplicant
HAS_WPA_SUPPLICANT = y

# Support for Native WpaSupplicant Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = y

And then I ran make.
But got an error.

```
lordjj@HP:/media/E04C983D4C981080/3070 2087 Drivers/Linux/2008_0925_RT2870_Linux_STA_v1.4.0.0$ sudo make
[sudo] password for lordjj: 
make -C tools
make[1]: Entering directory `/media/E04C983D4C981080/3070 2087 Drivers/Linux/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/media/E04C983D4C981080/3070 2087 Drivers/Linux/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
/media/E04C983D4C981080/3070 2087 Drivers/Linux/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools/bin2h
make: /media/E04C983D4C981080/3070: Command not found
make: *** [build_tools] Error 127
```

Any help?

---

### Post by chili555 on 2011-08-25
Yeah, here's some help. Let's skip the whole thing and use the rt2870sta that's already in your install. Please post:```
lsusb
lsmod | grep -e rt2 -e ndis
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.> [COLOR="Red"]2008[/COLOR]_0925_RT2870_Linux_STA_v1.4.0.0I love antiques!

---

### Post by lordjj on 2011-08-26
Thanks for the reply.
```
lordjj@HP:~$ lsusb
Bus 008 Device 002: ID 192f:0616 Avago Technologies, Pte. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:231d Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 148f:3070 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 5986:03b0 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lordjj@HP:~$ lsmod | grep -e rt2 -e ndis
rt2870sta             461811  0 
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
crc_ccitt               1339  1 rt2800usb
mac80211              204922  4 rt2x00usb,rt2x00lib,iwlagn,iwlcore
led_class               2864  3 rt2x00lib,hp_accel,iwlcore
cfg80211              126485  4 rt2x00lib,iwlagn,iwlcore,mac80211
```

Also, I did find a newer version :P (2010_0709_RT2870_Linux_STA_v2.4.0.1) [here]("http://www.ralinktech.com/support.php?s=2")

---

### Post by chili555 on 2011-08-26
I'm feeling lazy today. Let's just try one thing. In a terminal, please do:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us if your wireless is working.> iwlagn,iwlcore,mac80211Do you also have an internal wireless device that's not working? Have you tried to troubleshoot it?

---

### Post by lordjj on 2011-08-26
Hm, ok, a funny turn of events:
for some reason I guess the spaces in the directory interfered, even though I was using single quotes ''. Anyways I changed the directory from:
/media/E04C983D4C981080/3070 2087 Drivers/Linux/
to:
/media/E04C983D4C981080/RT2870_Drivers/Linux/

Apparently that helped. So here's what happened when I ran make:
```
lordjj@HP:/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1$ sudo make
make -C tools
make[1]: Entering directory `/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h
cp -f os/linux/Makefile.6 /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_md5.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_sha2.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_hmac.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.o
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c: In function &#8216;AES_GTK_KEY_WRAP&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1100 bytes is larger than 1024 bytes
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c: In function &#8216;WscDecryptData&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1364 bytes is larger than 1024 bytes
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c: In function &#8216;WscEncryptData&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1364 bytes is larger than 1024 bytes
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_arc4.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.o
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.c: In function &#8216;BssTableSortByRssi&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.c:6100: warning: the frame size of 1720 bytes is larger than 1024 bytes
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_wep.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/action.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_data.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtmp_init.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_tkip.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_aes.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_sync.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/eeprom.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_sanity.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_info.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_cfg.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_wpa.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/dfs.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/spectrum.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtmp_timer.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rt_channel.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_profile.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_asic.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_cmd.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/assoc.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/auth.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/auth_rsp.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.o
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c: In function &#8216;PeerBeacon&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c:1764: warning: the frame size of 1308 bytes is larger than 1024 bytes
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtJoinAction&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c:1094: warning: the frame size of 1300 bytes is larger than 1024 bytes
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtScanAction&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c:764: warning: the frame size of 1268 bytes is larger than 1024 bytes
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c: In function &#8216;MlmeStartReqAction&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c:581: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sanity.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/rtmp_data.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/connect.o
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/connect.c: In function &#8216;CntlOidScanProc&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/connect.c:355: warning: the frame size of 1748 bytes is larger than 1024 bytes
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/wpa.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/ags.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sta_cfg.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_profile.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.o
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;rt_ioctl_siwencode&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:1479: warning: suggest parentheses around operand of &#8216;!&#8217; or change &#8216;&&#8217; to &#8216;&&&#8217; or &#8216;!&#8217; to &#8216;~&#8217;
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;RTMPIoctlE2PROM&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:6035: warning: the frame size of 1348 bytes is larger than 1024 bytes
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;RTMPIoctlMAC&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:5836: warning: the frame size of 1344 bytes is larger than 1024 bytes
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;rt_ioctl_iwaplist&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:599: warning: the frame size of 1288 bytes is larger than 1024 bytes
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;rt_ioctl_siwmlme&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:1979: warning: the frame size of 1652 bytes is larger than 1024 bytes
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.o
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevDetach&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c:1694: warning: initialization discards qualifiers from pointer target type
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevAttach&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c:1731: warning: initialization discards qualifiers from pointer target type
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_main_dev.o
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_main_dev.c: In function &#8216;MainVirtualIF_close&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_main_dev.c:117: warning: unused variable &#8216;Cancelled&#8217;
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/ba_action.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeTxRxRingMemory&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function &#8216;NICInitTransmit&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocTxRxRingMemory&#8217;:
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;UCHAR **&#8217;
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtusb_io.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtusb_bulk.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtusb_data.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_data_usb.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/ee_prom.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtmp_mcu.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_usb.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_usb_util.o
  CC [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/usb_main_dev.o
  LD [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/rt2870sta.mod.o
  LD [M]  /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/rt2870sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
lordjj@HP:/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1$ sudo make install
make -C /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux -f Makefile.6 install
make[1]: Entering directory `/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-21-generic
make[1]: Leaving directory `/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
lordjj@HP:/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1$ cd os/linux
```

So then, I went on with the steps on page 1:
```
lordjj@HP:/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1$ cd os/linux
lordjj@HP:/media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux$ sudo insmod rt2870sta.ko
insmod: error inserting 'rt2870sta.ko': -1 File exists
```

Now it seems there's an error in the insmod step.

I tried going to the 18th step:
gedit /etc/network/interfaces
and added
auto ra0
iface ra0 inet dhcp
But nothing changed.

---

### Post by chili555 on 2011-08-26
So you came here to ask for help, I posted the solution and you didn't try it and your wireless still isn't working??

Good luck.

---

### Post by lordjj on 2011-08-26
Hey man I was just updating the situation in case it might be relevant.
I did
```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
```
and restarted.
Now I don't even see the ralink device in network manager,
and
```
lsmod | grep -e rt2 -e ndis
```
shows no results.

---

### Post by lordjj on 2011-08-26
```
lordjj@HP:~$ sudo modprobe rt2870sta
lordjj@HP:~$ dmesg | grep rt2
[   12.821329] usbcore: registered new interface driver rt2870
```

---

### Post by chili555 on 2011-08-26
It sounds like the rt2870sta version that you compiled doesn't actually claim or drive your device. Let's check:```
modinfo rt2870sta | grep -e version -e 3070
```While you post that, I'll load up my live version of 10.04.

---

### Post by lordjj on 2011-08-26
```
lordjj@HP:~$ modinfo rt2870sta | grep -e version -e 3070
version:        2.4.0.0
srcversion:     5598BFE60F8B720D8D64062
vermagic:       2.6.32-21-generic SMP mod_unload modversions 586
```

---

### Post by chili555 on 2011-08-26
As you can see, the modinfo doesn't contain 3070, your device:> Bus 002 Device 003: ID 148f:[COLOR="Red"]3070[/COLOR] Ralink Technology, Corp. Let's add it. Please go to your files, /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1 and go to the folder common. Open the file rtusb_dev_id.c with a text editor. Add a new line as shown attached. All before and after the addition must be unchanged. Proofread carefully, save and close the text editor. All punctuation, brackets, spelling, etc. are crucial. It must be exact.

Now rebuild. In a terminal:```
cd /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1
sudo su
make clean
make
make install
exit
```Reboot and let us have your report.

---

### Post by lordjj on 2011-08-26
Ok, so now its visible in Network Manager, its LED light is on and ifconfig lists it as ra0

```
lordjj@HP:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 18:a9:05:d2:cc:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41552 (41.5 KB)  TX bytes:41552 (41.5 KB)

ra0       Link encap:Ethernet  HWaddr 00:0d:a3:0a:12:9b  
          inet6 addr: fe80::20d:a3ff:fe0a:129b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:40656 (40.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:64:80:60:5a  
          inet addr:192.168.0.127  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:64ff:fe80:605a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5699 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2355906 (2.3 MB)  TX bytes:681478 (681.4 KB)

```

But its still not detecting any networks in Network Manager.

---

### Post by chili555 on 2011-08-26
Do you think it might if you shut down the internal wireless that is now connected?```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo iwlist ra0 scan
```If there are no scan results, let's see:```
dmesg | grep -e rt2 -e ra0
```

---

### Post by lordjj on 2011-08-26
```
lordjj@HP:~$ sudo ifconfig wlan0 down
lordjj@HP:~$ sudo rmmod -f iwlagn
lordjj@HP:~$ sudo iwlist ra0 scan
ra0       No scan results

lordjj@HP:~$ dmesg | grep -e rt2 -e ra0
[   12.774370] usbcore: registered new interface driver rt2870
[   14.514964] <==== rt28xx_init, Status=0
[   25.408515] ra0: no IPv6 routers present
```

(I also tried disabling the Internal WLAN Device from BIOS, still no scan results.)

---

### Post by chili555 on 2011-08-26
> In os/linux/config.mk:

Changed these from:
# Support wpa_supplicant
HAS_WPA_SUPPLICANT = n

# Support for Native WpaSupplicant Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = n

To:

# Support wpa_supplicant
HAS_WPA_SUPPLICANT = y

# Support for Native WpaSupplicant Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = yCan you confirm that, in the later version you downloaded, you made those changes?

---

### Post by lordjj on 2011-08-26
Yes, confirmed.
Also here's the whole folder (with my changes) if you need to check anything:
[here]("http://uiu.me/0wbVGjoGMYXqEbrD1sP8d378QHBMdeRPXNPh.zip")

---

### Post by chili555 on 2011-08-26
I believe the built-in rt2870sta actually claims and drives your device; at least on my 10.04.3 LTS it does. Let's check. Please do:```
sudo updatedb
```It will take a few moments, please be patient. Now do:```
locate rt2870sta.ko
```You will find several versions. The one you compiled goes into kernel/drivers/net/wireless/. The natively installed version is in kernel/drivers/staging/rt2870.

Using the full path of the natively installed version, see if it includes 3070. Here is an example. As you can see, the specific driver version drives your device, 148f:3070. If that is the case for you, I suggest you uninstall the compiled version.

---

### Post by lordjj on 2011-08-26
```
lordjj@HP:~$ sudo updatedb 
lordjj@HP:~$ locate rt2870sta.ko
/lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/rt2870sta.ko
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
lordjj@HP:~$ modinfo /lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko | grep 3070
alias:          rt3070sta
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
```

So this one:
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko

Was already there? I did try to plug the device right out of the box, but all that happened was exactly what's happening now -it shows up in network manager and ifconfig but doesn't detect any networks.

---

### Post by chili555 on 2011-08-26
> So this one:
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko

Was already there? I did try to plug the device right out of the box, but all that happened was exactly what's happening now -it shows up in network manager and ifconfig but doesn't detect any networks.Yes, indeed; however, rt2800usb was also loading and conflicting. I suggest you remove the compiled version and reboot:```
cd /media/E04C983D4C981080/RT2870_Drivers/Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1
sudo su
make uninstall
exit
```After it boots, unload the internal wireless' driver:```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
```The USB interface will probably now be wlan1; verify:```
iwconfig
sudo iwlist wlan1 scan
```

---

### Post by lordjj on 2011-08-26
:guitar:
I am very thankful for your patience!

Btw, :P upon reboots, iwconfig gave me sometimes "wlan0" as the ralink and "wlan1_rename" as the Built-in device, and sometimes "wlan0" as built-in & "wlan1" as ralink -I just unplugged the usb device on reboot and plugged it in after the system booted to have it as wlan1 :P

```
lordjj@HP:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 18:a9:05:d2:cc:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40336 (40.3 KB)  TX bytes:40336 (40.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:64:80:60:5a  
          inet addr:192.168.0.127  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:64ff:fe80:605a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10884 (10.8 KB)  TX bytes:10110 (10.1 KB)

wlan1     Link encap:Ethernet  HWaddr 00:0d:a3:0a:12:9b  
          inet6 addr: fe80::20d:a3ff:fe0a:129b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40590 (40.5 KB)  TX bytes:2680 (2.6 KB)

lordjj@HP:~$ sudo ifconfig wlan0 down
lordjj@HP:~$ sudo rmmod -f iwlagn
lordjj@HP:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-77 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lordjj@HP:~$ sudo iwlist wlan1 scan
wlan1     Scan completed :
          Cell 01 - Address: 00:23:CD:D4:99:04
                    Protocol:802.11b/g
                    ESSID:"hazem@starnet"
                    Mode:Managed
                    Channel:6
                    Quality:18/100  Signal level:-83 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:36 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 02 - Address: D8:5D:4C:D0:6B:B7
                    Protocol:802.11b/g
                    ESSID:"Blink556BB7"
                    Mode:Managed
                    Channel:10
                    Quality:26/100  Signal level:-79 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:36 Mb/s

```

Network Manager now shows me detected networks under both devices!
I will test the device more tomorrow to make sure all is well.
Thank you, very much for your help!

---

### Post by UltraAnders on 2011-09-01
Trying to get wireless N support using WUSB600N v1 (1737:0071) on Natty (kernal 2.6.38-11). I've tried quite a few bits, but based on this thread I have: 
- Downloaded latest RT2870 from RA Link website
- Extracted and made changes to os/linux/config.mk
- But when I run make or sudo make it exits with an error and doesn't create a rt2870sta.ko file in /os/linux.
Any ideas on how I can move forward??
```
andersharrison@anders-Ubuntu-11:~/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1$ sudo make
make -C tools
make[1]: Entering directory `/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h
cp -f os/linux/Makefile.6 /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile
make -C /lib/modules/2.6.38-11-generic/build SUBDIRS=/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_md5.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.o
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1096 bytes is larger than 1024 bytes
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.o
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.c:5739:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.c:6100:1: warning: the frame size of 1724 bytes is larger than 1024 bytes
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_wep.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/action.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_data.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtmp_init.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_aes.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_sync.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/eeprom.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_info.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/dfs.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/spectrum.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rt_channel.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_profile.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_asic.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/assoc.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/auth.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.o
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c:1094:1: warning: the frame size of 1296 bytes is larger than 1024 bytes
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c:764:1: warning: the frame size of 1264 bytes is larger than 1024 bytes
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c:581:1: warning: the frame size of 1064 bytes is larger than 1024 bytes
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c:1764:1: warning: the frame size of 1308 bytes is larger than 1024 bytes
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sanity.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/connect.o
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/connect.c:355:1: warning: the frame size of 1748 bytes is larger than 1024 bytes
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/wpa.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/ags.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/ba_action.o
  CC [M]  /home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52:2: error: implicit declaration of function ‘usb_buffer_alloc’
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52:13: warning: assignment makes pointer from integer without a cast
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:78:3: error: implicit declaration of function ‘usb_buffer_free’
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:234:9: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:241:9: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:278:11: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:507:12: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:566:13: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:596:12: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:610:12: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:628:13: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/andersharrison/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [LINUX] Error 2

```

One other thing, in my messing I've deleted the rt2870 folder and contents from /lib/modules/`uname -r`/kernel/drivers/staging/rt2870 :oops:. Don't know if this matters. Currently I'm limping along with rt2800 driver, I think:
```
lsmod | grep rt2
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211

```

---

### Post by Michael_BoG on 2011-09-16
Got exactly the same issue as the above poster got.

---

### Post by arraen on 2011-09-29
> **Michael_BoG said:**
> Got exactly the same issue as the above poster got.

try recompile in this way:
```
make clean
find . -name \*.[ch] -exec grep usb_buffer_alloc "{}" ";" -exec sed -i 's/usb_buffer_alloc/usb_alloc_coherent/g' "{}" ";"
find . -name \*.[ch] -exec grep usb_buffer_free "{}" ";" -exec sed -i 's/usb_buffer_free/usb_free_coherent/g' "{}" ";"
```
[http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-%28ubuntu%29/](http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-%28ubuntu%29/)

---

### Post by arraen on 2011-09-29
I'm try to use rt2870sta on Kernel 3.0.0-11 64x, driver load, but channels scan return nothing.
Could you please propose any workaround?

My logs output:
```

#uname -a
Linux blackray 3.0.0-11-generic #18-Ubuntu SMP Tue Sep 13 23:38:01 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

#lsusb
...
Bus 001 Device 005: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter [Ralink RT2870]
...

#lsmod
Module                  Size  Used by
rt2870sta             629991  1 
...

#dmesg
...
[  549.710209] usb 1-2: new high speed USB device number 5 using ehci_hcd
[  549.880585] 
[  549.880588] 
[  549.880590] === pAd = ffffc900157ce000, size = 541688 ===
[  549.880592] 
[  549.881150] <-- RTMPAllocTxRxRingMemory, Status=0
[  549.881339] <-- RTMPAllocAdapterBlock, Status=0
[  550.167396] -->RTUSBVenderReset
[  550.167520] <--RTUSBVenderReset
[  550.442678] Key1Str is Invalid key length(0) or Type(0)
[  550.442710] Key2Str is Invalid key length(0) or Type(0)
[  550.442740] Key3Str is Invalid key length(0) or Type(0)
[  550.442771] Key4Str is Invalid key length(0) or Type(0)
[  550.443221] 1. Phy Mode = 0
[  550.443224] 2. Phy Mode = 0
[  550.474109] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  550.482854] 3. Phy Mode = 0
[  550.487730] MCS Set = 00 00 00 00 00
[  550.498391] <==== rt28xx_init, Status=0
[  550.499977] 0x1300 = 00073200
[  551.339242] -->RTUSBVenderReset
[  551.339365] <--RTUSBVenderReset
[  551.614009] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[  551.614024] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[  551.614396] Key1Str is Invalid key length(0) or Type(0)
[  551.614427] Key2Str is Invalid key length(0) or Type(0)
[  551.614457] Key3Str is Invalid key length(0) or Type(0)
[  551.614487] Key4Str is Invalid key length(0) or Type(0)
[  551.614943] 1. Phy Mode = 0
[  551.614946] 2. Phy Mode = 0
[  551.645829] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  551.654574] 3. Phy Mode = 0
[  551.659450] MCS Set = 00 00 00 00 00
[  551.670149] <==== rt28xx_init, Status=0
[  551.671700] 0x1300 = 00073200
[  551.783185] /home/arraen/tmp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_asic.c:3425 assert KeyIdx < 4failed
[  551.783807] /home/arraen/tmp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_asic.c:3425 assert KeyIdx < 4failed
[  562.430069] ra0: no IPv6 routers present

# less /etc/Wireless/RT2870STA/RT2870STA.dat 
...
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=
NetworkType=Infra
WirelessMode=5
Channel=
...

#iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results

#modinfo rt2870sta 
filename:       /lib/modules/3.0.0-11-generic/kernel/drivers/net/wireless/rt2870sta.ko
version:        2.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     74F4B070313F3B8072D1208
...
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
...
depends:        
vermagic:       3.0.0-11-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

```

---

### Post by chili555 on 2011-09-29
I thought, in kernel 3.0 that rt2870sta was going to be retired in favor of rt2800usb which, reportedly, has gone through much development. Did rt2800usb not work as expected?

---

### Post by arraen on 2011-09-29
> **chili555 said:**
> I thought, in kernel 3.0 that rt2870sta was going to be retired in favor of rt2800usb which, reportedly, has gone through much development. Did rt2800usb not work as expected?

Yes, max. download speed up to 300Kb/s, under Windows it's 9Mb/s

---

### Post by UltraAnders on 2011-10-03
> **arraen said:**
> try recompile in this way:
```
make clean
find . -name \*.[ch] -exec grep usb_buffer_alloc "{}" ";" -exec sed -i 's/usb_buffer_alloc/usb_alloc_coherent/g' "{}" ";"
find . -name \*.[ch] -exec grep usb_buffer_free "{}" ";" -exec sed -i 's/usb_buffer_free/usb_free_coherent/g' "{}" ";"
```
[http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-%28ubuntu%29/](http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-%28ubuntu%29/)Thank-you, thank-you, thank-you, followed the full instructions in the link, and they worked a treat :guitar:
Will I have to recompile each time a new version of the kernel is installed? <-- in answer to my own question: Yes.
[edit]
For some reason, the link to the post doesn't work. Go [here]("http://linuxforums.org.uk/hardware-compatibility/") and the thread is called "Ralink RT2870 based USB Wireless N adapters (Ubuntu)"

---

### Post by PCNetSpec on 2011-10-03
Here's a working link -

[http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-(ubuntu)/]("http://bit.ly/qIexq8")

Just in case it helps someone.

---

### Post by Burky on 2011-10-08
> make[2]: *** [/home/david/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/david/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
make: *** [LINUX] Error 2
david@david-linux:~/2010_0709_RT2870_Linux_STA_v2.4.0.1$ 


It keeps doing that when I try to compile :(

---

### Post by chili555 on 2011-10-08
Did you try the fix in post #345 above?

---

### Post by Burky on 2011-10-08
> **chili555 said:**
> Did you try the fix in post #345 above?

Yes, and it worked up the step where i have to Run insmod rt2870sta.ko. When I try to it claims it cant find it :(

---

### Post by chili555 on 2011-10-08
How about:```
sudo modprobe rt2870sta
```See if it gets the correct version with:```
modinfo rt2870sta
```You should have version 2.4.0.1.

---

### Post by Burky on 2011-10-09
> **chili555 said:**
> How about:```
sudo modprobe rt2870sta
```See if it gets the correct version with:```
modinfo rt2870sta
```You should have version 2.4.0.1.

It's the correct version, My DWA 140 revb still doesnt work though :(

---

### Post by chili555 on 2011-10-09
> **Burky said:**
> It's the correct version, My DWA 140 revb still doesnt work though :(This thread is getting a bit long. Please start a new thread and leave a link here. Include:```
lsusb
dmesg | grep rt2
lsmod | grep rt2
```Thanks.

---

### Post by Burky on 2011-10-09
> **chili555 said:**
> This thread is getting a bit long. Please start a new thread and leave a link here. Include:```
lsusb
dmesg | grep rt2
lsmod | grep rt2
```Thanks.

No problem, i appreciate your help. Here's the the thread:

[http://ubuntuforums.org/showthread.php?p=11325591#post11325591]("http://ubuntuforums.org/showthread.php?p=11325591#post11325591")

---

### Post by imu96 on 2011-12-30
when i tried to make the file this is the error that i got... please help... :'(

```
make -C /home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.0.0-sabayon/kernel/drivers/net/wireless/
install -m 644 -c rt3090sta.ko /lib/modules/3.0.0-sabayon/kernel/drivers/net/wireless/
install: cannot stat `rt3090sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
make: *** [install] Error 2

```

---

### Post by chili555 on 2011-12-31
Would you please try:```
cd 20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
sudo su
make clean
make
make install
modprobe rt3090sta
exit
```Please let us hear your report.

---

### Post by imu96 on 2011-12-31
```
imran@imran ~ $ cd 20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
imran@imran ~/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO $ sudo su
Password: 

imran 20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO # make clean
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d,bak}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d,bak}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d,bak}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
rm -rf os/linux/Makefile

imran 20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO # make
make -C tools
make[1]: Entering directory `/home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'
/home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/Makefile
make -C /lib/modules/3.0.0-sabayon/build SUBDIRS=/home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-3.0.0-sabayon'
Makefile:327: /usr/src/linux-3.0.0-sabayon/scripts/Kbuild.include: No such file or directory
Makefile:567: /usr/src/linux-3.0.0-sabayon/arch/x86/Makefile: No such file or directory
/bin/sh: /usr/src/linux-3.0.0-sabayon/scripts/gcc-goto.sh: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-3.0.0-sabayon/arch/x86/Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-3.0.0-sabayon'
make: *** [LINUX] Error 2

imran 20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO # make install
make -C /home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.0.0-sabayon/kernel/drivers/net/wireless/
install -m 644 -c rt3090sta.ko /lib/modules/3.0.0-sabayon/kernel/drivers/net/wireless/
install: cannot stat `rt3090sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/imran/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
make: *** [install] Error 2

imran 20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO # modprobe rt3090 sta
FATAL: Module rt3090 not found.

```

---

### Post by chili555 on 2011-12-31
> make: *** [LINUX] Error 2When you get to this point, stop and proceed no farther. All further steps will also be erroneous.

Can you confirm that you have *build-essential* installed?

---

### Post by imu96 on 2011-12-31
i don't think i have it...

i run sabayon which is gentoo based

when i tried running the command 

```
sudo build-essential
```

i got 

```
sudo: build-essential: command not found
```

i tried looking for it in ubuntu software centre's sabayon equivalent (entropy) but it said that it wasn't there.

i then tried the command 

```
emerge build-essential
```

but that did not work either as it just said that 

```
emerge: there are no ebuilds to satisfy "build-essential".

emerge: searching for similar names... nothing similar found.

```

---

### Post by chili555 on 2011-12-31
> i run sabayon which is gentoo basedSorry, I know very little about Sayayon/Gentoo.

*build-essential* is all the build tools required to compile these things. In Ubuntu it includes dpkg-dev, g++, gcc, libc6-dev and make. I'm sorry I can't help you further.

---

### Post by Kemikal04 on 2012-07-11
Great post, thanks

---

### Post by v3ng3ful on 2013-03-28
Sorry for bringing up this post, I just have to add a piece of wisdom in it, if it's not already been done. Today I could confirm, rt3070sta, a driver similar -if not the same- to 2870, could not connect to a network in channel 3 (maybe even more). Although I was able to connect after changing my router to channel 1. I tested 0 and 5 country regions in RT2870STA.DAT, as well as other options without any results. I just felt like posting it here, just in case someone experiences the same problem. To be honest, putting the info from all around the net together to install this &*#$, gave me some hard time.

Best Regards

---

### Post by sandyd on 2013-03-28
**Necromancing - thread closed**

Please do not post in threads more than one year old as many things change between ubuntu releases.

Thanks!

---

