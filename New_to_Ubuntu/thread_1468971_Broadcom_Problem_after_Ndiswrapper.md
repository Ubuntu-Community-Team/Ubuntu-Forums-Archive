---
title: "Broadcom Problem after Ndiswrapper"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by mmck5 on 2010-05-01
Okay, so I have been having problems with my wireless for several weeks now and I know I am kind of beating a dead horse here, but the point I am at is that I followed the directions using ndiswrapper from [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) up to point 3.6 in which I have become stuck and cannot find the necessary program. Now, my wireless hardware is not being recognized anywhere and I am simply stuck. I followed all the directions and before my computer restarted it said the device wasn't ready yet.

iwconfig is not registering anything other than lo and eth0 and the ndisgtk says that the hardware is not present. I blacklisted b43, b43xx, b43legacy, and ssb and assume that that is the problem. Any tips would be greatly appreciated! I've only been using linux for a month now this is simply over my head.

---

### Post by lkraemer on 2010-05-01
What Version of Ubuntu?  32 Bit or 64 Bit?

Open a Terminal Window and use these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted.  You MUST use the
Proper Windows brivers for 32 or 64 Bit to match the 32 or 64 Bit 
Version of Ubuntu.  You need the .inf and .sys files.......

Use copy & paste to prevent typos!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf 
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Post the output of each command listed above ........

Your options that can be used:
1. Ndiswrapper and a Windows Driver....bcmwl5.inf & sys
2. bcm43xx module and some Firmware.... B43 & B43legacy *.fw
3. b43 and some Firmware that was downloaded/extracted when you
enabled the Driver.


To install the Windows Drivers you did something like this:
I'll assume broadcom.......just for a change.....
```

cd ~/Desktop/broadcom
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
lsmod
ifconfig
iwconfig

```
To make sure it starts on boot:
```

echo ndiswrapper | sudo tee -a /etc/modules

```
If you want to REMOVE the Windows Drivers:...............
If the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. If memory serves me correctly the command is:
```

sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -e ssb

```
This should clean up nidswrapper & drivers and:
```

ndiswrapper -l

```
should return nothing as being loaded.

Then remove ndiswrapper:
```

sudo modprobe -r ndiswrapper

```
Remove from startup file by editing:
```

sudo nano /etc/modules

```
to remove ndiswrapper.

Open a Terminal & Check for errors:
```

dmesg tail
lsmod

```
You may have to remove other modules depending on what lsmod shows:......example only.....
What you will REMOVE depends on what you post as output from your commands.

If lsmod shows module b43 and others installed you will
need to blacklist them, since you are going to be using ndiswrapper.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```
You can use sudo gedit /etc/modprobe.d/blacklist.conf
and add the necessary modules to blacklist.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
Post the output of iwconfig above.

lk

---

### Post by mmck5 on 2010-05-01
[SIZE=1]Thanks for the time! Here are the results:

> [/SIZE]    [SIZE=1]mackenzie@mackenzie-laptop:~$ lspci[/SIZE]
    [SIZE=1]00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)[/SIZE]
    [SIZE=1]00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)[/SIZE]
    [SIZE=1]00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)[/SIZE]
    [SIZE=1]00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)[/SIZE]
    [SIZE=1]00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)[/SIZE]
    [SIZE=1]00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)[/SIZE]
    [SIZE=1]00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)[/SIZE]
    [SIZE=1]00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)[/SIZE]
    [SIZE=1]00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)[/SIZE]
    [SIZE=1]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)[/SIZE]
    [SIZE=1]00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)[/SIZE]
    [SIZE=1]00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)[/SIZE]
    [SIZE=1]00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)[/SIZE]
    [SIZE=1]00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)[/SIZE]
    [SIZE=1]00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)[/SIZE]
    [SIZE=1]02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)[/SIZE]
    [SIZE=1]02:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)[/SIZE]
    [SIZE=1]02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)[/SIZE]
    [SIZE=1]mackenzie@mackenzie-laptop:~$ lsusb[/SIZE]
    [SIZE=1]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE]
    [SIZE=1]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE]
    [SIZE=1]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE]
    [SIZE=1]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE]
    [SIZE=1]mackenzie@mackenzie-laptop:~$ lshw -C network[/SIZE]
    [SIZE=1]WARNING: you should run this program as super-user.[/SIZE]
    [SIZE=1]  *-network:0             [/SIZE]
    [SIZE=1]       description: Ethernet interface[/SIZE]
    [SIZE=1]       product: RTL-8139/8139C/8139C+[/SIZE]
    [SIZE=1]       vendor: Realtek Semiconductor Co., Ltd.[/SIZE]
    [SIZE=1]       physical id: 0[/SIZE]
    [SIZE=1]       bus info: pci@0000:02:00.0[/SIZE]
    [SIZE=1]       logical name: eth0[/SIZE]
    [SIZE=1]       version: 10[/SIZE]
    [SIZE=1]       serial: 00:c0:9f:5b:da:27[/SIZE]
    [SIZE=1]       width: 32 bits[/SIZE]
    [SIZE=1]       clock: 33MHz[/SIZE]
    [SIZE=1]       capabilities: bus_master cap_list ethernet physical[/SIZE]
    [SIZE=1]       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes[/SIZE]
    [SIZE=1]       resources: irq:10 ioport:3000(size=256) memory:e0202000-e02020ff[/SIZE]
    [SIZE=1]  *-network:1[/SIZE]
    [SIZE=1]       description: Network controller[/SIZE]
    [SIZE=1]       product: BCM4306 802.11b/g Wireless LAN Controller[/SIZE]
    [SIZE=1]       vendor: Broadcom Corporation[/SIZE]
    [SIZE=1]       physical id: 6[/SIZE]
    [SIZE=1]       bus info: pci@0000:02:06.0[/SIZE]
    [SIZE=1]       version: 03[/SIZE]
    [SIZE=1]       width: 32 bits[/SIZE]
    [SIZE=1]       clock: 33MHz[/SIZE]
    [SIZE=1]       capabilities: bus_master[/SIZE]
    [SIZE=1]       configuration: driver=b43-pci-bridge latency=64[/SIZE]
    [SIZE=1]       resources: irq:11 memory:e0200000-e0201fff[/SIZE]
    [SIZE=1]mackenzie@mackenzie-laptop:~$ lsmod[/SIZE]
    [SIZE=1]Module                  Size  Used by[/SIZE]
    [SIZE=1]binfmt_misc             8356  1 [/SIZE]
    [SIZE=1]ndiswrapper           185404  0 [/SIZE]
    [SIZE=1]ppdev                   6688  0 [/SIZE]
    [SIZE=1]lp                      8964  0 [/SIZE]
    [SIZE=1]parport                35340  2 ppdev,lp[/SIZE]
    [SIZE=1]joydev                 10272  0 [/SIZE]
    [SIZE=1]pcmcia                 36808  0 [/SIZE]
    [SIZE=1]snd_intel8x0           30168  2 [/SIZE]
    [SIZE=1]snd_ac97_codec        101216  1 snd_intel8x0[/SIZE]
    [SIZE=1]ac97_bus                1532  1 snd_ac97_codec[/SIZE]
    [SIZE=1]snd_pcm_oss            37920  0 [/SIZE]
    [SIZE=1]yenta_socket           24200  1 [/SIZE]
    [SIZE=1]psmouse                56180  0 [/SIZE]
    [SIZE=1]snd_mixer_oss          16028  1 snd_pcm_oss[/SIZE]
    [SIZE=1]rsrc_nonstatic         11644  1 yenta_socket[/SIZE]
    [SIZE=1]serio_raw               5280  0 [/SIZE]
    [SIZE=1]snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss[/SIZE]
    [SIZE=1]pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic[/SIZE]
    [SIZE=1]snd_seq_dummy           2656  0 [/SIZE]
    [SIZE=1]shpchp                 32272  0 [/SIZE]
    [SIZE=1]iptable_filter          3100  0 [/SIZE]
    [SIZE=1]snd_seq_oss            28576  0 [/SIZE]
    [SIZE=1]ip_tables              11692  1 iptable_filter[/SIZE]
    [SIZE=1]x_tables               16544  1 ip_tables[/SIZE]
    [SIZE=1]snd_seq_midi            6432  0 [/SIZE]
    [SIZE=1]snd_rawmidi            22208  1 snd_seq_midi[/SIZE]
    [SIZE=1]snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi[/SIZE]
    [SIZE=1]snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event[/SIZE]
    [SIZE=1]snd_timer              22276  2 snd_pcm,snd_seq[/SIZE]
    [SIZE=1]snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq[/SIZE]
    [SIZE=1]snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/SIZE]
    [SIZE=1]soundcore               7264  1 snd[/SIZE]
    [SIZE=1]snd_page_alloc          9156  2 snd_intel8x0,snd_pcm[/SIZE]
    [SIZE=1]fbcon                  36640  72 [/SIZE]
    [SIZE=1]tileblit                2460  1 fbcon[/SIZE]
    [SIZE=1]font                    8124  1 fbcon[/SIZE]
    [SIZE=1]bitblit                 5372  1 fbcon[/SIZE]
    [SIZE=1]softcursor              1756  1 bitblit[/SIZE]
    [SIZE=1]8139too                22620  0 [/SIZE]
    [SIZE=1]8139cp                 19260  0 [/SIZE]
    [SIZE=1]mii                     5212  2 8139too,8139cp[/SIZE]
    [SIZE=1]ssb                    35300  0 [/SIZE]
    [SIZE=1]i915                  221064  2 [/SIZE]
    [SIZE=1]drm                   159584  2 i915[/SIZE]
    [SIZE=1]i2c_algo_bit            5760  1 i915[/SIZE]
    [SIZE=1]intel_agp              27484  2 i915[/SIZE]
    [SIZE=1]agpgart                34988  2 drm,intel_agp[/SIZE]
    [SIZE=1]video                  19380  1 i915[/SIZE]
    [SIZE=1]output                  2780  1 video[/SIZE]
    [SIZE=1]mackenzie@mackenzie-laptop:~$ ndiswrapper -l[/SIZE]
    [SIZE=1]oem3 : driver installed[/SIZE]
    [SIZE=1]mackenzie@mackenzie-laptop:~$ cat /etc/modprobe.d/blacklist.conf[/SIZE]
    [SIZE=1]# This file lists those modules which we don't want to be loaded by[/SIZE]
    [SIZE=1]# alias expansion, usually so some other driver will be loaded for the[/SIZE]
    [SIZE=1]# device instead.[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# evbug is a debug tool that should be loaded explicitly[/SIZE]
    [SIZE=1]blacklist evbug[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# these drivers are very simple, the HID drivers are usually preferred[/SIZE]
    [SIZE=1]blacklist usbmouse[/SIZE]
    [SIZE=1]blacklist usbkbd[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# replaced by e100[/SIZE]
    [SIZE=1]blacklist eepro100[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# replaced by tulip[/SIZE]
    [SIZE=1]blacklist de4x5[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# causes no end of confusion by creating unexpected network interfaces[/SIZE]
    [SIZE=1]blacklist eth1394[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much[/SIZE]
    [SIZE=1]# hardware on its own (Ubuntu bug #2011, #6810)[/SIZE]
    [SIZE=1]blacklist snd_intel8x0m[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# Conflicts with dvb driver (which is better for handling this device)[/SIZE]
    [SIZE=1]blacklist snd_aw2[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)[/SIZE]
    [SIZE=1]blacklist i2c_i801[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# replaced by p54pci[/SIZE]
    [SIZE=1]blacklist prism54[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# replaced by b43 and ssb.[/SIZE]
    [SIZE=1]blacklist bcm43xx[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# most apps now use garmin usb driver directly (Ubuntu: #114565)[/SIZE]
    [SIZE=1]blacklist garmin_gps[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# replaced by asus-laptop (Ubuntu: #184721)[/SIZE]
    [SIZE=1]blacklist asus_acpi[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# low-quality, just noise when being used for sound playback, causes[/SIZE]
    [SIZE=1]# hangs at desktop session start (Ubuntu: #246969)[/SIZE]
    [SIZE=1]blacklist snd_pcsp[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# ugly and loud noise, getting on everyone's nerves; this should be done by a[/SIZE]
    [SIZE=1]# nice pulseaudio bing (Ubuntu: #77010)[/SIZE]
    [SIZE=1]blacklist pcspkr[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]# EDAC driver for amd76x clashes with the agp driver preventing the aperture[/SIZE]
    [SIZE=1]# from being initialised (Ubuntu: #297750). Blacklist so that the driver[/SIZE]
    [SIZE=1]# continues to build and is installable for the few cases where its[/SIZE]
    [SIZE=1]# really needed.[/SIZE]
    [SIZE=1]blacklist amd76x_edac[/SIZE]
    [SIZE=1]blacklist b43[/SIZE]
    [SIZE=1]blacklist ssb[/SIZE]
    [SIZE=1]blacklist b43legacy[/SIZE]
    [SIZE=1]mackenzie@mackenzie-laptop:~$ iwconfig[/SIZE]
    [SIZE=1]lo        no wireless extensions.[/SIZE]
    [SIZE=1] [/SIZE]
  [SIZE=1] [/SIZE]
  [SIZE=1]eth0      no wireless extensions.[/SIZE]
    [SIZE=1]


What I don't get is that there is clearly the broadcom device, but my OS is not recognizing it as such.
[/SIZE]

---

### Post by anewguy on 2010-05-02
Do you have access to hard-wire the PC to the router temporarily?  If so, do the following:

- reverse all of the changes you made to blacklist.conf -> you can put a # in the front of those blacklist entries you added to accomplish this or you can just remove them.

- remove ndiswrapper

- open a terminal window and type:

sudo apt-get update

- now unplug the hard-wire connection

- look in System/Administration/Hardware Drivers and see if there is a driver listed there for your wireless -> is so, enable it.

- check in network manager (right click on the icon) to be sure the "Enable Wireless" box is checked

- wait a couple of minutes, then check to see if you have wireless now

If not, post back and we'll go from there.

Dave ;)

---

### Post by mmck5 on 2010-05-02
I've done that before. The problem is that when I did it the internet would work for a week or so and then it would shut off for a week. I could never figure out why.

---

### Post by anewguy on 2010-05-02
If it works at all, then the driver would be working.

If it were me, I would do as I mentioned above, except I would reboot and then test the wireless as there are some modules that need to get unloaded.

Once you've done that and have your wireless working again, then post back with a new thread (Something like "wireless quit working" or some such thing) if/when your wireless stops again (just use a hard wire connection to do so).  If/when you do, also post back the output of:

lshw -C network

and possibly:

dmesg | tail


The thing to do now is get your wireless working with the restricted driver again, then IF you have problems later post again.

Dave ;)

---

### Post by lkraemer on 2010-05-02
OK, Let's reverse what you did

If you want to REMOVE the Windows Drivers:...............
If the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. If memory serves me correctly the command is:
```

sudo ndiswrapper -e oem3

```

This should clean up nidswrapper & drivers and:
```

ndiswrapper -l

```
should return nothing as being loaded.  If not keep removing
what is shown as a loaded driver.

Then remove ndiswrapper:
```

sudo modprobe -r ndiswrapper

```
Remove from startup file by editing:
```

sudo nano /etc/modules

```
to remove ndiswrapper.

Then REMOVE the following from your Blacklist file, by deleting the
last three lines in that file as I previously posted.


To Blacklist a driver you had to edit the file at:
/etc/modprobe.d/blacklist.conf

In that file you added some filename for the driver that needed to be
blacklisted, or you removed the "#" at the beginning of the line.

Just go back and edit the file with gedit or nano and reverse what
you previously did for the files below:

blacklist b43
blacklist ssb
blacklist b43legacy
mackenzie@mackenzie-laptop:~$ iwconfig

Post the output of lsmod and ndiswrapper -l


For Refernece:
You can see a list of the previous history commands with the
following command in a terminal window: (cut and paste to prevent typos)
```

history
[/code
If you want to pipe those commands to a file use......
[code]
history > histfile.txt

```
Post the output of histfile.txt also........

Then you will need to reboot for the changes to take effect or try:
```

sudo /etc/init.d/networking restart

```

Download the attached Firmware and unzip it to your Desktop.
There thould be two folders b43 & b43legacy.

You will need to download the Firmware, or have your
computer connected to the internet via ethernet when you enable
the Hardware Drivers. The Firmware is installed at /lib/firmware
as folders /b43 and /b43legacy. Open a Terminal window and do the
following commands (cut and paste one at a time):
```

cd /
pwd
cd /lib
cd /firmware
ls -alt
pwd
sudo cp -r /home/loginname/Desktop/b43* .
cd /b43
pwd
ls -alt

```
(You are looking for any *.fw files in /lib/firmware/b43 or
/lib/firmware/b43legacy and if you had a Wired LAN connection and
went to SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS and enabled the
Hardware Drivers with a LAN connection there should have been folders
created and files inserted for the Restricted Drivers to work.)

Now do as Dave is suggesting:
- look in System/Administration/Hardware Drivers and see if there is a driver listed there for your wireless -> is so, enable it.  (It should show B43 and if by chance you have already tried that go ahead and let it try to uninstall,
then install it again by clicking again.  It should find the drivers and load them.

- check in network manager (right click on the icon) to be sure the "Enable Wireless" box is checked (It should be
ENABLED already by default.)

- wait a couple of minutes, then check to see if you have wireless now

AHhhhhh......Now how tough was that.  Took me about 10 minutes on my Compaq V5201US and I finished this post with it.

That should get you going because it did just that when I booted Ubuntu 10.04 on my Compaq V5201US with Broadcom Wifi

lk

---

### Post by 1915flyer on 2010-05-02
I have a Linksys wireless pcmcia card with the Broadcom b43 chip.

bcm43-fwcutter available in through Synaptic works for me. I had to get it with a hardwired connection though. 

Unfortunately, I had to spend about 1 hour looking for the ethernet card.:(

---

### Post by anewguy on 2010-05-03
The firmware cutter is available on the LiveCd you installed from, at:

/pool/main/b

The build-essential package is also in that same folder.


Dave ;)

---

