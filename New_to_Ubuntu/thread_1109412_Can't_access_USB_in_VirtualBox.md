---
title: "Can't access USB in VirtualBox"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by UnknownFear on 2009-03-28
I am trying to access my iPod Touch in VirtualBox in XP, but it won't let me. The option is there in the devices tab, but it's greyed out. Does anyone know how to get it working?

---

### Post by cwsnyder on 2009-03-28
Are you using the Open Source Edition of VirtualBox?  The OSE does not enable USB in the virtual machines.  You have to go to the closed source version (still free as in beer, just not free as in speech).

---

### Post by TheLions on 2009-03-28
here is your answer:
[http://tazbuntu.blogspot.com/2008/12/enable-virtualbox-usb-support-in-ubuntu.html](http://tazbuntu.blogspot.com/2008/12/enable-virtualbox-usb-support-in-ubuntu.html)

[HTML]just got around to installing VirtualBox in my newly installed Ibex system.
Finished the install and noticed a warning message that there were no USB ports present or supported.

I know from past experience that to have USB access in VirtualBox that you need the PUEL version from their website and not the OSE version from the repositories.

So I do some searching and found some info that fixed the USB problem and is a very easy fix. It should work for all Ibex users and hopefully this problem will be fixed in future versions.

First make sure you have added your user to the list of VirtualBox users group. To do this just copy and paste the following into your terminal;

$ sudo gpasswd -a YOURUSERNAME vboxusers

Where YOURUSERNAME is your user name.

Now let's add some USB support to VirtualBox. Open the fstab file so you can edit it. Since it needs root permissions we can do it through the terminal with this command;

sudo gedit /etc/fstab

Now that the fstab file is open add the following command to the bottom of the fstab file;

none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

Close the file making sure to save it.
Now reboot your computer and when you open VirtualBox you will have USB support.

Simple enough?

Enjoy!

TaZMAn
[/HTML]

---

### Post by UnknownFear on 2009-03-28
> **cwsnyder said:**
> Are you using the Open Source Edition of VirtualBox?  The OSE does not enable USB in the virtual machines.  You have to go to the closed source version (still free as in beer, just not free as in speech).

I have virtualbox 2.0 I think. I'll reinstall a newer version and see if that does anything.

---

### Post by UnknownFear on 2009-03-28
> **TheLions said:**
> 
So I do some searching and found some info that fixed the USB problem and is a very easy fix. It should work for all Ibex users and hopefully this problem will be fixed in future versions.


That worked! Thanks!!

---

