---
title: "broadcom wireless problem"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by nivesh on 2008-04-26
hi,

i just finished installing hardy. it installed without any errors and is booting up in 36seconds ! including the default 10sec grub timeout. sweet !

this is a hpdv9000, hibernate, audio, compiz all works excellent !

I only have the problem with my broadcom wireless. It doesn't show up in my hardware drivers, but the hardware testing detects it just fine. 


lshw -C network
 sudo lshw -C network
[sudo] password for nivesh: 
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb


any help would be appreciated.

thanks


nivesh

---

### Post by kai60 on 2008-04-26
Hi mate,

I had the same problem and after several hours and nearly going back to 7.10 I was able to figure out how to do it.

First thing to do is to install b43-fwcutter from your 8.04 CD or download it from [http://packages.ubuntu.com/hardy/utils/b43-fwcutter]("http://packages.ubuntu.com/hardy/utils/b43-fwcutter") and just select the one for your architecture. Once you have that, download the tarball from this location: [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2]("http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2"), extract the tarball in your home directory and find the file called wl_apsta.o.

Install b43-fwcutter and just say yes to everything that it wants to do. Open up a terminal and type:
```
sudo b43-fwcutter -w /lib/firmware/2.6.24-16-generic ~/wl_apsta.o
```
where the last part is wherever the wl_apsta.o file is located.
Then type
```
sudo modprobe b43
```

Reboot

Once you are back in, check your wireless networks on the top panel and it should list all the available wireless networks, click on the one that you want to connect to and configure it and hey presto.

Hope that helps.

---

### Post by thepisu on 2008-04-26
I too have problems here with broadcom wireless... Tried your procedure with no luck.

I have an Asus WL-138G v2, it worked perfectly in Ubuntu 7.10... After update to Hardy, I reinstalled it with the "hardware driver" function, tried also using manually the b43-fwcutter.

The strange thing is that, the wireless card is recognized, I see also wireless network, names, signal and encryption type, but I can't join to my wireless network. It tries, but after sometime, gives up. Tried with WPA, WP2, and also with no protection at all..

Any ideas? It's really a problem for me...

I think this is a downside of Ubuntu. It's not good to have always problems with wireless cards, that are so widespread today... For anything else, Ubuntu can really compete in Windows XP / Vista!!

Hardware report:
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by Ash96 on 2008-04-26
Thank you very much Kai60, I was getting very frustrated, but your solution worked great for me!

---

### Post by denarced on 2008-04-26
yeah .. I have the same problem
worked great on ubuntu studio 7.10
and on hardy I get visual effects .. :)
but the wireless .. tried kai60's way
error came ..

root@ubulap:/home/denarced/Desktop/tar/kmod# b43-fwcutter -w /lib/firmware/2.6.24-16-generic wl_apsta.o
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta.o
  version    :  351.126
  MD5        :  9207bc565c2fc9fa1591f6c7911d3fc0
Extracting b43/ucode4.fw
failed to create output directory: No such file or directory

also tried the ndiswrapper .. works like it did 7.10 but Network doesn't
see wireless

---

### Post by kai60 on 2008-04-26
Hi thepisu,

> have an Asus WL-138G v2, it worked perfectly in Ubuntu 7.10... After update to Hardy, I reinstalled it with the "hardware driver" function, tried also using manually the b43-fwcutter.

The strange thing is that, the wireless card is recognized, I see also wireless network, names, signal and encryption type, but I can't join to my wireless network. It tries, but after sometime, gives up. Tried with WPA, WP2, and also with no protection at all..

Can you show me the output of your shell when you run through the commands and I might be able to help...

Cheers

---

### Post by kai60 on 2008-04-26
Hi denarced,

> root@ubulap:/home/denarced/Desktop/tar/kmod# b43-fwcutter -w /lib/firmware/2.6.24-16-generic wl_apsta.o

I am not sure why it says that, but I suggest that you come back to normal user and make sure that you use sudo as that is the way that it worked for me. Sometimes working as root in bash stops things working the way that they should. Don't ask me why that is though.

Good luck with it and let me know how you are going...

---

### Post by TrevP on 2008-04-26
Hi,

I'm having similar problems. I have tried the suggested solution with no luck. The firmware is extracted OK and sudo modprobe b43 appeared to be accepted as a valid command, but when I reboot, I have no connectivity even though my network applet appears to suggest that I am connected.The card worked perfectly under version 7.10. 

Here is the output from lshw -C network:

 *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:12:17:94:4f:24
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Any suggestions would be gratefully received! The wireless network overall is working fine as other devices connect to it with no problem.


Trev

---

### Post by kai60 on 2008-04-26
Hi mate,

make sure that you use the network configuration icon as shown and if that doesn't work, please show me the output from
```
iwconfig
```

Good luck mate...

---

### Post by thepisu on 2008-04-26
> **kai60 said:**
> Hi thepisu,



Can you show me the output of your shell when you run through the commands and I might be able to help...

Cheers

Thanks, here it is the result of the command you posted:

```
stefano@pisulinux:~$ sudo b43-fwcutter -w /lib/firmware/2.6.24-16-generic ~/wl_apsta.o
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta.o
  version    :  351.126
  MD5        :  9207bc565c2fc9fa1591f6c7911d3fc0
Extracting b43/ucode4.fw
Extracting b43/ucode5.fw
Extracting b43/ucode11.fw
Extracting b43/ucode13.fw
Extracting b43/pcm4.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0initvals4.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/lp0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/a0g1bsinitvals13.fw
```

Then, I ran "sudo modprobe b43", no result in shell (it should be ok?).

Also, this is the result of "iwconfig" command:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

In "dmesg" command, I see a lot of these lines:
```
[ 1123.083749] eth1: Initial auth_alg=0
[ 1123.083762] eth1: authenticate with AP 00:1a:2a:a2:82:20
[ 1123.282417] eth1: authenticate with AP 00:1a:2a:a2:82:20
[ 1123.482267] eth1: authenticate with AP 00:1a:2a:a2:82:20
[ 1123.682146] eth1: authentication with AP 00:1a:2a:a2:82:20 timed out

```

Why a timeout problem? It's not possible to return to old bcm43xx drivers, that worked?

---

### Post by kai60 on 2008-04-26
Hi thepisu,

no, you can't use the old bcm43xx drivers any longer, something to do with the kernel, I think.

Your output seems to be okay, just reboot if you haven't already done so and then use the network icon in the toolbar as per the pic on my previous post to configure the network, it should all work fine then.

The iwconfig output indicates that you haven't configured a network as yet and that means that it won't authenticate with any, so this is the easiest way to configure a network in roaming mode, which you can check through SYSTEM > ADMINISTRATION > NETWORK...
Let me know if there is anything else that I can do...

---

### Post by sbrbot on 2008-04-26
> **thepisu said:**
> Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I have exactly the same WLAN card. 

> **kai60 said:**
> Once you are back in, check your wireless networks on the top panel and it should list all the available wireless networks, click on the one that you want to connect to and configure it and hey presto.

My problem is strange in that way that wireless card is working (as you can see) but nm-applet does not work! I just extracted Broadcom firmware using b43-fwcutter and put it into /lib/firmware directory. I succeeded to establish wireless connection to my AP but nm-applet does not show list of available wireless networks around.

```
lshw -C network

  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:5f:d0:39
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:cf:b6:c1:02
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.31 multicast=yes wireless=IEEE 802.11g

```

I have one ethernet and one wireless card in my notebook but according to this output here is "network" and "network:1" for wireless!? It seems to me that "network" works since it received dynamic IP address from AP, and that nm-applet is assigned to "network:1". How's that I have "network" and "network:1". On my other notebook having the same Broadcom card with Fedora 8 there is modprobe.conf file where I define "alias wlan0 b43" to assign wlan0 to b43 driver but how it works here on Uuntu 8.04?

---

### Post by TrevP on 2008-04-26
> **kai60 said:**
> Hi mate,

make sure that you use the network configuration icon as shown and if that doesn't work, please show me the output from
```
iwconfig
```

Good luck mate...

Thanks for the quick response. The output from iwconfig is as follows:

t[I]rev@trev-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/I]

Trev

---

### Post by thepisu on 2008-04-26
> **kai60 said:**
> Hi thepisu,

no, you can't use the old bcm43xx drivers any longer, something to do with the kernel, I think.

Your output seems to be okay, just reboot if you haven't already done so and then use the network icon in the toolbar as per the pic on my previous post to configure the network, it should all work fine then.

The iwconfig output indicates that you haven't configured a network as yet and that means that it won't authenticate with any, so this is the easiest way to configure a network in roaming mode, which you can check through SYSTEM > ADMINISTRATION > NETWORK...
Let me know if there is anything else that I can do...

I was in "roaming mode", autodiscovery, and it worked in 7.10...
However, I tried to manually configure. New this is iwconfig result:
```
stefano@pisulinux:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"AnnaCasa"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1A:2A:A2:82:20   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

But, still doesn not work, and still there are lot of timeout messages in "dmesg"...

(i tried also using ndiswrapper, but without luck..)

---

### Post by kai60 on 2008-04-26
> **TrevP said:**
> Thanks for the quick response. The output from iwconfig is as follows:

t[I]rev@trev-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/I]

Trev

It looks like you are not associated with a wireless network, you can do this through iwconfig if you like, manually, but I would recommend using nm-applet to do it, see my post with the pic and then authenticate. If it doesn't show it, then check your SYSTEM > ADMINISTRATION > NETWORK to make sure that your wireless card is set up to roam.

If you can't do it that way and you can e-mail me your wireless settings and I'll send you back the bash commands to set up the network

Good luck

---

### Post by kai60 on 2008-04-26
Did you set up the IP address manually? If you are using DHCP then you have a network connection, which would be a good thing.

Let me know...

---

### Post by kai60 on 2008-04-26
You don't have a network connection as yet, your output should look similar to the one that is shown below.
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Home"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:90:8C:52   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=69/100  Signal level=-72 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

If you are still having problems, I would suggest that you remove b43-fwcutter and also the file in b43 in /lib/firmware/2.6.24-16-generic and reboot and then start again, as it seems likely that there problems with the installation.

You could also try doing the following in your second attempt, after you have installed the firmware and see if that helps:
```
sudo modprobe -r b43
sudo modprobe b43
```

---

### Post by denarced on 2008-04-26
still no luck in my end .. did notice a couple of things
like this

denarced@ubulap:/lib/firmware$ ls -a
.  ..  2.6.24-16-rt  b43  b43legacy

that's why your suggestion didn't work originally
so I tried it with the 2.6.24-16-rt
no luck

any more tips ?
thanks for all the help so far

---

### Post by npallett on 2008-04-26
If you can't the b43 driver working reliably with your Broadcom card, and you would like to get ndiswrapper working with Ubuntu 8.04, check out the end of my earlier post:

[http://ubuntuforums.org/showthread.php?t=761325](http://ubuntuforums.org/showthread.php?t=761325)

---

### Post by kai60 on 2008-04-26
Hi mate,

what does your restricted driver's manager have to tell us? SYSTEM > ADMINISTRATION > HARDWARE DRIVERS

Are you getting any errors when you reboot in regards to your wireless card? If so, what are they?

---

### Post by denarced on 2008-04-26
npallett
your last post in
[http://ubuntuforums.org/showthread.php?t=761325&page=2](http://ubuntuforums.org/showthread.php?t=761325&page=2)
shows a lot of promise
but I don't understand the first action :

1. Disabled the "restricted Driver" (b43 using b43-fwcutter)

disable how ?
It is my understanding that b43-fwcutter is only a tool for extracting
I am a bit newbie
be patient with me

---

### Post by npallett on 2008-04-27
> **denarced said:**
> npallett
your last post in
[http://ubuntuforums.org/showthread.php?t=761325&page=2](http://ubuntuforums.org/showthread.php?t=761325&page=2)
shows a lot of promise
but I don't understand the first action :

1. Disabled the "restricted Driver" (b43 using b43-fwcutter)

disable how ?
It is my understanding that b43-fwcutter is only a tool for extracting
I am a bit newbie
be patient with me

On the Menu System , choose: System/Administration/"Hardware Drivers"

When the dialog pops up , untick the box for Broadcom B43 Wireless Driver

---

### Post by f37u5g0d on 2008-04-27
This method did not work for me.  ubuntu 8.04 & BCM4306

---

### Post by unMourned on 2008-04-27
> **npallett said:**
> On the Menu System , choose: System/Administration/"Hardware Drivers"

When the dialog pops up , untick the box for Broadcom B43 Wireless Driver

It doesn't work for me, either.  Under "hardware drivers" the only item I have listed is my video card.

-p

---

### Post by denarced on 2008-04-27
okay
now we're getting somewhere
did as instructed by npallett
system -> administration -> network
now there is a wireless connection
but 'iwlist scan'
still comes up with nothing
and yes, there are several networks here

suggestions

thanks for the help so far, npallett

---

### Post by denarced on 2008-04-28
never mind
works great

---

### Post by nivesh on 2008-05-04
kai i tried what you suggested, unfortunately it still didnt work for me, iwconfig ifconfig dont even show my wireless card, needless to say neither does the network manager.

any other ideas ? thanks for your help.

nivesh

> **kai60 said:**
> Hi mate,

I had the same problem and after several hours and nearly going back to 7.10 I was able to figure out how to do it.

First thing to do is to install b43-fwcutter from your 8.04 CD or download it from [http://packages.ubuntu.com/hardy/utils/b43-fwcutter]("http://packages.ubuntu.com/hardy/utils/b43-fwcutter") and just select the one for your architecture. Once you have that, download the tarball from this location: [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2]("http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2"), extract the tarball in your home directory and find the file called wl_apsta.o.

Install b43-fwcutter and just say yes to everything that it wants to do. Open up a terminal and type:
```
sudo b43-fwcutter -w /lib/firmware/2.6.24-16-generic ~/wl_apsta.o
```
where the last part is wherever the wl_apsta.o file is located.
Then type
```
sudo modprobe b43
```

Reboot

Once you are back in, check your wireless networks on the top panel and it should list all the available wireless networks, click on the one that you want to connect to and configure it and hey presto.

Hope that helps.

---

### Post by diony on 2008-05-25
exactly same problem here, on an ASUS 138g v2 wireless card.

i saw that many people gave lots of advices, but none of them were actually worked for us.

let me describe the problem again:

1. we use b43 driver comes with the 2.6.24 kernel
2. we use b43-fwcutter to extract firmwares from wl_apsta.o
3. after that, the wireless card is recognized, and we can see networks around us, the signal strength shows well. but if we try to connect to any one of them, the nm-applet tries lots of times and just fail. the dmesg shows the "timed out" thing again and again with no lucky.
4. our wireless card worked well before, in ubuntu 7.10.
5. iwconfig and ifconfig tells that wlan0 send 0 packets and received nothing.

isn't it so clear that it SHOULD be a bug in the new b43 driver? the card sent nothing means that it had not really try to connect to any network at all, am i right?

we need help.

---

### Post by diony on 2008-05-25
in addition, all the leds on the wireless card never blinks.

---

### Post by Karamiekos on 2008-05-25
> **unMourned said:**
> It doesn't work for me, either.  Under "hardware drivers" the only item I have listed is my video card.

-p

I'm with stuck unMourned here.  The only item I have listed there is my Nvidia graphics.  Also when I do iw config I get the following

dannylee@DannyLee:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

dannylee@DannyLee:~$ 

Thats all i get.  I have a dv6408nr with a BCM94311MCG (rev2) mini pci card.  Any help would be greatly appreciated.

---

### Post by Ayuthia on 2008-05-25
> **diony said:**
> exactly same problem here, on an ASUS 138g v2 wireless card.

i saw that many people gave lots of advices, but none of them were actually worked for us.

let me describe the problem again:

1. we use b43 driver comes with the 2.6.24 kernel
2. we use b43-fwcutter to extract firmwares from wl_apsta.o
3. after that, the wireless card is recognized, and we can see networks around us, the signal strength shows well. but if we try to connect to any one of them, the nm-applet tries lots of times and just fail. the dmesg shows the "timed out" thing again and again with no lucky.
4. our wireless card worked well before, in ubuntu 7.10.
5. iwconfig and ifconfig tells that wlan0 send 0 packets and received nothing.

isn't it so clear that it SHOULD be a bug in the new b43 driver? the card sent nothing means that it had not really try to connect to any network at all, am i right?

we need help.

You could try using bcm43xx-fwcutter.  Just install it and do the following:
```
sudo modprobe -r b43 ssb
sudo depmod -ae 
sudo modprobe bcm43xx
sudo ifconfig wlan0 up
```
That is the driver that was used in prior versions.

Or you might even try Wicd if you haven't yet.

---

### Post by diony on 2008-05-30
> **Ayuthia said:**
> You could try using bcm43xx-fwcutter.  Just install it and do the following:
```
sudo modprobe -r b43 ssb
sudo depmod -ae 
sudo modprobe bcm43xx
sudo ifconfig wlan0 up
```
That is the driver that was used in prior versions.

Or you might even try Wicd if you haven't yet.

:guitar: 
thanks a lot ayuthia! your advice just rocks! my wireless card now works perfect and only i have to do is blacklist the new b43 and ssb driver, and also, use the old firmware.

btw, "sudo ifconfig wlan0 up" not working for me, because when i use bcm43xx as the driver, the wireless card shows as eth0 but not wlan.

---

