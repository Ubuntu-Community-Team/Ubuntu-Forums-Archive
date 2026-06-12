---
title: "Ubuntu and wireless despite reaserch!"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by jamle on 2009-07-21
hi guys and girls. I have made the leap to linux making my home laptop dual boot vista and ubuntu jaunty (the new one?). its works brilliantly on my asus ee pc netbook and loving linux! 

HOWEVER! after installing on my home laptop a acer 5315 the issues began. Wireless.. it didnt want to work with my card puching the button didnt do anything (normally lights up) and after nearly giving up it popped a message a few days later asking to install a driver!?! low and be hold it installed and vola i have internet again!

yesterday i went to use it as normal and no internet... checked the router wasnt issue made new connection out details in again (same as before) nope nothing. i then noticed light wasnt on! i push the button and light came on but still nothing happens. ive gone into 
system > administartion > hardware drivers found the driver is still activated so i dont know what on earth to do ive head about ndiscwrapper which i installed through package manager after tweaking it to appear on the search and i ASUME its installed but i cant find it and dont see how it will help me if i was to find it. ive searched and found other topics with my laptop on but dont cover the issue of what happens when u get it to work with the wireless card and then randomly stop?

---

### Post by c0mput3r_n3rD on 2009-07-21
> **jamle said:**
> hi guys and girls. I have made the leap to linux making my home laptop dual boot vista and ubuntu jaunty (the new one?). its works brilliantly on my asus ee pc netbook and loving linux! 

HOWEVER! after installing on my home laptop a acer 5315 the issues began. Wireless.. it didnt want to work with my card puching the button didnt do anything (normally lights up) and after nearly giving up it popped a message a few days later asking to install a driver!?! low and be hold it installed and vola i have internet again!

yesterday i went to use it as normal and no internet... checked the router wasnt issue made new connection out details in again (same as before) nope nothing. i then noticed light wasnt on! i push the button and light came on but still nothing happens. ive gone into 
system > administartion > hardware drivers found the driver is still activated so i dont know what on earth to do ive head about ndiscwrapper which i installed through package manager after tweaking it to appear on the search and i ASUME its installed but i cant find it and dont see how it will help me if i was to find it. ive searched and found other topics with my laptop on but dont cover the issue of what happens when u get it to work with the wireless card and then randomly stop?


Hello.
First of all 9.04 Jaunty is the newest version.  The 9 stands for 2009 and the 04 stands for april (all of the version numbers correspond accordingly).  
You can try reinstalling the driver through System -> Administration -> Hardware drivers and see if that works.  As well, you can try using Windows Wireless program found in add/remove programs.
The reason why you can't find ndiswrapper is because it's installed into a root directory.  The way you use ndiswrapper is through the command prompt.  By typing ndiswrapper [options] file to install (.inf driver file).  Although; Windows Wireless program uses ndiswrapper, but through a graphical interface.  In order to be able to use it you have to have to driver for windows, have it installed and get the .inf file (something like: net5523.inf [you can get that from your vista partiton from Ubuntu]).

Hope that helps. :)

---

### Post by cariboo on 2009-07-21
If wireless worked, I wouldn't bother with ndiswrapper. If your wireless device was turned off on boot, it wouldn't have been detected, so it didn't receive an ip address. You can try right-clicking the network manager icon in the top panel and removing the check mark from enable wireless, then enabling it again or open an Applications-->Accessories-->Terminal and type:

```
sudo dhclient wlan0
```

Assuming that your wireless device is wlan0, the above command should get you an ip address.

---

### Post by LookTJ on 2009-07-21
do you have some sort of function key or switch to turn wireless on/off?

The way I interpret the OP is that it's not a driver problem, I think it's a hardware issue 

:)

---

### Post by jamle on 2009-07-22
right i shall give that terminal code a bash when i get in from work, i do have a toggle on off wireless button but it works fine turning it on and off. hopefully the code will work, failing that i have tried to remove the driver to re-install it but after getting to hardware drivers screen the only options on that screen is to activate or de-activate..

update: after typing the code in i got 
SIOCSIFADDR: no such device
wlan0: ERROR while getting interface flags: no such device
wlan0: ERROR while getting interface flags: no such device
bind socket to interface: no such device


the fact i cant even see the usuall thing in the tray at top right of screen to click enable etcc fromthe little drop down menu isnt there... cant see it on the list to add things to it.. REALLY confused now lol

---

### Post by jamle on 2009-07-22
bump up for help to get me back online for home laptop, need want 2 need 2 resort back to slow vista:(

---

### Post by superprash2003 on 2009-07-23
post outputs of the following
1)sudo iwlist scanning
2)iwconfig
3)ifconfig

---

### Post by jamle on 2009-07-23
sudo iwlist
lo interface doesn't support scanning
eth0  interface doesn't support scanning
eth1 failed to read scan data : invalid argument
pan0  interface doesn't support scanning

iwconfig

lo no wireless extensions
eth0 no wireless extensions
eth1 IEEE 802.11 Nickname: ""
       access point: not ssociated
        link quality: 4 signal levle:198 noise levle: 165
        Rx invalid nwid : 0 invaild crypt: 1   invaild misc:0
pan0 no wireless extensions

ifconfig


  	 	 	 	 	 	  eth0      Link encap:Ethernet  HWaddr 00:1b:38:66:04:4b   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:18  
 

 eth1      Link encap:Ethernet  HWaddr 00:1d:d9:61:46:96   
           inet6 addr: fe80::21d:d9ff:fe61:4696/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:46  
           TX packets:9 errors:6 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:3150 (3.1 KB)  
           Interrupt:19  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:236 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:236 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:15568 (15.5 KB)  TX bytes:15568 (15.5 KB)


Ive found i now have to trn on the wireless myself manually rather then it automaticlly doing it its self...

---

### Post by jamle on 2009-07-24
does that list of codes u asked for help at all lol, im really beyond my capabilities here lol.

---

### Post by mapes12 on 2009-07-24
Please post the output to ```
lspci
```

---

### Post by jamle on 2009-07-24
okay here is results from that lol, i havnt a bloody clue what this means i could be giving my enntire computers secrets and i wouldnt know lmao, i just want to use my ubuntu online again :-( was gaving such a good time tellin every1 how awesome it is untill this happens which really is a pain no internet renders it useless to me!

  	 	 	 	 	 	  lspci  
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
 00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)  
 00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)  
 00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)  
 00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)  
 00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)  
 00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)  
 00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)  
 00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)  
 00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)  
 05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)  
 06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by mapes12 on 2009-07-25
You have a Broadcom wifi adapter (last line of your output) which requires a special package to be installed to make it work. Go to Synpatic and search for fwcutter. You should find a package called b43 fwcutter and install it. Then go into Network Manager and disable your wifi device then enable it again. You may have to reboot.

These links should also help:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

Mark

EDIT: > i could be giving my enntire computers secrets and i wouldnt knowDon't worry. There is nothing in the output to give anything away about your stuff. The output just lists the adapters in your machine. That's all.

---

### Post by jamle on 2009-07-25
brilliant thankyou thats exaclly what i wanted to hear lol. will give it a bash when i get in from work and let u know!:D

---

### Post by jamle on 2009-07-25
Ive installed the software u said (cant find it on the system or applications drop downs, and the network manager thaat used to be in top right corner with clock etc isnt there and i dont know how to fnd it :-(

---

### Post by mapes12 on 2009-07-25
You shouldn't need to find it. Provided the package installed OK then disable then re enable your wifi adapter. What happens?

---

### Post by jamle on 2009-07-25
when u say "enable" u mean tick and then un tick the "enable" button on the wireless signal style bar in top right of the "notification" / "tray" thing? as it isnt there i dont know why it used to be but its disapeared. I TOGGLED the wireless on /off button couple times then restated etc but buy powering it on or having it off linux doesnt do anything to recognise ive tourned it on.... so in repsonce to the toggle button it does nothing... am worried i wont be able to get this working again now without mayb a fresh install and losing al the stuff ive added changed etc, but ur replys are giving me a glimpse of possibilite of using ubuntu again lol (vista is killing me its so slow lol)

---

### Post by mapes12 on 2009-07-26
In synaptic try installing the other support package for your card

**bcm43xx-fwcutter**

Did you have a look at this page? [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by jamle on 2009-07-28
after messing around trying other distro's ive gone back to ubuntu jauntyz and tried the first gguide u suggested i located the wireless driver from my windows partition and copyed it to the desktop but i cant install bcm43xx-fwcutter, ive tried all sorts of combinations an i cant get it to appear its not coming up when i serch in the package manager or try the terminal line
sudo apt-get install bcm43xx-fwcutter
just says E: Couldnt find package bcm43xx-fwcutter

feels like im so close but yet so far please help!

---

### Post by jamle on 2009-07-28
bump 4 help =(

---

