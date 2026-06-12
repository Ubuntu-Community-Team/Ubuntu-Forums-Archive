---
title: "Belkin N150 WIFI USB/F7D1101 Not connecting to wifi"
date: 2014-01-24
forum: Networking &amp; Wireless
---

### Post by andrew60 on 2014-01-24
Hi. For the past 3 days I've been researching my issue to no avail, and I'm ready to give up.  My problem is I can't connect to my university's wifi- both unencrypted and encrypted using WPA2 Enterprise peap version 0 mschapsv2, but I CAN connect to my android phone's wireless hotspot using WPA2. I have tried using wicd with wpasupplicant, ndiswrapper using drivers from Belkin website, and other drivers I found through forums that I can't remember. The current driver that I'm using is r8712u, which is suppose to be the best one. The weird thing is when I try to connect to the unsecured version, it just hangs and for the encrypted version, it continually asks for me to re-enter my password. Also, after it fails to connect to either network, it is no longer able to scan for networks- 'iwlist wlan3 s' results in no networks found, and I have to unplug and plug the USB dongle back in for it to scan again.

 I'm using a fresh install of 12.04.3 LTS w/ 3.8.0-29-generic x86_64

Relevent information:

```
ID 050d:945a Belkin Components F7D1101 Basic Wireless USB Adapter v1000 [Realtek RTL8188SU]
```
```
lsmod | grep "r8"
r8712u                189714  0 
r8169                  68716  0 
```
```
sudo lshw -C network
*-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlan3
       serial: ec:1a:59:ba:bb:4d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.43.42 multicast=yes wireless=IEEE 802.11bgn
```

Any help would be greatly appreciated.

---

### Post by chili555 on 2014-01-24
Since the device connects at home and is connected currently, let's, at least for the moment, assume the driver and hardware are working correctly.

Why is this wlan3? Does your laptop have an internal device (wlan0) that needs to be blacklisted in order to prevent a possible conflict? May we see all of:```
lsmod
```May we assume that you have properly filled in all of the required details for WPA2-Enterprise in Network Manager?  [http://www3.imperial.ac.uk/pls/portallive/docs/1/58227696.PNG](http://www3.imperial.ac.uk/pls/portallive/docs/1/58227696.PNG)

---

### Post by andrew60 on 2014-01-24
Hi Chili, I've actually come across your name multple times while trying to fix my issue :)

It turned to wlan3 when I used ndiswrapper to make the windows driver. I only have 2 network devices-ethernet on the mobo and the wireless usb dongle.

Yes, I entered those exactly. My university doesn't require entering the domain with the username. I looked online and found that might be a problem and used a specific wpasupplicant template that should've worked according to other people, but it didn't..unless I did/used it wrong. I used multiple MSCHAPv2 templates I found online and modified them trying to get it to work but to no avail.

```
ctrl_interface=/var/run/wpa_supplicant
network={
 ssid=&#8221;$_ESSID&#8221;
 proto=RSN
 key_mgmt=WPA-EAP
 pairwise=CCMP
 eap=PEAP
 identity=&#8221;$_IDENTITY&#8221;
 password=&#8221;$_PASSWORD&#8221;
 phase2=&#8221;auth=MSCHAPv2&#8221;
}
```

```
lsmod
Module                  Size  Used by
dm_crypt               23051  0 
snd_hda_codec_hdmi     37434  1 
snd_hda_codec_realtek    79916  1 
snd_hda_intel          44339  5 
snd_hda_codec         141716  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
kvm                   455932  0 
r8712u                189714  0 
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
dm_multipath           23275  0 
microcode              23017  0 
sp5100_tco             13870  0 
joydev                 17613  0 
serio_raw              13215  0 
scsi_dh                14834  1 dm_multipath
edac_core              62724  0 
snd                    69533  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_mce_amd           23343  0 
i2c_piix4              13459  0 
k10temp                13173  0 
soundcore              12680  1 snd
rfcomm                 47864  0 
bnep                   18258  2 
parport_pc             28284  0 
mac_hid                13253  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
bluetooth             247024  10 rfcomm,bnep
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ext2                   73755  1 
squashfs               36800  1 
overlayfs              28301  1 
nls_iso8859_1          12713  1 
dm_raid45              78029  0 
xor                    17116  1 dm_raid45
dm_mirror              22122  0 
dm_region_hash         20932  1 dm_mirror
dm_log                 18527  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 816158  0 
zlib_deflate           27110  1 btrfs
libcrc32c              12615  1 btrfs
hid_generic            12540  0 
usbhid                 47346  0 
hid                   105549  2 hid_generic,usbhid
usb_storage            61749  1 
radeon                960918  3 
floppy                 70206  0 
pata_acpi              13038  0 
r8169                  68716  0 
pata_atiixp            13242  0 
wmi                    19256  0 
ttm                    84051  1 radeon
drm_kms_helper         49597  1 radeon
drm                   287564  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13564  1 radeon
ahci                   25879  0 
libahci                31606  1 ahci


```

EDIT: Forgot to mention, I'm running Ubuntu on a persistent 8gb usb drive, if it matters.

---

### Post by chili555 on 2014-01-24
> used a specific wpasupplicant template Where and how does it get called? Is Network Manager installed and running, I'm not quite sure I see how your template gets used at all.

We can get it back to wlan0 at some point, but I doubt that's a factor in being able to connect. It's simply a subject for me to OCD over.

Your *lsmod* looks fine.

---

### Post by andrew60 on 2014-01-24
In my current setup I don't use wpasupplicant. I only have network manager running now. In a previous attempt, I had installed WICD and used templates but none of them worked.

---

### Post by chili555 on 2014-01-24
There are two or three things we can try, none of them sure-fire. Let's try the easiest first. I was looking at drivers under development for your device and landed here: [https://github.com/chunkeey/rtl8192su](https://github.com/chunkeey/rtl8192su) 

Within the files, I saw this:> RTL8192SU / RTL8712U firmwares

Since some people reported that not all firmwares
are compatible with all devices, we have to figure
out which is the most compatible, feature-rich and
bug-free of them all.

Currently, there are three different contenders:

 - rtl8712u-oldest-but-good.bin
   (Original firmware from 2010 - used by the r8712u
    staging driver - Take this image if you don't
    want to test)
   From Vendor's rtl8712_8188_8191_8192SU_usb_linux_v7_0.20100831

 - rtl8712u-linux-firmware-bad.bin
   Firmware 2012-04-02 (Known to be bad?)
   Taken from the linux-firmware.git
   From rtl8188C_8192C_8192D_usb_linux_v3.4.2_3727.20120404


 - rtl8712u-most-recent-v2.6.6-bad.bin
   Firmware 2012-04-05 (04?) (Reported not to work with ASUS devices?)
   From RTL819xSU_usb_linux_v2.6.6.0.20120405

Licence: Redistributable. See LICENCE.rtlwifi_firmware.txt for details.

These firmwares have to be placed into

	/lib/firmware/rtlwifi/

the driver will only load the firmware which is named "rtl8712u.bin",
so either rename one of these or set a symlink.

File: rtlwifi/rtl8712u.binVeerrrry interesting. Let's back up your current firmware first:```
cd /lib/firmware/rtlwifi
sudo mv rtl8712u.bin  rtl8712u.bak
```Now do:```
sudo wget https://github.com/chunkeey/rtl8192su/blob/master/firmwares/rtl8712u-oldest-but-good.bin
sudo mv rtl8712u-oldest-but-good.bin  rtl8712u.bin
```Now reboot and see if you can at least connect. 

If not, and you might make a copy of this for your emergency zombie apocalypse plan:```
cd  /lib/firmware/rtlwifi
sudo mv rtl8712u.bin  rtl8712u.bak2
sudo mv rtl8712u.bak  rtl8712u.bin 
```Now we have restored the default original. Reboot.

---

### Post by andrew60 on 2014-01-24
Didnt work..it kept asking me to re-enter password for encrpyted version and kept disconnecting/reconnecting for the unencrypted version.

In my rtlwifi folder, these drivers are also in it:
```
rtl8192cfw.bin     rtl8192cufw.bin  rtl8712u.bak     rtl8723fw.bin
rtl8192cfwU_B.bin  rtl8192defw.bin  rtl8712u.bin
rtl8192cfwU.bin    rtl8192sefw.bin  rtl8723fw_B.bin

```

I'm currently connected to my androids wifi with this 'new' driver.

EDIT: I'll try the other 2 drivers while waiting for a response

---

### Post by andrew60 on 2014-01-24
So I tried the first and third one so far, with no difference. Then I thought to myself, it seems like this bin isnt being loaded. So i renamed rtl8712u.bin to rtl8712u.bak2 and restarted, and my wifi is still "working". Currently there is no rtl8712u.bin in my rtlwifi folder, only the .bak's, and lshw -C network shows its using the r8712u driver.

EDIT: I think what I just said above doesn't matter...not sure how those bins work... anywho, i installed ubuntu to my HDD instead of running from a USB drive because it was taking a long time to boot. so now I am on a fully fresh install of ubuntu 12.04.3 (I still have my bootable USB so if you want me to continue with it I can), and I'm having the same problem. Also, as I'm currently updating, my download speed is about 2kB/s, with peaks of 1mB/s. It seems to fluctuate. My android wifi should get a max download speed of 4mB/s.

---

### Post by chili555 on 2014-01-25
I suggest you restore the first firmware file. If you have any trouble telling which is which, post back and we'll figure it out. Here is a hint. In my unmodified system, the default original has an md5sum of:```
chili@Think410:~$ md5sum /lib/firmware/rtlwifi/rtl8712u.bin
200fd952db3cc9259b1fd05e3e51966f  /lib/firmware/rtlwifi/rtl8712u.bin
```If the firmware wasn't getting loaded, the wireless wouldn't work at all. You'd get something like this in dmesg: ```
[100166.634495] p54pci 0000:16:00.0: enabling device (0000 -> 0002)
[100166.634509] p54pci 0000:16:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[100166.634525] p54pci 0000:16:00.0: setting latency timer to 64
[100166.650740] p54pci 0000:16:00.0: [COLOR="#FF0000"]Cannot find firmware (isl3886pci)[/COLOR]
[100166.655120] p54pci 0000:16:00.0: PCI INT A disabled
[100166.655133] p54pci: probe of 0000:16:00.0 failed with error -2
```Let's try to compile the driver I linked. On the right side, click on 'Download ZIP.' Move the file to your desktop so we can find it. Right-click it and select 'Extract Here.' Now install the prerequisites:```
sudo apt-get install build-essential linux-headers-generic
```Now we compile:```
cd ~/Desktop/rtl8192su-master
make
sudo make install
```Now blacklist the old driver:```
sudo -i
echo "blacklist r8712u"  >>  /etc/modprobe.d/blacklist.conf
echo r92su  >>  /etc/modules
exit
```Reboot and give us some great news.

---

### Post by andrew60 on 2014-01-25
I get errors whent trying to make...

```
make
make -C /lib/modules/3.8.0-35-generic/build M=/home/andrew/Downloads/rtl8192su-master/r92su CONFIG_R92SU=m CONFIG_R92SU_WPC=y  EXTRA_CFLAGS="-DDEBUG -DCONFIG_R92SU=m -DCONFIG_R92SU_WPC=y"
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-35-generic'
  CC [M]  /home/andrew/Downloads/rtl8192su-master/r92su/main.o
/home/andrew/Downloads/rtl8192su-master/r92su/main.c: In function &#8216;r92su_connect&#8217;:
/home/andrew/Downloads/rtl8192su-master/r92su/main.c:458:4: warning: passing argument 1 of &#8216;cfg80211_put_bss&#8217; from incompatible pointer type [enabled by default]
include/net/cfg80211.h:3075:6: note: expected &#8216;struct cfg80211_bss *&#8217; but argument is of type &#8216;struct wiphy *&#8217;
/home/andrew/Downloads/rtl8192su-master/r92su/main.c:458:4: error: too many arguments to function &#8216;cfg80211_put_bss&#8217;
include/net/cfg80211.h:3075:6: note: declared here
/home/andrew/Downloads/rtl8192su-master/r92su/main.c: In function &#8216;r92su_bss_free&#8217;:
/home/andrew/Downloads/rtl8192su-master/r92su/main.c:494:2: warning: passing argument 1 of &#8216;cfg80211_put_bss&#8217; from incompatible pointer type [enabled by default]
include/net/cfg80211.h:3075:6: note: expected &#8216;struct cfg80211_bss *&#8217; but argument is of type &#8216;struct wiphy *&#8217;
/home/andrew/Downloads/rtl8192su-master/r92su/main.c:494:2: error: too many arguments to function &#8216;cfg80211_put_bss&#8217;
include/net/cfg80211.h:3075:6: note: declared here
/home/andrew/Downloads/rtl8192su-master/r92su/main.c: In function &#8216;r92su_bss_add_work&#8217;:
/home/andrew/Downloads/rtl8192su-master/r92su/main.c:626:4: warning: passing argument 1 of &#8216;cfg80211_put_bss&#8217; from incompatible pointer type [enabled by default]
include/net/cfg80211.h:3075:6: note: expected &#8216;struct cfg80211_bss *&#8217; but argument is of type &#8216;struct wiphy *&#8217;
/home/andrew/Downloads/rtl8192su-master/r92su/main.c:626:4: error: too many arguments to function &#8216;cfg80211_put_bss&#8217;
include/net/cfg80211.h:3075:6: note: declared here
/home/andrew/Downloads/rtl8192su-master/r92su/main.c: In function &#8216;r92su_join_ibss&#8217;:
/home/andrew/Downloads/rtl8192su-master/r92su/main.c:1218:4: warning: passing argument 1 of &#8216;cfg80211_put_bss&#8217; from incompatible pointer type [enabled by default]
include/net/cfg80211.h:3075:6: note: expected &#8216;struct cfg80211_bss *&#8217; but argument is of type &#8216;struct wiphy *&#8217;
/home/andrew/Downloads/rtl8192su-master/r92su/main.c:1218:4: error: too many arguments to function &#8216;cfg80211_put_bss&#8217;
include/net/cfg80211.h:3075:6: note: declared here
make[2]: *** [/home/andrew/Downloads/rtl8192su-master/r92su/main.o] Error 1
make[1]: *** [_module_/home/andrew/Downloads/rtl8192su-master/r92su] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-35-generic'
make: *** [all] Error 2


```

---

### Post by chili555 on 2014-01-25
We are rapidly running out of available options. We could:

   # Install a later kernel, say 3.12, on your system and see if the r8712u runs better; and, if not

  # Compile r92su there. It compiles without error or even a warning on my 3.12 kernel. 

Of course, just because it compiles doesn't mean it actually works as expected! I haven't the device, so I can't test further. We could aslo:

  # Zip on over to the store and get a $15 USB and call it a good day. 

I'm a tinkerer and I'd try the 3.12 kernel. If you wish to do so, get the appropriate packages here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/) Be sure to get the packages appropriate to your architecture; either 32- or 64-bit:```
arch
```Get the linux-image, linux-headers-all and the headers package for your architecture; amd64 for 64-bit or i386 for 32-bit. Get them to your desktop. Install with:```
cd ~/Desktop
sudo dpkg -i linux*.deb
```Reboot.

Any improvement?

---

### Post by andrew60 on 2014-01-25
I was about to go to the store and buy a new WIfi USB until I saw you replied. The funny thing is I just bought this wifi dongle a month ago, its a new Belkin N150...I'll try my luck with another brand. I realized the problem is my kernel so I'm currently downloading 3.11 using the command ```
sudo apt-get install linux-image-generic-lts-saucy
```but it's taking forever...ubuntu's servers are either really slow or its the stupid driver. I'm also going to download the newest non LTS ubuntu image on a flash drive, try the standard r8712u driver, then r92su if it doesnt work, and if that fails, im going to take a hammer and destroy my wifi dongle.

---

### Post by andrew60 on 2014-01-25
With the 3.11 kernel, I was able to make the driver and I'm currently using it. Unfortunately, it still doesn't connect! I'm done with this USB dongle. Going to go buy a new one. Thanks for all your help Chili. Warning to anyone who has this device, it does not work on university wifi with PEAP version 0, MSCHAPSv2. At least for me...

---

### Post by Tweedle on 2014-02-15
I'm having the same issues using the same wireless adapter on Ubuntu 12.04 LTS. It see's the network, prompts for password, but then continues to ask for it even though its correct. It does connect eventually, after a bunch or tries, and stopped working during the Ubuntu installs update. I unplugged it and the install continued without all of the updates. In the fresh install, same problem, but it finnaly worked, and I was able to do an update. I have yet to reset my computer after the update, and I figured I should post this so we can try to figure this bug out and help those of us that are either too cheap or poor to get a different adapter, or those of us that just like this stuff :D

I'll post back if it connects after restart. :)

---

### Post by Tweedle on 2014-02-15
OK, i managed to get it to reconnect, but not with out problems.. It would continiously connect/disconnect/ask for password., with no avail. I also noticed it does the same thing with my ethernet connection (which isnt wired up). So this leads me to believe it may not be an issue with wireless adapter, but with mobo.
  I cant go online in Ubuntu unless this connection is working, so I may have to switch to windows :( for the time being. I'll keep in touch.

---

