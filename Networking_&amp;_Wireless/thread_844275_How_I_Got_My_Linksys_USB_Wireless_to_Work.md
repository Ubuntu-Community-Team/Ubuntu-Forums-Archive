---
title: "How I Got My Linksys USB Wireless to Work"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by kvmapr on 2008-06-29
In the spirit of "write this down before you forget it", I want to record my experiences getting Linksys 802.11 b Wireless-B USB Network Adapter (model WUSB11 ver. 2.8
) working in Ubuntu 7.10 (should also work for 8.04, but haven't tried it yet).

First I used this thread on launchpad, it's not exactly a "how-to" but there's enough clues there that you can figure it out:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152626](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152626)

I also mined some useful make and make install info from this thread:
[http://ubuntuforums.org/showthread.php?t=597476](http://ubuntuforums.org/showthread.php?t=597476)

I'll try to fill in some of the gaps with this post.

Background: I'm running a new Dell Inspiron 530n preloaded with Ubuntu 7.10 (Gutsy Gibbon). The kernel Dell ships with this factory install is 2.6.22-15-generic. The Linksys WUSB11 uses the Atmel at76c505a chipset (I'm lead to believe) and Ubuntu drives it with the at76_usb driver. Only version 0.14beta1 appears to ship with Ubuntu 7.10 and 8.04, but that version does not appear to work well with Network Manager 0.65, nor could I get to connect to either an WEP-enabled, or WEP-disabled, wireless network.

Note however that you can get wireless up and running using this version of the driver if you skip Network Manager and go to the command line:
1 - Open a terminal session and on the command line:

2 - execute> lsmod |grep at76
#checking to see if the at76_usb module is loaded, assumes your linksys USB #is plugged in to an available USB port. My output looks like this:
#
#kvmapr@dell-desktop:~$ lsmod |grep at76
#at76_usb               78296  0 
#usbcore               138632  5 at76_usb,usbhid,ehci_hcd,uhci_hcd

3 - execute> iwconfig
#lists the network interfaces with wireless capabilities, in my case it's #labelled wlan1. Note the ESSID field, useful info later. My output looks like this:
#lo        no wireless extensions.
#eth0      no wireless extensions.
#wlan1     IEEE 802.11b  ESSID:"PWIN2"  
#         Mode:Managed  Frequency:2.447 GHz  Access Point:..:..:..:..:B3:72   
#          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
#          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
#          Power Management: off
#          Link Quality:83/100  Signal level=83/100  
#          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
#          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


4 - execute> ethtool -i wlanX
#where X is the number of the wireless network interface reported on your #system by iwconfig. My output on wlan1 looks like this: 
#driver: at76_usb
#version: 0.17
#firmware-version: 1.101.0-86
#bus-info: usb-0000:00:1a.2-1

Note that I have version 0.17 of the driver installed already. Yours should show "0.14beta1" or something to that effect. Also note that my firmware version is different. This two must be upgraded to use the 0.17 version of the driver (we'll get to it below).

5 - execute> iwlist wlan1 scan
#this generates a list of wireless networks that your linksys can hear, #even thought you're still using version 0.14beta1 of the driver. My output #is too long to replicate here (at least 10 networks in my immediate #vicinity)

For this next part, you'll need to turn off WEP on your wireless access point if you want to connect successfully. Or, as in my case, if there's another access point with no encryption enabled (and a strong enough signal) you may connect to it.

6 - sudo dhclient wlanX
#remember to replace the X with the number of your wlan entry reflected by the output of iwconfig. This command executes a dhcp request from your command line and has always worked for me, when connecting to a non-WEP enabled access point and using version 0.14beta1 of the at76_usb driver. Note: After starting up your machine, Network Manager is normally churning away and trying to connect to a network. You must allow Network Manager to report it's failure and then "cancel" any more efforts. If Network Manager is actively trying to connect to a network, this command line dhcp request will fail.

This approach allowed me to get a basic network connection up and running so that I could do the additional search and downloads I need to upgrade my driver and get WEP working with the Linksys USB wireless.

Now for the good stuff:

Version 0.17 of the at76_usb driver is available from the developer at:
[http://developer.berlios.de/projects/at76c503a/](http://developer.berlios.de/projects/at76c503a/)

There are two packages there that you'll want to download and install:
at76_usb version 0.17 and
at76_usb-firmware version 0.1

I extracted the driver download file, at76_usb-0.17.tar.gz, into its own directory in my $HOME directory (execute> echo $HOME  on the command line if you don't know what that is). I did the same for the firmware, at76_usb-firmware-0.1.tar.gz.

Then I ran 'make' from the command line in each of those directories. This compiled the software with no apparent errors.

Next I ran 'sudo make install' from the command line, first in the driver directory, then in the firmware directory. This was supposed to load the driver, and firmware, but after a reboot I did an 'ethtool -i wlan1' and it showed that the version 0.14beta1 driver was still being loaded.

After much mucking about I finally noticed the line from "Gustavo Rahal" in that Launchpad link I provided above. Gustavo said - "I was actually a bit lazy and just noticed that I could copy the compiled .ko into /lib/modules/2.6.22-14-generic/ubuntu/wireless/at76/. Did that and it worked fine."

I looked at this and found that I had the same directory path:
/lib/modules/2.6.22-14-generic/ubuntu/wireless/at76/

But I know I'm running kernel version 2.6.22-15-generic based on the command line output of 'uname -r'. So when I went to check for a directory at /lib/modules/2.6.22-14-generic/ubuntu/wireless/at76/ ... it was there and the at76_usb.ko file was listed. I could tell by comparing the creation date and file size (output from 'ls -la' command) that this was not the same ".ko" file as I had just compiled with the make command.

So I backed up the file at76_usb.ko to at76_usb.ko.0.14beta1.ko with the command: 'sudo cp at76_usb.ko at76_usb.ko.0.14beta1.ko'

Note that you have to be in the directory /lib/modules/2.6.22-15-generic/ubuntu/wireless/at76/ for this to work.

Then I copied the newly compiled at76_usb.ko file from where I ran "make" in my $HOME directory to the directory at /lib/modules/2.6.22-15-generic/ubuntu/wireless/at76/

You must do this with "sudo cp" in order to overwrite the existing .ko file. Then I used chown (change owner) and chgrp (change group) to put the new .ko file under root ownership and in the root group. Here's the command line:
execute> chown root at76_usb.ko
execute> chgrp root at76_usb.ko

Then I rebooted my machine, and when it came up the output of> 
ethtool -i wlan1  showed me:
driver: at76_usb
version: 0.17
firmware-version: 1.101.0-86
bus-info: usb-0000:00:1a.2-1

(Make install seemed to load the firmware just fine, no need for manual intervention.)

After this Network Manager works as designed and I can connect to my WEP enabled wireless network with no problems.

Hope this can help you.
KVMAPR

---

### Post by kvmapr on 2008-07-10
Thought I would post a follow up to this. A couple days ago I upgraded my default 7.10 install to Hardy Heron, 8.04. And of course wireless stopped working. But I used the steps outlined above to first start wireless from the command line, just as before, connecting to a non-WEP enabled network (just to test that it would still work, really). Then I went back into the directory where I had extracted at76_usb.ko before, and ran "make" then "sudo make install". This recompiled the driver to work with the new kernel (the driver is now a different file size than when using kernel 2.6.15).

Just as before, the make worked, but the make install did not. So I once again copied the .ko file to it's new destination for the updated kernel 2.6.18, or specifically to: 
/lib/modules/2.6.24-18-generic/ubuntu/wireless/at76/

Did the reboot and once again, joy prevails.

But what this tells me is I need to learn more about installing modules to the linux kernel. This approach of manually copying the driver to a new directory location is what we would call, in the old days, a kludge.

Cheers,
kvmapr

---

### Post by tablaboi on 2008-08-23
Hi,

I was able to install the driver easily--however, I"m having trouble installing the firmware. When I did make on the firmware directory, I got the following error: 

```


vikas@vikas-desktop:~$ cd at76_usb-firm* 
vikas@vikas-desktop:~/at76_usb-firmware-0.1$ make 
make: *** No targets specified and no makefile found.  Stop. 


```

What am I doing wrong?

---

### Post by EricFC on 2008-11-12
kvmapr:

Your technique worked great for me with Hardy (thank you!), but it doesn't seem to work for Intrepid.  I get a slew of errors when I attempt to 'make' and the path under /lib/modules appears different for Intrepid - I haven't been able to find the wireless drivers (yet).

Eric

---

### Post by theSpaceAmoeba on 2009-01-23
I want to thank kvmapr for their VERY helpful post. After three days I finally have internet in Jaunty Alpha 3! Thanks much!

One new point, though. Since kernel 2.6.27 you need to apply a patch to the original at76_usb.c file: [http://developer.berlios.de/patch/?group_id=727](http://developer.berlios.de/patch/?group_id=727)

After that, it will compile fine. All of the other directions work great.

---

