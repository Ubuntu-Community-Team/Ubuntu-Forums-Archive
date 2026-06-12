---
title: "Howto: Install And Use Your Trendnet Tew-424ub"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by boom2k1 on 2007-08-18
HOWTO: INSTALL AND USE YOUR TRENDNET TEW-424UB 54Mbps 802.11g Wireless USB 2.0 Adapter


Feel free to improve the content here by responding. I actually don't understand why I can't connect by entering my WEP 128bit ASCII to connect to my network using the Network Manager applet program in taskbar. I am forced to use the old command line way. Feedback is welcome.
======

Prerequisite: basic knowledge in using terminal (how to locate your files..)

1. The first step is to check whether your TEW-424UB usb device is connected properly AND know what device you have:

In terminal, type
lsusb
charles@charles-desktop:~$ lsusb
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 045e:00db Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  

Notice Bus 006 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. would represent my Trendnet TEW-424UB wireless adapter(, while "Microsoft Corp" is for my USB Ergonomic keyboard).

2. Install ndiswrapper (so you can install the Windows networking driver (the extension that ends in .inf)
I install it EASILY with Automatix (under Driver).

3. with ndiswrapper, I chose to install WIN2000 driver
The file name is net8187b.inf

In my case, I plug my Windows Driver CD into my DVDrom, and in terminal type:
 sudo ndiswrapper -i /cdrom/Driver/WIN2000/net8187b.inf 

This install the usb driver.


4. After installing the driver, we can now use the USB device.
I am going to create a script to automate the process so everytime I load into Ubuntu, I can call the script by doubling clicking the script file, put into my startup session, or use a file launcher for the script file to connect to my wireless network at home.
You may first test it out in terminal before putting the below content into a script file.

I am going to create a script file and a file launcher so everytime I start my computer, I can double click the file launcher on my desktop to connect to the internet.

a.
In your favorite text editor, type:

```

#1. using ndiswrapper as an interface to your already installed driver
sudo modprobe ndiswrapper

#2. scan for device... I once omitted it... it seems that this command is needed even if you already know which essid to connect
sudo iwlist wlan0 scan

#3. configuring
sudo iwconfig wlan0 essid YOUR_ESSID_NAME_SHOWN ABOVE key s:YOURPASSWORD

#4. automatic dhcl
sudo dhclient3 wlan0

sleep 5

#after 1., I should see the list of available wifi networks in the networking icon of the task bar. In principle I can actually finish the steps there in that graphical interface; however, it doesn't work for some strange reasons in my case.

```



Save the file. Right click that file in your file explorer and set execute permission to be true... (

b. 
Right click an empty region in the desktop and click Create Launcher:

Type: Application in Terminal (you would like to track if it detects your network well)
Name: Connect
Command: (click browse and go to your script)

press OK


...
You can now double click on it. You should now be connected to the internet.
Everytime when Ubuntu load up, you can double click the icon to connect to the Internet!
Alternatively, you can automate it to connect on startup by going to :
System->Preferences->Sessions
and add a new entry there that connect to your script. (i haven't tested this yet.)

That's it!

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

### Post by babysteps on 2007-08-28
> **boom2k1 said:**
> HOWTO: INSTALL AND USE YOUR TRENDNET TEW-424UB 54Mbps 802.11g Wireless USB 2.0 Adapter


Feel free to improve the content here by responding. I actually don't understand why I can't connect by entering my WEP 128bit ASCII to connect to my network using the Network Manager applet program in taskbar. I am forced to use the old command line way. Feedback is welcome........


Thanks for posting the script.  I am in a similar situation with the same wireless card and chipset on my 3rd computer that's going Ubuntu 7.04.(getting lots of practice!) and I'm stuck on the inability to connect to the internet. 

I was wondering if you could clarify what you did, if anything, with the Network Manager?  Did you have to uninstall Network Manager, and also get rid of the applet?  With the Network Manager set in Roaming mode I could see all the networks available, including the one I have a wep key for, but I cannot satiisfy the repeated request for the wep key.  I think the usb dongle actually associated with the network for a brief moment, and then it's back to nothing again.  When I do the sudo dhclient wlan0 bit i get the annoying message about no dhcp offers and that it's sleeping.   I wonder if you ever got that message and if so, how did you work around it?

Babysteps

---

### Post by mahasmb on 2007-08-29
I was able to solve my problem [[COLOR="Green"]here[/COLOR]](http://ubuntuforums.org/showthread.php?t=536373).

---

### Post by anfractuosities on 2007-09-23
when i installed this driver I got the message

-laptop:~/Desktop$ sudo ndiswrapper -i net8187b.inf

installing net8187b ...
couldn't find models section "Realtek" -
installation may be incomplete
--------------------------------------------------------------------

Found that i need 8185.inf....
but i ran into another problem I don't have a wlan0?  I am running an internal wireless card, but i want to use the usb one at certain times.  would this be complicating things?

---

### Post by k1ll1nt1m3 on 2007-10-13
I got mine working with net8187b.inf and rtl8187.sys.  I installed wlanassistant for a gui.  I am using ununtu-server 32bit with kubuntu-desktop installed.  Kwifimanager seemed to mess it up for me.  Here is my /etc/network/interfaces

```

# My Trial wifi
auto wlan0
iface wlan0 inet dhcp
wireless-essid   MY_ESSID
wireless-key     MY_KEY
wireless-channel 6
wireless-mode    managed

```

I wish I found this thread sooner.  I wasted 4 days trying to install a 32bit driver in a 64bit OS.  If anyone knows how to get this working in a 64bit OS I sure could use a link to it..  

Thanks

---

### Post by go_beep_yourself on 2007-12-29
lsusb shows this.

Bus 002 Device 005: ID 0bda:8189 Realtek Semiconductor Corp. 

It's not working. I've spent the last 2 days trying to get it to work. Is it impossible?

---

### Post by go_beep_yourself on 2007-12-31
Why do these Linux drivers here not work?

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#1432](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#1432)

I installed rtl8185_linux_26.1027.0823.2007. It did not work. How can I remove it? I've tried "sudo make uninstall" and "sudo ./makedrv uninstall" Please help :confused:

---

### Post by Tlingit on 2008-05-24
Hello,

How is everyone? Well I think i am missing something. Everything seems to pull through, but I am still not connected.

I saw something on the front of the Wireless help forum about the rtl8187b.

I fallowed both the helps everything seemed to work fine but I'm still not connected.

Well if some one could assist that would be great.

Have a great day!

---

### Post by go_beep_yourself on 2008-05-25
Hey, the problem is using the 32 bit xp drivers in 64-bit. Maybe I could install 32 bit kernel and system using enlightenment 17 as my windows manager just cause I like it and don't want a bloated system similar to Vista, know what I mean? Hey, I think it's worth a try. I'm probably not going to find many 64-bit users here, but if there are any, please let me know of your experience. Thank you.

go_beep_yourself :popcorn:

---

### Post by Tlingit on 2008-05-26
> **go_beep_yourself said:**
> Hey, the problem is using the 32 bit xp drivers in 64-bit. Maybe I could install 32 bit kernel and system using enlightenment 17 as my windows manager just cause I like it and don't want a bloated system similar to Vista, know what I mean? Hey, I think it's worth a try. I'm probably not going to find many 64-bit users here, but if there are any, please let me know of your experience. Thank you.

go_beep_yourself :popcorn:

Hey if you look at that last post i posted I showed how to get the rtl8187 to work it looked like you were using the same thing! so well i showed a link that got it to work but
[http://ubuntuforums.org/showthread.php?t=807353](http://ubuntuforums.org/showthread.php?t=807353)

hope this helps

---

### Post by go_beep_yourself on 2008-05-27
> **Tlingit said:**
> Hey if you look at that last post i posted I showed how to get the rtl8187 to work it looked like you were using the same thing! so well i showed a link that got it to work but
[http://ubuntuforums.org/showthread.php?t=807353](http://ubuntuforums.org/showthread.php?t=807353)

hope this helps

Okay, I'll respond on that thread.

---

