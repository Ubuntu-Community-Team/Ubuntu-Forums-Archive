---
title: "DLink DWL G122."
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by ninjasauce on 2006-11-05
Stated above is the wireless usb card I have. I just simply don't know how to install it onto Ubuntu. I have the original Windows Disk for it. 

I'm a complete Linux/Ubuntu newbie never used it in my life. Can someone give me help on how to install the usb drive and get the internet running on that machine? 

I've been recommended ndiswrapper but again, I don't know how to use it. I don't know how to even install ndiswrapper never mind how to use it to install the drivers.

---

### Post by FrodoB on 2006-11-05
Can you report back the output of lsusb. Mine looks like this:

user@ubuntu:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 050d:705c Belkin Components 

See if your ID is included in the Linux Wireless List at:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

This will let you know if there are native drivers for your device.  If not you will need to go the ndiswrapper route.

---

### Post by ninjasauce on 2006-11-22
Bus 005 Device 003: ID 2001:3c00 D-Link Corp. [hex]

---

### Post by ninjasauce on 2006-11-22
This is urgent. I need links for the drivers, and also information on how to install those drivers.

I am a complete Ubuntu newbie.

---

### Post by FrodoB on 2006-11-22
What do you get if you run:

iwconfig

Also can you find the section of dmesg that shows the device being loaded?

---

### Post by ninjasauce on 2006-11-22
root@ubuntu:-# iwconfig
lo  no wireless extensios
eth0  no wireless extensions
sit0  no wireless extensions

---

### Post by FrodoB on 2006-11-22
It appears that you probably need the rt2570 driver from:

[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

at least that is what the serialmonkey forums would seem to indicate.

---

### Post by ninjasauce on 2006-11-22
can you give me a step-by-step guide on how to install the drivers? it really badly confuses me.

---

### Post by FrodoB on 2006-11-22
Just a few minutes, I am looking into this.

---

### Post by FrodoB on 2006-11-22
This is a DWL-G122 revision B1 ?

---

### Post by ninjasauce on 2006-11-22
thanks :) yeah it is B1

---

### Post by FrodoB on 2006-11-22
OK, a highly suspect set of instructions that I was starting for a Zonet ZEW2500P that use the same driver. Remember that If I refer to that device and its USB ID to replace it with yours.  Let me know about any problems you find.

= Ralink rt2570 Driver Installation =

This document was prepared based upon Ubuntu 6.06 (Dapper Drake) distribution, but other versions should be usable as well. 

In addition this procedure has been tested successfully on other Linux distributions.

For this example we assume that we are building the device in the user's home directory.

Note: I have only tested this using 128bit (104bit) WEP.

== Step 1 - Disable Competing Driver ==  

# Don't know if this is needed yet.

You need to blacklist the existing rt2570 modules which is not working:
```

user@ubuntu:~$ sudo gedit /etc/modprobe.d/blacklist

```add the following two lines to the end of the file:

# Added when rt2570 module was installed
blacklist rt2570usb

Save the file. The blacklisted module will not be loaded from now on.



== Step 2 - Prepare the Linux build environment ==

You will need to install the essential build files to compile the driver:
```

user@ubuntu:~$ sudo apt-get update 
user@ubuntu:~$ sudo apt-get install build-essential

```Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)
```

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` 
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

```
Install the todos and fromdos utilities for converting files from DOS/Windows text to UNIX text (required later in the process):
```

user@ubuntu:~$ sudo apt-get install tofrodos

```

== Step 3 - Download the latest version of the rt2570 driver ==

The driver can be found at:
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)


The latest at the time I am writing this is:

Latest BETA rt2570 driver: v1.1.0-b2

Download it to your desktop and then move it to your home directory by opening the:

Places --> Home Folder

directory using the middle menu at the top of the page.

== Step 4 - Extract and install the driver using make ==

Using tar extract the archived driver and change directories into the build area.
```

user@ubuntu:~$ tar xvzf rt2570-1.1.0-b2.tar.gz 
user@ubuntu:~$ cd rt2570-1.1.0-b2/Module
user@ubuntu:~/rt2570-1.1.0-b2/Module$ 

```
Make the driver with the make command:
```

user@ubuntu:~/rt2570-1.1.0-b2/Module$ make

```This will take several minutes.


Using sudo make install we install the complete driver into the "extra" directory of your kernel modules:
```

user@ubuntu:~/rt2570-1.1.0-b2/Module$ sudo make install

```
Verify that the driver was installed correctly using the list short command:
```

user@ubuntu:~/rt2570-1.1.0-b2/Module$ ls /lib/modules/`uname -r`/extra

```
You should see the file rt2570.ko



== Step 5 - Install the device and configure the network settings ==

Insert your rt2570 device, into a usb connector on your machine. 

You should now be able to  see that the device is installed by opening a terminal window and running lsusb:
```

user@ubuntu:~$ lsusb

```
Your output should contain a line that has your device's USB ID and description, similar to this:
```

Bus 00X Device 00X: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi

```Issuing an iwconfig command should reveal that your device is waiting to be configured, similar to this one:
```

rausb0    RT2500USB WLAN  ESSID:""
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated
          RTS thr:off   Fragment thr:off
          Link Quality=89/100  Signal level:-47 dBm  Noise level:-202 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Using the Ubuntu Networking applet at System --> Administration --> Networking menu setup the correct parameters for your device.

Reboot the system before proceding to the next step.


== Step 6 - Testing the device ==

If you device was unplugged before this step, you should plug it back into a USB slot on your system.

You should now confirm that the device is still installed by opening a terminal window and running lsusb:
```

user@ubuntu:~$ lsusb

```Your output should contain a line that has your device's USB ID and description, similar to this:
```

Bus 00X Device 00X: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi

```In the same terminal window run iwconfig and you should see the device as rausb0.
```

user@ubuntu:~$ iwconfig

```
If your system was correctly configured using the Networking applet you should see that your ESSID and Access Point fields have been filled in with your access point's correct information and the Frequency field shows the correctly detected frequency:
```

rausb0    RT2500USB WLAN  ESSID:"MY_ESSID"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:08:74:02:01:FC
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=90/100  Signal level:-42 dBm  Noise level:-202 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```If you configured your network correctly you should see that your ESSID is set for your access point and that the Access Point Media Access Code identifier has been filled in with your access point's MAC identifier.



Run a "netstat -rn" command, and you should see that the correct routing is setup:
```

user@ubuntu:~$ netstat -rn

```
The output should be similar to this example:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 rausb0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 rausb0

```In this case 192.168.1.1 is the gateway address to an Internet router.



== Step 9 - Controlling the device ==

You can now control the device with ifup and ifdown:
```

user@ubuntu:~$ sudo ifdown rausb0
user@ubuntu:~$ sudo ifup rausb0

```

---

### Post by ninjasauce on 2006-11-22
Thankyou, although when I get to Step4 it comes up as user@ubuntu:~/rt2570-1.1.0-b2/Module#  then with the user@ubuntu:~/rt2570-1.1.0-b2/Module# make it says *** /lib/modules/2.6.12-9-386/build: No such file or directory. Stop. rt2570.ko failed to build!

---

### Post by FrodoB on 2006-11-22
This seems to say that you did not get all of step 2 completed. The part that is missing is either part of or all of it. In particular it says that:

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` 
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
Was not successfully completed. Could you check to see that your headers are linked into your /lib/modules directory using the above two commands please?

---

### Post by ninjasauce on 2006-11-22
1) how do i get rid of the user@ubuntu:~/rt2570etcetc

2) first command results in - 
bash: root: command not found
Reading package lists... Done
Building dependency tre... Done
Package linux-headers is not installed, so not removed
0 upgraded, 0 newly listed, 0 to remove and 0 not upgraded

and 2nd command results in -

bash: root: command not found
ln: when making multiple links, last argument must be a directory

---

### Post by ninjasauce on 2006-11-22
just a quick bump.

---

### Post by FrodoB on 2006-11-22
Is the problem that you have no internet access at all at the moment?

---

### Post by ninjasauce on 2006-11-22
Well, I've only just installed ubuntu on to that pc (im on a laptop with windows on which im talking to you on now) and i need to install the usb card to get the internet on.

---

### Post by FrodoB on 2006-11-22
Do you have the regular Edgy 6.10 install or the alternative CD? 

If you can get the machine that you are installing Ubuntu on near enough  to temporarily put it on the net using a wired connection it would be a lot easier.

Otherwise you are going to have to download packages onto the Windows machine and burn a CD to take them to it.

---

### Post by ninjasauce on 2006-11-22
I've got the 5.10 version. The one that comes with the live and the install disk. Dunno if it's edgy (I dont know about those things)

---

### Post by FrodoB on 2006-11-22
Now I understand. You have an older version.  

If you could get either an Ubuntu 6.06 or a 6.10 it just might work out of the box. 

If not then you would still need to get it on the net temporarily to easily get this thing setup.

Can you download a CD image and burn it for 6.10 from the Ubuntu site, or borrow one from someone else?

This post would seem to indicate that it will work out of the box with 6.06 which is the long term support release:

[http://www.hotubuntunews.com/blog_2.shtml](http://www.hotubuntunews.com/blog_2.shtml)

---

### Post by ninjasauce on 2006-11-22
Cheers for the help. The downloads running at about 420=Kb/s atm so I'll just leave it and come back to it in the morning. It'll definitely be done by then. it'll be done by the time I'm asleep but yeah still. 
Anyway thanks for the help.

I'll keep you posted on this. I'll probably need help when I get the 6.10 installed anyway.

---

### Post by FrodoB on 2006-11-22
Sorry for the confusion. I should have asked more questions to begin with.  It may just work for you now, so have the device plugged in during install and maybe it will see it and work with it from the beginning. 

Otherwise report what you see from iwconfig, lspci, and a dump of the data from lsmod with the device plugged in might help as well.

---

### Post by ninjasauce on 2006-11-23
Ok, I've burnt the .iso to a DVD-R and it is in a seperate DVD-Reader (iomega Super DVD) which is plugged into the PC with Ubuntu on.

What mode do I select though to boot through? It's not actually in the CD Drive, it's in a seperate drive which is plugging inthrough USB. I guessed and tried IDE CD-ROM Device although this just boots up the 5.10 ubuntu and doesnt install 6.10 (Edgy Eft)

---

### Post by FrodoB on 2006-11-23
Well you should probably burn it to a CD, but maybe the DVD will work. 

As this is an external drive, it will depend upon the bios in your machine being setup to boot from the external drive.

So take a look and see it you can do it. Had no idea that you have to deal with an external drive.

---

### Post by ninjasauce on 2006-11-23
Neither did I tbh. I only just realised because the pc that i'm installing the os on doenst have a DVD reader. I can I suppose put it on a CD.

Although, the PC isn't even turning on now. My dad said it was something to do with the bios clock or something I can't remember what he said, so I'll try and turn it on again later. 

I'll put it on a CD now.

---

### Post by ninjasauce on 2006-11-23
Ok, it's going onto a CD now. 

I'm going to ask for support on Dell for why my PC isnt starting up :@

---

### Post by ninjasauce on 2006-11-23
Hey, ok I've got the Usunbut 6.10 installed now.

with iwconfig its coming up as

lo no wireless extensions

eth0 no wireless extensions

rausb0 
RT2500USB WLAN  ESSID: " "
Mode: Managed  Frequency=2.412 GHz
RTS thr: off   Fragment thr: off
Link Qualitiy=0/70  Signal level: -120 dBm Noise level: 256dBm
Rx invalid nwid:0 Rx invalid crpyt:0 Rx invalid invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extenions

---

### Post by ninjasauce on 2006-11-23
oooh! just an update. I've got the internet working, just had to entire the eesid name and the wep code and it started. so yeah i'm on there now. Just going to do a test post from it on this thread.

edit; spoke too soon it's gone off again.

---

### Post by FrodoB on 2006-11-23
Well, the unpromising thing is this:

Link Qualitiy=0/70  Signal level: -120 dBm Noise level: 256dBm

It says that you noise level is higher than your signal. But I suppose  that that is not necessarily true.

What is the output of:

 iwlist rausb0 scanning

---

### Post by ninjasauce on 2006-11-23
rausb0      No scan results

edit; i repeated the iwconfig and received same

exept Signal level: -76dBm and Noise level: -212 dBm

edit2; just realised i havent actually installed. doing it now.

---

### Post by FrodoB on 2006-11-23
Do you know that your access point is turned on? If so are you using WPA, WEP, or no security?

To make a record for the device in /etc/network/interfaces you need to start gedit with root privileges like this:

$ sudo gedit /etc/network/interfaces

Then put in a record like this with the correct ESSID filled in and the correct WEP key if you are using WEP:

auto rausb0 
iface rausb0 inet dhcp
wireless-essid My_ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXX


If you want to use ASCII wep keys it should be:

wireless-key s:XXXXXXXXXXXXX

13 characters for ASCII 128bit wep or 26 hex characters for the same thing.

A good wep key generator is at:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)


Once you are sure that the keys match in the Access Point and Ubuntu you can try

sudo ifdown rausb0

sudo ifup rausb0

Hopefully it gets an address from DHCP and works.

---

### Post by FrodoB on 2006-11-23
In fact, I can add this:

iface rausb0 inet dhcp
pre-up ifconfig rausb0 down
pre-up ifconfig rausb0 up
wireless-essid MY_ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX       # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX                  # This line for ASCII (string) keys
auto rausb0


Note the:

pre-up ifconfig rausb0 down
pre-up ifconfig rausb0 up

This is just insurance. The Ralink rt73 devices require it to wake up the device, this one does not, but it has the same name, rausb0, so putting it here does no damage and it might help someone someday.

I also note that removing the device from the system ( a Zonet ZEW2500P in my case) and then rebooting  and attaching the device just before Ubuntu started seemed to kick my Ralink device off and going.

Also mine like to be started up and shutdown from the System -> Administration -> Networking panel after all of these changes have been made, but does not work with sudo ifup rausb0, strange.

It does seem to plug and play, but it takes the device about 12-15 seconds to actually get booted up and running, I suppose that it is loading firmware. So even if all of your setting are correct, you have to wait the 12-15 seconds for the networking to come up and run.

---

### Post by ninjasauce on 2006-11-23
can i just ask? how is my wireless usb card going to work if it hasnt even got the drivers installed?

---

### Post by theavier on 2006-11-24
I just gotta thank you guys! 
I followed the guidelines provided here and that little "plug in" before ubuntuboot did the trick, or the the expanded configuration worked for the interfaces file. Anyway it works!

---

### Post by FrodoB on 2006-11-24
> **ninjasauce said:**
> can i just ask? how is my wireless usb card going to work if it hasnt even got the drivers installed?

Because if your device is the one that we think it is it should just work with the kernel drivers that are installed. At least that is the best I can tell without having your device to work with.

---

### Post by ninjasauce on 2006-11-25
Well I've got a Linksys PCI card (WMP54G) and would that be easier to install than that USB drive?

The only problem i've got atm is that its coming up on the iwconfig and lspci as Broadcom 4306. So I'm going to try and get this working, would you be able to help me with that?

---

### Post by ninjasauce on 2006-11-25
Lol sorry. Just found out that the Broadcom 4306 thing is the chipset for that card. 

from lspci - 01:08.0 Network Controller: Broadcom Corporation BCM4306 802.11g Wireless LAN Controller (rev 03)

---

### Post by FrodoB on 2006-11-25
This is the process. You will be using the .inf files etc. for your device and not the 4306.

I don't know that this is any easier.  Did you try and clean install of Edgy and just insert the device to see if it worked with the built-in Ralink drivers?

---

### Post by aceofhertz on 2006-12-07
FrodoB, that pretty much made my day... I went through every single manual I could to figure this out... thanks for posting a quicker way =)

---

