---
title: "internet connection"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by juzzy on 2008-12-04
Hi 
wonder if anyone can help?

i have installed ubuntu hardy on a toshiba laptop using the realtek 8101e network card and it doesnt seem to see the card.  I cant get a connection either by ethernet or wireless, please help????

regards
j

---

### Post by gabril on 2008-12-04
oooh thats a hard one... only solution i found EVER (reservation for wrongness) is to use ndiswrapper! Its far from optimal but it gives you a headstart of acutally HAVING a working connection to the internet! google it for your make! Its in apt!

---

### Post by juzzy on 2008-12-04
tried sudo apt-get install ndiswrapper but it says it cant find the package hmmm??? im stumped!!

---

### Post by theozzlives on 2008-12-04
It says it can't find the package because you're not on the net, do you have a different nic, or connect via PPP

---

### Post by juzzy on 2008-12-04
thanks for your replies so far guys, i dont have a ppp connection and the network card (as shown in windows xp device manager) is a realtek 8102e

---

### Post by aggiemarine07 on 2008-12-04
try this to get ndiswrapper on your system because as gabril stated above while ndiswrapper isnt perfect it does do the job fairly well.

Try this:

put your ubuntu install cd in the cd drive

then go to System-->Administration--> software Sources 

on the first screen that shows ("ubuntu software") look at the bottom where it says ubuntu cd and check the box next to it and finally click ok. it will then update its source and it might post an error since your not on the internet (but thats ok)

then open a terminal and type "sudo apt-get install ndiswrapper" (without the quotes) and see if it installs ndiswrapper.

try this and let me know if it works or doesnt work in which we will try something else.

---

### Post by juzzy on 2008-12-04
ok thank you, i'll try that now and get back to you with the results

---

### Post by Michael.Godawski on 2008-12-04
If you manage to add the Ubuntu to your sources also search for the package 

```
ndisgtk
```

it is the graphical front end to the ndiswrappaer utility and it makes the installation easier.

---

### Post by juzzy on 2008-12-04
ok i tried that but no luck im afraid, it still says cant find the package

---

### Post by juzzy on 2008-12-04
aha did the ndisgtk and it seems  to have set up ndiswwrapper, what is my next step???

---

### Post by aggiemarine07 on 2008-12-04
what command did you type?

to install ndiswrapper you need to use this command:

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

---

### Post by Michael.Godawski on 2008-12-04
Ndiswrapper (ndisgkt) needs windows wlan drivers. Search the internet for the windows drivers for you wlan card, looking especially for inf and sys files.

I guess the .inf file is the needed one.

Then you have to point ndisgtk to the downloaded . inf file.

---

### Post by juzzy on 2008-12-04
thank you everyone for your replies so far, i'll start the hunt for the driver files and post back my progress

---

### Post by juzzy on 2008-12-04
ok ive located the .inf file and got it  into ubuntu desktop, tried ndiswrapper from the terminal and it has pointed me to line 219 of the ndiswrapper-1.9, it appears im to insert the inf filename here somwhere? is this correct and if so where exactly should i place it in the code, thanks.

---

### Post by Michael.Godawski on 2008-12-04
What happens if you use the graphical way via ndisgtk?

---

### Post by juzzy on 2008-12-04
tried the ndisgtk and it says invalid driver, hmmm????

---

### Post by Michael.Godawski on 2008-12-04
Can you please post the result of these terminal commands:

```
sudo lshw -C network
```

and also post the link from the page where you have downloaded the drivers?

---

### Post by halitech on 2008-12-04
I believe you need the .inf and the .sys files (if I'm remembering right) in order to install the drivers. the .inf files are just text files with basic info, the .sys files have the actual parts to make it work.

---

### Post by juzzy on 2008-12-04
this is the output you asked for

rhys@rhys-laptop:~$ sudo lshw -C network
[sudo] password for rhys: 
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:43:a3:5e
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half ip=192.168.1.65 latency=0 link=no module=r8169 multicast=yes port=twisted pair

---

### Post by halitech on 2008-12-04
just out of curiousity, what do you get for a result of```
sudo ifconfig
```

---

### Post by juzzy on 2008-12-04
here is the ifconfig output

eth0      Link encap:Ethernet  HWaddr 00:1e:33:43:a3:5e  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:33ff:fe43:a35e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967282 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60192 (58.7 KB)  TX bytes:60192 (58.7 KB)

---

### Post by halitech on 2008-12-04
maybe I'm reading this wrong but this [color="red"]inet addr:192.168.1.65 Bcast:192.168.1.255 Mask:255.255.255.0[/color] makes it look to me that you have an ip address on the NIC. do you have more then 1 NIC?

---

### Post by juzzy on 2008-12-04
it has the ethernet card and the wireless card but none are working

---

### Post by juzzy on 2008-12-04
i should add that they work perfectly on the windows xp partiton

---

### Post by halitech on 2008-12-04
so the ethernet card is plugged in?

if it is, open a terminal and see if you can ping the router
```
ping 192.168.1.1
```

if that works, then try to ping google.com and post the results

---

### Post by juzzy on 2008-12-04
cant ping anything there is no connection at all

---

### Post by Michael.Godawski on 2008-12-04
... and please post also the result of:

```
iwconfig
```

---

### Post by theozzlives on 2008-12-04
go to system>administration>windows (something), then provide the path to your windows drivers

---

### Post by halitech on 2008-12-04
can you also post the output of```
cat /etc/network/interfaces
```

---

### Post by juzzy on 2008-12-04
output from iwconfig

lo    no wireless extensions. 

eth0    no wireless extensions

---

### Post by juzzy on 2008-12-04
output of cat /etc/network/interfaces

auto lo 
iface lo inet loopback




iface eth0 inet static
address 192.168.1.65
netmask 255.255.255.0
gateway 192.168.1.254

auto eth0

---

### Post by halitech on 2008-12-04
ok, maybe the static configuration is the problem

```
gksu gedit /etc/network/interfaces
``` and change it to 
```
iface eth0 inet dhcp
```
then restart the networking

```
sudo /etc/init.d/network
```

---

### Post by juzzy on 2008-12-04
no that didnt seem to work sorry, ho hum, what should i do next?

---

### Post by halitech on 2008-12-04
what is the output of sudo ifconfig now?

---

### Post by juzzy on 2008-12-04
here is the ifconfig output its the same as before

eth0 Link encap:Ethernet HWaddr 00:1e:33:43:a3:5e
inet addr:192.168.1.65 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::21e:33ff:fe43:a35e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:4294967282 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:221 Base address:0xa000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1200 errors:0 dropped:0 overruns:0 frame:0
TX packets:1200 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:60192 (58.7 KB) TX bytes:60192 (58.7 KB)

---

### Post by halitech on 2008-12-04
ok, so if the router is now assigning the IP address and you still can't get a web page, there is something else going on. can you ping the router by IP?

---

### Post by juzzy on 2008-12-04
cant ping the router at all and when trying ndiswrapper it says that the wireless driver is already installed but hardware not present

---

### Post by halitech on 2008-12-04
what kind of wireless card are  you using?

---

### Post by juzzy on 2008-12-04
this is the hardware

realtek rtl8187b wireless 802.11b/g 54mbps usb 2.0 network adapter

realtek rtl8102e family PCI-E fast ethernet NIC

---

### Post by halitech on 2008-12-04
ok, in a terminal post the output of
```
sudo lsusb
```
and
```
sudo lspci
```

---

### Post by juzzy on 2008-12-04
Here is the output for lsusb and lspci, im really grateful for your patience here

: 
Bus 007 Device 002: ID 0bda:8198 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
rhys@rhys-laptop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

---

### Post by juzzy on 2008-12-04
has anyone got any idea what the problem might be here, i cant figure it out, but it looks to me as if the driver doesnt recognise the hardware, hmmm, its a difficult one!

---

### Post by halitech on 2008-12-04
what driver were you trying to use with NDSIWrapper?

from what I can find, looks like this thread has info on resolving your issue

[http://ubuntuforums.org/showthread.php?t=879965](http://ubuntuforums.org/showthread.php?t=879965)

---

### Post by juzzy on 2008-12-04
thank you halitech youve been a great help and to everyone else, your input is appreciated.  I'll follow that link and post back here when im done.

---

### Post by halitech on 2008-12-04
welcome and yes please do let us know. hopefully the link that is provided in the other thread is still valid.

---

### Post by juzzy on 2008-12-04
ok guys managed to find a solution with your help by downloading the driver from here [http://rapidshare.com/files/152036377/rtl8187b_linux_driver_modified_for_0bda-8198_darck.zip.html](http://rapidshare.com/files/152036377/rtl8187b_linux_driver_modified_for_0bda-8198_darck.zip.html) and extracting the zip file to root then navigate to that directory (i just created a folder of the same name as the zip folder)

sudo apt-get install makedrv
sudo makedrv
sudo apt-get install wlan0up
sudo ./wlan0up

This has provided a temporary fix but have to re-enter the commands on each boot and gives low signal. im sure there is a fix for this problem somwhere...can anyone point me in the right direction

but at least we have connectivity now which should make the rest a little easier.  Thanks again to all who helped.

---

### Post by halitech on 2008-12-04
glad to hear that helped :)

please mark this thread solved so others searching will know.

---

### Post by juzzy on 2008-12-06
Thanks again everyone, much appreciated.

---

