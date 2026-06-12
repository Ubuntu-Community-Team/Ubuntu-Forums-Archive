---
title: "[Solved] Polar Infrared Interface (StIR4210 based)"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by regne v on 2007-08-13
I've struggled for two weeks to get this thing working so I hope this will help someone:

This IR USB dongle is based on the Sigmatel 4210 chip. Probably this will also work with 4220 and 4116 chips as they share the same driver

Copy [these two firmware patches]("http://www.sigmatel.com/documents/stir4210_4220_4116_patch_files.tar.gz") into [FONT="Courier New"]/lib/firmware[/FONT].

Create [FONT="Courier New"]/etc/modprobe.d/blacklist-usbserial[/FONT] and add:

[INDENT][FONT="Courier New"]#If these modules are loaded stir421x driver won't work.
blacklist       ir_usb
blacklist       usbserial[/FONT][/INDENT]

[FONT="Courier New"]/etc/default/irda-utils[/FONT] should be:
[INDENT][FONT="Courier New"]ENABLE="true"
AUTOMATIC="false"
DISCOVERY="true"
DEVICE="irda0"
DONGLE="none"
SETSERIAL=""[/FONT][/INDENT]

After reboot you should see in [FONT="Courier New"]dmesg[/FONT] something like:
[INDENT][FONT="Courier New"]stir421x_patch_device(): Received firmware 42101002.sb (1687 bytes)[/FONT][/INDENT]

Check it with [FONT="Courier New"]ifconfig irda0[/FONT]:
[INDENT][FONT="Courier New"]irda0     Link encap:IrLAP  HWaddr ea:b6:70:02  
          UP RUNNING NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3997 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:60526 (59.1 KiB)[/INDENT][/FONT]
And the final test: 
[INDENT][FONT="Courier New"]$ sudo irdadump
Password:
15:36:41.226983 xid:cmd eab67002 > ffffffff S=6 s=0 (14) 
15:36:41.314928 xid:cmd eab67002 > ffffffff S=6 s=1 (14) 
15:36:41.402926 xid:cmd eab67002 > ffffffff S=6 s=2 (14) 
15:36:41.490926 xid:cmd eab67002 > ffffffff S=6 s=3 (14) 
15:36:41.578922 xid:cmd eab67002 > ffffffff S=6 s=4 (14) 
15:36:41.666926 xid:cmd eab67002 > ffffffff S=6 s=5 (14) 
15:36:41.754922 xid:cmd eab67002 > ffffffff S=6 s=* islero hint=0400 [ Computer ][/INDENT][/FONT]

Hope this helps.

---

### Post by krsnendu on 2007-09-08
My irda device is not a polar device but it worked fine in Windows for uploading my 625x data. Now I want to use it for linux. I think it is being detected and loaded properly this is the output I get from irdadump[HTML]00:23:19.454683 xid:cmd 9e11eb19 > ffffffff S=6 s=0 (14) 
00:23:19.542675 xid:cmd 9e11eb19 > ffffffff S=6 s=1 (14) 
00:23:19.630677 xid:cmd 9e11eb19 > ffffffff S=6 s=2 (14) 
00:23:19.718682 xid:cmd 9e11eb19 > ffffffff S=6 s=3 (14) 
00:23:19.806686 xid:cmd 9e11eb19 > ffffffff S=6 s=4 (14) 
00:23:19.894690 xid:cmd 9e11eb19 > ffffffff S=6 s=5 (14) 
00:23:19.982697 xid:cmd 9e11eb19 > ffffffff S=6 s=* krsnendu-desktop hint=0400 [ Computer ] (32) [/HTML]

What do I have to do now to get it going with performance manager under Crossover office (wine)?

Thanks,
Krsnendu dasa

---

### Post by regne v on 2007-09-10
I use Polar Personal Trainer from a vmware virtual machine because I had no luck trying to get [this]("http://code.google.com/p/s710/") working.

When I tried to READ the configuration from my s625x it just messed its settings and had to reprogram it with PPT, nothing serious.

I also tried to make PPT work within wine with no luck at all, the screen was unviewable and the irda functions didn't work at all. Just like [this report]("http://appdb.winehq.org/appview.php?iVersionId=8183&iTestingId=12612").

If you get s710 to work, please tell me how.

---

### Post by brad103 on 2007-10-19
Cheers for the post! I have a DSE XH8286 with the same chipset.

Did you manage to build the driver then? I am having no luck building one so while I get the expected dmesg output I get no traffic in ifconfig irda0 and nothing in irdadump. Could you please attach your driver?

(Here's my dmesg for completeness: )
```
...
[  226.434393] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  226.602606] usb 1-1: configuration #1 chosen from 1 choice
[  228.883187] IRDA-USB found at address 2, Vendor: 66f, Product: 4210
[  228.937115] irda_usb_parse_endpoints(), And our endpoints are : in=02, out=01 (64), int=00
[  228.980430] irda_usb_init_qos(), dongle says speed=0x17F, size=0x20, window=0x8, bofs=0x1, turn=0x4
[  228.982139] IrDA: Registered device irda0
[  230.350945] stir421x_patch_device(): Received firmware 42101001.sb (8299 bytes)
[  230.367474] irda_usb_init_qos(), dongle says speed=0x13F, size=0x20, window=0x8, bofs=0x80, turn=0x4
[  230.367541] usbcore: registered new interface driver irda-usb
[  230.367553] USB IrDA support registered

```

Thanks so much
Brad

---

### Post by regne v on 2007-10-20
> **brad103 said:**
> Did you manage to build the driver then?

I did build no driver at all. The driver is built into the irda_usb kernel driver but somehow is incompatible with the two modules you have to blacklist.

In fact, here you can read in your dmesg that the driver has sent the firmware patch:

> **brad103 said:**
> [  230.350945] [COLOR="Red"]stir421x_patch_device()[/COLOR]: Received firmware 42101001.sb (8299 bytes)

And here you can read that you have got an "irda0" interface

> **brad103 said:**
> [  228.982139] [COLOR="Red"]IrDA: Registered device irda0[/COLOR]

You only need that irda_utils activates it. If you can't see the interface with "ifconfig irda0", please, double check the irda_utils configuration file.

---

### Post by zebrankyza on 2007-11-25
First off, thanks regne v for posting this!  It has saved me a tremendous amount of time :).

However, I now have some strange issues.  I have [the latest Polar IrDA USB device]("http://support.polar.fi/PKBSupport.nsf/OldProduct/IrDAUSBAdapter?openForm") (the standard IrDA as opposed to the Polar specific one), and followed the steps above.  I managed to get it installed, and detected (all outputs as described above work 100%).  However, after a second reboot, inserting the Polar device causes a coredump, and my machine locks (Caps Lock key flashes which I assume means a core dump or some fatal internal error).  I am not entirely sure if I've done something wrong, or if I just have a corrupt file somewhere.  If I do not insert the device, the system appears to run just fine.

Is there anything anyone can suggest to get the device working properly?  If you need logs/coredumps etc please let me know (and where to find them, I am pretty new to Linux).  I do not mind grinding away at a solution :D.  For now I have reversed the above steps to remove any potential lockups.

As a side note: once installed as irda0, where (or how) do I get the s710 application to work with it?  I saw [this link]("http://ubuntuforums.org/showthread.php?p=504374"), would this be correct?

Nearly forgot to mention: Running Ubuntu 7.10, with all updates through to Nov 24 2007.

Thanks in advance to anyone that can help :)
Brian

---

### Post by regne v on 2007-11-26
> **zebrankyza said:**
> However, after a second reboot, inserting the Polar device causes a coredump, and my machine locks (Caps Lock key flashes which I assume means a core dump or some fatal internal error).  I am not entirely sure if I've done something wrong, or if I just have a corrupt file somewhere.  If I do not insert the device, the system appears to run just fine.

I've tried to boot ubuntu and then plug the adapter and I got no problem. The "Received firmware..." message appeared in dmesg as usual. The only thing I had to do was running "sudo /etc/init.dirda-utils restart" for the irda interface to start working, but no core dump at all.

Please switch to text mode (ctrl-alt-F1) and plug the interface to see if any message is displayed there when the machine hangs and post it here. Press ctrl-alt-F7 to get back to X.

Are you pluging the adapter into a usb hub and your keyboard is also plugged in it?.

Also try to plug the interface with the drivers removed. Just in case.

> **zebrankyza said:**
> As a side note: once installed as irda0, where (or how) do I get the s710 application to work with it?  I saw [this link]("http://ubuntuforums.org/showthread.php?p=504374"), would this be correct?
You can download s710 from [here]("http://code.google.com/p/s710/"), but I can't give you any advice as I didn't get to make it work.

---

### Post by zebrankyza on 2007-11-27
Rightio, seems that "cleaning the pipes" made it work a with a little more stability.  So far so good.

I did have a look at the s710 app, and that lead me to here as I could not get the USB IrDA device working :)

However, I see on [this post]("http://code.google.com/p/s710/issues/detail?id=4") that you have to run this to get s710 working on /dev/ircomm0:
```

sudo modprobe ircomm-tty

```

But I just get this error:
```

brianj@brianj-desktop:~$ s710sh -d ir /dev/ircomm0

s710sh> get files

Reading [    0 bytes] [                                        ] [  0.0%]
get files: No response

[error]

s710sh> 


```

Anyway, thanks for all the assistance.  Will post here if the crash issue arises again.  I will post a new thread if I get s710 working with this device.

---

### Post by zebrankyza on 2007-11-28
I spoke too soon :(

Here's how I can get my machine to lock:
[LIST=1]
[*]Install the USB Device as per this thread.
[*]Execute sudo /etc/init.d/irda-utils restart.
[*]Execute sudo modprobe ircomm-tty.
[*]Execute **sudo** s710sh -d ir /dev/ircomm0.
[*]Set my HRM to "Connect" mode.
[*]Initiate a 'get users' command in s710.
[/LIST]

It appears that as soon as I use sudo to launch s710 that my problems start.  It is a little erratic though, sometimes locks on the first attempt, sometimes later, but still returns "No reponse" if it does not lock.  Will see if I can get any further.

Someone on a [link I posted previously]("http://code.google.com/p/s710/issues/detail?id=4") did [mention this about the 'i' Series Polar HRM vs non 'i']("http://www.alanjmcf.me.uk/comms/infrared/IrDA%20faq.html#_Toc128227619").

---

### Post by regne v on 2007-11-29
> **zebrankyza said:**
> It appears that as soon as I use sudo to launch s710 that my problems start.  It is a little erratic though, sometimes locks on the first attempt, sometimes later, but still returns "No reponse" if it does not lock.  Will see if I can get any further.
As I said in a previous post I didn't get s710 to work, but the computer never freezed. The only thing I could get was the "no response" command and the configuration of the watch becaming a complete mess.

I use Polar personal trainer from a vmware virtual machine and everything works fine. Could you try to communicate with another infrared device to test if the problem is s710 related?.

---

### Post by zebrankyza on 2007-12-03
> **regne v said:**
> As I said in a previous post I didn't get s710 to work, but the computer never freezed. The only thing I could get was the "no response" command and the configuration of the watch becaming a complete mess.

I use Polar personal trainer from a vmware virtual machine and everything works fine. Could you try to communicate with another infrared device to test if the problem is s710 related?.

Thanks Regne V, I have chosen the same route as you and installed WinXP in a VirtualBox instance and using the IrDA through that just fine.  I am not sure why the s710 is giving issues, but for now I'll just use the VM.

---

### Post by dabb1er on 2007-12-03
Can you tell me how you got the Polar USB interface working in Gutsy?

---

### Post by regne v on 2007-12-04
> **dabb1er said:**
> Can you tell me how you got the Polar USB interface working in Gutsy?

Em... am I missing something?. I just followed the instructions I wrote for Feisty in the first post of this thread. They're just the same for gutsy.

---

### Post by brad103 on 2007-12-05
This thread was very helpful and in the end I did manage to get my phone accessible with this chipset. One thing I found was that if I booted with the dongle plugged in, I then had to remove and reinsert it and/or restart irda-utils. I wrote a script to get some of the connecting happening automatically [over here]("http://waxingcerebral.blogspot.com/2007/12/get-connected-with-infrared-device-in.html").

Cheers!

---

### Post by xyoung on 2007-12-08
How configure you vmware?? I have configured irda-utils and all work fine but the polar aplication in windows xp over vmware don't detect nothing.

Regards and thanks.

---

### Post by regne v on 2007-12-09
> **xyoung said:**
> How configure you vmware?? I have configured irda-utils and all work fine but the polar aplication in windows xp over vmware don't detect nothing.
You have to connect the usb dongle with the virtual machine: Once the virtual machine is up and running go to the virtual machine menu VM/Removable Devices/USB Devices and choose "SigmaTel Inc, STIr 42xx".

If  the USB Devices menu is empty, please follow [this thread]("http://ubuntuforums.org/showthread.php?t=588225") to enable usbfs support in gutsy.

You can also find [here]("http://ubuntuforums.org/showthread.php?t=591732") a very good thread with tutorials and problems regarding VmWare and Gutsy.

---

### Post by xyoung on 2007-12-11
Thank you very much regne v, you're the best.

My vmware menu was empty and your solution solved the problem.

Thx
Good bye.

---

### Post by jonssoni on 2007-12-13
Ok, I tried to get Polar Precision Power SW + Polar ir-dongle (usb) to work but I didn't succeed.
First I installed VMware and Polar program, Polar usb dongle shows up in the Devices menu but it doesn't work with the PPP SW. I have Polar S625X.

Instead, I managed to find a software for Polar + Ubuntu, now I don't even need VMware.

1. Install SportsTracker. (very easy to install and to use)

[http://www.saring.de/sportstracker/](http://www.saring.de/sportstracker/)

2. Install the S710 code. Instructions are in the package. (readme / install)

[http://code.google.com/p/s710/](http://code.google.com/p/s710/)

3. Transfer files from your clock to your computer and open them with SportsTracker. (check out from the s710 readme how to transfer files)

---

### Post by regne v on 2007-12-14
> **jonssoni said:**
> Ok, I tried to get Polar Precision Power SW +** Polar ir-dongle (usb)** to work but I didn't succeed

Do you have the [Polar IrDA USB Adapter]("http://support.polar.fi/PKBSupport.nsf/OldProduct/IrDAUSBAdapter?openForm") or the [Polar IR Interface USB]("http://support.polar.fi/PKBSupport.nsf/OldProduct/IRInterfaceUSB?openForm")?

I had no luck at all with s710 and my guess is that it is not compatible with the Polar IrDA USB Adapter that I own.

---

### Post by jonssoni on 2007-12-15
> **regne v said:**
> Do you have the [Polar IrDA USB Adapter]("http://support.polar.fi/PKBSupport.nsf/OldProduct/IrDAUSBAdapter?openForm") or the [Polar IR Interface USB]("http://support.polar.fi/PKBSupport.nsf/OldProduct/IRInterfaceUSB?openForm")?

I had no luck at all with s710 and my guess is that it is not compatible with the Polar IrDA USB Adapter that I own.

I've got the second one, Polar Ir interface USB adapter, so that might be the reason.

---

### Post by johankunnen on 2008-03-24
Thanks to all of you. With the help of this thread I managed to transfer data from my Siemens ME75 to my computer and vise versa. 

However my most important goal was to connect to my polar s725x and that still does not work.

I am running Ubuntu gutsy with and I use the two kernel patches from the sigmatel site ([www.sigmatell.com](www.sigmatell.com)) as described earlier in this thread. I use a SigmaTel, Inc. STIr4210 IrDA Bridge (polar usb device) to connect to my polar or phone,

With irdadump I manage to see my mobile phone. By using sudo obexfs -i /media/phone I am even able to exchange data between my phone and my computer.

As soon as I do irdadump with my polar in connect mode near the dongle my system hangs completely !

I can start the s710 deamon by sudo s710d -d ir /dev/ircomm0 without problems. As soon as my polar is connecting the system hangs again.

I read that more people ran into hanging systems, but I did not find a solution. Does anyone have a suggestion ?

---

### Post by regne v on 2008-03-25
> **johankunnen said:**
> As soon as I do irdadump with my polar in connect mode near the dongle my system hangs completely !

Are you sure your system hangs?. I mean, probably the USB bus is not working and if keyboard and mouse are plugged through it you might think that the whole system is hung.

Please run a background application (a music player, a movie, anything) and while it is playing try to access the device. If the system "hangs" but the background application keeps playing then is just the USB bus who has stopped working. Unplug all USB devices, plug keyboard and mouse and test if they are working again.

I've seen this behaviour with bad usb cables.

---

### Post by johankunnen on 2008-03-26
I was actually running rythmbox when I tried the connection and indeed the music stopped playing. Both my keyboard and my mouse are of the more old fashioned types, so no usb. They stopped working as well. 

My irda device is connected via a usb hub of in my monitor. Maybe I should try to plug it directly into the computer. It is worth a try,

---

### Post by regne v on 2008-03-26
> **johankunnen said:**
> I was actually running rythmbox when I tried the connection and indeed the music stopped playing. Both my keyboard and my mouse are of the more old fashioned types, so no usb. They stopped working as well. 

My irda device is connected via a usb hub of in my monitor. Maybe I should try to plug it directly into the computer. It is worth a try,

Try also to press ALT-F1 and start s710d in a text mode terminal. Post here any kernel error that might show in the screen when the system hangs.

---

### Post by johankunnen on 2008-03-26
Ok, I did another test. I connected the irda device with a solid looking cable directly to the computer, 

I performed a sudo ```
/etc/init.d/irda-utils restart
``` to discover the device. Then I did a ```
sudo irdadump
``` and tried to connect the polar.

It showed among others:
```
21:25:18.233471 xid:rsp f5485e63 < 4802e5ad S=6 s=3 Polar S725X hint=8204 [ PDA/Palmtop IrCOMM ] (28)
```

So far so good. I did not see this before. Then I started the s710 deamon and tried to connect to the polar again. Unfortunately it hung again ! Rythmbox acted as if it was an old fashioned LP and both the capslock and the numlock where blinking.

---

### Post by johankunnen on 2008-03-26
I found some information in /var/log/messages. Maybe this is useful.
```
Mar 26 22:22:02 apollo kernel: [ 6712.992083] usb 2-5: new high speed USB device using ehci_hcd and address 4
Mar 26 22:22:03 apollo kernel: [ 6713.125033] usb 2-5: configuration #1 chosen from 1 choice
Mar 26 22:22:03 apollo kernel: [ 6713.199026] IRDA-USB found at address 4, Vendor: 66f, Product: 4210
Mar 26 22:22:03 apollo kernel: [ 6713.209983] IrDA: Registered device irda0
Mar 26 22:22:03 apollo kernel: [ 6713.230762] stir421x_patch_device(): Received firmware 42101002.sb (1687 bytes)
Mar 26 22:22:03 apollo kernel: [ 6713.251646] usbcore: registered new interface driver irda-usb
Mar 26 22:22:03 apollo kernel: [ 6713.251651] USB IrDA support registered
Mar 26 22:23:19 apollo irattach: executing: '/sbin/modprobe irda0'
Mar 26 22:23:19 apollo irattach: + FATAL: Module irda0 not found.
Mar 26 22:23:19 apollo irattach: Trying to load module irda0 exited with status 1
Mar 26 22:23:19 apollo irattach: executing: 'echo apollo > /proc/sys/net/irda/devname'
Mar 26 22:23:19 apollo irattach: executing: 'echo 1 > /proc/sys/net/irda/discovery'
Mar 26 22:23:19 apollo irattach: Starting device irda0
Mar 26 22:28:26 apollo kernel: [ 7095.528083] IrCOMM protocol (Dag Brattli)
Mar 26 22:30:16 apollo s710d[8592]: started
Mar 26 22:30:54 apollo kernel: [ 7244.185890] NETDEV WATCHDOG: irda0: transmit timed out
Mar 26 22:30:55 apollo kernel: [ 7245.184300] NETDEV WATCHDOG: irda0: transmit timed out
Mar 26 22:30:55 apollo kernel: [ 7245.184319] irda_usb_change_speed_xbofs(), URB still in use!
Mar 26 22:32:16 apollo syslogd 1.4.1#21ubuntu3: restart.

```

---

### Post by johankunnen on 2008-03-26
I pressed CTRL ALT F11, logged in as root and started the deamon. This resulted into a kernel panic and a lot of memory addresses.

---

### Post by regne v on 2008-03-27
> **johankunnen said:**
> I pressed CTRL ALT F11, logged in as root and started the deamon. This resulted into a kernel panic and a lot of memory addresses.
I've been googling a bit and it seems that the "NETDEV WATCHDOG" message is the key.

Most people suggest [disabling APIC and/or ACPI]("http://ubuntuforums.org/showthread.php?t=11501").

---

