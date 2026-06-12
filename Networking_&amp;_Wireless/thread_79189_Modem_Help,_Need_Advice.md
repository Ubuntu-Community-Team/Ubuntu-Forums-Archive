---
title: "Modem Help, Need Advice"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by gamerchick02 on 2005-10-19
Hi all,

I'm new to this.  Just installed Breezy Badger on my computer and am trying to get a USB modem to work.

Here are my specs about my machine:
Stock Dell 2400
512 MB RAM

I bought a Creative Blaster V.92 dial-up modem, USB external.  The model number is DE5671.

I have spent approximatly two hours Google-ing without any useful results.

Results of lsusb are:

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 148d:1671
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I am also willing to buy a new modem if this doesn't work.  I have no choice but a dial-up connection.

What dial-up modems have you had luck with?

Can anybody help me with getting this to work?

Thank you very much in advance,

Amy

---

### Post by migueljacq on 2005-10-19
[QUOTE=rpgirl]Hi all,

I'm new to this.  Just installed Breezy Badger on my computer and am trying to get a USB modem to work.

Here are my specs about my machine:
Stock Dell 2400
512 MB RAM

I bought a Creative Blaster V.92 dial-up modem, USB external.  The model number is DE5671.

I have spent approximatly two hours Google-ing without any useful results.

Results of lsusb are:

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 148d:1671
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I am also willing to buy a new modem if this doesn't work.  I have no choice but a dial-up connection.

What dial-up modems have you had luck with?

Can anybody help me with getting this to work?

Thank you very much in advance,

Amy[/QUOTE]

Hi Amy,

What is your problem exactly? Is it that you can't find the modem to be detected on your computer, or is it that it is detected but won't dial?
I'm not sure about USB modems, I run an external SwannSmart 56K through a COM port (ttyS0).
If it is simply the configuration (i.e getting it to dial), I might be able to help

Miguel

---

### Post by elebrin on 2005-10-20
The modem is not being recognised (I was there helping install Ubuntu).

we are, by the way, running Breezy instead of hoary if that makes any difference.

When you use the modem configuration tool it cannot autodetect the correct port, and as a USB device picking a COM port as such does not make sense (because it isn't connected to one).

So, we are a bit stuck.

---

### Post by gamerchick02 on 2005-10-20
Elebrin said it right.

I looked at the device manager (or whatever it's called in ubuntu) and saw that it was detected by the computer as a USB device.  It even said it was a Creative Blaster V.92 modem and everything.

I have it working in Windows.  (If that is any consolation.)

So, the computer can see it, but it's not detected as far as drivers are concerned.  I can't get it to dial either.

I dunno if that helps.

Amy

---

### Post by migueljacq on 2005-10-20
[QUOTE=rpgirl]Elebrin said it right.

I looked at the device manager (or whatever it's called in ubuntu) and saw that it was detected by the computer as a USB device.  It even said it was a Creative Blaster V.92 modem and everything.

I have it working in Windows.  (If that is any consolation.)

So, the computer can see it, but it's not detected as far as drivers are concerned.  I can't get it to dial either.

I dunno if that helps.

Amy[/QUOTE]

Yep - unfortunately I don't know much about USB modems in Linux.
Have you run sudo pppconfig, and configured the modem? Because one of the steps in pppconfig is to determine the port that the modem is on. You might be able to select the USB port, not sure. There's even an autodetect option, which might work for you since you said your machine already knows it's there. Hopefully, because then that would make it a lot easier

---

### Post by gamerchick02 on 2005-10-20
I will try sudo pppconfig.

I tried the autoconfig option, but it didn't find anything.  I think it looks at the serial ports and not the USB ports.

I just type sudo pppconfig in the terminal window, right?

Sorry for sounding kinda dumb, but I don't have a lot of experience with this type of thing.

Amy

---

### Post by migueljacq on 2005-10-20
[QUOTE=rpgirl]I will try sudo pppconfig.

I tried the autoconfig option, but it didn't find anything.  I think it looks at the serial ports and not the USB ports.

I just type sudo pppconfig in the terminal window, right?

Sorry for sounding kinda dumb, but I don't have a lot of experience with this type of thing.

Amy[/QUOTE]

No that's okay don't be sorry, that's what forums are for.

I think this will help you do the pppconfig: I wrote the steps in this thread:

[http://ubuntuforums.org/showthread.php?p=419217](http://ubuntuforums.org/showthread.php?p=419217)

Hopefully the pppconfig helps but like I said, I don't know much about USB modems. I know that if it is a winmodem, you're gonna have trouble with it in linux

EDIT: oops - in answer to your question, yes, type in the terminal 'sudo pppconfig' :)

---

### Post by gamerchick02 on 2005-10-20
Thank you for the help.  

I did figure out that I needed to type sudo pppconfig.  I put in what I thought made the most sense (ie what I recognised!) but still no luck.

At one time I did get a status bar thing, but it didn't connect.

I don't even hear the modem dial.

I can't choose the USB ports for the modem hookup.  The only thing I can choose is a serial port.

It's confusing that it sees the modem.  The only thing I think I can do is see if there are drivers for the modem written for linux.  Off to Google I go!

Amy

---

### Post by pkoebbe on 2005-10-21
By no means am I an expert in this jungle, but you never know when tidbits here and there will be useful.

First, on the topic of a different modem:  The serial version of the ModemBlaster is controller based and needs no drivers.  I ordered one from [www.TechForLess.com](www.TechForLess.com) for $8 (+$7 shipping) and it arrived in two days!  Beats the $60 that Best Buy wants for the same thing.  Anyway, if you have a serial port it will work just fine.  I'm still trying to get it to work via a USB-to-Serial adapter, though I've heard some people have had luck with it.

Regarding not being able to select USB ports when trying to detect your modem:  I have been using KPPP to try to see my modems (as I've been trying this one and that one), and I discovered last night that when you do the "query modem" option, it only looks to /dev/modem.  I was selecting the different ports on the other tab then switching over and doing the query thinking it was looking at whichever port I selected (like ttyS0), but it wasn't.  As soon as I created a symbolink link, it worked just fine.  So you might try doing

```

$ sudo ln -s /dev/ttyUSB0 /dev/modem

```

and fill in whatever port your modem is on in place of ttyUSB0.  Then try the auto find thing again.  It may help, it may not.

That's all I have.  If anyone has any thoughts regarding USB-serial, please post.

Peace, 
Phillip

---

### Post by gamerchick02 on 2005-10-21
Ok.

First I ran sudo lsusb again to get the information about where my USB modem was hooked up.  It showed information for all of the ports, but only two were being used, one for the optical mouse, and the other for the modem (I presume):

Bus 001 Device 003  ID148d:1671

Next, I tried the sudo ln -s /dev/ttyUSB0 /dev/modem and replaced the USB0 with usb3.  I tried again with usb003.

All it showed was:

/dev/modem: File exists.

I know that the file exists.

Am I missing something?

Amy

---

### Post by pkoebbe on 2005-10-21
Apparently, you already had a /dev/modem.  Do

$ ls -l /dev/modem

and it will show you what it is pointing to.  For example, the output might include

modem -> ttyS0

If modem is pointing where you don't want it, you can remove the link with

$ sudo rm /dev/modem

and then do the link again

$ sudo ln -s /dev/{your device here} /dev/modem

Also, another way to find out where your device is on the USB bus is to monitor /var/log/messages when you plug the device in.  You do that by opening another terminal window and entering

$ tail -f /var/log/messages

then plug your device in and watch the console window for clues.  Sometimes you will get them, sometimes you won't (depending on the device and driver that it uses).  When you're done with the tail output, CTRL-C stops it.

Unfortunately, I've just about tapped my knowledge of modems/busses/symbolic links.  The only other tidbit I can offer is this:  if /dev/modem either gets deleted or remapped when you reboot, it might be because of an entry in /etc/udev/udev.rules.  If this happens to you, post again and we'll deal with that separately.

Peace
Phillip

---

### Post by Matchless on 2005-10-21
Hi,
    I am not familiar with USB modems, but think they are in the same class as the internal winmodems, someone can correct me if wrong. I have had quite a bit of experience trying to get an internal modem to work and I can tell you it is not really worth the effort as in most cases its unstable and suddenly fails for no reason, locks up and needs the PC rebooted etc.
The best solution is to get an external serial modem, they work well and can easily be set up without the need for drivers and will use the "Com 1 to 4" port as /dev/tty0 etc. Use the Query Modem function in Kppp and it shows the modem and gives the details on the modem. The dev/modem is normally part of the symbolic link for internal (and USB) modems, I think.
If you want to challenge yourself, by compiling your own driver, give me a PM and I will send you some details to help you on the way, but believe me a serial modem will save you a lot of trouble.

---

### Post by gamerchick02 on 2005-10-21
Ok.

I have successfully unlinked the device the device file /dev/modem.  I cannot find the device for the USB modem and the information provided by tail -f /var/log/messages was not really helpful, since it just told me the same things that lsusb told me, just in a different format.

I need to know how to create the device file for it with mknod or how to find the device file.

(There are a bunch of devices called ttyuX [where X is a number 1-5].  I thought these might be my USB devices, but when I tried to link them to /dev/modem, it didn't recognise them and couldn't dial.)

Thanks for any help you can provide, and for the help already provided.  I really appreciate it!

Amy

---

### Post by migueljacq on 2005-10-21
I'm not normally an advocate of 'giving up', but I have to agree with Matchless. After browsing around the forum a bit, almost everyone with usbmodems and winmodems have trouble. I remember you saying you were willing to return your modem and get something different. Go for a serial modem, at least you know it will be stable and we've covered the setup here already so you know how to do the config.
All the same I'm wondering if troubles with usb modems etc are an incompatability issue with just Ubuntu or is it the linux system itself, across all boards.

---

### Post by gamerchick02 on 2005-10-22
That sounds like a good idea.  I don't really want to give up, but it seems like the best option in this instance.  Thanks to everybody for all their help.

Amy

---

### Post by gamerchick02 on 2005-10-22
Thank you to everybody who helped me.

I went out and returned the USB modem and bought a serial modem.  It worked with the autodetect feature with the modem properties in networking.

I'm getting good page display times with it (it's a creative serial modem).

Again, thanks for the help.  It's much easier to fiddle with things when you have internet access so you can check the forums and other resources online.

Maybe I should look into DSL.  :)

Amy

---

### Post by migueljacq on 2005-10-22
Glad to hear :-) 
I tried to get DSL but I'm too far away from the exchange :-( stuck on dialup for now

---

