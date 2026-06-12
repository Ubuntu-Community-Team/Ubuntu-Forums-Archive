---
title: "Another iwl3945 issue"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by D.r.e.a.m on 2008-05-26
Hello,


As a newbie to Ubuntu, Internet is one of the first to try. I could do that only with a wired connection because I can't detect any wireless netowrk.

I have Intel Pro/wireless 3945ABG card and the driver is iwl3945. I tried many solutions mentioned here in the forum such as

> sudo apt-get install linux-backports-modules-hardy-generic

Installing WICD

Switching to the old Kernel

without use.


Then I talked to Chili555 asking him to help me in switching back to ipw3945. But he could solve the problem using the same driver iwl3945.

The solution is:

> 1.sudo su

2.echo -e “alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1&#8243; > /etc/modprobe.d/iwl3945

3.reboot

This solution was mentioned in some other forum. After rebooting everything was perfect thanks to chili555 and Cyber-Hero.


Cheers

---

### Post by chili555 on 2008-05-26
The hints that you may be helped by this are no can results, then:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo iwlist wlan0 scan
```And it now gets scan results! If so, please implement D.r.e.a.m's fix. Those who are searching for a fix will also appreciate your feedback.

Thank you, D.r.e.a.m, for your comments. Would you please rename the title 'SOLVED Another iwl3945 issue'? Thanks.

---

### Post by Gnodab on 2008-05-26
Opps, wrong thread...

---

### Post by chili555 on 2008-05-29
CORRECTION!

The commands are actually:```
sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
reboot
```The text should be surrounded by ' instead of ".

---

### Post by alchemist0 on 2008-06-19
> **chili555 said:**
> 

The commands are actually:```

echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945

```

is this supposed to be typed altogether in one line?
or is everything after ">" the result?
:S

---

### Post by chili555 on 2008-06-19
Type all in one line. Please proofread and especially check spaces before you press enter.

---

### Post by alchemist0 on 2008-06-19
> **chili555 said:**
> Type all in one line. Please proofread and especially check spaces before you press enter.

nope......didnt work.....the led lights up while ubuntu is loading, but when i log in it turns off.....i switch on/off without result, i tried fn+f8 (toshibas keyboard switch) but no results either.........IM DESPERATE!

---

### Post by chili555 on 2008-06-19
How about letting us see:```
iwconfig
sudo cat /var/log/messages | grep switch
dmesg | grep wlan0
```Thanks.

---

### Post by alchemist0 on 2008-06-19
here comes....

```
jim@jim-laptop:~$ sudo su
[sudo] password for jim: 
root@jim-laptop:/home/jim# echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
root@jim-laptop:/home/jim# echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
root@jim-laptop:/home/jim# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@jim-laptop:/home/jim# sudo cat /var/log/messages | grep switch
Jun 18 09:09:35 jim-laptop kernel: [   14.079474] SMP alternatives: switching to UP code
Jun 18 09:09:35 jim-laptop kernel: [   14.856134] SMP alternatives: switching to SMP code
Jun 18 09:09:35 jim-laptop kernel: [   18.811005] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 18 09:51:17 jim-laptop kernel: [   13.274324] SMP alternatives: switching to UP code
Jun 18 09:51:17 jim-laptop kernel: [   14.055713] SMP alternatives: switching to SMP code
Jun 18 09:51:17 jim-laptop kernel: [   18.034461] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 18 10:04:32 jim-laptop kernel: [  194.851001] SMP alternatives: switching to UP code
Jun 18 10:04:32 jim-laptop kernel: [    0.405967] SMP alternatives: switching to SMP code
Jun 18 10:10:35 jim-laptop kernel: [   14.071384] SMP alternatives: switching to UP code
Jun 18 10:10:35 jim-laptop kernel: [   14.847745] SMP alternatives: switching to SMP code
Jun 18 10:10:35 jim-laptop kernel: [   18.808172] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 18 10:37:17 jim-laptop kernel: [   14.475814] SMP alternatives: switching to UP code
Jun 18 10:37:17 jim-laptop kernel: [   15.252312] SMP alternatives: switching to SMP code
Jun 18 10:37:17 jim-laptop kernel: [   19.312626] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 18 10:47:30 jim-laptop kernel: [   14.555902] SMP alternatives: switching to UP code
Jun 18 10:47:30 jim-laptop kernel: [   15.332413] SMP alternatives: switching to SMP code
Jun 18 10:47:30 jim-laptop kernel: [   19.312777] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 18 10:50:50 jim-laptop kernel: [   14.643983] SMP alternatives: switching to UP code
Jun 18 10:50:50 jim-laptop kernel: [   15.420234] SMP alternatives: switching to SMP code
Jun 18 10:50:50 jim-laptop kernel: [   19.568814] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 18 13:48:55 jim-laptop kernel: [   14.028349] SMP alternatives: switching to UP code
Jun 18 13:48:55 jim-laptop kernel: [   14.804822] SMP alternatives: switching to SMP code
Jun 18 13:48:55 jim-laptop kernel: [   18.812708] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 18 20:42:45 jim-laptop kernel: [   13.730114] SMP alternatives: switching to UP code
Jun 18 20:42:45 jim-laptop kernel: [   14.506419] SMP alternatives: switching to SMP code
Jun 18 20:42:45 jim-laptop kernel: [   18.546911] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 19 01:14:04 jim-laptop kernel: [   13.194698] SMP alternatives: switching to UP code
Jun 19 01:14:04 jim-laptop kernel: [   13.581908] SMP alternatives: switching to SMP code
Jun 19 01:14:04 jim-laptop kernel: [   16.510800] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 19 13:05:58 jim-laptop kernel: [   14.085582] SMP alternatives: switching to UP code
Jun 19 13:05:58 jim-laptop kernel: [   14.478496] SMP alternatives: switching to SMP code
Jun 19 13:05:58 jim-laptop kernel: [   17.276850] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 19 13:16:44 jim-laptop kernel: [   13.523101] SMP alternatives: switching to UP code
Jun 19 13:16:44 jim-laptop kernel: [   13.910464] SMP alternatives: switching to SMP code
Jun 19 13:16:44 jim-laptop kernel: [   16.765231] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 19 13:37:39 jim-laptop kernel: [   13.690107] SMP alternatives: switching to UP code
Jun 19 13:37:39 jim-laptop kernel: [   14.077647] SMP alternatives: switching to SMP code
Jun 19 13:37:39 jim-laptop kernel: [   17.018777] ACPI: EC: non-query interrupt received, switching to interrupt mode
root@jim-laptop:/home/jim# dmesg | grep wlan0
root@jim-laptop:/home/jim# dmesg | grep wlan0
root@jim-laptop:/home/jim# 

```

Thanks for everything....:)

---

### Post by chili555 on 2008-06-19
> root@jim-laptop:/home/jim# echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
root@jim-laptop:/home/jim# echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945Did you actually do this command two or more times? This is not a command to wake up the card, it's a command to edit a configuration file. It does no good, and may do some harm, to have multiple repetitions of the required parameters.

May I please see:```
sudo lshw -C network
```Thanks.

---

### Post by alchemist0 on 2008-06-19
oooooooooooops!!!hhhehehe! didnt know! I saw no warning up there so i guessed there wouldnt be a problem....anyway here it is:

```
root@jim-laptop:/home/jim# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 10
       serial: 00:1e:8c:fe:5b:d9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.7 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

```

:D

---

### Post by chili555 on 2008-06-19
Evidently you have no wireless card! Is wireless disabled in the computer's BIOS? Let's get the card recognized first, and then address any oops.

---

### Post by alchemist0 on 2008-06-19
ooooooooooooooooooooooops~:-\":-\"
heheheh!

---

### Post by chili555 on 2008-06-19
So does that mean your wireless works? Shall we fix your */etc/modprobe.d/iwl3945* file now?

---

### Post by alchemist0 on 2008-06-19
nnnnnnnnnnnnnnopes!
dead as a rotten carcass......its funny, u know, cuz the wireless worked smoothly in vista (vista???plz god dont let me make the same mistake again), but now, heron, as i told ya, seems to detect it at startup....but then...POOF! Gone! Darkness......guess im doomed......heh.....

---

### Post by chili555 on 2008-06-19
Well, there is certainly the possibility that the card has died, but that seems a bit remote. Let's see if the kernel has thrown up any messages about it while booting:```
dmesg | grep 3945
sudo cat /var/log/messages | grep -i wireless
```While we are at it, let's erase our previous Oops.```
sudo rm /etc/modprobe.d/iwl3945
```You might also try booting from the live CD and see if the card is recognized there, even if it doesn't connect. Check with our old pal:```
sudo lshw -C network
```

---

### Post by alchemist0 on 2008-06-19
A-ha! this must be something.....

```
jim@jim-laptop:~$ dmesg | grep 3945
[   15.493945] serio: i8042 KBD port at 0x60,0x64 irq 1
jim@jim-laptop:~$ sudo cat /var/log/messages | grep -i wireless
[sudo] password for jim: 
Jun 19 13:02:02 jim-laptop kernel: [ 8990.789598] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 19 13:11:26 jim-laptop kernel: [  164.436498] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
Jun 19 13:19:25 jim-laptop kernel: [  104.681980] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
Jun 19 13:20:16 jim-laptop kernel: [  111.705988] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25

```
another oops while deleting previous oops up there...
however.....cool! that means there's something there, right? (keep in mind that yesterday i tried to install several drivers i found in several forums....oops on that!)
Thanx again dear ubuntu master!:)

::EDIT:: gonna try the liveCD and ill tell u l8r about the results....:)

---

### Post by alchemist0 on 2008-06-19
nopes again.....live cd results:

```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 10
       serial: 00:1e:8c:fe:5b:d9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.7 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

```

now what?:(

---

### Post by alchemist0 on 2008-06-19
Knoppix wont find anything either............

::EDIT:: .............but with suse livecd 9.2 hardware manager, I found: 
REALTEK RTL8187B_WLAN_Adapter

hmm....this sounds promising.....

::EDIT2:: yeah this is the one....the ethernet cotroller is a toshiba model, so this is the wireless card....however, this one is listed under usb....and the fuuny thing is that, yesterday i read about it, but didnt really believe it......hmm....

check this one too:
>  Vendor: usb 0x0bda "RealTek Semiconductor Corp."
  Device: usb 0x8197 "RTL8187B_WLAN_Adapter"
  Revision: "2.00"
  Serial ID: "00e04c000001"
  Speed: 1.5 Mbps
  Config Status: cfg=no, avail=yes, need=no, active=yes
  Attached to: #34 (Hub)

...however i still dont have wireless connections....(im still using suse right now)...

---

### Post by zzandeamos on 2008-06-19
Chili;
I have the same appearent problem using Intel PRO iwl3945abg.  I have tried so many things I am lost. This much I know for sure: The wired eth0 works fine and always has.  The wireless works fine on an open net (Iwent to the library and it worked great).  At home I have an encrypted net with an older Gateway laptop with a Belkin PCMCIA wireless card that works fine, also a wired desktop,(no problem).  I got this laptop last fall and it was on Ubuntu 7.04 it worked fine.  I did not use the wireless from about Dec '07 til May of '08 then the wireless would not work.  So for the last month I have been haunting the net to try to figure it out, trying anything and everything that sounds close.  No luck.  I need guidance, direction, help of some kind.  I will include the basic stuff here and if you can help I would appreciate it very much.


fdc@fdc-laptop:~$ sudo lshw -C network
[sudo] password for fdc: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:85:1c:48
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 10
       serial: 00:1b:fc:d1:e2:f0
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.77 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
fdc@fdc-laptop:~$ 

fdc@fdc-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:95:C4:15:C1
                    ESSID:"2WIRE759"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/100  Signal level=-64 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000043b6fbab48

fdc@fdc-laptop:~$ 

fdc@fdc-laptop:~$ uname -a
Linux fdc-laptop 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux
fdc@fdc-laptop:~$ 
 

fdc@fdc-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
05:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
05:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
05:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
fdc@fdc-laptop:~$ 


Please let me know what else you need, I am at your command.

---

### Post by chili555 on 2008-06-20
With the CAT5 wire disconnected, what do you get when you open a terminal and do:```
sudo iwconfig wlan0 essid 2WIRE759
sudo iwconfig wlan0 key <your_verified_key>
sudo dhclient wlan0
```Please verify your key in the administration page of the router. Hex or ASCII? 64- or 128-bit? 

Your lshw and other listings look healthy.

@alchemist0

I suggest you start a new thread asking about your Realtek 8187 wireless.

---

### Post by zzandeamos on 2008-06-20
Chili555:
Thank you for the prompt response.

[QUOTE=chili555;5224957]With the CAT5 wire disconnected, what do you get when you open a terminal and do:```
sudo iwconfig wlan0 essid 2WIRE759
sudo iwconfig wlan0 key <your_verified_key>
sudo dhclient wlan0
```Please verify your key in the administration page of the router. Hex or ASCII? 64- or 128-bit? 

Your lshw and other listings look healthy.

It looks like the first two requests didn't yeild anything, and I am not sure what the admin page of the router is.  I need some direction to get to it.  

fdc@fdc-laptop:~$ sudo iwconfig wlan0 essid 2WIRE759
fdc@fdc-laptop:~$ sudo iwconfig wlan0 key 5144999703
fdc@fdc-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:77:85:1c:48
Sending on   LPF/wlan0/00:1b:77:85:1c:48
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
fdc@fdc-laptop:~$

---

### Post by karlatsaic on 2008-06-20
I also get EXACTLY the same behavior as noted in the previous reply. I think the iwl3945 driver is just too immature for prime time. I have a dell xps m1330 and am trying to get Hardy 8.04 clean install to work. This laptop came with gutsy 7.10 pre-installed and everything worked (it uses the restricted driver ipw3945). I just noticed about 5 minutes ago that today's (6/20/08) updates now cause wireless to break in 7.10 as well. I'm guessing there was a kernel upgrade and a switch to the iwl3945 driver for gutsy as well.

I have tried many of the suggestions in this thread + some other things found in these forums (ndiswrapper + windows drivers), manually connecting, ... and nothing really seems to work. This is a common wireless interface and I hope there will be a good driver update soon. I will probably go back to the dell 7.10 iso which came with this laptop and just avoid the latest kernel updates until iwl3945 gains a further level of maturity.

---

### Post by zzandeamos on 2008-06-20
Chili555;
I got the wep key off the modem/router. It is on the bottom with the serial number.  Is this modem the problem? It is a Qwest 2wire 2700HG-D. I have been doing some looking and it looks like maybe it will only take one wireless connection, could that be right?

---

### Post by chili555 on 2008-06-20
> **zzandeamos said:**
> Chili555;
I got the wep key off the modem/router. It is on the bottom with the serial number.  Is this modem the problem? It is a Qwest 2wire 2700HG-D. I have been doing some looking and it looks like maybe it will only take one wireless connection, could that be right?That's certainly a possibility. I've seen stranger things in my life! If I had to bet money on it, I have to say I doubt it.

If you got this from your internet service provider and you are still using the default values, I doubt that it has any limitations or filtering in place. I'd go into the administration pages for the router and check. Hook up a machine with an ethernet cable, if you haven't already. Here is a link that discusses your router: [http://www.avvanta.com/QDSLSupportFAQ2700HGDWireless](http://www.avvanta.com/QDSLSupportFAQ2700HGDWireless)

Before you change anything, I'd check to see if the WEP key is correct and if the authentication method is 'Open' or 'Shared.' It looks, reading between the lines, like the router is set up for 'Shared.' In that case, before you tinker with the router, you might try:```
sudo iwconfig wlan0 essid 2WIRE759
sudo iwconfig wlan0 key 5144999703 **restricted**
sudo dhclient wlan0
```Let us know.

---

### Post by zzandeamos on 2008-06-20
you might try:```
sudo iwconfig wlan0 essid 2WIRE759
sudo iwconfig wlan0 key 5144999703 **restricted**
sudo dhclient wlan0
```Let us know.[/QUOTE]

Chili555
I got the same result as shown above except with the 'restricted' in it.  I can post it if you wish.  Below is the results of the modem/router info.

EDIT 6/21:
I looked around that web site you gave me(above) and agree with you 'I don't think it is the modem'.  Good info though.
			
Network Name: 	
Warning
Wireless Channel: 	
Enable
	SSID Broadcast
Enables the wireless network name to be broadcast publicly to any wireless users within wireless range of your network. Disabling the SSID broadcast makes the network name private and provides enhanced security by requiring wireless users to enter the network name manually when creating a wireless network profile on their computer.
Wireless Security
Enable
	Wireless Network Security
	Authentication: 	
		Use default encryption key
		Use custom encryption key
	Key: 	
Warning
Additional Settings (defaults recommended)
Wireless Mode: 	
	
DTIM Period (seconds): 	
Warning
	
Maximum Connection Rate: 	
	
Power Setting: 	
	
	
Help
Current Settings
Access Point: 	00:14:95:c4:15:c1
Network Name: 	2WIRE759
Channel: 	6 (2437 MHz)
Authentication: 	WEP-Open
Encryption: 	WEP

To locate the built-in, 10-digit wireless encryption key for your system, please look at the bottom of the product near the bar code label:

As you can see the authentication is WEP-Open and the ssid broadcast is enabled.

---

### Post by zzandeamos on 2008-06-21
Chili555:

After looking at these two outputs they do not look just the same so I am including the last request you sent with the 'restricted' in it.

fdc@fdc-laptop:~$ sudo iwconfig wlan0 essid 2WIRE759
fdc@fdc-laptop:~$ sudo iwconfig wlan0 key 5144999703 restricted
fdc@fdc-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6692
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:77:85:1c:48
Sending on   LPF/wlan0/00:1b:77:85:1c:48
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.76 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.0.76 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
Trying recorded lease 192.168.0.76
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
fdc@fdc-laptop:~$ 

Thanks for your patience.

---

### Post by zzandeamos on 2008-06-21
Chili555:
O.K. I edited the router and disabled encryption and my ubuntu worked just fine. However it torpedoed the other wireless laptop on the lan.  So I had to change it back so her wireless works and mine don't.


So now when I start the wireless network "2WIRE759" the icon on the upper right   shows two little dots(circles) with a shadow swimming in a cirle through them.   
After a couple orbits the lower left light changes black to blue but the upper right one does not. It just loops there for over 1-1/2 minute (I didn't wait longer). If I put the cursor on the icon a 'tool tip' type of msg comes up saying 'waiting for network password for network "2WIRE759"'. This is the same as it used to do but since we put in the "restricted" it does not time out and present a window that wants the passphrase again after about 60-70 seconds.  
EDIT.......
No I'm wrong, it does time out and ask again for the passphrase.  I just didn't let it go long enough before. 
zzandeamos

---

### Post by karlatsaic on 2008-06-23
Interestingly, I upgraded my ancient, but trusty, linksys 802.11b wireless router to a linksys 802.11n model (WRT160N) and the iwl3945 works perfectly. I was suspicious that 'lshw - C network' showed Wireless=IEEE 802.11g with this driver (instead of b). Since I was planning this upgrade anyway, my issues with iwl3945 are now solved.

---

### Post by chili555 on 2008-06-23
> **zzandeamos said:**
> Chili555:
O.K. I edited the router and disabled encryption and my ubuntu worked just fine. However it torpedoed the other wireless laptop on the lan.  So I had to change it back so her wireless works and mine don't.


So now when I start the wireless network "2WIRE759" the icon on the upper right   shows two little dots(circles) with a shadow swimming in a cirle through them.   
After a couple orbits the lower left light changes black to blue but the upper right one does not. It just loops there for over 1-1/2 minute (I didn't wait longer). If I put the cursor on the icon a 'tool tip' type of msg comes up saying 'waiting for network password for network "2WIRE759"'. This is the same as it used to do but since we put in the "restricted" it does not time out and present a window that wants the passphrase again after about 60-70 seconds.  
EDIT.......
No I'm wrong, it does time out and ask again for the passphrase.  I just didn't let it go long enough before. 
zzandeamosOne other thing to try, before I smash my laptop, running a perfect 3945ABG! Please do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```If you can now connect, we can make this permanent.

---

### Post by zzandeamos on 2008-06-23
> **chili555 said:**
> One other thing to try, before I smash my laptop, running a perfect 3945ABG! Please do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```If you can now connect, we can make this permanent.

Well I put this in...

fdc@fdc-laptop:~$ sudo rmmod -f iwl3945
[sudo] password for fdc: 
fdc@fdc-laptop:~$ sudo modprobe iwl3945 disable_hw_scan=1
fdc@fdc-laptop:~$ 

But no luck.  I tried a reboot and that did not work but I the last line on your post indicates that so I re-did it and still no luck.

---

### Post by chili555 on 2008-06-24
If your */etc/network/interfaces* contains 'restricted' please remove it, as we have determined that your network is:> Authentication: WEP-Open> 'waiting for network password for network "2WIRE759"'.I am not sure I really understand this. If you are using Network Manager, I think you should drop down the menu and select 'WEP 40/128-bit hex', select 'Open' and put in your key: 5144999703. Have you tried it this way or am I misreading your post?

---

### Post by zzandeamos on 2008-06-24
Chili555:
I am not using network manager.  This was a new install when I started this thread as I had been trying some other distros and had just put 8.04 back on.  I'm sorry for this confusion, I guess I didn't make it very clear at the start.   
I was trying to see if any distro would work with the wireless.  Puppy linux did fine. 
Also looking through some other posts I noticed the 'install backports-hardy-generic' business has not been installed since I  reloaded 8.04.

---

### Post by chili555 on 2008-06-24
> **zzandeamos said:**
> Chili555:
O.K. I edited the router and disabled encryption and my ubuntu worked just fine. However it torpedoed the other wireless laptop on the lan.  So I had to change it back so her wireless works and mine don't.


**So now when I start the wireless network "2WIRE759" the icon on the upper right   shows two little dots(circles) with a shadow swimming in a cirle through them.**   
After a couple orbits the lower left light changes black to blue but the upper right one does not. It just loops there for over 1-1/2 minute (I didn't wait longer). If I put the cursor on the icon a 'tool tip' type of msg comes up saying 'waiting for network password for network "2WIRE759"'. This is the same as it used to do but since we put in the "restricted" it does not time out and present a window that wants the passphrase again after about 60-70 seconds.  
EDIT.......
No I'm wrong, it does time out and ask again for the passphrase.  I just didn't let it go long enough before. 
zzandeamosIs this not Network Manager? Am I misreading something?

---

### Post by zzandeamos on 2008-06-24
> **chili555 said:**
> If your */etc/network/interfaces* contains 'restricted' please remove it, as we have determined that your network is:I am not sure I really understand this. If you are using Network Manager, I think you should drop down the menu and select 'WEP 40/128-bit hex', select 'Open' and put in your key: 5144999703. Have you tried it this way or am I misreading your post?

Hey ... it works.  The drop down did not have "WEP 40/128-bit hex" but did have "WEP 64/HEX" and I checked that and it took off great.  

Chili55 - give yourself a banana.  I was about to give up on this.  I am at a loss it will take a bit to digest this.  In the mean while thank you - thank you...
zzandeamos.

---

### Post by chili555 on 2008-06-24
See, iwl3945 works like a chimp....er, champ! Thanks for your kind words.

---

### Post by kismeras on 2008-06-25
Ok , guys. i think i need your help please. I have been reading this thread and trying to follow along. But i haven't had any luck. I am a total Linux and CLI newbie. I'm used to windows and i don't know where to go to get anything done. There's no device manager, so i can't see my hardware. I have a bunch of text from out put that i got while trying to follow along. It's very long..so I'm sorry if I'm not supposed to post this much. I have an Acer 5672 Laptop with the Intel 3945 wireless card. I can not get it to work. I don't see anything that says enable wireless. When i slide the wireless switch on the front of the laptop the light does not come on. Also, i don't even know where to go to see available wireless networks and choose one to connect to. I am using WPA2 on my router and i am hoping i can get my wireless to work on that. This is probably my third attempt at using Linux. I've tried a few other earlier versions of Ubuntu in the past and have always just given up on it. Why can't simple things just work right out of the box? Anyway, here is the text :

xxxxx@Acer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

xxxxx@Acer:~$ sudo /var/log/messages |grep switch
[sudo] password for xxxxx: 
sudo: /var/log/messages: command not found
xxxxx@Acer:~$ dmesg | grep wlan0
xxxxx@Acer:~$

xxxxx@Acer:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:1c:dd:39
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11a
  *-network
       description: Ethernet interface
       product: NetLink BCM5789 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 21
       serial: 00:16:36:32:13:9a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5789-v3.49a ip=192.168.0.8 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
xxxxx@Acer:~$ 

xxxxx@Acer:~$ dmesg | grep 3945
[   29.941981] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   29.941986] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   29.942147] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   30.006159] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   30.650270] iwl3945: Radio disabled by HW RF Kill switch
[   30.988912] iwl3945: Radio disabled by HW RF Kill switch
[   31.199017] iwl3945: Radio disabled by HW RF Kill switch
[   31.199573] iwl3945: Radio disabled by HW RF Kill switch
[   37.658451] iwl3945: Radio disabled by HW RF Kill switch
[   57.170563] iwl3945: Radio disabled by HW RF Kill switch
[  134.254990] iwl3945: Radio disabled by HW RF Kill switch
[  215.105668] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[  220.249796] iwl3945: Radio Frequency Kill Switch is On:
[  231.129022] iwl3945: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
xxxxx@Acer:~$ sudo cat /var/log/messages | grep -i wireless
Jun 23 06:03:07 Acer kernel: [   30.335699] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 23 06:03:07 Acer kernel: [   30.335844] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Jun 23 06:03:07 Acer kernel: [   30.430917] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input8
Jun 23 06:03:07 Acer kernel: [   30.483890] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.0-1
Jun 23 06:03:07 Acer kernel: [   31.090257] Kill switch must be turned off for wireless networking to work.
Jun 23 12:12:03 Acer kernel: [   30.342747] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 23 12:12:03 Acer kernel: [   30.342895] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Jun 23 12:12:03 Acer kernel: [   30.529184] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input8
Jun 23 12:12:03 Acer kernel: [   30.577764] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.0-1
Jun 23 12:12:03 Acer kernel: [   30.907885] Kill switch must be turned off for wireless networking to work.
Jun 24 00:42:56 Acer kernel: [   29.732235] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 24 00:42:56 Acer kernel: [   29.732393] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Jun 24 00:42:56 Acer kernel: [   29.952134] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input8
Jun 24 00:42:56 Acer kernel: [   29.991501] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.0-1
Jun 24 00:42:56 Acer kernel: [   30.652803] Kill switch must be turned off for wireless networking to work.
Jun 25 05:27:01 Acer kernel: [19237.812565] Kill switch must be turned off for wireless networking to work.
Jun 25 05:34:38 Acer kernel: [19370.384355] Kill switch must be turned off for wireless networking to work.
Jun 25 11:54:18 Acer kernel: [26180.172857] Kill switch must be turned off for wireless networking to work.
Jun 25 11:54:43 Acer kernel: [26188.318091] Kill switch must be turned off for wireless networking to work.
Jun 25 11:55:02 Acer kernel: [26194.682669] Kill switch must be turned off for wireless networking to work.
Jun 25 11:55:18 Acer kernel: [26200.192297] Kill switch must be turned off for wireless networking to work.
Jun 25 12:00:38 Acer kernel: [   30.161960] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input7
Jun 25 12:00:38 Acer kernel: [   30.194563] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.0-1
Jun 25 12:00:38 Acer kernel: [   30.230586] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
Jun 25 12:00:38 Acer kernel: [   30.230743] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Jun 25 12:02:31 Acer kernel: [  112.611002] Kill switch must be turned off for wireless networking to work.
Jun 25 12:03:02 Acer kernel: [  119.807477] Kill switch must be turned off for wireless networking to work.
Jun 25 12:14:53 Acer kernel: [  410.765513] Kill switch must be turned off for wireless networking to work.
Jun 25 12:38:42 Acer kernel: [   29.999923] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
Jun 25 12:38:42 Acer kernel: [   30.000077] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Jun 25 12:38:42 Acer kernel: [   30.205507] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input8
Jun 25 12:38:42 Acer kernel: [   30.254747] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.0-1
Jun 25 12:44:38 Acer kernel: [  288.166974] Kill switch must be turned off for wireless networking to work.
Jun 25 12:46:03 Acer kernel: [   17.434893] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input2
Jun 25 12:46:03 Acer kernel: [   17.437241] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.0-1
Jun 25 12:46:03 Acer kernel: [   18.834246] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input3
Jun 25 12:46:03 Acer kernel: [   18.842710] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.0-1
Jun 25 12:46:03 Acer kernel: [   29.941981] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
Jun 25 12:46:03 Acer kernel: [   29.942147] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Jun 25 12:55:47 Acer kernel: [  220.249801] Kill switch must be turned off for wireless networking to work.
xxxxx@Acer:~$ 

:confused:

---

### Post by chili555 on 2008-06-25
> Kill switch must be turned off for wireless networking to work.That's it right there. Find and press the switch. Until that's fixed, we can go no further.

Is this an Acer laptop?

---

### Post by kismeras on 2008-06-25
@ Chili555

Yeh, it's an acer 5672. There is a sliding switch on the front that i use in windows to turn the wireless on and off. However, in Ubuntu the switch does not seem to work. It has a light that usually comes on if the wireless is on. When i slide the switch, nothing happens. I know the switch and the wireless card work, because they work in windows. Any ideas?

---

### Post by chili555 on 2008-06-26
Please try this:```
sudo su
modprobe acer_acpi
echo "enabled: 1" > /proc/acpi/acer/wireless
```Let us know.

---

### Post by kismeras on 2008-06-26
Hey Guys, 

Going out of town for a few days, so i wont be playing with Ubuntu. I'll try when i get back and let you know. Thanks.

---

### Post by henrycard on 2008-06-27
Hi guys.

I've had a lot of fun reading this post. Chili555, you have demonstrated a lot of knowledge about this Intel 3945 matter.

I also have trouble with this wireless device. With Gutsy, there were no problems because of the ipw3945 driver. With Hardy, the driver iwl recognize my corporate wireless router, no problems there. The router doesn't need authentication indeed.

It takes a looooooong loooooong time trying to connect and is unsuccessful.

I've done everything posted in this thread, but the laptop never connects.

Any help would be appreciated. Thanks in advance.

---

### Post by chili555 on 2008-06-27
> **henrycard said:**
> Hi guys.

I've had a lot of fun reading this post. Chili555, you have demonstrated a lot of knowledge about this Intel 3945 matter.

I also have trouble with this wireless device. With Gutsy, there were no problems because of the ipw3945 driver. With Hardy, the driver iwl recognize my corporate wireless router, no problems there. The router doesn't need authentication indeed.

It takes a looooooong loooooong time trying to connect and is unsuccessful.

I've done everything posted in this thread, but the laptop never connects.

Any help would be appreciated. Thanks in advance.Let's start from the easiest fix. There is evidently a better iwl3945 driver in here:```
sudo apt-get install linux-backports-modules-hardy-generic 
```If you have not done that, please do and let us know if you can now connect.

---

### Post by treeclimber on 2008-06-27
Hmmm... I've read this entire thread and many others concerning getting the 3956abg wireless to work with Hardy.  I have a Dell 1505n that worked fine until I updated to Heron.  I was using Network Manager.  It could find the connection, but wouldn't connect.  Every fix I have found has required downloading something to fix it.  I tried hooking my laptop directly to my Internet connection, but it couldn't even find it that way.  Maybe because my Internet is wireless broadband?  I don't know.

Anyhow, I ended up going back to Gutsy and the proprietary driver.  It is working fine, but I would like to upgrade.  Is there a way to get the new driver working without being on the Internet?  I've asked this before and can't seem to get an answer.  If so, How?  I would really appreciate any help.  Oh, by the way, I replaced Network Manager with Wicd and it seems to work much better.  If I upgrade instead of a clean install, will this stay on there or will it replace it with Network Manager?  Thanks again!

---

### Post by henrycard on 2008-06-27
> **chili555 said:**
> Let's start from the easiest fix. There is evidently a better iwl3945 driver in here:```
sudo apt-get install linux-backports-modules-hardy-generic 
```If you have not done that, please do and let us know if you can now connect.

Yeap.... I did that. I've the 2.6.24.18.20 version of that package. The signal appear to be stronger with this update. Anyway, the laptop can't connect.

I also did the ```
 
sudo rmmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1 
``` with no results.

As said, it recognize the spots, but never connects.

---

### Post by karlatsaic on 2008-06-30
For what it's worth, after upgrading my old wireless router (linksys BEFW11S4 - 802.11b only) to a new 802.11n (WRT160N), the iwl3945 driver which is the default in hardy (I have not done anything special with my configuration other than accept all updates) works like a charm. I think either network-manager or the driver itself was trying to connect as 802.11g instead of 802.11b [EDIT: as evident by the output of 'lshw -C network'], which was the only possibility with the old router. I hate to upgrade h/w to solve a software problem (sounds like Microsoft), but this upgrade to my home network was long overdue anyway. [EDIT: fyi - my laptop is a Dell XPS M1330, Intel Duo-core 64-bit]

---

### Post by kismeras on 2008-07-01
Hey Guys, 

I ended up reinstalling Ubuntu and it the wireless works now. However, the light on the switch still does not light up. Also, is there a wireless utility (like in windows) where you can scan for available wireless networks and pick one to connect to?

---

### Post by Creap on 2008-08-03
Is it possible this fix might work with iwl4965 aswell, what do you think?

---

### Post by chili555 on 2008-08-03
There are several fixes proposed in this thread. This one:```
sudo apt-get install linux-backports-modules-hardy-generic
```shouild help your 4965, as well. Please try it and post back.

---

### Post by dvlong on 2008-09-10
I have been working for about 2 weeks with and identical/similar ? issue.  I will post the outputs for the last few commands here - I hope I'm not in bad form or anything to just put this here - but having followed this thread, along with a few others as well, things don't seem to be going anywhere.  Hope you can help.

I'm using Hardy on a Compaq v3000 laptop with a Pro/Wireless 3945ABG.  I can connect at my work office with no problems and initially could here at my home office as well.  Then things started to just do downhill - and now the wireless won't connect at all.  I'm not sure if this could be due to regular updates or not - or if other program installation could be related.

dvlong@longslap2:~$ dmesg | grep -i iwl:
dvlong@longslap2:~$ sudo iwlist wlan0 scan
sudo: unable to resolve host longslap2
[sudo] password for dvlong:  
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:61:36:13
                    ESSID:"Raakgaew"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=77/100  Signal level=-46 dBm  Noise level=-77 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000003510feda8

dvlong@longslap2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Raakgaew"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:E5:61:36:13   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dvlong@longslap2:~$ sudo cat /var/log/messages | grep switch
sudo: unable to resolve host longslap2
Sep 10 12:30:00 longslap2 kernel: [   20.716113] SMP alternatives: switching to UP code
Sep 10 12:30:00 longslap2 kernel: [   21.147078] SMP alternatives: switching to SMP code
Sep 10 12:30:00 longslap2 kernel: [   21.363415] ACPI: EC: non-query interrupt received, switching to interrupt mode
dvlong@longslap2:~$ dmesg | grep wlan0
[   40.026176] wlan0: Initial auth_alg=0
[   40.026182] wlan0: authenticate with AP 00:1e:e5:61:36:13
[   40.027364] wlan0: RX authentication from 00:1e:e5:61:36:13 (alg=0 transaction=2 status=1)
[   40.027369] wlan0: AP denied authentication (auth_alg=0 code=1)
[   40.224832] wlan0: authenticate with AP 00:1e:e5:61:36:13
[   40.226000] wlan0: RX authentication from 00:1e:e5:61:36:13 (alg=0 transaction=2 status=1)
[   40.226004] wlan0: AP denied authentication (auth_alg=0 code=1)
[   40.424422] wlan0: authenticate with AP 00:1e:e5:61:36:13
[   40.425598] wlan0: RX authentication from 00:1e:e5:61:36:13 (alg=0 transaction=2 status=1)
[   40.425601] wlan0: AP denied authentication (auth_alg=0 code=1)
[   40.624512] wlan0: authentication with AP 00:1e:e5:61:36:13 timed out
[   41.602353] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   92.703529] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=193 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=173 
[   93.189379] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170 
[   93.648704] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=174 
[  107.491360] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=193 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=173 
[  108.490076] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170 
[  109.488783] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=174 
[  128.463356] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=193 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=173 
[  128.618465] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170 
[  129.202047] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=174 
[  135.334864] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[  135.424218] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[  135.424464] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[  135.424714] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[  135.441591] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[  136.590206] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  136.761748] wlan0: Initial auth_alg=0
[  136.761761] wlan0: authenticate with AP 00:1e:e5:61:36:13
[  136.762994] wlan0: RX authentication from 00:1e:e5:61:36:13 (alg=0 transaction=2 status=1)
[  136.763006] wlan0: AP denied authentication (auth_alg=0 code=1)
[  136.939221] wlan0: authenticate with AP 00:1e:e5:61:36:13
[  136.943837] wlan0: RX authentication from 00:1e:e5:61:36:13 (alg=0 transaction=2 status=1)
[  136.943850] wlan0: AP denied authentication (auth_alg=0 code=1)
[  137.123417] wlan0: authenticate with AP 00:1e:e5:61:36:13
[  137.125028] wlan0: RX authentication from 00:1e:e5:61:36:13 (alg=0 transaction=2 status=1)
[  137.125039] wlan0: AP denied authentication (auth_alg=0 code=1)
[  137.226287] wlan0: authentication with AP 00:1e:e5:61:36:13 timed out
[  163.554889] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=193 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=173 
[  164.284369] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170 
[  165.271831] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=174 
[  175.933954] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=261 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=241 
[  182.451258] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=193 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=173 
[  183.004523] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170 
[  183.632296] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=174 
[  203.362162] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=193 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=173 
[  204.115692] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170 
[  205.114170] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=174 
[  232.948287] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=193 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=173 
[  233.946642] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170 
[  234.944208] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=174 
[  264.221380] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=193 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=173 
[  265.219901] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170 
[  266.218612] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=174 
[  269.509589] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[  271.229499] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=261 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=241 
[  295.180889] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=193 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=173 
[  296.179659] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170 
[  297.178074] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=174 
[  326.140797] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=193 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=173 
[  327.139318] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170 
[  328.137735] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=174 
[  357.100288] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=193 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=173 
[  358.098765] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170 
[  359.097688] Unknown OutputIN= OUT=wlan0 SRC=169.254.3.94 DST=169.254.255.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=174 
dvlong@longslap2:~$ sudo lshw -C network
sudo: unable to resolve host longslap2
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:39:76:27
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:03:47:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.2.100 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

---

### Post by ProphetOfFrivolity on 2008-09-14
Gentlemen,

I was facing the same exact problem with my Intel wireless Card. This message is meant to thank Chilli for his wonderful advices and patience in guiding through a solution.

Thanks.

---

### Post by chubby127 on 2008-10-06
Chili555 I have been looking for a solution to fix my wireless and after putting what you said into the terminal, it FINALLY worked! you are a GENIUS! haha thanks

---

### Post by chili555 on 2008-10-06
Thanks so much for your kind comments. Glad it's working.

---

### Post by schou on 2008-10-09
Sorry to barge in like this, but I am having similar difficulties with a Packard Bell BU45 laptop using the iwl3945 driver..
When installing Ubuntu (8.10 beta) the wireless network works like a charm (although the led isn't on). After rebooting however, the wireless stops working.. :(
The wifi-switch on the laptop does not seem to work, and I have tried to reload the iwl3945-driver with the 'disable_hw_scan=1' parameter - without any luck unfortunately..
It appears that all my network connections have been shut down somehow - I cannot even connect via cable.. :confused:

Does anyone have a clue? 

Kind regards,
Jakob

---

### Post by schou on 2008-10-11
> **schou said:**
> Sorry to barge in like this, but I am having similar difficulties with a Packard Bell BU45 laptop using the iwl3945 driver..

Fixed it by installing Ubuntu 8.04 instead.. 

//Jakob

---

### Post by thorheimdall on 2008-10-13
I have installed the linux-backports-modules-hardy-generic, but I still can't connect to my wireless network. It seems to fail with the DHCP request:

From /var/log/daemon.log:
 
```
Oct 13 16:16:56 MYCOMPUTER NetworkManager: <info>  Device wlan0 activation scheduled...
Oct 13 16:16:56 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) started...
Oct 13 16:16:56 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 13 16:16:56 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 13 16:16:56 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 13 16:16:56 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 13 16:16:56 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 13 16:16:56 MYCOMPUTER NetworkManager: <info>  Activation (wlan0/wireless): access point 'MYWIRELESSNETWORK' is encrypted, but NO valid key exists.  New key needed.
Oct 13 16:16:56 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'MYWIRELESSNETWORK'.
Oct 13 16:16:56 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 13 16:17:12 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'MYWIRELESSNETWORK' received.
Oct 13 16:17:12 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 13 16:17:12 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 13 16:17:12 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 13 16:17:12 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 13 16:17:12 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 13 16:17:12 MYCOMPUTER NetworkManager: <info>  Activation (wlan0/wireless): access point 'MYWIRELESSNETWORK' is encrypted, and a key exists.  No new key needed.
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: response was 'OK'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: sending command 'AP_SCAN 1'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: response was 'OK'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: sending command 'ADD_NETWORK'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: response was '0'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6e65757472696e6f'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: response was 'OK'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA2'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: response was 'OK'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: response was 'OK'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: response was 'OK'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  SUP: response was 'OK'
Oct 13 16:17:13 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 13 16:17:21 MYCOMPUTER NetworkManager: <info>  Supplicant state changed: 1
Oct 13 16:17:21 MYCOMPUTER NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'MYWIRELESSNETWORK'.
Oct 13 16:17:21 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 13 16:17:21 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Oct 13 16:17:23 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction.
Oct 13 16:17:23 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct 13 16:17:23 MYCOMPUTER NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0
Oct 13 16:17:23 MYCOMPUTER NetworkManager: <info>  Old device 'wlan0' activating, won't change.
Oct 13 16:17:23 MYCOMPUTER dhclient: wmaster0: unknown hardware address type 801
Oct 13 16:17:24 MYCOMPUTER NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0
Oct 13 16:17:24 MYCOMPUTER dhclient: wmaster0: unknown hardware address type 801
Oct 13 16:17:28 MYCOMPUTER dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 13 16:17:33 MYCOMPUTER dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 13 16:17:41 MYCOMPUTER dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 13 16:17:53 MYCOMPUTER dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 13 16:17:59 MYCOMPUTER dhclient: No DHCPOFFERS received.
Oct 13 16:17:59 MYCOMPUTER avahi-autoipd(wlan0)[10471]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 13 16:17:59 MYCOMPUTER avahi-autoipd(wlan0)[10471]: Successfully called chroot().
Oct 13 16:17:59 MYCOMPUTER avahi-autoipd(wlan0)[10471]: Successfully dropped root privileges.
Oct 13 16:17:59 MYCOMPUTER avahi-autoipd(wlan0)[10471]: Starting with address 169.254.3.91
Oct 13 16:18:05 MYCOMPUTER avahi-autoipd(wlan0)[10471]: Callout BIND, address 169.254.3.91 on interface wlan0
Oct 13 16:18:09 MYCOMPUTER avahi-autoipd(wlan0)[10471]: Successfully claimed IP address 169.254.3.91
Oct 13 16:18:09 MYCOMPUTER NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface wlan0
Oct 13 16:18:09 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled...
Oct 13 16:18:09 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started...
Oct 13 16:18:09 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) failure scheduled...
Oct 13 16:18:09 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete.
Oct 13 16:18:09 MYCOMPUTER NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0
Oct 13 16:18:09 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) failed for access point (MYWIRELESSNETWORK)
Oct 13 16:18:09 MYCOMPUTER NetworkManager: <info>  Activation (wlan0) failed.
Oct 13 16:18:09 MYCOMPUTER NetworkManager: <info>  Deactivating device wlan0.

```


I have an Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02), and I am running Kubuntu 8.04.1

I am using other laptops (not with iwl3945 card) with Kubuntu 8.04.1 and I have no problem to connect to this wireless network.  So it must be an iwl3945 issue...

Someone has an idea?

---

### Post by thorheimdall on 2008-10-13
Forget it... that was my fault...  now it is working :-\"

---

### Post by Cauda_Draconis on 2008-10-18
My network manager has stopped working after I upgraded to Hardy. I have a Toshiba Satellite A100.
I've read through a bunch of possible solutions to this, and have tried everything to no meaningful degree of success. I can't get on to ANY wireless network, hidden or not. It won't even detect wireless networks.

I have a bunch of outputs from various commands, if they help.
From lspci -vvnn
```
user@computer:~$lspci -vvnn
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation PRO/Wireless 3945BG Network Connection [8086:1044]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 220
	Region 0: Memory at da000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
```
From iwlist scanning
```
user@computer:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      Failed to read scan data : Resource temporarily unavailable
```
From dmesg | grep iwl
```
user@computer:~$ dmesg | grep iwl
[   51.188079] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   51.188083] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   51.188270] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
[   53.931196] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels
[   53.936016] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   54.550376] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[   54.550387] iwl3945: Error Reply type 0x00000005 cmd REPLY_SCAN_CMD (0x80) seq 0x4418 ser 0x0000004B
[   55.542794] iwl3945: Can't stop Rx DMA.
```
From sudo lshw -C network
```
user@computer:~$ sudo lshw -C network
[sudo] password for user: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:44:77:29
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:41:65:47
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
```
From ethtool eth1 (eth1 being my wireless card)
```
user@computer:~$ ethtool eth1
Settings for eth1:
No data available
```

Thank you ^.^

Edit: I've also tried installing linux-backports-modules-hardy-generic, and I've tried installing wicd as well. Neither of them worked.

---

### Post by Manta xxv on 2008-11-20
Hi, I'm new to ubuntu and have just installed 8.04 and can't get my wireless working I have an hp dv2708ca laptop with a iwl3945 wireless card that doesn't seem to come up anywhere. I've tried entering some of the code and whatnot put up by Chili but have no idea what the input and outputs mean. all i know is that nothing is coming up in the wireless networks. Please help and give simple instructions.... sorry. But thanks a lot! 

I hate vista and really don't want to go back.

---

### Post by joeclueless on 2008-11-20
> **chili555 said:**
> Let's start from the easiest fix. There is evidently a better iwl3945 driver in here:```
sudo apt-get install linux-backports-modules-hardy-generic 
```If you have not done that, please do and let us know if you can now connect.

I finally fixed my Toshiba Satellite M105's (in)ability to connect via wifi by using chili555's "easiest fix." Thanks for you help, chili555!

---

### Post by jgaudario on 2008-11-23
> **joeclueless said:**
> I finally fixed my Toshiba Satellite M105's (in)ability to connect via wifi by using chili555's "easiest fix." Thanks for you help, chili555!

hi guys,
i'm enjoying the posts, very informative. i also have a similar problem. i tried posting this on other threads but no luck. i'm a nub. some of this stuff i can follow but some i'm totally lost.
can't connet, i have hardy,8.04 on a neo laptop t5500, 1.66 ghz, with pro/intel 3945abg wireless. 
i've tried the easy fix and this is what i got:
joel@Neo:~$ [COLOR="Purple"]sudo apt-get install linux-backports-modules-hardy-generic[/COLOR]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-backports-modules-2.6.24-18-generic linux-image-2.6.24-18-generic
Suggested packages:
  linux-doc-2.6.24 linux-source-2.6.24
The following NEW packages will be installed:
  linux-backports-modules-2.6.24-18-generic linux-backports-modules-hardy-generic linux-image-2.6.24-18-generic
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 18.8MB of archives.
After this operation, 63.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  linux-image-2.6.24-18-generic linux-backports-modules-2.6.24-18-generic linux-backports-modules-hardy-generic
Install these packages without verification [y/N]? y
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-image-2.6.24-18-generic 2.6.24-18.32
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-backports-modules-2.6.24-18-generic 2.6.24-18.16
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-backports-modules-hardy-generic 2.6.24.18.20
  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-18-generic_2.6.24-18.32_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-18-generic_2.6.24-18.32_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.24/linux-backports-modules-2.6.24-18-generic_2.6.24-18.16_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.24/linux-backports-modules-2.6.24-18-generic_2.6.24-18.16_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-hardy-generic_2.6.24.18.20_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-hardy-generic_2.6.24.18.20_i386.deb)  Could not resolve 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
joel@Neo:~$ 
any ideas?
Am in trouble or what?

---

### Post by jgaudario on 2008-11-23
i should gave you guys this first before the easy fix. these are all the results:
joel@Neo:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:07.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:07.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:07.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:07.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
joel@Neo:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 15ca:00c3  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
joel@Neo:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:0b:5c:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:90:f5:67:35:a4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
joel@Neo:~$ 

I got more coming.

---

### Post by jgaudario on 2008-11-23
joel@Neo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"magnet"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

joel@Neo:~$ iwconfig --version
iwconfig  Wireless-Tools version 29
          Compatible with Wireless Extension v11 to v22.

Kernel    Currently compiled with Wireless Extension v22.

wlan0     Recommend Wireless Extension v21 or later,
          Currently compiled with Wireless Extension v22.

joel@Neo:~$ 

[   36.163632] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   36.163638] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   36.163801] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   36.163820] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   36.163843] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   36.421433] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   36.459099] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   37.521881] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   37.521917] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   38.742245] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   38.756165] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   38.806277] cs: IO port probe 0x100-0x3af: clean.
[   38.808526] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   38.809462] cs: IO port probe 0x820-0x8ff: clean.
[   38.810242] cs: IO port probe 0xc00-0xcf7: clean.
[   38.811292] cs: IO port probe 0xa00-0xaff: clean.
[   39.190762] lp: driver loaded but no devices found
[   39.367470] Adding 1975952k swap on /dev/sda6.  Priority:-1 extents:1 across:1975952k
[   40.234658] EXT3 FS on sda5, internal journal
[   40.399501] NET: Registered protocol family 17
[   41.892519] ip_tables: (C) 2000-2006 Netfilter Core Team
[   42.430414] No dock devices found.
[   43.651951] apm: BIOS not found.
[   45.080234] r8169: eth0: link down
[   45.184363] Bluetooth: Core ver 2.11
[   45.184716] NET: Registered protocol family 31
[   45.184721] Bluetooth: HCI device and connection manager initialized
[   45.184727] Bluetooth: HCI socket layer initialized
[   45.214437] Bluetooth: L2CAP ver 2.9
[   45.214443] Bluetooth: L2CAP socket layer initialized
[   45.311286] Bluetooth: RFCOMM socket layer initialized
[   45.311298] Bluetooth: RFCOMM TTY layer initialized
[   45.311300] Bluetooth: RFCOMM ver 1.8
[   47.799927] ppdev: user-space parallel port driver
[   47.983092] audit(1227337708.047:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5484 profile="/usr/sbin/cupsd" namespace="default"
[   48.626437] [drm] Initialized drm 1.1.0 20060810
[   48.630251] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   48.630266] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   48.630352] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   65.893447] NET: Registered protocol family 10
[   65.893846] lo: Disabled Privacy Extensions
[   65.894520] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   65.895270] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   76.142012] CPU0 attaching NULL sched-domain.
[   76.142019] CPU1 attaching NULL sched-domain.
[   76.156135] CPU0 attaching sched-domain:
[   76.156141]  domain 0: span 03
[   76.156145]   groups: 01 02
[   76.156149] CPU1 attaching sched-domain:
[   76.156150]  domain 0: span 03
[   76.156152]   groups: 02 01
[ 7160.892888] r8169: eth0: link down
[ 7160.895025] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7160.914356] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7162.922958] r8169: eth0: link down
[ 7162.926463] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7163.002041] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7956.250640] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[ 7956.354414] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[ 7956.354422] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[ 7956.354548] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[ 7956.354573] PCI: Setting latency timer of device 0000:02:00.0 to 64
[ 7956.354598] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[ 7956.445444] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[ 7956.447187] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[ 7956.472339] ADDRCONF(NETDEV_UP): wlan0: link is not ready
joel@Neo:~$ 
:confused: so there you have it. i can't say i tried everything, but seems like i'm getting nowhere. it seems like you guys are having success and i like to join in.
i can connect to the wireless in the mall. i have no prblems with winxp with the wireless.
i am not the internet regularly, so if i don't reply soon i'm not ignoring anyone, that's why the long post. right now i'm in the internet cafe.
thank you, looking forward you response, any of you guys,,,,help.

---

### Post by ussndmac on 2008-11-25
Is there a detailed instruction for the intel 3945?

I mean if you if this and iw that and this is what you get, do this sort of thing?

As I've posted elsewhere, I've been round and round with this interface and have gotten nowhere.

And the #ubuntu irc channel has offered nothing.

Regards,
Mac

---

### Post by karlatsaic on 2008-11-25
> **jgaudario said:**
> joel@Neo:~$ iwconfig
:confused: so there you have it. i can't say i tried everything, but seems like i'm getting nowhere. it seems like you guys are having success and i like to join in.

It sounds like you might be similar to me. I could connect anywhere public, but not at home. I did not want to go the ndiswrapper route, which is really windows, so I just tried upgrading my wireless router at home to a linksys wrt160N. That's all it took. I had a first generation, old wireless router which evidently just could not quite do a 802.11b handshake with my iwl3945 driver (in a dell xps m1330). I know buying other new hardware is not a good solution, but in my case my upgrade was long overdue. It now connects as 802.11g.

---

### Post by jgaudario on 2008-11-26
[COLOR="purple"][/COLOR]> **karlatsaic said:**
> It sounds like you might be similar to me. I could connect anywhere public, but not at home. I did not want to go the ndiswrapper route, which is really windows, so I just tried upgrading my wireless router at home to a linksys wrt160N. That's all it took. I had a first generation, old wireless router which evidently just could not quite do a 802.11b handshake with my iwl3945 driver (in a dell xps m1330). I know buying other new hardware is not a good solution, but in my case my upgrade was long overdue. It now connects as 802.11g.

that's good you've got it solved. that's what i have a 802.11g. i don't have any connection at home, not even wireless that's why i go to a mall or such like. 
hardy says i don't have wlan0, eth0, wmaster0, but when i do command lshw -c, it lists the interface: wmaster0 and eth0
joel@Neo:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       [COLOR="Purple"]logical name: wmaster0[/COLOR]       version: 02
       serial: 00:13:02:0b:5c:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 [COLOR="purple"]module=iwl3945 multicast=yes wireless=IEEE 802.11g[/COLOR]
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       [COLOR="DarkOrchid"]logical name: eth0[/COLOR]       version: 01
       serial: 00:90:f5:67:35:a4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
joel@Neo:~$ 
so i do have these, but i can't connect. one thing i haven't tried is connecting with the CD.
but let me ask?
if i can get the wireless going with the CD, what does that mean?
if i can not, then what does that mean?
anyone? help? i'll try to get back check any response by tomorrow.thanks.

---

### Post by karlatsaic on 2008-11-26
> **jgaudario said:**
> 
so i do have these, but i can't connect. one thing i haven't tried is connecting with the CD.
but let me ask?
if i can get the wireless going with the CD, what does that mean?
if i can not, then what does that mean?

Your lshw output looks like mine, so that's good. Did you do a fresh install of 8.04 or did you upgrade? If you did an upgrade, then sometimes there are lingering settings which may be lying around. I would definitely try the live CD, so that you would be looking at how Network Manager would, by examining your hardware, try to optimize your network configuration from scratch. If that works, and you have a nice backup of all your user files, a fresh install might be the ticket. If not, others more knowledgeable with network details will have to help you. [EDIT] Also - I had no need to install the [COLOR=Purple]linux-backports-modules-hardy-generic package[/COLOR]

---

### Post by jgaudario on 2008-11-28
It was a fresh install of 8.0. that's what i don't understand, will definitely try the CD. thanks for the prompt response, i really appreciate any input. sometimes im at the point of uninstalling and reinstalling this thing.
i'll let you know what happens with the cd.

---

### Post by jgaudario on 2008-11-28
> **karlatsaic said:**
> Your lshw output looks like mine, so that's good. Did you do a fresh install of 8.04 or did you upgrade? If you did an upgrade, then sometimes there are lingering settings which may be lying around. I would definitely try the live CD, so that you would be looking at how Network Manager would, by examining your hardware, try to optimize your network configuration from scratch. If that works, and you have a nice backup of all your user files, a fresh install might be the ticket. If not, others more knowledgeable with network details will have to help you. [EDIT] Also - I had no need to install the [COLOR=Purple]linux-backports-modules-hardy-generic package[/COLOR]

it was a fresh install. i tried the cd and the network manager just kept swimming around in circles, then it gave me 4 bars(that's an improvement, i never seen that before) so i tried to connect via mozilla, still no connection. tried to manually configure, but no luck there. it's picking up the network in the coffee shop but it's not connecting, i mean it's listing the networks but i can't connect.
i clicked on the "information" it says i have 802.11 wifi(wlan0)
i don't know what to make of this.
guys, anybody, i need some help.

---

### Post by jgaudario on 2008-12-15
well, what do you know? my iwl3945 is not supported. i don't have ndiswrapper for windows, nor linux ndiswrapper. that's why my wireless wont work. i followed the trouble shooting guide on hardy, it was leading me to my problems. so i got rid of ubuntu on my computer, may be i'll try again sometimes.

---

### Post by 80hd on 2012-09-10
+1 for this thread on my iwl3945 based work laptop.  
My phone and tablet were getting 22/30 whereas my computer onyl saw .5/5  
HUGE difference. Is there any reason this setting simply isn't the default? Power savings, network chatter, hurricanes in Australia etc?

---

### Post by lisati on 2012-09-11
A lot can change in the time that this thread has been inactive.

Thread closed.

---

