---
title: "Laptop does not connect to any Wireless Network - rt2500pci"
date: 2013-10-19
forum: Networking &amp; Wireless
---

### Post by amjjawad on 2013-10-19
Hi,

This is Lubuntu 13.10 i386 install on an old machine (Packard Bell - Easy Note):

```
Linux Packard-Bell 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686 athlon i686 GNU/Linux
```

There is a Wireless Driver:

```
sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: RT2500 Wireless 802.11bg
       vendor: Ralink corp.
       physical id: 15
       bus info: pci@0000:00:15.0
       logical name: wlan0
       version: 01
       serial: 00:10:60:63:4a:2f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci driverversion=3.11.0-12-generic firmware=N/A latency=128 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:d0008000-d0009fff

```

I have tried:

```
nano /etc/pm/config.d/config
```

Added:
```
SUSPEND_MODULES="rt2500pci"
```

But that did NOT change anything, still can not conncet to a Wireless Network.

Help is highly appreciated, thank you!

---

### Post by praseodym on 2013-10-19
Check:
```

dmesg | grep rt2
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```

---

### Post by amjjawad on 2013-10-19
> **praseodym said:**
> Check:
```

dmesg | grep rt2
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```

```
dmesg | grep rt2
[   14.246674] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2560, rf: 0003, rev: 0004
[  246.935249] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  246.963621] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 0005 detected
[  246.972118] usbcore: registered new interface driver rt2800usb
[  246.999297] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  247.008066] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29

```

```
lsmod
Module                  Size  Used by
rt2800usb              22485  0 
rt2x00usb              20041  1 rt2800usb
rt2800lib              70115  1 rt2800usb
crc_ccitt              12627  1 rt2800lib
zram                   18070  1 
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323534  10 bnep,rfcomm
joydev                 17097  0 
snd_intel8x0           33069  1 
snd_ac97_codec        105668  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
arc4                   12536  4 
snd_pcm                89488  2 snd_ac97_codec,snd_intel8x0
rt2500pci              22682  0 
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
rt2x00pci              13111  1 rt2500pci
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
rt2x00mmio             13395  1 rt2500pci
rt2x00lib              48854  6 rt2x00pci,rt2x00usb,rt2500pci,rt2800lib,rt2800usb,rt2x00mmio
pcmcia                 51368  0 
snd_rawmidi            25094  1 snd_seq_midi
radeon               1307301  2 
mac80211              513247  4 rt2x00lib,rt2x00pci,rt2x00usb,rt2800lib
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
psmouse                90642  0 
serio_raw              13189  0 
snd_timer              24447  2 snd_pcm,snd_seq
ttm                    71886  1 radeon
drm_kms_helper         46867  1 radeon
cfg80211              401436  2 mac80211,rt2x00lib
snd                    60790  10 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
i2c_ali15x3            13139  0 
yenta_socket           40193  0 
k8temp                 12842  0 
i2c_ali1535            13102  0 
soundcore              12600  1 snd
pcmcia_rsrc            18319  1 yenta_socket
drm                   242354  4 ttm,drm_kms_helper,radeon
ohci_pci               13305  0 
i2c_algo_bit           13197  1 radeon
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
eeprom_93cx6           13168  1 rt2500pci
shpchp                 32129  0 
ati_agp                13177  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
firewire_ohci          35257  0 
pata_ali               13562  3 
uli526x                22164  0 
firewire_core          57656  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

```

```
 iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"ABC"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: C8:D3:A3:48:99:70   
          Bit Rate=81 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:5   Missed beacon:0


```

```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```
cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search Dlink

```


NOTE:
Pleaste note that this laptop is not mine. It is for a friend I converted her to Linux. I am currently using MY OWN USB Wireless Adapter which I can not give it with the laptop, therefore, I need to fix this issue. That should explain where this come from:

```
driver=rt2800usb
```

Thanks!

---

### Post by praseodym on 2013-10-19
From the stick you are currently using?!

Try:
```

sudo modprobe -rfv rt2800usb
sudo modprobe -rfv rt2500pci
sudo modprobe -v rt2500pci
```
Check:
```

iwconfig
sudo iwlist scan
rfkill list
route -n
ifconfig -a
```

---

### Post by amjjawad on 2013-10-19
> **praseodym said:**
> From the stick you are currently using?!

Try:
```

sudo modprobe -rfv rt2800usb
sudo modprobe -rfv rt2500pci
sudo modprobe -v rt2500pci
```


I am using the USB Adapter so that I can run the commands and post the result over here. I need to return the laptop soon.

Before I carry on with these commands, could you please be so kind and explain to me what these commands will do?

Appreciate your help :)

---

### Post by chili555 on 2013-10-20
> could you please be so kind and explain to me what these commands will do?They will temporarily unload the driver for the USB so that we can see clearly what the internal is doing or not doing without the system being confused by the USB.

---

### Post by amjjawad on 2013-10-20
> **chili555 said:**
> They will temporarily unload the driver for the USB so that we can see clearly what the internal is doing or not doing without the system being confused by the USB.

Hi :)

Okay then, I will run these commands and post the output ASAP :)

Thank you!

---

### Post by amjjawad on 2013-10-20
Okay, here is a weird and odd thing :/

While I was running the commands, I got a Wireless Connection and when I tried to post the output here, the page of Firefox stopped and when I checked, there is no internet but I am connected to the Wireless. I ran:

```
apt-get update
```

And there is no Internet Connection - "could not resolve" message and on Firefox: "Server not found".

Not sure what is going on!!!

I am posting this from another machine connected to the same Wireless Network that laptop is connected to.

---

### Post by amjjawad on 2013-10-20
For the 2nd time, I am trying to run: 

```
sudo modprobe -rfv rt2800usb
```

While the USB Adapter is plugged in, the whole machine is frozen and I can NOT do anything unless I shut it down by pressing and holding the power button for few seconds :(

This is very odd!

I am thinking now whether it was good idea to install Lubuntu 13.10 on this machine or not?

Help is highly appreciated. This laptop needs to go back to my neighbour who I just converted her to Linux and I can't give her the laptop while it is like that!

---

### Post by wildmanne39 on 2013-10-20
amjjawad I received your pm I will give you a script to run shutdown the computer and remove the usb device boot back up then run the script, but I will let My good friend chili555 handle your issue since he is already helping you and as you know he is the best person for the task.

copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by amjjawad on 2013-10-20
> **Wild Man said:**
> amjjawad I received your pm I will give you a script to run shutdown the computer and remove the usb device boot back up then run the script, but I will let My good friend chili555 handle your issue since he is already helping you and as you know he is the best person for the task.

Hi,

Yes, I know he is helping as well and I do appreciate that a lot but the reason why I sent you too is because this is not my laptop, it is for my neighbour and I should return it back ASAP and it is really bad this issue came to my way when I was trying to convert her after finally managed to convince her to get rid of Windows XP and install Linux. Now, this issue is not yet resolved and the laptop still with me for 3 days or more, I don't know what to tell her.

> copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks


I don't have LAN Connection at the moment. 

I will take a look at the link. Will report back, thanks!

---

### Post by chili555 on 2013-10-20
We hope you run the script with the USB detached.

---

### Post by amjjawad on 2013-10-20
> **chili555 said:**
> We hope you run the script with the USB detached.

Believe it or not, the Laptop is now connected to the Wireless Network and I just did:

```
sudo apt-get update
```

and it works O_o :D

NOT sure what happened? maybe the commands I ran did something? well, you are the boss, you know better than me when it comes to Networking issues :D

Do I need to run anything now? I will keep the laptop running until tomorrow morning and then give it back to her, she will be so happy :)

Is there any test I can run to make sure this issue won't happen again? just in case!

---

### Post by chili555 on 2013-10-20
You might shut it down completely; cold boot and see if it works. If it does work, I'd assume you are good to go!

---

### Post by amjjawad on 2013-10-20
> **chili555 said:**
> You might shut it down completely; cold boot and see if it works. If it does work, I'd assume you are good to go!

Done and it is still working :)

Thank you so much everyone, really appreciate your help and support :)

[http://i44.tinypic.com/2z8nq4w.jpg](http://i44.tinypic.com/2z8nq4w.jpg)

---

### Post by wildmanne39 on 2013-10-20
I imagine shutting it down and removing the usb device then booting up is what allowed it to load the correct driver and finally work.
Good Luck!

---

### Post by amjjawad on 2013-10-20
> **Wild Man said:**
> I imagine shutting it down and removing the usb device then booting up is what allowed it to load the correct driver and finally work.
Good Luck!

Could be, I am not quite sure what happened but the good news is, it works and I can't wait to see the smile on my neighbour face tomorrow :D

Just in case the same issue will come back, I will remove the SOLVED tag from this thread and seek your help yet again ;)

Thanks a lot everyone!

---

### Post by amjjawad on 2013-10-21
Hi again,

This is just to post some updates about the issue.

I took the laptop and went to my neighbour house. At first, it refused to connect to the Wireless Network but then, it got connected. But, same what happened with me, there was a connection between the laptop and the Wireless Network but without internet. After some reboot, same. I had to reboot the Router and only then, I got it to work so for now, it should be connected and has internet access :)

I wish you have seen what I did see :D 
She was SO MUCH dazzled and amazed by the speed. She admits her Core i3 (or i5?) machine is slower than this laptop which is from 2005 and she was extremely happy and shocked. I told her you have seen nothing, this is the real power of Linux. Not to mention when she opened her mouth and got shocked when she saw the laptops actually can be turned off in 2 seconds and get a working desktop in less than a minute :D

If there is something happen, I will update this thread. Thanks for everything, once more!

P.S.
Out of curiosity, any idea why it got connected to the Wireless BUT WITHOUT internet connection until I rebooted the router?

---

### Post by chili555 on 2013-10-21
> P.S.
Out of curiosity, any idea why it got connected to the Wireless BUT WITHOUT internet connection until I rebooted the router? I haven't any idea. I do know that we see this from time to time; a problem that is magically cured by rebooting the router. I even had that issue with my ancient WRT54G once in a while. Imagine my shame when Mrs. Chili can't get a connection and is standing over me as I pound the keyboard and she's asking why the great and powerful chili555 can't get her Facebook!

---

