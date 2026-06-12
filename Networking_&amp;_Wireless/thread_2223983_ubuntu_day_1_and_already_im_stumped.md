---
title: "ubuntu day 1 and already im stumped"
date: 2014-05-13
forum: Networking &amp; Wireless
---

### Post by Trey_Porter on 2014-05-13
ive used micorsoft since windows 3.1.

i bought a laptop for my kids and it had windows that constantly telling me i had an unregistered copy of windows. eventually it wouldnt let me in at all. after reading many articles on linux OS, i downloaded ubuntu. everything blew me away. i couldnt imagine i would get this much of an OS for free... nevertheless, i am having one MAJOR issue. i bought the laptop so my kids could hdmi into their tv from the computer for youtube, ect.  

from the gate i noticed i couldnt find the wireless network center. i plugged in the ethernet cable and the internet works just fine. but i NEED wireless, or this computer is useless to me. i cant buy a good copy of windows as i just sunk all my spare $ into this system. i have read a lot on this issue the past 24 hours, i have also watched countless youtube vids trying to get help without having to ask for it. alas, i was unable. now i need help. can anyone tell me what i can do?

i have comcast 50mbs service, the modem is also the router
the computer is dell latitude D630.

this is the info on my processor:
Status     End of Interactive Support
Launch Date     Q3'07
Processor Number     T7250
# of Cores     2
Clock Speed     2 GHz
L2 Cache     2 MB
FSB Speed     800 MHz
FSB Parity     No
Instruction Set     64-bit
Embedded Options Available
    No
Lithography     65 nm
Max TDP     35 W
VID Voltage Range     1.075V-1.175V

and my network card is: Intel 3945 WLAN (802.11a/g) mini Card

can anyone please help me. oh yeah, i am running the most uptodate ubuntu

---

### Post by HiImTye on 2014-05-14
what does```
iw dev
ip addr
```tell you?

---

### Post by SeijiSensei on 2014-05-14
That Intel wireless card is well-supported in Linux.  When you click on the [Network Manager icon](https://help.ubuntu.com/community/NetworkManager#NM-applet_Overview) in the system tray, can you not see your local wifi hotspot?

Update: Some people [report]("http://askubuntu.com/questions/449658/networkmanager-tray-nm-applet-is-gone-after-upgrade-to-14-04-trusty") that the Network Manager icon does not appear correctly in 14.04. There are a couple of proposed solutions in that linked article.

As you can see in my profile, I don't use vanilla Ubuntu with the "Unity" interface.  I prefer a different "desktop environment" called KDE.  A version of Ubuntu packaged together with that environment is released as Kubuntu.  The installation image for version 14.04, Trusty, is here: [http://www.kubuntu.org/getkubuntu/](http://www.kubuntu.org/getkubuntu/).  If you've only been using Ubuntu for a day, I suggest you try out Kubuntu and maybe also the other choices like Lubuntu or Xubuntu.  These two use less-demanding desktop environments than Unity or KDE and are generally targeted at weaker machines than yours.  Still you and your kids might find any of these alternatives to regular Ubuntu more appealing.

All Ubuntu releases offer a method to "try" Ubuntu first before installing.  These demo sessions will run much slower than a fully-installed version because they rely on the optical disc for all their program code.  Other than that, you have a full desktop session so you can "try before you buy."

For the HDMI issue, please [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and run this command:
```
lspci | grep VGA
```
so we can see what video hardware you have available.

Some laptops use "hybrid" designs that include both a motherboard Intel chip for ordinary tasks and a proprietary adapter for games, video, etc.  For instance, on my machine that command returns:
```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT]

```
Systems like this can take some futzing to get HDMI to work properly.  I have to use the ATI adapter to connect over HDMI.  I do get full video and sound with the proper drivers.  Some machines pair NVIDIA adapters with the Intel ones, too.

Oh, and please wrap your responses in [noparse]```

```[/noparse] tags for legibility.

Update:  [According to Dell]("http://www.dell.com/us/dfb/p/latitude-d630/pd") your machine has an NVIDIA Quadro NVS 135M and Intel motherboard video.  I'd first try running the Additional Drivers application in the System menu to see whether Linux can detect the NVIDIA card and install the drivers for it.  If it cannot see the NVIDIA adapter, you might need to change a BIOS setting to force it to be the primary adapter.

---

### Post by zacktu on 2014-05-14
I use vanilla Ubuntu with Unity, and I think that the Network Manager is visible across the top of your window.  (I don't recall ever installing anything to be able to manage Ethernet and wireless networking.)  If you're using Ethernet, you should see up-and-down arrows side-by-side in the upper right corner.  Click on the icon and a window with all the options that you see with Windows will appear, so you can make your wireless selection there.

---

### Post by SeijiSensei on 2014-05-14
Thanks for adding that, zacktu.  I thought NM was visible the last time I looked at Unity, but since I use Kubuntu, I wasn't sure whether that might have been Trey's problem.

However your profile says you're running 12.04.  The problem with the NM icon reportedly occurs in the latest version, 14.04.

---

### Post by Trey_Porter on 2014-05-14
> **HiImTye said:**
> what does```
iw dev
ip addr
```tell you?

>                          porterfamily@porterfamily-Latitude-D630:~$ iw dev 
 porterfamily@porterfamily-Latitude-D630:~$ ip addr 
 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default  
     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00 
     inet 127.0.0.1/8 scope host lo 
        valid_lft forever preferred_lft forever 
     inet6 ::1/128 scope host  
        valid_lft forever preferred_lft forever 
 2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000 
     link/ether 00:1c:23:1b:ee:d2 brd ff:ff:ff:ff:ff:ff 
     inet 10.0.0.3/24 brd 10.0.0.255 scope global eth0 
        valid_lft forever preferred_lft forever 
     inet6 fe80::21c:23ff:fe1b:eed2/64 scope link  
        valid_lft forever preferred_lft forever    
 

  

> **zacktu said:**
> I use vanilla Ubuntu with Unity, and I think that the Network Manager is visible across the top of your window.  (I don't recall ever installing anything to be able to manage Ethernet and wireless networking.)  If you're using Ethernet, you should see up-and-down arrows side-by-side in the upper right corner.  Click on the icon and a window with all the options that you see with Windows will appear, so you can make your wireless selection there.

> i have 14.04, and after doing google searches yesterday, i have found that MANY people are having this issue. ethernet works flawlessly. no where on this computer can i find the wireless networks. i know it works. i used it in windows before installing this over windows.

> **SeijiSensei said:**
> That Intel wireless card is well-supported in Linux.  When you click on the [Network Manager icon]("https://help.ubuntu.com/community/NetworkManager#NM-applet_Overview") in the system tray, can you not see your local wifi hotspot?

Update: Some people [report]("http://askubuntu.com/questions/449658/networkmanager-tray-nm-applet-is-gone-after-upgrade-to-14-04-trusty") that the Network Manager icon does not appear correctly in 14.04. There are a couple of proposed solutions in that linked article.

As you can see in my profile, I don't use vanilla Ubuntu with the "Unity" interface.  I prefer a different "desktop environment" called KDE.  A version of Ubuntu packaged together with that environment is released as Kubuntu.  The installation image for version 14.04, Trusty, is here: [http://www.kubuntu.org/getkubuntu/](http://www.kubuntu.org/getkubuntu/).  If you've only been using Ubuntu for a day, I suggest you try out Kubuntu and maybe also the other choices like Lubuntu or Xubuntu.  These two use less-demanding desktop environments than Unity or KDE and are generally targeted at weaker machines than yours.  Still you and your kids might find any of these alternatives to regular Ubuntu more appealing.

All Ubuntu releases offer a method to "try" Ubuntu first before installing.  These demo sessions will run much slower than a fully-installed version because they rely on the optical disc for all their program code.  Other than that, you have a full desktop session so you can "try before you buy."

[QUOTE]   	 	 	 	   no, not at all. it just shows the wired connection. i also installed Wicd Network Manager (suggested by someone on one of my many google searches.)
  and can i still do that since i have already fully installed it over windows in this laptop?


thanks for the help everyone!

---

### Post by HiImTye on 2014-05-14
> **Trey_Porter said:**
> [QUOTE=SeijiSensei;13023437]```
porterfamily@porterfamily-Latitude-D630:~$ iw dev 
 porterfamily@porterfamily-Latitude-D630:~$ ip addr 
 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default  
     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00 
     inet 127.0.0.1/8 scope host lo 
        valid_lft forever preferred_lft forever 
     inet6 ::1/128 scope host  
        valid_lft forever preferred_lft forever 
 2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000 
     link/ether 00:1c:23:1b:ee:d2 brd ff:ff:ff:ff:ff:ff 
     inet 10.0.0.3/24 brd 10.0.0.255 scope global eth0 
        valid_lft forever preferred_lft forever 
     inet6 fe80::21c:23ff:fe1b:eed2/64 scope link  
        valid_lft forever preferred_lft forever
```
this suggests that no wireless hardware was detected. take a look at the startup logs in /var/log/

---

### Post by SeijiSensei on 2014-05-15
> **Trey_Porter said:**
> this suggests that no wireless hardware was detected. take a look at the startup logs in /var/log/

Which is really uncommon with Intel adapters.  They are among the best-supported devices I know of.

Trey, I hate to ask this but, is the wifi adapter turned on?  Maybe it got disabled by accident.  There's usually an Fn-key combination that turns the wifi off and on.  Check the BIOS settings, too.

Another possibility might be missing firmware.  Try checking that the **linux-firmware** package is installed with
```
sudo apt-get install linux-firmware
```

Finally you can try forcing the machine to use the appropriate driver with
```
sudo modprobe -v iwlwifi
```
The "-v" is for "verbose" output.

---

