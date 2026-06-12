---
title: "The wireless is very unstable."
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by kjman83 on 2008-04-08
Hi guys..  At last I intalled wireless in my laptop. (8.04 ubuntu)
I can see lots of networks. 
but one problem is I can't connect to the network what I used to use.
Just one Time I connected to the network. I still see the network but I can't connect to it.
I don't know What problem is.. 
Do you think is there a conflict with something?
Really :(

*information
-------------------------------------------------------------------
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:a4:e4:2a:ee  
          inet addr:87.198.40.161  Bcast:87.198.41.255  Mask:255.255.254.0
          inet6 addr: fe80::217:a4ff:fee4:2aee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3009 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2565682 (2.4 MB)  TX bytes:482360 (471.0 KB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6600 (6.4 KB)  TX bytes:6600 (6.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:4f:ea:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Memory:c8000000-c8004000

---

### Post by dstew on 2008-04-08
Sometimes it helps to blacklist the alternate driver. You do that by editing the /etc/modprobe/blacklist file. In your case, add the line **blacklist ssb** and reboot. See if that helps. Oh, and do **ndiswrapper -l** again to see if the blacklisted driver is gone after you reboot.

---

### Post by kjman83 on 2008-04-08
really Thank you 
I just one time connected again but 
it seemed not to work,,


echo 'blacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist
and then I rebooted but The ssb is still there..
I think still something  conflict.
Could you help me one more?


kjman83@guinness:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
kjman83@guinness:~$

---

### Post by dstew on 2008-04-08
Do ```
lsmod
```and see if ssb is there. If it is not, then the alternate driver message is only coming from ndiswrapper, and you can ignore it. If ssb is there, try```
sudo modprobe -r ssb
```to remove it. Look at the lsmod output again. It should be gone. Then try ndiswrapper -l to see if it is still listed.

---

### Post by kjman83 on 2008-04-08
Really thank you..

kjman83@guinness:~$ sudo modprobe -r ssb
FATAL: Module ssb is in use.
kjman83@guinness:~$ 


There is  ssb  . What is it?

---

### Post by dstew on 2008-04-08
I did a bit more googling. It seems that the ssb module has a bug in it that causes it to associate with the wireless card. I think ssb is actually intended to be used with other hardware (the PCI bus in general). [This thread]("http://bbs.archlinux.org/viewtopic.php?id=43904") shows users struggling with this problem. It seems it does not happen in all systems, but only some.

The solution seems to be to make sure ndiswrapper loads before ssb. It seems ssb is associated with the modules b43 and b44, so the fix was to edit the file /etc/rc.conf to make the ndiswrapper load before b44, and to blacklist b43. Its worth a look.

Here is [another thread about the same thing]("http://sidux.com/PNphpBB2-viewtopic-t-9040.html"). It is really a kernel bug. Both older and newer kernels work fine.

---

### Post by kjman83 on 2008-04-08
Actually I don't know What I did.
I just followed other users' saying.
After ndiswrapper installing, I followed this one.
---------------------------------------------------------------
HOWTO: Get Ndiswrapper working in Hardy Beta
Original message:

Quote:
I gave up on the b43-fwcutter driver (worst driver ever) and have instead followed the ndiswrapper method which worked for me in Gutsy. I've blacklisted the b43 driver and added "ndiswrapper" to my /etc/modules file, but no dice. I'd like to add that doing "sudo ndiswrapper -m" tells me that the file i'm adding it to isn't used anymore. What is used instead? Has anyone got ndiswrapper working?
How to get Ndiswrapper working!

1.) Remove the b43-fwcutter package if you have it installed, and get an ethernet cable ready. Connect the cable to your wireless router, and run

Code:

sudo aptitude remove b43-fwcutter


2.) Follow the method you have used which worked in Gutsy. Ignore the part about blacklisting bcm43xx.

3.) There's currently a workaround to getting ndiswrapper working, which might be fixed before release.

run this:

Code:

sudo gedit /etc/init.d/wirelessfix.sh

and paste this:

Quote:
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
into the file. Close and save it.

Next, run this:

Code:

cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

and finally, this:

Code:

sudo update-rc.d wirelessfix.sh defaults

Restart and enjoy your wireless!
----------------------------------------------

So I can see my wireless turning on.
But now a little problem.. 
In lsmod , there is not b43,  there is b44.

I'm really beginner of ubuntu(linux).

Could you explain more easy please?
I think I don't understand what you wrote.

Sorry & Really Thanks

---

### Post by kjman83 on 2008-04-08
and I found  about ssb .
it is just related to bcm43xx.
If it is possible to remove forcedly, How about removing?
Isn't it good method?

---

### Post by dstew on 2008-04-08
> In lsmod , there is not b43, there is b44.That is how it should be. The only important thing is that ndiswrapper loads before ssb (or, b44 in this case). In the script you posted, that is what they are trying to do. The problem might be that the modprobe -r b44 does not work, for the same reason that modprobe -r ssb doesn't work, that the module is in use. I think you have to get the system to load ndiswrapper before b44 at boot time, and not just run a script later. It might be different in different systems though. I think the script posted here attempts to do that:```
#/etc/rc.conf
MOD_AUTOLOAD="yes"
MOD_BLACKLIST=(... b43)
MODULES=(ndiswrapper b44 mii !bcm43xx ...)
```I am not at my linux computer, so I don't know if this rc.conf file has more stuff in it, or if you just add these lines, or what the ...'s mean. But I think this script will be run at bootup time, and it tries to get ndiswrapper loaded before b44.

EDIT: About removing ssb by force, I am not sure about that. I only know about blacklisting. Maybe blacklist b43 also, I don't know. Can you post your blacklist file?

---

### Post by kjman83 on 2008-04-08
can I put it this one in /etc/init.d/wirelessfix.sh
Sorry I don't know where should I put it in...


--------------------------------------------------------
And I just typed it in terminal. in case I can't login again after rebooting.
kjman83@guinness:/etc$ MOD_AUTOLOAD="yes"
kjman83@guinness:/etc$ MOD_BLACKLIST=(... b43)
kjman83@guinness:/etc$ MODULES=(ndiswrapper b44 mii !bcm43xx)
bash: !bcm43xx: event not found
kjman83@guinness:/etc$ 
--------------  the last line is ok? Doesn't it matter?

---

### Post by kjman83 on 2008-04-09
Sorry It's my blacklist , I'm very late. 

-------------------------------------------------------------------------------
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

blacklist bcm43xx
blacklist ssb
blacklist ssb

---

### Post by kjman83 on 2008-04-09
# replaced by b43 and ssb.
blacklist bcm43xx

instead of the line, can I use replaced by ndiswrapper ?

Is there anyone know about changing this thing.. please just tell me.

---

### Post by dstew on 2008-04-09
> instead of the line, can I use replaced by ndiswrapper ?Don't worry about the line that starts with #, that is just a comment. Since you are trying to get ndiswrapper to work, you should also blacklist b43.

---

### Post by tora201 on 2008-04-09
Heh... thanks for posting your blacklist. I just copied it over mine and all is well. Before that my stupid wireless kept on dropping. Cheers!

---

### Post by kjman83 on 2008-04-09
blacklist ssb
blacklist ssb
blacklist b43

I added the line..
and reboot but still like this below
--------------------------------------------------
kjman83@guinness:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
--------------------------------------------------
I think you solved my problem nearly :), but my laptop is nauty boy.

---

### Post by dstew on 2008-04-09
Post the output of```
lsmod | grep ssb
```

---

### Post by kjman83 on 2008-04-09
kjman83@guinness:~$ lsmod | grep ssb
ssb                    32772  1 b44

---

### Post by dstew on 2008-04-09
I am stuck at this point. From everything I know, ssb should not be loading if it is blacklisted. The only other thing to try is the script to load ndiswrapper before ssb, as I posted above. Sorry I can't figure this one out.

---

### Post by kjman83 on 2008-04-09
It's ok. Really thank you for concerning.
I just wonder one thing. What is b44.
Can I add blacklist b44. How do you think?

---

### Post by dstew on 2008-04-09
Yes, do that. From your lsmod output, you can see that b44 and ssb are sharing some hardware. Maybe b44 is causing ssb to load. However, b44 might be running something else, like the PCI bus, so if you blacklist it, your system might not work right. But, you can always boot a live CD, and find the blacklist file on your hard disk, and un-blacklist b44 if that happens.

EDIT: b44 is the driver for Broadcom wired etherned NICs, so if you blacklist it you will probably lose your wired network connection.

---

### Post by kjman83 on 2008-04-09
I just tried this one.
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper


before it has 'modprobe b44'.
I rebooted but same as before.
nothing different..
Can I know what is wired network driver?
I just remove wired network driver instantly, how do you think?

---

### Post by dstew on 2008-04-09
> Can I know what is wired network driver?You can look at the output of```
lshw -C network
```Both the wired and wireless interfaces should be there, with the information about the drivers.> I just remove wired network driver instantly, how do you think?You can just enter the command```
sudo modprobe -r b44
```

---

### Post by kjman83 on 2008-04-09
This below is out put of that.

I just wonder before do it off , Can I know how can I turn my wired network on?

-----------------------------------------
kjman83@guinness:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:17:a4:e4:2a:ee
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=87.198.40.150 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:4f:ea:20
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
kjman83@guinness:~$

---

### Post by kjman83 on 2008-04-09
I did it(below one) but I still can connect to the internet.



---------------------------------------------------------
kjman83@guinness:~$ sudo modprobe -r b44
kjman83@guinness:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
kjman83@guinness:~$

---

### Post by dstew on 2008-04-09
Post the output of iwconfig. I don't have any more ideas about blacklisting ssb. Maybe we can configure a working interface anyway.

---

### Post by kjman83 on 2008-04-09
kjman83@guinness:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kjman83@guinness:~$

---

### Post by kjman83 on 2008-04-09
ESSID Off/any 

I think this line is problem.. when I turn off this laptop..
laptop always warns about ESSID things..
You know what is that?

---

### Post by dstew on 2008-04-09
I don't know why that is. Anyway, enter your SSID and see if we can get connected. By the way, is the wireless access point set up with any encryption? If so, we need to enter the key. And, will you get your IP address from the router DHCP server, or do we need to set it up with a static IP address? To enter your SSID do```
sudo iwconfig wlan0 essid "Your_SSID"
```

---

### Post by kjman83 on 2008-04-09
Jesus Thank you .. your relpy  
Everytime you helped me..
But I'm Actually beginner of ubuntu.
I really don't know about your last reply.
Your_SSID  What's this? is that my ID(kjman83)?

Why doesn't my wired network turn off? you know?
I turn it off though , it still works.

weird.

---

### Post by dstew on 2008-04-09
> Your_SSID What's this? is that my ID(kjman83)?No, the SSID is the name of the wireless network you want to connect to. Who owns the wireless access point you are trying to connect to? Is it your own router, or does it belong to someone else? Sometimes you can get a list of available SSIDs by the command```
iwlist wlan0 scan
```

I think you should try to enter the /etc/rc.conf script I mentioned in an earlier post. This will make it so ndiswrapper loads before the other network drivers. One user had success with this. To do it, open a text editor to edit (or create) the file:```
gksudo gedit /etc/rc.conf
```Enter the lines```
MOD_AUTOLOAD="yes"
MOD_BLACKLIST=(... b43)
MODULES=(ndiswrapper b44 mii !bcm43xx ...)
```just like that. Copy them from this post and paste them into the file. Then save the file, and reboot. Then try ndiswrapper -l again.

---

### Post by kjman83 on 2008-04-09
My laptop always makes you be disappointed.

kjman83@guinness:~$ iwlist wlan0 scan
wlan0     No scan results

kjman83@guinness:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
kjman83@guinness:~$ 


It's the reaction after makinf rc.conf file

---

### Post by kjman83 on 2008-04-09
It's the picture of my laptop. 
When I restart it I can always see this warning at the time .

---

### Post by kjman83 on 2008-04-10
I watched movie.
So I unplugged wire.
after 2 hours it worked very well without wire.
But I rebooted it.
It the same..
Now I 'm connect by wire. :(

---

### Post by dstew on 2008-04-10
One more thing to try: disable Network Manager. Here is how taken from a post in [this bug thread]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/82335"):

1. Stop network manager```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```

2. Create two files with only the word 'exit' in them. These files are:```
/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher
```

---

### Post by kjman83 on 2008-04-10
Now Network manager doesn't work.
So I connect to here by dhclient.
I learnt it today, dhclient.

Should I remove the files what I made just before?

or How can I start Network Manager?


-----------------------------------------  just added  in case it helps you.
kjman83@guinness:~$ nm-applet 

** (nm-applet:5540): WARNING **: <WARN>  nma_dbus_update_wireless_enabled_cb(): dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files

---

### Post by dstew on 2008-04-10
To go back to the way it was before, remove the /etc/default/NetworkManager and /etc/default/NetworkManagerDispatcher files, then do```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher start
sudo /etc/dbus-1/event.d/25NetworkManager start
```

---

### Post by kjman83 on 2008-04-10
The first time after rebooting, It works fairly well..

but second time after rebooting without anyting, It's same as before.
the thrid time after rebooting without anyting, It's same as second time.

I will do it again.
stop things, and creat things and then remove, start things

---

### Post by kjman83 on 2008-04-10
no still wired network.

How about another network manager program.

 is there any different things? 

I installed 'wicd' in the morning but it doesn't work. I can't see any program of 'wicd'.

---

### Post by dstew on 2008-04-10
Did you follow [the wicd directions]("http://wicd.sourceforge.net/download.php")?

---

### Post by kjman83 on 2008-04-10
Nearly I did do it.
I 'll do it again.
Just a sec.

---

### Post by kjman83 on 2008-04-10
Now I installed Wicd
It looks different..
Anyway.. 
I can Find lots of wireless network.
I tried to connect to the internet by my wireless network.
but Just I can see the message 'Obtaining IP address'.

Should I install my driver things again in this program?

I'm connecting by dhclient


Additionally I can't use wired network now.. I just connect by dhclient.

---

### Post by kjman83 on 2008-04-10
Do you Think Should I buy wireless Lan by USB?
or after long time can I use my stupid wireless lan?
I really don't give up my lovely ubuntu.
I tried 7.10 version but I couldn't install in here.
If I can do it, I wouldn't have any problems.
:(
You are very nice guy.
How do you think about my situation?

I reinstalled Network Manager. It seems to be better.
If after it is upgrade ,do you think I can use wireless?
Is it stupid question , isn't it?  

You are really nice man , because of you I won't give up I won't go back to windows.
Really Thanks.

If you have any different idea, Just post here for me please..

---

### Post by dstew on 2008-04-10
> I can Find lots of wireless network.This is good, the driver is working better.> but Just I can see the message 'Obtaining IP address'.Is the wireless access point set up as a DHCP server? Or do you need to set a static IP address?

---

### Post by kjman83 on 2008-04-10
I could connect to wireless network by wicd but very unstable as well..
Now I 'm connecting by ndiswrapper.. I don't know why now it works perfectly.
Maybe After reboot I should use wired network.
The bad thing is I can't use wired network by wicd.

How do you think?

Now it works perfectly, I didn't do any thing though just tried my wireless network.


------------------------- information When it works lovely ..
kjman83@guinness:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:a4:e4:2a:ee  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31736 (30.9 KB)  TX bytes:20623 (20.1 KB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8900 (8.6 KB)  TX bytes:8900 (8.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:4f:ea:20  
          inet addr:87.198.40.174  Bcast:87.198.41.255  Mask:255.255.254.0
          inet6 addr: fe80::21a:73ff:fe4f:ea20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:686989 (670.8 KB)  TX bytes:87269 (85.2 KB)
          Interrupt:10 Memory:c8000000-c8004000 

kjman83@guinness:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"MAGNET-4820"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:03:6F:95:27:32   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kjman83@guinness:~$

---

### Post by dstew on 2008-04-10
If the wireless is working, do```
lshw -C network
```to see which driver is being used.

---

### Post by kjman83 on 2008-04-10
It's the result. now it works well because I didn't retood yet.

-----------------------

kjman83@guinness:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:17:a4:e4:2a:ee
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:4f:ea:20
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. ip=87.198.40.174 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
kjman83@guinness:~$

---

### Post by dstew on 2008-04-10
So we know your wireless works well with ndiswrapper+bcmwl5. At least that is something.

---

### Post by kjman83 on 2008-04-10
Anyway I want to enjoy this situation more longer.
I don't want to reboot and I don't want to think more :(
Man!! you are Really good man..
Thanks.. 
If It works well after rebooting, I will post here again. :)
Now I just enjoy and relax with my naughty laptop.
See you.. soon

---

### Post by lswest on 2008-04-10
um, i was just reading through this and wanted to point out that in Hardy, for me, iwlist scan gives me no result unless i do ```
sudo iwlist scan
``` don't know if you needed it anymore, but just wanted to point that out.

---

### Post by kjman83 on 2008-04-10
Thank you


kjman83@guinness:~$ sudo iwlist scan
[sudo] password for kjman83: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:03:6F:95:27:32
                    ESSID:"MAGNET-4820"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:11:50:FB:A5:DE
                    ESSID:"ciannetwork"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:0F:CC:CF:8A:E8
                    ESSID:"eircom6370 2444"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:16:E3:1F:9D:71
                    ESSID:"BTVOYAGER2110-71"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:0F:CC:5E:02:14
                    ESSID:"eircom2740 6730"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

