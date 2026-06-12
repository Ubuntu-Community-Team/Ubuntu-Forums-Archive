---
title: "Lost my internet connectivity after upgrade"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-04-28
A few days ago I upgraded from intrepid to jaunty via the Update Manager.

All seemed to have gone pretty well, but now I cannot connect to the internet through my Vodafone Mobile Broadband.

When I click on the icon in the task bar, everything seems to be fine and it tells me I'm connected, but when I try to use Firefox or Update Manager it's quite clear that nobody's home.

During the install of jaunty there were three occasions where I was asked whether I'd like to keep my original file or replace it with a new one. Being a bit of a burke, I elected to replace them, which has meant that I've lost my desktop cube thingy done through Compiz and I presume it's thrown away lots of my internet connection data.

Has anyone got any idea as to how I could get my Mobile Broadband working?

---

### Post by lkraemer on 2009-04-29
Roger,
I haven't a clue as to what drivers you are using......MadWifi,
ndiswrapper, Broadcom.....

But, if a Kernel upgrade made the Wifi stop working, just pick the
previous Grub Boot Menu selection for Ubuntu and it should be 
functional.  If this makes it work, you will need to re-compile
the drivers for the new Kernel.  The guide you used for the initial
install should lead you through the process.

Open a Terminal and Do:
```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig

```
Post the output of each.

lkraemer

---

### Post by brunogirin on 2009-04-29
Roger, I'm using 3 Mobile Broadband (which should be the same or very similar hardware to Voodoofone) and it works perfectly in Jaunty (I'm typing this using it). What dongle do you have? Is it the Huawei 160?

What I would suggest is:
[LIST]
[*]Unplug your mobile broadband dongle
[*]Right click on the Network Manager applet and select "Edit connections"
[*]Go to the Mobile Broadband tab
[*]Select your connection
[*]Delete it
[*]Plug your dongle back in and reconfigure it
[/LIST]

---

### Post by Roger Allott on 2009-04-29
> **lkraemer said:**
> Roger,
Open a Terminal and Do:
```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig

```
Post the output of each.

lkraemer

Thanks. Here it all comes.

lshw -C network
output:
```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:67:45:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:03:0d:89:33:d7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e6:d7:36:b2:2c:ab
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```


lsmod
output:
```
Module                  Size  Used by
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  6 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
arc4                    9856  2 
snd_seq_oss            37760  0 
ecb                    10752  2 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwl3945                97912  0 
joydev                 18368  0 
soundcore              15200  1 snd
iTCO_wdt               19108  0 
intel_agp              34108  1 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
iTCO_vendor_support    11652  1 iTCO_wdt
agpgart                42696  3 drm,intel_agp
mac80211              217208  1 iwl3945
led_class              12036  1 iwl3945
cfg80211               38032  2 iwl3945,mac80211
option                 28036  0 
video                  25360  0 
output                 11008  1 video
psmouse                61972  0 
serio_raw              13316  0 
pcspkr                 10496  0 
usbhid                 42336  0 
usb_storage            82880  4 
r8169                  40836  0 
mii                    13312  1 r8169
vesafb                 13828  1 
fbcon                  46112  72 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```


ndiswrapper -l
output:
```
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
```


cat /etc/modprobe.d/blacklist
```
output:
cat: /etc/modprobe.d/blacklist: No such file or directory
```


iwconfig
```
output:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

Is that any help?

---

### Post by lkraemer on 2009-04-29
OK,
Your Wireless interface is an Intel Corporation, PRO/Wireless 3945ABG.
Your Drivers are iwl3945, and lsmod looks appropriate.

Your connected to an essid of NETGEAR.  Is that a valid Router
that you are trying to connect to?  You are not associated with
that essid. Your Wifi is wlan0, so use it in the following commands.

Let's try scanning to see if you can find the correct router that
you really want.  In a Terminal window DO:

```

sudo ifconfig wlan0 up
sudo iwlist wlan0 scanning
iwconfig


```
Post the output of the previous three commands.

Then DO:
```

sudo ifconfig wlan0 down

```
You should see your router that you want to connect to.  Let's assume
that name is Airlink instead of NETGEAR.  UPPER/lower case makes a difference.

So, let's connect to Airlink.....(Just subsitiute your router's
name for Airlink)...DO:
```

sudo iwconfig wlan0 essid "Airlink"
sudo iwconfig wlan0 mode Managed
iwconfig

```
Post the output of the previous three commands

So, now let's finish up with this.
```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid "Airlink"
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up
sudo dhclient wlan0
iwconfig

```
Post the output of iwconfig.
Try to surf.  Hopefully you will be able to access the internet.

lkraemer

---

