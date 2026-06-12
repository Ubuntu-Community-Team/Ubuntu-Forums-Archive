---
title: "Intel PRO/wireless 3945 Network manager problem."
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by Polaroid on 2008-01-21
Hi there,
I've read a lot of threads, and tried a lot of things, but my wireless is still not working.
I have an Intel pro/Wireless 3945 (seems to me that this is the buggiest one) that will not even recognize in the network manager (see attached pic)


My laptop computer is an acer aspire 5600.

The thing that is really strange is that the first day that I installed Gutsy from the live CD  (I've had it for three days now), the wireless was recognized, I entered my network key and everything went absolutely fine. Then I shut down the computer, came back to it 12 or so hours later and it did this. Really annoying. Maybe I've done something wrong?

I'll be grateful for ANY help at all, because this is starting to frustrate me.
Sorry for being a TOTAL noob.
Cheers.

---

### Post by staticvoid on 2008-01-22
Wow, thats really strange... that it worked with the live cd but now it doesn't..
Have you tried using an [Ndiswrapper]("http://ndiswrapper.sourceforge.net/joomla/")?
it may not be neccesary as you had it working before but not anymore... if you just mess with a configuration file... hmm..

hope you get an awnser soon!

sv

---

### Post by Polaroid on 2008-01-23
> **staticvoid said:**
> Wow, thats really strange... that it worked with the live cd but now it doesn't..
Have you tried using an [Ndiswrapper]("http://ndiswrapper.sourceforge.net/joomla/")?
it may not be neccesary as you had it working before but not anymore... if you just mess with a configuration file... hmm..

hope you get an awnser soon!

sv

Thanks staticvoid..
Gutsy comes with a preinstalled ndiswrapper, I thought.. 
Anyway, I reinstalled the 1.48 version with synaptics.. no such luck with the wireless still.
afterwards I tried to install the newest ndiswraper  1.51, and for some weird reason it just wont install through the terminal. (perhaps I'm doing something wrong).
It won't even let me extract it!


antho@antho-laptop:~$ tar zxvf ndiswrapper-version.tar.gz
tar: ndiswrapper-version.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

_______________

antho@antho-laptop:~$ tar zxvf ndiswrapper-1.51.tar.gz
tar: ndiswrapper-1.51.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors



Obviously though, I do have a directory.

This has got me REALLY stumped. >=(

Any help with why my wireless is randomly deciding not to work would be appreciated!

---

### Post by LucaTNT on 2008-01-23
You don't need ndiswrapper, your network card doesn't neeed it, it has a "restricted" driver called ipw3945, you should be able to enable it from the restricted manage.

I have the same card and it worked out-of-the-box, both on LiveCD and in the installed system (Kubuntu for me).

---

### Post by Polaroid on 2008-01-23
> **LucaTNT said:**
> You don't need ndiswrapper, your network card doesn't neeed it, it has a "restricted" driver called ipw3945, you should be able to enable it from the restricted manage.

I have the same card and it worked out-of-the-box, both on LiveCD and in the installed system (Kubuntu for me).


Thanks for the info on the ndiswrapper..
Also,
My restricted driver is already enabled.. 
According to ubuntu, my driver is Enabled AND in use..
Which it is obviously not :(
Thanks for the help anyway

---

### Post by mikewhatever on 2008-01-23
There is a lengthy Wireless Troubleshooting Guide you might find useful. [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wireless%29](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wireless%29)
The card you have has one of the best supports on Linux and the driver is definitely in use (driver=ipw3945). Try following the guide to get the idea of what's wrong, but skip ndisrapper section.

---

### Post by ankuryu on 2008-01-23
Hi, I too have a Intel 3945 Wireless Card.  I too had the same problem.  However I have KUBUNTU.   well here is what I did .......

  edited the file  /etc/network/interfaces  so as to remove everything except the following
 two lines

 auto lo
 iface lo inet loopback

 save it (make sure u have edited using sudo ....) Also make a backup of Original interface file as interface.bak

 Right Clicked on the network manager Icon and select  Options > Show Other Networks

remove all the Trusted Network in the list using "REMOVE"

Exit and reboot.

Soon was shown the Active Networks, selected the appropriate Network and enter the necessary Data and Voila, Computer was connected to my WFH54G Router using WPA2 Encryption.

Also remember when u choose the manual Configuration and save it, You may have to go through the above process again.  So be sure to aviod manual configuration option 

Hope this helps you.



If you gain knowledge, Be Sure to Pass It On and make someone elses life Easy

---

### Post by LucaTNT on 2008-01-23
You may also check if the driver is *really* loaded.
Launch
```
lsmod | grep ipw
```
if it outputs something like
```
ipw3945               119840  1 
ieee80211              35656  1 ipw3945
```
it means that the kernel module is loaded.

The driver also needs a daemon running to work, launch
```
ps aux | grep ipw3945d
```
if the output contains something like
```
root      5084  0.0  0.0   1744   360 ?        S<   12:28   0:14 /sbin/ipw3945d-2.6.22-14-generic --quiet
```
it should be running.

Please, post also the result of iwconfig and ifconfig.

---

### Post by Polaroid on 2008-01-24
> **mikewhatever said:**
> There is a lengthy Wireless Troubleshooting Guide you might find useful. [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wireless%29](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wireless%29)
The card you have has one of the best supports on Linux and the driver is definitely in use (driver=ipw3945). Try following the guide to get the idea of what's wrong, but skip ndisrapper section.

Thanks heaps, I'm reading it now..

> **ankuryu said:**
> Hi, I too have a Intel 3945 Wireless Card.  I too had the same problem.  However I have KUBUNTU.   well here is what I did .......

  edited the file  /etc/network/interfaces  so as to remove everything except the following
 two lines

 auto lo
 iface lo inet loopback

 save it (make sure u have edited using sudo ....) Also make a backup of Original interface file as interface.bak

 Right Clicked on the network manager Icon and select  Options > Show Other Networks

remove all the Trusted Network in the list using "REMOVE"

Exit and reboot.

Soon was shown the Active Networks, selected the appropriate Network and enter the necessary Data and Voila, Computer was connected to my WFH54G Router using WPA2 Encryption.

Also remember when u choose the manual Configuration and save it, You may have to go through the above process again.  So be sure to aviod manual configuration option 

Hope this helps you.



If you gain knowledge, Be Sure to Pass It On and make someone elses life Easy

Thanks heaps for the info :D
I just tried this method out by means of [this guide]("http://ubuntuforums.org/showthread.php?t=603154&highlight=edit+using+sudo"), although I don't think this is the problem..
I think with this method your network manager has to be able to recognize your wireless in the first place, whereas my network manager is missing a few *beans* and thinks that it doesn't have any wireless connection TO establish. 
I tried it anyway with the live cd, but that still didn't work. In fact, it said that there was a wired internet connection when i had nothing plugged in.
Soooo yeah, still no luck. :(
 

> **LucaTNT said:**
> You may also check if the driver is *really* loaded.
Launch
```
lsmod | grep ipw
```
if it outputs something like
```
ipw3945               119840  1 
ieee80211              35656  1 ipw3945
```
it means that the kernel module is loaded.

The driver also needs a daemon running to work, launch
```
ps aux | grep ipw3945d
```
if the output contains something like
```
root      5084  0.0  0.0   1744   360 ?        S<   12:28   0:14 /sbin/ipw3945d-2.6.22-14-generic --quiet
```
it should be running.

Please, post also the result of iwconfig and ifconfig.


These are my results:

```
ipw3945               119840  1 
ieee80211              35656  1 ipw3945
```

And:

```
root      3864  0.0  0.0   1744   360 ?        S<   15:45   0:00 /sbin/ipw3945d-2.6.22-14-generic --quiet
antho 5983   0.0  0.0  2992   784   pts/0     S+    15:47   0.0  grep  ipw3945d
```

Well, to me everything looks okay..

---

### Post by LucaTNT on 2008-01-24
> **Polaroid said:**
> Thanks heaps, I'm reading it now..



Thanks heaps for the info :D
I just tried this method out by means of [this guide]("http://ubuntuforums.org/showthread.php?t=603154&highlight=edit+using+sudo"), although I don't think this is the problem..
I think with this method your network manager has to be able to recognize your wireless in the first place, whereas my network manager is missing a few *beans* and thinks that it doesn't have any wireless connection TO establish. 
I tried it anyway with the live cd, but that still didn't work. In fact, it said that there was a wired internet connection when i had nothing plugged in.
Soooo yeah, still no luck. :(
 




These are my results:

```
ipw3945               119840  1 
ieee80211              35656  1 ipw3945
```

And:

```
root      3864  0.0  0.0   1744   360 ?        S<   15:45   0:00 /sbin/ipw3945d-2.6.22-14-generic --quiet
antho 5983   0.0  0.0  2992   784   pts/0     S+    15:47   0.0  grep  ipw3945d
```

Well, to me everything looks okay..
Yes, it should be...
It might be useless, but try to post the result of iwconfig and ifconfig anyway.

---

### Post by Polaroid on 2008-01-24
> **LucaTNT said:**
> Yes, it should be...
It might be useless, but try to post the result of iwconfig and ifconfig anyway.

Here are the results:
```

antho@antho-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:81:A7:7C  
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:3763 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4728613 (4.5 MB)  TX bytes:306806 (299.6 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```

antho@antho-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```


I'm not sure what that entirely means..
but I don't like the look of 'no wireless extensions'

I can plug in wired internet and that works like a charm, so there's no reason why the wireless shouldn't do the same :\

Thanks for your help :)

---

### Post by tengil on 2008-01-24
I must be having the exact same problem. The strange thing is that I had everything working before. Wireless was working ok from day one in 7.10. I'm usually connecting through wire so the last time I used the wireless was at christmas. Now it's gone, so something must have happened between then and now.

---

### Post by tengil on 2008-01-24
I'm sorry but my setup is working perfectly. Had things confused (I'm home sick so maybe I'm excused :-)).

Well, here's a shot in the dark...

Since you have a laptop maybe the wireless device is disabled? There might be a button to enable/disable the device, or an fn-key combo. Run:

```
lshw
```

and look for something like this:

```

           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: eth1
                version: 02
                serial: 00:1b:77:96:b8:a6
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=no module=ipw3945 multicast=yes wireless=unassociated

```

This might also work (avoiding the lengthy output):

```
lshw | grep ipw3945
```

The end of the last line holds the key, "wireless=unassociated". If this instead reads "wireless=radio off" then the wireless card is disabled and you have to turn it on.

---

### Post by Polaroid on 2008-01-25
> **tengil said:**
> I'm sorry but my setup is working perfectly. Had things confused (I'm home sick so maybe I'm excused :-)).

Well, here's a shot in the dark...

Since you have a laptop maybe the wireless device is disabled? There might be a button to enable/disable the device, or an fn-key combo. Run:

```
lshw
```

and look for something like this:

```

           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: eth1
                version: 02
                serial: 00:1b:77:96:b8:a6
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=no module=ipw3945 multicast=yes wireless=unassociated

```

This might also work (avoiding the lengthy output):

```
lshw | grep ipw3945
```

The end of the last line holds the key, "wireless=unassociated". If this instead reads "wireless=radio off" then the wireless card is disabled and you have to turn it on.



Here are my results...
With the network, it says ethernet interface instead of wireless, does this mean I have to change it from ethernet to wireless?
I'm not sure how to do that (pardon me for me noobness lol)

```


  *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0a:00.0
                logical name: eth0
                version: 10
                serial: 00:16:36:81:a7:7c
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes

```



And here is the lshw | grep ipw3945 code, it looks totally different from what you were talking about D:
```

antho@antho-laptop:~$ lshw | grep ipw3945
WARNING: you should run this program as super-user.
                configuration: driver=ipw3945 latency=0 module=ipw3945

```

---

### Post by tengil on 2008-01-25
You should have two *-network sections in the output from lshw. One for the wire card and one for wireless. See if you can find the section for the wireless card and post it here. If you can't locate it just post the entire lshw output.

---

### Post by Polaroid on 2008-01-26
> **tengil said:**
> You should have two *-network sections in the output from lshw. One for the wire card and one for wireless. See if you can find the section for the wireless card and post it here. If you can't locate it just post the entire lshw output.

Hey tengil, sorry for the late reply...

Damn i'm silly hahahha
here's the WIRELESS interface section:

```

   *-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ipw3945 latency=0 module=ipw3945


```

---

### Post by Polaroid on 2008-01-26
Still no results!
:confused:

---

### Post by themrcul on 2008-01-26
I had the exact same problem, a few days ago, wireless was working fine. Just before, it wasn't. iwconfig said there were no wireless extensions, and lshw didn't give me a logical name for my wireless card, just like it doesn't for poloroid. I didn't know what went wrong... I tried restarting, enabling/disabling the restricted driver... Nothing turned it on again, until I restarted back into windows and turned it on there.
So wireless activation/deactivation status is stored at the hardware level, not software...
So poloroid, if you have windows, reboot into that and switch your card on there, then boot back into ubuntu. If you don't have windows, please find a thread on the forums on getting your notebook wireless on/off switch working and switch it on there. I will look for the same kind of thread for my notebook later, but I have to go now.
Good luck.

---

### Post by themrcul on 2008-01-26
This solved it for me, and I don't need to go into windows to turn my wireless card on or off anymore:

To turn on my card from the terminal, I type:
sudo modprobe ipw3945 disable=0

To turn it off, I type:
sudo modprobe -r ipw3945

I hope this helps, I will research into binding those commands into the button press soon.

---

### Post by Polaroid on 2008-01-27
> **themrcul said:**
> This solved it for me, and I don't need to go into windows to turn my wireless card on or off anymore:

To turn on my card from the terminal, I type:
sudo modprobe ipw3945 disable=0

To turn it off, I type:
sudo modprobe -r ipw3945

I hope this helps, I will research into binding those commands into the button press soon.

Thanks for your replies!
Turning it on and off from the terminal doesn't help me, but maybe I just need to try and do what you did first, by reinstalling windows, then going with ubuntu again.
Then perhaps it'll follow the commands.
Thanks heaps for your help, I think I'm getting closer to the problem now :D

-Edit- now that I tried the codes, I have my restricted drivers as enabled, but now they say that they are not in use..
No matter whether it's code A or B I put into the terminal, :S
-Edit2- after reinstalling ubuntu, it says it is in use again, although for some strange reason those commands don't seem to have an effect at all 

My computer seems about as stable as my ex girlfriend :(

---

### Post by BoojiBoy on 2008-01-27
I'm having the same issue with my HP laptop. I think it may have something to do with the driver's version. When I boot into kernel version 2.6.22-14, everything works fine. But, when booting into 2.6.24-5 (or any of the others in-between) I get the same symptoms. When I go to [http://www.intellinuxwireless.org/]("http://www.intel") and look at the "Debian" packages, the newest one is 2.6.22-4. Is a newer driver just not available yet?

---

### Post by starsheeep on 2008-02-06
i have a lg f1 notebook wth intel 3945abg / ubuntu-gutsy
and I can't connect using wpa, if i try nm-applet will freeze after a while
nm-applet manual configuration takes 5' to load

I tried ipw3946 (from sourceforge and from the restricted driver manager) and iwlwifi drivers.
The manual configuration delay was corrected with the iwlwifi driver (guess it was the binary daemon causing it) but wap still freezes the nm-applet

and i also read in a thread that ndiswrapper wont work cause the windows driver depends on some windows files; (i haven't confirmed that)

point is, even if you get the ipw3945 or lwlwifi drivers up and running, can you connect using wpa, and find some way to manage your connections through the gui? (the notebook is intended for a novice user)

wpasupplicant installed and all.

**_solved: downgraded to edgy and installed wicd network manager, wpa worked after that, its the gnome network manager that causes this problem pro/bly, will try wicd in gutsy and edit again_.**

---

### Post by militem on 2008-02-10
I have the same wireless card, here is my problem.  I did a clean install of 7.10, and wiped off the Vista partition.  Before I did that, I was running of the liveCD, and I was able to connect to my network with Vista.  I was not able to connect to wireless though Ubuntu on the liveCD, but, me being a noob, I thought it would work once I installed.  I don't care that everything is not working hunky-dory off the bat.  I need Linux for my professional and personal computing development, and I intend to stick with it until it works.  Here is the output 

matt@matt-laptop:~$ sudo lshw -C network
[sudo] password for matt:
  *-network               
       ** description: Wireless interface **
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
      ** logical name: eth1**
       version: 02
       serial: 00:1c:bf:6b:cf:f2
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=no module=ipw3945 multicast=yes wireless=unassociated
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:8c:6f:97:4b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full ip=192.168.1.72 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s


I think my problem is the my wireless logical name is "eth1".  I think it should be wlan0 or something like that.  Does anyone know how I can change that in Ubuntu?  I've seen how to do it in Kunbuntu.  Thanks

---

### Post by starsheeep on 2008-02-12
I'm no experienced user, so don't take my word for it, but i think that if your card appears in iwconfig then it should work, the name doesn't matter, I have the same card and got it working (with wpa) after installing wicd, the gnome network manager did not work for me (the applet installed by default in gutsy)

the following 
from:[http://ubuntuforums.org/showthread.php?t=527488](http://ubuntuforums.org/showthread.php?t=527488)

To install WICD do the following: (for gutsy, edgy, or dapper replace feisty as needed)
echo 'deb [http://apt.wicd.net](http://apt.wicd.net) feisty extras' | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install wicd

i think this will uninstall the network manager and install wicd, if you get any error in the last command try again from synaptic manager

after the installation run wicd applications->internet>wicd
go 2 preferences and in the wireless tag type eth1

the rest is easy :)

---

### Post by diogoandre on 2008-02-19
I'm having a similar problem with ipw2200. From my debugging it looks like a IRQ allocation problem... but I have no idea how to solve it.

here is the output of lshw

> 
 sudo lshw -C network
  *-network:0 UNCLAIMED   
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:d0:75:51:b9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=189.6.68.170 latency=128 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s


and my lsmod

> 
ipw2200               149320  0 
ieee80211              35656  1 ipw2200



any clues ?!

thanks !

Diogo

---

