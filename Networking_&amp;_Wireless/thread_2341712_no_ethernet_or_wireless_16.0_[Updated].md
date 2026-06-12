---
title: "no ethernet or wireless: 16.0 [Updated]"
date: 2016-10-30
forum: Networking &amp; Wireless
---

### Post by digi84 on 2016-10-30
So I am new to Ubuntu and Linux in general(finally had it with Windows) but anxious to learn.  However I am having trouble getting my internet to work.  I have searched the interwebs for hours trying to find solutions and nothing works also anything I can find with similar problems is 10 months to multiple years old.

Both my Ethernet and wireless will not connect.  My wireless can see my home network but will not connect.  I would prefer to use Ethernet but if wireless is my only option that's ok.  I have tried resetting network manager, I have tried disabling ipv6 and I have tried editing etc/network/interfaces.

Please any help would be greatly appreciated.  I don't understand what's wrong.  Again, new to Linux so not sure what other information is needed.

Please and Thank you.

[UPDATE 11/4/16]

On [**[COLOR=#000000]Geoffrey_Arndt[/COLOR]**]("https://ubuntuforums.org/member.php?u=1973436")'s  suggestion.  I purchased a usb dongle that seems to be working.  I can  now connect to my wireless network.  I would still prefer to connect via  ethernet though.


[UPDATE 11/4/16]

> **Geoffrey_Arndt said:**
> See:   [https://ubuntuforums.org/showthread.php?t=2293272](https://ubuntuforums.org/showthread.php?t=2293272)

Thank you to Geoffrey_Arndt - With my temporary internet connection with the dongle I was able to download from the Synaptic Package Manager and it fixed the problem right away!  Thank you to everyone who replied!

---

### Post by oldrocker99 on 2016-10-30
Welcome to the forums!

It's not too unusual for wireless to not work, but not Ethernet, which almost certainly should work just fine. I have had problems with USB 3.0 ports, but never with USB 2.0.

It would help if you'd list your motherboard, CPU, RAM and GPU. Also post the output of ```
lspci
```

---

### Post by digi84 on 2016-10-30
> **oldrocker99 said:**
> Welcome to the forums!

It's not too unusual for wireless to not work, but not Ethernet, which almost certainly should work just fine. I have had problems with USB 3.0 ports, but never with USB 2.0.

It would help if you'd list your motherboard, CPU, RAM and GPU. Also post the output of ```
lspci
```


Thanks for the reply.
CPU is and FX-6300 6 core processor
Ram is 16GB ddr3
Motherboard is AMD AM3+
GPU is a nvidia card.  Gforce HTC 950

> **oldrocker99 said:**
> Welcome to the forums!

It's not too unusual for wireless to not work, but not Ethernet, which almost certainly should work just fine. I have had problems with USB 3.0 ports, but never with USB 2.0.

It would help if you'd list your motherboard, CPU, RAM and GPU. Also post the output of ```
lspci
```

lspci listing is

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port E)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 950] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0fba (rev a1)
02:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8812AE 802.11ac PCIe Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
```

---

### Post by Bucky Ball on 2016-10-31
Welcome. Much better for network details is this. 

```
sudo lshw -C network
```

Output if you will, and please use code tags for the terminal output (see the link in the first line of my signature at bottom of this post).

Your USB issue is the stuff of another thread. To improve your chances of support, edit that out of this one and post a new thread regarding USB. We like to stick to one support issue per thread here. Saves confusion and gets you fixed faster (hopefully). Thanks.

You might also like to change the title of this thread (edit first post, 'Go Advanced') to something specific that describes your actual problem like 'no ethernet or wireless: 16.04' as most people here have got problems and are wanting someone to help. Non-generic titles will also improve your chances of support. Good luck. :)

---

### Post by digi84 on 2016-10-31
> **Bucky Ball said:**
> Welcome. Much better for network details is this. 

```
sudo lshw -C network
```

Output if you will, and please use code tags for the terminal output (see the link in the first line of my signature at bottom of this post).

Your USB issue is the stuff of another thread. To improve your chances of support, edit that out of this one and post a new thread regarding USB. We like to stick to one support issue per thread here. Saves confusion and gets you fixed faster (hopefully). Thanks.

You might also like to change the title of this thread (edit first post, 'Go Advanced') to something specific that describes your actual problem like 'no ethernet or wireless: 16.04' as most people here have got problems and are wanting someone to help. Non-generic titles will also improve your chances of support. Good luck. :)

Thanks for the input!  Edited the post.  Here is the output.

```

*-network               
       description: Wireless interface
       product: RTL8812AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 01
       serial: f8:7b:8c:2c:dc:30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ae driverversion=4.4.0-31-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:34 ioport:d000(size=256) memory:fe200000-fe203fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 0c
       serial: 40:8d:5c:85:4e:10
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=169.254.70.255 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:29 ioport:c000(size=256) memory:fe100000-fe100fff memory:d2100000-d2103fff

```

---

### Post by Geoffrey_Arndt on 2016-10-31
See:   [https://ubuntuforums.org/showthread.php?t=2293272](https://ubuntuforums.org/showthread.php?t=2293272)

---

### Post by digi84 on 2016-10-31
> **Geoffrey_Arndt said:**
> See:   [https://ubuntuforums.org/showthread.php?t=2293272](https://ubuntuforums.org/showthread.php?t=2293272)

I will give it a try, thank you.  But probably a stupid question but sorry, new.  

Can I do the 'sudo apt-get' commands without internet access?

-Thanks

---

### Post by Bucky Ball on 2016-10-31
Thread moved to Networking and Wireless.

Cheers. The only problem with Geoffrey_Arndt's link is that it appears that the OP in that thread was able to get online (as they installed Synaptic Package Manager). You can't so not sure it will be of much use.

Please run the wirelessinfo script linked in my signature below and post the output here. That will give us all details of what is happening and hopefully what is going wrong.

Seems to be the correct driver for wireless but something blocking.

* Just saw this:

> **digi84 said:**
> Can I do the 'sudo apt-get' commands without internet access?

No, you can't, which is why that link probably won't do you a lot of good. :|

---

### Post by digi84 on 2016-10-31
> **Bucky Ball said:**
> Thread moved to Networking and Wireless.

Cheers. The only problem with Geoffrey_Arndt's link is that it appears that the OP in that thread was able to get online (as they installed Synaptic Package Manager). You can't so not sure it will be of much use.

Please run the wirelessinfo script linked in my signature below and post the output here. That will give us all details of what is happening and hopefully what is going wrong.

Seems to be the correct driver for wireless but something blocking.

* Just saw this:



No, you can't, which is why that link probably won't do you a lot of good. :|


So I got to the point where I double click on the file and select run.  It doesn't seem to do anything.  The terminal opens for a split second but closes.  Doesn't ask for my password. If I open the wireless-info.txt all it displays is 'wireless info START'

---

### Post by Bucky Ball on 2016-10-31
> **digi84 said:**
> So I got to the point where I double click on the file and select run.  It doesn't seem to do anything.  The terminal opens for a split second but closes.  Doesn't ask for my password. If I open the wireless-info.txt all it displays is 'wireless info START'

How are you running the script? Did you use method one or method two? You should be using method two, no internet access.

---

### Post by digi84 on 2016-10-31
> **Bucky Ball said:**
> How are you running the script? Did you use method one or method two? You should be using method two, no internet access.

Yes, method 2 is what I'm using.

---

### Post by Bucky Ball on 2016-10-31
Once you have the wirelessinfoscript downloaded you are following these instructions exactly, particularly point 1? If you do not make the file executable you won't have a lot of luck.

[QUOTE=varunendra]1) Right-click the downloaded file > click "Properties" > go to "Permissions" tab > tick the "Execute" checkbox > close the box.

2) Double-click the file > select "Run" in the opened dialogue box. Provide your password when asked.
[NOTE 1: Since Ubuntu 13.04, Text Files open up in text editor even if they are made executable. To change this-
Open any folder > go to Files > Preferences > Behavior tab > select "Ask each time" option under "Executable Text Files" section.]

3) A fresh new file "wireless-info.txt" (or "wireless-info.txt.tar.gz" file, if the text file size exceeds 19.5 KB) will be created in the same directory where you have run the script from. Attach it or copy-paste its contents (as described above) in your next post.[/QUOTE]

If it does spit out the correct output, please post at [http://pastebin.ubuntu.com](http://pastebin.ubuntu.com) and post the link here.

... and remember these points from the wirelessinfoscript lin:

[QUOTE=varunendra]    If the generated file is "wireless-info.txt.tar.gz" instead of a simple text file, you may simply right-click > Extract here to extract the file, then double click the extracted file to open it.
    Alternative version of wireless_script, provides information in a different format and sequence that I personally prefer : [http://dl.dropboxusercontent.com/s/q...ireless_script](http://dl.dropboxusercontent.com/s/q...ireless_script)[/QUOTE]

---

### Post by digi84 on 2016-10-31
> **Bucky Ball said:**
> Once you have the wirelessinfoscript downloaded you are following these instructions exactly, particularly point 1? If you do not make the file executable you won't have a lot of luck.
If it does spit out the correct output, please post at [http://pastebin.ubuntu.com](http://pastebin.ubuntu.com) and post the link here.

... and remember these points from the wirelessinfoscript lin:

Following it step by step.  Made it executable.  It's wireless-info.txt.  when I double click it gives me the option to run in terminal(doesn't work),display(opens as text file), cancel, run(nothing happens)

---

### Post by Geoffrey_Arndt on 2016-10-31
In the forum link that I sent earlier in this thread, it's important to note the poster had exactly the same situation re hardware and lack of connectivity.   Two reasons why he solved the problem:

>   he connected to the internet via a USB tethered android phone (I'm not sure about Apple phones), and,
>   after connection established, he used the steps described in his post to resolve the issue

IF you don't have a phone that allows for tethering,  perhaps a friend does . . . or even a throw away track phone.

How to tether a phone to PC:   [https://www.youtube.com/watch?v=HK6EhJpvDOU](https://www.youtube.com/watch?v=HK6EhJpvDOU)

Additionally, if you have about ($10 usd or equivalent in other money) then you can solve the problem by ordering from Amazon a usb wireless dongle (the ultra 150 b/g/n) from Panda:

[http://www.pandawireless.com/](http://www.pandawireless.com/)

---

### Post by digi84 on 2016-10-31
> **Geoffrey_Arndt said:**
> In the forum link that I sent earlier in this thread, it's important to note the poster had exactly the same situation re hardware and lack of connectivity.   Two reasons why he solved the problem:

>   he connected to the internet via a USB tethered android phone (I'm not sure about Apple phones), and,
>   after connection established, he used the steps described in his post to resolve the issue

IF you don't have a phone that allows for tethering,  perhaps a friend does . . . or even a throw away track phone.

How to tether a phone to PC:   [https://www.youtube.com/watch?v=HK6EhJpvDOU](https://www.youtube.com/watch?v=HK6EhJpvDOU)

Additionally, if you have about ($10 usd or equivalent in other money) then you can solve the problem by ordering from Amazon a usb wireless dongle (the ultra 150 b/g/n) from Panda:

[http://www.pandawireless.com/](http://www.pandawireless.com/)



Hmm, the dongle could work.  I don't have a problem spending a little bit on money.  One thing though.  On the site it says its plug-and-play for linux but then it also has a driver.  Will it work out of box or will I still need the driver?

Thanks!

---

### Post by Geoffrey_Arndt on 2016-10-31
It should work out of the box - - I have about two dozen various dongles from different suppliers;  the Panda devices all worked directly (plug & play). 

The driver is included for multiple scenarios (old hardware/kernels, custom mobos/chipsets, etc.).   The possibility to "build" the driver/module is a good thing, especially for tech support and IT depts.   They (Panda) would advise how to use via phone or email if needed . . . but that's not a common issue.   

It's good to get the dongle, but why not try the phone tether if you can, . . . it might be fun and productive and you're not out anything if it doesn't connect.

---

### Post by Bucky Ball on 2016-10-31
How can OP tether to anything if their wireless is not working?

---

### Post by Geoffrey_Arndt on 2016-11-02
Bucky . . . I personally have never needed or used "tethering" to connect a PC to internet, but know people that have.    In one case they had no Internet service from a local ISP but did via Verizon.

So, here's the Youtube instructional video (maybe I am missing something . . . it seems to me the laptop or PC is just receiving & redisplaying the phone internet feed . . ?)   Am I wrong?

[https://www.youtube.com/watch?v=HK6EhJpvDOU](https://www.youtube.com/watch?v=HK6EhJpvDOU)

---

### Post by jeremy31 on 2016-11-02
Let's try the normal things
```
echo "options rtl8821ae fwlps=N" | sudo tee /etc/modprobe.d/rtl8821ae.conf
```
That should disable some of the modules troublesome power management

A recent change to network manager may also be enabling power management, that can be changed back to disabled
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Then I would check results from ```
iwlist scan | egrep -i 'ssid|cipher'
```
Check to see if the cipher results under your wifi show CCMP only, no TKIP, make changes to the router encryption settings
Save router settings and reboot it and the computer.

I have tethered to my cell phone using USB before and it does work but if it is network encryption causing the wifi issue there is a chance that a wifi tether to the phone will work

---

### Post by Bucky Ball on 2016-11-02
> **Geoffrey_Arndt said:**
> Bucky . . . I personally have never needed or used "tethering" to connect a PC to internet, but know people that have.    In one case they had no Internet service from a local ISP but did via Verizon.

I posted this in the wrong thread yesterday (!) but yes, the OP has network card that's working just not connecting (after checking one of their posts). Was thinking the card wasn't working at all, in which case, no tethering. 

Tethering from the phone is done in a couple of clicks on the phone settings, no twiddling with the computer. Once the phone is acting as an access point just pops up like any other network on your available network list. :)

Hopefully, jeremy31 can get to the bottom of this without going there as tethering doesn't solve why a working wireless is seeing the network and not connecting. :-k

---

### Post by digi84 on 2016-11-04
> **jeremy31 said:**
> Let's try the normal things
```
echo "options rtl8821ae fwlps=N" | sudo tee /etc/modprobe.d/rtl8821ae.conf
```
That should disable some of the modules troublesome power management

A recent change to network manager may also be enabling power management, that can be changed back to disabled
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Then I would check results from ```
iwlist scan | egrep -i 'ssid|cipher'
```
Check to see if the cipher results under your wifi show CCMP only, no TKIP, make changes to the router encryption settings
Save router settings and reboot it and the computer.

I have tethered to my cell phone using USB before and it does work but if it is network encryption causing the wifi issue there is a chance that a wifi tether to the phone will work


I can certainly try this.  Quick update though.  On [**[COLOR=#000000]Geoffrey_Arndt[/COLOR]**]("https://ubuntuforums.org/member.php?u=1973436")'s suggestion.  I purchased a usb dongle that seems to be working.  I can now connect to my wireless network.  I would still prefer to connect via ethernet though.  Should I still go through with your instructions, or should I do something different now that I have Internet connection?

Thanks!

---

### Post by digi84 on 2016-11-04
> **jeremy31 said:**
> Let's try the normal things
```
echo "options rtl8821ae fwlps=N" | sudo tee /etc/modprobe.d/rtl8821ae.conf
```
That should disable some of the modules troublesome power management

A recent change to network manager may also be enabling power management, that can be changed back to disabled
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Then I would check results from ```
iwlist scan | egrep -i 'ssid|cipher'
```
Check to see if the cipher results under your wifi show CCMP only, no TKIP, make changes to the router encryption settings
Save router settings and reboot it and the computer.

I have tethered to my cell phone using USB before and it does work but if it is network encryption causing the wifi issue there is a chance that a wifi tether to the phone will work


First one gave me this as a response
```
options rtl8821ae fwlps=N
```

Second one didn't respond with anything, didn't give error message or anything though.

Third displayed
```
lo        Interface doesn't support scanning.

enp4s0    Interface doesn't support scanning.

                    ESSID:"WOW!1245"
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP


```


[i]Check to see if the cipher results under your wifi show CCMP only, no TKIP, make changes to the router encryption settings
Save router settings and reboot it and the computer.[/i]

Okay so it does show TKIP in addition to the CCMP.  How do I make changes to the router encryption settings?  Will that fix the Ethernet or just the wifi?


Thanks for the help!

---

### Post by digi84 on 2016-11-04
> **Geoffrey_Arndt said:**
> See:   [https://ubuntuforums.org/showthread.php?t=2293272](https://ubuntuforums.org/showthread.php?t=2293272)


Was finally able to try this with my temporary wireless connection and it worked!   Thank you so much!

---

