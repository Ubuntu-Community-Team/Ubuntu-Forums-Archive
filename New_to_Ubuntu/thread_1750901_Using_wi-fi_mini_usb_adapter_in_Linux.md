---
title: "Using wi-fi mini usb adapter in Linux?"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by juggleclown on 2011-05-06
Hey, it's been a while since I asked a question here. I'm still awful with Linux and have been trying out a few distros. Right now I'm primarily tinkering with Lucid Puppy, as I'm thinking about getting something like the Gecko Edubook.

My main concern is a problem I've been trying to solve for the last eight or so months that's been a real detriment to my learning Linux. Well, this and having to reinstall Puppy Linux if I lose power without shutting down, as I end up booting to a command prompt and have no idea what to type after the hash '#' to fix it.


Seeing as this is the Ubuntu forum, I'm happy just learning how to do this in Ubuntu, and hopefully I'll figure out how to do it in other distros later. My problem is that I can't figure out how to use the mini usb adapter I bought on eBay in Linux. I can use it easily on any computer in Windows with the included driver cd (a mini-cd that says edup or something like that on it), but no such luck in Linux.

[Here's a listing for one just like mine.]("http://cgi.ebay.com/Mini-150Mbps-USB-Wireless-Adapter-LAN-WIFI-802-11n-Pink-/110627395318?pt=LH_DefaultDomain_0&hash=item19c1e816f6")

I recently got a Samsung Epic, and if I enable wifi and tether it, Ubuntu and Puppy have no problem finding it. I'm in Puppy right now, and it shows up as a wired connection on usb0. When I try to use the wi-fi adapter, it doesn't seem to see it at all, like it's not even there.


I've been stumped for nearly a year now, so as much as I'd rather not bother you with my idiotic problems, I can't do a damn thing in Linux without wi-fi and could seriously use some help to get at least this far. :confused:


Thanks in advance.

---

### Post by wep940 on 2011-05-06
As with Windows, you need a driver to use the device in Linux.  One of the differences between Windows and Linux is that the manufacturers usually don't make or include a Linux driver.  So, what would I do?  There are things specific to Ubuntu to try, but I don't think they even apply to things like Puppy.  So, let's try things a little more basic:

- with the adapter plugged in to a USB port, open a terminal window, type lsusb, then post the output back here.  That will give us a USB manufacturer id and product id (the xxxx:xxxx string) that we can then use to search the net, such as:

linux+xxxx:xxxx+driver

A lot of times this type of search will return many different things to try.  We'll try to help you when you post the output back here.

---

### Post by juggleclown on 2011-05-06
On a Thinkpad R32 in Ubuntu 10.04 booting from the CD, I plugged the pink wifi adapter into one of the two usb ports (the other port was unused) and typed lsusb into Terminal. Here are the results:

```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 148f:3370 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Ubuntu 10.04 otherwise seemingly ignores the presence of the adapter, but when I plug in my phone in wifi tether mode, Ubuntu automatically starts to use it, and currently shows the Up/Down arrow at the top of the screen, and highlighting it says "Wired network connection 'Auto usb0' active".


Tethering is definitely a good temporarily solution, and perhaps my future netbook will be one with built-in wifi that will automatically work with most distros, but ultimately I'd like to be able to use a usb adapter such as the one I already have, and I don't understand why my phone's tethering works instantly while the adapter seems to require additional effort.

---

### Post by wep940 on 2011-05-06
This link gives info specific to ubuntu for getting the adapter to work:
 
[http://forum.aircrack-ng.org/index.php?topic=5755.0](http://forum.aircrack-ng.org/index.php?topic=5755.0)
 
I haven't been through it all, but I believe it involves patching a driver module for the rt2800STA driver, removing a couple of conflicting driver modules, and installing the newly patched module.
 
Normally, in Ubuntu, we have people temporarily hard-wire a connection and do the following:
 
- in a terminal window:  sudo apt-get update
 
- go to system/administration/additional drivers (might say restricted drivers) and let it check for drivers while the hard-wire connection is still up.  If it finds any, it should install and enable them
 
- physically disconnect the hard-wire cable, then go to network manager and see if wireless is enabled and if any networks show
 
Now, since you want to use this on something other than Ubuntu, I might suggest trying ndiswrapper and the Windows XP (*only*) driver files (the .inf and .sys files) matching your Linux OS architecture (32 or 64 bit).

---

### Post by juggleclown on 2011-05-06
The Hardware Drivers section seems to be totally empty, even after performing 'sudo apt-get update'.

As for the link, I'll have to try it later, but it looks incredibly complicated, especially in contrast to the fact that, again, the phone tethering requires absolutely no effort, for reasons I have yet to understand.

I'm not sure what ndiswrapper is, how to get it, how to install it, and how to use it. I seem to be poor with instructions, it takes me several hours to install the latest Java in Puppy Linux, and can't understand the instructions for installing programs outside of repositories like the Ubuntu Software Center. I'd probably be just as bad with Windows if not for the fact that I've had countless opportunities to get help in person, though have never met anybody in real life has ever tried Linux.


In Puppy Linux, I once tried locating the *.inf file from the driver cd and choosing it, as requested by one of the network setup options for choosing a Windows driver. This had no effect.

---

### Post by wep940 on 2011-05-07
If you tried the .inf file in Puppy, then I assume you mean using ndiswrapper and possibly ndisgtk.  You must have more than the .inf - you must have the .inf and the .sys files.  They also *MUST* be Windows XP drivers.   This is a must - the others won't work - sometimes you'll see a device but can't connect with it, other times it just flat out doesn't install.

---

### Post by juggleclown on 2011-05-08
> **wep940 said:**
> If you tried the .inf file in Puppy, then I assume you mean using ndiswrapper and possibly ndisgtk.  You must have more than the .inf - you must have the .inf and the .sys files.  They also *MUST* be Windows XP drivers.   This is a must - the others won't work - sometimes you'll see a device but can't connect with it, other times it just flat out doesn't install.

I *mean* I right-clicked the network tray icon, chose "Setup networking" to open "Barry's Simple Network Setup", clicked the 'Windows' button to "install and use a MS Windows driver", selected the *.inf file directly from it's location on the CD, and... nothing happened.

It was on the cd, there were *.sys files too, and obviously they were Windows drivers, since they work fine in and were designed for Windows XP.


Unfortunately, I have yet to get through the instructions in that link you posted. I've gotten a headache and a lot of confusion, but haven't gotten too far through it and will have to give it a try later.


On the bright side, I've been easing myself back into Linux and learned how to rotate the display with 'xrandr -o [orientation]', learned how to put the system into sleep with 'echo -n mem > /sys/power/state', figured out how to make a shortcut on the desktop in Puppy to execute the 'sleep.sh' that I made to do this, and learned how to get back into the GUI from the prompt using 'xwin', so I won't have to reinstall Puppy the next time it doesn't shut down properly.

I almost feel like I have a chance at becoming competent with Linux, and then I can start customizing things, as I'd rather have my system vanilla while I'm still trying to learn the absolute basics. :guitar:


Unfortunately, I can't do a whole hell of a lot in Puppy yet, compared to Ubuntu which I'm still not terribly proficient with, but learning is a hell of a lot more fun now that I can solve problems without being at a cramped desk tied to an ethernet cable. Still need to get a usb dongle to work, or else I'll have to velcro my phone to the back of my laptop! :rolleyes:

---

