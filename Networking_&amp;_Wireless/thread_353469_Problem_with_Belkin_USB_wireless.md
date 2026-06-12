---
title: "Problem with Belkin USB wireless"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by revengeska on 2007-02-04
Hi.  I'm using Ubuntu 6.10 and have been trying to configure a Belkin F5D7050 usb device to work with our network.  Unfortunately I don't know what version it is, or how to check, but I used the driver provided on the cd.    I followed the specific instructions found [*here*]("http://ubuntuforums.org/showthread.php?p=2015668"), but on step 11, the wireless still didn't work.  I wasn't sure about the essid, but I checked the network on my windows machine, and the default network name was linksys, so I'm assuming that's what it was.  I installed the ndisgtk and it showed the driver as being installed and the hardware present as yes.  Right now I have the networking icon up in the corner saying "Not connected" and clicking on it says "No networking devices have been found."  The lsusb command outputs:

Bus 004 Device 003: ID 050d:705c Belkin Components

The iwconfig command outputs:

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:-2147483648 dBm   Sensitivity=0/3  
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The iwlist scanning outputs:

wlan0     No scan results

I know the network is currently up because my windows box can find and connect to it.  I'm completely clueless on what could be wrong.  Anyone have an idea?  Thanks.

---

### Post by revengeska on 2007-02-05
Bumping this, since it's still unresolved.

---

### Post by bmartin on 2007-02-08
I'd like to apologize in advance for the technical details below. These instructions will require you to remove ndiswrapper. This is a "more native" approach; it uses a kernel module built for using your WiFi device in Linux. If you don't want the technical jargon, just skip right to the instructions below the dashed line. The rest of this probably doesn't concern you.


Before following these instructions, you should know that I've been talking w/ the guys in the Fedora Project and they've told me that the following driver doesn't contain support for SNMP. It probably doesn't concern you (unless you're on a huge network running SNMP), but I thought I'd throw it out there as a disclaimer.

Additionally, this solves two problems:

1. The "stack" size of your kernel doesn't need to be modified to ensure this driver works. I had that problem when I was using Fedora and ndiswrapper with a 4K kernel stack size.

2. Having to use ndiswrapper at all, at the expense of having to compile a new kernel module each time a new kernel is released.

-----------------------

I have this same WiFi USB stick (7050) and I went through the same problem. I found the answer on this website:

[http://opensource.bureau-cornavin.com/belkin/index.html](http://opensource.bureau-cornavin.com/belkin/index.html)

I contacted the author for several reasons and the page has been revised. I've tested this on both Ubuntu Edgy and Fedora Core 6 and it works.

If you have any problems, let me know. Make sure you follow the directions carefully in the "What next?" section. You may need additional software if your network uses WPA encryption; I currently have WEP set up :-( 

Let me know if this solves your problem. This device is fairly inexpensive and I expect that a lot of people are having problems with it. You should recompile a new kernel module after every kernel update... unless Ubuntu has some way of getting around that annoyance. I'm new to Ubuntu so I'm unsure.

---

### Post by yigal.weinstein on 2007-02-26
bmartin I have a 7050.  I have used the commercial and am now using serialmonkey's it is really nice to be able to use open source.  I want WPA if possible, have you attempted this and if so with what result?

---

### Post by bmartin on 2007-02-26
I found this while browsing the Puppy Linux forums: [http://www.murga-linux.com/puppy/viewtopic.php?search_id=520290594&t=14252](http://www.murga-linux.com/puppy/viewtopic.php?search_id=520290594&t=14252)

I haven't tried. You could try a Google search for "wpa supplicant"; that might be about your best bet. I don't know what drivers it works with.

---

### Post by yigal.weinstein on 2007-02-26
I already have a promising link in the serial monkey forum

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=18804&sid=f7efc128290649aff89133b106db511a]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=18804&sid=f7efc128290649aff89133b106db511a")

but if someone actually has it working that would be good to know.  I know there is the Italian wiki entry that uses wpa but I couldn't get my set up to work this way.  

I also don't really care if I use wpa client or simply /etc/network/interfaces .  In fact the 2nd method is more comfortable to me.

---

### Post by yigal.weinstein on 2007-02-28
WPA is very easy on this card but it took me until now to get it to work followed the wiki for the rt73 gnu version,

iface rausb0 inet dhcp
        pre-up ifconfig rausb0 up
        pre-up ifconfig rausb0 down
        pre-up ifconfig rausb0 up
        pre-up iwconfig rausb0 essid "your wireless id"
        pre-up iwconfig rausb0 mode Managed
        pre-up iwpriv rausb0 set AuthMode=WPAPSK
        pre-up iwpriv rausb0 set EncrypType=TKIP
        pre-up iwpriv rausb0 set WPAPSK="your key"
        pre-up ifconfig rausb0 up

good stuff

---

