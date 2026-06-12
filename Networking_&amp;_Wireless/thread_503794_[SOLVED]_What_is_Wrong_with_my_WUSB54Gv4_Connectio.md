---
title: "[SOLVED] What is Wrong with my WUSB54Gv4 Connection?"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by qrprat77 on 2007-07-18
Hi!  I've been an Ubuntu user for about six months strong now, started using Eft, and I loved it.  My Linksys wireless device (WUSB54Gv4) worked well, using some connection advice I found here.  Now I am running Fiesty Fawn, and well, things have not been pretty.  

Currently, the internet works(?).  I have a netgear router with WPA-TKIP and the dongle will connect using ndiswrapper and wpa_supplicant.  NOTE:  I have removed the gnome wireless manager, and compiled ndiswrapper from source, and done all the bells and goodies people seem to need to do with this device.  I've ready almost every post on the WUSB54G v4 and still have one very big problem that is causing me stress, and making my wife hate Ubuntu:
Sometimes, the connection drops, and needs to be restarted via /etc/init.d/networking restart .  Sometimes that doesn't work, and I need to run ifconfig and scan(something) and then networking restart to get it to work.  I wrote a script to handle it.

It's driving me crazy because other than this one issue Ubuntu has been excellent.  Unfortunately, the internet is a big deal in my house.  Any help?

---

### Post by kevdog on 2007-07-18
What chipset and driver (besides ndiswrapper) are you using??

Unfortunately for a limited handful of people Ive found actually downgrading to Edgy was the final solution.  Im using Feisty (Edgy previously), but really could tell you much difference that Ive found between the two distributions.

---

### Post by qrprat77 on 2007-07-18
My driver is the latest from the linksys website, and the only one that worked under edgy.  Chipset is the ralink one I suppose, since it's version 4.  
a funny thing is that it registers under the interface file as rausb0 and not wlan0.  From what I understand, wlan0 is supposed to be the right setting, but alas, it don't work that way...

---

### Post by kevdog on 2007-07-18
Hmmm,

You have a ra chipset.

This can be confirmed with both
lspci -nn
lshw -C network

Did you compile the serial monkey ra drivers from source or are you using the old built in ones??? Also are you trying to use network manager or making your configurations from the /etc/network/interfaces file???

---

### Post by qrprat77 on 2007-07-18
> **kevdog said:**
> Hmmm,

You have a ra chipset.

This can be confirmed with both
lspci -nn
lshw -C network

Did you compile the serial monkey ra drivers from source or are you using the old built in ones??? Also are you trying to use network manager or making your configurations from the /etc/network/interfaces file???

here is the output of lshw -C network

 *-network
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       serial: 00:12:17:73:7b:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Linksys,10/17/2005, 2.01.00.000 ip=192.168.5.3 link=yes multicast=yes wireless=IEEE 802.11g

I am using the latest drivers from linksys not the native drivers from serial monkey.
I am using /etc/network/interfaces to do my setup:

auto lo
iface lo inet loopback

auto rausb0
iface rausb0 inet dhcp
wpa-driver wext
#wpa-conf managed
wpa-ap-scan 2
wpa-scan-ssid 1
wpa-ssid <SSID>
wpa-passphrase *********
wpa-key-mgmt WPA-PSK
wpa-pairwise TKIP
wpa-group TKIP
wpa-proto WPA


#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

Is how I got it to work.  NOTE:  This line:  #wpa-conf managed **MUST** be commented otherwise something says "Cannot read contents of managed" and the driver won't start...

---

### Post by Austin_KW on 2007-07-18
What is the chipset rt73 or rt2570. Either way make sure that you have blacklisted any competing (native) drivers. what is the output of "lsmod | grep usbcore"

You should also look into the serialmonkey native legacy drivers, but first make sure that they are not loading now and competing with ndiswrapper.

---

### Post by kevdog on 2007-07-18
Can you post
lspci -nn

This would clarify what chipset you are running.  You are correct that the ndiswrapper driver is currently associated with your wireless card.  If you are truly running an ra chipset, I think I can try something else besides ndiswrapper -- hopefully that will work better.

Sorry I guess in your case it would:
lsusb
since its a USB device!

---

### Post by qrprat77 on 2007-07-18
> **Austin_KW said:**
> What is the chipset rt73 or rt2570. Either way make sure that you have blacklisted any competing (native) drivers. what is the output of "lsmod | grep usbcore"

You should also look into the serialmonkey native legacy drivers, but first make sure that they are not loading now and competing with ndiswrapper.

lsmod | grep usbcore yields:

usbcore               134280  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

lsusb yields:

Bus 005 Device 002: ID 13b1:000d Linksys 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 049f:000e Compaq Computer Corp. Internet Keyboard
Bus 004 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


I have the rt2570 driver blacklisted.  I JUST blacklisted the rt73 driver...
lets see what happens now...

---

### Post by kevdog on 2007-07-18
If things dont work, then I would suggest compiling the serial monkey drivers from scratch.  Sorry but the info I asked you for doesnt tell me the chipset of your device.  Looking at the serialmonkey website:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)
It looks like only rt73 or rt2570 are possible drivers for your stick.  If only I knew which to suggest.

If you get in a pinch, possibly you could try the following:
blacklist ndiswrapper, and then "unblacklist" or just put a # sign in front of the rt lines.  Reboot the computer, and see if the computer automatically assigns a driver to your stick -- this would show with:
lshw -C network
under the driver statement.

---

### Post by Austin_KW on 2007-07-18
Google 13b1:000d suggests that it is the rt2570 chipset. So you probably only needed to blacklist the rt2570.

So your choice is between the native serial monkey rt2570 and the ndiswrapper (with rt2500usb or whatever linksys rename it). Just make sure that when you choose one you blacklist the other.

If ndiswrapper is giving problems then it might be worth downloading and building the serialmonkey driver from kevdogs link above

---

### Post by kevdog on 2007-07-18
> Google 13b1:000d suggests that it is the rt2570 chipset

Nice piece of googling Austin!!

---

### Post by qrprat77 on 2007-07-19
So now lessee,
I've downloaded and compiled the serial monkey drivers.  Now do I need to install anything or remove anything (ie old rt2570 drivers) before I install the driver in the modprobe file??

---

### Post by Austin_KW on 2007-07-19
It should overwrite the old rt2570.ko.

What does the command " lshw -C net " now report as your driver? And what is your interface from "ifconfig"

---

### Post by ubanchaos on 2007-07-19
well use the ndiswrapper

---

### Post by kevdog on 2007-07-19
Great

Dont use ndiswrapper for rtchipset

Here is a quick guide for how to compile.  Note that your chipset number will be different so substitute your chipset number:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

---

### Post by qrprat77 on 2007-07-19
Hey Kevdog, that was actually the process I was paralleling to compile them!

Ok, heres the bacon, tried to post this before, but there was a snafu on my windoze lappy:
Here's what I've done:
    compiled the rt2570 driver
    ran command modprobe -v rt2570
    discovered that my device's logical name is now rausb1 and not rausb0
    blacklisted rt2500usb, rt73 , and ndiswrapper
    fooled around with interface to change the appropriate names, experimented with some wpa-driver values
    used knoppix to rescue myself from fooled around with network interface file ;-)
    unblacklisted rt2500usb entry

    lshw -C net reveals :  "wireless=RT2500USB WLAN"; with or without rt2500usb blacklisted.
    
    
So what now will rtutil work for me from this post:
[http://ubuntuforums.org/showthread.php?t=434952&highlight=rt2570+wpa+how+to]("http://ubuntuforums.org/showthread.php?t=434952&highlight=rt2570+wpa+how+to")

---

### Post by qrprat77 on 2007-07-19
Ok,
Progress?
Good news!
     I installed rutilt (mentioned it in my last post)
     Ran it and connected to the network (yeah!)
     Turned off computer and restarted
     Didn't automatically connect to internet, had to rutilt again...  (*sigh*)
     now performing "wait and see" check.  
        -Does the connection stay active after I've left it alone for enough time for the screensaver to come on?
            -if yes:  YEAH!! Its fixed, how can I connect to the net without having to run rutilt everytime, and thus require a password (make things easy for everyone else in the house.)
            -if no:  (*D'oh*) back to square one...

TO BE CONTINUED>>>>

---

### Post by Austin_KW on 2007-07-19
the serial monkey drivers can be configured to connect on boot using the /etc/interfaces file
Check this post for the rt73 driver [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) on editing the interfaces file. Just replace wlan0 with rausb1 or whatever your interface name is.

---

### Post by qrprat77 on 2007-07-20
Austin:
Tried the following code in my  /etc/network/interfaces files:

 auto rausb1
iface rausb1 inet dhcp
    pre-up ifconfig rausb1 up
    pre-up iwconfig rausb1 mode managed
    pre-up iwpriv rausb1 set EncrypType=TKIP
    pre-up iwpriv rausb1 set AuthMode=WPAPSK
    pre-up iwconfig rausb1 essid MySite
    pre-up iwpriv rausb1 set WPAPSK="*******"
    pre-up iwconfig rausb1 essid MySite

and got an error:

gbhoyt@RajinCajin:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Invalid command : set
Failed to bring up rausb1.

so,
the good news is that rutilt really works!  I can surf like mad, leave the connection alone and it stands, but it doesn't load from the boot still. :-(
so,
I tried deleting the word "set" in the above interfaces file.  It still didn't work...

should I try something else???

---

### Post by qrprat77 on 2007-07-20
PS, I did try man iwpriv to get some answers, and it wasn't very helpful.

---

### Post by Austin_KW on 2007-07-20
Ok, has a quick look at the iwpriv_usage.txt, seem to supporrt the older interface.

try ```

auto rausb1
iface rausb1 inet dhcp
pre-up ifconfig rausb1 up
pre-up iwconfig rausb1 mode managed
pre-up iwpriv rausb1 auth 3
pre-up iwpriv rausb1 enc 3
pre-up iwconfig rausb1 essid MySite
pre-up iwpriv rausb1  WPAPSK="*******"
pre-up iwconfig rausb1 essid MySite


```

---

### Post by qrprat77 on 2007-07-20
> **Austin_KW said:**
> Ok, has a quick look at the iwpriv_usage.txt, seem to supporrt the older interface.

...
pre-up iwpriv rausb1  WPAPSK="*******"
...
[/code]

This line produces a "command not found" type error.
whereis iwpriv_usage.txt?

---

### Post by Austin_KW on 2007-07-20
> **qrprat77 said:**
> This line produces a "command not found" type error.
whereis iwpriv_usage.txt?

In the Module directory

---

### Post by qrprat77 on 2007-07-20
YEAH!!!!
I have a working internet connexion!   From Reboot!
Yeah!! Now I can mark thread solved!~!!!
Thanks a bunch guys!  It helped a lot.  My wife was starting to think I was going crazy, and well, she was right, but alas, Linux Users save the day!

Oh, and my computer is a Compaq Presario 5000 with an AMD Athlon XP 1.466 GHz and 512 memory.

Final solution for WUSB54Gv4:
Blacklisted ndiswrapper
compiled and installed drivers from serial monkey.
altered interfaces file to read:
    auto rausb1
iface rausb1 inet dhcp
    pre-up ifconfig rausb1 up
    pre-up iwconfig rausb1 mode managed
    pre-up iwpriv rausb1 auth 3
    pre-up iwpriv rausb1 enc 3
    pre-up iwconfig rausb1 essid "MyESSID"
    pre-up iwpriv rausb1 wpapsk **********
    pre-up iwconfig rausb1 essid "MyESSID"

apparently the critical difference was the LOWER CASE wpapsk.

Thanks again guys,
Prollum solved!
Now, on to getting my DVDs to play right!!!!

---

### Post by qrprat77 on 2007-07-20
Did I speak too soon??

Ok, Just failed the "wait and see" test that I passed when running rutilt
apparently when you go to screen saver, the connection drops or something.  Is this a router issue or an interface issue?  running /etc/init.d./networking restart fixed the connection problem.

---

### Post by qrprat77 on 2007-07-20
Ok, Maybe it was wrong!
Just passed the wait and see test.
Maybe I just needed a restart!!!
Will mark as solved...

---

### Post by cwood06 on 2007-07-21
Howdy Im having the same problems i has the WUSB54gv4 as well.

I removed the netowork-manager, in compiled the rt2570 driver and installed it but whenever i i modprobe -l the old drivers are still there. I try to use modprobe -r "w/e module" it seams like it works then when i do a modprobe -l | grep rt2 its still there.

So whats going on?

---

