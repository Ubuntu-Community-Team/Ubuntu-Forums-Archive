---
title: "Ndiswrapper USB Wireless Adapter Error"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by EfrenP on 2009-02-08
I've been trying to get my wireless USB adapter to work on Ubuntu by using Ndiswrapper to install the driver it needs to work.

I'm using a Dynex Wireless EnhancedG Usb Adapter


I install the driver correctly using ndiswrapper

```
ndiswrapper -i NDISWDM.INF
```

I check if I have it installed and it checks out ok, but when I use
```

modprobe ndiswrapper
``` I get some weird errors/bugs

for one thing I can't use

```
lsusb
``` anymore, the terminal just doesn't seem to tell me what I have.

I can't use ```
ndiswrapper -l
```

I tried using the GUI version "Wireless Network Drivers" to install my driver but it just gives me a error with no error description :(

This is a screenshot of what I get when I install my driver and want to use Wireless Network Drivers

[IMG]http://img7.imageshack.us/img7/3343/error1pl5.png[/IMG]

This is my inf file I'm using that came with the cd.
[http://pastebin.com/m5f44d885](http://pastebin.com/m5f44d885)

I hope I can get to the bottom of this problem because I really want to use my USB Adapter.


This problem not only doesn't let me use my USB adapter but I can't turn of my computer properly I doesn't finish shutting off and when I start-up my computer again I need to run a system check so it can repair/fix some files that where damage due to ndiswrapper or my driver.

---

### Post by lkraemer on 2009-02-09
Here are some commands for ndiswrapper & modprobe:

ndiswrapper - tool

The user space tool (/usr/sbin/ndiswrapper) is used whenever a new Windows XP driver is to be installed. This program takes the following options:

OPTIONS

-i <inf file>
    installs new Windows XP driver, where <inf file> is full path to INF file for that driver. 
-l
    lists the currently installed drivers. 
-e <driver>
    removes an installed Windows XP driver named <driver>. 
-m
    writes an alias for wlan0 (default wireless device) into module configuration file so that ndiswrapper kernel module is loaded automatically when this interface is used. 

modprobe [ -r ] [ -v ] [ -n ] [ -i ] [ modulename ... ] 
-r --remove
    This option causes modprobe to remove, rather than insert a module.


So, I'd try removing the driver first with
```

ndiswrapper -e ndiswdm.inf
modprobe -r ndiswrapper

```


Then do the following in the Terminal window:
```

ndiswrapper --help
lspci
ndiswrapper -l

```

and post the output.

ndiswrapper --help will tell us if ndiswrapper is installed in Ubuntu
lspci will tell us if the USB device is detected.  Run it once with the
USB device unplugged and then again after plugging in the USB device.
ndiswrapper -l will list all currently installed drivers.

Are you sure the Driver Filename is in all CAPITALS?
I'd bet it isn't, and there is a difference!
DOUBLE CHECK THE FILENAME AND UPPERCASE or LOWERCASE characters.

I haven't a clue as to what you might have done in the GUI.
If you can properly UNDO all of that we will try ndiswrapper again.

Also, use your Windows machine to pop in your CD for the USB drivers
and go to START -> RUN
Then type 
cmd      and press enter
A command window will come up.  do a cd\ which will get you to C:\
Then do a
dir D: > dirlst.txt
If your CD Drive is something other... use that for D: above

Copy the file contents of dirlst.txt and post the listing here.
exit will get you out of the windows command window.
 
lkraemer

---

