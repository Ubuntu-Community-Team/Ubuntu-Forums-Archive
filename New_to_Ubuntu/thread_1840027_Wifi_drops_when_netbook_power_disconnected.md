---
title: "Wifi drops when netbook power disconnected"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by spamdisco on 2011-09-06
Hi,

I've only been using ubuntu/linux for a few months, installed 10.04, used ndiswrapper to get rtl8187se wifi working on Advent 4211 (Msi Wind clone) and worked without fault. 

I've updated to 10.10 then 11.04 and now have a strange fault where intermittently when the ac power is removed the wifi drops, no APs are seen, rmmod & modprobe ndiswrapper doesn't recover it. Works ok again after reboot.

The syslog from when it happened showed:* irq 17: nobody cared (try booting with the "irqpoll" option)*
Irq17 is assigned to ndiswrapper in interrupts.

Rebooted with irqpoll set, when the fault ocurred again syslog showed a different error:
[I] [ 9121.512226] atkbd serio0: Use 'setkeycodes e077 <keycode>' to make it known.
[ 9122.080296] EXT4-fs (sda11): re-mounted. Opts: errors=remount-ro,commit=600
[ 9122.766849]** pciehp 0000:00:1c.1:pcie04: Card present on Slot(0-1)**
[ 9122.872697] **pciehp 0000:00:1c.1:pcie04: Device 0000:02:00.0 already exists at 0000:02:00, cannot hot-add**
[ 9122.872855]** pciehp 0000:00:1c.1:pcie04: Cannot add device at 0000:02:00**
wpa_supplicant[564]: CTRL-EVENT-DISCONNECTED bssid=1c:af:f7:xx:xx:xx reason=0
NetworkManager[466]: <info> (wlan0): supplicant connection state:  completed -> disconnected[/I]

Not sure what to do next!

Any help will be appreciated......
Thanks.

---

### Post by elgordodude on 2011-09-06
Might be power related. 11.04 has been described as way more power hungry than 10.10

[http://www.tomshardware.com/reviews/ubuntu-11.04-natty-narwhal,2943-13.html](http://www.tomshardware.com/reviews/ubuntu-11.04-natty-narwhal,2943-13.html)

powertop should show you current power usage, and netbooks don't tend to have great battery life anyway.

---

### Post by wildmanne39 on 2011-09-06
Hi, welcome to the forum! you might try this if it works we will need to make it persistent.
```
sudo iwconfig wlan0 power off
```
Thank you

---

### Post by spamdisco on 2011-09-07
Thanks elgordodude, the battery life is poor, but the wifi usually drops off the very second that the cable is disconnected. After rebooting and leaving on battery the wifi is ok.


Thanks Wildmanne3, when i initially checked iwconfig it showed that power management was already off, but checked later and it was set to "*max timeout:0us*", is this normal?
I've switched off now and will see how it runs.... Thanks.

---

### Post by wildmanne39 on 2011-09-07
Hi, this 
> max timeout:0us
usually just says on or off.

Let me know if the command I gave you works and we will make it persistent.
Thank you

---

### Post by spamdisco on 2011-09-08
Hi Wildmanne39, I ran it with power management off, but it still dropped wifi. I ran iwconfig straight after:

                          ```
chris@tinyII:~$ uptime  
  18:56:58 up 21:57,  2 users,  load average: 0.85, 0.50, 0.34  
 chris@tinyII:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11g  ESSID:off/any   
           Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated    
           Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3   
           RTS thr:off   Fragment thr:off  
           Power Management max timeout:0us  mode:All packets received  
           Link Quality:0  Signal level:0  Noise level:0  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  

```power management had changed again, it hadn't been rebooted since changing, but will have been suspended and hibernated.

---

### Post by wildmanne39 on 2011-09-08
Hi, ok please run these commands so we can get start getting to the heart of the problem:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by spamdisco on 2011-09-08
```
chris@tinyII:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux tinyII 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux

``````
chris@tinyII:~$ sudo lshw -C network
[sudo] password for chris: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:92:58:97:46
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:c000(size=256) memory:ffd10000-ffd10fff memory:ffd00000-ffd0ffff memory:dfd00000-dfd0ffff
  *-network
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 22
       serial: 00:1d:92:c6:f8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187se driverversion=1.56+Realtek Semiconductor Corp. ip=192.168.0.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: irq:17 ioport:b000(size=256) memory:dfc00000-dfc03fff

``````
chris@tinyII:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)

``````
chris@tinyII:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"dlink"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 1C:AF:F7:A5:C6:DA   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````
chris@tinyII:~$ rfkill list all
chris@tinyII:~$ lsmod
Module                  Size  Used by
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
i915                  451033  3 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           192828  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         40745  1 i915
psmouse                73312  0 
serio_raw              12990  0 
drm                   184164  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
r8169                  42534  0 

```Thanks for the help, rfkill didn't appear to do anything.

---

### Post by wildmanne39 on 2011-09-08
Hi, all right I finally found the driver that should work with your card so we can uninstall the ndiswrapper driver and install it, then you should have a much better connection.
Run these commands please:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
do the commands one at a time.
then make sure you are disconnected from your wired connection and restart your computer.
 
Then run this command and see if the the connection works
```
sudo modprobe r8187se
```
if it does we will need to make it persistent.
Thank you

---

### Post by spamdisco on 2011-09-08
Thanks again Wildmanne39, back online ok without ndiswrapper. Will let it run for a day.....

---

### Post by wildmanne39 on 2011-09-08
Hi, that is great please let me know if you need more help also we need to make that persistent with this command other wise when you restart your computer you will have to run the moprobe again.

Please run this command:
```
sudo su 
echo r8187se >> /etc/modules 
exit
```
Also if you would like to support my ubuntu membership by click on the link in my signature I would greatly appreciate it.
Thank you

---

### Post by spamdisco on 2011-09-09
Hi Wildmanne, the fault is still occuring, but now it is also causing the netbook to hang shortly afterwards, any ideas? Thanks.

---

### Post by wildmanne39 on 2011-09-09
Hi, you can try this if it works we will need to make it persistent.
```
sudo iwconfig wlan0 power off

sudo iwconfig wlan0 rate auto

sudo service network-manager restart
```
one command at a time.
Thank you

---

### Post by spamdisco on 2011-09-09
Cheers, will leave it running with these settings...


> **wildmanne39 said:**
> Hi, you can try this if it works we will need to make it persistent.
```
sudo iwconfig wlan0 power off

sudo iwconfig wlan0 rate auto

sudo service network-manager restart
```one command at a time.
Thank you

---

### Post by wildmanne39 on 2011-09-09
Hi, so did it work if so we need to make the changes persistent otherwise it will reset when you restart your computer.
Thank you

---

### Post by spamdisco on 2011-09-09
> **wildmanne39 said:**
> Hi, so did it work if so we need to make the changes persistent otherwise it will reset when you restart your computer.
Thank you


After running the commands the netbook is still online, the fault doesn't occur every time the ac is disconnected, but seems to be after a few hours, with sleep/hibernate being used. The netbook is rarely rebooted except for faults. Thanks.

---

### Post by wildmanne39 on 2011-09-09
Hi, To make the changes permanent so you do not have to re-enter it after every reboot, run 
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
exit

```
just above the exit, then save and exit and that should do it.

If I have help you in a small way would you please click on the link in my signature and support me becoming an ubuntu member?

Also would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by spamdisco on 2011-09-13
Hi, turning power management off still didnt resolve the issue, but found a 'fix'/workaround by downgrading pm-utils from_ _[http://www.robertbeal.com/1248/ubuntu-10101104-freezing-battery-power](http://www.robertbeal.com/1248/ubuntu-10101104-freezing-battery-power) . Thanks for the help wildmanne39.

---

### Post by wildmanne39 on 2011-09-13
Hi, your welcome! I am glad it is working.

---

