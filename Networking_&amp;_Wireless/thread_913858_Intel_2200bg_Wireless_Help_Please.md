---
title: "Intel 2200bg Wireless Help Please"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by ozanamn on 2008-09-08
Hey all

Hope somebody could help me here as if i dont get this wifi card working i will have to go back to m$ which is something i really really dont want to do. REALLY dont want to do.

I have a NX8220 Laptop [Here]("http://search.hp.com/gwieeng/query.html?cc=ie&lang=en&qt=nx8220&la=en") and a intel 2200bg Pro/wireless adapter in the laptop [Here]("http://support.intel.com/support/wireless/wlan/pro2200bg/")the intel website gives linux drivers which i have no idea how to install. I used ndiswrapper with the windows drivers and it picked up the card and i have wifi option, The thing is it just cant find and wireless networks in the area. I think its that the card isnt turned on because i read a few forums and they give you a command to put in to start the card but it doenst work for me so the other option was to install windows and turn the card on and reinstall ubuntu, But thats not an option. So inturn thinking i was really smart i installed windows with virtualbox but of course it didnt pick up the wireless as for windows to see it in the virtualbox ubuntu would still have had to have turned the card on so that was a waste of an hour or two. 

Any help on the subject would be much appreciated.

Also on my desktop pc i also have ndiswrapper running but i have a little problem i need the gui to load the drivers for the wireless on that as for some unknown reason to me it wont work by command line and now when i try to load ndiswrapper it says starting administration and flashes the ndiswrapper gui for a second and shuts itself down. so no im down two computers with no internet. I need both for work and i need the internet on both and really want to ubuntu as an operation system. Everything else has worked on ubuntu. The only problems i have with them is the wireless which i thought i had got past it.

---

### Post by Kevbert on 2008-09-08
What you could do is put the Hardy install CD in the drive, using Nautilus file manager browse to pool, main, n, ndiswrapper and double click on each of the .deb files in turn in this directory to install ndiswrapper and utils. Next you want to go up one directory and go into the ndisgtk directory and double click on the .deb file there. The file that you've just installed in the graphical front end for ndiswrapper. This file can be found under System-Admin-Windows Wireless Drivers. You can now use your Intel windows drivers (CD) by browsing to them using this program (click on the folder icon to the right of the text box). The file that you need is an .inf file.

---

### Post by ozanamn on 2008-09-08
Hi 

Thanks for your response ill try that out when i get home and let you know how it goes. Thanks

Regards,
Oz

---

### Post by ozanamn on 2008-09-08
Im trying that know with the live cd but has anyone got any ideas about the laptop. 

THanks again,
Oz

---

### Post by Kevbert on 2008-09-11
You should be able to use the procedure for both laptop and desktop.  Regarding the switch.  This could be a bit more of a problem as there was a similar problem with Acer laptops and the front panel switch (I have one, but can't remember the solution).  Somewhere on the forums there is a guide on this, if the drivers don't resolve the problem.  You could also try,in terminal,
```
ifconfig wlan0 up
```
-substitute the name of your connection for wlan0.  You can get this via
```
iwconfig
```
It will show the type of adapter you have 802.11a/b/g or N.  Then to scan for wireless networks including your router you can use
```
iwlist scanning
```
Please post back if you have any further questions.

---

### Post by ozanamn on 2008-09-11
Hi Kevbert

I tried what you said, Still getting no results. Have you any other input on this, Thanks

Thanks for your time,
Oz

---

### Post by Crafty Kisses on 2008-09-11
Try this add these lines to the following config file:
```
/etc/network/interfaces
```
Then after that comes up, add these lines:
```
auto eth1
iface eth1 inet dhcp
```
That should work.

---

### Post by Kevbert on 2008-09-12
Please post the outputs for
```
iwconfig
lshw -C network
```

for the laptop and desktop.

---

### Post by ozanamn on 2008-09-12
Hey again Thanks for getting back to me.

Here is the information you where looking for.

lshw -C network
> scott@scott-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 11
       serial: 00:14:c2:e2:fb:48
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5751m-v3.29a latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 05
       serial: 00:15:00:4d:56:7e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+w29n51 driverversion=1.52+Intel,09/12/2005,9.0.3.9 latency=64 maxlatency=24 mingnt=3 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: vnet0
       serial: 1e:30:92:a1:9d:4c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 multicast=yes
scott@scott-laptop:~$ 



iwconfig
> 
scott@scott-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          RTS thr=1600 B   Fragment thr=2304 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

vnet0     no wireless extensions.


Sorry i will post the output for the desktop later on as im in work at the moment. 

Also thanks for your input codename but unfortunately that did not work but thanks for your input. 



Regards,
Oz

PS: my job takes me many places and today im working in microsoft and i pull out the ubuntu laptop and all the people around my desk are all like omg how you do that. Ubuntu 1 - MIcrosoft 0 haha

---

### Post by Kevbert on 2008-09-12
It looks like the firmware is on the PC but it may be that the drivers have been blacklisted.  The driver files can be found in /lib/firmware/2.6.24-19-generic and are named ipw2200xxx.fw (at least on my version of Xubuntu).
Please take a look at this [[COLOR="Red"]post[/COLOR]]("http://ph.ubuntuforums.com/showthread.php?p=5615397"), especially from #6 onwards.
Good to hear that Microsoft staff are interested in Ubuntu (as long as they don't try to take over!!!)

---

### Post by ozanamn on 2008-09-15
Hi Sorry 

I was away for the weekend didn't get to try that out until today. Thanks for getting back to me so fast. This is the output from that forum. It didn't work but at lest we got an error.

```
scott@scott-laptop:~$ sudo rmmod -f ipw2200
[sudo] password for scott: 
ERROR: Removing 'ipw2200': No such file or directory
scott@scott-laptop:~$ sudo modprobe ipw2200 disable=0 led=1
scott@scott-laptop:~$ 


```

I Wonder would that have anything to do with the fact that I didn't install the linux drivers and used the windows drivers on ndiswrapper.

Regards,
Oz

---

### Post by ozanamn on 2008-09-15
Oh and here is my blacklist file if it makes any sense to someone. 

```
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

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

```

---

### Post by ozanamn on 2008-10-03
You wont believe it. After everything i tried to get this wireless working the wireless card was broke in the first place. I didn't realize as the laptop was second hand. I put my hard drive in another laptop of the same model and it work right away. I went out and bought a Belkin wireless card stuck it in the side and boom badda bing Michel Jackson is your brother we have wireless.

---

