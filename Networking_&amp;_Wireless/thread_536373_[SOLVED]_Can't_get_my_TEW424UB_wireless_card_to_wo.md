---
title: "[SOLVED] Can't get my TEW424UB wireless card to work"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by mahasmb on 2007-08-27
Hi, I've tried looking through all the threads I could find in these forums and following their instructions, but I still can't get it to work.

I'm currently on my laptop and trying to set up my wireless on my desktop, which has no internet. But I do have a 2 GB flashdrive that I'm using to transfer files from my desktop to my laptop.

I have a TEW-424UB Wireless card.

```


maha@maha-dlu:~/Desktop/bla/Drivers/Windows2000$ [COLOR="Green"]lsusb[/COLOR]
Bus 005 Device 007: ID 0457:0163 Silicon Integrated Systems Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
maha@maha-dlu:~/Desktop/bla/Drivers/Windows2000$[COLOR="Green"] lshw -C network[/COLOR]
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: 8
       bus info: pci@00:08.0
       logical name: eth1
       version: 24
       serial: 00:10:4b:6d:16:c7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=32 maxlatency=10 mingnt=10 multicast=yes
       resources: ioport:c000-c07f iomemory:df000000-df00007f irq:17
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 78
       serial: 00:11:5b:1b:ce:b5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.2 latency=32 maxlatency=8 mingnt=3 multicast=yes
       resources: ioport:e000-e0ff iomemory:df002000-df0020ff irq:18
maha@maha-dlu:~/Desktop/bla/Drivers/Windows2000$ [COLOR="Green"]ndiswrapper -v[/COLOR]
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 586 
maha@maha-dlu:~/Desktop/bla/Drivers/Windows2000$ [COLOR="Green"]cat /etc/modprobe.d/blacklist[/COLOR]
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
maha@maha-dlu:~/Desktop/bla/Drivers/Windows2000$ [COLOR="Green"]iwconfig[/COLOR]
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

maha@maha-dlu:~/Desktop/bla/Drivers/Windows2000$ [INDENT]iwlist scan[/INDENT]
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

maha@maha-dlu:~/Desktop/bla/Drivers/Windows2000$ [COLOR="Green"]ndiswrapper -l[/COLOR]
autorun : invalid driver!
sis163u : invalid driver!
sis163u.sys : invalid driver!
maha@maha-dlu:~/Desktop/bla/Drivers/Windows2000$ 


```

---

### Post by mahasmb on 2007-08-27
The Trendnet drivers are available for Windows 2000, XP, 98 and ME OS'es.

No matter which OS driver I use I always get the following message (I remove each driver and then re-install with):

sudo ndiswrapper -r sis163u
sudo ndiswrapper -i sis163u.inf
```
installing sis163u...
couldn't open sis163u.inf: No such file or directory at /usr/sbin/ndiswrapper line 217.
```

I hope this helps to pinpoint my problem.

---

### Post by mahasmb on 2007-08-28
Anyone? 

Please? 

My computer's useless without internet and the Windows partition on it is so messed up it's even more useless.

---

### Post by mahasmb on 2007-08-29
**THANK GOODNESS!!**

After two days of doing nearly nothing else, (because like I said, my computer's useless without internet) and hours of trying out everything I can and refreshing this page over and over just hoping someone would come up with something, ANYTHING, that could help. I *think* and really hope I've found something that works for at least installing my drivers.

Using the following website:
[http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html](http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html)

I installed unshield or the "libunshield0" package (from [[COLOR="Red"]here[/COLOR]](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fu%2Funshield%2Flibunshield0_0.5-3_i386.deb&md5sum=4f52891a95bed2f458e3486b789066b9&arch=i386&type=main)) and then doing the following

```
gksudo gedit /etc/modules
```

and adding the word 'ndiswrapper' to the bottom of the file, **I WAS FINALLY ABLE TO INSTALL MY DRIVER!**

And now I can actually see the wireless networks in my area!

So, that's a big improvement so far.

EDIT:
Awesomeness! I'm fully connected to my network with WPA-PSK encryption right now.

Goes to show you, perseverance can really pay off.

---

### Post by haran_hockey on 2008-05-14
EDIT: What did you do after you installed ndiswrapper.

---

### Post by KennyMac on 2008-07-21
> **haran_hockey said:**
> EDIT: What did you do after you installed ndiswrapper.
For those new to Ubuntu, let me add the following which might help.  This worked on the following:

Operating System: Hardy Heron
Wireless Card: Realtek
Wireless Card Drivers: net8185.inf (this is a Windows XP driver provided by vendor)

1. Under Menu Item [Applications] at the top left of the screen - Select [Add/Remove] and then select "Windows Wireless Drivers" and "Ndiswrapper driver installation tool" (Note: you should see star rating after this).

2. Mark this for installation and then apply the changes.

(This effectively installs the infamous NDISWRAPPER module)

3.  Open a terminal session [Applications ->Accessories ->Terminal]

4.  Type this in the terminal window: "sudo ndisgtk" without the quotes.  (Note: ndisgtk will invoke the visual graphical application - it (probably) does not show up on your menu).  ndisgtk was installed in #2 above, and prior to its installation, you did not have this program available to run.  Now you do!  Also note: sudo stands for "Switch User (Root Implied) and "Do" - you may have to provide your root user password now.

5.  After invoking (running) ndisgtk you have a little application running in a GUI window that allows you to add a driver.  If you see this, breath a sigh of relief.  You are close.

(when you purchased your wireless card, you should have gotten "drivers" from your vendor. If you did not, locate some (google your card + drivers).  your card can NOT 
WORK WITHOUT A DRIVER THAT TELLS IT WHAT TO DO - Same as under "any" other operating system.  

6.  You are now going to tell it (wrapper) where to get the driver. Click the folder icon and point to the path.  You are looking for a file ending in "inf". I tried the Windows XP driver that came with my card (net8185.inf) which did work fine.

7.  After you tell it where to find the driver, Network Manager should pop up, and you should now see (where you could not see before) Wireless Connection.  

8.  NOTE: I could not get Network Manager to work from the one that popped up.  It needed root privileges and I could not use it.  No Problem!  Just click your menu item:  System -> Admin -> Network.  Then you may have to "unlock" it with root password.  If you also need to provide the "encryption key", click the wireless connection and provide the needed elements.

Hope this helps.

---

