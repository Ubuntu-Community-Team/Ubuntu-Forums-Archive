---
title: "Unable to Install T-Mobile (Mobile) Broadband"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by BrettUK on 2008-12-28
Using Ubuntu 8.04 I am having problems installing the Mobile Broadband. I have copied the contents of the CD and placed it on a USB key, I have even copied the contests from the key onto my desktop. I clicked on the .exe but nothing seems to happen. The disk or key does have Linux drivers so I know it’s compatible but what am I doing wrong?

Should the .exe run just like windows or does the installation require me to install the application in another way. 

Thanks for the help

Brett

---

### Post by prshah on 2008-12-28
> **BrettUK said:**
> 
I clicked on the .exe but nothing seems to happen. The disk or key does have Linux drivers so I know it’s compatible but what am I doing wrong?

You should not have an .exe file for linux. EXE is a Windows (/DOS) executable format, or possibly a self extracting file.

Can you post the list of contents of the CD here? Then it will probably be a lot easier to guide you.

---

### Post by gsocker on 2008-12-28
The Windows drivers (the .exe file) will not work in Ubuntu. You may not need to install anything. Assuming this is an external card, try plugging it in. Then, run ```
dmesg
``` from a terminal and look at the last couple of lines. If it's recognized, you should see something along the lines of:
"USB serial support registered for *name of device*

If that shows up, all you will need to do is configure the PPP dialup software. If nothing happens, please post the name of the card you are trying to use.

---

### Post by BrettUK on 2008-12-28
> **prshah said:**
> You should not have an .exe file for linux. EXE is a Windows (/DOS) executable format, or possibly a self extracting file.

Can you post the list of contents of the CD here? Then it will probably be a lot easier to guide you.


Within the CD the following can be found

Folders 

Linux
x32
x64
Autorun
Setup
Webnwalk manager icon

Within the Linux folder the following folders can be found

Asus_EEE_PC_Installation 
Linux driver installation

As i do not have an asus_ee_PC can i will assume you want the info for the other Linux dir

Under the Linux driver installation folder the following can be found

hso-1.6.tar & udev.tar

Within the above 2 files there are lots of different files and types. Would be easier if I could email or attach them and upload them as a zip file if you wish

---

### Post by DGortze380 on 2008-12-28
> **BrettUK said:**
> Within the CD the following can be found

Folders 

Linux
x32
x64
Autorun
Setup
Webnwalk manager icon

Within the Linux folder the following folders can be found

Asus_EEE_PC_Installation 
Linux driver installation

As i do not have an asus_ee_PC can i will assume you want the info for the other Linux dir

Under the Linux driver installation folder the following can be found

hso-1.6.tar & udev.tar

Within the above 2 files there are lots of different files and types. Would be easier if I could email or attach them and upload them as a zip file if you wish

looks like you'll have to compile to drivers. there should be a readme file in the Linux foler (or elsewhere on the disk) to tell you exactly how to do it. If not, there should be documentation with the device, or call t-mobile for specific support.

---

### Post by BrettUK on 2008-12-28
> **gsocker said:**
> The Windows drivers (the .exe file) will not work in Ubuntu. You may not need to install anything. Assuming this is an external card, try plugging it in. Then, run ```
dmesg
``` from a terminal and look at the last couple of lines. If it's recognized, you should see something along the lines of:
"USB serial support registered for *name of device*

If that shows up, all you will need to do is configure the PPP dialup software. If nothing happens, please post the name of the card you are trying to use.

Attached is a screen shot, hope this helps

---

### Post by shifty_powers on 2008-12-28
erm, hate to say it, but this is all probably completely unnecessary.

network manager 0.7, included in 8.10, comes with the ability to configure and run your mobile broadband, and should work with your t-mobile dongle.

you won't get any free texts or whatever, (never bothered me with my 3 dongle), but my 3 dongle works like a dream.

either upgrade to 8.10, or install the network manager 0.7...

---

### Post by BrettUK on 2008-12-28
> **shifty_powers said:**
> erm, hate to say it, but this is all probably completely unnecessary.

network manager 0.7, included in 8.10, comes with the ability to configure and run your mobile broadband, and should work with your t-mobile dongle.

you won't get any free texts or whatever, (never bothered me with my 3 dongle), but my 3 dongle works like a dream.

either upgrade to 8.10, or install the network manager 0.7...

Shifty, 

As I am a complete newbie to Linux I would rather not try upgrading yet, only got the laptop for xmas and want to play with it for a while before I decide to atempt something like that.

If its possible to install the network manager for 8.04, with support for what I need that would be the way to go for me. 

Silly question, how can I install the network manager 0.7 or where can I find it?

Thanks

Brett

---

### Post by gsocker on 2008-12-28
Ah, you have one of the ones which has the software "built in" - it shows up as a virtual CD-ROM. Unfortunately, this complicates matters. 
You will need to build the driver included on the CD.
Install build-essential and kernel-headers, if not already installed. 
Do the following from a terminal.
Untar the hso-1.6.tar:
```
tar xf hso-1.6.tar
```
This should create a directory. Look for a README file with instructions. 
[http://www.pharscape.org/hso.html]("http://www.pharscape.org/hso.html") has instructions for this driver. Try following those as see how it goes.

---

### Post by shifty_powers on 2008-12-28
> **gsocker said:**
> Ah, you have one of the ones which has the software "built in" - it shows up as a virtual CD-ROM. Unfortunately, this complicates matters. 
You will need to build the driver included on the CD.
Install build-essential and kernel-headers, if not already installed. 
Do the following from a terminal.
Untar the hso-1.6.tar:
```
tar xf hso-1.6.tar
```
This should create a directory. Look for a README file with instructions. 
[http://www.pharscape.org/hso.html]("http://www.pharscape.org/hso.html") has instructions for this driver. Try following those as see how it goes.

not with the new network manager you don't.

i'll have a look and get back to you brett.

---

### Post by BrettUK on 2008-12-28
> **shifty_powers said:**
> not with the new network manager you don't.

i'll have a look and get back to you brett.

Thanks Shifty, I am trying to get this up and running before Tuesday.

I will wait to hear from you

Brett

---

### Post by shifty_powers on 2008-12-28
go to system>administration>software sources>thirdparty software>add

then

```
deb http://ppa.launchpad.net/network-manager/ubuntu hardy main
deb-src http://ppa.launchpad.net/network-manager/ubuntu hardy main
```

one after the other.

then system>administration>synaptic

click on reload,

and search for network-manager and make sure you mark the 0.7 version, and unmark the old version for complete removal, then click apply.

once 0.7 is installed, plugin your modem and then right click on the system tray icon then you will see an option for you dongle, which will then give you the option to set-up and use it.

any q's just shout.

---

### Post by gsocker on 2008-12-28
How, exactly, is upgrading NetworkManager going to help when the kernel his system is running lacks support for the hardware? It **will** make using it quite easy once it is recognized by the kernel as a modem. If you look at the screenshot posted, note that it shows up as  a CD-ROM drive. This is called different things by different manufacturers, but it allows them to bundle the drivers on the modem so no CD is required. Until it shows up as  one or more serial ports NetworkManager will be **useless** since the kernel thinks it is a CD drive.
This has to be disabled to actually use the dongle as a modem. 
Brett: make sure you have all the updates.
Check and see if /dev/ttyHS0 is present. If not, and it still 
 shows up as a CD drive, you will have to build the driver from the source on the CD.

---

### Post by BrettUK on 2008-12-28
> **gsocker said:**
> How, exactly, is upgrading NetworkManager going to help when the kernel his system is running lacks support for the hardware? It **will** make using it quite easy once it is recognized by the kernel as a modem. If you look at the screenshot posted, note that it shows up as  a CD-ROM drive. This is called different things by different manufacturers, but it allows them to bundle the drivers on the modem so no CD is required. Until it shows up as  one or more serial ports NetworkManager will be **useless** since the kernel thinks it is a CD drive.
This has to be disabled to actually use the dongle as a modem. 
Brett: make sure you have all the updates.
Check and see if /dev/ttyHS0 is present. If not, and it still 
 shows up as a CD drive, you will have to build the driver from the source on the CD.

how can i check if the /dev/ttyHS0 is present

---

### Post by gsocker on 2008-12-28
In a terminal, do ```
ls /dev/ttyHS*
```. 

Sorry if my previous post offends someone.
However, there are a couple of levels involved in getting a usb modem like this working.
1. The kernel must find the device. 
2. It must recognize that device as a modem(usually this will result in one or more serial ports appearing).
Here is what my Sierra Wireless 881 3G card shows up as(from dmesg):
```
usb 5-1: new full speed USB device using ohci_hcd and address 2
usb 5-1: configuration #1 chosen from 1 choice
sierra 5-1:1.0: Sierra USB modem (3 port) converter detected
usb 5-1: Sierra USB modem (3 port) converter now attached to ttyUSB0
usb 5-1: Sierra USB modem (3 port) converter now attached to ttyUSB1
usb 5-1: Sierra USB modem (3 port) converter now attached to ttyUSB2

``` 
This is the point we need to get to for NetworkManager to be useful. Without the correct devices showing up NetworkManager is pointles since it will not "see" the card.
Yours will look different since your card is made by Option. It will probably show up as /dev/ttyHS0 once the driver is installed.

3. Once previous steps  are complete, step three is to get the userspace portion going. This is what the NetworkManager upgrade is designed to make simple. However, it is possible to get it working just fine without it.

The original poster is still at step one - the device is recognized but is showing up as a CD, not a modem. I believe the manufacturer calls this "ZeroCD". This will need to be disabled - the URL in the earlier post mentions a utility called "zerocdoff". Until this is disabled, trying to load the correct driver will probably fail since usb-storage has already claimed the device.

---

### Post by zvacet on 2008-12-28
> How, exactly, is upgrading NetworkManager going to help when the kernel his system is running lacks support for the hardware?

Kernel will support that hardware if he install hso or network-manager.Believe me installing network-manager is easier thing to do.As far I know that kind of connection is nativly supported on Itrepid but not in Hardy so you need to install network-manager that **shifty_powers** recommended.

---

### Post by gsocker on 2008-12-28
> **zvacet said:**
> Kernel will support that hardware if he install hso or network-manager.Believe me installing network-manager is easier thing to do.As far I know that kind of connection is nativly supported on Itrepid but not in Hardy so you need to install network-manager that **shifty_powers** recommended.
You need **both**.
One last time: Without the **kernel** creating one or more serial ports after the device is plugged in, NetworkManager will not work.
 NetworkManager is only a nice interface. It is not a driver in and of itself. It relies on the kernel to talk to the modem and create the device files. For the OP's modem, this driver  appears to be the "hso" module, the source to which is on the CD he received with it.

If installing NetworkManager pulls in the hso driver as well, that will work. However, looking at the package, it does not appear to depend on any kernel module packages.

---

### Post by BrettUK on 2008-12-29
> **gsocker said:**
> You need **both**.
One last time: Without the **kernel** creating one or more serial ports after the device is plugged in, NetworkManager will not work.
 NetworkManager is only a nice interface. It is not a driver in and of itself. It relies on the kernel to talk to the modem and create the device files. For the OP's modem, this driver  appears to be the "hso" module, the source to which is on the CD he received with it.

If installing NetworkManager pulls in the hso driver as well, that will work. However, looking at the package, it does not appear to depend on any kernel module packages.


I have installed the network manager at Shifty recommended and my options for wireless and wired connections have changed. I now see an option for mobile broadband but when I plug in my dongle for the mobile connection nothing happens.

---

### Post by BrettUK on 2008-12-29
[QUOTE=gsocker;6451603]In a terminal, do ```
ls /dev/ttyHS*
```. 

I have done as you asked and it says No such file or directory

can we do something with this so i dont have to build the drivers. Looking at the other posts it is complicated and i am not clear on what i need to download

Brett

---

### Post by gsocker on 2008-12-29
You are running 8.04, right? I can  try to build the driver and send you the module or I can talk you through it on IM or IRC

---

### Post by BrettUK on 2008-12-29
> **gsocker said:**
> You are running 8.04, right? I can  try to build the driver and send you the module or I can talk you through it on IM or IRC

If you can build the driver that would be great.

On saying that I do have some drivers that maybe useful, PM me your email or if you are on MSN your addy and I will send you the drivers I have and you can see what you can do with them

Thanks for your help its most appreciated

---

### Post by MenZa on 2008-12-29
I have to admit, I'm more in favour of upgrading your system. It's very, very easy:

```

sudo update-manager

```

You should see a 'New Release' (or similar) button. Click it. Then follow on-screen instructions.

Very simple.

---

### Post by BrettUK on 2008-12-29
> **MenZa said:**
> I have to admit, I'm more in favour of upgrading your system. It's very, very easy:

```

sudo update-manager

```

You should see a 'New Release' (or similar) button. Click it. Then follow on-screen instructions.

Very simple.

I am happy to upgrade to the latest version but will it resolve the initial problem that the Kernel sees the dongle as a CD drive and not a modem. I don’t want to go thought the upgrade to find I still have the same issue

---

### Post by gsocker on 2008-12-29
Let's try getting it working under 8.04. 8.10 includes version 1.2 of the driver. The current version is 1.6. If 1.2 doesn't support his card the driver will have to be compiled anyway, and the upgrade will pull several hundred MB's worth of packages and probably take at least an hour after it's finished downloading.

---

### Post by barneybunkle on 2009-01-16
Hello, I have just started to use Ubuntu- had never heard of it before it was  installed it on my Eee PC 900 last week!-and have the same problem as BrettUK, can't get my T-Mobile Mobile Broadband USB stick to work. I'm sorry but I'm not a technie and would really appreciate some very simple advice on how to get it to work if that's possible. Nothing atall happens when the stick is plugged in.

---

### Post by barneybunkle on 2009-01-16
Sorry, I should have said that I have version 8.04

---

### Post by gsocker on 2009-01-20
Pretty simple. 
Steps:
1. Get a copy of hso-1.6.tar.gz and udev.tar.gz from [http://www.pharscape.org/forum/index.php?board=14.0](http://www.pharscape.org/forum/index.php?board=14.0)
Put them in your home folder.
2. Open Terminal(probably under accessories).

2. Install neccesary packages:
```
sudo apt-get install build-essential linux-headers libusb-dev
```
3. Extract the driver: ```
 tar zxvf hso-1.6.tar.gz 
```
4. Compile/install the driver: ```
 cd hso-1.6
make
sudo make install

```
5. Compile/install the zerocdoff utility.
```
 tar zxvf udev.tar.gz
cd udev
make clean && make
sudo make install

```

At this point, the modem should show up after a reboot.
There are two ways to manage it: you can either use the traditional PPP tools such as wvdial and gnome-ppp, or you can follow this post: 
   [http://ubuntuforums.org/showpost.php?p=6451112&postcount=12](http://ubuntuforums.org/showpost.php?p=6451112&postcount=12)
to install the latest version of NetworkManager which has support for wireless broadband modems.

If you have any problems please post error messages.
If you are not familiar with sudo, you enter your login password when it asks you for one.

---

### Post by sebasters on 2009-02-20
Please help, nwm0.7 does see my option globetrotter thingy but it will not connect to t-mobile-netherlands.

it returns the message " the connection could not be establist" 
(well...something similar in my language that is.)

i have ubuntu8.10, nwm 0.7, ozerocd installed, hso driver1.9 installed, libusb-dev12.12 installed.

Also the nwm lists the hsdpa modem twice, but ppp doesn´t see any modem at all
does the nwm connect to the modem with the wvdial.conf file?

---

### Post by katumba1 on 2009-02-20
So, I'm running 8.10 and have the mobile broadband manager up and config'd for my t-mobile card.

Question is, how do I get it to connect over that card? I've selected the 'connect auto' button, and even disabled the other cards. I don't see any option for 'connect' anywhere.

Help! I'm trying to dump windoze and this wireless card is important.

Thank you!
Kat

---

### Post by katumba1 on 2009-02-24
bump. any help on this?

---

### Post by Captain_tux on 2009-03-14
Katumba and Sebasters: I highly recommend you begin your own threads... whilst this thread is relevant to your problems, posting your own thread will enable better tailored support for your particular issues.

Good luck!

---

### Post by mcdreamy81 on 2009-03-14
Get Intrepid Ibex and using mobile broadband will become ridiculously easy.

---

