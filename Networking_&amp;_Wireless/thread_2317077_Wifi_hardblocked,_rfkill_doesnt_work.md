---
title: "Wifi hardblocked, rfkill doesnt work"
date: 2016-03-13
forum: Networking &amp; Wireless
---

### Post by desversen on 2016-03-13
Hello,

I can't activate my wifi pressing the botton,

*sudo rfkill unblock all* seems to not function.

I had Bodhi linux on this laptop and I solved the problem with* modprobe fsam7400 radio=1*.
I had to press the button in winXP on the other partition in order to activate the wifi.

Now I decided to reinstall and re-part the hard disc deleting windows and installing Lubuntu, but, as I predicted I have to resolve this wifi problem.

my lubuntu version 
[B]lubuntu-14.04.4-desktop-i386

[/B]my kernel version
**4.2.0-30-generic**

rfkill list
```
0: phy0: Wireless LAN
   Soft blocked: no
   Hard blocked: yes
```


lsmode
```

Module                  Size  Used by
snd_intel8x0           36864  1 
snd_ac97_codec        106496  1 snd_intel8x0
ac97_bus               16384  1 snd_ac97_codec
i915                 1032192  2 
snd_pcm                94208  2 snd_ac97_codec,snd_intel8x0
snd_seq_midi           16384  0 
ipw2100                77824  0 
snd_seq_midi_event     16384  1 snd_seq_midi
bnep                   20480  2 
rfcomm                 65536  0 
bluetooth             454656  10 bnep,rfcomm
libipw                 36864  1 ipw2100
snd_rawmidi            28672  1 snd_seq_midi
lib80211               16384  1 libipw
pcmcia                 53248  0 
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
cfg80211              471040  2 libipw,ipw2100
drm_kms_helper        114688  1 i915
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
yenta_socket           40960  0 
joydev                 20480  0 
snd_timer              32768  2 snd_pcm,snd_seq
drm                   303104  4 i915,drm_kms_helper
input_leds             16384  0 
pcmcia_rsrc            20480  1 yenta_socket
serio_raw              16384  0 
snd                    69632  9 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device
pcmcia_core            24576  3 pcmcia,pcmcia_rsrc,yenta_socket
lpc_ich                20480  0 
soundcore              16384  1 snd
shpchp                 32768  0 
i2c_algo_bit           16384  1 i915
irda                  172032  0 
crc_ccitt              16384  1 irda
video                  24576  1 i915
parport_pc             32768  1 
ppdev                  20480  0 
mac_hid                16384  0 
lp                     16384  0 
parport                45056  3 lp,ppdev,parport_pc
hid_generic            16384  0 
b44                    36864  0 
firewire_ohci          36864  0 
ssb                    57344  1 b44
usbhid                 49152  0 
psmouse               114688  0 
firewire_core          61440  1 firewire_ohci
hid                    98304  2 hid_generic,usbhid
mii                    16384  1 b44
pata_acpi              16384  0 
crc_itu_t              16384  1 firewire_core
wbsd                   24576  0 

```

sudo lshw -C network

```
 *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 01
       serial: 00:0a:e4:20:cc:85
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=b44  driverversion=2.0 duplex=full ip=192.168.0.8 latency=64 link=yes  multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:10 memory:e0200000-e0201fff memory:34000000-3400ffff
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:05:85:f6
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=ipw2100  driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 link=no  maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
       resources: irq:10 memory:e0203000-e0203fff
```

---

### Post by jeremy31 on 2016-03-13
If this is a Fujitsu Amilo you might want to see if there are any BIOS updates for it

---

### Post by desversen on 2016-03-13
its a Nevad@ (doesnt exist anymore) model ms2137 , Intel Centrino , from 2002

---

### Post by jeremy31 on 2016-03-13
Does the button work to change the rfkill state?

---

### Post by desversen on 2016-03-14
nothing happen.

The connection menu on the right bottom side says [COLOR=#808080]*Wi-Fi Networks*[/COLOR] and [COLOR=#808080]*Wi-Fi is disabled by hardware switch*[/COLOR], and they are in grey.

When I had xubuntu I solved the problem with 
**modprobe fsam7400 radio=1**

---

### Post by jeremy31 on 2016-03-14
What version of xubuntu?  The only code for fsam7400 I found is 4 years old.  Have you tried going into BIOS and choose reset to defaults?

---

### Post by desversen on 2016-03-14
a version I installed in 2012. I will try to check the BIOS now, but do you think there is another way to turn off the hardblocking ?

---

### Post by jeremy31 on 2016-03-14
One website claimed that this worked but it was a few years ago
```
sudo modprobe -r ipw2100
sudo rfkill unblock all
sudo modprobe ipw2100
```

---

### Post by desversen on 2016-03-14
> **jeremy31 said:**
> One website claimed that this worked but it was a few years ago
```
sudo modprobe -r ipw2100
sudo rfkill unblock all
sudo modprobe ipw2100
```

thank you. nothing happen :(

---

### Post by desversen on 2016-03-15
maybe there are some drivers I could install ?

---

### Post by chili555 on 2016-03-15
The fsam7400 module was written and subsequently abandoned. It was written for Fujitsu Seimens Amilo laptops, of which yours is evidently a re-branded version. I know of no way to resurrect it.

There is a laptop module called *fujitsu-laptop*. You might try loading it:```
sudo modprobe fujitsu-laptop
```I suspect it will do nothing. It may, however, enable the wireless button.

Otherwise, I'd get out a screwdriver and try the tape-over trick: [http://madwifi-project.org/wiki/UserDocs/MiniPCI](http://madwifi-project.org/wiki/UserDocs/MiniPCI)> Masking Pin 13

If this does not work for you, you could try masking off pin 13; sellotape is ideal for this. To find pin 13, hold the card so that the pins, (contacts) are facing you and the key (a little cut in the card) in on the left. Pins are counted up-to-down and left-to-right:

1  key  3  5  7  9 11 13 15 ...
2  key  4  6  8 10 12 14 16 ...

Pin 13 will be thus the seventh pin from the left edge or the sixths pin from the key on the upper side of the card.

---

### Post by desversen on 2016-03-15
Thank you for the answer ! :)
i'm not sure if I have a mini PCI-card, how could I check that? should it be a physical wifi card? never seen it in my computer..

anyway I tried this:

```
iversen@iversen-laptop:~$ sudo modprobe fujitsu-laptop
[sudo] password for iversen: 
iversen@iversen-laptop:~$ modprobe ath_pci rfkill=0
modprobe: FATAL: Module ath_pci not found.
iversen@iversen-laptop:~$ 


```

---

### Post by jeremy31 on 2016-03-15
Chili post has given me an idea post ```
sudo dmidecode | grep -iA17 'System Information'
```

I might be able to patch a module to make it work, amilo-rfkill.ko might be the replacement for fsam7400 but lacks some info about your computer

---

### Post by desversen on 2016-03-15
> **jeremy31 said:**
> Chili post has given me an idea post ```
sudo dmidecode | grep -iA17 'System Information'
```

I might be able to patch a module to make it work, amilo-rfkill.ko might be the replacement for fsam7400 but lacks some info about your computer

```
System Information
    Manufacturer:                
    Product Name:                
    Version: -1             
    Serial Number: 9147XZ1A02336006D9KS00        
    UUID: 146386A0-E336-11D7-8FF7-B5F5752C3E2F
    Wake-up Type: Power Switch

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer:                
    Product Name:                
    Version: Rev.A          
    Serial Number: 9147XZ1A02336006D9KS00        

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
    Manufacturer: 

```

---

### Post by jeremy31 on 2016-03-15
```
sudo -i
for i in /sys/class/dmi/id/*; do if [ -f $i ]; then echo -n "$i \""; cat $i | tr -d '\n'; echo '"'; fi; done
exit
```

---

### Post by chili555 on 2016-03-15
> **desversen said:**
> Thank you for the answer ! :)
i'm not sure if I have a mini PCI-card, how could I check that? should it be a physical wifi card? never seen it in my computer..

On the back of some laptops, there is often a little door you can access, something like this: [http://www.insidemylaptop.com/images/pavilion-dv9000-laptop/05-disconnect-wireless-antenna.jpg](http://www.insidemylaptop.com/images/pavilion-dv9000-laptop/05-disconnect-wireless-antenna.jpg)

[http://www.irisvista.com/tech/laptops/Toshiba-Qosmio-G40-G45/big/removing-laptop-motherboard-09.jpg](http://www.irisvista.com/tech/laptops/Toshiba-Qosmio-G40-G45/big/removing-laptop-motherboard-09.jpg)

Unscrew the door and see if there is a wireless card within. It is usually obvious as it has antenna wires attached.

Only attempt this with the computer turned off, unplugged and the battery removed.

---

### Post by desversen on 2016-03-15
> **jeremy31 said:**
> ```
sudo -i
for i in /sys/class/dmi/id/*; do if [ -f $i ]; then echo -n "$i \""; cat $i | tr -d '\n'; echo '"'; fi; done
exit
```


I hope it worked, I copied and pasted the whole code

```
iversen@iversen-laptop:~$ sudo -i
[sudo] password for iversen: 
 Sorry, try again.
[sudo] password for iversen: 
root@iversen-laptop:~# sudo -i
root@iversen-laptop:~# for i in /sys/class/dmi/id/*; do if [ -f $i ]; then echo -n "$i \""; cat $i | tr -d '\n'; echo '"'; fi; done
/sys/class/dmi/id/bios_date "07/01/03  "
/sys/class/dmi/id/bios_vendor "Phoenix Technologies LTD"
/sys/class/dmi/id/bios_version "R01-A0X   "
/sys/class/dmi/id/board_asset_tag ""
/sys/class/dmi/id/board_name "        "
/sys/class/dmi/id/board_serial "9147XZ1A02336006D9KS00        "
/sys/class/dmi/id/board_vendor "        "
/sys/class/dmi/id/board_version "Rev.A          "
/sys/class/dmi/id/chassis_asset_tag "        "
/sys/class/dmi/id/chassis_serial "None           "
/sys/class/dmi/id/chassis_type "1"
/sys/class/dmi/id/chassis_vendor "        "
/sys/class/dmi/id/chassis_version "N/A            "
/sys/class/dmi/id/modalias "dmi:bvnPhoenixTechnologiesLTD:bvrR01-A0X:bd07/01/03:svn:pn:pvr-1:rvn:rn:rvrRev.A:cvn:ct1:cvrN/A:"
/sys/class/dmi/id/product_name "        "
/sys/class/dmi/id/product_serial "9147XZ1A02336006D9KS00        "
/sys/class/dmi/id/product_uuid "146386A0-E336-11D7-8FF7-B5F5752C3E2F"
/sys/class/dmi/id/product_version "-1             "
/sys/class/dmi/id/sys_vendor "        "
/sys/class/dmi/id/uevent "MODALIAS=dmi:bvnPhoenixTechnologiesLTD:bvrR01-A0X:bd07/01/03:svn:pn:pvr-1:rvn:rn:rvrRev.A:cvn:ct1:cvrN/A:"
root@iversen-laptop:~# exit
logout
root@iversen-laptop:~# exit
```

[**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=35909") : I checked but i finded only the Hd and the place where the RAM is.. no wifi or usb cards

---

### Post by jeremy31 on 2016-03-15
This is experimental as chili555 would call it but it is safe
```
wget https://www.dropbox.com/s/2o4879ykstn8aii/amilo-rfkill.ko
sudo mv /lib/modules/4.2.0-30-generic/kernel/drivers/platform/x86/amilo-rfkill.ko /lib/modules/4.2.0-30-generic/kernel/drivers/platform/x86/amilo-rfkill.ko.bak
sudo cp ./amilo-rfkill.ko /lib/modules/4.2.0-30-generic/kernel/drivers/platform/x86/amilo-rfkill.ko
sudo depmod -a
sudo modprobe -v amilo-rfkill

```

Or just reboot and post ```
lsusb | grep amilo
``` and say whether the wifi works or not.  Also post any errors that may occur after sudo modprobe -v amilo-rfkill

---

### Post by goofprog on 2016-03-15
I had to do that on my dead Toshiba laptop.  I had to kill the switch by blacklisting the Intel device driver '**iwlwifi**' and then I was able to use another wifi adapter to use Linux on the information highway.

---

### Post by jeremy31 on 2016-03-15
> **goofprog said:**
> I had to do that on my dead Toshiba laptop.  I had to kill the switch by blacklisting the Intel device driver '**iwlwifi**' and then I was able to use another wifi adapter to use Linux on the information highway.

 Some Toshibas can be fixed by shutting down, remove battery and power cable, then hold the power button for 20-30 seconds.  Then reconnect battery and power cable and boot up

---

### Post by desversen on 2016-03-15
> **jeremy31 said:**
> This is experimental as chili555 would call it but it is safe
```
wget https://www.dropbox.com/s/2o4879ykstn8aii/amilo-rfkill.ko
sudo mv /lib/modules/4.2.0-30-generic/kernel/drivers/platform/x86/amilo-rfkill.ko /lib/modules/4.2.0-30-generic/kernel/drivers/platform/x86/amilo-rfkill.ko.bak
sudo cp ./amilo-rfkill.ko /lib/modules/4.2.0-30-generic/kernel/drivers/platform/x86/amilo-rfkill.ko
sudo depmod -a
sudo modprobe -v amilo-rfkill

```

Or just reboot and post ```
lsusb | grep amilo
``` and say whether the wifi works or not.  Also post any errors that may occur after sudo modprobe -v amilo-rfkill

first result

```
iversen@iversen-laptop:~$ sudo modprobe -v amilo-rfkill
insmod /lib/modules/4.2.0-34-generic/kernel/drivers/platform/x86/amilo-rfkill.ko 
modprobe: ERROR: could not insert 'amilo_rfkill': No such device


```

now im goin to reboot and then post the second result

nothing happent

```
iversen@iversen-laptop:~$ lsusb | grep amilo
iversen@iversen-laptop:~$ 


```


I did also try the thing holding the power button 30 seconds without cable and battery, but nothing changed I see

---

### Post by jeremy31 on 2016-03-15
That didn't work as the no such device means my patch failed
```
[COLOR=#000000][FONT=Ubuntu Mono]wget [/FONT][/COLOR]https://www.dropbox.com/s/2o4879ykstn8aii/amilo-rfkill.ko
[COLOR=#000000]sudo cp ./amilo-rfkill.ko /lib/modules/4.2.0-30-generic/kernel/drivers/platform/x86/amilo-rfkill.ko
sudo depmod -a
sudo modprobe -v amilo-rfkill[/COLOR]
```[COLOR=#000000]

Hopefully No such device doesn't happen

[/COLOR]

---

### Post by desversen on 2016-03-17
nothing else to do guys?

---

### Post by chili555 on 2016-03-17
> **desversen said:**
> nothing else to do guys?What was the result of Jeremy's post just above? Any interesting messages, errors, warnings?? All of those are helpful.

---

### Post by desversen on 2016-03-17
> **chili555 said:**
> What was the result of Jeremy's post just above? Any interesting messages, errors, warnings?? All of those are helpful.

you mean this one?

```
iversen@iversen-laptop:~$ wget https://www.dropbox.com/s/2o4879ykstn8aii/amilo-rfkill.kosudo cp ./amilo-rfkill.ko /lib/modules/4.2.0-30-generic/kernel/drivers/platform/x86/amilo-rfkill.ko
--2016-03-17 21:36:14--  https://www.dropbox.com/s/2o4879ykstn8aii/amilo-rfkill.kosudo
Resolving www.dropbox.com (www.dropbox.com)... 162.125.4.1
Connecting to www.dropbox.com (www.dropbox.com)|162.125.4.1|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: ‘amilo-rfkill.kosudo’

    [   <=>                                 ] 158.045      306KB/s   in 0,5s   

2016-03-17 21:36:16 (306 KB/s) - ‘amilo-rfkill.kosudo’ saved [158045]

--2016-03-17 21:36:16--  http://cp/
Resolving cp (cp)... failed: Name or service not known.
wget: unable to resolve host address ‘cp’
--2016-03-17 21:36:16--  http://./amilo-rfkill.ko
Resolving . (.)... failed: No address associated with hostname.
wget: unable to resolve host address ‘.’
/lib/modules/4.2.0-30-generic/kernel/drivers/platform/x86/amilo-rfkill.ko: Scheme missing.
FINISHED --2016-03-17 21:36:16--
Total wall clock time: 2,1s
Downloaded: 1 files, 154K in 0,5s (306 KB/s)
iversen@iversen-laptop:~$ sudo depmod -a
[sudo] password for iversen: 
iversen@iversen-laptop:~$ sudo modprobe -v amilo-rfkill
insmod /lib/modules/4.2.0-34-generic/kernel/drivers/platform/x86/amilo-rfkill.ko 
modprobe: ERROR: could not insert 'amilo_rfkill': No such device


```

---

### Post by Hadaka on 2016-03-17
Hi, was there a possible type O made from the code on post #12 ?
```
sudo modprobe -v amilo[COLOR=#ff0000]**-**[/COLOR]rfkill
```
```
modprobe: ERROR: could not insert 'amilo[COLOR=#ff0000]**_**[/COLOR]rfkill': No such device
```
error shows an underscore.

---

### Post by jeremy31 on 2016-03-17
Try my commands from [http://ubuntuforums.org/showthread.php?t=2317077&p=13455950#post13455950](http://ubuntuforums.org/showthread.php?t=2317077&p=13455950#post13455950) again.  For some reason I am missing carriage returns in posts and PM's, chili555 has seen my PM's

---

### Post by desversen on 2016-03-17
> **jeremy31 said:**
> Try my commands from [http://ubuntuforums.org/showthread.php?t=2317077&p=13455950#post13455950](http://ubuntuforums.org/showthread.php?t=2317077&p=13455950#post13455950) again.  For some reason I am missing carriage returns in posts and PM's, chili555 has seen my PM's


```
iversen@iversen-laptop:~$ wget https://www.dropbox.com/s/2o4879ykstn8aii/amilo-rfkill.ko
--2016-03-17 22:12:52--  https://www.dropbox.com/s/2o4879ykstn8aii/amilo-rfkill.ko
Resolving www.dropbox.com (www.dropbox.com)... 162.125.4.1
Connecting to www.dropbox.com (www.dropbox.com)|162.125.4.1|:443... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: https://dl.dropboxusercontent.com/content_link/rigCbphD29ndgE3gkuWIpixUikuVgyyYkUHH3xTUnPs85O4vG5K3wiZUuILC1NMm/file [following]
--2016-03-17 22:12:53--  https://dl.dropboxusercontent.com/content_link/rigCbphD29ndgE3gkuWIpixUikuVgyyYkUHH3xTUnPs85O4vG5K3wiZUuILC1NMm/file
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 108.160.173.69
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|108.160.173.69|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9912 (9,7K) [text/plain]
Saving to: ‘amilo-rfkill.ko.1’

100%[======================================>] 9.912       --.-K/s   in 0s      

2016-03-17 22:12:54 (71,1 MB/s) - ‘amilo-rfkill.ko.1’ saved [9912/9912]

iversen@iversen-laptop:~$ sudo cp ./amilo-rfkill.ko /lib/modules/4.2.0-30-generic/kernel/drivers/platform/x86/amilo-rfkill.ko
iversen@iversen-laptop:~$ sudo depmod -a
iversen@iversen-laptop:~$ sudo modprobe -v amilo-rfkill
insmod /lib/modules/4.2.0-34-generic/kernel/drivers/platform/x86/amilo-rfkill.ko 
modprobe: ERROR: could not insert 'amilo_rfkill': No such device
iversen@iversen-laptop:~$ 


```

---

### Post by jeremy31 on 2016-03-17
I didn't see that coming
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo cp ./amilo-rfkill.ko.1 /lib/modules/4.2.0-30-generic/kernel/drivers/platform/x86/amilo-rfkill.ko
[/FONT][/COLOR][COLOR=#000000]sudo depmod -a
sudo modprobe -v amilo-rfkill[/COLOR]
```

---

### Post by desversen on 2016-03-17
> **jeremy31 said:**
> I didn't see that coming
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo cp ./amilo-rfkill.ko.1 /lib/modules/4.2.0-30-generic/kernel/drivers/platform/x86/amilo-rfkill.ko
[/FONT][/COLOR][COLOR=#000000]sudo depmod -a
sudo modprobe -v amilo-rfkill[/COLOR]
```

```
iversen@iversen-laptop:~$ sudo cp ./amilo-rfkill.ko.1 /lib/modules/4.2.0-30-generic/kernel/drivers/platform/x86/amilo-rfkill.ko
[sudo] password for iversen: 
iversen@iversen-laptop:~$ sudo depmod -a
iversen@iversen-laptop:~$ sudo modprobe -v amilo-rfkill
insmod /lib/modules/4.2.0-34-generic/kernel/drivers/platform/x86/amilo-rfkill.ko 
modprobe: ERROR: could not insert 'amilo_rfkill': No such device
iversen@iversen-laptop:~$ 


```

---

### Post by jeremy31 on 2016-03-17
I would look into using the tape trick on the wifi card if you can find it

---

### Post by desversen on 2016-03-28
I will try it as soon as possible, hoping there will come some other solutions out

---

### Post by leclerc65 on 2016-03-28
This happened to me.
I don't remember much, but I think it's putting the computer into suspense, then log back on.

---

