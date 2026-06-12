---
title: "[SOLVED] Wireless Broadcom B43 in 8.04"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by f37u5g0d on 2008-04-26
I updated from 7.10 to 8.04 and my wireless no longer works.  I just went through the entire wireless set up process.  I completely removed ndisgtk and restarted.  I reinstalled ndisgtk, found new copies of the *.inf and *.sys file from my xp install.  I installed them in windows wireless drivers utility, enabled the restricted drivers and the wireless networks show up but I can't connect to them.  (Neither of the little lights turn green).  Any ideas?  How come I can find the networks and they have valid signal strengths but I can't connect to them?

---

### Post by Tim Sharitt on 2008-04-26
Several people seem to have trouble getting ndiswrapper working in hardy (myself included). Have you tried using the B43 driver with b43-fwcutter?
```
sudo apt-get install b43-fwcutter
```
Enable Broadcom 43 wireless driver in System > Administration > Hardware Drivers.

I just noticed where you said you enabled the restricted driver, if your going to use ndiswrapper you need to disable the driver and may need to blacklist it in /etc/modprobe.d/blacklist.
```
sudo gedit /etc/modprobe.d/blacklist
```
Add "blacklist b43" without the quotes.

---

### Post by sbrbot on 2008-04-26
Broadcom wireless cards work without ndiswrapper in new Ubuntu 8.04 distribution. You just have to extract Broadcom firmware into /lib/firmware directory and leave b43 driver to use it.

---

### Post by kai60 on 2008-04-26
You could try doing this and then see how you go...

[http://ubuntuforums.org/showthread.php?p=4798063#post4798063](http://ubuntuforums.org/showthread.php?p=4798063#post4798063)

---

### Post by f37u5g0d on 2008-04-26
I tried the instructions at the link in the previous post but it didn't work for me.  (I am using bcm4306 for anybody out there searching for the same answer).

---

### Post by kai60 on 2008-04-26
I am using the same chipset that you are using, and I had similar problems to what you are having. Did you do a fresh install? If not, did you blacklist the bcm43xx fw?

You could try that. Also, did you get any Error messages when you rebooted, especially in regards to your network manager? Something such as missing b43/ucode4.fw would be good.

---

### Post by f37u5g0d on 2008-04-26
I did not fresh install.  I upgraded from 7.10.  I have not tried blacklisting but I am going to now.  I did not notice any error messages regarding that but I also wasn't looking for any.  Right now the networks show up and they have valid signal strength but when I try to connect the lights never light up.  I'll post again and tell you how it went.

---

### Post by kai60 on 2008-04-26
If the networks are showing up in nm-applet, then the odds are that your firmware is properly installed, which means that maybe your network settings are wrong. 

If you use the nm-applet in the top right of your screen, then click on it, it should show you up an option to connect using security. You could try and disable security on your AP for a while and see if you can connect that way. That should indicate whether you have connection and then we can work on the security aspect.

---

### Post by f37u5g0d on 2008-04-26
That's just it.  I'm connecting to an open network.  No security at all!

---

### Post by f37u5g0d on 2008-04-26
I just blacklisted and now I have no wireless at all so that doesn't work.  I put things back.  So now I am used fwcutter to get the firmware and I am using the b43 driver.  Like I said before I can't connect to the networks but I can see them and they have valid strength.  I know all the hardware works because I can connect in windows.

---

### Post by kai60 on 2008-04-26
Can you do me a favour and grab a screenshot of what you are doing to connect to the network? And also show me the output from
```

$iwconfig

$ls /lib/firmware/2.6.25-16-*

```

Cheers

---

### Post by f37u5g0d on 2008-04-26
As you can see from the screen shot all I am doing is clicking the nm-applet and clicking on mcPublic (my network).  It tries to connect and fails.  But like I said it has a valid signal strength and it works under windows.  Sorry if I wasn't being clear before lol. o and here is the output from those commands

$iwconfig
```
lo        no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

eth0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0B:86:94:93:60   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

and $ls /lib/firmware/2.6.2**4**-16-* (I am using 2.6.24)
```
acx                                 dvb-usb-vp702x-01.fw
aic94xx-seq.fw                      dvb-usb-vp7045-01.fw
atmel_at76c502_3com.bin             dvb-usb-wt220u-02.fw
atmel_at76c502_3com-wpa.bin         dvb-usb-wt220u-fc03.fw
atmel_at76c502.bin                  dvb-usb-wt220u-zl0353-01.fw
atmel_at76c502d.bin                 ipw2100-1.3.fw
atmel_at76c502d-wpa.bin             ipw2100-1.3-i.fw
atmel_at76c502e.bin                 ipw2100-1.3-p.fw
atmel_at76c502e-wpa.bin             ipw2200-bss.fw
atmel_at76c502-wpa.bin              ipw2200-ibss.fw
atmel_at76c503-i3861.bin            ipw2200-sniffer.fw
atmel_at76c503-i3863.bin            isl3877
atmel_at76c503-rfmd-0.90.2-140.bin  isl3886
atmel_at76c503-rfmd-acc.bin         isl3887usb_bare
atmel_at76c503-rfmd.bin             isl3890
atmel_at76c504_2958-wpa.bin         isl3890usb
atmel_at76c504a_2958-wpa.bin        iwlwifi-3945-1.ucode
atmel_at76c504.bin                  iwlwifi-3945.ucode
atmel_at76c504c-wpa.bin             iwlwifi-4965-1.ucode
atmel_at76c505a-rfmd2958.bin        iwlwifi-4965.ucode
atmel_at76c505-rfmd2958.bin         ql2100_fw.bin
atmel_at76c505-rfmd.bin             ql2200_fw.bin
atmel_at76c506.bin                  ql2300_fw.bin
atmel_at76c506-wpa.bin              ql2322_fw.bin
b43                                 ql2400_fw.bin
dvb-fe-or51132-qam.fw               rt2561.bin
dvb-fe-or51132-vsb.fw               rt2561s.bin
dvb-fe-or51211.fw                   rt2661.bin
dvb-fe-tda10046.fw                  rt73.bin
dvb-ttpci-01.fw                     v4l-cx2341x-dec.fw
dvb-usb-avertv-a800-02.fw           v4l-cx2341x-enc.fw
dvb-usb-bluebird-01.fw              v4l-cx2341x-init.mpg
dvb-usb-dib0700-1.10.fw             v4l-cx25840.fw
dvb-usb-dibusb-5.0.0.11.fw          v4l-pvrusb2-24xxx-01.fw
dvb-usb-dibusb-6.0.0.8.fw           v4l-pvrusb2-29xxx-01.fw
dvb-usb-dtt200u-01.fw               zd1201-ap.fw
dvb-usb-tvwalkert.fw                zd1201.fw
dvb-usb-umt-010-02.fw               zd1211

```

Thanks for all of your help!

---

### Post by kai60 on 2008-04-26
My suggestion here is to go into SYSTEM > ADMINISTRATION > NETWORK and check that you have roaming mode enabled on all of your wired and wireless connections. Also you may want to try and connect to mcLibrary if you have access to that. It appears to me that your AP is configured, as in it is trying to access a particular AP, but can't for some reason, so another option is to manually delete the AP MAC address out of your iwconfig.

Your card should be set up correctly...

Good luck and let me know...

---

### Post by searland on 2008-04-26
I have exactly the same problem. b43/ was correctly extracted to /lib/firmware/2.6.24-16-generic/ and Ubuntu recognized the driver. Wireless network card works (light on). I can find APs with signal strength, but can't connect to them, no matter whether they are encrypted.

But the bcm43xx firmwares in /lib/firmware/2.6.22-14-generic works fine when I use 2.6.22 kernel.

(I blacklisted bcm43xx when I test wireless in 2.6.24.)

---

### Post by f37u5g0d on 2008-04-26
I don't know why it isn't connecting.  I think I am going to give up for tonight.  Although I did notice one peculiar thing.  If I restart the computer I have to go into system > admin > hardware drivers and re-enable the driver but the really strange thing is that when I open hardware drivers the box is checked but the button is red and it says "not in use" if I un-check the box it disables the driver.  Then I can "enable" it (by re-checking the box again).  Obviously something is screwy here.  IDK if this has anything to do with my problem but yeah I'm gonna give it a rest for tonight.  (It's 10:35 here).  Thank you for all your help Kai!

---

### Post by Ayuthia on 2008-04-26
If you still want to try ndiswrapper, you might try blacklisting b43 and ssb.  Those are the new modules for the Broadcom cards.  You might check lsmod to see if they are still there and possibly check for b43legacy (the module that is supposed to be used for some 4306 cards).  I have not seen too many successful 4306 owners in Hardy with the Broadcom module.  There is a fix for them in the 2.6.25 kernel, but I am not for sure about what is to be done with the 2.6.24.x kernels.

---

### Post by f37u5g0d on 2008-04-27
Umm.  This may sound stupid but why don't I just upgrade to the 2.6.25 kernel?  Is it out?

---

### Post by dnr101 on 2008-04-27
Don't know if this helps anyone, but I just upgraded from 7.10 to 8.04. Was using ndiswrapper for my bcm4318 chip card, 8.04 broke that. I pluged an e-net cable in and ran the Hardware Drivers app (formerly restricted drivers...) and It had me connected using b43 in ~3 mins, with wpa2. Great work to the b43 team and those who automated it's use, that was easy!
-D

---

### Post by f37u5g0d on 2008-04-29
Apparently this is a bug and nobody will be able to get wireless to work on broadcom 4306 until some code is changed.  I found the bug on launchpad the other day and if they come out with some sort of patch I will list it here or you can subscribe to the bug yourself.  Here is the link

[https://bugs.launchpad.net/bugs/138400](https://bugs.launchpad.net/bugs/138400)

---

### Post by Ayuthia on 2008-04-29
> **f37u5g0d said:**
> Umm.  This may sound stupid but why don't I just upgrade to the 2.6.25 kernel?  Is it out?
It is not available in the Ubuntu repositories, but it is out at [http://kernel.org](http://kernel.org).  I am not for sure about how much Linux experience you have, but it will not be too easy if this is your first time at compiling a kernel.  If you are using a proprietary graphics driver like Nvidia you will also have to compile the driver for this kernel.

---

### Post by Ayuthia on 2008-04-29
> **f37u5g0d said:**
> Apparently this is a bug and nobody will be able to get wireless to work on broadcom 4306 until some code is changed.  I found the bug on launchpad the other day and if they come out with some sort of patch I will list it here or you can subscribe to the bug yourself.  Here is the link

[https://bugs.launchpad.net/bugs/138400](https://bugs.launchpad.net/bugs/138400)You might even try to see if you can still use the bcm43xx driver with this kernel.  You will need to remove the blacklist for the bcm43xx driver (in /etc/modprobe.d/blacklist) and you will have to blacklist the b43 and possibly the ssb drivers.  

Another option is to try the NDISwrapper option.  If you already have NDISwrapper installed you will need to do the following:
```
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe ndiswrapper
```
If it works, then there are some additional steps that will need to be done to allow you to keep it working after each boot.

---

### Post by desktopj on 2008-05-01
Had a number of problems with BMC4306, B43 and 8.04
Following the instructions for B43 and wl_asta.o I would sometimes connect, other times not. After messing with the gnome network manager - eventually I'd get an Gnome Settings Daemon error and would  lose my ethernet device listing in /etc/network/interfaces and be unable to log in. At that point I'd just reinstall and try again.

Finally, after reinstalling 4 times, I installed Kubuntu instead. Did the install for B43-fwcutter, and wl_asta.o. Set my wireless network ID, activated the wireless on the menu bar and viola!! I was connected and picked up an ip address in seconds. I've rebooted multiple times, and my wireless comes on and connects every time. 

The difference between the functionality of the KDE and the Gnome network tools was like night and day for me.

---

### Post by f37u5g0d on 2008-05-07
So this morning I was toying around looking at the add/remove applications list from the applications menu and I found "Windows Wireless Drivers" with "NDiswrapper driver installation tool" as the description.  I realized that I wasn't sure if I had ever truely proved ndiswrapper to not work so I though what the hell.  I checked the box, applied my changed, restarted and now WIRELESS WORKS AGAIN!!! :D

---

### Post by waterspider on 2008-05-18
i have the same problem too, after the upgrade i cant find my wireless card below is the output of lshw-c

 lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:11:2f:14:18:18
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=10.1.1.210 latency=32 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32
 i will appreciate any help

---

### Post by f37u5g0d on 2008-05-18
"network: 1 unclaimed" is your wireless card.  You can tell because of the "product" line.  I got my 4306 card working using ndiswrapper.  Below is a link to the instructions I used.  I don't know if it will work for your 4303 card but it wouldn't surprise me if it did.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by elicoten on 2008-05-19
I found that blacklisting the b43 driver, and ssb doesn't work. The way I do it, which is a bit clumsy but is the easiest configuration-wise is have the b43 driver load up at boot, then use modprobe to remove b43 & ssb and load bcm43xx. (may need to reinstall bcm43xx and bcm43xx-fwcutter before this works).

I have a Linksys Wireless PCI card with the BCM4306 chipset

Hope this helps someone.

---

### Post by Ayuthia on 2008-05-19
> **waterspider said:**
> i have the same problem too, after the upgrade i cant find my wireless card below is the output of lshw-c

 lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:11:2f:14:18:18
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=10.1.1.210 latency=32 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32
 i will appreciate any help

Before you go the ndiswrapper route, I would like to know how you were able to get your wireless to work in Gutsy.  If it was using the restricted drivers, we can get it up and running again.  We can also try the new drivers that replace the old.  If it is ndiswrapper, we might have to make some modifications to get it back up and running.

---

