---
title: "Belkin Wireless G Plus MIMO USB Network Adapter"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by shoenigman on 2008-02-08
Hi all,

I am very new to Linux and am trying to configure wireless access. I followed the directions to load the appropriate driver in the post at at [http://ubuntuforums.org/showthread.php?t=400236]("http://ubuntuforums.org/showthread.php?t=400236"). I get to the point where you have to enter your sid and WEP key and it does not work.

I thought that it was working at one point because the light on the wireless device was blinking green but I still could not get to the Internet. I was unsure if I should use the WEP password (String) or the hexadecimal representation, so I used the hex value. Once that didn't work I tried it again using the passphrase which I think really messed it up because now it appears that the device is in there twice. Anyway, if anybody could point me in the right direction I would be etenally grateful. Thanks!

```
scott@scott-laptop:~$ ifconfig -a
eth2      Link encap:Ethernet  HWaddr 00:04:76:4B:86:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:440 (440.0 b)  TX bytes:440 (440.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:17:3F:74:FB:F5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:17:3F:74:FB:F5  
          inet addr:169.254.10.167  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-74-FB-F5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

scott@scott-laptop:~$ sudo ifconfig wlan0 up
[sudo] password for scott:
scott@scott-laptop:~$ sudo ifconfig wlan0 up
scott@scott-laptop:~$ sudo iwconfig wlan0 essid wirelessconn
scott@scott-laptop:~$ sudo iwconfig wlan0 key 04A6AD4237
scott@scott-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:17:3f:74:fb:f5
Sending on   LPF/wlan0/00:17:3f:74:fb:f5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
scott@scott-laptop:~$ 

```

---

### Post by Austin_KW on 2008-02-08
Are you still running the rt73usb driver and not the legacy driver from the howto,

Make sure you blacklist and unload the running driver

Post the results of the command (to see what usb drivers are loaded)
```
lsmod | grep usbcore

```

---

### Post by shoenigman on 2008-02-08
Thanks for looking at this for me... Here is the result:

```

scott@scott-laptop:~$ lsmod | grep usbcore
usbcore               138632  7 usb_storage,libusual,rt73,rt73usb,rt2x00usb,uhci_hcd
scott@scott-laptop:~$ 

```

---

### Post by Austin_KW on 2008-02-08
You have 2 conflicting drivers rt73 and rt73usb, you want to  remove the beta driver and leave the legacy driver
```

sudo modprobe -r rt73usb

```

make sure that /etc/modprobe.d/blacklist contains the line
```

blacklist rt73usb

```

You may need to remove and reinsert the belkin adapter  and then it should use the rt73 driver. Then retry the config commands

---

### Post by shoenigman on 2008-02-08
Thank you... It seems to be recognizing the wireless adapter because it is blinking green very quickly. I still am getting the Server not found message in Firefox. Is there anything else that I have to do in order to connect correctly? Am I leaving something out? I really appreciate your help with this!

Thanks!

---

### Post by shoenigman on 2008-02-08
I forgot to say that I followed your instructions...

---

### Post by Austin_KW on 2008-02-08
what is the output of
```

iwconfig
ifconfig -a

```

after the dhclient command

---

### Post by shoenigman on 2008-02-08
I am so sorry... you will never guess it but when I typed in my essid I inadvertantly made the first letter uppercase. I fixed that and now it works. Thanks!

---

### Post by Austin_KW on 2008-02-08
You may want to follow the howto and setup your interfaces file so it automatically connects on boot. You can then use the manual commands only when you need to connect to a different network.

Also consider changing your serurity to WPA , WEP can be cracked in 2 minutes

---

### Post by shoenigman on 2008-02-08
Hey,

I tried to set this up to automatically connect on reboot but it is not working. I added the following to the interfaces document and saved it then rebooted.

```

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid wirelessconn
pre-up iwconfig wlan0 key 04A6AD4237

```

Is there something else that I am missing here? Thanks

---

### Post by Austin_KW on 2008-02-09
Looks OK,
You might try adding "pre-up iwconfig wlan0 mode managed" after the third line, but it should default to managed mode.

The following command will force a reinit from the interfaces file, and tell you if there are any errors in the file. It is also useful if your connection drops and you need to reconnect for any reason
```

sudo ifup --f wlan0

```

---

### Post by sarahbobera on 2008-02-09
Hi, I'm not new to Ubuntu, but for all practical uses, I might as well be. 

I just got this same wireless adapter, and I'm trying to configure the SSID and Key, but I use a WPA rather than a WEP, and I don't know where to go from here. Everything has gone perfectly until this step, I'd hate to have to give up now!

Any help?

---

### Post by Austin_KW on 2008-02-10
> **sarahbobera said:**
> Hi, I'm not new to Ubuntu, but for all practical uses, I might as well be. 

I just got this same wireless adapter, and I'm trying to configure the SSID and Key, but I use a WPA rather than a WEP, and I don't know where to go from here. Everything has gone perfectly until this step, I'd hate to have to give up now!

Any help?

Follow the same howto from the OP [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by sarahbobera on 2008-02-10
Alright, so now the internet works, but for some reason, it won't let me open any applications that don't have quickstart buttons on the menu. It's very strange. I can't open a terminal, and when I use the "places" button to try to open my home folder, it lets me open the dropdown, but does nothing when I click "home" or whatever. I'm getting really frustrated with this.

If nautilus is open, and I mouseover an mp3 within that, nautilus freezes up and goes completely blank.

It snaps out of its limbo after about 30 minutes on its own, or instantly if I killall -9 nautilus. Any ideas why this happened?

If I run my mouse over any mp3 file, it breaks again. 

If I open a terminal, and then make it lock up, and then try to open the home folder, I get this:

sarah@Danny-The-Rat:~$ open /home/sarah
Couldnt get a file descriptor referring to the console
Could not get a file descriptor referring to the console


I don't know how to make heads or tails of it.

---

### Post by Austin_KW on 2008-02-11
@sarahbobera

Not sure I understand, what is going on. Do these problems only happen with the usb adapter installed/running. If so it may be a driver conflict.

What drivers are installed for the usb adapters (output from command)
```
lsmod | grep usbcore

```

The command to open/view your home folder would be "nautilus /home/sarah" not "open".

---

### Post by sarahbobera on 2008-02-11
Sorry, it confuses me too. If I mouseover an mp3 file on the desktop, the desktop freezes up and all the icons disappear, and I can still open menus, but nothing useful will actually open. If I mouseover an mp3 in Nautilus, Nautilus behaves the same way, going blank (even the menus), and being unresponsive. If I kill Nautilus from my Gnome menu command line, it kills it and reopens Nautilus, like it should, and everything is functional again, as long as I don't try to move mp3 files. If I disable the wireless adapter, it works fine (thanks for asking, I hadn't thought of testing that). Does that mean when I did the clearing-conflicting-drivers part of the HOW-TO, maybe I missed one? 

The output is this:

usbcore               138632  3 rt73,uhci_hcd

And thanks, like I said, I really am new to actually *doing* anything with Ubuntu.

---

### Post by shoenigman on 2008-02-11
Hey, I am sorry that it has taken so long to respond but I had to go out of the country unexpectedly and just got back. Everything now works perfectly and I totally appreciate your responses...

---

### Post by jimoz on 2008-04-26
Hi all

Im trying to setup up ubuntu GG on a friends PC. Everything works fine out of the box except for the USB wireless - a Belkin G Plus MIMO (F5D9050B v3000).
Initially I plugged it in and it wouldnt register on ifconfig. Followed the instructions for the rt73 serialmonkey drivers - but still wouldnt register. The device does register under lsusb. dmesg does output a whole heap of error-110's. ifconfig/iwconfig dont register anything other than the loopback. Ive tried swapping usb ports, i do have to use the cable though as it wont plug in directly (however i can still use a usb pen drive through the same cable). Its a fudged old system, using an old usb 1.1 controller. If i plug the wireless adapter into my own laptop it runs flawlessly straight out of the box.

Im starting to think the usb controller is half stuffed. Anyone have any ideas or suggestions?

---

