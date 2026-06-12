---
title: "How to connect to an existing network"
date: 2015-08-19
forum: Networking &amp; Wireless
---

### Post by jfh on 2015-08-19
Having successfully installed Ubuntu 14.4 over a corrupted XP os, I have been trying to get connected to the internet, and as a complete novice, I am confused by the process.  When I left click on the little fan-shaped icon in that taskbar at the top of the screen, a small box appears with the following options: Ethernet network (this is grayed out)
                           disconnected (grayed out)
                            VPN connections >
                           ^ Enable Networking (the ^ signifies a check mark)
                            Connection information (grayed out)
                            Edit connections
When I select the last of the above options, a small screen appears entitled "Network Connections" and which contains the following:
                            Name                                                               Last Used                                                                  Add (a box)
                  Ethernet                                                                                                                                                      Edit (a box)
                           Auto ethernet                                                       1 day ago                                                                 Delete (a box)
                   WiFi
                           WiFi Connection2                                                   Never
                           WiFi Connection1                                                   Never
(I did mention that I've beet trying to connect, which explains the abortive entries - I actually tried to connect a router before I realized that I had no modem or cable connection where this computer is located:oops:)
When, in the "Network Connections" screen, I select one of the WiFi Connection options a new larger screen appears entitled "Editing WiFi Connection" which contains several tabs: General - WiFi -   WiFi Security - IPv4Settings - IPv6Settings      but the screen seems to open defaulted to the "WiFi" screen, which contains the following:
                    SSID
                    Mode
                    BSSID
                    Device MAC address
                    Cloned MAC address
                     MTV                                                    Automation - +    bytes
    To someone like me, accustomed to Windows' more or less automatic handling of connections, this is pretty bewildering.  I think I know what the SSID is (I think), but not much else.  I would greatly appreciate it if someone could walk me through this process, or tell me where I could get simplified, detailed instructions.

---

### Post by chili555 on 2015-08-21
> To someone like me, accustomed to Windows' more or less automatic handling of connections, this is pretty bewildering.In Ubuntu, the process is largely the same; more or less automatic!

Generally, when you click on the fan-shaped icon,* if you have a working wireless device*, a list of available networks appears. [http://www.techotopia.com/images/d/de/Ubuntu_10.10_networkmanager_menu.jpg](http://www.techotopia.com/images/d/de/Ubuntu_10.10_networkmanager_menu.jpg) You click on yours, supply the password and connect. Simple, eh?> I had no modem or cable connection where this computer is locatedDoes this imply that there is no list to see because there is no available network to join, or...what??

Let's see if you have the needed working wireless device. Please open a terminal Ctrl+Alt+t and run:```
iwconfig
```Is there a listing for a wireless interface, ideally wlan0? Next, let's see if the wireless switch or key combination is set to enable or disable wireless:```
rfkill list all
```Does your wireless device scan and see networks at all?```
sudo iwlist wlan0 scan
```Once we have more information from you, we'll proceed.

---

### Post by jfh on 2015-08-21
When I enter the command   iwconfig   two lines appear:
lo       no wireless extensions

etho   no wireless extensions

I thought that when I tried earlier to access the internet I might have been too far from the modem/router, so I have moved the computer next to this laptop which is (obviously) connected, so proximity to the wireless network does not seem to be the problem.

---

### Post by chili555 on 2015-08-21
> **jfh said:**
> When I enter the command   iwconfig   two lines appear:
lo       no wireless extensions

etho   no wireless extensions

The problem is actually that your wireless device hasn't a working driver as yet. Let's see what you have and then install a driver. If your device is PCI, that is internal, please run and post:```
lspci -nn | grep 0280
```That funny pipe symbol | is on the right side of my keyboard on the same key with \.

If it is USB, then let's see:```
lsusb
```May I assume you are able to get a temporary connection by ethernet or tethered or however if we need to go on line to get the driver?

---

### Post by jfh on 2015-08-21
Hold everything - my big laptop here may not be connecting via the router (network), but directly via the ethernet cable.  I said I didn't know what I was doing!!!  Still, I do have a router here connected to the modem, so network connection should be possible. I have an old laptop in the next room running Vista which is clearly connected via the network, so I still have the question why Ubuntu installed on this tower is not connecting.  I know this sounds like stream of consciousness, but probably just frustration. (I got stuck in "guest" mode -in which you apparently can't change anything, including getting OUT of guest mode - and inserted the dvd to format and reboot.  Guess what - apparently just inserting the dvd enabled me to get out of guest mode.  Maybe inserting the dvd threatened Ubuntu into cooperating.)

---

### Post by chili555 on 2015-08-21
So you are connected and problem solved??

Or do we need to continue with the wireless?

---

### Post by jfh on 2015-08-21
No, unfortunately I am not connected.  I have brought the computer with Ubuntu into the same room with the modem and router.  I know that my network is active because an old laptop in an adjacent room (which is running Vista) is connected to the internet via the network.

I entered in the terminal the command    lspci -nn | grep 0200   and got this entry in the terminal:

03:00.0 Ethernet controller [0200 in red]: Marvell Technology Group Ltd. 88E8050 PCI-E
ASF Gigabit Ethernet Controller [11ab:4361] (rev 17)

I am reluctant to unplug the ethernet cable from my working computer to try downloading drivers for the Ubuntu computer.  Is there any way to download the driver(s) any other way - say, to a cd or usb drive?  
Also, would it work for me to do a format and re-install Ubuntu from my dvd?  Is it possible that the necessary items for network functioning were not installed originally because I was in a location where the network signal was weak or poor?

---

### Post by Erik The Pope on 2015-08-21
I am having the same problem with 15.04. I have no access either with ethernet (connected whilst installing) or Wi-Fi (probably no driver yet). This is on an old Dell (had XP) 32 bit & I installed Ubuntu a while back & it connected w/o me doing anything. I have also tried 14.04.3, same thing. I reset the BIOS to factory defaults. Linux newbie but experience on Windows. I have a cable modem & a Trendnet router. No trouble with Windows. ???

---

### Post by chili555 on 2015-08-22
> **Erik The Pope said:**
> I am having the same problem with 15.04. I have no access either with ethernet (connected whilst installing) or Wi-Fi (probably no driver yet). This is on an old Dell (had XP) 32 bit & I installed Ubuntu a while back & it connected w/o me doing anything. I have also tried 14.04.3, same thing. I reset the BIOS to factory defaults. Linux newbie but experience on Windows. I have a cable modem & a Trendnet router. No trouble with Windows. ???I recommend you start your own new thread. Your hardware and other details are unlikely to be the same.

---

### Post by chili555 on 2015-08-22
>  Is there any way to download the driver(s) any other way - say, to a cd or usb drive? Sure. It could be easy or it could be excrutiating depending on the exact device and its driver. See this for example: [http://ubuntuforums.org/showthread.php?t=2228244&p=13042921#post13042921](http://ubuntuforums.org/showthread.php?t=2228244&p=13042921#post13042921) CAUTION: This is not necessarily your driver. It is simply to demonstrate two methods; one with ethernet and one off-line.

Let's identify your wireless device:```
lspci -nn | grep 0280
```> Also, would it work for me to do a format and re-install Ubuntu from my dvd? Is it possible that the necessary items for network functioning were not installed originally because I was in a location where the network signal was weak or poor?Very unlikely.> I am reluctant to unplug the ethernet cable from my working computer to try downloading drivers for the Ubuntu computer. Why? Once we identify the device, you'll likely be done in five minutes instead of five days and 500 posts asking for a bailout.

---

### Post by jfh on 2015-08-22
OK, let's say I unplug my ethernet cable from my working computer and plug it in to the Ubuntu computer, how do I download and install the drivers?  I assume that I will then be "blind" with neither computer connected until the Ubuntu computer is connected to my network.

---

### Post by chili555 on 2015-08-22
>  I assume that I will then be "blind" with neither computer connected until the Ubuntu computer is connected to my network.LOL! That's right, you won't be connected until you are connected!!

Seriously, your ethernet device has a driver, namely *sky2*, that should work correctly from the start. If you run:```
ifconfig
```Do you see an interface eth0? If so, that means a driver has matched up with your hardware and all it ideally needs is an ethernet cable to connect.

We don't know what to download or what else to do until we get more details as I requested above:```

lspci -nn | grep 0280
```

---

### Post by jfh on 2015-08-22
When I entered the above command (ending in 0280), several paragraphs appeared on my terminal screen.  I took a picture of the terminal screen and tried to attach it to this reply, but could not figure out how to do so - like so much of Ubuntu.
Chili555, I am very grateful for your effort to held this hopeless noob, but I think I'll just give it a rest for now. Thanks again.

---

### Post by chili555 on 2015-08-22
It shouldn't be several paragraphs. Please check what you typed and try again. Here is the result from my computer for comparison:```
chili@T410:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]:[COLOR="#FF0000"] Intel Corporation Centrino Advanced-N 6200 [8086:4239] [/COLOR](rev 35)

```You needn't take a picture of the screen to post it. Just write it down and copy it here. All we really need is what I highlighted above.

---

