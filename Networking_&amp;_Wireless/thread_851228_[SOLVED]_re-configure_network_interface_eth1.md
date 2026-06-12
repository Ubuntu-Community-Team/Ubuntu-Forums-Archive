---
title: "[SOLVED] re-configure network interface eth1"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by statman88 on 2008-07-06
Hello, I am having some problems getting ubuntu to reconize my wireless network card interface. It used to reconize it just fine but after trying to install a driver for a USB NIC it stopped working.  Here are the outputs of the following commands:

```
me@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```
```
me@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8b:be:99:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:129.1.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76600 (74.8 KB)  TX bytes:76600 (74.8 KB)

```
```
me@ubuntu:~$ sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device

```
```
me@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

I booted using the live cd and it still did not reconize the wireless card, but as you can see at the bottom of the lspci command it has the card as a hardware decvice.

I'm assuming the driver is corrupt??  But I couldn't find where to download it.

Thanks in advance for your help!

Statman88

---

### Post by chili555 on 2008-07-06
Let's have a look at:```
lsmod | grep ipw
sudo cat /var/log/messages | grep switch
```Thanks.

---

### Post by statman88 on 2008-07-06
sorry for the not so prompt reply....never got the email notification.

Per your request:

```
me@ubuntu:~$ lsmod | grep ipw
me@ubuntu:~$ sudo cat /var/log/messages | grep switch
Jul  3 07:50:03 ubuntu kernel: [12432.988000] SMP alternatives: switching to UP code
Jul  3 07:50:03 ubuntu kernel: [12433.000000] SMP alternatives: switching to SMP code
Jul  3 18:27:12 ubuntu kernel: [    9.008393] SMP alternatives: switching to UP code
Jul  3 18:27:12 ubuntu kernel: [    9.311470] SMP alternatives: switching to SMP code
Jul  3 18:27:12 ubuntu kernel: [   18.620000] hda_intel: azx_get_response timeout, switching to polling mode...
Jul  4 10:23:18 ubuntu kernel: [ 2222.700000] SMP alternatives: switching to UP code
Jul  4 10:23:18 ubuntu kernel: [ 2222.712000] SMP alternatives: switching to SMP code
Jul  4 10:23:22 ubuntu kernel: [ 2228.188000] Kill switch must be turned off for wireless networking to work.
Jul  4 10:35:10 ubuntu kernel: [ 2936.484000] Kill switch must be turned off for wireless networking to work.
Jul  4 12:22:06 ubuntu kernel: [ 9352.456000] Kill switch must be turned off for wireless networking to work.
Jul  4 12:27:13 ubuntu kernel: [    8.134731] SMP alternatives: switching to UP code
Jul  4 12:27:13 ubuntu kernel: [    8.437828] SMP alternatives: switching to SMP code
Jul  4 12:27:13 ubuntu kernel: [   18.848000] Kill switch must be turned off for wireless networking to work.
Jul  4 14:24:43 ubuntu kernel: [ 7070.984000] Kill switch must be turned off for wireless networking to work.
Jul  4 14:37:59 ubuntu kernel: [   11.817724] SMP alternatives: switching to UP code
Jul  4 14:37:59 ubuntu kernel: [   12.120776] SMP alternatives: switching to SMP code
Jul  4 14:37:59 ubuntu kernel: [   19.000000] Kill switch must be turned off for wireless networking to work.
Jul  4 18:44:55 ubuntu kernel: [   24.242747] SMP alternatives: switching to UP code
Jul  4 18:44:55 ubuntu kernel: [   24.545888] SMP alternatives: switching to SMP code
Jul  4 18:44:55 ubuntu kernel: [   18.500000] hda_intel: azx_get_response timeout, switching to polling mode...
Jul  4 18:44:55 ubuntu kernel: [   18.656000] Kill switch must be turned off for wireless networking to work.
Jul  4 19:41:41 ubuntu kernel: [   11.504392] SMP alternatives: switching to UP code
Jul  4 19:41:41 ubuntu kernel: [   11.807544] SMP alternatives: switching to SMP code
Jul  4 19:41:41 ubuntu kernel: [   18.768000] hda_intel: azx_get_response timeout, switching to polling mode...
Jul  4 19:41:41 ubuntu kernel: [   18.904000] Kill switch must be turned off for wireless networking to work.
Jul  4 19:56:21 ubuntu kernel: [   12.510101] SMP alternatives: switching to UP code
Jul  4 19:56:21 ubuntu kernel: [   12.813329] SMP alternatives: switching to SMP code
Jul  4 19:56:21 ubuntu kernel: [   18.744000] Kill switch must be turned off for wireless networking to work.
Jul  4 20:19:44 ubuntu kernel: [ 1423.960000] Kill switch must be turned off for wireless networking to work.
Jul  4 20:21:49 ubuntu kernel: [ 1549.112000] Kill switch must be turned off for wireless networking to work.
Jul  4 20:26:07 ubuntu kernel: [   12.701165] SMP alternatives: switching to UP code
Jul  4 20:26:07 ubuntu kernel: [   13.004174] SMP alternatives: switching to SMP code
Jul  4 20:26:07 ubuntu kernel: [   18.992000] hda_intel: azx_get_response timeout, switching to polling mode...
Jul  4 20:26:07 ubuntu kernel: [   19.168000] Kill switch must be turned off for wireless networking to work.
Jul  4 20:28:04 ubuntu kernel: [    8.824297] SMP alternatives: switching to UP code
Jul  4 20:28:04 ubuntu kernel: [    9.127397] SMP alternatives: switching to SMP code
Jul  4 20:28:04 ubuntu kernel: [   18.796000] hda_intel: azx_get_response timeout, switching to polling mode...
Jul  4 20:28:04 ubuntu kernel: [   18.972000] Kill switch must be turned off for wireless networking to work.
Jul  4 20:40:09 ubuntu kernel: [  747.328000] Kill switch must be turned off for wireless networking to work.
Jul  5 22:48:25 ubuntu kernel: [   10.787490] SMP alternatives: switching to UP code
Jul  5 22:48:25 ubuntu kernel: [   11.337235] SMP alternatives: switching to SMP code
Jul  5 22:48:25 ubuntu kernel: [   21.988000] Kill switch must be turned off for wireless networking to work.
Jul  5 23:49:39 ubuntu kernel: [    8.766825] SMP alternatives: switching to UP code
Jul  5 23:49:39 ubuntu kernel: [    9.069872] SMP alternatives: switching to SMP code
Jul  5 23:49:39 ubuntu kernel: [   17.400000] hda_intel: azx_get_response timeout, switching to polling mode...
Jul  5 23:52:07 ubuntu kernel: [  169.340000] Kill switch must be turned off for wireless networking to work.
Jul  6 00:26:22 ubuntu kernel: [   11.567052] SMP alternatives: switching to UP code
Jul  6 00:26:22 ubuntu kernel: [   11.870290] SMP alternatives: switching to SMP code
Jul  6 01:58:33 ubuntu kernel: [    9.223911] SMP alternatives: switching to UP code
Jul  6 01:58:33 ubuntu kernel: [    9.526919] SMP alternatives: switching to SMP code
Jul  6 01:58:33 ubuntu kernel: [   23.928000] hda_intel: azx_get_response timeout, switching to polling mode...
Jul  6 02:26:01 ubuntu kernel: [    8.200067] SMP alternatives: switching to UP code
Jul  6 02:26:01 ubuntu kernel: [    8.503171] SMP alternatives: switching to SMP code
Jul  6 10:24:17 ubuntu kernel: [   13.016988] SMP alternatives: switching to UP code
Jul  6 10:24:17 ubuntu kernel: [   13.319997] SMP alternatives: switching to SMP code
Jul  6 10:24:17 ubuntu kernel: [   19.276000] hda_intel: azx_get_response timeout, switching to polling mode...
Jul  6 11:09:30 ubuntu kernel: [   23.442623] SMP alternatives: switching to UP code
Jul  6 11:09:30 ubuntu kernel: [   23.745634] SMP alternatives: switching to SMP code
Jul  6 15:17:04 ubuntu kernel: [    9.906839] SMP alternatives: switching to UP code
Jul  6 15:17:04 ubuntu kernel: [   10.209846] SMP alternatives: switching to SMP code
Jul  6 15:17:04 ubuntu kernel: [   18.836000] hda_intel: azx_get_response timeout, switching to polling mode...
Jul  6 15:53:53 ubuntu kernel: [   21.258653] SMP alternatives: switching to UP code
Jul  6 15:53:53 ubuntu kernel: [   21.561834] SMP alternatives: switching to SMP code
Jul  6 15:53:53 ubuntu kernel: [   18.592000] hda_intel: azx_get_response timeout, switching to polling mode...
Jul  6 20:45:54 ubuntu kernel: [    9.715693] SMP alternatives: switching to UP code
Jul  6 20:45:54 ubuntu kernel: [   10.018808] SMP alternatives: switching to SMP code
Jul  6 20:51:13 ubuntu kernel: [    8.255218] SMP alternatives: switching to UP code
Jul  6 20:51:13 ubuntu kernel: [    8.558384] SMP alternatives: switching to SMP code

```

Thanks so much for the interest!

Statman88

---

### Post by statman88 on 2008-07-07
Bump

---

### Post by AlbertTatlocksCap on 2008-07-07
Ok - from your output, I reckon you need to install teh restricted hardware drivers to support the Broadcom wireless card. It usually prompts you to do this - green icon at the top right of screen somewhere

Hope this helps

Sorry misread your output - Intel Wireless card but I am sure it is the same as teh one on my Dell laptop - so try restricted drivers

---

### Post by statman88 on 2008-07-07
nope I don't get a prompt...do you know where I can get the drivers for the Centrino b/g chipset?  I know they come with the release but I would just like to re-install them.  Any info?

Thanks for the help!

Statman88

---

### Post by ddo on 2008-07-07
Let's try :

$> sudo ls hw -C network

to verify if there is a driver loaded for your device

ddo

---

### Post by ddo on 2008-07-07
by the way do you happen to have a physical  wifi on-off switch?

ddo

---

### Post by statman88 on 2008-07-07
> by the way do you happen to have a physical  wifi on-off switch?


Answer: Yes

> Let's try :

$> sudo ls hw -C network

to verify if there is a driver loaded for your device


Here we are:

```

me@ubuntu:~$ sudo ls hw -C network
ls: cannot access hw: No such file or directory
ls: cannot access network: No such file or directory 


```

Do I need to run it from a different location?
the directories exist in other locations when I run
```

sudo find -name hw

```

do i need something like:
```
 sudo find -name "name goes here" -exec ls {} \;
```

---

### Post by ddo on 2008-07-07
oops, I'm sorry. should be:
sudo lshw -C network

ddo.

---

### Post by statman88 on 2008-07-07
> 
oops, I'm sorry. should be:
sudo lshw -C network


Not a Problem :)

Here we are:

```
me@ubuntu:~$ sudo lshw -C network 
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       logical name: eth0
       version: 02
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s


```

---

### Post by ddo on 2008-07-07
Ok, it shows that your wifi module is loaded but there is not ethernet port assigned to, and looking back at the result from:

lsmod | grep ipw
sudo cat /var/log/messages | grep switch


I see that you must have the wifi swith on by accident:

"Jul  5 23:52:07 ubuntu kernel: [  169.340000] Kill switch must be turned off for wireless networking to work."

Let's try to turn it off and reboot the laptop again. BTW what is your laptop model?

---

### Post by chili555 on 2008-07-07
I thhink the old, forgetful guy that asked the question meant to ask about:```
lsmod | grep **iwl**
```Sorry.

Any errors thrown out when you do:```
sudo modprobe iwl3945
```If so, please post them.

---

### Post by statman88 on 2008-07-07
Output directly from terminal:

```

me@ubuntu:~$ lsmod | grep iwl
me@ubuntu:~$ lsmod | grep ipw
me@ubuntu:~$ sudo modprobe iw13945
FATAL: Module iw13945 not found.

```

> 
Let's try to turn it off and reboot the laptop again. BTW what is your laptop model?


I have already previously tried shutting off the wireless and rebooting the computer....no such luck :(

I am on a Dell XPS M1210, with dual boot Vista Business and Ubuntu 8.04 using the NeoGrub bootloader.

I have also tried:
Shutting the wireless off
Booting into Vista
Turning wireless on
Connecting to internet (works fine)
then rebooting into Vista

Again no such luck :(

---

### Post by chili555 on 2008-07-07
After you do:```
sudo updatedb
```which will need a few moments to run, please let us see:```
locate iwl3945.ko
```Thanks.

Your wireless wants iwl3945 in order to run, but evidently can't find it for some reason.

---

### Post by statman88 on 2008-07-07
here we are:

```
me@ubuntu:~$ locate iwl3945.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl3945.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko

```

---

### Post by ddo on 2008-07-08
Try to use this then:
[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

Be sure to follow instruction in readme

---

### Post by chili555 on 2008-07-08
Wist all due respect to my colleague ddo, I'd be cautious about replacing your iwl3945 module with one that is a couple of generations older. It may or may not even compile correctly. First, I'd walk my laptop over to the router, hook up an ethernet cable and do:```
sudo apt-get install linux-backports-modules-hardy-generic
```Afterwards, try modprobe again.

---

### Post by statman88 on 2008-07-08
I did notice that it was an older driver and didn't proceed further....I did try such things as

```

sudo apt-get install git-core

```

but not luck.

I will give your suggestion a try.

---

### Post by statman88 on 2008-07-08
ok, 
```
modprobe iwl3945
```
did not give any nasty errors

---

### Post by statman88 on 2008-07-08
I rebooted the computer and IT WORKS! :D

Thanks ddo for your interest in solving this problem and all of your help!

Thanks sooooo much chili you are awesome! :)

Just Kidding....

---

### Post by statman88 on 2008-07-08
ok so it looked like it only worked that one time i rebooted, it is not working again.

---

### Post by chili555 on 2008-07-08
Is *iwl3945* not loading on boot as expected? Check with:```
lsmod | grep 3945
```If it is not getting loaded, go ahead and load it manually:```
sudo modprobe iwl3945
```and then *sudo gedit /etc/modules* and add a single line:```
iwl3945
```Proofread, save and close. See if it loads and wireless works on boot.

---

### Post by statman88 on 2008-07-08
Alright that worked GREAT!  Thank you sooo much!! :D

small minor detail though, the wifi light does not light up?

Is there a quick fix for this?

---

### Post by chili555 on 2008-07-08
Perhaps *led-class* is also not getting loaded properly! Check with:```
lsmod | grep led-class
```Add it to */etc/modules* as above.

I have no clue why these modules don't load automagically on boot.

---

### Post by statman88 on 2008-07-08
humm....didn't seem to work.

The physical wireless kill switch on the computer actually isn't working I just discovered?? :confused:

---

### Post by statman88 on 2008-07-09
the wireless works fine on the computer though.  I just can't manually control it with the switch....is there another module for this?...I have looked but can't find it

---

### Post by kevdog on 2008-07-09
Ok, dont know if this will work, however if you are using the iwl3945 driver can you try this:

sudo rmmod iwl3945
sudo modprobe iwl3945 led=1

That might work, I don't know -- its driver specific.

---

### Post by statman88 on 2008-07-09
Just curious, I am still on my learning curve for Linux here, What exactly does the rmmod command do....I have an idea but was wondering if I could get a more explicit deffinition of it's workings.

Thanks so much in advance.

---

### Post by statman88 on 2008-07-09
ok, Nevermind i just found some documentation on it. :)

---

### Post by statman88 on 2008-07-09
> Ok, dont know if this will work, however if you are using the iwl3945 driver can you try this:

sudo rmmod iwl3945
sudo modprobe iwl3945 led=1

That might work, I don't know -- its driver specific. 

Nope, No such luck.

Thanks for the suggestion though! :)

---

### Post by kevdog on 2008-07-09
Is this an Acer laptop?

---

### Post by statman88 on 2008-07-09
Xps M1210

---

### Post by kevdog on 2008-07-09
Alt-F2? Fn-F2? Again a guess -- if not -- out of ideas.

---

### Post by statman88 on 2008-07-09
Nope, Thanks again though :)

---

