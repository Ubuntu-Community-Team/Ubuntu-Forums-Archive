---
title: "Can't get Wi-Fi to work in Ubuntu 8.10"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by psfelgate on 2009-02-09
I know this question has been asked dozens of times, though I'm still struggling to get my wireless dongle to work in 8.10.

I got so far as to install ndiswrapper as well as the windows drivers for the device. The gui for ndiswrapper says that the device is present but I get an error when I try to connect to the wireless network even though I can see all the essid's in the area.

I also updated the system but still cannot come right. It is a atheros chipset and the device works in windows xp.

I tried to follow some advice in another thread that said I must type in "sudo modprobe -r b43 b44 ssb". Immediately after running this my adapter stopped showing up in ifconfig. I tried rebooting but the problem still persists.

I installed wicd after that but naturally it does not even pick up the card as ifconfig cant either.

Can someone please help me?

---

### Post by lkraemer on 2009-02-10
Try this to see what Drivers have been loaded, but first unmount
the USB device, remove it, and do the steps in order so I have an
idea what is loaded, etc.

Open a Terminal window:
```

lsusb
ndiswrapper -l

```

now plug in the USB device
```

lsusb
ndiswrapper -l

```

Is the driver that is displayed by ndiswrapper the Windows Driver that
you used?

Post the output of what is displayed on your terminal, and the name of the
Windows Driver if it is different than what is displayed.

lkraemer

---

### Post by superprash2003 on 2009-02-10
if you still have problems post output of **lshw -C network** from the terminal

---

### Post by psfelgate on 2009-02-11
I have reinstalled my laptop with another flavour of linux and I did exactly the same on there that I tried to do with ubuntu and it just worked.

All I did was type

ndiswrapper -i net5523.inf
modprobe ndiswrapper
iwconfig wlan0 essid "wlan"
dhcpcd wlan0

and it all just worked where ubuntu would hang and freeze.

I wonder why that is?

Another interesting thing is that with the other linux my wireless dongle properly shows a lit power led when plugged in whereas ubuntu shows a flashing power led, so clearly something is not working the way it should in ubuntu.

---

### Post by psfelgate on 2009-02-25
Ok, I'm trying to get it working again with ubuntu 8.10. I cant seem to get the ndiswrapper installed.

I ran: sudo apt-get install ndiswrapper-common
and it installed that but when I type ndiswrapper it tells me:
Error: no ndiswrapper utils found!

But when I run sudo apt-get install ndiswrapper-utils I get:

Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate

What do I do now?

---

### Post by psfelgate on 2009-02-25
Okay, I've installed: sudo apt-get install ndiswrapper-utils-1.9

Hope this is right.

But I still cannot connect to my wifi point.

Please someone have any ideas?

---

