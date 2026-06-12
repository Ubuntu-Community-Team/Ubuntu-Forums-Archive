---
title: "Realtek 8192SU USB wifi adapter"
date: 2014-01-12
forum: Networking &amp; Wireless
---

### Post by kristen2 on 2014-01-12
I'm urgently in need of a driver for belkin f9l1001v1... It's the N150 wireless USB adapter. I just bought it today because my previous adapter is broken. The installation included with the device is for Windows but, of course, I'm using Linux. Anyone know where it is available for download? Help me out pleaaase! Thank you so much.

---

### Post by carl4926 on 2014-01-12
Let us see from a terminal

```
lsusb -v
```

---

### Post by kristen2 on 2014-01-13
lsusb -v returns a very long output. I can't copy & paste it because I'm posting on the forum from a device that is not my computer. My computer has no connection lol you know. So, yeah. The output is really long. What are you looking for?

lsusb returns
```
Bus 001 Device 007: ID 050d:945a Belkin Components 
```

---

### Post by carl4926 on 2014-01-13
There is an older thread here
[http://ubuntuforums.org/showthread.php?t=1721410](http://ubuntuforums.org/showthread.php?t=1721410)

see if it is similar to your device

---

### Post by squakie on 2014-01-13
Indeed, the USb xxxx:xxxx string tells you the manufacturer id (050d) and the product id (945a).  Looking up that USB string says the chipset used is indeed Realtek 8192SU,, so what you are looking for is the driver, and how to activate it, for a Realtek 8192SU.  The thread carl4926 is indeed old (like back to 10.xx), so I'm not sure how much of it still applies.  There is a linux driver (source form) at [www.realtek.com](www.realtek.com).  It looks like it turns around and builds the 8192cu driver, so perhaps they both use the same driver.
 
In either case you would need some additional things installed:  build-essential, linux-headers, etc., which would need to be downloaded as well.

I don't know myself how to take the list of what you need, go to another system and download them, them copy them back to your system and do the install.sh which is part of the driver download from Realtek. 

Perhaps someone else can help you there.  The Realtek thing itself is a simple download - I just don't know how to go about getting the headers, build-essential, etc., for your particular release and just download the packages, not install them, so you can copy them to your PC to install them.

---

### Post by kristen2 on 2014-01-13
I don't know. I tried this: 
```
Run this command:
sudo gedit /etc/udev/rules.d/network_drivers.rules 

And add this line to the file (which may be empty) and save:

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="945a", RUN+="/sbin/modprobe -qba r8192s_usb"

Then run this command:
sudo gedit /etc/modprobe.d/network_drivers.conf 

And add this file (and save)
install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb  $CMDLINE_OPTS; /bin/echo "050d 945a" >  /sys/bus/usb/drivers/rtl819xU/new_id

Finally, download this file:
[http://svn.debian.org/wsvn/kernel/di...rtl8192sfw.bin]("http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin")

and copy it to the directory /lib/firmware/RTL8192SU/
```

but it had no effect, it appears. My computer is actually Ubuntu 10.04, so shouldn't that have worked?

---

### Post by carl4926 on 2014-01-13
You would do well trying 13.10, even if just the live cd. It may work OOTB

---

### Post by kristen2 on 2014-01-13
I don't have a live CD. How do I obtain that? Preferably 12.04. Do you think all of the above would work on 12.4?

---

### Post by coffeecat on 2014-01-13
> **kristen2 said:**
> My computer is actually Ubuntu 10.04, so shouldn't that have worked?

No. Ubuntu 10.04 is still supported for the server version but not for the desktop version. A lot of your GUI is out-of-date and as far as the web browser is concerned, a potential security risk. You need to think about upgrading or re-installing with a newer version of Ubuntu.

But as far as the driver for your wireless device is concerned, a more recent version of Ubuntu will have a newer kernel and more up-to-date drivers. What doesn't work in 10.04 may well work in 13.10 - hence carl4926's suggestion.

> **kristen2 said:**
> I don't have a live CD. How do I obtain that? Preferably 12.04. Do you think all of the above would work on 12.4?

Again - if you want to test your wireless device you are strongly advised to try the latest available version. The Realtek drivers in 12.04 will likely be 2 years old. A lot can happen in 2 years.

If you want to try a live session of Ubuntu, you can download the ISO from here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

You can get both 12.04 and 13.10. If you have the bandwidth, I suggest you try both.

Burning to CD/DVD and/or USB is covered here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

The ISO for 13.10 is too large for a CD and you will need a DVD. I'm not sure about 12.04 - that may still fit on a CD.

Be warned that both 12.04 and 13.10 use the newer Unity desktop which will be very different from what you are used to in 10.04 - the old gnome 2 desktop. Disregard all the trolling about Unity that you may find around the internet. It's a perfectly usable desktop environment that suits some people but not others. Some people disliked it at first, but now like it. Others dislike it and prefer other desktops. And others liked it from the beginning. And that's all fine. There are links to guides to the version of Unity in the two Ubuntu releases in my sig.

---

### Post by kristen2 on 2014-01-13
This has been really helpful. Thank you so much :) 
I burned 12.04 to a DVD and installed from there. When I insert my wifi USB, it is recognized by my computer and gives me available networks to connect to but won't connect...

---

### Post by carl4926 on 2014-01-13
> **kristen2 said:**
> This has been really helpful. Thank you so much :) 
I burned 12.04 to a DVD and installed from there. When I insert my wifi USB, it is recognized by my computer and gives me available networks to connect to but will not connect. What's the story about that? :/
The kernel
Particularly since kernel 3> has wireless improved, so your device is now working but...

Obviously you need to tell us if there is anything unique about the access point your are trying to connect to?
Is it a College Campus?
Is the AP control access by MAC address?

---

### Post by kristen2 on 2014-01-13
Huh? What about the kernel? 

I'm just trying to connect to my home network at the time being, if that's what you mean by access point. There shouldn't be anything unique about it

---

### Post by kristen2 on 2014-01-14
Why won't it connect and why does what the "access point" is matter??

---

### Post by carl4926 on 2014-01-14
Access Point, yes your home network.
Depends if the router has been configured to allow devices access by MAC address
Presumably you can see what you want to connect to and you enter the wireless password, but it's not connecting?

---

### Post by kristen2 on 2014-01-14
That's right. I can see networks and enter a password, but it doesn't connect. It just keeps trying

How is a MAC address relevant to me?

---

### Post by kristen2 on 2014-01-14
Is that a stupid question?

---

### Post by carl4926 on 2014-01-14
> **kristen2 said:**
> Is that a stupid question?
Not stupid
You obviously have no idea what I am talking about.
Who is the admin of your router?

---

### Post by kristen2 on 2014-01-14
No, lol, I have absolutely no idea what you're talking about.

The admin is not me, and it's someone who won't give me any information if I ask for it. I don't think it's the router, though... I think I'm not going to be able to get a connection anywhere I go. Maybe it's the router. I don't know. Is there something else that would be the problem if not the MAC address thing?

---

### Post by carl4926 on 2014-01-14
> [COLOR=#000000]it's someone who won't give me any information if I ask for it[/COLOR]That doesn't sound promising

If you can see access points your device is working

---

### Post by kristen2 on 2014-01-14
Ummmm.... Okay..... what did you do?? Lol. My wifi just suddenly connected... 2 hours later. It just now connected. I think you were wrong about the MAC address lol

---

### Post by kristen2 on 2014-01-14
It disconnected again. I took the USB out and inserted it back in and now I can't get a connection. I guess there isn't anything wrong? Something must just be slow

---

### Post by carl4926 on 2014-01-14
Could be this new wireless device is just not very compatible.
It helps if you buy devices that are known to work without issue
I guess you need to google the ID ifo you found earlier in this thread and look for solutions posted by others

---

### Post by kristen2 on 2014-01-14
Thank you for your help

---

### Post by carl4926 on 2014-01-14
[http://www.ubuntu.com/certification/catalog/category/WIRELESS/](http://www.ubuntu.com/certification/catalog/category/WIRELESS/)

---

