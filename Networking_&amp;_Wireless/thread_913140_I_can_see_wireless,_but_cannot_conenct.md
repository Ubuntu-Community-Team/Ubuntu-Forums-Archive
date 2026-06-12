---
title: "I can see wireless, but cannot conenct"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by aiko.uda on 2008-09-07
I have found some posting related to this topic, but yet to see a solution.

I can see my wireless connection in the Network Manager, but cannot connect to it. I need you help.

Thank you

aiko@aiko-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

aiko@aiko-laptop:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
aiko@aiko-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:09:4f:38
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.2.82 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 03
       serial: 00:1a:73:e7:68:e9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
aiko@aiko-laptop:~$ cat /etc/modprobe.d/blacklist
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

aiko@aiko-laptop:~$ lspci -nn | grep -i broadcom
03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
aiko@aiko-laptop:~$ 
aiko@aiko-laptop:~$

---

### Post by hajk on 2008-09-07
Can you describe precisely what happens when you click on your wireless network in the Network-Manager applet?

There are known problems with the Broadcom 4328 chip, Ndiswrapper and WPA/WPA2 security... is this the problem in your case?

---

### Post by aiko.uda on 2008-09-07
> **hajk said:**
> Can you describe precisely what happens when you click on your wireless network in the Network-Manager applet?

When I click the Network Manager icon on the upper right hand side (two screens overwrapping each other), I see all available wireless conection in the drop down menu. I click my wireless network and Wireless Network Key Required dialog box opens.

Choices I have here are as follows:
Wireless Security: WEP 123-bit Passphrase, WEP 64/128-bit Hex, WEP 64/128-bit ASCII, or LEAP
Passphrase:
Authentication: Open System, Shared Key

I chose WEP 128-bit Passphrase and Open system, type in my password, and click connect. The dialog box closes.

The Network Manager icon changes from two screens to two black dots and a blue thing going around the two dots. The bottom left dot becomes from black to green. After a while trying to connect to the Internet, dialogue box opens asking me to type in the password, I type, and goes back to the beginning of this paragraph. It's a repetition.

Yes, I did check the password I am typing and it's the right one. I have another computer connecting to the wireless with the same password and it's working perfectly fine.

> **hajk said:**
> There are known problems with the Broadcom 4328 chip, Ndiswrapper and WPA/WPA2 security... is this the problem in your case?

I am really newbie and I am not sure what you are talking about... I know I had to install something for Ndiswrapper so that I can get this wireless icon appearing on my Network Manager.

How can I get the info for you???

---

### Post by hajk on 2008-09-07
OK, the good news is that your wireless interface wlan0 is working. The bad news is that Ndiswrapper and security don't work together well, most likely timing out before accepting the security password. It sounds, from your description, exactly like the problem that many people with Broadcom 4328 (rev 05) chips have had (myself included, using it in an Apple MacBook Pro laptop). You could check that connecting to an open network is indeed possible. Sorry, I haven't seen a solution yet. You could try and install the latest version of Ndiswrapper from their SourceForge site; if that doesn't work either, than I suggest getting yourself a USB adapter with kernel support (I'm using the Linksys WUSB54GC).

---

### Post by aiko.uda on 2008-09-07
I just tried to connect to my neighbour's unsecured network, but it's not working either...

How would having a UBS adaptar help this issue?

---

### Post by hajk on 2008-09-07
Mmm... it surprises me that you can't connect to an open network. The neighbour's access point could have MAC address restrictions, so not really open. Isn't there a wifi hotspot nearby?

(I'm assuming that there isn't a problem with your setup, and that the "sudo iwlist scan" command shows your network and others nearby.)

A USB adapter is a plugin wireless device that could be used instead of the built-in device.

---

### Post by aiko.uda on 2008-09-07
Uhm... If I try broadcom instead of Ndiswrapper, would that help?
I found this page, but I don't know if this works.

[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

### Post by Ayuthia on 2008-09-07
> **aiko.uda said:**
> Uhm... If I try broadcom instead of Ndiswrapper, would that help?
I found this page, but I don't know if this works.

[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

You can try this link.  The Broadcom driver does support your card.  I have seem some people use this driver with your card and have had success.  If you don't want to try the kernel that is currently in test, you can go to the Broadcom site that is linked in the post and compile the driver yourself.  It should work with the current kernel.  If you go this route, you can try and use this link starting at post 49:
[http://ubuntuforums.org/showthread.php?t=780692](http://ubuntuforums.org/showthread.php?t=780692)

You will need to install build-essential.  It should be on your liveCD if you don't have a working internet connection.

---

### Post by aiko.uda on 2008-09-09
> **Ayuthia said:**
> You can try this link.  The Broadcom driver does support your card.  I have seem some people use this driver with your card and have had success.  If you don't want to try the kernel that is currently in test, you can go to the Broadcom site that is linked in the post and compile the driver yourself.  It should work with the current kernel.  If you go this route, you can try and use this link starting at post 49:
[http://ubuntuforums.org/showthread.php?t=780692](http://ubuntuforums.org/showthread.php?t=780692)

Hi Ayuthia,

This wireless thing is way over my head, and I'm sorry if I ask a stupid question. I think it is safer for me to chose a driver which is not in test. All I need is to follow all the code described in the post #49 on the link above, right?

"Compile a driver myself" means I type the codes into terminal???

Right now, I am connected with wired network. Do I need to remove or do anything with NDISwrapper and other drive I installed before I start the new process?

> You will need to install build-essential.  It should be on your liveCD if you don't have a working internet connection.

I have a Internet connection working (wired). I found the build-essential in Synaptic, but I have no clue as to what they talking about in its description. Do I need to understand this software, or just have it installed in my computer?

Thank you

---

### Post by Ayuthia on 2008-09-09
> **aiko.uda said:**
> Hi Ayuthia,

This wireless thing is way over my head, and I'm sorry if I ask a stupid question. I think it is safer for me to chose a driver which is not in test. All I need is to follow all the code described in the post #49 on the link above, right?

"Compile a driver myself" means I type the codes into terminal???
You are correct.  Post #49 in that link will help you compile the wireless driver and compiling a driver yourself means that you will need to do the commands in the Terminal. 

> Right now, I am connected with wired network. Do I need to remove or do anything with NDISwrapper and other drive I installed before I start the new process?
We should blacklist ndiswrapper and the other drivers, but for now we can wait.  The commands in post 49 will help us test the driver to see if it works.  If it does, we can then blacklist the unnecessary drivers.
> I have a Internet connection working (wired). I found the build-essential in Synaptic, but I have no clue as to what they talking about in its description. Do I need to understand this software, or just have it installed in my computer?

Thank you

You don't really need to understand the software.  It just provides some commands (the make command) that we need to compile the driver.

---

### Post by aiko.uda on 2008-09-09
Thank you so much. I will try it now.

---

### Post by aiko.uda on 2008-09-09
Ayuthia, what does this mean?

aiko@aiko-laptop:~$ tar -xrf <path>/hybrid-portsrc.tar.gz
bash: path: No such file or directory

---

### Post by Ayuthia on 2008-09-09
> **aiko.uda said:**
> Ayuthia, what does this mean?

aiko@aiko-laptop:~$ tar -xrf <path>/hybrid-portsrc.tar.gz
bash: path: No such file or directory

You are supposed to replace <path> with the location of where the file is located.  If you are already in the same directory as the .tar.gz file, just do:
```
tar -xrf hybrid-portsrc.tar.gz
```

---

### Post by aiko.uda on 2008-09-09
Hum... I am trying but this is what I have been getting...

aiko@aiko-laptop:~$ tar -xrf hybrid-portsrc.tar.gz
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.
aiko@aiko-laptop:~$ tar -xrf /home/aiko/wl_hybrid/hybrid-portsrc.tar.gz
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.
aiko@aiko-laptop:~$ 

I really appreciate your paitience and help!

---

### Post by Ayuthia on 2008-09-09
> **aiko.uda said:**
> Hum... I am trying but this is what I have been getting...

aiko@aiko-laptop:~$ tar -xrf hybrid-portsrc.tar.gz
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.
aiko@aiko-laptop:~$ tar -xrf /home/aiko/wl_hybrid/hybrid-portsrc.tar.gz
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.
aiko@aiko-laptop:~$ 

I really appreciate your paitience and help!
Let's try this:
```
cd /home/aiko/wl_hybrid
tar -xvvf hybrid-portsrc.tar.gz
```
Hopefully that will work better.  The commands that you were using came from the Broadcom site.  I have had success with using the one in this post.

---

### Post by aiko.uda on 2008-09-09
aiko@aiko-laptop:~$ cd /home/aiko/wl_hybrid
aiko@aiko-laptop:~/wl_hybrid$ tar -xvvf hybrid-portsrc.tar.gz
tar: hybrid-portsrc.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

Somehow, the name appearing in the folder is following.
hybrid-portsrc-x86_32_5_10_27_6.tar.gz

---

### Post by Ayuthia on 2008-09-09
> **aiko.uda said:**
> aiko@aiko-laptop:~$ cd /home/aiko/wl_hybrid
aiko@aiko-laptop:~/wl_hybrid$ tar -xvvf hybrid-portsrc.tar.gz
tar: hybrid-portsrc.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

Somehow, the name appearing in the folder is following.
hybrid-portsrc-x86_32_5_10_27_6.tar.gz

Ok.  Let's go ahead and do the following:
```
cd /home/aiko/wl_hybrid
tar -xvvf hybrid*.tar.gz
```
That should get it.

---

### Post by aiko.uda on 2008-09-10
Hi Ayuthia! I managed it. Thank you so so much. 

The last line.
aiko@aiko-laptop:~$ echo `uname -r`
2.6.24-19-generic

Now, the new driver is not shown in the Windows Wireless Network nor Network Manager. What next???

---

### Post by Ayuthia on 2008-09-10
> **aiko.uda said:**
> Hi Ayuthia! I managed it. Thank you so so much. 

The last line.
aiko@aiko-laptop:~$ echo `uname -r`
2.6.24-19-generic

Now, the new driver is not shown in the Windows Wireless Network nor Network Manager. What next???

Ok.  I am assuming that the wl.ko module was updated.  Just to be sure, can you post the results of the following:
```
sudo updatedb
locate wl.ko
```This will update the search database and let us know if it can find the wl driver.

Since you are not able to get anything in network manager, can you post the results of:
```
lshw -C network
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e b44 -e wl
```
This will let us see what driver your wireless is trying to use and also let us know what wireless modules are currently loaded.

---

### Post by aiko.uda on 2008-09-10
This is the result.

aiko@aiko-laptop:~$ sudo updatedb
[sudo] password for aiko: 
aiko@aiko-laptop:~$ locate wl.ko
/home/aiko/wl_hybrid/.wl.ko.cmd
/home/aiko/wl_hybrid/wl.ko
/lib/modules/2.6.24-19-generic/wl_hybrid/wl.ko
aiko@aiko-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:09:4f:38
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.2.82 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:1a:73:e7:68:e9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
aiko@aiko-laptop:~$ lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e b44 -e wl
ndiswrapper           192920  0 
wl                   1073924  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
usbcore               146028  6 ndiswrapper,uvcvideo,hci_usb,ehci_hcd,ohci_hcd
aiko@aiko-laptop:~$

---

### Post by Ayuthia on 2008-09-10
> **aiko.uda said:**
> This is the result.

aiko@aiko-laptop:~$ sudo updatedb
[sudo] password for aiko: 
aiko@aiko-laptop:~$ locate wl.ko
/home/aiko/wl_hybrid/.wl.ko.cmd
/home/aiko/wl_hybrid/wl.ko
/lib/modules/2.6.24-19-generic/wl_hybrid/wl.ko
aiko@aiko-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:09:4f:38
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.2.82 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:1a:73:e7:68:e9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
aiko@aiko-laptop:~$ lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e b44 -e wl
ndiswrapper           192920  0 
wl                   1073924  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
usbcore               146028  6 ndiswrapper,uvcvideo,hci_usb,ehci_hcd,ohci_hcd
aiko@aiko-laptop:~$

It looks like the ndiswrapper module is still present.  Do you know if you are using a script for it?  Some guides have you create something in /etc/init.d and some have you add something in /etc/rc.local.  Do you recall doing this?  Those will need to be taken out if you did.  It looks like you might not because I don't see the b44 module anywhere.

If you did not create a script we can blacklist ndiswrapper:
```
echo blacklist ndiswrapper|sudo tee -a /etc/modprobe.d/blacklist
```

You can try the following for the current session to see if your card works:
```
sudo modprobe -r b43 ssb bcm43xx wl ndiswrapper
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```

---

### Post by aiko.uda on 2008-09-11
> **Ayuthia said:**
> It looks like the ndiswrapper module is still present.  Do you know if you are using a script for it?  Some guides have you create something in /etc/init.d and some have you add something in /etc/rc.local.  Do you recall doing this?  Those will need to be taken out if you did.  It looks like you might not because I don't see the b44 module anywhere.

I do not remember. I followed your previous posting #8 on the page below.
[http://ubuntuforums.org/showthread.php?t=908001&highlight=aiko.uda](http://ubuntuforums.org/showthread.php?t=908001&highlight=aiko.uda)

> **Ayuthia said:**
> 

Result.
aiko@aiko-laptop:~$ echo blacklist ndiswrapper|sudo tee -a etc/modprobe.d/blacklist
tee: etc/modprobe.d/blacklist: No such file or directory
blacklist ndiswrapper

[QUOTE=Ayuthia;5761791You can try the following for the current session to see if your card works:
```
sudo modprobe -r b43 ssb bcm43xx wl ndiswrapper
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```

Result.
aiko@aiko-laptop:~$ sudo modprobe -r b43 ssb bcm43xx wl ndiswrapper
aiko@aiko-laptop:~$ sudo modprobe wl
aiko@aiko-laptop:~$ ifconfig eth1 up
SIOCSIFFLAGS: Permission denied
aiko@aiko-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:70:90:FA:8C
                    ESSID:""
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-83 dBm  Noise level:-90 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:18:F8:3E:AD:42
                    ESSID:"Bathing Suit Area"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-76 dBm  Noise level:-87 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: 00:19:E4:D3:A0:C1
                    ESSID:"Home"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:1C:F0:F7:9C:13
                    ESSID:"wcps"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:1/5  Signal level:-89 dBm  Noise level:-91 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:19:5B:D8:C9:EC
                    ESSID:"Educacentre"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:2/5  Signal level:-77 dBm  Noise level:-85 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 06 - Address: 00:19:5B:D8:C9:94
                    ESSID:"college"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:4/5  Signal level:-59 dBm  Noise level:-90 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 07 - Address: 00:15:70:92:39:6C
                    ESSID:""
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/5  Signal level:-91 dBm  Noise level:-87 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

Permission denied...?

---

### Post by Ayuthia on 2008-09-12
> **aiko.uda said:**
> I do not remember. I followed your previous posting #8 on the page below.
[http://ubuntuforums.org/showthread.php?t=908001&highlight=aiko.uda](http://ubuntuforums.org/showthread.php?t=908001&highlight=aiko.uda)



Result.
aiko@aiko-laptop:~$ echo blacklist ndiswrapper|sudo tee -a etc/modprobe.d/blacklist
tee: etc/modprobe.d/blacklist: No such file or directory
blacklist ndiswrapper



Result.
aiko@aiko-laptop:~$ sudo modprobe -r b43 ssb bcm43xx wl ndiswrapper
aiko@aiko-laptop:~$ sudo modprobe wl
aiko@aiko-laptop:~$ ifconfig eth1 up
SIOCSIFFLAGS: Permission denied
You left out the sudo in front of ifconfig eth1 up.

---

### Post by aiko.uda on 2008-09-13
Hi Ayuthia

I am connected!!! Thank you so so so much! Without your help, I would have had to go back to Windows Vista which I really did not want. I was almost giving up on trying Ubuntu. Thank you again for your patients and hand in hand support!

Warmest regards,

Aiko

---

