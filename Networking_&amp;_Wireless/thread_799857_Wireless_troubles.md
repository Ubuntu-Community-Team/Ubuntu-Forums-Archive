---
title: "Wireless troubles"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by Sevy on 2008-05-19
Hello
I am completely new to Ubuntu and just installed it on my desktop.
Firstly Im trying to install my wireless usb dongle.
I have a Netgear wireless router DG834PN and the dongle is WG111v2
Im trying to connect using Wicd manager but am experiencing problems.
My router has to be set up(for other users) with SSID not broadcast ,WPA security and DHCP turned off
Ive entered the static ip and gateway and WPA password etc but it wont connect.
If I select hidden network and enter the name it does connect but the signal is at zero. 
Sometimes it does connect but when I browse using Firefox the first couple of pages load quite slowly and then not at all.
After this has happened the signal in wicd sticks to a number eg 91.
My pc is a Clevo L285P
Any suggestions? let me know if you need more info
Many thanks

---

### Post by Sevy on 2008-05-19
Ive gone back to the default settings of hardy and tried again with no luck.I tried the suggestions in the stickies but dont seem to be getting anywhere
Please advise

---

### Post by XedGeneral on 2008-05-19
Kind of same problem here too...

I use a Intel Wireless Pro 3945ABG wireless card... Can find a lot of connection but cannot connect to any at all! :(

---

### Post by Sevy on 2008-05-19
I typed lshw -c network in the terminal to find out what chipset it uses but its not showing this.I would post it here but I dont yet know how to save the terminal display onto my memory stick and then post it on my xp machine
It shows
Hardware Lister (lshw) - B.02.12.01
usage lshw [-format]  [-options....]
            lshw -version

and then it continues with what formats and options can be

??
Someone??

---

### Post by Sevy on 2008-05-19
Sorry my mistake,used a small instead of capital c in the termimal
Now Ill try and post it on here

---

### Post by chili555 on 2008-05-19
Nope, use a capital C.```
sudo lshw -C network
```If you want to create a text document you can drag-n-drop on your memory stick, do:```
sudo lshw -C network > hardware.txt
```

---

### Post by Sevy on 2008-05-19
Im trying to go through this sticky [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)  the first one but when I come to entering the commands in the terminal I cant figure how to enter each one as a seperate line and then hit enter to run the whole thing:confused:

---

### Post by chili555 on 2008-05-19
> I cant figure how to enter each one as a seperate line and then hit enter to run the whole thingYou should't do it that way. Enter a command in the terminal, press Enter, type in the next command, press Enter, etc. If there is an error at step 3, for example, it will do no good to execute steps 4 on. Better to fix or research the error first and then proceed.

---

### Post by Sevy on 2008-05-20
sevy@sevy-ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth0
       version: 10
       serial: 00:90:f5:11:07:e3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:6c:b6:51:86
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

It seems I dont have the driver installed for the wireless interface but am having trouble doing so
Please advise

---

### Post by Sevy on 2008-05-20
bump:)

---

### Post by Sevy on 2008-05-20
I now have the following but when I type sudo ifconfig <wlan0> down   in the terminal I get bash: wlan0: no such file or directory
What am I doing wrong??


 *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:6c:b6:51:86
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net111v2 driverversion=1.52+NETGEAR Inc.,3/16/2006,5.12 multicast=yes wireless=IEEE 802.11g
sevy@sevy-ubuntu:~$

---

### Post by chili555 on 2008-05-20
> sudo ifconfig <wlan0> downIt's trying to tell you to use wlan0 or substitute your wireless interface, eth1 or whatever, if it's not wlan0. Yours appears to be wlan0. Try the command again without the < and >.

---

### Post by Sevy on 2008-05-20
Thanks for your response chilli555
The code is now almost working.I recieve the following error

Listening on LPF/wlan0/00:14:6c:b6:51:86
Sending on   LPF/wlan0/00:14:6c:b6:51:86
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
sevy@sevy-ubuntu:~$

I recieve this error with DHCP on and off and either dynamic or static IP

---

### Post by chili555 on 2008-05-20
Your router or access point is not authenicating with the wireless card. The most likely, but not only reason is that you have encryption set in the router, WEP, WPA or otherwise, and you have not set the correct encryption details in *iwconfig*. Another reason is that you may have the incorrect ESSID. Please do:```
sudo iwlist wlan0 scan
```You will see a result like this:```
eth1      Scan completed :
          Cell 01 - Address: 99:9C:41:19:58:77
                    ESSID:"GBR919"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=85/100  Signal level=-48 dBm  Noise level=-82 dBm
                    Encryption key:**on**
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
```Key: on means 'show me correct key and I'll let you in.' Please try:```
sudo iwconfig wlan0 essid <essid_from_scan>
sudo iwconfig wlan0 ap 99:9C:41:19:58:77 (address from scan)
sudo iwconfig wlan0 key <any_encryption_here?>
sudo dhclient wlan0
```If your router uses WPA instaed of WEP, please check here: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Let us know.

---

### Post by Sevy on 2008-05-20
```
sudo iwlist wlan0 scan
```

When I type this I get no scan results

---

### Post by Sevy on 2008-05-21
Ive done what you suggested chilli555 and here are the following results.
I can only pick up my router (UXBRIDGE) if I put the adaptor right next to the router.If Im further away I either recieve someone elses router (next door neighbour)(BTHomeHub-B370) or "no scan results"
If I try and connect to my router with no encrytion I still get this error:- No DHCPOFFERS received.
No working leases in persistent database - sleeping.



sevy@sevy-ubuntu:~$ sudo iwlist wlan0 scan
[sudo] password for sevy: 
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:18:FD:A6
                    ESSID:"UXBRIDGE"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1D:68:4F:F9:83
                    ESSID:"BTHomeHub-B370"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sevy@sevy-ubuntu:~$ sudo iwconfig wlan0 essid UXBRIDGE
sevy@sevy-ubuntu:~$ 
sevy@sevy-ubuntu:~$ sudo iwconfig wlan0 ap 00:18:4D:18:FD:A6 
sevy@sevy-ubuntu:~$ 
sevy@sevy-ubuntu:~$ sudo iwconfig wlan0 key 83C97814B3
sevy@sevy-ubuntu:~$ 
sevy@sevy-ubuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:6c:b6:51:86
Sending on   LPF/wlan0/00:14:6c:b6:51:86
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
sevy@sevy-ubuntu:~$ 

This is driving me nuts:(:confused:

---

### Post by Sevy on 2008-05-21
Im also not getting the light flashing on my adaptor

---

### Post by vjsimon on 2008-05-21
Hi,

This is what I got when I typed sudo lshw -C network

  *-network:0 UNCLAIMED
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:01:04.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=128 maxlatency=34 mingnt=2
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:03:9d:73:84:e8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.64 latency=128 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3e:63:65:bd:ec:74
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

When I tried typing in sudo iwlist wlan0 scan, I get this

home@BenQ:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

I can't get my wireless working after about 2 weeks of continuous troubleshooting.

Please help.

---

### Post by Sevy on 2008-05-21
I can now scan for my router without being right next to it.I tried using another router but same problem-
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Sevy on 2008-05-21
Im not even sure if my netgear WG111v2 adaptor is compatible with ubuntu considering it only lights up for a split second when I plug it in.It should continue to flash every few seconds or so.
Has anyone else got this adaptor to work? 
Im recieving mixed answers when I google it

---

### Post by Roel1963 on 2008-05-21
> **Sevy said:**
> Has anyone else got this adaptor to work? 
Im recieving mixed answers when I google it

Flawless when using Gutsy, but Hardy doesn't do a thing with it...

---

### Post by Sevy on 2008-05-21
OK thanks for that Roel1963
Ill give Gutsy a try tomorrow as setup is so quick compared with xp

---

### Post by Sevy on 2008-05-22
Im now having trouble installing the driver on Gutsy.I cant remember how I did it before:mad:
Im trying to use ndisgtk.
Can someone show me where it explains how to do this?
Ive tried "sudo apt-get install ndisgtk" but when the terminal asks for my password I cant type anything in

---

### Post by Roel1963 on 2008-05-22
> **Sevy said:**
> Im now having trouble installing the driver on Gutsy.I cant remember how I did it before:mad:
Im trying to use ndisgtk.
Can someone show me where it explains how to do this?
Ive tried "sudo apt-get install ndisgtk" but when the terminal asks for my password I cant type anything in

I installed ndiswrapper through synaptic (both files, ndiswrapper-common itself and the utils).

Then:

(mind that you're at a command line, in the directory where the .inf and .sys files are):

sudo ndiswrapper -i [driver].inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

I am not sure ndisgtk worked in 7.10, I always do it like I wrote down here.

Good luck!

---

### Post by chili555 on 2008-05-22
> when the terminal asks for my password I cant type anything inIt is taking the password, even though it doesn't show. Just type it and press Enter.

---

### Post by Roel1963 on 2008-05-22
> **chili555 said:**
> It is taking the password, even though it doesn't show. Just type it and press Enter.

Of course, that's what Sevy meant!

---

### Post by Sevy on 2008-05-22
I now get the following.What am I missing?

sevy@sevy-desktop:~$ sudo ndiswrapper -i net111v2.inf
installing net111v2 ...
couldn't open net111v2.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ sudo modprobe ndiswrapper
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
sevy@sevy-desktop:~$ lshw -C network

---

### Post by Sevy on 2008-05-22
Roel1963
(mind that you're at a command line, in the directory where the .inf and .sys files are):
How do I do this
Im such a newb:)

---

### Post by Roel1963 on 2008-05-22
> **Sevy said:**
> Roel1963
(mind that you're at a command line, in the directory where the .inf and .sys files are):
How do I do this
Im such a newb:)

You're on a commandline when you are in a terminal, I see that you know how to get there :)

Then, navigate to the directory (folder) where your inf-file is.

For example: cd /home/sevy-desktop (when the inf and sys file are in your home dir).

Then first, remove your ndiswrapper settings from the kernel (these settings must be wrong as you didn't actually loaded the inf-file before modprobe):

sudo modprobe -r ndiswrapper

Then try to give each command I typed earlier:

sudo ndiswrapper -i net111v2.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

I think it should work this way...

---

### Post by Sevy on 2008-05-22
Ive started from the beginning
Completely removed ndiswrapper and reinstalled
I then copy my inf file to the desktop or where ever
In the terminal I try to navigate to the inf file but where ever I put it I get "no such file or directory.
After completely removing ndiswrapper and its configuration files,In the ndiswrapper folder there are 2 empty folders called
"net111v2" and "[net111v2]"
In the terminal I list the drivers "ndiswrapper -l and I get the prementioned folders stating invalid drivers
:confused:

---

### Post by Roel1963 on 2008-05-22
> **Sevy said:**
> Ive started from the beginning
Completely removed ndiswrapper and reinstalled
I then copy my inf file to the desktop or where ever
In the terminal I try to navigate to the inf file but where ever I put it I get "no such file or directory.
After completely removing ndiswrapper and its configuration files,In the ndiswrapper folder there are 2 empty folders called
"net111v2" and "[net111v2]"
In the terminal I list the drivers "ndiswrapper -l and I get the prementioned folders stating invalid drivers
:confused:

And when you completely remove these 2 folders, remove ndiswrapper from the kernel (sudo modprobe -r ndiswrapper) and then start from the top?

Somehow it seems you're near the solution...

---

### Post by Sevy on 2008-05-22
I try removing these folders but it says I dont have permission to change it or its parent folders

---

### Post by Roel1963 on 2008-05-23
> **Sevy said:**
> I try removing these folders but it says I dont have permission to change it or its parent folders

Hmmm this sort of ends my capabilities to help you out...

But there MUST be others who should know how to handle this :)

---

### Post by Sevy on 2008-05-23
Ive reinstalled Gutsy and ndiswrapper and now the folders are gone.
Ive placed my inf and sys files in the home folder but when Im in the terminal I try to navigate using home /sevy-desktop (is this right?)butI get "command not found" or if I type home/sevy-desktop (without the space after home) I get "no such file or directory"

---

### Post by chili555 on 2008-05-23
Try:
/home/sevy-desktop

   that is, with a leading /

---

### Post by Sevy on 2008-05-23
I get
bash: /home/sevy-desktop: No such file or directory

---

### Post by Sevy on 2008-05-23
If I look at the properties of Desktop its location is "/home/sevy"
If I enter this in the terminal I get "bash: /home/sevy: is a directory"
What answer am I looking for so I can continue?

---

### Post by Sevy on 2008-05-23
I tried the following

sudo ndiswrapper -i ~/drivers/drivername.inf

but now its put an empty net111v2 folder in ndiswrapper and not the inf. file and I cant delete it.

I dont know whats going on
Looks like Ill have to reinstall Gutsy again!

Any ideas anyone????:confused::(:confused::mad:

---

### Post by Everywhere_at_Once on 2008-05-23
i'm having similar issues with my intel 3945.

lshw -C
```
*-network               
       description: Ethernet interface
       product: ET-131x PCI-E Ethernet Controller
       vendor: Agere Systems
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:91:14:f1:97
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=et131x ip=192.168.1.100 latency=0 module=et131x multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

---

### Post by Sevy on 2008-05-23
@Everywhere_at_Once
Are u running Gutsy?
If so,where did you get it eg. url
Im getting the impression Ive got a dodgy copy:confused::confused:

---

### Post by chili555 on 2008-05-23
> **Sevy said:**
> I tried the following

sudo ndiswrapper -i ~/drivers/drivername.inf

but now its put an empty net111v2 folder in ndiswrapper and not the inf. file and I cant delete it.

I dont know whats going on
Looks like Ill have to reinstall Gutsy again!

Any ideas anyone????:confused::(:confused::mad:You can remove it with:```
sudo ndiswrapper -r ~/drivers/drivername.inf
```Just the same command as you installed it, but with -r for remove. Did you download the .inf file to Desktop? Or where? If you think it was to Desktop, do:```
cd Desktop
ls -l
```Do you see your .inf? Or do you see a file folder called 'drivers'? If so, do:```
cd drivers
ls -l
```Now do you see net111v2.inf? If so, please do:```
sudo ndiswrapper -i net111v2.inf
```Did it work?

I have seen nothing in your posts, so far, that suggest a dodgy copy.

---

### Post by Sevy on 2008-05-23
I did> sudo ndiswrapper -i net111v2.inf
and it says it installed:)

I then did

> sudo modprobe -r ndiswrapper

and

> sudo ndiswrapper -i net111v2.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

I get

sevy@sevy-desktop:~$ sudo ndiswrapper -i net111v2 .inf
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ sudo modprobe ndiswrapper
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
sevy@sevy-desktop:~$ 

but when I type lshw -C network
no drivers are shown for my wireless connection

---

### Post by Sevy on 2008-05-23
I typed ndiswrapper -l and I get

net111v2 : driver installed
        device (0846-6A00) present (alternative driver rtl8187)

Should I try driver rtl8187 and if so how would I go about this?

---

### Post by Fenris_rising on 2008-05-23
hi there. you are very close. follow this link to the tut i used. if you have the driver cd for your dongle you need the 'inf' and the 'sys' files from it. put them in a folder called drivers as instructed from LINE 3 of the tut. its worked for my belkin, another unbranded USB adapter i have and my PCI wireless card. take your time its a good tut and you are close it seems.

[http://ubuntuforums.org/showthread.php?t=771894](http://ubuntuforums.org/showthread.php?t=771894)

---

### Post by Sevy on 2008-05-23
F***ING SORTED!!!!
Ive finally got an internet connection even if its unencrypted and the drivers not listed
Im now going for WPA
Wish me luck
:):)
Ill take a look at that Fenris_rising if I run into more problems

---

### Post by chili555 on 2008-05-23
Great! Good luck.> net111v2 : driver installed
device (0846-6A00) present **(alternative driver rtl8187)**This sometimes means that another alternate driver, in your case, rtl8187, is getting loaded. Please do:```
lsmod | grep 8187
```If nothing comes back, nothing is wrong and you can safely disregard the 'alternate driver' comment. If it is getting loaded, that is, you have a few words of text from this command, we'll need to blacklist rtl8187:```
sudo gedit /etc/modprobe.d/blacklist
```Add a new line:```
blacklist rtl8187
```Save and close gedit. Then do:```
sudo rmmod rtl8187
```You should be good to go.

---

### Post by Sevy on 2008-05-23
When I was recieving the internet connection before it was from my neighbours router:(
Ive done what you suggested chilli555 but when I type lshw -C network I only get the Ethernet interface and not my wireless interface:confused:

---

### Post by chili555 on 2008-05-23
Please follow through on the post above concerning rtl8187, and then do:```
**sudo** lshw -C network
```Let me know. Are you able to connect, nonetheless?

---

### Post by Sevy on 2008-05-24
rtl8187 is sucessfully blacklisted and when I scan, net111v2 driver is installed but Im not getting a light on my adaptor


I try connecting to my router unencrypted but I get the following

sevy@sevy-desktop:~$ sudo ifconfig wlan0 down
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:6c:b6:51:86
Sending on   LPF/wlan0/00:14:6c:b6:51:86
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ sudo ifconfig wlan0 up
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ sudo iwconfig wlan0 essid "UXBRIDGE"
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ sudo iwconfig wlan0 mode Managed
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ sudo dhclient wlan0

I do the following but get no result

sevy@sevy-desktop:~$ sudo iwlist wlan0 scan
wlan0     No scan results

---

### Post by chili555 on 2008-05-24
Is ndiswrapper getting loaded? Plaese do:```
lsmod | grep ndiswrapper
```If you get no output, that means ndiswrapper did not load. Please do:```
sudo modprobe ndiswrapper
```Did the light come on? Do your commands above now work? If so, you can fix this with *sudo gedit /etc/modules* and add a new line:```
ndiswrapper
```When you start up again, ndiswrapper will load automatically.

---

### Post by Sevy on 2008-05-24
I assume ndiswrapper is loading,I get-

sevy@sevy-desktop:~$ lsmod | grep ndiswrapper
ndiswrapper           193436  0 
usbcore               138632  5 ndiswrapper,usb_storage,libusual,uhci_hcd
sevy@sevy-desktop:~$ 

The light still doesnt come on and I get the same "network is unreachable"
ndiswrapper is already in sudo gedit /etc/modules

---

### Post by chili555 on 2008-05-24
May I please see your *ifconfig?* Thanks.

---

### Post by Sevy on 2008-05-24
Doesnt look right to me

sevy@sevy-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:F5:11:07:E3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1408 (1.3 KB)  TX bytes:1408 (1.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:6C:B6:51:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:14:6C:B6:51:86  
          inet addr:169.254.6.241  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

---

### Post by Sevy on 2008-05-25
bump :)

---

### Post by Sevy on 2008-05-25
OK, Ive started from scratch and had some sucess.(see code below)
If I do a scan the net111v2 driver doesnt show up even if I blacklist rtl8187.
I try to connect unencrypted and am sucessfull,but I get 2 errors-
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801


chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory

Will these 2 errors effect my connection particulary If I use WPA encrytion(which I need) and if so how can I remedy this?




sevy@sevy-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth0
       version: 10
       serial: 00:90:f5:11:07:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:6c:b6:51:86
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
sevy@sevy-desktop:~$ sudo ifconfig wlan0 down
[sudo] password for sevy:
sevy@sevy-desktop:~$ sudo ifconfig wlan0 down
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:6c:b6:51:86
Sending on   LPF/wlan0/00:14:6c:b6:51:86
Sending on   Socket/fallback
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ sudo ifconfig wlan0 up
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ sudo iwconfig wlan0 essid "UXBRIDGE"
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ sudo iwconfig wlan0 mode Managed
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:6c:b6:51:86
Sending on   LPF/wlan0/00:14:6c:b6:51:86
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
grep: /etc/resolv.conf: No such file or directory
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory
bound to 192.168.0.3 -- renewal in 122953 seconds.
sevy@sevy-desktop:~$ 

:)

---

### Post by Sevy on 2008-05-25
Ive successfully connected unencrypted and WEP.:):)
Im having problems connecting using WEP with static IP,while going through one of the stickies.
Could someone possibly simplify this process??
:)

---

### Post by Sevy on 2008-05-26
I recieve the following errors when I try to connect WPA with static ip

sevy@sevy-desktop:~$ auto wlan0
bash: auto: command not found
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ iface wlan0 inet static
bash: iface: command not found
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ address 192.168.0.4
bash: address: command not found
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ gateway 192.168.0.1 
bash: gateway: command not found
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ dns-nameservers 192.168.0.1
bash: dns-nameservers: command not found
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ netmask 255.255.255.0
The program 'netmask' is currently not installed.  You can install it by typing:
sudo apt-get install netmask
You will have to enable component called 'universe'
bash: netmask: command not found
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ wpa-driver wext
bash: wpa-driver: command not found
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ wpa-ssid UXBRIDGE
bash: wpa-ssid: command not found
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ wpa-ap-scan 2
bash: wpa-ap-scan: command not found
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ wpa-proto WPA
bash: wpa-proto: command not found
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ wpa-pairwise TKIP
bash: wpa-pairwise: command not found
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ wpa-group TKIP
bash: wpa-group: command not found
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ wpa-key-mgmt WPA-PSK
bash: wpa-key-mgmt: command not found
sevy@sevy-desktop:~$ 
sevy@sevy-desktop:~$ wpa-psk 86bd98742279f4a1a0cf85c8f63f9ec9a72013568ff2f606e9b33c73b4f5155b

---

### Post by chili555 on 2008-05-26
These are undoubtedly lines that are to be added to */etc/network/interfaces*, please go back and double-check whatever tutorial you are reading.

---

### Post by Sevy on 2008-05-26
I have the following in my interfaces.before I added this I had the first 2 lines-

auto lo
iface lo inet loopback

but not

auto wlan0
iface wlan0 inet dhcp 

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.0.4
gateway 192.168.0.1 
dns-nameservers 192.168.0.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid UXBRIDGE
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 86bd98742279f4a1a0cf85c8f63f9ec9a72013568ff2f606e9b33c73b4f5155b

---

### Post by chili555 on 2008-05-27
For the information of the searchers, Sevy got his wireless working using the Windows 98 driver from here: [http://kbserver.netgear.com/release_notes/D102843.asp](http://kbserver.netgear.com/release_notes/D102843.asp)

Unzip the file and find the WIN98 .inf. After installing, and a *sudo /etc/init.d/networking restart* and with a manually configured */etc/network/interfaces* file, the wireless started perfectly. It would not survive a reboot without the fix here: [http://ubuntuforums.org/showthread.php?p=4843394&highlight=rc.local#post4843394](http://ubuntuforums.org/showthread.php?p=4843394&highlight=rc.local#post4843394)

Everthing works as expected. WPA work fine with the WIN98 driver.

---

### Post by robjbrooker on 2008-06-10
If it isn't too much trouble, could the entire successful process be put into some sort  of instruction list?  I get the impression that a lot of people could use a guide like this (myself included)

---

