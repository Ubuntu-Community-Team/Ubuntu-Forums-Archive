---
title: "rt61 and Ubuntu Feisty Fawn, 7.04, WPA-PSK problems solved"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by lukaszJarochowski on 2007-04-20
Hi! everyone!

Just yesterday I've upgraded to FF, and of course had problems with my Wireless card. In Edgy I had rt61 driver compiled from source RT61_Linux_STA_Drv1.1.0.0.

In kernel 2.6.20 the package wouldn't compile, and Ubuntu shipped rt61 driver is not working properly.

I tried different howtos on this forum, but none has worked for me to enable WPA, so i did this:

in file:
/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c

comment out line 197, it should look like this:

#if WIRELESS_EXT >= 12
//  net_dev->get_wireless_stats = RT61_get_wireless_stats;
    net_dev->wireless_handlers = (struct iw_handler_def *) &rt61_iw_handler_def;
#endif

then run:
make

and driver is ready tu use

I copied mine to:
sudo cp rt61.ko /lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko

and run:
sudo modprobe -r rt61
sudo modprobe rt61

then:
sudo ifdown ra0
sudo ifup ra0

and that's it!

It works - and the best proof is that i'm writing this post!

Sorry for my english
Cheers!

---

### Post by dercaS on 2007-04-20
This seems great. Gonna run downstairs and try it on my other comp in a bit.
Do i still have to copy the .bin files and edit that rt61sta.dat file to use WPA-PSK?

---

### Post by jhpope on 2007-04-20
do i need to download the source? sorry i'm a n00b

---

### Post by lukaszJarochowski on 2007-04-21
First You must follow this tutorial:
[http://ubuntuforums.org/showthread.php?t=132980]("http://ubuntuforums.org/showthread.php?t=132980")

on step **(b)** download latest ralink drivers - version 1.1.0.0

step **(c)** will look like this:

Untar and follow the instructions in the included readme file. Basic steps would be:

```
$ sudo cp Makefile.6 Makefile
$ sudo vim rtmp_main.c
```

go to line 197, and change it from:
```
net_dev->get_wireless_stats = RT61_get_wireless_stats;
```
to:
```
// net_dev->get_wireless_stats = RT61_get_wireless_stats;
```

then:

```
$ sudo make all
$ sudo mkdir /etc/Wireless/RT61STA/
$ sudo cp *.bin /etc/Wireless/RT61STA/
$ sudo cp rt61sta.dat /etc/Wireless/RT61STA/
```

If you had rt61 driver installed by this method in Edgy, then you can stop here, otherwise you need to follow normal steps from howto i've mentioned

Hope that helps

Cheers!

---

### Post by Ynem on 2007-04-21
Hi,

I've installed 7.04 on my thinkpad x21. In previous versions I couldn't install the card (I read pages of instructions using ndsiwrapper, madwifi, or using the.tar.gz package, but none of them worked).

In this version however, the card worked immediately! It was recognised en after filling in the 64bit HEX WEP code in the manual configuration I could surf the internet.
But after 6 minutes it crashes. I looked in the sytem logbook and got these lines just before every crash:

Apr 21 12:44:23 LaptopYen2 kernel: [   89.868000] ondemand governor failed to load due to too long transition latency
Apr 21 12:44:27 LaptopYen2 gconfd (yen-4930): Resolved address "xml:readwrite:/home/yen/.gconf" to a writable configuration source at position 0
Apr 21 12:44:29 LaptopYen2 NetworkManager: <information>^IUpdating allowed wireless network lists. 
Apr 21 12:44:29 LaptopYen2 NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

Y

---

### Post by sblanzio on 2007-04-21
this way it worked perfectly! tnx!

---

### Post by Sterkarm on 2007-04-22
the place to downlaod the whole thiong from dosent wrk


[http://www.ralinktech.com/drivers/Li...1.0.3.0.tar.gz](http://www.ralinktech.com/drivers/Li...1.0.3.0.tar.gz)  <--- come up wi errors ?

---

### Post by sblanzio on 2007-04-23
> **Sterkarm said:**
> the place to downlaod the whole thiong from dosent wrk


[http://www.ralinktech.com/drivers/Li...1.0.3.0.tar.gz](http://www.ralinktech.com/drivers/Li...1.0.3.0.tar.gz)  <--- come up wi errors ?

the correct link now is:
[http://www.ralinktech.com.tw/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz](http://www.ralinktech.com.tw/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz)

---

### Post by sblanzio on 2007-04-23
In a previous reply i said my wifi now works perfectly.
This is true, under a point of view, but I still have a problem:

When I start feisty from boot, the wifi card works, but all internet programs which start on logon (gaim, feed reader) think being offline. So they doesn't connect.

I think this happens because my network icon in systray shows "Not connected" even if I am perfectly online.

Is there a way to fix this problem?

thank you very much!
sblanzio

EDIT: I found some hints here: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/82335](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/82335)

---

### Post by Guranic on 2007-04-23
I have Compaq evo n1020v laptop and A-link rt61 wireless card and I installed Feisty from beta about a week ago. After installation I couldn't get wlan to connect. So I followed [http://ubuntuforums.org/showthread.php?t=392415&highlight=rt61+feisty](http://ubuntuforums.org/showthread.php?t=392415&highlight=rt61+feisty) thread and I disabled network-manager away. Without networkmanager I got wlan to connect by manually configuring network (I'm using wep encryption). After that I was able to get all updates from repos and I noticed there was update for network-manager too. So, after update I enabled network-manager back and wlan works still, but only with manual settings (no roaming mode or dhcp). Now I'm only waiting for update to get roaming mode working 'cause it would be nice to have as long as I'm moving my laptop around several networks... Hope you get something out of my story..

---

### Post by jhpope on 2007-04-23
this fix didn't work for me

---

### Post by whitie on 2007-04-24
Hi there,

Thanks for the great help to get this working under Feisty! I thought my RT61 days were all numbered.

I just have one question thought. I noticed when I ifconfig, I am getting a whole bunch of errors in my wireless card:

ra0     Link encap:Ethernet  HWaddr 00:0:00:00:00:00
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:00ff:fe9c:5f6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:834513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:794792 errors:0 dropped:0 overruns:0 carrier:0
          [COLOR="Red"]collisions:7419[/COLOR] txqueuelen:1000
          RX bytes:460585758 (439.2 MiB)  TX bytes:405717124 (386.9 MiB)
          Interrupt:10

I cant remember if I would get them on edgy as I dont think I ever checked. If anyone could help me out and let me know if this is normal behaviour or not that would be great.
:)

---

### Post by whayong on 2007-04-24
I need some help following the OP's how to.  I don't know where to begin to look for the said file and what commands to use.  Some help please?

---

### Post by mezcal on 2007-04-24
Your fix for compiling the driver worked for me. Thanks and impressive that you figured that out!
The driver itself however doesn't work for me.
I also have now found that the recent nightly builds from serial monkey compile without issues.
They don't work either, unfortunately.

On boot, iwconfig yeilds ra0 no wireless interfaces detected.
If I then do sudo dhclient ra0 I can then do iwlist scan and I see a list of neighborhood networks including mine.
I can't seem to connect though.
I have removed network manager and configured the rt61sta.dat file. The driver seems to be completely ignoring the configuration file and after 3 reinstalls and a dozen or so hours of troubleshooting I fear I'm going to have to give up on Feisty.
Weird it seems to work for some but not others.
I'm pretty much a nix noob but I have gotten dapper going on this same hardware after some struggling.
I dunno.

---

### Post by mezcal on 2007-04-24
Oh, I forgot to mention that I had originally tried downgrading my wireless security to wep just to get it going (network manager was still installed and could 'see' the network at that time, stock feisty driver.) 
Entering the wep key and clicking on connect resulted in immediate and complete lockup of the machine, forcing a hard reboot.

---

### Post by amniarix on 2007-04-25
> **lukaszJarochowski said:**
> 
In kernel 2.6.20 the package wouldn't compile, and Ubuntu shipped rt61 driver is not working properly.

In my experience, the shipped rt61 driver does work if configured with 'iwpriv'. I wrote up a [HOWTO: RT61 on Feisty Fawn with WPA]("http://ubuntuforums.org/showthread.php?t=419709") documenting how to do this.

---

### Post by Guranic on 2007-04-25
As I told before, I have original Feisty driver working almost out of the box. Gnome device manager shows info about my card (A-link pcmcia card) RT2561/RT61 rev B 802.11g Maybe different revisions have something to do with the fact that some chips are working and other not...

---

### Post by mezcal on 2007-04-25
> **amniarix said:**
> In my experience, the shipped rt61 driver does work if configured with 'iwpriv'. I wrote up a [HOWTO: RT61 on Feisty Fawn with WPA]("http://ubuntuforums.org/showthread.php?t=419709") documenting how to do this.

I'll go check that out. I did yet another complete format and reinstall with the mobo's onboard lan disabled in bios but still no love. My card shows up as ra1 instead of ra0. Gotta be a conflict somewhere.

---

### Post by dahen on 2007-05-03
Thank you. This worked well for me.
The solution with iwpriv and included driver from serialmonkey also worked, but required several ifdown ifup each boot to work and I didn't like that. With the RT-drivers I have not had this problem. :)

---

### Post by codeslicer on 2007-05-03
Help! About a week ago, I decided to try out Ubuntu Edgy 6.10. Unfortunately, I have an rt61 ralink turbo card, and the network didn't work. I compiled the source code millions of times, and tried everything I could on the web. I re-installed Edgy anout 4 times. So I decided to download and burn Ubuntu Dapper 6.06. Although it recognized my card, and the network still didn't work even when I enabled it in network manager, it detected a connection. Unfortunately though, at boot when Ubuntu configures the network interfaces, my system freezes. Not good. And when I try to access the ext3 partition from Windows (I have the drivers. Just google ext3 for windows), it says the drive is not formated. Strange, it worked with Edgy before. . .

So now, should I try and get Feisty and see how it goes, or just drop Ubuntu and stay with Windows? Any help would be helpful. Thanks in advance :)

---

### Post by gatoruss on 2007-05-23
Ok....I am freaking lost.  Sorry for the rant, but this wifi thing has me crazy...:(

I have downloaded the .tar file.

I have untarred it in my wpa_supplicant dir (already had one as I was trying to follow general instructions for setting up wpa, which had worked before I upgrades to 7.04).

Followed instructions in "readme" until I got to "make."  Neither the instructiuons in the "readme" nor your work 

When I run "sudo Makefile.6 Makefile" I get

> sudo: Makefile.6: command not found

I tried "make" and "make all" and I get

> make: *** No rule to make target `config.o', needed by `wpa_supplicant'.  Stop.

This is as far as I can get.....

---

### Post by gatoruss on 2007-05-24
OK....I figured out the above.  Now I have made it to step (d);

> (d) Edit the /etc/Wireless/RT61STA/rt61sta.dat as a binary file. The recommended way of doing this is:

Code:
$ cd /etc/Wireless/RT61STA
$ sudo vi -b rt61sta.datEnter the necessary information to access your network. Refer to the readme file for options.


How do I know what to edite into these fields, and more importnatly how do I actually edit the fields?

---

### Post by sdrambo on 2007-05-30
Thank you finally I get my D-Link DWL-G510 Rev. c card working under Linux. Tried Mandriva and Suse with no  luck,  Regards Ian

---

### Post by gatoruss on 2007-06-01
Ok, I have gotten the wifi to work following the tutorial mentioned above...thing is I cannot get it to fire up on start up...I need to manually launch every time I boot up?"

I tried to set up a start up script in the manner described in item (g) of the following link: [http://ubuntuforums.org/showthread.php?t=132980;](http://ubuntuforums.org/showthread.php?t=132980;) as modified per the Additional Notes, item "(c) "No DHCPOFFERS Received." But it does not fire up wifi on start up....any suggestions?

---

### Post by Andrew MacDonald on 2007-06-01
Rather than modifying the source you could download the latest rt61 CVS tarball from 
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

---

### Post by brodiepearce on 2007-06-08
I got mine working finally, using both this guide and the one that this is based one.  :D

---

### Post by bigdave146 on 2007-07-17
I am having a nightmare with this.

I have got a clean install of Feisty and have an RT61 card that was functioning perfectly this morning with Edgy (and the drivers downloaded from Realteks website, installed as per the info in the Wiki).  I had full access to my WLAN, and no problems with connection.  I am using WEP 64 bit (yes i know its not the best)

Now, when i look at the networking straight after the clean install of Feisty, ifconfig shows ra1 on there.  I have done the following....

sudo iiwlist ra1 scan - and my wireless network is shown - however link quality is 0/100
sudo ifconfig ra1 down - OK
sudo iwconfig ra1 essid WLAN_NAME - OK
sudo iwpriv ra1 set AuthMode=SHARED = OK
sudo iwpriv ra1 set EncrypType=WEP - PROBLEM

As soon as i type this line or "sudo iwpriv ra1 set Key1=12345678" Ubuntu hangs.

Am i doing something wrong, as this worked fine on Edgy with the Realtek drivers.  I dont want to have to reinstall that !!  Lots of other people seem to have got this working on Feisty so it cant be too hard.  I dont want to have to go to Vista........

Dave

---

### Post by huygens on 2007-07-23
> **bigdave146 said:**
> As soon as i type this line or "sudo iwpriv ra1 set Key1=12345678" Ubuntu hangs.
I also have the same problem :(
Worse is that if I use the wire cable, from time to time Ubuntu hang completly, and I suspect that this is because of the rt61 module (though I haven't been able to confirm that). I suspect that some operations occurs from time to time with this card (and its driver) and it crashes Ubuntu.

When I mean crash/hang I really mean that Ubuntu is just frozen: mouse does not move, keyboard has no effect, nothing is refreshed on screen, it does not answer to ping commend anymore, etc. the only input it understands is hard reset!!

---

### Post by bigdave146 on 2007-07-23
I have configured it with WPA and it works great.  Must be something to do with rt61 and WEP.

Dave

---

