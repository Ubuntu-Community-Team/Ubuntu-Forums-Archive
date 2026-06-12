---
title: "Suddenly can't see any wireless networks, even after ubuntu reinstall"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by Brandon81 on 2008-10-12
EDIT: Anyone looking for help for their wireless issues don't look at this thread. My whole problem was the bios had a wireless switch which was FN+F2 and troubleshooting EVE I used ALT+F2 a bunch and mashed the bios function and didn't realize it. 

Hey... I'm new to Ubuntu, but I think I'm getting the hang of it... The only problem so far has been this wireless network issue I'm having. I have a Broadcom43 something, and it was working fine with ubuntu for three days. 

Then I downloaded Eve Online linux client, and I couldn't get it to display properly. I was reading through other people's experiences and I did a couple things, I wish I could remember what exactly and suddenly I couldn't see wireless networks. I thought it might have had something to do with the HAL layer from some other posts I was reading, so I really think it might have been something related to that if it helps. I wound up breaking my copy of linux, lost the gnome panel in trying some HAL fixes and wound up doing a fresh format and reinstall. Since the reinstall I did the same steps I did last time, download all the updates, then check the driver and enable it and reinstall the firmware. Haven't gotten the ability to see wireless networks since I started messing with Eve. 

I have searched for a while and I seriously can't find a fix that works for me. I am sorry for not  being able to be more specific, but I've done so much on the new os over the past few days that I'm not at all familiar with, from a ton of different forums, cause I'm a (converting) XP user. I'm also sorry for semi-ranting here, but I can't get this figured out and it's driving me insane. Especially with the reformat and reinstall. It doesn't make any sense. 

Any help would be appreciated.

I am using a Dell Inspiron 5160 with Ubuntu 8.04.

---

### Post by gwoodruff on 2008-10-12
Howdy, Did you try to install Eve again after the fresh Ubuntu install?  Open a terminal window and type ```
lspci
```Look for the broadcom line and post the exact chipset. And ```
ifconfig
```  Also post the output.

Thanks, Gary

---

### Post by Brandon81 on 2008-10-12
```
brandon@ubuntu-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
```

```
brandon@ubuntu-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:2a:d3:f5  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe2a:d3f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5007149 errors:1 dropped:0 overruns:0 frame:0
          TX packets:19130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2411 txqueuelen:1000 
          RX bytes:278708256 (265.7 MB)  TX bytes:1485818 (1.4 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112300 (109.6 KB)  TX bytes:112300 (109.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0b:7d:0b:5b:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0B-7D-0B-5B-96-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

No, I never did try to reinstall Eve... Thank you for your quick reply.

Broadcom Corporation BCM4306

---

### Post by gwoodruff on 2008-10-12
Howdy, It looks like the system recognizes your card and the driver is loaded. Try ```
iwlist scan
``` and post the result.

Gary

---

### Post by Brandon81 on 2008-10-12
```
brandon@ubuntu-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```

Thanks again!

I know there's a wireless network available, I'm on Xbox live wirelessly right now. :P

---

### Post by pytheas22 on 2008-10-13
Sorry to jump in, but I wanted to point out that Broadcom 4306 chips in Hardy don't work with the driver that gets used by default (b43).  It will create an interface but I don't think you'll be able to connect.  At least, that's always been my experience.

You could run these commands to switch back to the bcm43xx driver, however, which should support your card:

```
sudo sed 's/blacklist bcm43xx/#blacklist bcm43xx/' /etc/modprobe.d/blacklist
sudo apt-get install bcm43xx-fwcutter
```

You should be asked about downloading firmware automatically; say yes.  Then continue with:

```
sudo modprobe -r b43 b44 b43legacy ssb
sudo modprobe bcm43xx
```

Now your wireless should work and you should be able to connect.  If not, please post the output of:
```

lspci -nn | grep -i broadcom
sudo iwlist scan
dmesg | grep -e bcm -e eth1
ls /lib/firmware
lshw -C Network
```

As a disclaimer, your 4306 card may not be the same as mine--Broadcom's naming scheme is confusing and there may be more than one chipset named '4306'; I'm not sure.  The only way to know for certain that our cards are the same is to refer to their 'lspci *-nn*' entries, which will give a unique PCI ID (in the form of XXXX:XXXX).  Either way, even if the above steps don't work, once we know your PCI ID we can look up ones that do.

Also note that if the steps above get things working, you will need to run these commands each time you reboot your computer to get it to work again (there's a permanent automatic solution that we can apply once we make sure that the steps above actually work):

```
sudo modprobe -r b43 b44 b43legacy ssb
sudo modprobe bcm43xx
```

---

### Post by Brandon81 on 2008-10-13
Thank you so much for posting that information. I really appreciate the quick and easy nature of looking for help here. 

I tried what you posted, and after running those last two commands I lose my wired network somehow and still cannot see wireless networks. I click the network manager icon and it shows Wireless Networks indented, but nothing underneath that. 

What could this possibly be from? I have a fresh reinstall after format. It's gotta be something with firmware no?

Just to keep updates going, I am trying this right now:


I have resolved the problem with my broadcom 4306 card using this guide:

1) sudo gedit /etc/init.d/bcm43xxfix.sh

Write in the file:

         #! /bin/sh

         rmmod b43legacy
         rmmod b43
         rmmod bcm43xx
         rmmod ssb
         modprobe bcm43xx

2) cd /etc/init.d/ && sudo chmod 755 bcm43xxfix.sh
3) sudo update-rc.d bcm43xxfix.sh defaults
4) sudo gedit /etc/modprobe.d/blacklist

Replace in this file

         # replaced by b43 and ssb.
         blacklist bcm43xx

with

         # replaced by b43 and ssb.
         # blacklist bcm43xx

5) reboot

Let me know if it works also for you
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210373](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210373)

Additionally, unfortunately at this time I do not have a wired internet connection available for my laptop (I am at work) and so anything I download will have to go to a flash drive. 

Thank you.

EDIT: That did not work. Totally lost wireless. Going to try to undo it now.
EDIT: Okay, I seem to have undone it, and reinstalled from the Hardware Drivers item and now I'm back to where I was. It shows Wireless, but no wireless networks being seen.
EDIT: Thank you again so much! I really am loving this OS a lot, and am going to use it on my main PC (Going to dual boot with a really clean copy of XP for certain things), and luckily I won't have any wireless trouble with my main PC. My laptop used to run like crap with XP and it runs beautifully with Ubuntu, unfortunately this wireless network thing is really a killer here.

---

### Post by Brandon81 on 2008-10-13
The Results you asked for!

```
brandon@ubuntu-laptop:~$ lspci -nn | grep -i broadcom
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
```

```
brandon@ubuntu-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results
```

```
brandon@ubuntu-laptop:~$ dmesg | grep -e bcm -e eth1
[   49.905138] bcm43xx driver
```

```
brandon@ubuntu-laptop:~$ ls /lib/firmware
2.6.24-19-generic     bcm43xx_initval05.fw    bcm43xx_microcode2.fw
b43                   bcm43xx_initval06.fw    bcm43xx_microcode4.fw
b43legacy             bcm43xx_initval07.fw    bcm43xx_microcode5.fw
bcm43xx_initval01.fw  bcm43xx_initval08.fw    bcm43xx_pcm4.fw
bcm43xx_initval02.fw  bcm43xx_initval09.fw    bcm43xx_pcm5.fw
bcm43xx_initval03.fw  bcm43xx_initval10.fw    bcmwl5.sys
bcm43xx_initval04.fw  bcm43xx_microcode11.fw
```

```
brandon@ubuntu-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
PCI (sysfs)  

  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 02
       serial: 00:0f:1f:2a:d3:f5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:7d:0b:5b:96
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

EDIT: Just want to point out that I've just gone through this, with my correct card Rev 3: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I also attempted the Hardy Bug Fix and after each I show: module=ssb for my Wireless network. I just rebooted the computer and I'm still showing module ssb.

I do have a Windows Wireless Devices window, that does show bcmwl5 Hardware Present Yes.

EDIT After doing the above steps, I no longer have Wireless showing up in my network tool. It only shows Wired connection. When I go to manual configuration it only shows the hard wired connection now. 

Thank you again for the help in advance! I'm pretty much done with this from my end. I've tried so many things over the past few days that I am going to wait for suggestions or responses before trying anything else, so I will be pretty much where I am now for any future troubleshooting.

---

### Post by pytheas22 on 2008-10-13
You have the same card as mine, so it should definitely work using the bcm43xx driver.  However for some reason it appears that the b43 driver is refusing to give up control of things.  If you run these commands, though, they should force b43 to unload:

```
sudo modprobe -r b43 b44 b43legacy ssb bcm43xx ndiswrapper
sudo modprobe bcm43xx

```
They will also break your ethernet, as you already discovered :)  The reason is complicated, but basically there's an issue where Broadcom-based ethernet cards (like yours) stop working when the b43 module gets unloaded, as a result of dependency issues.  We can sort through this later to get a better solution, but for the time being, to make the ethernet work again, you can either reboot your computer, or run the commands:
```

sudo modprobe b44
sudo modprobe ssb
```

So I think that the best thing for you to do at this point is run the following set of commands (in the order below) and post all of their output (if you can't get your laptop online at all since you're at work, you can save the output to a text file and transfer it to another machine using a USB drive).  These commands should make your wireless work, or if not should help us to diagnose whatever is wrong:

```
sudo modprobe -r b43 b44 b43legacy ssb bcm43xx ndiswrapper
sudo modprobe bcm43xx
lsmod | grep -e bcm -e ssb
sudo iwlist scan
dmesg | grep -e bcm -e eth1
```

That should help us to nail down the problem.

---

### Post by Brandon81 on 2008-10-13
```
brandon@ubuntu-laptop:~$ lsmod | grep -e bcm -e ssb
bcm43xx               127720  0 
ieee80211softmac       30976  1 bcm43xx
ieee80211              35528  2 bcm43xx,ieee80211softmac
```

```
brandon@ubuntu-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.
eth1      No scan results
```

```
brandon@ubuntu-laptop:~$ dmesg | grep -e bcm -e eth1
[   63.016249] bcm43xx driver
[ 1003.011398] bcm43xx driver
[ 1002.990460] udev: renamed network interface eth0 to eth1
[ 1003.556106] bcm43xx: Radio disabled by hardware
[ 1003.750127] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

Here is the results after performing the commands you requested. 

I can't thank you enough for helping me out here. I'm normally very resourceful in fixing problems but this has got me to my wits end. I just double checked and verified that two devices right next to me are both connected to a strong wireless linksys non security enabled network and I still can't see any networks.

EDIT: I'll let you tell me, but to me the Radio disabled by hardware is definitely interesting. I do NOT have a physical wireless on/off switch on the laptop, just throwing that out there.

---

### Post by pytheas22 on 2008-10-13
hmmm, that's strange.  Everything else seems to be working now--b43 has been replaced by bcm43xx, which is what we want--but it's very strange that it thinks the radio is disabled in hardware and you have no switch (but I believe you about having no switch; my laptop with this card doesn't have one either).

It's possible that the wireless radio is disabled by BIOS; please take a look there to see if there are any options regarding the wireless card.  Windows may also have done something to it; if you go to Hardware Manager in Windows and view the details for your wireless card, there may be different options regarding power-saving mode or something (or there may be nothing of interest at all).  Switch them to the options that make the card stay on as much as possible (i.e. disable power-saving mode or whatever).  Finally, it might help to unplug the laptop and remove the battery for a minute, then turn it back on and boot to Ubuntu--this should cause the wireless card to forget any weird settings that may have been imposed on it and switch back to the defaults.

Please let me know if any of the above helps.  I may not be able to respond again till later.

---

### Post by Brandon81 on 2008-10-13
Hmm... I went into BIOS and there's an option to allow the wireless to be modified by either FN+F2, Application only, or off. I changed this setting to see what settings there were and then noticed another setting underneath it which is basically like "Wireless: On" or Off. After I changed the option, it set it to (or was set to) off, so I switched it to on and rebooted. The ndiswrapper continued to do the same thing, killed hardwired ethernet and continued to show no wireless networks, so I reinstalled the one through the Hardware Drivers menu item. (removed the entries from the blacklist file of course as well) 

Seems to not be showing up still on the network manager or under manual configuration. I am working now on trying to get back to the original driver that was provided, because that did work for three days. If I accidentally hit FN+F2 (ALT is right next to it, and ALT+F2 was pressed quite a few times trying to force kill EVE) I'll be so mad at myself :)

---

### Post by pytheas22 on 2008-10-13
That's good that the "radio disabled by hardware message" has an explanation.  Please try doing whatever you did to get the card working originally, making sure the radio is on this time.  You could also try running these commands:
```

sudo modprobe -r bcm43xx b43 b43legacy b44 ssb
sudo modprobe bcm43xx
```

which should make the wireless come up and work, provided the radio is on.

Also, if you run the command:
```

dmesg | tail
```

it will spit out the ten most recent messages from the kernel.  If you toggle the wireless on or off, this should be mentioned in those messages, so you can use that command to check that alt-F2 is really doing something.

---

### Post by Brandon81 on 2008-10-13
Suddenly I can see wireless networks!!!!! (Sorry, excited... been working on this for days)

I think that was it!! I had some trouble actually connecting to it now, so I'm rebooting and changing that setting to application only so this doesn't happen again and making sure it's correctly on.

I really think this problem is fixed, and I thank you so much for helping me!

---

### Post by Brandon81 on 2008-10-13
Okay, haha, now I rebooted and it's showing in the Hardware Drivers list Not In Use and it's checked. 

I removed everything from Windows Wireless Drivers. 

I also removed the items from the blacklist. 

What can I do to just undo the stuff we did here and go back to the regular wireless through the hardware drivers list?

Thanks again so much, I am SO relieved! Also, this makes perfect sense considering it persisted after the install!

EDIT: Now I just seem to have a problem connecting to the actual network, and I am pretty sure it's something I did over the past 2-3 days of troubleshooting. I am thinking I may just reinstall Ubuntu again, now that everything is going to work correctly, unless you or someone can help me easily. It's not a big deal for me to just wipe it out and reinstall it one more time. I'm getting better at this each time.

---

### Post by Brandon81 on 2008-10-13
Okay last bump... 

Thanks again so much man, I am now connected to the wireless network. The router needed a reset, haha. 

Anything you can suggest to help me get it to boot up that way would be appreciated as I'll have to uncheck and then recheck the wireless adaptor in the hardware drivers page. I've rebooted it twice and it comes up without wireless, and I go into the hardware drivers window and the Broadcom B43 is listed with a check and a red circle and says Not In Use. So I uncheck it and recheck it and it's fine after that. Can you help me get it to boot back up that way? Then I'll be perfect! 

Either way is fine, as I'll just reinstall if I can't get it to work off booting up, I really appreciate this a ton and it's a giant weight off my chest now. You've been a big help and I love ubuntu!

---

### Post by pytheas22 on 2008-10-13
Glad to hear it's finally straightened out...I remember from my early days how frustrating it can be working on problems like this for days on end without understanding enough about Linux to really know what was going on.

I'm sure we can figure out a way to make the wireless work automatically after a reboot without too much work.  But because I'm not certain exactly which settings are doing the trick to make it work, please reboot your computer, do whatever you need to get online via wireless, then post the output of these commands so I'll know which driver it's using, etc.:
```

lshw -C Network
iwconfig
lsmod | grep -e bcm -e b43 -e ndis
ls -al /etc/init.d/bcm43xxfix.sh
cat /etc/init.d/bcm43xxfix.sh
```

Probably we will just need to change that boot script that you wrote to get things going.

---

### Post by Brandon81 on 2008-10-13
This is much easier now! Haha. 

Here they are... This is after rebooting, and then unchecking and rechecking the wireless in the hardware drivers window.

```
brandon@ubuntu-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 02
       serial: 00:0f:1f:2a:d3:f5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:7d:0b:5b:96
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.104 multicast=yes wireless=IEEE 802.11g
```

```
brandon@ubuntu-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:49:E4:56   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=78/100  Signal level=-53 dBm  Noise level=-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
brandon@ubuntu-laptop:~$ lsmod | grep -e bcm -e b43 -e ndis
b43                   144420  0 
bcm43xx               127720  0 
ieee80211softmac       30976  1 bcm43xx
ieee80211              35528  2 bcm43xx,ieee80211softmac
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ndiswrapper           193500  0 
ssb                    34308  2 b43,b44
usbcore               146028  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

```

```
brandon@ubuntu-laptop:~$ ls -al /etc/init.d/bcm43xxfix.sh
-rwxrwxr-x 1 root root 79 2008-10-13 08:31 /etc/init.d/bcm43xxfix.sh

```

```
brandon@ubuntu-laptop:~$ cat /etc/init.d/bcm43xxfix.sh
#! /bin/sh

rmmod b43legacy
rmmod b43
rmmod bcm43xx
rmmod ssb
modprobe bcm43xx
brandon@ubuntu-laptop:~$ 

```

Thank you :)

---

### Post by pytheas22 on 2008-10-13
Try opening up that script you wrote by typing:
```

sudo gedit /etc/init.d/bcm43xxfix.sh
```

and comment everything out so that it looks like this:
```

#! /bin/sh

#rmmod b43legacy
#rmmod b43
#rmmod bcm43xx
#rmmod ssb
#modprobe bcm43xx
```

(the # tells the computer to ignore that line).  Then save and close the file, and reboot.  Does your wireless work now automatically?  I think that the script was the problem because it's unloading the b43 module, which (contrary to what I wrote yesterday) appears to be able to drive your card successfully.

---

### Post by Brandon81 on 2008-10-13
I will try that later and let you know what happens. I have to go in for a training class at work and broke down my laptop already. 

With the risk of being very redundant, thank you so much again for all the help. :D

---

### Post by Brandon81 on 2008-10-13
Worked perfectly, thank you! :guitar:

---

