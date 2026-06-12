---
title: "can not dial up with conexant HCF V90"
date: 2005-10-09
forum: Networking &amp; Wireless
---

### Post by tmtjjhnsn on 2005-10-09
I am a Newbie with a capital N.  I recently installed Ubuntu Linux in a dual-boot setup with no problem.  However, I can not dial up in firefox or the email app.  My Conexant HCF V90 56K RTAD Speakerphone PCI modem is listed in the devices in Device Manager, but the system can not auto-detect my modem.  I have tried pppconfig and pon, but no success.  I don't know if I have a driver problem or just a configuration problem.  Any help would be appreciated.
:confused:

---

### Post by mlomker on 2005-10-09
Drivers for Conexant modems do not come with Ubuntu.  [Linuxant]("http://www.linuxant.com/drivers/?PHPSESSID=cdf2f0f9701c37be0bb653e28226da3d") sells a full-speed driver for $15 and offers a 14.4 version as a free trial.

---

### Post by tmtjjhnsn on 2005-10-09
Okay, thank you for the info about Linuxant.  I had already downloaded drivers for my modem from Linuxant while in Firefox for Windows and saved the file to a floppy, but I have no idea how to get the drivers from the fat formatted floppy into Linux, or if that is even possible.  Help.  Thanks.

---

### Post by mlomker on 2005-10-09
> I have no idea how to get the drivers from the fat formatted floppy into Linux, or if that is even possible.

You can try this at a prompt.  

```

sudo mkdir /media/fd0
sudo mount -t vfat /dev/fd0 /media/fd0

```

---

### Post by tmtjjhnsn on 2005-10-09
Okay, great.  I will try that.  Thanks, mlomker.  I will keep you posted.  I have a dream that I will be able to surf the net and send/receive email in the Ubuntu Linux distro.  I am determined.  

t

---

### Post by landotter on 2005-10-10
FWIW, the Linuxant drivers are helplessly overpriced--but they do work absolutely flawlessy.

pppconfig is definitely the program to use to configure the modem once you install the drivers. Then you can use the gnome modem-lights applet to control your modem.

---

### Post by mlomker on 2005-10-10
> but they do work absolutely flawlessy.


It should.  I believe that their parent company is Conexant.  Conexant sells chips to motherboard manufacturers, which then go to HP/Dell/etc, and then to customers.

Conexant's argument is that they are so far removed from the end-user that they shouldn't be obligated to write a driver for free.  I agree with them.  The company to get upset with is the one that you bought the machine from--they are choosing to not fully support linux.

Given how much cheaper dial-up is than broadband...a one-time $15 charge is no big deal.

---

### Post by bruce3au on 2005-10-10
Hey tmtjjhnsn, dont give up , had same trouble here, took about 9 months and many trips to so called comp. experts, i finally found an external modem on our local rubbish tip which i took home and cleaned up , pluged it in and its never failed  me since, my advice is to just keep trying different brand names, borrow from ur  mates if u have to, the moden that worked for me is an Aopen, model FM56EX/2, linux seem a bit that way that what might work for one might not work for another, best of luck . but stick with an external.    Bruce3au

---

### Post by tmtjjhnsn on 2005-10-10
Thanks for the info on the external modem, Bruce.  I wonder if there is a list somewhere of modems that ship with drivers with Linux support.  I suppose I will end up using my existing modem with the Linuxant drivers, but I am not certain, yet.  Incidentally, my machine is a Dell.  I suspect that Dell would argue that it is not worth the expense of supporting Linux, when Linux users make up such a small minority of users.

t

---

### Post by mlomker on 2005-10-10
> I wonder if there is a list somewhere of modems that ship with drivers with Linux support.

Any external serial-port model will work because they don't require drivers.  It is the DSP-based soft-modems that are the problem under linux.  It's because they aren't actually modems...the software just programs a DSP to pretend that it is a modem.

---

### Post by Efwis on 2005-10-10
[QUOTE=tmtjjhnsn]Thanks for the info on the external modem, Bruce.  I wonder if there is a list somewhere of modems that ship with drivers with Linux support.  I suppose I will end up using my existing modem with the Linuxant drivers, but I am not certain, yet.  Incidentally, my machine is a Dell.  I suspect that Dell would argue that it is not worth the expense of supporting Linux, when Linux users make up such a small minority of users.

t[/QUOTE]
thats not quite true, Dell has started selling comps with Linux pre-installed in some European countries. Hopefully they will start doing that in America too, that would help Linux out a lot IMO.

There is a list of modems that support Linux,

the following links are from [Winmodems are not modems](http://free.hostdepartment.com/g/gromitkc/winmodem.html)

[PCI list](http://free.hostdepartment.com/g/gromitkc/pci_list.html)
[ISA list](http://free.hostdepartment.com/g/gromitkc/isa_list.html)
[External list](http://free.hostdepartment.com/g/gromitkc/extlist.html)
[USB modem list](http://free.hostdepartment.com/g/gromitkc/usblist.html)
[pcmcia list](http://free.hostdepartment.com/g/gromitkc/pcmcia_list.html)

hope this helps.

---

### Post by tmtjjhnsn on 2005-10-10
I hadn't thought of that, mlomker.  Do you mean a modem that plugs into a COM port?  Not a serial bus (USB) modem, right?  I haven't seen a serial port modem in years.

t

---

### Post by mcrofutt on 2005-10-10
eBay might be your best friend and best bet when looking for an external modem. I bought 2 for like $10 USD. Good luck dude!

---

### Post by mlomker on 2005-10-10
> Do you mean a modem that plugs into a COM port?

Sure, like mcrofutt said...modems haven't changed in many years.  An older USR 56k modem could probably be had for a song.  I bet a USB modem would also work, though...I have a USB serial port adapter that works fine under Ubuntu.  It's the modems built into laptops (and the inexpensive PCI cards for desktops) that require software drivers.

---

