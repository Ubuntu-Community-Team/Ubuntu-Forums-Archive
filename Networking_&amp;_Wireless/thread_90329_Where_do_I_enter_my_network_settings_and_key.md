---
title: "Where do I enter my network settings and key"
date: 2005-11-14
forum: Networking &amp; Wireless
---

### Post by andy101 on 2005-11-14
Just installed Breezy Badger. It wouldn't connect to network during install. I have tried opening 'network settings' under administration and it lists ethernet and modem. I have a wireless card plugged in. Its a belkin G usb adapter. I can't find where I setup the connection settings. My router (also a Belkin) requires a WEP key to access it so my wireless link won't connect till I enter the key. I have seen something called niswrapper (or similar). Do i need to install this? If so where do I get it? How can I tell if my wireless adapter is recognized or not? Its kind of important so I know whether its a problem with Linux talking with the adapter or whether is a problem communicating with the router. Also is there anyway to view all wireless networks in the area so I can select one to connect to? It appears I need a network connection to install stuff, (this is proberly how ubuntu fits on one disk instead of 4, which in my oppion 1 disk is best cause thoose 4 disks have loads of stuff I am never going to use).

I have the driver installer disk for my wireless adapter, but I think it only works in windows (and I don't want to try and run it in linux incase it screws something up, unless you guys know better (you proberly do, this is my first time setting up Linux)

The part number on my wireless adapters box is: F5D7051uk

I don't mind having to download and install stuff, or having to edit config files on my disk I just need some pointers (and no I don't mean things like char* var ;)).

---

### Post by MightyMouse on 2005-11-14
Check with iwconfig if you have a wlan0 device. If not you can set it up with a windows driver if you install ndiswrapper-utils and ndisgtk. You will get the Windows wireless drivers in System/Administration.
You might want to Google for the Windows wireless drivers, there was a nice online article about it somewhere.

MightyMouse

---

### Post by Lambert on 2005-11-14
This looks to be a very new device so it may/may not work but we'll find out.

Graphical method.
If you can connect while booted into ubuntu download something called ndisgtk.

If you don't know how to install go [here]("https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29")

If you don't see ndisgtk then check the link for adding repositories

Copy all the files from your driver folder on the disk that came with the device. Click system>admin>windows wireless drivers, click and follow the prompts. 

Then go into networking, you should see your card. highlight, click properties, enter your ssid and wep info, click ok thenclick activate.

You can also do this from the command line.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu")
or
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")


If you have trouble open a terminal applications>accesories>terminal and type the following commands in.

```
sudo lshw -C bus
and
iwconfig
and
ndiswrapper -l

``` 
Then post the output back here
for the lshw-C bus command you can limit it to just the section specifically about your wireless device.

---

### Post by andy101 on 2005-11-14
I tried installing ndiswrapper and got an "invalid driver" message.Tried updating it and now ndsiwrapper recognizes the hardware but iwconfig won't

andy@AndyLinux:~$ ndiswrapper -l
Installed ndis drivers:
bcmrndis                driver present, hardware present
andy@AndyLinux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

andy@AndyLinux:~$

It didn't compile ndsiwrapper-utils properly.
My PC only has access to the internet via wireless so when I am in Ubuntu I can't access anything online, thus synaptic and apt-get don't work.

haven't tried ndsigtk yet.

will try 'sudo lshw -C bus' now.

Is installing wireless on Linux always tricky or are some distros easier than others?

---

### Post by Lambert on 2005-11-14
It is tricky because the hardware vendors don't put any effort in developing a native linux driver. 

In your case it looks like you have a device that was just released to market in the past 45 days.

ndiswrapper makes the windows drivers work in many cases but not all. The newer the device and depending on any redisgn in the chipset, ndiswrapper might not be able to make it work.

ndiswrapper -l does show hardward present and driver present but you say you had an error during install. Did you copy all the files from the driver folder (.inf, .sys, .dll) into the directory on your harddrive?

---

### Post by andy101 on 2005-11-14
damn, I think I missed a DLL. Will try that.

Also would using a Windows driver for an older version of windows (e.g. 98, ME, 2000) make any differance?

Not sure exactly which bit of the lshw readout you wanted.

I think this could be the bit:
 *-usb:4
       description: USB Controller
       product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
       vendor: Intel Corporation
       physical id: 1d.7
       bus info: pci@00:1d.7
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: ehci bus_master cap_list
       configuration: driver=ehci_hcd
       resources: iomemory:febffc00-febfffff irq:23
     *-usbhost
          product: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
          vendor: Linux 2.6.12-9-386 ehci_hcd
          physical id: 1
          bus info: usb@5
          logical name: usb5
          version: 2.06
          capabilities: usb-2.00
          configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s

incase its not, I have attached the full readout.

Thanks for the help.

Its a pitty device manufacturers ignore Linux, its a kind of vicous circle, manufacturers won't support Linux till it gets enough users, people won't use Linux till the devices work.

Will try copying the entire contents of the driver folder, and if that still fails might try the windows 2000 driver.

---

### Post by Lambert on 2005-11-14
If the xp drivers don't work you can always step backwards and try the next driver to see if it makes a difference.


I didn't see it in the list. try sudo lshw -C network or just sudo lshw. Look for a device with a logical name that matches the device we're working with. with ndiswrapper I believe it should always be wlan0

---

### Post by andy101 on 2005-11-15
I have been trying to follow the guide at: [http://wiki.ubuntu.com/SetupNdiswrapperHowTo](http://wiki.ubuntu.com/SetupNdiswrapperHowTo)

Didn't work with out of the box ndiswrapper (said it was an invalid driver)
Tryed compilling from source 1.5 ndiswrapper. it created the ndiswrapper-utils ok but wouldn't create ndiswrapper-modules. Gave an error message about some shell script trying to use gcc-3.4 command which didn't exist.

With 1.5 utils it will install the driver and display hardware present driver present, but iwconfig still cant see it.

1.6rc1 won''t install either. I think the problem could be because I don't have an internet connection in ubuntu so apt-get and synaptic doesn't work properly.

Is there any specific packages i should have installed/not installed in synaptic that would help?

i did lshw -C network, output is attached.

---

### Post by andy101 on 2005-11-15
I mentioned this in my first post, but I should have poberly made it clearer. My wireless device is a USB adapter, i.e. it plugs into the USB socket on my PC and sits on the desk. It is not a card thats inserted into the back. Does this make a differance?

Thanks

---

### Post by andy101 on 2005-11-15
For some odd reason whe I try to compile anything from source I get an error message about: gcc-3.4 command unknown, I have checked gcc's version and it is reporting its version as gcc 4.0 and the command gcc-4.0 is known. This error seems to come from one of the kernel header files. However this file appears to be reading something like __GNUCC__ to find out the version number. Any idea why Ubuntu seems to think the compiller is a differant version? Is there anyway to change these values, and if there is is it safe to do so? Maybe if I could compile the source properly ndiswrapper would play nice with my windows driver. There any store of precompilled copies of ndiswrapper I can use if gcc and the headers still won't work?

I have found a couple of things that might get my wieless working if only I could make the compiller work properly, or more precisely the thing responsible for reporting the version for use in make files.

---

