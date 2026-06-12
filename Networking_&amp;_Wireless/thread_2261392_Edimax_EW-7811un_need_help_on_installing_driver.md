---
title: "Edimax EW-7811un need help on installing driver"
date: 2015-01-18
forum: Networking &amp; Wireless
---

### Post by LoLaccount.01 on 2015-01-18
Hi new to linux user here. I've been trying to figure thing out by myself by using this forum and google but i just always run into somekind of trouble by just simply following other's thread instruction. Sorry if I'm making a similar thread but i think i need a specific help so that i can have this wireless working. 

Its been weeks since i tried fixing my wifi problem and until now haven't got to fix it. When i first installed ubuntu 14.04 lts and installed all required essential My EW-7811un seem to be workin fine but for only about 5-10 mins before it starts losing connection. I then started using wicd network manager and disabling ubuntu wireless manager that came in package and still same problem. 

my current possition right now is wifi don't work. RealTek 8188CUs driversare blacklisted. I get 1-2 error installing the driver. 

Sorry about the poorly written thread lack of info etc. if anyone can provide me some assistance that would be great. If more info is needed i will provide if needed. Thanks in advace.

---

### Post by chili555 on 2015-01-18
May we see just a bit more information? From a terminal:```
lsusb
lsb_release -d
```Thanks.

---

### Post by LoLaccount.01 on 2015-01-18
igi@Ubuntu-User:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 003 Device 003: ID 047b:0011 Silitek Corp. SK-1688U Keyboard
Bus 003 Device 002: ID 04b3:310d IBM Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
gigi@Ubuntu-User:~$ lsb_release -d
Description:    Ubuntu 14.04.1 LTS

---

### Post by chili555 on 2015-01-18
> [COLOR="#FF0000"]7392:7811[/COLOR] Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless AdapterYour device uses the tricky driver rtl8192cu. Please check here: [http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648](http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648)

---

### Post by LoLaccount.01 on 2015-01-18
> **chili555 said:**
> Your device uses the tricky driver rtl8192cu. Please check here: [http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648](http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648)

Everything went fine but i still don't have any wireless discovery no blue activity light from the wireless USB. I may have disasbled the wireless before when i was trying to fix it.

---

### Post by chili555 on 2015-01-18
> **LoLaccount.01 said:**
> Everything went fine but i still don't have any wireless discovery no blue activity light from the wireless USB. I may have disasbled the wireless before when i was trying to fix it.I assume you did the requested reboot. Let's check:```
lsmod | grep 8192
cat /etc/modprobe.d/blacklist.conf
rfkill list all
```

---

### Post by LoLaccount.01 on 2015-01-18
gigi@Ubuntu-User:~$ lsmod | grep 8192
gigi@Ubuntu-User:~$ cat /etc/modprobe.d/blacklist.conf
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

# Blacklist native RealTek 8188CUs drivers
blacklist rtl8192cu

gigi@Ubuntu-User:~$ rfkill list all

i did removed blacklist rtl8192c_common and rtlwifi inside blacklist.conf

---

### Post by chili555 on 2015-01-18
> gigi@Ubuntu-User:~$ lsmod | grep 8192The correct driver isn't loaded. Please try:```
sudo modprobe 8192cu
```If there are no errors, then:```
iwconfig
```

---

### Post by LoLaccount.01 on 2015-01-18
gigi@Ubuntu-User:~$ sudo modprobe 8192cu
[sudo] password for gigi: 
modprobe: FATAL: Module 8192cu not found.

---

### Post by chili555 on 2015-01-18
> **LoLaccount.01 said:**
> gigi@Ubuntu-User:~$ sudo modprobe 8192cu
[sudo] password for gigi: 
modprobe: FATAL: Module 8192cu not found.Please try:```
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
sudo depmod -a

```Please tell me if each and every step is executed perfectly or there is an error. If there is an error, please post it. Warnings are probably OK.

---

### Post by LoLaccount.01 on 2015-01-18
> **chili555 said:**
> Please try:```
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
sudo depmod -a

```Please tell me if each and every step is executed perfectly or there is an error. If there is an error, please post it. Warnings are probably OK.

gigi@Ubuntu-User:~$ sudo dkms add ./rtl8192cu-fixes
[sudo] password for gigi: 
Error! DKMS tree already contains: 8192cu-1.9
You cannot add the same module/version combo more than once.
gigi@Ubuntu-User:~$ sudo dkms install 8192cu/1.9

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.13.0-44-generic -C /lib/modules/3.13.0-44-generic/build M=/var/lib/dkms/8192cu/1.9/build........
cleaning build area....

DKMS: build completed.

8192cu.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-44-generic/updates/dkms/

depmod....

Backing up initrd.img-3.13.0-44-generic to /boot/initrd.img-3.13.0-44-generic.old-dkms
Making new initrd.img-3.13.0-44-generic
(If next boot fails, revert to initrd.img-3.13.0-44-generic.old-dkms image)
update-initramfs......

DKMS: install completed.
gigi@Ubuntu-User:~$ sudo depmod -a

---

### Post by chili555 on 2015-01-18
So now does it load?```
sudo modprobe 8192cu
```

---

### Post by LoLaccount.01 on 2015-01-18
> **chili555 said:**
> So now does it load?```
sudo modprobe 8192cu
```

nothing really happened when i sudo modprove 8192cu

---

### Post by chili555 on 2015-01-18
> **LoLaccount.01 said:**
> nothing really happened when i sudo modprove 8192cuExcellent! It didn't complain that the module wasn't found! Now how about:```
iwconfig
sudo iwlist wlan0 scan
```

---

### Post by LoLaccount.01 on 2015-01-18
gigi@Ubuntu-User:~$ sudo modprobe 8192cu
[sudo] password for gigi: 
gigi@Ubuntu-User:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

gigi@Ubuntu-User:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

gigi@Ubuntu-User:~$

i do have my USB wireless unplugged

---

### Post by chili555 on 2015-01-18
> i do have my USB wireless unpluggedDon't you think it makes it very hard to get working if it isn't even plugged in?

---

### Post by LoLaccount.01 on 2015-01-18
> **chili555 said:**
> Don't you think it makes it very hard to get working if it isn't even plugged in?

:lol: 

here's what i got with the device plug in 

gigi@Ubuntu-User:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gigi@Ubuntu-User:~$ sudo iwlist wlan0 scan
wlan0     No scan results

Wicd wireless manager now has list of wifi. I'll see if i can stay connected longer this time :D thanks for helping me out really apriciate the help from you! i will post back again if i ran into some trouble with this one.

---

### Post by LoLaccount.01 on 2015-01-18
can i get a quick answer on what fixed this issue?

---

### Post by chili555 on 2015-01-19
Someone determined what caused or rather cured instability in your driver rtl8192cu and we installed it. It is a relatively well-known fix. As you saw, I posted it and it was accepted elsewhere previously.

Glad it's working.

---

### Post by Jim_Ormsby on 2015-12-11
Hi;
Short version of my question: Does the above procedure work for ubuntu 15.10 as well as the original posters earlier version?

Background: I had 14.04, installed the Edimax EW-7811Un as the original poster had. Similar problem occurred: it dropped after about 5 minutes.  In the ensuing efforts to fix the problem, I royally toasted the OS, and ended up going to 15.10.  The hardware operates but only for about 5-10 minutes, so I have the same problem again.  I am a novice at this, and know just more than enough to get myself in trouble!!
Thanks.

---

### Post by chili555 on 2015-12-11
>  Does the above procedure work for ubuntu 15.10I hope I am not seen as too blunt, but we don't know if it works for 15.10 as we don't have the device. You have the device and are the best suited to try it and report.

I think the process that is likely to have a slightly better chance of success is this: [http://askubuntu.com/questions/625987/does-tp-link-wn822n-work-on-ubuntu/625989#625989](http://askubuntu.com/questions/625987/does-tp-link-wn822n-work-on-ubuntu/625989#625989)

---

### Post by Jim_Ormsby on 2015-12-11
No, you are not too blunt.  Sometimes that's what it takes to get through to me  <grin>
I'll give that process a shot.  I was only hoping to find out if anyone knew that it wouldn't work with 15.10 and save me the fun and aggravation of reloading the OS again.
Thanks,

---

### Post by chili555 on 2015-12-11
> **Jim_Ormsby said:**
> No, you are not too blunt.  Sometimes that's what it takes to get through to me  <grin>
I'll give that process a shot.  I was only hoping to find out if anyone knew that it wouldn't work with 15.10 and save me the fun and aggravation of reloading the OS again.
Thanks,I'd try the process I linked. If it doesn't work, it is easy to uninstall.

---

### Post by Jim_Ormsby on 2015-12-11
I used the below procedure from the referenced page, and the ubuntu now doesn't even complete a powerup.  Note that this was the only change I made to the system after installing 15.10.  I"m re-installing the system.
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware

---

### Post by chili555 on 2015-12-11
Then something else is wrong. What happens, exactly, when it "doesn't even complete a powerup"? Does it come to a blank screen with a flashing cursor? Or what exactly?

EDIT: I just installed it on my own system and rebooted. I have no trouble at all.

---

### Post by Jim_Ormsby on 2015-12-11
I get that reddish screen for a few moments, then it goes blank; there is no further disk activity, and the monitor displays a loss of signal message.  No cursor ever appeared.
I have reloaded the OS from disk, and will be trying something else.
The wireless is working for the moment; I'll wait to see how long.

---

### Post by Jim_Ormsby on 2015-12-11
I just used the earlier process in the thread, as follows:
sudo apt-get install git
git clone [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
cd rtlwifi_new
make
sudo make install

It lasted about 15 minutes before failing.
I can regain the connection by suspending, or rebooting.

---

### Post by Jim_Ormsby on 2015-12-11
Further experiment:
I changed managed from "false" to "true" in /etc/NetworkManager.conf.
This time, instead of a suspend, I rebooted.
The reboot hung up as before.
Reloading the OS again...  (getting comfortable doing that!)
I wonder, but am not nearly knowledgeable enough to know, if something changed in 15.10 that causes the hangup?

---

### Post by chili555 on 2015-12-11
I'm stumped. This is the first such case I've seen. As I said, I installed it on this very machine with no ill effect whatever.

When you reinstall and before you apply the rtlwifi_new fix, are there any interesting clues in the logs?```
dmesg | grep -i error
dmesg | grep -i warn
cat /var/log/Xorg.0.log | grep EE
```

---

### Post by Jim_Ormsby on 2015-12-11
Here are the results. I ran the commands before doing anything after the re-install.
Looks like Klingon to me.  Do you see clue?  I had to enter it via keyboard on a second computer; I hope there are no typos.
Thanks for looking at this by the way.  Without you type guys, I'd be sinking!


[SIZE=1]dmesg | grep -i error[/SIZE]
 [SIZE=1][  4.786546]  EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro[/SIZE]
 [SIZE=1]dmesg | grep -i warn[/SIZE]
 [SIZE=1][   0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20150619/tbfadt-654)[/SIZE]
 [SIZE=1]cat /var/log/Xorg.0.log | grep EE[/SIZE]
 [SIZE=1]	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.[/SIZE]
 [SIZE=1][     13.252] (EE) Failed to load module &#8220;fglrx&#8221; (module does not exist, 0)[/SIZE]
 [SIZE=1][     13.295] (EE) Failed to load module &#8220;fglrx&#8221; (module does not exist, 0)[/SIZE]
 [SIZE=1][     37829]  (II] XKB: generating xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm[/SIZE]

---

### Post by chili555 on 2015-12-12
> (EE) Failed to load module “fglrx” (module does not exist, 0)*fglrx* is a video driver. With no driver or a faulty driver, there is no video or garbled video.

Sound familiar?

Video is really outside my limited capability. All I know is that on my four Ubuntu computers, it just works.

I suggest you ask here: [http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332) I continue to believe that the problem is not wireless.

---

### Post by praseodym on 2015-12-12
Lets check the VGA card(s):
```

lspci -nnk | grep VGA
lsmod
cat /etc/X11/xorg.conf
```

---

### Post by Jim_Ormsby on 2015-12-12
Well, even with those video driver errors, the video works very nicely.
I'm using an ASUS hdmi monitor, and didn't add any drivers.  Just the standard ubuntu 15.10 software.

I readily admit I don't know much about what I am doing, but I don't see a connection between the monitor and the wireless problem.  True, a couple attempted fixes blanked the monitor, but the hard drive also wasn't being accessed normally, so I would think that perhaps maybe the attempted wireless fixes somehow interrupted the bootup process.  And of course, the wireless ceases to communicate after about 10 minutes, even though the wireless tool (accessed at the top bar) seems to indicate that it is still connected.

Here are the results of the suggested commands:

Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
arc4                   16384  2
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              733184  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              548864  2 mac80211,rtlwifi
joydev                 20480  0
input_leds             16384  0
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
kvm_amd                65536  0
video                  36864  1 asus_wmi
kvm                   512000  1 kvm_amd
snd_hda_codec_realtek    86016  1
snd_hda_codec_hdmi     49152  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
ghash_clmulni_intel    16384  0
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
aesni_intel           167936  2
aes_x86_64             20480  1 aesni_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
snd_seq_midi           16384  0
ablk_helper            16384  1 aesni_intel
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
k10temp                16384  0
shpchp                 36864  0
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw              16384  0
soundcore              16384  1 snd
8250_fintek            16384  0
i2c_piix4              24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
pata_acpi              16384  0
hid_logitech_hidpp     20480  0
hid_logitech_dj        20480  0
usbhid                 49152  0
hid                   118784  5 usbhid,hid_logitech_dj,hid_logitech_hidpp
amdkfd                122880  1
amd_iommu_v2           20480  1 amdkfd
radeon               1519616  4
psmouse               126976  0
i2c_algo_bit           16384  1 radeon
r8169                  81920  0
ttm                    94208  1 radeon
mii                    16384  1 r8169
drm_kms_helper        126976  1 radeon
pata_atiixp            16384  0
ahci                   36864  2
drm                   356352  7 ttm,drm_kms_helper,radeon
libahci                32768  1 ahci
wmi                    20480  1 asus_wmi

cat:  /etc/X11/Xorg.conf:  no such file or directory

---

### Post by praseodym on 2015-12-13
Change the driver completely:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.10
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot

---

### Post by chili555 on 2015-12-13
He has tried that already. Every time, his computer refuses to reboot.

---

### Post by Jim_Ormsby on 2015-12-13
HI
The first command came up with an error "Couldn't find any package by regex 'https://github.com/pvaret'
I tried it without the double "git" in the middle; same result
tried it without the last ".git" at the end; same result
I can see the website [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes), and it lists a number of directories/files.

Is something wrong with the command?

---

### Post by chili555 on 2015-12-13
> **Jim_Ormsby said:**
> HI
The first command came up with an error "Couldn't find any package by regex 'https://github.com/pvaret'
I tried it without the double "git" in the middle; same result
tried it without the last ".git" at the end; same result
I can see the website [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes), and it lists a number of directories/files.

Is something wrong with the command?You evidently have a space in the command, like this:```
git clone https://github.com/pvaret/  rtl8192cu-fixes.git
```It is, instead:```
git clone https://github.com/pvaret/rtl8192cu-fixes.git
```Please retrace your steps and try again.

I just ran the command on my own machine and it runs correctly:> chili@T410:~$ git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
Cloning into 'rtl8192cu-fixes'...
remote: Counting objects: 435, done.
remote: Total 435 (delta 0), reused 0 (delta 0), pack-reused 435
Receiving objects: 100% (435/435), 1.79 MiB | 670.00 KiB/s, done.
Resolving deltas: 100% (222/222), done.
Checking connectivity... done.


---

### Post by Jim_Ormsby on 2015-12-13
OK, first real silly brain cramp on my part...
My browser width made the first two lines look like one command, hence the "git git" question.
Slightly chagrined, I ran them correctly.
Rebooted, and the wireless doesn't come up at all. It is editable in the wireless tool, and all looks OK.  Just no connection, and the wireless icon shows no communication.  I had that result with one of the earlier attempts.

At this point, does anyone have a strong recommendation of another USB wireless device that works without the hassle.
I'm beginning to thing there must be something different about the combination of motherboard and the 7811 that just isn't apparent. And while this is somewhat interesting, it is winter in western Wyoming and I have to get back to getting firewood.

---

### Post by chili555 on 2015-12-13
I have and use a TPLink WN-722N that simply plugs in and connects. Sorry we couldn't solve the case for you.

[http://www.amazon.com/TP-LINK-TL-WN722N-Wireless-Adapter-External/dp/B002SZEOLG](http://www.amazon.com/TP-LINK-TL-WN722N-Wireless-Adapter-External/dp/B002SZEOLG)

---

### Post by Jim_Ormsby on 2015-12-13
Thanks for the recommend.  And thanks for all your advice and time.  They are most appreciated!
Jim

---

