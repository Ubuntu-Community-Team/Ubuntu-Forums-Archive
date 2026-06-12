---
title: "no ethernet/wireless connection after 14.04 install"
date: 2014-07-13
forum: Networking &amp; Wireless
---

### Post by gary43 on 2014-07-13
I give up and need to ask for help on completing an install of Lubuntu 14.04 on a Dell Latitude D600.
Have no background in computer language so that the numerous posts have me "scratching my head" and not
making any meaningful progress.

My understanding is that I have a BCM4306 802.11b/g wireless LAN converter [14e4:4320] (rev B) and the appropriate driver needs loading
which from the chili555 posts requires a "linux-firmware-nonfree" driver.  Unfortunately, I have no ethernet connection.  I'm not sure how best to proceed.  Ultimately, I will use the computer wirelessly.  

I have included the following commands:  lshw -C network, lsmod, iwconfig, rfkill list

  fifi@fifi-Latitude-D600:~$ lshw -C network
  WARNING: you should run this program as super-user.
    *-network               
         description: Network controller
         product: BCM4306 802.11b/g Wireless LAN Controller
         vendor: Broadcom Corporation
         physical id: 3
         bus info: pci@0000:02:03.0
         version: 03
         width: 32 bits
         clock: 33MHz
         capabilities: bus_master
         configuration: driver=b43-pci-bridge latency=32
         resources: irq:5 memory:faffe000-faffffff
  WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
  fifi@fifi-Latitude-D600:~$ lsmod
  Module                  Size  Used by
  bnep                   18895  2 
  rfcomm                 53664  8 
  dm_crypt               22622  0 
  joydev                 17101  0 
  snd_intel8x0           33110  1 
  snd_ac97_codec        105709  1 snd_intel8x0
  ac97_bus               12642  1 snd_ac97_codec
  snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
  snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
  snd_seq_midi           13132  0 
  snd_seq_midi_event     14475  1 snd_seq_midi
  gpio_ich               13229  0 
  snd_rawmidi            25135  1 snd_seq_midi
  b43                   356470  0 
  dell_laptop            17808  0 
  snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
  bcma                   42043  1 b43
  dcdbas                 14448  1 dell_laptop
  snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
  psmouse                91033  0 
  pcmcia                 51828  0 
  mac80211              545990  1 b43
  snd_timer              28584  2 snd_pcm,snd_seq
  serio_raw              13230  0 
  snd                    60871  10 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
  cfg80211              409394  2 b43,mac80211
  yenta_socket           40201  0 
  btusb                  27580  0 
  lpc_ich                16864  0 
  soundcore              12600  1 snd
  pcmcia_rsrc            18319  1 yenta_socket
  bluetooth             342263  22 bnep,btusb,rfcomm
  pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
  mac_hid                13037  0 
  shpchp                 32128  0 
  parport_pc             31981  1 
  ppdev                  17391  0 
  lp                     13299  0 
  parport                40836  3 lp,ppdev,parport_pc
  radeon               1416373  2 
  i2c_algo_bit           13197  1 radeon
  ttm                    72698  1 radeon
  drm_kms_helper         46907  1 radeon
  ssb                    51854  1 b43
  drm                   243792  4 ttm,drm_kms_helper,radeon
  video                  18903  0 
  fifi@fifi-Latitude-D600:~$ iwconfig
  lo        no wireless extensions.
   
  fifi@fifi-Latitude-D600:~$ rfkill list
  0: hci0: Bluetooth
              Soft blocked: no

Thanks in advance.

---

### Post by varunendra on 2014-07-13
Welcome to the forums Gary!

This post describes how to install the "linux-firmware-nonfree" package without internet connection : [http://ubuntuforums.org/showpost.php?p=13062169](http://ubuntuforums.org/showpost.php?p=13062169)

---

### Post by gary43 on 2014-07-14
Thanks Varunendra,

I was able to download and install the driver and connect wireless.  
Was wondering however, why i'm not able to connect with ethernet.  Is it turned off?  Do I have this on the computer? 
thanks, g

---

### Post by varunendra on 2014-07-14
You're welcome!

If the output of "lshw -C network" in your post was complete, there appears to be no ethernet controller in your system. Do you have an ethernet port on it? If yes, please post the full outputs of -
```
sudo lshw -C network
lspci -nnk | grep -iA2 net
```

---

### Post by gary43 on 2014-07-15
varunendra,

I have an ethernet port on the computer.  I have listed the codes you requested.

```
fifi@fifi-Latitude-D600:~$ sudo lshw -C network
[sudo] password for fifi: 
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:faffe000-faffffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:7d:0a:1c:0e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.13.0-24-generic firmware=666.2 ip=192.168.0.104 link=yes multicast=yes wireless=IEEE 802.11bg
fifi@fifi-Latitude-D600:~$ lspci -nnk / grep -iA2 net
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of A2
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file

```

thanks g

---

### Post by varunendra on 2014-07-16
The output of 'lshw' shows there is no Ethernet controller detected on the system. If you have an Ethernet port, either the controller is disabled from BIOS (although it should still show up in the lshw output) or is no more functioning (more likely).

The second command was not entered correctly. It is a 'pipe' symbol (|) before 'grep', not a slash (/ or \). The pipe symbol is on the same key as backslash (\) above the 'Enter' key on my US-104 type keyboard. Although that command should only confirm what 'lshw' returned.

---

### Post by gary43 on 2014-07-16
Varunendra,

Thanks, I have enclosed the missing codes

```
fifi@fifi-Latitude-D600:~$ lspci -kk | grep -iA2 net
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
    Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card
    Kernel driver in use: b43-pci-bridge

```

I did look at the bios setup but it doesn't suggest any ethernet being disabled.  So I guess it must not have that capacity.  

Thanks agai

---

### Post by varunendra on 2014-07-17
The last thing I can suggest is to look into BIOS again, and see if there is an option called "IOMMU" somewhere in it. If there is, try changing its state (usually 'enabled' to disabled'). This feature is not available in all motherboards, so not much hope there either.

Bottom line - if you have an Ethernet port (are you sure it is not a 'Modem' port? That would be slightly slimmer than Ethernet port) on the system, either something unusual in BIOS (like "IOMMU") is hiding the Ethernet controller from Linux kernel, or it is simply gone - disconnected or dead.

---

