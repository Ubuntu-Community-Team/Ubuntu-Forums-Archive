---
title: "wpa option does not show in network settings"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by 1feistymedic on 2007-07-29
I have a Linksys WUSB54GC wifi device that supports WPA encryption.  For some reason that option is not available in the network settings.  The only options that are available are:

WEP key (hexadecimal)
WEP key (ascii)

How do I enable WPA encryption for this card?  And please make it very simple and step by step as I am the nu-est of nubians.  Thanks.  Everything else on the network is using WPA.

---

### Post by noob12 on 2007-07-29
Assuming you are running Feisty based on your forum name.  If this is incorrect, let me know.

Try this.  In the network manager settings you should leave the device in Roaming mode. Left-click on the Network Manager applet icon in the panel and left-click.  Select the network you want to connect to.  The right options should show up in the dialog box that comes up.

If you have more trouble, we'll want to run some diagnostic commands.

---

### Post by 1feistymedic on 2007-07-29
Yes..I am running Feisty....

The network icon, the two dots with the blue comet swirly looking thing, is swirling...THis is what happens when I try to connect..

1)I left click the swirly dots and click on "manual configuration
2) I click on "wireless connection (wlan0)
3)I click properties
4) I uncheck "enable roaming mode"
5)I go to password type and the only two choices are "wep key (hex)" and "wep key (ascii)
6)when I try to connect it states that the security level is not supported by my device


my router is a wrt54g Linksys

Thanks

---

### Post by 1feistymedic on 2007-07-29
the wifi card wusb54gc does support wpa....it does in windows OS

---

### Post by noob12 on 2007-07-29
To use WPA, you actually want Roaming Mode enabled.  Do not select manually configured.

When you left click on the network manager icon in the panel, you should see a list of SSIDs that your wireless device can see.  If you don't see any SSIDs, we need to do further diagnostics.

The following would help as a start to make sure the wireless device is seeing your router:
> 
iwlist scan


You need the wpasupplicant package installed if you haven't already
> 
aptitude show wpasupplicant


If it says it is not installed, then

> 
sudo aptitude install wpasupplicant


---

### Post by 1feistymedic on 2007-07-29
My SSID does show up....I re-checked roaming mode....when I did iwlist in the terminal it told me that for "lo" and "etho" interface does not support scanning..and for "wmaster0" it states failed to read scan data: operation not supported and "wlan0" states: no scan results..

I did the "aptitude show wpasupplicant" and it states it's installed

---

### Post by noob12 on 2007-07-29
Based on the iwlist output, I think there's a more fundamental problem configuring the device, which we will probably have to diagnose.

I'm puzzled that your SSID does show up in the network manager list.   Do you see a signal bar to the right of the SSID name in that list?  What happens when you select this SSID?  If things are normal, you should get a dialog box for entering the WPA authentication information at that point.

---

### Post by 1feistymedic on 2007-07-29
I see a signal bar with no signal in it

---

### Post by 1feistymedic on 2007-07-29
WPA is till not an option open to me.....only:

 wep key (hex)" and "wep key (ascii)

---

### Post by noob12 on 2007-07-29
OK.  It looks like the wireless device is not really set up.  We need to take a few steps back and get the wireless device working, then we can tackle WPA.

Can you fill me in on what you did to set up the device so far?  Did you install any drivers already?

---

### Post by 1feistymedic on 2007-07-29
At first I installed a windows driver with ndiswrapper and couldn't get it to work...

out of frustration for a whole weeks work and surfing the net for fixes I reinstalled Ubuntu Feisty today....

All I did was plug in the device and apparently Feisty has drivers built in to recognize the card...

I have not done any other configuration to the card

---

### Post by noob12 on 2007-07-29
Can you post the output of
```
sudo lsusb -v
```

---

### Post by 1feistymedic on 2007-07-29
I sure can....I first have to bring it down to the basement and connect it to the ethernet cable...that way I can copy and paste the results.....stand by

---

### Post by 1feistymedic on 2007-07-29
lsusb -v

Bus 001 Device 003: ID 13b1:0020 Linksys 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x13b1 Linksys
  idProduct          0x0020 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0         8
  idVendor           0x0451 Texas Instruments, Inc.
  idProduct          0x1446 TUSB2040/2070 Hub
  bcdDevice            1.10
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0 
      UNRECOGNIZED:  09 29 04 09 00 32 64 00 1e
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

---

### Post by 1feistymedic on 2007-07-29
if there are any other settings I need to check on, please let me know....I can have them all ready for review the next time you log on...thanks

---

### Post by inque_54 on 2007-07-29
I'm on the same boat with the OP

I'm also configuring a wifi connection to be able to connect to our WPA secured network

Anybody got any new info on this?

---

### Post by fizikz on 2007-07-29
Count me as another person with the same problem. I'm surprised that the Ubuntu support team hasn't come up with a clear solution to this issue. I originally had installed Ubuntu, but because of this wireless connection problem, I went with OpenSuse 10.2 which detected and configured the wireless straight out of the box. Now, I still want to try Ubuntu so I'm battling with this problem again. But on the whole, this one issue has been a major deterrent for me from being more enthusiastic about Ubuntu, as it has caused me to waste several days trying to resolve what should be a simple matter. 

In any case, I'll be watching this thread and if I get my wireless working I'll post.

---

### Post by noob12 on 2007-07-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89665](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89665) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You other guys may have a different problem.  

The original poster 1feistymedic has a usb wireless device (13b1:0020 Linksys) with the rt73 chipset and is running 7.04 Feisty.  There is a driver rt73usb in Feisty that will bind to this device and according to most reports it doesn't really seem to work.   See the associated bug URL I've put on this thread. 

I don't have direct experience with this device.  Based on my crude survey of the forum and bug list, most of the people that have got it working have used much more recent rt73 drivers built from sources at serialmonkey following essentially the method in this post [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236).

This has several issues:
- it's not for the faint of heart; fairly long though straightforward instructions
- serialmonkey doesn't have tested versioned source snapshots of this
  driver; you get a daily tarball only.
- it is reported not to work with network manager, so you will still have
  to directly edit essid and wpa info into conf files.  


See also this thread [http://ubuntuforums.org/showthread.php?t=508093](http://ubuntuforums.org/showthread.php?t=508093) for another user's walk down this path with good help from kevdog.

If 1feistymedic still wants to walk through this, I can try to help troubleshoot.

---

### Post by noob12 on 2007-07-29
As for the other two posters **fizikz** and **inque_54**, the first step is to determine the device chipset you have in your device.  That determines what path you need to take to get it working.  You may be in an entirely different situation with somewhat similar symptoms.  You probably should start new threads unless you know yourself to have the same device as the feisty medic.

---

### Post by kevdog on 2007-07-29
Because your device seems to have an ra chipset either go with the serial monkey drivers as explained in the above thread, or downgrade to edgy where the linux built in drivers and network manager do work "essentially out of the box".  Im not sure what happened with the Feisty upgrade, but the rt driver and network manager relationship was broken.

---

### Post by fizikz on 2007-07-30
I got my problem solved. Like noob12 mentioned your problem may be different, but just in case it turns out helpful, here's what worked for me. I had to enable SSID broadcasting on my router. I had previously turned this feature off as a security measure. Now with it enabled everything is working fine. FYI, I'm using Ubuntu 6.06 and Intel's drivers ipw3945 as well as wpasupplicant and gnome network manager. I hope it gets worked out for you.

---

### Post by inque_54 on 2007-07-30
Finally got my problem solved with this [thread ]("http://ubuntuforums.org/showthread.php?t=419709&highlight=RT2561%2FRT61")

Not sure though if it could be applicable with your Linksys device, but could be worth a shot? 

FYI: I had the same model of lan card that is mentioned in the link

---

### Post by 1feistymedic on 2007-07-30
Thanks all.  I looked at the other posts you referenced and I think I would like to try the serial monkey.

Actually, I have seen all those posts before and tried the serial monkey tarball and could not get the command line entries to work in the terminal.  

When I see the commands I am to enter, I don know if it is one continuous line or if I have to press the enter key in between each entry...also when there are things to enter that I have to supply  such as a prompt like: < your id>, do I leave the "<  >" marks in the command or am I supposed to delete those...

p.s....how do you reference another post in a reply so it shows up as a link?  Thanks
Like I said earlier, I am the nu-est of the nubians....I don know the difference between tarballs and furballs....so If you could help me decipher the commands to enter as a baby-step-by-step walkthrough, I would gladly appreciate it!

The wife and kids would also gladly appreciate it!

This old PC and 17¨ CRT monitor is getting to be a back breaker carrying it up and down two flights of stairs :sad:

---

### Post by 1feistymedic on 2007-07-30
I will be back soon....have to eat breaksfast.....:popcorn:

---

### Post by kevdog on 2007-07-30
Assuming your device runs on the rt73 chipset (I have no way to confirm this), have you seen this post:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

---

### Post by 1feistymedic on 2007-07-30
Yes I did see the post.  My card does run on the rt73.  I tries everything on the post you mentioned.  But as I stated earlier, I am such a nubian that the command line entries on the post are confusing and not working when I input them in the terminal.  Is there anyway that they can be made even simpler?  I am not brilliant but I can copy and paste.  Thanks.

---

### Post by diepruis on 2007-07-30
> **1feistymedic said:**
> Yes I did see the post.  My card does run on the rt73.  I tries everything on the post you mentioned.  But as I stated earlier, I am such a nubian that the command line entries on the post are confusing and not working when I input them in the terminal.  Is there anyway that they can be made even simpler?  I am not brilliant but I can copy and paste.  Thanks.

Why don't you just get started with the HOWTO and when you run into a specific problem (like an error message), you can ask us for help with that specifically?

---

### Post by 1feistymedic on 2007-07-30
ok...I am following the "how to"in this thread :  

 HOWTO: RT73 (RT71) serialmonkey drivers
Currently, the wiki page on rt73 drivers is a tad out of date. I found that many of the instructions didn't make sense, as ralink have apparently changed things without incrementing the driver version.

A much simpler approach to getting this chipset to work is using the drivers from rt2x00.serialmonkey.com The only drivers available from this site for rt73 devices is CVS source code, so it might be slightly unstable. I haven't experienced any problems so far, however. If you do experience problems with the driver, please upload debug information to their forums. See the TESTING file (which comes with the source code) for more information on how to do this.

Okay, so here's a quick howto on setting up your rt73 / rt71 device to work in Linux by using a completely free driver.

   1. Open a terminal.
   2. Go to the directory where we'll keep the driver's source code:
      Code:

      cd /usr/src

   3. Download the source code. (NOTE: because /usr/src is a privileged directory, we'll need to prefix all our command with sudo from here on. Type "man sudo_root" for more information.)
      Code:

      sudo wget [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) -O /usr/src/rt73-cvs-daily.tar.gz

   4. If you have no internet access on the Linux install already, you will need to download this file from another PC (or from Windows) and then copy it to /usr/src. Just copy the file to a flash disk or something, boot your Linux install and copy the file to your home directory. Then do the following in a terminal:
      Code:

      sudo cp ~/rt73-cvs-daily.tar.gz /usr/src

apparently I am stuck at this point by looking at a copy of my terminal below:

sean@desktop:~$ cd /usr/src
sean@desktop:/usr/src$ sudo wget [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) -O /usr/src/rt73-cvs-daily.tar.gz
Password:
--11:57:31--  [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)
           => `/usr/src/rt73-cvs-daily.tar.gz'
Resolving rt2x00.serialmonkey.com... 208.100.15.174
Connecting to rt2x00.serialmonkey.com|208.100.15.174|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 302,419 (295K) [application/x-tar]

100%[====================================>] 302,419        1.27M/s             

11:57:31 (1.27 MB/s) - `/usr/src/rt73-cvs-daily.tar.gz' saved [302419/302419]

sean@desktop:/usr/src$ sudo cp ~/rt73-cvs-daily.tar.gz /usr/src
cp: cannot stat `/home/sean/rt73-cvs-daily.tar.gz': No such file or directory
sean@desktop:/usr/src$ 



Tank you!

---

### Post by noob12 on 2007-07-30
The cp is not necessary since you have network connectivity and downloaded already to /usr/src.  Proceed to the next step!  The moon beckons.

---

### Post by diepruis on 2007-07-30
> **noob12 said:**
> The moon beckons.

Lol. Style.

---

### Post by 1feistymedic on 2007-07-30
Ok..Since you stated the "cp"command was not necessary, assuming you meant this one:

#  If you have no internet access on the Linux install already, you will need to download this file from another PC (or from Windows) and then copy it to /usr/src. Just copy the file to a flash disk or something, boot your Linux install and copy the file to your home directory. Then do the following in a terminal:
Code:

sudo cp ~/rt73-cvs-daily.tar.gz /usr/src

.......I went to the next command as follows:

xtract the archive you just downloaded.
Code:

sudo tar -xvzf rt73-cvs-daily.tar.gz

......And this is what I got:


sean@desktop:~$ sudo tar -xvzf rt73-cvs-daily.tar.gz
Password:
tar: rt73-cvs-daily.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
sean@desktop:~$ 

What in the world is going on?  I copied and pasted correctly.  Please assist.  Thank you.

---

### Post by noob12 on 2007-07-30
In the interim, you resumed in your home directory, but the instructions assumed you had stayed in the /usr/src directory.

```

cd /usr/src

```

Then resume the instructions where you were...

```

sudo tar -xvzf rt73-cvs-daily.tar.gz

```

and continue...

---

### Post by 1feistymedic on 2007-07-30
ok....that helped and got me a little further.....

now apparently I am stuck at step number 7 from the post [COLOR="Blue"]"HOWTO: RT73 (RT71) serialmonkey drivers" [/COLOR]as follows:

# If you don't have internet access on the Linux install, refer to the section below.
# Compile the module.
Code:

[COLOR="Red"]cd /usr/src/rt73-cvs-yyyymmddhh/Module
sudo make[/COLOR]

...a copy of the terminal is shown below....

sean@desktop:~$ cd /usr/src
sean@desktop:/usr/src$ sudo tar -xvzf rt73-cvs-daily.tar.gz
Password:
rt73-cvs-2007073010/
rt73-cvs-2007073010/FAQ
rt73-cvs-2007073010/THANKS
rt73-cvs-2007073010/CHANGELOG
rt73-cvs-2007073010/CVS/
rt73-cvs-2007073010/CVS/Root
rt73-cvs-2007073010/CVS/Repository
rt73-cvs-2007073010/CVS/Entries.Log
rt73-cvs-2007073010/CVS/Entries
rt73-cvs-2007073010/LICENSE
rt73-cvs-2007073010/Module/
rt73-cvs-2007073010/Module/auth.c
rt73-cvs-2007073010/Module/rt73.h
rt73-cvs-2007073010/Module/rt73.bin
rt73-cvs-2007073010/Module/rt2x00debug.h
rt73-cvs-2007073010/Module/md5.c
rt73-cvs-2007073010/Module/rtusb_data.c
rt73-cvs-2007073010/Module/rtmp_main.c
rt73-cvs-2007073010/Module/rt_config.h
rt73-cvs-2007073010/Module/assoc.c
rt73-cvs-2007073010/Module/CVS/
rt73-cvs-2007073010/Module/CVS/Root
rt73-cvs-2007073010/Module/CVS/Repository
rt73-cvs-2007073010/Module/CVS/Entries
rt73-cvs-2007073010/Module/wpa.c
rt73-cvs-2007073010/Module/sync.c
rt73-cvs-2007073010/Module/rtmp_info.c
rt73-cvs-2007073010/Module/iwpriv_usage.txt
rt73-cvs-2007073010/Module/rtusb_bulk.c
rt73-cvs-2007073010/Module/mlme.h
rt73-cvs-2007073010/Module/connect.c
rt73-cvs-2007073010/Module/rtmp_tkip.c
rt73-cvs-2007073010/Module/auth_rsp.c
rt73-cvs-2007073010/Module/oid.h
rt73-cvs-2007073010/Module/rtmp_init.c
rt73-cvs-2007073010/Module/TESTING
rt73-cvs-2007073010/Module/rtusb_io.c
rt73-cvs-2007073010/Module/rtmp.h
rt73-cvs-2007073010/Module/mlme.c
rt73-cvs-2007073010/Module/md5.h
rt73-cvs-2007073010/Module/wpa.h
rt73-cvs-2007073010/Module/rtmp_wep.c
rt73-cvs-2007073010/Module/rtmp_def.h
rt73-cvs-2007073010/Module/Makefile
rt73-cvs-2007073010/Module/rtmp_type.h
rt73-cvs-2007073010/Module/sanity.c
rt73-cvs-2007073010/README
sean@desktop:/usr/src$ sudo aptitude install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev 
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev 
  linux-libc-dev 
0 packages upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 667kB/8053kB of archives. After unpacking 33.7MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main linux-libc-dev 2.6.20-16.29 [667kB]
Media Change: Please insert the disc labeled 'Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)' in the drive '/cdrom/' and press enter

Fetched 667kB in 2m3s (5386B/s)                                                 
Selecting previously deselected package linux-libc-dev.
(Reading database ... 106596 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.20-16.29_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.5-0ubuntu14_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.24ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up linux-libc-dev (2.6.20-16.29) ...
Setting up libc6-dev (2.5-0ubuntu14) ...
Setting up dpkg-dev (1.13.24ubuntu6) ...
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...
sean@desktop:/usr/src$ [COLOR="Red"]cd /usr/src/rt73-cvs-yyyymmddhh/Module[/COLOR]
bash: cd: /usr/src/rt73-cvs-yyyymmddhh/Module: No such file or directory
sean@desktop:/usr/src$ cd /usr/src/rt73-cvs-yyyymmddhh/Module
bash: cd: /usr/src/rt73-cvs-yyyymmddhh/Module: No such file or directory
sean@desktop:/usr/src$ 


thanks for your continued patience with me....I really appreciate it!

---

### Post by noob12 on 2007-07-30
The yyyymmddhh is short for whatever source bundle you got.  In your case, seeing from the extraction, it is
```
cd /usr/src/rt73-cvs-2007073010/Module
```

onward!

---

### Post by 1feistymedic on 2007-07-30
ok..now we are cooking with gas!  I got to this step in the process:

[COLOR="Red"]If the module is too big, strip unnecessary stuff from it.

On some systems, the rt73 kernel module compiles to a file that is unnecessarily large. If this happens to you, you will receive a warning like this:
Code:

!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'

If you want to make doubly sure, you can check the file's size by typing
Code:

ls -alh rt73.ko[/COLOR]

This is what shows in terminal:

sean@desktop:~$ cd /usr/src/rt73-cvs-2007073010/Module
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo make
Password:
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/rtmp_main.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/mlme.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/connect.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/rtusb_bulk.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/rtusb_io.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/sync.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/assoc.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/auth.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/auth_rsp.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/rtusb_data.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/rtmp_init.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/sanity.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/rtmp_wep.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/rtmp_info.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/rtmp_tkip.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/wpa.o
  CC [M]  /usr/src/rt73-cvs-2007073010/Module/md5.o
  LD [M]  /usr/src/rt73-cvs-2007073010/Module/rt73.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/src/rt73-cvs-2007073010/Module/rt73.mod.o
  LD [M]  /usr/src/rt73-cvs-2007073010/Module/rt73.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'
*** Module rt73.ko built successfully
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ ls -alh rt73.ko
-rw-r--r-- 1 root root 2.7M 2007-07-30 21:39 rt73.ko
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ 


..soooo the question is now, do I have to do the following?:

If the file's size is in the megabytes, you are affected by this issue (it's not really a bug).

Luckily this is easily fixed, just type
Code:

[COLOR="Red"]sudo strip -S rt73.ko[/COLOR]

Thanks....

---

### Post by noob12 on 2007-07-30
Yep.

---

### Post by 1feistymedic on 2007-07-30
ok..looks like another problem.....I did the following as directed here:

[COLOR="Red"]# Luckily this is easily fixed, just type
Code:

sudo strip -S rt73.ko

As Abadaar points out, that -S might appear to be lower case on some displays, note that it should be upper case.

All this does is remove debugging symbols, which most users don't require. After the strip command, you can check the file size again, it should be around 240K.
# Install the module.
Code:

sudo make install[/COLOR]

and this is what I got in terminal:

sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ ls -alh rt73.ko
-rw-r--r-- 1 root root 2.7M 2007-07-30 21:39 rt73.ko
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo strip -S rt73.ko
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ ls -alh rt73.ko
-rw-r--r-- 1 root root 242K 2007-07-30 21:48 rt73.ko
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo make install
*** Install module in /lib/modules/2.6.20-16-generic/extra ...
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/src/rt73-cvs-2007073010/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  INSTALL /usr/src/rt73-cvs-2007073010/Module/rt73.ko
  DEPMOD  2.6.20-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for wlan*
[COLOR="Blue"]grep: /etc/modprobe.conf: No such file or directory[/COLOR]
*** Install firmware in /lib/firmware ...
*** Check config ...
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ 


..should the highlighted part in blue say "no such directory"?

---

### Post by noob12 on 2007-07-30
That's ok.  Proceed.  We can add the alias later if you want.  It's not needed.

This is kind of like non-instant messenger.

---

### Post by 1feistymedic on 2007-07-30
ok..that didn not go very far....I am at this step: 
[COLOR="Red"]
Make sure neither the Ubuntu, nor the RaLink modules are loaded (the former doesn't work, while the latter causes conflicts). Some other modules need to be removed as well. Don't worry if your computer complains about these modules not being found - that's a good thing.
Code:

sudo ifconfig wlan0 down
sudo modprobe -r rt73usb
sudo modprobe -r rt2570
sudo modprobe -r rt2500usb
sudo modprobe -r rt2x00lib[/COLOR]

I entered the sudo iconfig wlan0 down command and got this in the terminal:

sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo ifconfig wlan0 down
Password:
wlan0: ERROR while getting interface flags: No such device
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ 


Is this right?  and also, do I enter all the sudo commands at onceas a copy and paste or as separate lines at the command prompts?  Thanks...

---

### Post by kevdog on 2007-07-30
You are doing great so far.  Your interface might not be wlan0 but may be something like eth0, eth1, ra0, etc.

To determine your interface name assigned to your card, do the following:

lshw -C network

Look for the section pertaining to your wireless card.  With the section should be a logical name, such as the following:

```
 *-network
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
     **  logical name: wlan0**
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.47+Cisco-Linksys ,LLC.,02/19/2 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11
```

Now instead of wlan0, substitute whatever your interface name is.  So continue on with the instructions but remember to substitute your own interface name.

---

### Post by noob12 on 2007-07-30
Yep.  What kevdog says.  Thanks.

---

### Post by 1feistymedic on 2007-07-30
ok...I think it did not work before because I didn have the card plugged in....

It seems to have worked now as follows:

sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 9
       bus info: pci@01:09.0
       logical name: eth0
       version: 10
       serial: 00:05:5d:44:6b:5c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.102 latency=66 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:1400-14ff iomemory:40200000-402000ff irq:5
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo ifconfig wlan0 down
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo modprobe -r rt73usb
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo modprobe -r rt2570
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo modprobe -r rt2500usb
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo modprobe -r rt2x00lib

When I tried to do the blacklist part, this is what I got on the terminal:

sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ gksu gedit /etc/modprobe.d/blacklist

(gedit:6856): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ 

..I would assume something went wrong...was I supposed to do this from a different prompt other than : "Module$"?

Thanks....

---

### Post by kevdog on 2007-07-30
Are you sure that is your wireless card???

The card you listed is using eth0 and has a realtek driver/chipset, not an ra chipset -- there is a difference.

---

### Post by 1feistymedic on 2007-07-30
Sorry...this is what it shows after I did the "lshw -C network"with the card plugged in:



sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 9
       bus info: pci@01:09.0
       logical name: eth0
       version: 10
       serial: 00:05:5d:44:6b:5c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.102 latency=66 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:1400-14ff iomemory:40200000-402000ff irq:5
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$

---

### Post by noob12 on 2007-07-30
Good.  This is the part about the wireless card.

> 
*-network DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=RT73 WLAN


It's ok so far.  You have put the interface down and it looks like you haven't probed the driver module yet.

In order for the gedit to work as root, you may need to first type 
```
xhost +
```

then redo

```
gksu gedit /etc/modprobe.d/blacklist
```

---

### Post by kevdog on 2007-07-30
You see how your wireless card says "Disable".  That's because no driver is currently associated with the card.  Its true you have an ra card with the RT73 driver needed.

Ok lets just check if your driver is correct:
```
modinfo rt73
```

You should get something like the following (Note I dont have the rt73 driver installed but do have the rt2500 driver so hence the difference):
> modinfo rt2500
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2500/rt2500.ko
license:        GPL
description:    Ralink RT2500 802.11g WLAN driver 1.1.0 BETA4 2006/06/18
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     FE0FF717CAE37FC640C6914
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
depends:
vermagic:       2.6.20-16-generic SMP mod_unload 586
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)
parm:           ifname:Network device name (default ra%d) (charp)


If everyhing looks good, see if the module is loaded into the kernel:
```

sudo modprobe -l rt73
```

Again the output should be similar for mine (again Im using rt2500 driver):
> /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2500/rt2500.ko

---

### Post by 1feistymedic on 2007-07-30
ok..I did what you suggested and I got this:



sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ xhost +
access control disabled, clients can connect from any host
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ gksu gedit /etc/modprobe.d/blacklist


plus another window popped up titled "blacklist(/etc/modprobe.d -gedit" that includes the following info:

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

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
[COLOR="Blue"]blacklist r8187[/COLOR]

..if this is correct, then I assume I can continue with this step:

[COLOR="Red"]# Add the following lines to the text file:
Code:

# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib



[/COLOR]

..if so, then where do I paste this to?  If in the blacklist window that popped up do I insert it as a continuation of the last line highlighted in blue above or hit enter once after this line and then paste?

Once I paste, do I save the file by clicking on the  "save" icon on the top left??


I really apologize for being such a noob, but I really appreciate all your help!

---

### Post by kevdog on 2007-07-30
Yes keep going......

---

### Post by 1feistymedic on 2007-07-30
ok..I added it as shown below and chose save....I am continuing on with the instructions...

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

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

[COLOR="Blue"]# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib[/COLOR]

---

### Post by noob12 on 2007-07-30
Yes, you put the blacklist lines in the gedit window that popped up.  This is a text editor like notepad or wordpad on windows.  You will then save the file.

Keep going!

---

### Post by 1feistymedic on 2007-07-30
ok...now I am at this point in the instructions:

[COLOR="Red"]  13.  Configure the interface.
      Code:

      sudo ifconfig wlan0 up
      sudo iwconfig wlan0 essid YOUR_NETWORK_NAME_HERE
      sudo iwconfig wlan0 key YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY
      sudo dhclient wlan0[/COLOR]

I did the "sudo ifconfig wlan0"as shown below

[COLOR="Blue"]sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo ifconfig wlan0 up
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ [/COLOR]

....now I am stuck as to what to put in the part that says [COLOR="Red"]¨sudo iwconfig wlan0 essid YOUR_NETWORK_NAME_HERE".[/COLOR]...I assume it is the network id for my router but do I have to have the "_" (underscore) marks like the directions or do I just type it in normally?  If normally, do I have to have it in all caps?  Thanks....

---

### Post by 1feistymedic on 2007-07-30
oh..I forgot to mention, my router is using WPA....not WEP..Thanks....that may make a difference at this point

---

### Post by noob12 on 2007-07-30
At this point, let's first do the checks that kevdog suggested earlier

Can you
```
modinfo rt73
```

and check that the module loaded

```
sudo modprobe -l rt73
```

and look at 

```
sudo lshw -C network
```

again.

---

### Post by 1feistymedic on 2007-07-30
ok..did those three things and this is what shows in the terminal:

sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ modinfo rt73filename:       /lib/modules/2.6.20-16-generic/extra/rt73.ko
license:        GPL
description:    Ralink RT73 802.11abg WLAN Driver 1.0.3.6 CVS 2007073010
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     89B66F479EABF10D6C2CDA7
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           debug:Debug mask: n selects filter, 0 for none (int)
parm:           firmName:Permit to load a different firmware: (default: rt73.bin)  (charp)
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo modprobe -l rt73
Password:
/lib/modules/2.6.20-16-generic/extra/rt73.ko
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 9
       bus info: pci@01:09.0
       logical name: eth0
       version: 10
       serial: 00:05:5d:44:6b:5c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.102 latency=66 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:1400-14ff iomemory:40200000-402000ff irq:5
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:b6:97:1a:f7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ 

now what do we do?

---

### Post by kevdog on 2007-07-30
For now, since nothing is working, and we would like to do some testing, turn of WEP/WPA/Mac filtering on the router.  Once everything is working we can add this back in.  It will make it a lot easier.  If you have no WEP, then just skip the line above you were enquiring about:

sudo iwconfig wlan0 key XXXX

As far as your essid - just type the name of the router as its entered in the setup, or do a 
```
iwlist scan
```

This should show you the router name

---

### Post by 1feistymedic on 2007-07-30
ok....this is what I did next in the terminal:

sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:F5:D9:AE
                    ESSID:"1serving23jah4"
                    Mode:Managed
                    Channel:11
                    Encryption key:off
                    Bit Rates:0 kb/s

sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:F5:D9:AE
                    ESSID:"1serving23jah4"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s

sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo iwconfig wlan0 essid 1serving23jah4
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo iwconfig wlan0 key off
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:16:b6:97:1a:f7
Sending on   LPF/wlan0/00:16:b6:97:1a:f7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$

---

### Post by noob12 on 2007-07-30
Can you enter just
```
iwconfig wlan0
```
and show us the output?

---

### Post by 1feistymedic on 2007-07-31
Ok..this is what I get....


sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ iwconfig wlan0
wlan0     RT73 WLAN  ESSID:"1serving23jah4"  
          Mode:Managed  Frequency=2.462 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=85/100  Signal level:-54 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ 

Just aside note....the network manager does not show a wireless connection option anymore...I did remember reading somewhere else to uninstall network manager and install something called Rutil because only Rutil will work with serialmonkey....is this so?..thanks...

---

### Post by kevdog on 2007-07-31
Can you just try the following:

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo ifconfig wlan0 essid 1serving23jah4
sudo ifconfig wlan0 mode managed
sudo dhclient wlan0
```

If this doesnt work,
try
```
sudo /etc/init.d/dbus restart
```

and then retype the commands above.  If this doesnt work try rebooting (I know this isnt windows, but for some things this actually works)

AND TURN OFF WEP

---

### Post by noob12 on 2007-07-31
This looks good.  But did you turn all of the encryption on your router off?  The last iwlist scan from your previous message showed encryption on.

---

### Post by noob12 on 2007-07-31
I have to get on my bike home, which means I'll probably miss the moon landing.  Will check up later.

---

### Post by 1feistymedic on 2007-07-31
ok..I did what you suggested and this is what happened:

sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ iwconfig wlan0
wlan0     RT73 WLAN  ESSID:"1serving23jah4"  
          Mode:Managed  Frequency=2.462 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=85/100  Signal level:-54 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo ifconfig wlan0 down
Password:

sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ 
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo ifconfig wlan0 up
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo ifconfig wlan0 essid 1serving23jah4
essid: Unknown host
ifconfig: `--help' gives usage information.
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo ifconfig wlan0 mode managed
mode: Unknown host
ifconfig: `--help' gives usage information.
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo ifconfig wlan0 down



sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ 
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ 
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ 
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo ifconfig wlan0 up
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo ifconfig wlan0 essid 1serving23jah4
essid: Unknown host
ifconfig: `--help' gives usage information.
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo ifconfig wlan0 mode managed
mode: Unknown host
ifconfig: `--help' gives usage information.
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 8932
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:16:b6:97:1a:f7
Sending on   LPF/wlan0/00:16:b6:97:1a:f7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.105 -- renewal in 37502 seconds.
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:F5:D9:AE
                    ESSID:"1serving23jah4"
                    Mode:Managed
                    Channel:11
                    Encryption key:off
                    Bit Rates:0 kb/s

sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ iwconfig wlan0
wlan0     RT73 WLAN  ESSID:"1serving23jah4"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0C:41:F5:D9:AE   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=85/100  Signal level:-58 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ sudo /etc/init.d/dbus restart
 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting Hardware abstraction layer hald                              [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Starting network connection manager NetworkManager                    [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ] 
sean@desktop:/usr/src/rt73-cvs-2007073010/Module$ 

what next?

---

### Post by kevdog on 2007-07-31
Ok some modified instructions:

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid 1serving23jah4
sudo iwconfig wlan0 mode managed
sudo dhclient wlan0
```

---

### Post by 1feistymedic on 2007-07-31
I also did a reboot....nada......

---

### Post by kevdog on 2007-07-31
See above

---

### Post by 1feistymedic on 2007-07-31
sean@desktop:~$ sudo ifconfig wlan0 down
Password:
sean@desktop:~$ sudo ifconfig wlan0 up
sean@desktop:~$ sudo iwconfig wlan0 essid 1serving23jah4
sean@desktop:~$ sudo iwconfig wlan0 mode managed
sean@desktop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:16:b6:97:1a:f7
Sending on   LPF/wlan0/00:16:b6:97:1a:f7
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.105 -- renewal in 41408 seconds.
sean@desktop:~$

---

### Post by kevdog on 2007-07-31
Ok, 

> bound to 192.168.1.105 -- renewal in 41408 seconds.

You should be connected to the LAN...browse away...see if you can use firefox, etc.

This means that everything is working (for the manual configuration)

---

### Post by 1feistymedic on 2007-07-31
ok..I will have to go into Network manager and disable the wired connection and try to browse....but like I said earlier, there is no more option for wireless connections under Network manager...should I be using/installing another network manager?..

I disabled the wired connection in Network manager and also unplugged the ethernet cable just to make sure.... I am now working on the wireless....

Yeah!.....:guitar:

Now I am going to reboot and make sure it still works upon reboot.....

If it does, I need help to configure WPA since that is what I am using and also would like a gui so I can view the connection info instead of going into the terminal each time......

be right back:)

---

### Post by 1feistymedic on 2007-07-31
all right..rebooted and didn't work once again...I then did the following.....

sean@desktop:~$ sudo ifconfig wlan0 down
Password:
sean@desktop:~$ sudo ifconfig wlan0 up
sean@desktop:~$ sudo iwconfig wlan0 essid 1serving23jah4
sean@desktop:~$ sudo iwconfig wlan0 mode managed
sean@desktop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:16:b6:97:1a:f7
Sending on   LPF/wlan0/00:16:b6:97:1a:f7
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.105 -- renewal in 38506 seconds.
sean@desktop:~$ 


..and it works once again with the ethernet cable unplugged....

this is great and I really like the interaction with the terminal, but my kids may not like it....

what would be nice is 
1) a gui that I can use since the default Network manager does not work....
2) instructions to have the card work without having to enter the sudo config commands after every reboot
3) enable wpa encryption since that is what my system uses 

can you please advise?  I really appreciate this soo much....this has been a lot of fun......(next will be my radeon 7000 card and my ati tv wonder ve...:lolflag:

---

### Post by kevdog on 2007-07-31
Is this a laptop, or desktop?  If you are going to be just connecting to one router 99% of the time, I just say we put the configuration in the /etc/network/interfaces file and forget about it.  If its a laptop and you are going to be roaming and connecting to other networks, then probably the rutilt program is the answer.  

I'll let you choose what you want, and then we can build wpa into the solution.  Do you need a static IP for your computer (ie going to be running any servers ftp, ssh, web, ntp, etc)??  Again no right or wrong answer  -- we can modify the solution to fit your needs.

Also do me a favor and do the following:
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install wpasupplicant libgtk2.0-dev

---

### Post by 1feistymedic on 2007-07-31
ok....tried to use Network manager and it crashed the system...I had to do a hard boot and am now using the wired connection.....I will go into terminal and reactivate the USB card now and run the commands you indicated....

to answer the questions, this is a desktop but it will not be any where near the router, hence the usb wifi card

I will need a static ip address issued to this desktop

---

### Post by kevdog on 2007-07-31
And you definitely want a GUI or icon that sits in the system tray?

---

### Post by 1feistymedic on 2007-07-31
it&#347; not necessary to have a gui in the systray as long as it is an automatic connection....

I did do the other commands as follows:  

sean@desktop:~$ sudo ifconfig wlan0 down
Password:
sean@desktop:~$ sudo ifconfig wlan0 up
sean@desktop:~$ sudo iwconfig wlan0 essid 1serving23jah4
sean@desktop:~$ sudo iwconfig wlan0 mode managed
sean@desktop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:16:b6:97:1a:f7
Sending on   LPF/wlan0/00:16:b6:97:1a:f7
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.105 -- renewal in 36205 seconds.
sean@desktop:~$ sudo aptitude update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Fetched 3B in 1s (3B/s)  
Reading package lists... Done
sean@desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  tcpdump 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 303kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main tcpdump 3.9.5-2ubuntu1 [303kB]
Fetched 303kB in 1s (203kB/s)   
(Reading database ... 108498 files and directories currently installed.)
Preparing to replace tcpdump 3.9.5-2 (using .../tcpdump_3.9.5-2ubuntu1_i386.deb) ...
Unpacking replacement tcpdump ...
Setting up tcpdump (3.9.5-2ubuntu1) ...
sean@desktop:~$ sudo aptitude install wpasupplicant libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libatk1.0-dev libcairo2-dev libexpat1-dev libfontconfig1-dev 
  libfreetype6-dev libglib2.0-dev libice-dev libpango1.0-dev libpng12-dev 
  libsm-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev 
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev 
  libxrender-dev x11proto-core-dev x11proto-fixes-dev x11proto-input-dev 
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev 
  x11proto-xinerama-dev xtrans-dev zlib1g-dev 
The following NEW packages will be installed:
  libatk1.0-dev libcairo2-dev libexpat1-dev libfontconfig1-dev 
  libfreetype6-dev libglib2.0-dev libgtk2.0-dev libice-dev libpango1.0-dev 
  libpng12-dev libsm-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev 
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev 
  libxrandr-dev libxrender-dev x11proto-core-dev x11proto-fixes-dev 
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev 
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev 
0 packages upgraded, 32 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.2MB of archives. After unpacking 45.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-core-dev 7.0.10-1 [86.3kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libfreetype6-dev 2.2.1-5ubuntu1.1 [640kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libice-dev 2:1.0.3-1build1 [55.9kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libsm-dev 2:1.0.2-1build1 [25.6kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxau-dev 1:1.0.3-1 [15.5kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxdmcp-dev 1:1.0.2-1 [19.8kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-input-dev 1.4.1-1 [15.4kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-kb-dev 1.0.3-2ubuntu1 [27.0kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main xtrans-dev 1.0.3-1 [69.2kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libx11-dev 2:1.1.1-1ubuntu3 [8685kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libpng12-dev 1.2.15~beta5-1ubuntu1 [172kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-render-dev 2:0.9.2-4ubuntu1 [6960B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxrender-dev 1:0.9.1-3 [24.4kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-xext-dev 7.0.2-5ubuntu1 [42.2kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-fixes-dev 1:4.0-0.1ubuntu2 [5662B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxfixes-dev 1:4.0.3-1 [12.1kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxcursor-dev 1:1.1.8-1 [30.6kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxext-dev 2:1.0.3-1build1 [81.5kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libexpat1-dev 1.95.8-3.4build1 [129kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main zlib1g-dev 1:1.2.3-13ubuntu4 [407kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libfontconfig1-dev 2.4.2-1ubuntu1 [344kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxft-dev 2.1.12-1 [60.7kB]    
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxi-dev 2:1.1.0-1build1 [67.7kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-xinerama-dev 1.1.2-4ubuntu1 [5424B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxinerama-dev 2:1.0.1-4build1 [4196B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-randr-dev 1.2.1-1 [28.6kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxrandr-dev 2:1.2.0-3ubuntu1 [27.5kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libglib2.0-dev 2.12.11-0ubuntu1 [536kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libatk1.0-dev 1.18.0-0ubuntu1 [112kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libcairo2-dev 1.4.2-0ubuntu1 [507kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libpango1.0-dev 1.16.2-0ubuntu1 [355kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libgtk2.0-dev 2.10.11-0ubuntu3 [2590kB]
Fetched 15.2MB in 41s (364kB/s)                                                 
Extracting templates from packages: 100%
Selecting previously deselected package x11proto-core-dev.
(Reading database ... 108498 files and directories currently installed.)
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.10-1_all.deb) ...
Selecting previously deselected package libice-dev.
Unpacking libice-dev (from .../libice-dev_2%3a1.0.3-1build1_i386.deb) ...
Selecting previously deselected package libsm-dev.
Unpacking libsm-dev (from .../libsm-dev_2%3a1.0.2-1build1_i386.deb) ...
Selecting previously deselected package libxau-dev.
Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.3-1_i386.deb) ...
Selecting previously deselected package libxdmcp-dev.
Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.0.2-1_i386.deb) ...
Selecting previously deselected package x11proto-input-dev.
Unpacking x11proto-input-dev (from .../x11proto-input-dev_1.4.1-1_all.deb) ...
Selecting previously deselected package x11proto-kb-dev.
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.3-2ubuntu1_all.deb) ...
Selecting previously deselected package xtrans-dev.
Unpacking xtrans-dev (from .../xtrans-dev_1.0.3-1_all.deb) ...
Selecting previously deselected package libx11-dev.
Unpacking libx11-dev (from .../libx11-dev_2%3a1.1.1-1ubuntu3_i386.deb) ...
Selecting previously deselected package x11proto-render-dev.
Unpacking x11proto-render-dev (from .../x11proto-render-dev_2%3a0.9.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxrender-dev.
Unpacking libxrender-dev (from .../libxrender-dev_1%3a0.9.1-3_i386.deb) ...
Selecting previously deselected package x11proto-xext-dev.
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.0.2-5ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-fixes-dev.
Unpacking x11proto-fixes-dev (from .../x11proto-fixes-dev_1%3a4.0-0.1ubuntu2_all.deb) ...
Selecting previously deselected package libxfixes-dev.
Unpacking libxfixes-dev (from .../libxfixes-dev_1%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package libxcursor-dev.
Unpacking libxcursor-dev (from .../libxcursor-dev_1%3a1.1.8-1_i386.deb) ...
Selecting previously deselected package libxext-dev.
Unpacking libxext-dev (from .../libxext-dev_2%3a1.0.3-1build1_i386.deb) ...
Selecting previously deselected package libexpat1-dev.
Unpacking libexpat1-dev (from .../libexpat1-dev_1.95.8-3.4build1_i386.deb) ...
Selecting previously deselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3-13ubuntu4_i386.deb) ...
Selecting previously deselected package libfreetype6-dev.
Unpacking libfreetype6-dev (from .../libfreetype6-dev_2.2.1-5ubuntu1.1_i386.deb) ...
Selecting previously deselected package libfontconfig1-dev.
Unpacking libfontconfig1-dev (from .../libfontconfig1-dev_2.4.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package libxft-dev.
Unpacking libxft-dev (from .../libxft-dev_2.1.12-1_i386.deb) ...
Selecting previously deselected package libxi-dev.
Unpacking libxi-dev (from .../libxi-dev_2%3a1.1.0-1build1_i386.deb) ...
Selecting previously deselected package x11proto-xinerama-dev.
Unpacking x11proto-xinerama-dev (from .../x11proto-xinerama-dev_1.1.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxinerama-dev.
Unpacking libxinerama-dev (from .../libxinerama-dev_2%3a1.0.1-4build1_i386.deb) ...
Selecting previously deselected package x11proto-randr-dev.
Unpacking x11proto-randr-dev (from .../x11proto-randr-dev_1.2.1-1_all.deb) ...
Selecting previously deselected package libxrandr-dev.
Unpacking libxrandr-dev (from .../libxrandr-dev_2%3a1.2.0-3ubuntu1_i386.deb) ...
Selecting previously deselected package libglib2.0-dev.
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.12.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package libatk1.0-dev.
Unpacking libatk1.0-dev (from .../libatk1.0-dev_1.18.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libpng12-dev.
Unpacking libpng12-dev (from .../libpng12-dev_1.2.15~beta5-1ubuntu1_i386.deb) ...
Selecting previously deselected package libcairo2-dev.
Unpacking libcairo2-dev (from .../libcairo2-dev_1.4.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libpango1.0-dev.
Unpacking libpango1.0-dev (from .../libpango1.0-dev_1.16.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgtk2.0-dev.
Unpacking libgtk2.0-dev (from .../libgtk2.0-dev_2.10.11-0ubuntu3_i386.deb) ...
Setting up x11proto-core-dev (7.0.10-1) ...
Setting up libice-dev (1.0.3-1build1) ...
Setting up libsm-dev (1.0.2-1build1) ...
Setting up libxau-dev (1.0.3-1) ...
Setting up libxdmcp-dev (1.0.2-1) ...
Setting up x11proto-input-dev (1.4.1-1) ...
Setting up x11proto-kb-dev (1.0.3-2ubuntu1) ...
Setting up xtrans-dev (1.0.3-1) ...
Setting up libx11-dev (1.1.1-1ubuntu3) ...
Setting up x11proto-render-dev (0.9.2-4ubuntu1) ...
Setting up libxrender-dev (0.9.1-3) ...
Setting up x11proto-xext-dev (7.0.2-5ubuntu1) ...
Setting up x11proto-fixes-dev (4.0-0.1ubuntu2) ...
Setting up libxfixes-dev (4.0.3-1) ...
Setting up libxcursor-dev (1.1.8-1) ...
Setting up libxext-dev (1.0.3-1build1) ...
Setting up libexpat1-dev (1.95.8-3.4build1) ...

Setting up zlib1g-dev (1.2.3-13ubuntu4) ...
Setting up libfreetype6-dev (2.2.1-5ubuntu1.1) ...

Setting up libfontconfig1-dev (2.4.2-1ubuntu1) ...
Setting up libxft-dev (2.1.12-1) ...
Setting up libxi-dev (1.1.0-1build1) ...
Setting up x11proto-xinerama-dev (1.1.2-4ubuntu1) ...
Setting up libxinerama-dev (1.0.1-4build1) ...
Setting up x11proto-randr-dev (1.2.1-1) ...
Setting up libxrandr-dev (1.2.0-3ubuntu1) ...
Setting up libglib2.0-dev (2.12.11-0ubuntu1) ...
Setting up libatk1.0-dev (1.18.0-0ubuntu1) ...
Setting up libpng12-dev (1.2.15~beta5-1ubuntu1) ...
Setting up libcairo2-dev (1.4.2-0ubuntu1) ...
Setting up libpango1.0-dev (1.16.2-0ubuntu1) ...
Setting up libgtk2.0-dev (2.10.11-0ubuntu3) ...
sean@desktop:~$

---

### Post by 1feistymedic on 2007-07-31
When this is done and working correctly, I am going to review it and resubmit it as a sticky so that everyone with this card, which is a common card, can have a "noob-proof" walk through that explains each and every step..step by step....thanks a million....still standing by

---

### Post by kevdog on 2007-07-31
OK try this, we will work on rutilt last
We will setup the router last using WPA (not WPA2) with TKIP
```

gksu gedit /etc/network/interfaces
```
```

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid YOUR_ESSID
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set WPAPSK=***** <---- see below
pre-up iwpriv wlan0 set EncrypType=TKIP
```

For static IP setup replace ***iface wlan0 inet dhcp*** with:

```
iface wlan0 inet static
address 192.168.x.x
netmask 255.255.255.0
gateway 192.168.1.1 
dns-nameservers x.x.x x.x.x.x
```

***Here is how to generate you key for the WPAPSK parameter
To generate your password, do this:

```
wpa_passphrase <SSID of your router> <your password>
```

Discard the < and > here.
The command will generate the password for your that you can copy and paste.
The output would would look like this as an example:

```
network={
        ssid="MyHomeWireless"
        #psk="SuperSecretPassphrase"
        psk=e42ac2538ef03f906d37332a0df4446150e04cdcdd392e309486075065a70a1f
}
```


Ok you might lose connection after you change your router settings, but now setup with WPA(1) not WPA2 and with TKIP algorithm

Save the file.

Reboot or kill the sudo dhclient wlan0 process with Cntr-C, then try:
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

Good Luck!

---

### Post by 1feistymedic on 2007-07-31
ok.....got this message:

sean@desktop:~$ gksu gedit /etc/network/interfaces
(gedit:6719): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

 and a "ïnterfaces (/etc/network -gedit) pop up window....that says this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


...at what point and where, terminal or interfaces pop-up window, do I do this?:


Code:

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid YOUR_ESSID
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set WPAPSK=***** <---- see below
pre-up iwpriv wlan0 set EncrypType=TKIP

---

### Post by kevdog on 2007-07-31
Im not certain about the error warning you got there -- seems like you dont have a root account, but any way, add those lines in the gedit popup window.

Oh one last thing -- back up your interfaces file so you have an original copy

sudo cp /etc/network/interfaces /etc/network/interfaces.orig

Then
gksu gedit /etc/network/interfaces

Add the following under wlan0, if no wlan0 section make one.  

Please post your interfaces file, along with 
lshw -C network
when done.

---

### Post by 1feistymedic on 2007-07-31
> **kevdog said:**
> OK try this, we will work on rutilt last
We will setup the router last using WPA (not WPA2) with TKIP
```

gksu gedit /etc/network/interfaces
```
```

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid YOUR_ESSID
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set WPAPSK=***** <---- see below
pre-up iwpriv wlan0 set EncrypType=TKIP
```

For static IP setup replace ***iface wlan0 inet dhcp*** with:

```
iface wlan0 inet static
address 192.168.x.x
netmask 255.255.255.0
gateway 192.168.1.1 
dns-nameservers x.x.x x.x.x.x
```

***Here is how to generate you key for the WPAPSK parameter
To generate your password, do this:

```
wpa_passphrase <SSID of your router> <your password>
```

Discard the < and > here.
The command will generate the password for your that you can copy and paste.
The output would would look like this as an example:

```
network={
        ssid="MyHomeWireless"
        #psk="SuperSecretPassphrase"
        psk=e42ac2538ef03f906d37332a0df4446150e04cdcdd392e309486075065a70a1f
}
```


Ok you might lose connection after you change your router settings, but now setup with WPA(1) not WPA2 and with TKIP algorithm

Save the file.

Reboot or kill the sudo dhclient wlan0 process with Cntr-C, then try:
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

Good Luck!

one more thing before I do the above....are all those things to be added to the -gedit window and if so do I have to put the "#" sign in front of each entry as before?  OR, are some of those commands to be put in the terminal instead....Thanks

---

### Post by kevdog on 2007-07-31
Hold on

Some of the above post were specifically settings to enter into the interfaces file (with an optional static IP part). Others were commands to type into the terminal -- ie the wpa password generation process to get the hex key, which you then cut and paste back into the interfaces file.

The ifconfig up/down were command line commands.

Again if you post your interfaces file it would be obvious if everything was ok.

---

### Post by 1feistymedic on 2007-07-31
> **kevdog said:**
> Hold on

Some of the above post were specifically settings to enter into the interfaces file (with an optional static IP part). Others were commands to type into the terminal -- ie the wpa password generation process to get the hex key, which you then cut and paste back into the interfaces file.

The ifconfig up/down were command line commands.

Again if you post your interfaces file it would be obvious if everything was ok.

ok..so let me get this straight....I now have an open terminal that looks like this with no prompt to enter in commands:

sean@desktop:~$ gksu gedit /etc/network/interfaces
(gedit:6719): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

..and I have a interfaces windows that looks like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


..am I to understand that I need to 

1)copy and paste this info as is into the interfaces like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid YOUR_ESSID
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set WPAPSK=***** <---- see below
pre-up iwpriv wlan0 set EncrypType=TKIP

2) start a new terminal, since I have no command prompt and paste this command in and hit the enter key:

wpa_passphrase <SSID of your router> <your password>

3)which wil generate a file that looks like this:

network={
        ssid="MyHomeWireless"
        #psk="SuperSecretPassphrase"
        psk=e42ac2538ef03f906d37332a0df4446150e04cdcdd392e309486075065a70a1f
}

4) and then copy and paste this at the end of the interface file like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid YOUR_ESSID
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set WPAPSK=***** <---- see below
pre-up iwpriv wlan0 set EncrypType=TKIP

network={
        ssid="MyHomeWireless"
        #psk="SuperSecretPassphrase"
        psk=e42ac2538ef03f906d37332a0df4446150e04cdcdd392e309486075065a70a1f
}

5) and then do this in terminal:

Save the file.

Reboot or kill the sudo dhclient wlan0 process with Cntr-C, then try:
Code:

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up

6) and then do this in terminal:

sudo cp /etc/network/interfaces /etc/network/interfaces.orig

Then
gksu gedit /etc/network/interfaces

7)

---

### Post by kevdog on 2007-07-31
Almost right

#1.  Before making any changes to the interfaces file -- back it up!!!

#2.  Cut and paste almost all the configuration statements in the interfaces file except:
> pre-up iwpriv wlan0 set WPAPSK=***** <---- see below

The **** portion is generated at the command prompt by:

```
wpa_passphrase <SSID of your router> <your password>  <------Substitute appropriate values without the <>
```

Get the output (for example the following):
> network={
ssid="MyHomeWireless"
#psk="SuperSecretPassphrase"
psk=e42ac2538ef03f906d37332a0df4446150e04cdcdd392e 309486075065a70a1f
}

Cut and paste the last line of the output: into the interfaces file so you have a line similar to this:
> pre-up iwpriv wlan0 set WPAPSK=e42ac2538ef03f906d37332a0df4446150e04cdcdd392e 309486075065a70a1f

#3. Save the file

#4. Make changes to router

#5. Cycle the interface to see if it works
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up

#6 If it doesnt work, then reboot if necessary.

---

### Post by 1feistymedic on 2007-07-31
> **kevdog said:**
> Im not certain about the error warning you got there -- seems like you dont have a root account, but any way, add those lines in the gedit popup window.

Oh one last thing -- back up your interfaces file so you have an original copy

sudo cp /etc/network/interfaces /etc/network/interfaces.orig

Then
gksu gedit /etc/network/interfaces

Add the following under wlan0, if no wlan0 section make one.  

Please post your interfaces file, along with 
lshw -C network
when done.

ok...here we go....

1) how do I activate the "root account"
2) after I followed the directions I had to reboot because my router kicked me off
3) I rebooted and had to do this again:

sudo ifconfig wlan0 up
 sudo iwconfig wlan0 essid 1serving23jah4
 sudo iwconfig wlan0 mode managed
 sudo dhclient wlan0

4) then I got this message in terminal:

sean@desktop:~$ sudo ifconfig wlan0 down
Password:

sean@desktop:~$ 
sean@desktop:~$ sudo ifconfig wlan0 up
sean@desktop:~$ sudo iwconfig wlan0 essid 1serving23jah4
sean@desktop:~$ sudo iwconfig wlan0 mode managed
sean@desktop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:16:b6:97:1a:f7
Sending on   LPF/wlan0/00:16:b6:97:1a:f7
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
Trying recorded lease 192.168.1.105
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 2.602/2.602/2.602/0.000 ms
bound: renewal in 29546 seconds.
sean@desktop:~$ 

5) I did this in terminal:

gksu gedit /etc/network/interfaces

6) and here is the info:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid YOUR_ESSID
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set WPAPSK=psk=c91fd5b50be99fc3093baf4c7db85ee1125b14a1f50400957a1f8a3a1045e605
pre-up iwpriv wlan0 set EncrypType=TKIP

7) i then entered this in terminal after closing the interface:

lshw -C network

8) and got this:

sean@desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 9
       bus info: pci@01:09.0
       logical name: eth0
       version: 10
       serial: 00:05:5d:44:6b:5c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.102 latency=66 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:1400-14ff iomemory:40200000-402000ff irq:5
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:b6:97:1a:f7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.105 multicast=yes wireless=RT73 WLAN
sean@desktop:~$

.....if you are not asleep yet tell me more....if not we can resume later....

---

### Post by 1feistymedic on 2007-07-31
ooops....I think I found the problem...forgot my ssid in the interface...here is the corrected info:

1)sean@desktop:~$ 
sean@desktop:~$ gksu gedit /etc/network/interfaces

2)# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid 1serving23jah4
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set WPAPSK=psk=c91fd5b50be99fc3093baf4c7db85ee1125b14a1f50400957a1f8a3a1045e605
pre-up iwpriv wlan0 set EncrypType=TKIP

3)sean@desktop:~$ 
sean@desktop:~$ gksu gedit /etc/network/interfaces
sean@desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 9
       bus info: pci@01:09.0
       logical name: eth0
       version: 10
       serial: 00:05:5d:44:6b:5c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.102 latency=66 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:1400-14ff iomemory:40200000-402000ff irq:5
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:b6:97:1a:f7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.105 multicast=yes wireless=RT73 WLAN
sean@desktop:~$

---

### Post by stchman on 2007-07-31
> **1feistymedic said:**
> I have a Linksys WUSB54GC wifi device that supports WPA encryption.  For some reason that option is not available in the network settings.  The only options that are available are:

WEP key (hexadecimal)
WEP key (ascii)

How do I enable WPA encryption for this card?  And please make it very simple and step by step as I am the nu-est of nubians.  Thanks.  Everything else on the network is using WPA.

Use network manager.  WPA and WPA2 is there.  Broadcast your SSID and click on network manager.  Your broadcast will be there.  Select your WAP and network manager will ask you for your WPA passphrase.  Very easy.  Leave your wireless connection on roaming.

---

### Post by 1feistymedic on 2007-07-31
> **stchman said:**
> Use network manager.  WPA and WPA2 is there.  Broadcast your SSID and click on network manager.  Your broadcast will be there.  Select your WAP and network manager will ask you for your WPA passphrase.  Very easy.  Leave your wireless connection on roaming.

no..wpa is not there..it is still the same as it was.....network manager doesn work with serialmonkey driver...need Rutil....but thanks anyway....

---

### Post by 1feistymedic on 2007-07-31
still not working.....going to try and disable wpa again.....

---

### Post by 1feistymedic on 2007-07-31
disabled wpa on the router and now I am bound again and surfing wirelessly....it&#347; gotta be a problem with what I did to the WPA settings in terminal and interface....

sean@desktop:~$ sudo ifconfig wlan0 down
Password:

sean@desktop:~$ 
sean@desktop:~$ sudo ifconfig wlan0 up
sean@desktop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:16:b6:97:1a:f7
Sending on   LPF/wlan0/00:16:b6:97:1a:f7
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.105 -- renewal in 33304 seconds.
sean@desktop:~$

---

### Post by noob12 on 2007-07-31
Medic: you have an extra **psk=** in the WPAPSK setting in the /etc/network/interfaces file.  That doesn't belong.

It should read
```

pre-up iwpriv wlan0 set WPAPSK=c91fd5b50be99fc3093baf4c7db85ee1125b14a1f50400957a1f8a3a1045e605

```

Make sure you have the key right from your **wpa_passphrase** output.  It shouldn't have spaces in it.  Don't include the **psk=** part from the output of **wpa_passphrase**.  Just the rest of the line after the  equals sign.

---

### Post by kevdog on 2007-07-31
Good advice, you are almost there!!  Then onto rutilt, and then DONE!

---

### Post by 1feistymedic on 2007-07-31
ok..still not working..here is what I get

1) sean@desktop:~$ gksu gedit /etc/network/interfaces


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto wlan0
iface wlan0 inet static
address 192.168.1.117
netmask 255.255.255.0
gateway 192.168.1.1 
dns-nameservers 68.87.77.130
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid 1serving23jah4
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set WPAPSK=c91fd5b50be99fc3093baf4c7db85ee1125b14a1f50400957a1f8a3a1045e605
pre-up iwpriv wlan0 set EncrypType=TKIP

2)sean@desktop:~$ sudo ifconfig wlan0 up
sean@desktop:~$ sudo iwconfig wlan0 essid 1serving23jah4
sean@desktop:~$ sudo iwconfig wlan0 mode managed
sean@desktop:~$ sudo dhclient wlan0

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:16:b6:97:1a:f7
Sending on   LPF/wlan0/00:16:b6:97:1a:f7
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.105 -- renewal in 42888 seconds.
sean@desktop

3)sean@desktop:~$ lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 9
       bus info: pci@01:09.0
       logical name: eth0
       version: 10
       serial: 00:05:5d:44:6b:5c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.106 latency=66 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:1400-14ff iomemory:40200000-402000ff irq:5
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:b6:97:1a:f7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.105 multicast=yes wireless=RT73 WLAN
sean@desktop:~$ 

4) now I am surfing with the connection

5) troubled though that I specified a network address in the interface of 192.168.1.117 along with the appropriate dns id but it shows I am bound to 192.168.1.105.  Isn this a problem?

6) also, I have to do the following every time after reboot in order to get a connection


sean@desktop:~$ sudo ifconfig wlan0 up
sean@desktop:~$ sudo iwconfig wlan0 essid 1serving23jah4
sean@desktop:~$ sudo iwconfig wlan0 mode managed
sean@desktop:~$ sudo dhclient wlan0

Is there a way around this?

7) once these issues are resolved, then I guess it is on to rutil.......:guitar:

---

### Post by 1feistymedic on 2007-07-31
oh..almost forgot...I need to get this thing working ***without*** having the ssid broadcasted......thanks....

this will make the best tutorial out there......thanks so much...so many others will benefit....

---

### Post by 1feistymedic on 2007-07-31
yep..I think the ip address thing is going to cause a problem because I just lost the connection....back to wired access.....:(

---

### Post by 1feistymedic on 2007-07-31
This is the most recent attempt.......



sean@desktop:~$ sudo ifconfig wlan0 down
sean@desktop:~$ sudo ifconfig wlan0 up
sean@desktop:~$ sudo iwconfig wlan0 essid 1serving23jah4
sean@desktop:~$ sudo iwconfig wlan0 mode managed
sean@desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5500
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:16:b6:97:1a:f7
Sending on   LPF/wlan0/00:16:b6:97:1a:f7
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
Trying recorded lease 192.168.1.105
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.188/1.188/1.188/0.000 ms
bound: renewal in 40481 seconds.
sean@desktop:~$ 

I am almost ready to throw this thing out the window:mad:

---

### Post by noob12 on 2007-07-31
Right after #89, you were close to having things running and working automatically at boot.

After removing those, here's what your entire section for wlan0 in /etc/network/interfaces should look like
```

auto wlan0
iface wlan0 inet [COLOR="Red"]dhcp[/COLOR]
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid 1serving23jah4
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set WPAPSK=c91fd5b50be99fc3093baf4c7db85ee1125b14a1f50400957a1f8a3a1045e605
pre-up iwpriv wlan0 set EncrypType=TKIP

```

This should work on boot with WPA, provided you got the key right.

---

### Post by 1feistymedic on 2007-07-31
Noob...........you are a genius.....

actually, I just got it working...I forgot the basic rule of wireless routing...always unplug everything, let it sit for a while, then plug everything back up....it now works on reboot......and I did a lshw -C network and it is bound to the correct ip address.....

before we go onto rutil, I need to know how I add the second dns server to the interface....do i just copy the dns line and paste it deirectly below and then update the server addres? like this?:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto wlan0
iface wlan0 inet static
address 192.168.1.117
netmask 255.255.255.0
gateway 192.168.1.1 
dns-nameservers 68.87.77.130
[COLOR="Blue"]dns-nameservers 68.87.72.130[/COLOR]
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid 1serving23jah4
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set WPAPSK=c91fd5b50be99fc3093baf4c7db85ee1125b14a1f50400957a1f8a3a1045e605
pre-up iwpriv wlan0 set EncrypType=TKIP

just curious.....and for fyi here is the lshw -C network info:

sean@desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 9
       bus info: pci@01:09.0
       logical name: eth0
       version: 10
       serial: 00:05:5d:44:6b:5c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=66 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:1400-14ff iomemory:40200000-402000ff irq:5
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:b6:97:1a:f7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.117 multicast=yes wireless=RT73 WLAN
sean@desktop:~$

---

### Post by kevdog on 2007-07-31
Onto Rutilt
```

cd ~
mkdir rutilt
cd rutilt
wget http://cbbk.free.fr/bonrom/files/RutilTv0.15.tar.gz -O RutilTv0.15.tar.gz
tar -zxvf RutilTv0.15.tar.gz
cd RutilTv0.15
./configure.sh --launcher=external
make
sudo make install
```

To try out program, then just type at command line:
rutilt

If you like this we can just add this to the Ubuntu sessions so it will start at startup!

---

### Post by kevdog on 2007-07-31
If you need to add more name servers I just do it like this:

```
dns-nameservers 68.87.85.98 68.87.69.146 192.168.1.1
```

---

### Post by 1feistymedic on 2007-07-31
still compiling.....

---

### Post by 1feistymedic on 2007-07-31
in the meantime, is there a book I can buy or a free resource that will teach me all these command codes?  THanks....

---

### Post by 1feistymedic on 2007-07-31
ok..I like it....Rutilt is what I was looking for.....how do we add it to the start-up file?

---

### Post by kevdog on 2007-07-31
Ok, the following command will help you look up files and see where they are located on your computer.  It can be used for any file:

It firsts updates the database (this may take as long as 5 minutes), then you can run the locate command to find the file

```
sudo updatedb 
locate rutilt
```

Im only including this to teach you this method.  It should report among other things rutilt is located in /usr/local/bin

So to add this to a startup group on the menu at the top of the screen
System->Preferences->Sessions

Select New
Type in a name such as Rutilt
Then you have to type or browse to find the path of the executable (which we just find above)
Within the rutilt program itself (under Options) you can select to Start hidden in tray if you dont want the big window popping up at startup.

Maybe you could provide a screen shot of the main rutilt interface.  Since I dont have a ra card, the WPA features within rutilt wont work for me, but supposedly you can configure your wpa parameter somehow.  If you could report back, you could actually teach me

---

### Post by 1feistymedic on 2007-07-31
man.....I am really feeling too noobish....I guess I am new to posting in forums as well....I took several screenshots....how do I include them in a post?

---

### Post by 1feistymedic on 2007-07-31
never mind...I think I got it

---

### Post by 1feistymedic on 2007-07-31
I am definitely new to using the "snapshot" feature.....but that&#347; another thread in the forum:lolflag:

---

### Post by kevdog on 2007-07-31
Anything you can get a snapshot with that shows anything about WPA in the rutilt GUI??

---

### Post by 1feistymedic on 2007-07-31
Ok...how does this look?

---

### Post by noob12 on 2007-07-31
Sweet!

That's the scan.  Is there a tab for selecting the authentication mode and entering the key through the GUI?

---

### Post by 1feistymedic on 2007-07-31
Well, to all who helped me I extend a hearty "thank you"!  I will go over this thread and redo the instructions so that anyone with this wireless card can get it to work.

I just have a question, how do I get it to become a sticky?

I also have another question.  How do I get help with the following and what section of the forum do I post them in?

1) cant get totem, realplayer, smplayer to play dvds

2)how to get Ubuntu to recognize my radeon 7000 pci card

3) how to get ubuntu to recognize my ati wonder ve card

4) how to learn the different command prompts so I can help other people and maybe even contribute something useful one day to the linux source code.

Thanks all and take care...look for the recap of this thread coming soon to a forum near you!

---

### Post by noob12 on 2007-07-31
> 
I just have a question, how do I get it to become a sticky?

I also have another question. How do I get help with the following and what section of the forum do I post them in?

1) cant get totem, realplayer, smplayer to play dvds

2)how to get Ubuntu to recognize my radeon 7000 pci card

3) how to get ubuntu to recognize my ati wonder ve card

4) how to learn the different command prompts so I can help other people and maybe even contribute something useful one day to the linux source code.


For 1-3 the Multimedia and Video forums should be able to guide you.

For 4, Start by learning to use the **man** manual page system.  Type **man iwlist** and **man lshw** to see the man pages of some of the commands that you used in this thread.

I'd always assumed stickies were the realm of the gods, but I'm a noob.

---

### Post by kevdog on 2007-07-31
Just wondering if you could configure the WPA settings through rutilt.  Ive heard rumors that this could possibly be done, but can not confirm.  I was hoping on a screen shot that showed a WPA configuration section, but alas, none was posted.

As far as a HOW-TO.  There is nothing to it.  Just write it up, entitle it a HOW-TO-xxxx.  Its simply a post.   You may however want to run it by someone first.  There are a lot of worthless howto's.

As far as dvd's, (although I think this is controversialy), automatix2 with the restricted codecs is the answer.

Vid card problems -- no clue, cant help you there.

---

### Post by 1feistymedic on 2007-07-31
Ok..here is the tutorial...let me know what you think....When I go back to the basement, I will send you those screen shots....

---

### Post by kevdog on 2007-07-31
Id put the rutilt setup in it to -- maybe as an optional section

Where are you planning on putting this how-to (in this forum)???  If you are, hate to make you do it, but could you cut and paste it in the form of a forum post (with code and quote sections).  It will definitely make it look a lot more polished.

---

### Post by 1feistymedic on 2007-07-31
> **kevdog said:**
> Id put the rutilt setup in it to -- maybe as an optional section

Where are you planning on putting this how-to (in this forum)???  If you are, hate to make you do it, but could you cut and paste it in the form of a forum post (with code and quote sections).  It will definitely make it look a lot more polished.

Great idea...how do you cut and paste in the form of a forum post?  I have never done that...

Here are the screenshots as well

---

### Post by 1feistymedic on 2007-07-31
and one more

---

### Post by kevdog on 2007-07-31
You will figure out the cut and paste part (there is no trick, Its going to be a lot of work!! -- Almost like retyping it)

Try setting up a new profile in rutilt (3rd tab) -- Im curious to see what that does and what options it gives to you -- for example wpa options or static IP options.  If it does, we could try experimenting with changing the values in your /etc/network/interfaces file.

---

### Post by pedro.solorzano on 2007-12-13
Hi Everyone:

I have the same problem. I connect with WPA without trouble in many places. But there is one single wireless network, say SSID "toy" that does not show the WPA option. Other people with windows os can connect to "toy" using WPA but I cant because it only shows WEP ascii and hex options for security and again I have seen the WPA option for other networks in this laptop. WPA suplicant is installed, and the signal is ok.

What can be happening? Thanks in advance for any answer.

---

