---
title: "Having trouble setting up wireless adapter"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Trafficflow on 2009-03-11
Alright . I have worked on computers my whole life and now I can not open a program on my jump drive. I understand this is going to be different but what am I not understanding.

---

### Post by linuxuser21 on 2009-03-11
What happens when you try to open it?

---

### Post by iitywygms on 2009-03-11
what program?

---

### Post by mhgsys on 2009-03-11
lol.
I don't even understand your question.

---

### Post by Trafficflow on 2009-03-11
I have a executable file to load my wireless adapter for internet connection

---

### Post by kidux on 2009-03-11
> **mhgsys said:**
> lol.
I don't even understand your question.
What I get is that he just switched to Linux, and is trying to run a Windows program from his jump drive.

---

### Post by iitywygms on 2009-03-11
a windows executable?

---

### Post by mhgsys on 2009-03-11
lol 

now I get it.. 

windows exe / drivers won't work on ubuntu.

---

### Post by kidux on 2009-03-11
> **Trafficflow said:**
> I have a executable file to load my wireless adapter for internet connection
.exe files won't work in Linux. They are Windows only. If you have internet via copper wire, then go into Restricted Drivers, enable the wireless driver which will probably download the driver if it's not already present. If that doesn't work, you'll need to look into ndiswrapper or madwifi, both of which have multiple tutorials if you do a search for them here or on Google.

---

### Post by Trafficflow on 2009-03-11
Yes a windows executable. Yes I just made the switch.

---

### Post by jflaker on 2009-03-11
Linux doesn't run Windows .exe files natively.  

If this is drivers, it is likely that your wireless already works without those drivers....Have you tried to see your wireless connection?

---

### Post by linuxuser21 on 2009-03-11
Is it the software that came with the wireless card or something?

---

### Post by mkvnmtr on 2009-03-11
Explain what you want to do and someone will probably be able to tell you how to do it. If it is install a driver for your wireles a windows file only works on windows. You might check in hardware drivers and find one for Ubuntu that you can download and install by clicking on enable.

---

### Post by Locke_99GS on 2009-03-11
> **kidux said:**
>  If that doesn't work, you'll need to look into ndiswrapper or madwifi, 

Or if he's using an Atheros wireless adapter, using the backported ath5k kernel module.

---

### Post by kidux on 2009-03-11
> **Locke_99GS said:**
> Or if he's using an Atheros wireless adapter, using the backported ath5k kernel module.
Good one, forgot about that one.

---

### Post by Trafficflow on 2009-03-11
I do not see anything under network. I have it plugged in usb.I have been using help and it tells me to put a command in. I need to read up. Am I on the right track

---

### Post by cariboo on 2009-03-11
To show us the details of your network device, becuase you haven't given us any details, open an Applictions-->Accessories-->Terminal and type:

```
sudo lshw -C network > network.txt
```

This will create a text file called network.txt that you can transfer to the computer you have internat access on and paste the result in you next post.

Just a note, just because you have been working with windows computers all your life,  doesn't mean that any skills you have transfer to other operating systems

Jim

---

### Post by lindsay7 on 2009-03-11
There is an icon on the top menu bar that will indicate if you a connceted to the internet and show the wireless signals that the card is picking up if it is working. If your wirless card or adaptor works with Ubuntu, you do not need to do anything (no drivers to load). If it is not working. You can look for threads  to help you. Please list the maker and model of adaptor you are using and someone will try to help you. Also go to system/preferences/network configuration, this is where you setup the network security, etc.

---

### Post by Trafficflow on 2009-03-11
I understand about the different OS. I remeber dos from years ago. Thanks for the start. Once I get online i will be  able to start learning. Will be back in a few days after I do some research.

---

### Post by Trafficflow on 2009-03-14
I need some help.I have been reading but I am still not there.I  typed in the sudo command in a terminal window and do not get any info.I take it I need some drivers. In the driver window nothing is there. I found the window for wired or wireless. I can not get it off the wired window. Can somebody guide me in the right direction. Thanks

---

### Post by Trafficflow on 2009-03-14
I have a netgear wg111t adapter and a wgt624 router.Can somebody help??

---

### Post by RetchingRabbit on 2009-03-14
Open a terminal and enter the following:

```
sudo lshw -C network
```


And post the resulting output back here. This will allow us to know what kind of hardware you have.

---

### Post by Trafficflow on 2009-03-15
Pardon me I am attempting to learn this os. Does sudo mean password?

---

### Post by ALIENDUDE5300 on 2009-03-15
sudo allows you to run files as the 'super user', or 'root'. as a regular user, you aren't given direct access to make changes to settings. This is a security measure that windows should have. however, if you want to "become root", you can run sudo passwd to change the password for the root account, then switch user with su. otherwise, you can just use sudo to execute commands as the super user. for most functionality you will NOT need to be root. mostly just for package management or system maintenance.

---

### Post by ALIENDUDE5300 on 2009-03-15
Also, you are simply trying to run an exe file? For many exe files that do not have Ubuntu alternatives available, you can simply use Wine. Wine is not an emulator for Windows, but instead it is a compatibility layer which allows windows executables to be run natively within windows. For more information about Wine, you can see [http://winehq.org/](http://winehq.org/)

---

### Post by RetchingRabbit on 2009-03-15
> **RetchingRabbit said:**
> Open a terminal and enter the following:

```
sudo lshw -C network
```


And post the resulting output back here. This will allow us to know what kind of hardware you have.

See above.

---

### Post by ed89 on 2009-03-15
> **Trafficflow said:**
> I need some help.I have been reading but I am still not there.I  typed in the sudo command in a terminal window and do not get any info.I take it I need some drivers. In the driver window nothing is there. I found the window for wired or wireless. I can not get it off the wired window. Can somebody guide me in the right direction. Thanks

Try this:

Applications > Accessories > Terminal
Type in the following: ```
sudo lshw -C network > network.txt
```
You will be prompted for your password - type in the password you chose and press ENTER.
Wait until Terminal has done it's work, and it says you@your-laptop again.
Exit Terminal.

Click Places > Home Folder.
Open "network.txt"

---

### Post by lisati on 2009-03-15
> **mhgsys said:**
> lol 

now I get it.. 

windows exe / drivers won't work on ubuntu.
At least not without help....
> **ed89 said:**
> 
You will be prompted for your password - type in the password you chose and press ENTER.

Don't worry if your password doesn't show as you type: this is normal...

---

### Post by lisati on 2009-03-15
> **Trafficflow said:**
> I have a netgear wg111t adapter and a wgt624 router.Can somebody help??

I recall reading somewhere on these forums about getting the wg111t adapter (or similar) working....... it can be done.

---

### Post by teamcoltra on 2009-03-15
I am going to post a clear how-to for you here, this is simply a mashup of above, but will assist us in aiding you further:

Please go to the top left (by default) of your screen and click: Applications > Accessories > Terminal
Type in the following: ```
sudo lshw -C network > network.txt
```
You will be prompted for your password - type in the password that is linked to your user. Your password WILL NOT DISPLAY as you are typing it (sorry no *******), so just type it out, and click enter.. it will work.

Wait until Terminal has done it's work, and it says you@your-laptop again (or whatever it says mine is teamcoltra@geeksparadox-desktop:~$)
Exit Terminal.

Now right next to appliactions Click Places > Home Folder.
Open "network.txt" and please paste it here.


**NEXT**
After you get your internet up and going, you may be able to open some windows appliacations by using a program previously mentioned called WINE I believe it stands for Windows I-something N-something Emumlator, this will not make you open a virtual box but still allow you to run windows programs from Ubuntu, its a really great app especally if you like playing a few games from windows.

However, when it comes to driver instalation, this will not help you and you are going to want to do the above steps.


The driver list in ubuntu is crazy extensive, I have no doubt we can assist you.

---

### Post by Trafficflow on 2009-03-15
I hope  this is what you need Thanks




  *-network
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:b8:11:0a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

---

### Post by cariboo on 2009-03-15
The driver for your network card is already loaded, you should be able to connect. Open a Applications-->Accessories-->Termianl and type:

```
ifconfig
```

the above command is the equivalent to the Windows ipconfig command, you should get a result something like this:

```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:9c:84:b5  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe9c:84b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:190273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:238882079 (238.8 MB)  TX bytes:34794860 (34.7 MB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:427368 (427.3 KB)  TX bytes:427368 (427.3 KB)
```

If you aren't getting an ip address in the same terminal type:

```
sudo dhclient eth0
```

This should hopefully get you an ip address

Jim

---

### Post by Trafficflow on 2009-03-15
I can get a wire connection but no wireless with my adapter.That info that is displayed is for wired correct?

---

### Post by Cresho on 2009-03-15
Lets simplify this a bit.

up in the right hand corner, you will come accross a network manager or wired network connection.  left click will give you your network access devices  which in my case is a wired and a wireless stating 2 networks I can access.  if you right click on that network icon, you can enable and disable devices.  see if you have a "wired connection" and a "wireless connection"

If not, then I assume your drivers are not installed.

now go to system->administration->"Hardware drivers" and look to see if you can enable a proprietary driver.  then reboot and use the icon again from the right hand corner which is the network manager.

---

### Post by Trafficflow on 2009-03-15
No connection when I click on icon. No drivers installed. Also wired mode enabled.I been looking online for drivers .No luck on the install

---

### Post by Trafficflow on 2009-03-15
Can somebody tell me drivers i need for a Wg111t and how to install. I tried earlier but could not figure out the install. I will use tomorrow. Thanks and good night

---

### Post by Cresho on 2009-03-15
did you look at the administration, hardware drivers list?  is there any?

---

### Post by 3rdalbum on 2009-03-15
Looks like Ubuntu can't see the adapter; odd. With that card, you should have had an entry in the Hardware Drivers program for "Atheros Wireless".

Can you please make sure for us that the adapter is plugged in and turned on? If it is plugged into a hub, please plug it straight into the computer instead.

Also, the output of the command "lsusb" would help.

---

### Post by Cresho on 2009-03-15
follow this thread.  it is old.  If I had your pc infront, its easy to install.

[http://ubuntuforums.org/showthread.php?t=258732](http://ubuntuforums.org/showthread.php?t=258732)

---

### Post by Trafficflow on 2009-03-15
I am still having trouble getting the wireless to work. I m online thru the wired connection. I downloaded the fdis app.Should that show up in the drivers. When I tried install it ask for inf file but there was none in the folder. I am doing a buch of reading on diff topics but no luck on the wireless. when I go to network connections everything is gray. I know this simple but once I get over the hump I will start figuring this Ubunta out somehow. Thanks Trying but no Luck

---

### Post by Locke_99GS on 2009-03-16
Drivers in Linux are usually in the form of kernel modules - they plug in to the kernel, and aren't quite the same as the Windows drivers you are used to. This is why you are not finding them when you search for them on the internet, they aren't available.

You say you are using a USB wifi adapter, we need to know what chipset it is using. Open a terminal with the device inserted, as you have done before, and type:

```

lsusb

```

That will list all USB devices attached to your machine - post the part containing your WiFi dongle's information. If you don't understand the output, just post all of it's output.

And just to see what the kernel thinks is going on, remove the USB dongle, wait a couple of seconds, and re-insert it. Then, post the last 10-15 line from the output of this command:

```

dmesg

```

This should give us enough information to provide you with guided assistance.

---

### Post by Trafficflow on 2009-03-17
Okay I did a reload  to start over. Maybe somebody can guide me thru installing the wireless adapter. I have did the update first. There is no drivers loadesd. There ia alot of advice from previous post and I am not sure because there is no drivers unless they are hidden. Any advice? Thanks

---

### Post by Locke_99GS on 2009-03-19
See post 41 - it still applies.

---

### Post by issih on 2009-03-19
First I point you here:

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)

If that advice is no good then as has been said several times. we need to know the chipset of your device, not the model number or anything simple like that, the chipset.

Assuming that when you ran:

```
lshw -C network
```

you did it whilst the dongle was plugged into the copmter, then we have to go more low level. I think you stated it was a usb dongle, so with it plugged in please post the output of :

```
lsusb
```

when run in a terminal.

Once we have that we can advise you what method/driver to install to get the wireless functioning.

Without that the best we can do is

---

### Post by mikewhatever on 2009-03-19
I can't believe it that you Can Not Believe IT. ;)

Just wanted to participate in this very valuable thread.

---

### Post by sdowney717 on 2009-03-19
a wg111t will work with linux
this link shows you how
It will use ndiswrapper which can use windows drivers

[http://www.debianadmin.com/netgear-wg111t-working-with-debian-etch-and-lenny.html](http://www.debianadmin.com/netgear-wg111t-working-with-debian-etch-and-lenny.html)

It might be easier than the above by following this below
Do you have an entry under menu
system -administration- windows wireless drivers?

this should be there and is using ndiswrraper
You need the *.inf for the device

In the exe file the inf file is stored. You might need to extract this file out of the exe file

[http://www.linux-archive.org/gentoo-user/27975-extracting-xp-drivers-exe.html](http://www.linux-archive.org/gentoo-user/27975-extracting-xp-drivers-exe.html)

so perhaps you can cabextract this or you might need to run the file on a windows box to get the inf file.
or perhaps you might be able to download the inf file.

---

### Post by Trafficflow on 2009-03-21
Okay here is the info on my install of Ubunta. Been out of town. Did a update with a wired hookup. I have been reading and I know a lot more than last week.

Bus 004 Device 002: ID 1385:4251 Netgear, Inc 

Bus 004 Device 002: ID 1385:4251 Netgear, Inc 

trafficflow@trafficflow-desktop:~$ lusb
bash: lusb: command not found
trafficflow@trafficflow-desktop:~$ lsusb
Bus 004 Device 002: ID 1385:4251 Netgear, Inc 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 001 Device 001: ID 0000:0000 

This the network
  *-network
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:b8:11:0a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

This is dmesg
[   41.286269] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   41.286284] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   41.286366] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  129.404080] NET: Registered protocol family 10
[  129.404568] lo: Disabled Privacy Extensions
[  129.405358] ADDRCONF(NETDEV_UP): eth0: link is not ready
[13074.968449] usb 4-1: USB disconnect, address 2
[13103.979323] usb 4-1: new high speed USB device using ehci_hcd and address 4
[13104.112725] usb 4-1: configuration #1 chosen from 1 choice

I hope this what you need.  Thanks

---

### Post by halitech on 2009-03-22
check here: [https://help.ubuntu.com/community/WifiDocs/Device/WG111T](https://help.ubuntu.com/community/WifiDocs/Device/WG111T)

and here: [http://garethrwhite.wordpress.com/2009/02/05/netgear-wg111t-ubuntu/](http://garethrwhite.wordpress.com/2009/02/05/netgear-wg111t-ubuntu/)

either of these should get you going

---

### Post by Trafficflow on 2009-03-22
Well I finally was able to install the wireless adaters using the last comment from the netgear site. The light is blinking and i have enabled the wireless connection. Do I need to do a configuration? I have the name and the key in. I sure learned a lot this week. I did a update. Maybe a mistake 270 updates. Oh well. Thanks everybody. Need to do more reading

---

