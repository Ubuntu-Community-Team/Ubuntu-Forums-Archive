---
title: "Fresh install and laptop wireless is not working"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by pandaking on 2007-04-06
Hello there

So I have installed ubuntu on my laptop! And it rocks! Everything is where you expect it to be, set how you want it to be and I am still amazed because by battery life has nearly doubled. Not to mention how much faster it's now running.

So firstly - VERY IMPRESSED!

I have encountered a quite significant problem though, my wireless network card isn't working (probably me being nooby).
As you can guess I am a noob to ubuntu so I need your help.

I found this site which has some good info on the laptop: [http://www.uktsupport.co.uk/advent/laptop/7040.htm](http://www.uktsupport.co.uk/advent/laptop/7040.htm)
It says my wireless card is a "Intel Pro 2100 wireless LAN".

If I go into device manager, then I can see my wireless card with that very name.

Also, if I click System -> Administration -> Netwroking, then in the connections tab it shows "wireless conenction" not configured.
If I click properties on it, it asks for an essid among other things.

Also, there are 3 buttons next to the power button on this laptop. The first used to turn wireless internet on or off, and the other two labeled "P1" and P2" you could customise to open applications or whatever.
I am not bothered about those two, but it would be so sweet if I could get the first wireless one to work as well.

The supported card list shows that this should natively work, but I can't work it out for the life of me.
It's like the card is disabled by the button, so I can't ever connect...

So there is my problem, and I really hope it is fixable, as I have fallen in love with this system now.
I still can't get over just how simple it all is lol. What have windows been doing...

---

### Post by chili555 on 2007-04-06
Let's try a thing or two to see if your card is on or off, if it is alive as a result of drivers being loaded, and finally connect. First, open a terminal and type:```
iwconfig
```A lot of text will spit out and several interfaces will be shown with 'no wireless extensions' but one may show lots of data next to it. That will be your wireless interface. It may be eth1 or wlan0 or wifi0 or otherwise. For now, let's guess it's eth1.

Do another command:```
iwlist eth1 scan
```Substitute your wireless interface here. Post the result here. Thanks.

---

### Post by siefer132 on 2007-04-06
i think i might also need help with this thing, heres a scrnshot of the results.

---

### Post by chili555 on 2007-04-06
Which one is your access point? I see all four have encryption turned on. WEP or WPA? Looks like "Do Not Connect" is the closest and uses WPA.

---

### Post by siefer132 on 2007-04-06
yea, lol, mine is do not connect

---

### Post by pandaking on 2007-04-07
> **chili555 said:**
> Let's try a thing or two to see if your card is on or off, if it is alive as a result of drivers being loaded, and finally connect. First, open a terminal and type:```
iwconfig
```A lot of text will spit out and several interfaces will be shown with 'no wireless extensions' but one may show lots of data next to it. That will be your wireless interface. It may be eth1 or wlan0 or wifi0 or otherwise. For now, let's guess it's eth1.

Do another command:```
iwlist eth1 scan
```Substitute your wireless interface here. Post the result here. Thanks.

Thank you very much for getting back to me :)

This is what I got:

[[IMG]http://img72.imageshack.us/img72/5161/screenshot1ff7.th.png[/IMG]](http://img72.imageshack.us/my.php?image=screenshot1ff7.png)

---

### Post by pandaking on 2007-04-08
Anyone? Thanks...

---

### Post by skip27 on 2007-04-08
Hi,

Edit your post if you can. You said "here's what I got" but there's nothing underneath. Also, type "sudo lshw -class network" and post the output if you don't mind.


**WHAT THIS MEANS:**

lshw is the command to (L)i(S)t (H)ard(W)are. The -class parameter tells the program you are looking for a specific type of hardware, and the 'network' modifier says that you want it to cherrypick out the class of hardare pertaining to the network. As you probably already know, 'ls' is the basic command to list anything in a directory. You'll soon learn that 'ls' precedes many commands, such as lsusb, lspci, and lspcmcia. lshw is yet another one.

---

### Post by pandaking on 2007-04-08
Hi sorry, I posted a pic but it's not showing anymore. I think imageshack is down.

Here is what it contained:
[http://www.b3ta.cr3ation.co.uk/data/png/screenshot1.png]("http://www.b3ta.cr3ation.co.uk/data/png/screenshot1.png")

or

```
andy@andy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

andy@andy-laptop:~$ iwlist eth1 scan
eth1      No scan results
andy@andy-laptop:~$ 
andy@andy-laptop:~$ 

```



This is the results of what you told me to type:
(thanks for the extra info btw :) )

```
andy@andy-laptop:~$ sudo lshw -class network
Password:
  *-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth1
       version: 04
       serial: 00:04:23:77:28:85
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 link=no multicast=yes wireless=unassociated
       resources: iomemory:e0200000-e0200fff irq:10
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@02:05.0
       logical name: eth0
       version: 10
       serial: 00:40:ca:c5:3f:16
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:3000-30ff iomemory:e0201800-e02018ff irq:10

```

Thanks very much! :D

---

### Post by skip27 on 2007-04-08
Excellent! As I had suspected. Your wireless interface is DISABLED, as indicated by lshw. There is a simple fix for this.

sudo ifconfig eth1 up

The generic format for this command is:

sudo ifconfig <interface> up/down

'man ifconfig' for more details. The man pages are an excellent way to find information about certain commands. Use 'man <command>' in the future for reference.

ifconfig is used to configure network interfaces in general. iwconfig is specifically tailored for wireless connections, and is the command we will use next...

Now configure your interface using iwconfig. This should get you started:

iwconfig eth1 essid <essid>

---

### Post by The Dan of Steel on 2007-04-08
> **skip27 said:**
> Excellent! As I had suspected. Your wireless interface is DISABLED, as indicated by lshw. There is a simple fix for this.

sudo ifconfig eth1 up

The generic format for this command is:

sudo ifconfig <interface> up/down

'man ifconfig' for more details. The man pages are an excellent way to find information about certain commands. Use 'man <command>' in the future for reference.

ifconfig is used to configure network interfaces in general. iwconfig is specifically tailored for wireless connections, and is the command we will use next...

Now configure your interface using iwconfig. This should get you started:

iwconfig eth1 essid <essid>

I am also having the same issue. I tried everything that was said so far and I got to this point. Now after I try the 'sudo ifconfig' command to turn on the wireless card I get: 

SCIOCSIFFLAGS: No such file or directory

Thanks so much for all your knowledge.

---

### Post by skip27 on 2007-04-08
Hi The Dan of Steel,

It seems that you are using the incorrect alias for your network card. After doing a 'lshw -class network,' you need to locate the part where it says "logical name: <name>". It should be something like wlan0 or eth0. Only then can you invoke sudo ifconfig <name> up. Since everyone's configuration is different, someone else's eth1 might be your eth0.

Let me know if this helps.

Also, though I would *strongly* encourage you to use the CLI (command line interface) to configure your network--since it will help familiarize yourself with Linux better--you may use the Gnome networking tool to simplify this process. There should be an icon in your system tray that you can simply right-click and configure from there.

---

### Post by pandaking on 2007-04-08
> **skip27 said:**
> Excellent! As I had suspected. Your wireless interface is DISABLED, as indicated by lshw. There is a simple fix for this.

sudo ifconfig eth1 up

The generic format for this command is:

sudo ifconfig <interface> up/down

'man ifconfig' for more details. The man pages are an excellent way to find information about certain commands. Use 'man <command>' in the future for reference.

ifconfig is used to configure network interfaces in general. iwconfig is specifically tailored for wireless connections, and is the command we will use next...

Now configure your interface using iwconfig. This should get you started:

iwconfig eth1 essid <essid>

If I type the first command in, it asks for my password. If I type it in, nothing is displayed but when I hit enter it seems to accept it.
Once I have hit enter though it is awaiting my next command.

I would like to be able to use the networking tools that are provided with ubuntu, but if I click the network connection in the top tray only "lo" is available still. I can't search for wireless signals around me.

If I type in the essid command, what do I type in the essid part? How can I search for wireless networks if I need the network name to connect to them?

Of course I know what my one at home is called, but if I type it in with that command you gave me, it says:

```
Error for wireless request "Set ESSID" (8B1A) :
           SET failed on device eth1 ; Operation not permitted.
```

I really know nothing here, but surely the light on my laptop which used to tell me wireless was on, should be lit? And for it to be lit does the wireless button not need to work?

Thanks again...

---

### Post by The Dan of Steel on 2007-04-08
Thanks all for replying, however I am getting all the same results as pandaking until the ifconfig part. Where mine too is eth1. However like I said above it won't work. Mine is a Broadcom BCM4306. Is there a known issue with this device?

I like using terminal. I am fairly familiar with the inner workings of Windows and Mac OSs. I work as a Network Technician for a small company and some of the engineers prefer Linux to well...anything. So to not only quench my own curiosity but to further my job oppurtunities I would love to learn Ubuntu. However I need to be able to get this to work on my home PC first so I can play around with it.

Thanks again.

---

### Post by skip27 on 2007-04-08
> **pandaking said:**
> If I type the first command in, it asks for my password. If I type it in, nothing is displayed but when I hit enter it seems to accept it.
Once I have hit enter though it is awaiting my next command.


That's how it should be. If you repeat the 'lshw -class network' command, 'DISABLED' next to your wireless networking device should be gone.

> 
I would like to be able to use the networking tools that are provided with ubuntu, but if I click the network connection in the top tray only "lo" is available still. I can't search for wireless signals around me.

If I type in the essid command, what do I type in the essid part? How can I search for wireless networks if I need the network name to connect to them?


Use 'iwlist eth1 scan'

> 
Of course I know what my one at home is called, but if I type it in with that command you gave me, it says:

```
Error for wireless request "Set ESSID" (8B1A) :
           SET failed on device eth1 ; Operation not permitted.
```

I really know nothing here, but surely the light on my laptop which used to tell me wireless was on, should be lit? And for it to be lit does the wireless button not need to work?

Thanks again...

Sorry, I should have said 'sudo iwconfig eth1 essid <your essid>'. Also, depending on the drivers you are using, the wireless lights may or may not go on. Generally speaking, the lights are not indicative of whether or not your hardware is actually working. So, depending on your setup, you may have a functional wireless conection despite the lights not being on.

---

### Post by skip27 on 2007-04-09
> **The Dan of Steel said:**
> Thanks all for replying, however I am getting all the same results as pandaking until the ifconfig part. Where mine too is eth1. However like I said above it won't work. Mine is a Broadcom BCM4306. Is there a known issue with this device?


Ah, I'm glad you mentioned this. I also have a Broadcom BCM4306, so you're actually quite lucky :). I'm going to recommend using ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

There is also another way to get this working using the native drivers, but they tend to limit the functionality of the hardware. Let me know if this works for you.

---

### Post by pandaking on 2007-04-09
Wow thanks for all the help skip!
I had a feeling that password thing was meant to happen just wanted to check.

So I do the:```
sudo ifconfig eth1 up
``` to enable the device, then the search for wireless networks using ```
'iwlist eth1 scan'
```
and then i put the essid of the one I want to connect into:```
'sudo iwconfig eth1 essid <your essid>'
```

That makes sense, only problem is when I do the search command it says:
```
eth1     No scan results
```

:confused:

---

### Post by siefer132 on 2007-04-09
heres what i got with the thing u said to type...(attached)

---

### Post by skip27 on 2007-04-09
> **pandaking said:**
> Wow thanks for all the help skip!
I had a feeling that password thing was meant to happen just wanted to check.

So I do the:```
sudo ifconfig eth1 up
``` to enable the device, then the search for wireless networks using ```
'iwlist eth1 scan'
```
and then i put the essid of the one I want to connect into:```
'sudo iwconfig eth1 essid <your essid>'
```

That makes sense, only problem is when I do the search command it says:
```
eth1     No scan results
```

:confused:

What does 'sudo iwconfig eth1' say? Also, make sure the 'ipw2100' module is loaded. Type 'lsmod | grep ipw' and it should show up. If it does not, type 'sudo modprobe ipw2100' and then try to set your essid.

---

### Post by skip27 on 2007-04-09
> **siefer132 said:**
> heres what i got with the thing u said to type...(attached)

Hmm... everything appears as it should. Could you point out the problem for me?

---

### Post by pandaking on 2007-04-09
> **skip27 said:**
> What does 'sudo iwconfig eth1' say? Also, make sure the 'ipw2100' module is loaded. Type 'lsmod | grep ipw' and it should show up. If it does not, type 'sudo modprobe ipw2100' and then try to set your essid.


Here we go:

```
andy@andy-laptop:~$ sudo ifconfig eth1 up
Password:

andy@andy-laptop:~$ iwlist eth1 scan
eth1      No scan results

andy@andy-laptop:~$ sudo iwconfig eth1
eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

andy@andy-laptop:~$ lsmod | grep ipw
ipw2100                75828  0 
ieee80211              35272  1 ipw2100

andy@andy-laptop:~$ sudo iwconfig eth1 essid swanbarn

andy@andy-laptop:~$ sudo iwconfig eth1
eth1      unassociated  ESSID:"swanbarn"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by skip27 on 2007-04-09
Found the problem. Examine the first line of the output:

```

eth1      unassociated  ESSID:"swanbarn"  Nickname:"ipw2100"

```

It shouldn't be printing 'unassociated.' It should be printing something like IEEE 802.11g.

At this point, I suspect it has to do with a conflict between a specific REVISION of your hardware and the native linux drivers. So, let's go ahead and isolate the problem.

First, type this:

```

lspci

```

And look for your network card. Here's my output so you'll know what to look for:

```

00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
**[COLOR="Red"]02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)[/COLOR]**
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

```

See the numbers on the far left? Mine was 02:02.0. Yours will more than likely be different. Keep a note of this number.

Now execute:

```

lspci -n

```

Remember that number? Let's use mine for illustrative purposes (02:02.0). Match that number with the output you get. So, for example:

```

00:00.0 0600: 10de:00d1 (rev a4)
00:01.0 0601: 10de:00d0 (rev a6)
00:01.1 0c05: 10de:00d4 (rev a4)
00:02.0 0c03: 10de:00d7 (rev a5)
00:02.1 0c03: 10de:00d7 (rev a5)
00:02.2 0c03: 10de:00d8 (rev a2)
00:06.0 0401: 10de:00da (rev a2)
00:06.1 0703: 10de:00d9 (rev a2)
00:08.0 0101: 10de:00d5 (rev a5)
00:0a.0 0604: 10de:00dd (rev a2)
00:0b.0 0604: 10de:00d2 (rev a4)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:00.0 0300: 10de:0176 (rev a3)
02:01.0 0200: 10ec:8139 (rev 10)
[COLOR="Red"]**02:02.0 0280: 14e4:4320 (rev 03)**[/COLOR]
02:04.0 0607: 104c:ac54 (rev 01)
02:04.1 0607: 104c:ac54 (rev 01)
02:04.2 0880: 104c:8201 (rev 01)

```

Now that you have this information, you'll need to keep it noted. Now, go ahead and download ndiswrapper.

[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

This thread will walk you through it.

[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

Remember that information we had from earlier?

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Let's take mine, for example. I had 02:02.0 0280: 14e4:4320. The LAST PART is the number you need to actually use, which in this case, is 14e4:4320. Search for YOUR number on the ndiswrapper hardware list to see if someone has found a reliable driver for it. So, for me, I'd look through the list to see if someone found a way to get 14e4:4320 working. Usually, people post a link to a .exe file, which is a self-extracting file containing the Windows native drivers. Go ahead and download this file. If you CANNOT find your model in the ndiswrapper hardware list, go ahead and download a copy of the *WINDOWS* drivers directly from the manufacturer. If Intel offers Linux drivers, however, scratch this HOWTO and follow the installation procedures for that driver. Anway, if you end up downloading a self-extracting .exe from the hardware list, copy it into an EMPTY directory and execute:

```

cabextract <name of file>

```

There should now be an .inf and a .sys file.

Do:

```

sudo rmmod ipw2100
ndiswrapper -i <driver_name>.sys
sudo modprobe ndiswrapper

```

Now you can execute just 'ifconfig' and see what name the interface is, i.e. wlan0 or eth0. Configure from there.

Again, I'm pressed on time, so I can't do a really thorough HOWTO. But [http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926) and [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) are good places to review regarding how to install and configure ndiswrapper. I know it looks daunting, but you'll soon realize it's actually pretty easy to install.

---

### Post by pandaking on 2007-04-09
WOW! Thanks dude!

I have found these linux drivers on this website if it helps:
[http://ipw2100.sourceforge.net/index.php](http://ipw2100.sourceforge.net/index.php)
[http://sourceforge.net/project/showfiles.php?group_id=103822](http://sourceforge.net/project/showfiles.php?group_id=103822)

Is this the best thing to do? If so do I need to download any of your links?

Thanks again dude, that reply was awesome! :D

---

### Post by skip27 on 2007-04-09
No problem :) Try downloading and installing the Linux drivers first. If that doesn't work, THEN try ndiswrapper (last resort).

---

### Post by siefer132 on 2007-04-09
yay... i figured it out, i just messed around with a couple of settings in the Network thing and it works!!

---

### Post by pandaking on 2007-04-10
I can't figure out how to install the linux drivers...

---

### Post by skip27 on 2007-04-10
Yeah, the process is a bit complicated, especially for someone new to Linux. Scratch that and try ndiswrapper. Basically, ndiswrapper is a tool that is used to make Windows drivers compatible with Linux.

---

### Post by x.1.alvin on 2007-04-13
Hi Skip, your I really learned a lot from your posts! I was actually able to get some laptops working by reading your instructions. You da man!

I have just 1 problem with this Compaq 800 laptop. The wireless drivers and devices are properly detected, but it seems my access point cannot see my laptop. iwconfig yields this:

```
 IEEE 802.11b/g  ESSID:"linksys"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Is there a way to see the log files of the AP from a terminal? Any ideas on how to make this work? Btw I'm a noob. Thanks!

---

### Post by tim525l on 2007-06-20
It would seem that you've had more luck than me in installing ubuntu on this type of laptop.  did you do anything special during the install?  and what version of ubuntu did you install?

---

