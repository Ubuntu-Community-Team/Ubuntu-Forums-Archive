---
title: "WUSB54GC w/ rt73usb driver no monitor mode in Ubuntu Gutsy 7.10, can't compile rt73"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by JoeLinux117 on 2007-10-26
I recently purchased a Linksys WUSB54GC wireless card (because it worked so well in Feisty).  I wanted to use it on my Gutsy machine for no other reason than to use monitor mode and packet injection (I am adamant about securing my wireless network, and I wanted to try and see if I could crack it).

I tried sticking it into monitor mode "iwconfig wlan1 mode monitor" or "airmon-ng start wlan1 channel 6", but no joy.  Also, I thought it was supposed to be "rausb0", not "wlan1"?  I'm guessing that this rt73usb driver does things a little differently.  Now, it also seems that BT2 is able to get this card working just fine.  So it's just Gutsy.

When I try to compile the rt73 driver myself, in order to get it working on Gutsy, I get this:

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/joe/Download/temp/rt73-k2wrlz-1.0.0/Module/rtusb_data.o
/home/joe/Download/temp/rt73-k2wrlz-1.0.0/Module/rtusb_data.c: In function ‘RTUSBRxPacket’:
/home/joe/Download/temp/rt73-k2wrlz-1.0.0/Module/rtusb_data.c:1971: error: ‘struct sk_buff’ has no member named ‘mac’
make[2]: *** [/home/joe/Download/temp/rt73-k2wrlz-1.0.0/Module/rtusb_data.o] Error 1
make[1]: *** [_module_/home/joe/Download/temp/rt73-k2wrlz-1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'
*** Module rt73.ko built successfully
```

Yes, it says that it built successfully, but it doesn't.  It gets an error "struct sk_buff has no member named mac", which I assume is in the block that specifically deals with monitor mode.  I tried commenting out that section (which is a dirty move in itself), and it compiled.  I tried using it, and I was able to get it into monitor mode, but couldn't use packet injection.  I would appreciate any help with this.

--JoeLinux

[Learn About Linux - A World Without Windows]("http://www.learnaboutlinux.net")

---

### Post by ctsdownloads on 2007-10-26
Assuming you are sure it is indeed, rt73usb in use here, try this, no compiling needed. ;)

First open terminal and paste:

> echo 'blacklist rt2500usb' | sudo tee -a /etc/modprobe.d/blacklist

Reboot, then try this in another terminal for testing:

> modprobe rt73usb

Should say nothing. Then paste:

> iwconfig

Making sure you are still using wlan1

Then paste:

> sudo ifconfig wlan1 down

then

> sudo ifconfig wlan1 up

So long as you*** do not*** get this output:

> SIOCSIFFLAGS: No buffer space available

you are good to go. Chances are huge that network-manager will not work for you, despite inroads with RaLink stuff, download the latest Wicd version (1.4 I think is their latest beta, do not use the main release). Install it and reboot, you should not need to do any modprobing at all or even compiling either.

This is working with two USB wifi devcies:

Edimax EW-7318Ug and  EW-7318USg
Going to Preferences, Hardware information shows both of them as using the rt2500usb driver, I suspect this is the same issue you are having, considering it should be using what we just made it use. :)


Also me running lsusb in the terminal only gave me a generic RaLink device, this is another point that means that we may be on the same page here.

Say what you will about using Wicd, but using my technique - it works. :)

With all of this said, if you have already made changes to the driver with your compiling, I cannot promise that this will work, of course.

---

### Post by JoeLinux117 on 2007-10-29
Hey ctsdownloads, thanks for the tip.  I had already blacklisted rt73usb, and everytime I inserted the WUSB54GC card, the compiled rt73 module came up (after I commented out that offending block).

However, I feel kinda stupid, because I actually managed to get it working by using the latest CVS snapshot (latest, on the same day as my first post).  I compiled that one, and it didn't error out like the previous one did.  Success!

I tested it, and I was able to successfully throw it into monitor mode, use packet injection, and I was able to crack a test 128-bit encrypted wireless network in just over 5 minutes.  Sweet!

Maybe I'll post a tutorial about this on my website in the future.  Thanks anyway!

--JoeLinux

[Learn About Linux - A World Without Windows]("http://www.learnaboutlinux.net")

---

### Post by syncmasta on 2007-11-02
I am facing the same problem as Joe did.... I blacklisted the rt2500 module as ctsdownload said and got these results. Please let me know where did I go wrong. 

> amir@Cypher:~/Downloads/rt73-k2wrlz-1.0.0/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/amir/Downloads/rt73-k2wrlz-1.0.0/Module/rtusb_data.o
/home/amir/Downloads/rt73-k2wrlz-1.0.0/Module/rtusb_data.c: In function ‘RTUSBRxPacket’:
/home/amir/Downloads/rt73-k2wrlz-1.0.0/Module/rtusb_data.c:1971: error: ‘struct sk_buff’ has no member named ‘mac’
make[2]: *** [/home/amir/Downloads/rt73-k2wrlz-1.0.0/Module/rtusb_data.o] Error 1
make[1]: *** [_module_/home/amir/Downloads/rt73-k2wrlz-1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
rt73.ko failed to build!
make: *** [module] Error 1

---

### Post by ctsdownloads on 2007-11-02
Cannot speak to those who tried to compile then use the driver in question. What I did was avoid needing to compile in the first place was the instructions as seen previously.  

With devices like the EdimaxEW-7318USg USB wifi device, there was no compiling needed.
In this instance, Gutsy was detecting this as rt2500usb but actually needed to allow rt71usb to step forward automatically. Then again, I do not use big box store wireless products by choice.

In you instance, I guess you can simply forget the compiling, looks like it did not take anyway, and try what i did previously to see if you have any luck. Select Edimax products are working very well in Gutsy, with Wicd of course and network-manager is a joke.

---

### Post by panchofmx on 2007-11-06
I cant wait to try ubuntu gutsy  on my USB Alfa AWUSO36s. i will need to use the module rt73usb.

Hoppe it work. :lolflag:

---

### Post by rodica.balasa on 2008-01-18
I managed to make it work using Edimax drivers, only on inconvinence: it is seen as a wired connection by network manager (using gutsy):

[http://www.len.ro/work/tools/old-new-i8000-2]("http://www.len.ro/work/tools/old-new-i8000-2")

---

