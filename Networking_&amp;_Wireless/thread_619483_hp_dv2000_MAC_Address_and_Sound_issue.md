---
title: "hp dv2000 MAC Address and Sound issue"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by croniksoft on 2007-11-21
Hello everyone,

first of all just want to let everyone know that I try to google this issues for the past 3 days and I have no were else to go...:(


I just got an brand new HP dv2000 with vista,with an AMD64 x2 ,1 gig of ram and Nvidia Video card.
I will explain to you guys everything I did so you can better understand the issue.

1)ubuntu live cd was not booting up correctly,mange to fix that by booting in to safe graphic mode and installing the restricted Nvidia Driver that came with ubuntu.
2)Wireless was not working,manage to set it up with a tutorial that I found online ( don't have the link but will find it if you guys need it) setting up Ndiswrapper and some device driver that I downloaded from the hp site
3)My head phone was not working,when I plug them in the headphone plug the external speaker will still play ,manage to fix the problem by compiling the latest alsa driver my self and adding “laptop mode” to one of the config files,but from what I had research there is a bug that when you dual boot with windows and try to use Linux it wont work unless you first boot up without the AC adapter..strange but true I ran in this issue my self

After all that everything was working ok but then my laptop started to hang at boot up and when I press F4 I see and Error pops up saying “Invalid mac address, contact vendor” something like that ,and trys to assign one and that when the real issue starts

when I run by running ifconfig I can see that my eth increments by one every time I boot up

ex:eth0, eth2 ,eth16 and now I am up to eth38.
 
I can use the Internet and everything work ok when I manage to boot up,but another thing I notice is that in the network management utility I see the my wireless and Ethernet cable are set into roaming mode but in reality I know is not that way because I am using the interface to get online 

So I think the issue is that every time I boot up there is a new MAC address  and causes my computer to hang.

Can anyone please help
and sorry for my poor writing ,English is my 2nd  lenguage


I am using ubuntu 7.10



Tks
:popcorn:

---

### Post by croniksoft on 2007-11-22
k guys,after 3 days of no sleep I mange to fix some of my problem on my HP dv2000

I will post them here in case anyone has the same issues.


First is first,
**Live Cd is not booting up?**
To install it you have to install it in text mode or in safe Graphic mode.

.**I have a bad resolution,how can I fix this?**
install the Nvidia restricted driver for your video card.

**Wireless is not working?**
Download this driver 
```
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
```
and If that dont work download this one
 ```
sudo wget ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
```

make a directory and put the drivers there.
> mkdir ~/wireless

put the bcm43xx in the black list file.
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

Get cabextract so we can be able to unzip the driver file from the .exe file
```
sudo apt-get install cabextract
cd ~/wireless
cabextract “name of the driver you just downloaded”
```

now install Ndiswrapper
```
sudo apt-get install ndiswrapper-utils-1.9
go to the dirctory were your driver is
cd ~/wireless
```





Run this commans and reboot your system

```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```
reboot your system

**Sound is working but headphone do not mute external speaker?**
open
```
sudo gedit /etc/modprobe.d/alsa-base
```

add the following line to the end of the file
```
options snd-hda-intel model=laptop
```

reboot


**Mac address keep on changing and the “eth” keeps on incrementing by one (ex: eth1, eth2, eth20)**
I really dont know why this happens but I mange to fix that by deleting 2 files,Please be advise that I am not resposible how this might work for you.
 please make a back up before  you deleted them

```
cd /etc/udev/rules.d/
mkdir ~/backup
cp 70-persistent-net.rules ~/backup
cp 75-persistent-net-generator.rules ~/backup
sudo rm -rf 70-persistent-net.rules
sudo rm  -rf 75-persistent-net-generator.rules 

```
Reboot and that should fix the problem




those are just some of the problem I mange to solve,just have one more to go.
**_My system  hangs every now and then_**

Notice:
This works only ubuntu 7.10 32 bits and 64 bits,Dont know about the rest but feel free to tell us if it works on anyother.

---

### Post by gaudete on 2007-12-14
Hi Croniksoft,

I followed all your instructions and my wireless still does not work!
I downloaded this driver  [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)
and this is my Broadcom chip: 01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 02)

I know I'm doing something wrong as I am completely clueless and your help would be greatly
appreciated. 

Thanks.

Gaudete

---

### Post by croniksoft on 2007-12-21
Sorry for the late response,but anyways lets get to work.
did you try the other driver,if you notice i put 2 drivers there!
before you install the other driver make sure you uninstall   any wireless drivers you have previously installed.

if that don't work try to uninstall ndiswrapper and install it from source.


let me know if you need any help doing this :)

---

### Post by moe120 on 2008-01-17
Hi,

the last week while i desperately tried to install ubuntu 7.10, i ran in the same problem with a new mac adress at every boot and increasing eth interfaces.

i read lots of stuff about this and could find pieces fitting my problem on different sites, but no complete solution, so i decided to post one here.

**The Problem:**
when the Kernel starts there is a message like:
"Invalid Mac address detected: af:52:de:7d:1d:00  switching to a random mac"
the mac address is indeed invalid, but only because it was read out in reverse, the correct mac address in this case is 00:1d:7d:de:52:af

then a random mac address like 00:6c:..... is assigned and a new eth interface is created in [COLOR="DarkOliveGreen"]/etc/udev/rules.d/70-persistent-net.rules[/COLOR]
in this file a new devicename is given to each mac-address >> resulting in an ever bigger useless file with random mac adresses

**The Solution:**
first you need to change the file [COLOR="DarkOliveGreen"]/etc/udev/rules.d/70-persistent-net.rules[/COLOR], deleting all unneeded lines so it looks like:
```
# PCI device 0x10de:0x0450 (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*",ATTRS{address}=="af:52:de:7d:1d:00", NAME="eth0"
```
as you can see above, the device eth0 is identified by the (reversed) mac address, but this only works, if it keeps it mac-address, what is not the case (the mac-address is assigned randomly every boot). So we need to identify the network adapter by its BUS address.
To find out the needed adress, just execute[COLOR="DarkOliveGreen"] lspci[/COLOR], this should bring up sth. like this:
```
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
```
the number we need is 0000:**00:06.0** (may vary on your system).

then we change the [COLOR="DarkOliveGreen"]/etc/udev/rules.d/70-persistent-net.rules[/COLOR] a last time, to make the NIC be identified by its position in the bus (that doesnt change):
```
# PCI device 0x10de:0x0450 (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ID=="0000:00:06.0", NAME="eth0"
```

this stops the increasing number of eth interfaces, but to re-assign the original mac-address and thus prevent further network problems, we need to change another file: [COLOR="DarkOliveGreen"]/etc/network/interfaces[/COLOR]:
in my case it looks like

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
pre-up ifconfig eth0 hw ether 00:1d:7d:de:52:af
```

(enter the correct mac-address of your adapter instead of 00:1d:7d:de:52:af)
this assigns the wanted mac adress everytime the system is rebooted and stops random mac-addresses.

this worked fine in my case (Ubuntu 7.10, Gigabyte Motherboard with nForce550 and MCP65).
If anyone knows how to get rid of this kernel message at the beginning, or how to correct the reverse readout of the mac-adress, please let me know.

Moe

---

### Post by pt123 on 2008-02-29
Thanks your solution worked on my Gigabye GA-M68SM-S2L motherboard which also uses a similar nvidia ethernet chip.

Good news is that Hardy Alpha 4 had no problems with the ethernet card.

---

### Post by LexRoss on 2008-03-05
I have recently discovered the same problem with my Asus F5N laptop. I never noticed it before, actually. The message "please complain to hardware vendor" rang the bell when suspending the laptop. So new MAC address generated not only on new reboot, but on every suspend, too!

Applied your solution, and it worked as it should. Yet I am to use VPN connection to my ISP to go to the Internet. Naturally, Network Manager comes in handy. And guess what? Network manager can't stand physical interface configuration lines in /etc/network/interfaces! Doesn't matter if it's eth0, eth1 or whatever, the network information icon is disabled in Network Manager, and VPN connection setup dialog now shows "Require working network connection" check box, which is also disabled. All despite the fact that there is a working connection (as per /etc/network/interfaces file).

The combination of bugs in forcedeth (I wonder is they spell it right, forced-eth instead of forcedeath , is it?:)) and Network Manager applet is a prescription for disaster. I ended up wiping out physical interface configuration from /etc/network/interfaces file, so I am back to randomly generated MAC addresses, which is bad bad bad.

The summary.

1. Applying your fix worked but did not stop kernel messages complaining about bad MAC address. The reported bad MAC address is different from the real one assigned to the device in /etc/udev/rules.d/70-persistent-net.rules file and appears to be randomly generated. The only difference is that device ID from that file is now included with the kernel error message.

The output of lspci command reveals the following:
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)

2. Entries for physical interfaces in /etc/network/interfaces render Network Manager applet to become unusable. Entries for logical interfaces are okay.

3. Interesting enough, if I add an entry for my home LAN in /etc/network/interfaces like this

auto eth0:1
iface eth0:1 inet static
address 192.168.1.10
netmask 255.255.255.0
up flush-mail

the eth0:1 interface is not brought up automatically during system startup. I have to bring it up manually with 'sudo ifup eth0:1' command.

Any ideas how to fix that? I'd like to try interface mapping method described in interfaces(5) man page but I have no idea how to write a mapping script as per sample code on that page.

So any comments, ideas and suggestions are welcome.

---

### Post by mrming on 2008-07-20
Hi,

I'd just like to add that this problem still exists for me in Hardy Heron, and that this solution still fixes the problem.


Thanks very much - I may well have gone insane without this thread... :)

---

