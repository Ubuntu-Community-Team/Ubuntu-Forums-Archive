---
title: "Can't get wired internet to work"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by thetwobob on 2011-05-18
Hello, I recently installed the latest version of Ubuntu as the sole OS on my Dell Dimension 8300 desktop and haven't been able to connect to the internet on it. When I go to Network Connections it shows "Auto eth0" as being last used "now" but it's not working.

When i run "ifconfig" in the terminal, it gives me this:

```
eth0      Link encap:Ethernet  HWaddr 00:07:e9:43:fd:d1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18032 (18.0 KB)  TX bytes:18032 (18.0 KB)
```

---

### Post by PowerBarry43 on 2011-05-18
Hi

can you run lspci in the terminal and post that too please :)

also this may sound a bit obvious but have you enabled networking in the menu you get when you click on the networking icon in the system tray and have you tried wireless?

---

### Post by PowerBarry43 on 2011-05-18
you might also want to try installing additional drivers in system/administration/additional drivers

hope this helped

Barry

---

### Post by thetwobob on 2011-05-18
@PowerBarry43: Thanks for your response. Yes, there is a check next to "Enable Networking" so that shouldn't be the problem. This computer used to run windows xp and I was always connected using a cable and never had wireless on it.

This is what I get when I use the lspci command:

```
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:01.0 Communication controller: Conexant Systems, Inc. Device 2702 (rev 01)
02:02.0 PCI bridge: Texas Instruments PCI2050 PCI-to-PCI Bridge (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
03:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:06.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)

```
I also tried installing additional drivers and it said: "No proprietary drivers are in use on this system."

---

### Post by jtarin on 2011-05-18
Now post the result from the command "lsmod"
Or look at the results and see if you have an "e100" module loaded.
Are you connecting with ADSL? Do you have pppoe configured?

---

### Post by PowerBarry43 on 2011-05-18
ok i think this is a common problem with your computer ive found this thread ([http://ubuntuforums.org/showthread.php?t=1696825](http://ubuntuforums.org/showthread.php?t=1696825)) that explains how to activate the network card on a dell dimension 8300 when using ubuntu from the terminal

they say you have to type in the terminal

```
gksudo gedit /etc/network/interfaces
```

to edit the interfaces file

then add

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

to the interfaces file

hopefully that should sort it out :)

---

### Post by thetwobob on 2011-05-18
Here are the results from the command "lsmod":

```
Module                  Size  Used by
nls_utf8               12493  1 
udf                    83795  1 
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  178 
aes_generic            38023  1 aes_i586
dm_crypt               22463  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
binfmt_misc            13213  1 
snd_rawmidi            25269  1 snd_seq_midi
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
dcdbas                 14054  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32111  1 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
nouveau               621970  2 
ttm                    65184  1 nouveau
usbhid                 41704  0 
drm_kms_helper         40745  1 nouveau
drm                   180037  4 nouveau,ttm,drm_kms_helper
usb_storage            43946  0 
firewire_ohci          31504  0 
hid                    77084  1 usbhid
floppy                 60032  0 
e100                   40108  0 
firewire_core          56138  1 firewire_ohci
uas                    17676  0 
crc_itu_t              12627  2 udf,firewire_core
i2c_algo_bit           13184  1 nouveau
video                  18951  1 nouveau

```
I get my internet through a dish, but I'm not sure what pppoe is.

---

### Post by thetwobob on 2011-05-18
> **PowerBarry43 said:**
> 

```
gksudo gedit /etc/network/interfaces
```to edit the interfaces file

then add

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

to the interfaces file

hopefully that should sort it out :)

I did that and successfully changed the file, but then it gives me this in the terminal:

```
(gedit:2041): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2041): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.19LUVV': No such file or directory

(gedit:2041): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2041): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.UVPLVV': No such file or directory

(gedit:2041): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```Is that not good?

---

### Post by jtarin on 2011-05-18
> **thetwobob said:**
> I did that and successfully changed the file, but then it gives me this in the terminal:

```
(gedit:2041): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2041): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.19LUVV': No such file or directory

(gedit:2041): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2041): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.UVPLVV': No such file or directory

(gedit:2041): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```Is that not good?

This is only showed because you ran this as root.Create the directory in your /root directory, with that path, if these messages annoy you, although it's not necessary.

---

