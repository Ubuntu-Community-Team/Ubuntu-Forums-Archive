---
title: "madwifi wireless drivers"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by xGutsAndGloryx on 2007-08-29
I believe i just successful installed my wireless drivers but its not picking anything up... i don't know if its my area or it wasn't installed correctly... how can i test it?

---

### Post by kevdog on 2007-08-29
Lets just see if OS has made the association between the madwifi drivers and your card

Reboot after installation of drivers (if not already done so)

Please post
lshw -C network
iwlist scan

---

### Post by xGutsAndGloryx on 2007-08-29
*-network:0             
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 9
       bus info: pci@00:09.0
       logical name: wifi0
       version: 01
       serial: 00:0e:9b:42:6b:c8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:38000000-3800ffff irq:11
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 10
       serial: 08:00:46:ed:7c:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.46 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:9000-90ff iomemory:e000bc00-e000bdff irq:3



lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

---

### Post by kevdog on 2007-08-29
Weird

Whats the make and model of your wireless card (I know its an atheros chipset).

---

### Post by xGutsAndGloryx on 2007-08-29
Lan Express... i believe


i have a sony notebook computer if that helps any

---

### Post by kevdog on 2007-08-29
I need some more information, b/c from what it states on the madwifi wiki, your card should be supported.  How did you install the drivers -- from source or repository?

Can you post
modinfo ath_pci

---

### Post by xGutsAndGloryx on 2007-08-29
from repository

filename:       /lib/modules/2.6.20-16-generic/madwifi/ath_pci.ko
license:        Dual BSD/GPL
version:        0.9.3.1
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     D33427613CC54A874D9A746
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           countrycode:Override default country code (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)



what other information do you need and i will try to find it.

---

### Post by xGutsAndGloryx on 2007-08-29
its a sony notebook model pcgk23

---

### Post by kevdog on 2007-08-29
Well lets just try somethings, but we might need to compile from source.

Do you have an ethernet connection on the computer?? (wired)

Try this first
sudo modprobe ath_pci
sudo wlanconfig ath0 create wlandev wifi0 wlanmode sta
sudo ifconfig ath0 up
sudo modprobe wlan_scan_sta
iwlist ath0 scan

---

### Post by nosrednaekim on 2007-08-29
"iwconfig" might help too...

---

### Post by xGutsAndGloryx on 2007-08-29
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo modprobe ath_pci
Password:
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo wlanconfig ath0 create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: Input/output error
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo ifconfig ath0 up
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo modprobe wlan_scan_sta
xgutsandgloryx@xgutsandgloryx-laptop:~$ iwlist ath0 scan
ath0      No scan results
xgutsandgloryx@xgutsandgloryx-laptop:~$

---

### Post by kevdog on 2007-08-29
Well that didnt work did it.

Ok, do you have an internet connection because I want to try to compile and install the drivers from source.  You will need to install a few packages from either CD or internet along with downloading the madwifi source packages.

This is the page Im referencing:
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

---

### Post by xGutsAndGloryx on 2007-08-29
xgutsandgloryx@xgutsandgloryx-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

xgutsandgloryx@xgutsandgloryx-laptop:~$ 



yes, i have a wired internet connection.... do you have a instant messager? we could finish this on a instant messager instead of over the msg board?

---

### Post by kevdog on 2007-08-29
Pidgin not working for me right now.

Ok install packages so you can compile
sudo aptitude install build-essential linux-headers-`uname -r`

cd ~
mkdir madwifi
wget [http://superb-east.dl.sourceforge.net/sourceforge/madwifi/madwifi-0.9.3.2.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/madwifi/madwifi-0.9.3.2.tar.gz) -O ~/madwifi/madwifi-0.9.3.2.tar.gz
cd madwifi
tar -zxvf madwifi-0.9.3.2.tar.gz
cd madwifi-0.9.3.2

sudo ifconfig ath0 down
sudo ifconfig wifi0 down

cd scripts
./madwifi-unload.bash
./find-madwifi-modules.sh $(uname -r)
cd ..

make
sudo make install
sudo modprobe ath_pci

iwconfig

Please post the output of iwconfig
and modinfo ath_pci

Thanks

---

### Post by xGutsAndGloryx on 2007-08-29
xgutsandgloryx@xgutsandgloryx-laptop:~/Desktop/madwifi$ sudo ifconfig wifi0 downxgutsandgloryx@xgutsandgloryx-laptop:~/Desktop/madwifi$ cd scripts
xgutsandgloryx@xgutsandgloryx-laptop:~/Desktop/madwifi/scripts$ ./madwifi-unload.bash
FATAL: Module wlan_scan_sta is in use.
FATAL: Module wlan is in use.
xgutsandgloryx@xgutsandgloryx-laptop:~/Desktop/madwifi/scripts$

---

### Post by kevdog on 2007-08-29
Hmmm, thats a new one for me

Try this first
sudo modprobe -r wlan_scan_sta

And then pickup here:

./madwifi-unload.bash
./find-madwifi-modules.sh $(uname -r)
cd ..

And if that doesnt work, reboot the computer with wireless device turned off, and then remove the module that way.

---

### Post by xGutsAndGloryx on 2007-08-29
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo modprobe -r wlan_scan_sta
Password:
FATAL: Module wlan_scan_sta is in use.
xgutsandgloryx@xgutsandgloryx-laptop:~$ 


i ran the command and got the err msg.... i tried rebooting the computer and running it again.. i got the same thing...

---

### Post by kevdog on 2007-08-30
Can you turn the wireless card off and try again??

Ive seen other people report this error and Im looking for a solution.

Another possibility is to use synaptic to uninstall the madwifi drivers (reverse the process you did to install them linux-restriced-modules)

or type
sudo aptitude purge linux-restricted-modules-`uname -r`

---

### Post by xGutsAndGloryx on 2007-08-30
ok i ran the command... what do i do now?

---

### Post by kevdog on 2007-08-30
Ok lets try it again:

sudo modprobe -r wlan_scan_sta

And then pickup here:

./madwifi-unload.bash
./find-madwifi-modules.sh $(uname -r)
cd ..

---

### Post by xGutsAndGloryx on 2007-08-30
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo modprobe -r wlan_scan_sta
FATAL: Module wlan_scan_sta not found.
xgutsandgloryx@xgutsandgloryx-laptop:~$ 



still nothing...

---

### Post by kevdog on 2007-08-30
Your all good, 

keep going with the instructions as originally posted.

---

### Post by xGutsAndGloryx on 2007-08-30
after following the instructions... how will i know if the driver was successful?

---

### Post by xGutsAndGloryx on 2007-08-30
xgutsandgloryx@xgutsandgloryx-laptop:~/Desktop/madwifi$ modprobe ath_pci
WARNING: Error inserting ath_hal (/lib/modules/2.6.20-16-generic/net/ath_hal.ko): Operation not permitted
WARNING: Error inserting wlan (/lib/modules/2.6.20-16-generic/net/wlan.ko): Operation not permitted
FATAL: Error inserting ath_pci (/lib/modules/2.6.20-16-generic/net/ath_pci.ko): Operation not permitted
xgutsandgloryx@xgutsandgloryx-laptop:~/Desktop/madwifi$

---

### Post by kevdog on 2007-08-30
sudo modprobe ath_pci

(Just a tip -- anytime you are screwing around with system / kernel files -- like we are -- you need root priviledges)

---

### Post by xGutsAndGloryx on 2007-08-30
xgutsandgloryx@xgutsandgloryx-laptop:~/Desktop/madwifi$ sudo wlanconfig ath0 create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: Input/output error

---

### Post by kevdog on 2007-08-30
Sorry I dont think you need that step with the newer drivers.  What is the output of 
iwconfig

---

### Post by xGutsAndGloryx on 2007-08-30
xgutsandgloryx@xgutsandgloryx-laptop:~/Desktop/madwifi$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by kevdog on 2007-08-30
Sweet --  I guess the documentation is right on at this point.

Ok 
sudo ifconfig ath0 up
sudo modprobe wlan_scan_sta
Then post output of:
iwlist ath0 scan

---

### Post by xGutsAndGloryx on 2007-08-30
xgutsandgloryx@xgutsandgloryx-laptop:~/Desktop/madwifi$ iwlist ath0 scan
ath0      No scan results

---

### Post by kevdog on 2007-08-30
Is the interface up??

Please post again

lshw -C network

and reboot

Make sure your router has no encryption set (no WEP/WPA/MAC filtering)

After rebooting try:
iwlist scan
sudo modprobe wlan_scan_sta
iwlist scan
sudo iwconfig ath0 essid "YOUR_ROUTER_ESSID_IN_QUOTES"
sudo dhclient ath0

---

### Post by xGutsAndGloryx on 2007-08-30
xgutsandgloryx@xgutsandgloryx-laptop:~/Desktop/madwifi$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 9
       bus info: pci@00:09.0
       logical name: wifi0
       version: 01
       serial: 00:0e:9b:42:6b:c8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:38000000-3800ffff irq:11
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 10
       serial: 08:00:46:ed:7c:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.46 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:9000-90ff iomemory:e000bc00-e000bdff irq:3





gutsandgloryx@xgutsandgloryx-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo modprobe wlan_scan_sta
Password:
xgutsandgloryx@xgutsandgloryx-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo iwconfig ath0 essid 
Error for wireless request "Set ESSID" (8B1A) :
    too few arguments.
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0e:9b:42:6b:c8
Sending on   LPF/ath0/00:0e:9b:42:6b:c8
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
xgutsandgloryx@xgutsandgloryx-laptop:~$ 



i am not directly connected to a router...

---

### Post by kevdog on 2007-08-30
sudo iwconfig ath0 essid "YOUR_ROUTER_ESSID_IN_QUOTES"
sudo dhclient ath0

You didnt do the first command correctly

---

### Post by kevdog on 2007-08-30
My enthusiasm is waning

Try this again if nothing works:

sudo ifconfig ath0 up
sudo ifconfig wifi0 up
sudo modprobe wlan_scan_sta
iwlist scan
sudo iwconfig ath0 essid "YOUR_ROUTER_ESSID_IN_QUOTES"
sudo dhclient ath0

---

### Post by xGutsAndGloryx on 2007-08-30
this command 
sudo iwconfig ath0 essid "YOUR_ROUTER_ESSID_IN_QUOTES"


i don't have a router connect do i still need to enter it in?

---

### Post by kevdog on 2007-08-30
Where is your wireless card going to connect to???  I dont understand? Dont you have a router?

---

### Post by xGutsAndGloryx on 2007-08-30
its built into my notebook computer

---

### Post by kevdog on 2007-08-30
I know the wireless card is in your notebook --- wireless cards connect to wireless routers/access points.  Where is your wireless card going to connect?

---

### Post by xGutsAndGloryx on 2007-08-30
i am going to my parents house this weekend... i'll need to have internet access on my pc.... when i was running windows... it would automatically detect my parents wireless router..... i didn't have to configure it or anything.... can that not be done in linux?

---

### Post by kevdog on 2007-08-30
Yes it is, but for now I think we are done b/c there is no way to confirm what we did works or does not work.  iwlist scan fails b/c there are no routers around the wireless card is picking up.  I wish you would have told me this a long time ago.

---

### Post by xGutsAndGloryx on 2007-08-30
i am sorry... i am still very new to linux... i am still learning... i apologize....

---

### Post by kevdog on 2007-08-30
Check back this weekend to let me know if it works.  There is still a little bit more configuring to do -- hopefully it will work.

---

### Post by cjbehm on 2007-08-31
Having just gone through a bit of silliness trying to install the most recent madwifi drivers (0.9.3.2) from scratch (mostly just because), it seems that the madwifi sources install the ath_pci and associated drivers into /lib/modules/$(uname -r)/net while the default 7.04 kernels appear to want to load them from /lib/modules/$(uname -r)/madwifi

I'm headed out for the weekend and so went about the expedient method of opening up Makefile.inc and changing the install directory from net to madwifi. After rebooting, it's working as expected.

This originally came about because I was going to go with an updated kernel, but while I could get everything to compile and I could get an wifi0 and ath0, I couldn't get any scan results.

So some of the problems here (other than the fact that he won't be able to test without a wifi connection) could be related. If not, perhaps it will help someone else out. As soon as I get a chance, I'm going to try my kernel again with the change to the madwifi install and see how it goes (though I'd rather learn how to tell the kernel to look at a different location - just didn't have time for further research today). If that proves successful then I'll post that it was.

---

### Post by cjbehm on 2007-09-03
Just to follow up on my previous experience, madwifi 0.9.3.2 altered to install to /lib/modules/$(uname -r)/madwifi is working fine for me now. I just rebuilt the latest stable 2.6.22 kernel and madwifi worked immediately with that change.

Time to research what dictates what is making the kernel look for them in madwifi instead of net (not that it matters terribly, other than not having to edit the madwifi Makefile.inc).

---

### Post by kevdog on 2007-09-03
Thanks for the post.  If you had not altered the file and left the drivers installed in the net directory, would they have worked anyway???

---

