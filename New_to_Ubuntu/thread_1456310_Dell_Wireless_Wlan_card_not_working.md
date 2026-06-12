---
title: "Dell Wireless Wlan card not working"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by camn on 2010-04-17
It just won't work... Please help me :confused:
Edit: I don't have access to the internet on the computer with Ubuntu, I'm on my Windows computer right now.

---

### Post by anewguy on 2010-04-17
Please do the following:

- open a terminal window by clicking on Applications, then down to Accessories, then over to and click on Terminal

- type:

lspci <press enter>  copy this information and paste it back in a reply here (hopefully you have a USB flash drive or something you can copy it to)

lsusb <press enter>  copy this information and paste it back in a reply here (again, hopefully you have a USB flash drive or something you can copy it to to take it to the Windows machine you are posting from)

lshw -C network <press enter>  Ditto - copy and paste back in a reply.

We need to identify what adapter you have and the chipset it is using before we can direct you to anything helpful.

Dave ;)

---

### Post by undecim on 2010-04-17
The easiest way to get your wireless drivers is to connect to your router with an ethernet cable and use that connection to install wireless drivers from System -> Administration -> Hardware Drivers

If that's not an option, then I need to know your wireless card model number to give you altenrative instructions. You can find out by opening a terminal and pasting this command: ```
lspci | grep Wireless
```

---

### Post by camn on 2010-04-17
lspci gave me this:
 > 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
  00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
  00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
  00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
  00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
  00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
  00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
  00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
  00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
  00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
  00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
  00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
  00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
  00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
  00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
  00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
  00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
  00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
  03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
  03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
  03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
  03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
  03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
  0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
  lsusb gave me this:
> 
   Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 002 Device 002: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
  Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  [FONT=&quot]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]  And finally,   [FONT=&quot]lshw -C network gave me this:
[/FONT]>  
   WARNING: you should run this program as super-user.
  
    *-network               
         description: Network controller
         product: BCM4312 802.11b/g
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:0c:00.0
         version: 01
         width: 64 bits
         clock: 33MHz
         capabilities: bus_master cap_list
         configuration: driver=b43-pci-bridge latency=0
         resources: irq:17 memory:fe8fc000-fe8fffff
    *-network
         description: Ethernet interface
         product: BCM4401-B0 100Base-TX
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:03:00.0
         logical name: eth0
         version: 02
         serial: 00:1d:09:d2:32:c7
         width: 32 bits
         clock: 33MHz
         capabilities: bus_master cap_list ethernet physical
         configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
         resources: irq:17 memory:fe5fe000-fe5fffff


---

### Post by anewguy on 2010-04-17
_EDIT-2_:  I just noticed from the lshw -C network that it is showing b43 as the driver for the wireless.  Check in network manager to be sure you have "enable wireless" checked, then check again to see if you see any networks available.  If not, please do the following in a terminal window and post it back here:

lsmod <press enter>

----- END OF EDIT-2 -----

Ok, from the lspci (which means list all pci devices), we get:

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

This is your wireless.  Check under System/Administration/Hardware Drivers and see if there is a driver listed there and if so enable it.  If that isn't available or it doesn't work, do you have the ability to hard-wire a connection from your PC to the router?  If so, use it and do the following ( I *think* this is what people do to get the "built-in restricted driver):

- open a terminal window again

- type:

sudo apt-get update <press enter>

sudo apt-get upgrade <press enter>

Then check under System/Administration/Hardware Drivers and see if there is a driver listed there, and if so enable it.

If you don't have the ability to access the net via a hard-wired connection, then there is something else we can try as well:

- locate the Windows driver (should be .inf and .sys files for the adapter).  This may come as an .exe and if so you may need to run the exe on your Windows computer just so you can get the files (if so, copy them to a USB stick if you can).  Copy the files to your Ubuntu Desktop folder (~/Desktop).

- place the LiveCD you used to install Ubuntu back in the drive.  Let it "think" a couple of minutes - if it comes up saying a disk with packages has been found and ask if you want to open the package manager, just say no.

- Click on "Places" and then the drive your CD is in

- navigate to the /pool/main/n/ndiswrapper folder on the CD.  You should find 2 files there - 1 for common, the other for utilities.  Double-click these (1 at a time) to install them.

- open a terminal window

- type:

cd Desktop <press enter>

sudo ndiswrapper -i xxxxxxx.inf <press enter> where that's a lower case "I" (for insert) and replacing xxxxxxx.inf with the actual name of your .inf file you put on the desktop

sudo ndiswrapper -l <press enter> where that's a lower case "L" (for list).  Check the output to be sure it shows your driver and says the device is active.

sudo depmod -a <press enter>

sudo gedit /etc/modules <press enter> 

This will call up an editor with the file /etc/modules opened in the window.  Scroll to the bottom of that file and add the following line:

ndiswrapper

Save the file, exit the editor.

sudo gedit /etc/modprobe.d/blacklist.conf <press enter>
This will call up the editor again, this time opening the blacklist.conf file (this file indicates what modules NOT to load on boot).  Scroll to the end of the file and add the following lines:

blacklist b43
blacklist b43-legacy
blacklist ssb

Save the file, exit the editor.

Now, reboot.  After the boot, look in network manager and see if your wireless is showing (you may have to click on "enable wireless" in network manager first).

Dave ;)

EDIT:  Additions:

(1) you may need to add "blacklist bcm43xx" to the blacklist.conf file as well.

(2) be sure you unplug your network cable from the PC (if you can hard-wire a connection to the router) before you try wireless again.  While it may be possible (I don't know), I've never had any luck getting both running at the same time.

---

### Post by unmole on 2010-04-17
**_Ultra Easy Way_**

1) Download [this installer .]("http://docs.google.com/leaf?id=0B73yM4iNvLLlZDM3MThhZDctZjYyOC00NGZhLTlkMjUtZDczZGJmZmMwMTYx&hl=en") using Windows and copy it to a pen drive.

2) Boot into Ubuntu, insert the pendrive and extract the archive it and open the resulting folder.

3) Double Click on install.sh and choose "Run in Terminal"

4)Follow on screen instructions.

5)Done!

P.S. When you are asked for your password, the password will not be displayed on screen.

---

### Post by warfacegod on 2010-04-17
Check to see if your getting any wireless signals:

```
sudo iwlist scanning
```

If you are then your wireless card probably isn't the issue.

---

### Post by camn on 2010-04-17
What unmole said worked... Thanks :D

---

### Post by anewguy on 2010-04-17
unmole, I didn't know that existed - did you create it?  Either way around it's a much simpler way of doing things.

Thanks!
Dave ;)

---

### Post by camn on 2010-04-17
Oh wait, I had to re-install Ubuntu and now unmole's thing isn't working...

---

### Post by camn on 2010-04-17
Ok, lsmod gave me:
```

   Module                  Size  Used by
  nls_iso8859_1           5280  1 
  nls_cp437               6976  1 
  vfat                   13184  1 
  fat                    59832  1 vfat
  binfmt_misc            10220  1 
  ppdev                   8232  0 
  snd_hda_codec_idt      72976  1 
  snd_hda_intel          31880  2 
  snd_hda_codec          87584  2 snd_hda_codec_idt,snd_hda_intel
  snd_hwdep               9352  1 snd_hda_codec
  joydev                 13088  0 
  snd_pcm_oss            44704  0 
  snd_mixer_oss          18976  1 snd_pcm_oss
  snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
  snd_seq_dummy           3460  0 
  snd_seq_oss            33440  0 
  b43                   136552  0 
  snd_seq_midi            8192  0 
  ricoh_mmc               4480  0 
  iptable_filter          3872  0 
  dell_wmi                3216  0 
  ip_tables              21200  1 iptable_filter
  x_tables               25832  1 ip_tables
  snd_rawmidi            27360  1 snd_seq_midi
  snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
  snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
  sdhci_pci               8928  0 
  sdhci                  20484  1 sdhci_pci
  lp                     11908  0 
  parport                40528  2 ppdev,lp
  dell_laptop             9692  0 
  dcdbas                  9136  1 dell_laptop
  psmouse                57124  0 
  serio_raw               6596  0 
  mac80211              210104  1 b43
  cfg80211              109144  2 b43,mac80211
  led_class               5256  2 b43,sdhci
  snd_timer              26992  2 snd_pcm,snd_seq
  snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
  snd                    77096  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
  soundcore               9088  1 snd
  snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
  b44                    34352  0 
  fbcon                  41344  72 
  tileblit                3136  1 fbcon
  font                    8832  1 fbcon
  bitblit                 6688  1 fbcon
  softcursor              2336  1 bitblit
  usb_storage            65952  1 
  ssb                    40944  2 b43,b44
  mii                     6368  1 b44
  ohci1394               33780  0 
  ieee1394              100896  1 ohci1394
  i915                  246984  3 
  drm                   193856  3 i915
  i2c_algo_bit            7076  1 i915
  intel_agp              32816  2 i915
  video                  23612  1 i915
  output                  3680  1 video

```

---

### Post by anewguy on 2010-04-17
Well, the lsmod shows the b44 module loaded, but not the b43 module.  Try this in a terminal window:

sudo modprobe b43 <press enter>

sudo rmmod b44 <press enter>

Wait a little bit then check to see if the "enable wireless" option is clicked in network manager since you did your reinstall, then check to see if any wireless networks show.

Post back with anything that happens.

Dave ;)

---

### Post by camn on 2010-04-17
Neither sudo modprobe b43 or sudo rmmod b44 did anything.
EDIT: Found a way to hardwire it but that didn't work to get me on the internet either ._.

---

### Post by newbielawl on 2010-04-17
> **unmole said:**
> **_Ultra Easy Way_**

1) Download [this installer .]("http://docs.google.com/leaf?id=0B73yM4iNvLLlZDM3MThhZDctZjYyOC00NGZhLTlkMjUtZDczZGJmZmMwMTYx&hl=en") using Windows and copy it to a pen drive.

2) Boot into Ubuntu, insert the pendrive and extract the archive it and open the resulting folder.

3) Double Click on install.sh and choose "Run in Terminal"

4)Follow on screen instructions.

5)Done!

P.S. When you are asked for your password, the password will not be displayed on screen.

You da man! :)  worked great!  Thanks!:guitar:

---

### Post by camn on 2010-04-17
> **newbielawl said:**
> You da man! :)  worked great!  Thanks!:guitar:
Umm... I guess I should re-re-install Ubuntu to see if it didn't install all the way or something... Hardwiring it didn't work to get me on the internet either.
EDIT: Re-re-installing worked... Turns out I used the wrong Ubuntu disk xD

---

### Post by unmole on 2010-04-22
Good to know my installer helped you guys out.

P.S. This works not just for Dell but for any Broadcom WiFi card supported by the STA driver.

---

### Post by Quantum Paradox on 2011-02-24
I have the same card and I am using wubi with unbuntu/windows 7. I followed the steps and downloaded the package but it did not work for me =[ can anyone else help me? I really really really want to be using ubuntu and using windows 7 when needed for school computer classes. or possible just unbuntu if i can figure out how to get the internet working! 

pretty please help me!!!!!!!!!!!!! please!!! with linux sprinkles on top!!:D

---

### Post by mikewhatever on 2011-02-24
Quantum Paradox, just connect an  ethernet cable, then install the driver with the following command:
```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by oddsonandy on 2012-09-14
I used your advice with great success and Just wanted to say thanks.

---

