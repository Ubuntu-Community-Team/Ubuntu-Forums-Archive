---
title: "Cant Connect"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Chong112193 on 2010-06-22
I am using a Belkin wireless card and at&t service. I cant connect to it. It asks for my password and it trys to connect but doesnt and then asks for password again. Any help would be great. 

Thanks

Chong

---

### Post by Zeike on 2010-06-23
> **Chong112193 said:**
> I am using a Belkin wireless card and at&t service. I cant connect to it. It asks for my password and it trys to connect but doesnt and then asks for password again. Any help would be great. 

Thanks

Chong

Can you provide the model of your Belkin wireless card?

It also might help if you post the output of the terminal command 'lspci -v'.  Please post this in code tags.

---

### Post by anewguy on 2010-06-23
Also, is it asking for your password, or is it asking for the network password?

Dave ;)

---

### Post by Chong112193 on 2010-06-23
> **Zeike said:**
> Can you provide the model of your Belkin wireless card?

It also might help if you post the output of the terminal command 'lspci -v'.  Please post this in code tags.

I have no idea what you mean or how to do what you want. It is a Belkin F5D 8053 N Wireless USB. When i go to connect the box that pops up is the Wireless Network Authentication Required, The setting is WPA personal. I hope this helps. I havent been able to find anything that really helps me. I am brand new to Linux.

---

### Post by Chong112193 on 2010-06-23
Ok I figured out how to do lspci and i do not see my wireless card listed. I also turned off security on my router and that did not help. where can i find a driver for Belkin F5D 8053?

---

### Post by anewguy on 2010-06-23
Please see the following link for information on getting this adapter working.  If you have ANY questions on how to do the things in that link, please post back!  We all know how confusing/intimidating some of this can appear when you are new to it, so we are here to help you!

[Belkin F5D 8053 N Wireless USB]("Belkin F5D 8053 N Wireless USB")

EDIT:  I should add that after the driver is installed, you still have to provide the encryption type and the password/passphrase associated with it in order to connect to the router.

Dave ;)

PS - Since your adapter is a USB device, it won't show in the output of lspci.  "ls" stands for "list" and "pci" means the PCI devices on your system, so "lspci" no matter what options are added will only show PCI devices.

There is a similar command for USB devices, like your adapter - lsusb.  Again, the "ls" stands for "list" and "usb" means the USB devices on your system, so "lsusb" will list the USB devices on your system.

For both of these commands there are also options that can be used to isolate on a specific device, get more detail, etc.  Most of the time when we are trying to help we just want the standard output.

There may be exceptions:

for example, to list the network adapters, we may ask you to do the following or others:

lspci

ifconfig

---

### Post by Chong112193 on 2010-06-23
when i type lsusb i get
kids@ubuntu:~$ lsusb
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 050d:815c Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kids@ubuntu:~$ 

when i type i get

eth0      Link encap:Ethernet  HWaddr 00:15:58:1c:b9:67  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe1c:b967/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4446986 (4.4 MB)  TX bytes:411992 (411.9 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33000 (33.0 KB)  TX bytes:33000 (33.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:75:3c:c4:bd  
          inet6 addr: fe80::222:75ff:fe3c:c4bd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39526 (39.5 KB)  TX bytes:2016 (2.0 KB)

I ran a cord from my router upstairs thru the house so i am online but i would like to be wireless. When i copy the link above this is the address i get [http://Belkin](http://Belkin) F5D 8053 N Wireless USB 

I also found [http://swiss.ubuntuforums.org/showthread.php?t=1382798](http://swiss.ubuntuforums.org/showthread.php?t=1382798) but it might as well be written in chinese. So far all i Know is ls

---

### Post by anewguy on 2010-06-24
Sorry about messing up the link - indeed the thread you found, [http://swiss.ubuntuforums.org/showthread.php?t=1382798](http://swiss.ubuntuforums.org/showthread.php?t=1382798), is the link I was trying to point to.  If you are confused by this thread, please let us know where you get lost and we'll help you through it.

Dave ;)

---

### Post by anewguy on 2010-06-24
Okay, I'm going to see if I can walk you through this.  Be aware I don't have your adapter, so I'm trying to take the instructions in the post and hopefully put things in a way you can follow.  Please remember that Linux is case sensitive, so you must put in uppercase when shown.

(1) While hard wired to your to your router so you can get on the net, copy and paste this into the address line and press enter:

[http://www.ralink.com.tw/support.php?s=2](http://www.ralink.com.tw/support.php?s=2)

This will get you to the ralink support page for downloading Linux drivers.  Look down that page to about the 7th entry or so - the title should read:

RT2870USB(RT2870/RT2770)

Click on this title to begin the download of the file containing the driver for your wireless adapter.

Wait until this has finished before proceeding.

(2) Open a terminal window (Applications/Accessories/Terminal)

(3) My Ubuntu defaults to downloading into a folder called Downloads, so I'm going to assume yours does as well.  With this in mind, type:

cd Downloads <press enter>

(4) Type:

ls <press enter>

You should see a file there called "RT2870_LinuxSTA_V2.3.0.0.tar.tar.bz2". If you don't see this file, STOP here and post back.

(5) Type:

tar xfj RT2870_LinuxSTA_V2.3.0.0.tar.tar.bz2 <press enter>

This will decompress the downloaded driver file and create a folder called "RT2870_LinuxSTA_v2.3.0.0" in the Downloads folder.

(6) Type:

cd RT2870_LinuxSTA_V2.3.0.0 <press enter>

This "c"hanges your default "d"irectory to the newly created folder containing all of the driver information.

(7) Now you must configure the driver.  To do this, you must edit a config file.  The instructions in the link say to use nano, but since you do have a GUI, you can use gedit instead:

gedit os/linux/config.mk <press enter>

This will call up the editor and open the config.mk file supplied with the driver information.  Search for about the section beginning with the 4th leading "#" character.  You should see the following:

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n


These 2 items are describing whether or not the driver supports WPA supplicant (used for encryption).  You need to change both "=n" sequences to "=y" for these 2 items only.  The result should be a section that looks like the following:

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y


Don't change or delete any other part of the file. Now save the file and exit the editor.

(8\) Now the driver must be built.  This requires a couple of packages to be installed first.  Type:

sudo apt-get install build-essential linux-headers-generic <press enter>


This will ask for a password - just type in your regular password.  As you are typing your password nothing will show on the screen but don't worry.  This is a security feature so someone else cannot see your password or know the length.  Just press enter after you have typed your password.  It may prompt you saying it needs to use xxx of disk space and ask if this is ok - just press y and press enter.  Wait for this to complete and return you to the prompt.

Now to build the driver:

make <press enter>

This step actually compiles the driver.

(9) Now to install the driver:

sudo make install <press enter>

If prompted again for your password, just enter it as per step (8\).

(10) Now the default drivers for the adapter delivered in 10.04 must be made not to load, so as not to step on the new driver.  To do so, we add the default driver modules to a "black list" file.  This file is used at boot to tell Ubuntu not to load the certain kernel modules.  The link says to do this in a different file, but I know I don't have that file, and I know the following WILL work - type:

sudo gedit /etc/modprobe.d/blacklist.conf <press enter>

Again, this will open the editor with the file blacklist.conf showing.  Go to the bottom of this file and add the following lines:

# Blacklist the default usb drivers for rslink card
blacklist rt2500usb
blacklist rt2800usb

Save the file and exit the editor.

(11) The link shows part of the code needed to manually remove the existing modules and load the new ones, but the easiest way, as stated in the link, is to just reboot.

(12) Now right click on the network manager icon and be sure "Enable Wireless" is checked.

(13) Click on the network manager icon and see if wireless networks now show.  If so, you're good to go.  Be sure to set up your connection to match the encryption and password/passphrase used on the router, and add your adapters' MAC address to the router MAC address table if you are using MAC filtering on the router.

My EXTREME thanks to user Compu-king for his thread (the link) the contained all of this information.  I just tried ( I *hope* successfully) to make it more friendly to the absolute beginning user.

Please post back letting us know if this worked or not.  Once it is working, please also open the link to the howto and thank compu-king there.

Dave ;)

---

### Post by netwarriorwy on 2010-06-24
@anewguy nice explanation! .@Chong112193 If you still have problems maybe...just maybe (I'm trying to cover all posibilities) your wireless connection on your laptop isn't configured well. Problems may arise when using a Dynamic IP address when DHCP is disabled or only "well-known" IPs are allowed on your router. Or when using Static IP address when DHCP is enabled and that IP is out of the allowed pool of IPs.

If you tell us that everything is fine with the wired connection,check if both wired and wireless connection have the same configuration. To do this right-click over the wireless network icon on top of your desktop. Go to "Edit Connections", in the window that pops up chose the tab Wired, your connections name should be "ethernet" choose it and the "Edit" button on your right will be enabled, click "Edit" choose the tab "IPv4 Settings" and check the "Method" value. If "Automatic (DHCP)" is selected or "Manual", you have to verify you have the same "Method" enabled in you Wireless connection.
To check it just repeat all the steps above, take note that under Wireless Tab you may find several connections, just choose YOURS and follow the steps. Remember you must have the same "Method" as wired (Because you say Wired connection is working).

I hope it helps and good luck!

---

### Post by Chong112193 on 2010-06-24
Thank You Thank You Thank you. That worked perfectly. I was able to understand and learned a few things along the way. I have a lot more questions. I am now going to try to load Java and adobe flash. This Computer is the kids computer and the reason l changed to Linux was because i was sick of all the Junk getting loaded and screwing everything up. 
Other then less viruses and malware, what are the advantages of using Linux or windows. Windows 7 seems very stable and much easier to use. It also seems to run an less powerful machines. Again thanks for the help and i welcome all conversation.

Chong

---

### Post by anewguy on 2010-06-24
Glad that worked - be sure to go to the other link and post a thank you there!

As far as Linux versus Windows, well it's just a matter of choice and what works the best for you.  I still dual-boot because I have a couple of things that I haven't found great replacements for yet without doing a lot of work converting data (I'm lazy!).

With Linux, I get the freedom of open-source, and mostly free software.  It also allows us to "play" a little with things and not worry about reinstalling something and having the software vendor question what I am doing and not giving me another registration try.

But, there are some trade-offs.  You found one - wireless, and that is a common one.  So are video problems.  Both of these are due to drivers.  With Windows, most people have bought a computer that already had all the software and drivers installed prior to their purchase.  Microsoft makes deals with vendors for producing devices and drivers that work with Windows, and this is done with a lot of non-disclosure clauses.  Linux on the other hand wants everything to be open - the source code should be freely available and open to any one who wants it.  The OS itself is open and the source is available.  Manufacturers don't normally go out of their way to create drivers for Linux for their hardware.  Some of this is due to a smaller market than Windows.

There are a lot of very talented people doing all of this work for free.  You won't find that with Windows.

Just my take on it.

Dave ;)

---

### Post by netwarriorwy on 2010-06-24
I'm glad to hear your problem was solved. As @anewguy said the great thing in the Linux world is that if we have a drivers problem there are a lot of people outside willing to help by devoloping their own compatible driver verions. Taka care!

---

### Post by Chong112193 on 2010-06-24
Please understand I am trying to learn this stuff so if my questions seem stupid its because they are. I am going to try to load Adobe flash player and i have to choose one of 5 options 
1)Yum for Linux
2)tar.gz for linux This is the one i think i need.
3).rpm for Linux I think this one is for Red Hat
4).deb for ubuntu 8.04+ Maybe this one
5)APT for ubunto 9.04+ Maybe this one

What is the difference? .deb is for Debian isn't it? 

Thanks again for all the help.

Chong

Im not sure what i did but i am now watching videos on youtube. Im headed in the right direction. Now to figure out sound and Java. 
Is there a Device manager in Linux to see if my sound card is working?

---

### Post by xtremesupremacy3 on 2010-06-24
We can totally understand the confusion between different Linux distrobutions (versions).

Okay, Ubuntu is what they call a 'debian-based OS'...that means Ubuntu uses Deb packages. Most of the time when you are installing from a package like that and the option for a .deb file is available, then that's the one you want to get.

But before you do that, have you checked in the repositories if your package might be there?
If you have no idea what I am talking about then you can do two things to check:

1) Under Applications, you will find the Ubuntu Software Center. Open that up and type in 'Adobe', if it appears on the list what you are looking for, simply click install.

2)Click on System > Synaptic. This is basically the same as the Ubuntu Software Center but without the bling. It works the same though.

What we advice is that before you go to an internet site to download something, to check if it's in the repositories first. That way it is much quicker and more support for it if it requires extra packages.

Let me know if you need further explaining.

Welcome to Ubuntu

---

### Post by xtremesupremacy3 on 2010-06-24
Oops, I forgot about the sound question then.

There sure is an option for that.

Click on System, Preferences, then click on Sound.

If all is well, then you should be able to see little sliders.

As for Java, try this:

Click on Applications > Accessories > Terminal

And type the following (or copy and paste):
```
sudo apt-get install sun-java6-jre
```

Now, hit enter and when asked, enter your password (dont worry if nothing shows up as you type your password, thats normal).

Now if it doesn't spew out any errors then after a few minutes, you have java.

Arthur

---

### Post by anewguy on 2010-06-24
Yeah, for the sound thing definitely check the sliders and if anything you might need is muted.  After all this time, when I saved everything and then installed 10.04 when it came out, I couldn't figure out why my sound wasn't working.  I even started a thread on the forum, only to find out my sound was muted!  Talk about embarrassing.  

Also - understand there is no dumb question!  It's okay to be new and need help.  Heck, I'm not new and I still need help (of course, people have been telling me that for years anyway!).  Everyone has been there, or is still there to some extent, and we're here to help when we can!

Dave ;)

---

### Post by Chong112193 on 2010-06-24
You guys ROCK! We have Video we have Audio (i had to un-mute it) Im going to run like this for a while and if the kids dont crash it I will probably delete windows all together. Thank you so much for the help.

---

### Post by tdlucas on 2010-08-30
Just wanted to say many thanks. I followed Dave's clear and concise instructions and this worked like a dream.

As a tip for anyone else in a similar predicament, the file at Ralink has been updated and the extracted folder names are now different. If you want to find the exact tar file that is mentioned in the instructions, you can get it [here]("http://www.apfelkraut.org/download/RT2870_LinuxSTA_V2.3.0.0.tar.tar.bz2")

Many thanks again guys for your excellent help.

---

### Post by tdlucas on 2010-09-05
Ah. Having successfully installed the Belkin wireless adapter, I now have two sets of wireless networks showing up in my network manager. Could someone please give me some assistance in explaining how to uninstall the built in wireless card (which was rubbish anyway) in my Revo R3610.

Many thanks

---

