---
title: "HP pavilion ze4900 wireless"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by macuser9214 on 2007-07-01
I got ubuntu installed on my HP ZE4900 laptop, but cant get the wireless to work.

I used NDISWRAPPER, and when I type iwconfig, the wireless shows up as eth1.

The light for the wireless card, on the front of the laptop is NOT lit.

sudo pccardctl ident (whatever that means) returns:
Socket 0:
 No product info available.

I cant think of anything else.

Please help. I am new to linux, and love open source, and I really want to use it.

I always brag about how good linux is, but I can't get this to work, so hopefully you guys can help.

Thanks a lot.

---

### Post by kevdog on 2007-07-01
I assume your wireless is built-in.  Lets just find a few things out about your card right now.  At command line please type following commands and post output:

lspci
lshw -C network

Did you install ndiswrapper?? Can you tell me if you used synaptic to install this??
Please post output of following:
ndiswrapper -v

Thanks

---

### Post by macuser9214 on 2007-07-01
ricky@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)




---


ricky@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:ea:27:ad
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:3000-30ff iomemory:e0202000-e02020ff irq:10
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@02:06.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:9c:9b:e4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:e0200000-e0201fff irq:11



---


ricky@ubuntu:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 586 



--

I couldn't even got on wired now. I had to transfer those with a flash drive (made it into a text file - I'm too new to linux, lol)

---

### Post by macuser9214 on 2007-07-01
I see in your profile your responding to my thread, but I'm gonna call it a night. It's 2:15 where I'm at, and I'm tired as heck.

I'll respond tomorrow, and thanks a lot for your help.

---

### Post by kevdog on 2007-07-01
Let me show you a few things:

Your wireless card is the following:
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

The driver currently associated with your card is bcm43xx:
configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 multicast=yes wireless=IEEE 802.11b/g

So since you want to use ndiswrapper, you dont want the bcm43xx driver associated with your card, you want ndiswrapper!!

First lets black the bcm43xx driver:
gksu gedit /etc/modprobe.d/blacklist

Add the following to the end of the file:

#Blacklist bcm43xx driver
blacklist bcm43xx

Save the file.

Onto ndiswrapper
Your version has an error and is not installed properly:
utils Error: no version specified!

So first uninstall ndiswrapper.  You probably used Synaptic, so use Synaptic to uninstall ndiswrapper

Next we are going to reinstall ndiswrapper -- but from source

Lets do some setup work first
1. Stick ubuntu cd-rom into driver and wait to become ready
2. At command line type: sudo apt-cdrom add
3. Then: sudo aptitude update
4. Then: sudo aptitude install build-essential

At command line, do the following:
cd ~
mkdir ndiswrapper

Download the ndiswrapper source files and place in the ~/ndiswrapper directory:
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

cd ~/ndiswrapper
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install

Ok great, now lets check ndiswrapper installation to see if it correct:
ndiswrapper -v

You should see no errors!

Ill stop right now to let you catch up!

---

### Post by macuser9214 on 2007-07-01
I'll let you know how I make out tomorrow, I'm going to bed. Thanks so much, and like I said, I'll respond tomorrow.

But thanks a lot for taking the time to help me. For free, nonetheless.

Have a good night.

EDIT: I used Wubi, so I dont have the Ubuntu CD. I will burn one, or find the one that I have laying around somewhere.

---

### Post by macuser9214 on 2007-07-01
when I ran "apt-get cdrom add", it said it couldn't mount the cd.

I tried to go to the next part, and got a crapload of warnings and errors.

---

### Post by macuser9214 on 2007-07-01
ok, I finally got the ETHERNET working again, so I just used apt-get to install the build-essential thing, and ndiswrapper installed. Now, for ndiswrapper -v, I get this:

ricky@ubuntu:~/Desktop/ndiswrapper-1.47$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 586 


So it appears to be working.

---

### Post by kevdog on 2007-07-01
Ok, the ndiswrapper is now installed as an executable appropriately.  Do you have the XP drivers or just the drivers for your wireless card??  It should be quick work from here on in.

Assumptions: drivers are in:
~/drivers <---Just an example directory

Ok installation steps based on above
cd ~/drivers
sudo ndiswrapper -i  ****.inf  <---Make sure you have both the .sys and .inf file in this directory

Insert module into kernel
sudo depmod -a 
sudo modprobe -i ndiswrapper  

Check to see you dont have any errors
dmesg
Go through this long output and you should see something telling you ndiswrapper was inserted appropriately

Make module load at boot time
sudo ndiswrapper -m

reboot
Proabably will not work so when posting back please list the contents of these files
/etc/network/interfaces
/etc/iftab

Give me the output of 
lshw -C network

Thanks

---

### Post by macuser9214 on 2007-07-01
when i run sudo ndiswrapper -m, it says

Module configuration already contains alias directive.

should I reboot, or will I lose the changes?

---

### Post by macuser9214 on 2007-07-01
Also, I'm not sure of the driver, I think it's right but I'm not sure. Do you know the exact driver I need? or in windows, where are the files? I'll jst copy those, and use them.

---

### Post by kevdog on 2007-07-01
Usually your windows drivers came on a disk, cd, or were located in a file somewhere.  If you cant find them let me know!

---

### Post by macuser9214 on 2007-07-01
I followed this guys step # 5, and got it working.

For a while, the light was on but it wouldn't connect, then it finally worked!

But It still wont let me do the -m thing, (read my post a few up) so I''m afraid to reboot.

---

### Post by kevdog on 2007-07-01
Dont worry about the -m thing.  From reading your post its most likely already installed.  This command basically makes a file named ndiswrapper in the /etc/modprobe.d directory.  Within the file is  simply the statement:

```

alias wlan0 ndiswrapper

```

Thats all that command does.

Does everything work??? It seems by your post it does.  It might take a minute or two for the wireless to comeup after startup.

Reboot and try again.  Nothing is going to break
What does your ifconfig say now??

---

### Post by macuser9214 on 2007-07-01
I had to run modprobe again, befor the light came on, then go into the gui, and tell it to use roaming mode again, so I can pick a network in the menubar.

After i did that, it worked fine.Any way to automate the process at startup?

  Here's ifconfig:

> 
ricky@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:EA:27:AD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 

eth1      Link encap:Ethernet  HWaddr 00:90:4B:9C:9B:E4  
          inet addr:10.0.2.2  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe9c:9be4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:735804 (718.5 KiB)  TX bytes:183978 (179.6 KiB)
          Interrupt:11 Memory:e0200000-e0202000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 b)  TX bytes:500 (500.0 b)



---

### Post by kevdog on 2007-07-01
The answer is yes!!!

Please be specific about the commands you type.  "I had to type that modprobe thing again" doesnt help me.  I need to know exactly what you typed.

Your wireless MAC address for your card is:
00:90:4b:9c:9b:e4

Can you post the contents of your 
/etc/iftab file??

Thanks

---

### Post by macuser9214 on 2007-07-01
Sorry, I typed: 
sudo modprobe -a ndiswrapper


Contents of the file you requested:

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:36:ea:27:ad arp 1
eth1 mac 00:90:4b:9c:9b:e4 a

---

### Post by kevdog on 2007-07-01
In the iftab file change eth1 to wlan0.  

Reboot, I think after the change you wont have to use the modprobe statement anymore

---

### Post by macuser9214 on 2007-07-01
I still had to run that command.

But iwconfig now shows wlan0 instead of eth1.

How do you make it run the command at startup?

---

### Post by Ayuthia on 2007-07-01
I don't think that ndiswrapper has been added to /etc/modules.  Just add that to the end of the file and ndiswrapper should start up next time.

---

### Post by kevdog on 2007-07-01
Did you ever run the command:

sudo ndiswrapper -m

Just wondering, its another method of doing what Ayuthia suggested.

---

