---
title: "Ubuntu Feisty | Apple Airport Extreme with HDD NAS"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by supermonkey on 2007-05-20
Hi all

Just installed Ubuntu and am a n00b to all this. I have one of the new Airport Extreme routers, to which I have connected a USB external hard drive. In Windows, I just used the CD to install AirDisk or something and it auto mounted the hard drive on log-on and I can browse on a home network or integrated into Windows Explorer.

So I have two questions. One, how do I see the hard drive for browsing in the first place? I don't know how to browse the network workgroup in Ubuntu - I just connected to my network and entered my WEP key but I can't see the other devices on the network :( Second, once I can do that, is there any way to auto mount the networked HDD on log on?

Thanks for your help!

---

### Post by supermonkey on 2007-05-20
Just some further info... I have found the Places / Network and I can see my PC name and "My-Airport". I can browse "My-Airport" but there are no files there. Maybe someone has written a program that emulates Airport Disk? Or Airport Disk will work under WINE?

---

### Post by fireslack on 2007-06-17
I have  the same problem.  I have an AirPort Extreme Base Station 802.11n, a 20' iMac, a Dell Inspiron 6000, and a PC that I built a few years back that now has Ubuntu installed.  I have an AirPort Disk connected to the AEBS and I can access it in Windows XP and OSX, but I cannot access it in Ubuntu.  AN AirPort Disk Utility for Ubuntu would be great, but I'd settle for a workaround.

---

### Post by antonyw on 2007-06-19
[http://ubuntuforums.org/showthread.php?t=393034](http://ubuntuforums.org/showthread.php?t=393034)

This is a previous post that deals with this.  I have the same problem and will be trying to resolve it tonight after work.

Hope this helps.

---

### Post by twocargar on 2007-09-03
Just curious if anyone has tried the Avahi Zeroconf Browser for this.  I installed it and it immediately saw my Mac OS X Server and my other Mac on my network and prompted me to login to both.  I realize your AirDisk *should* show up on your network via Samba, but hey, give it a whirl.  Let me know if that works for you.

-TCG

---

### Post by MJ Britt on 2008-03-09
Hello all,

I have had very good luck in the forums resolving my issues..... This one is killing me.

Zeroconf and Avahi can not see the Apple Extreme Disk or printer I have attached. It is just my linux boxes not seeing the drives or printer.

This is what I've done:
Installed Avahi, reinstalled Zeroconf, installed every SMB program I can find, tried creating a link to the IP and name of the Airport, and the list goes on........

If anyone can help, I would name my next son/daughter after them. :)

---

### Post by Eiríkr on 2008-03-09
For those of you using your basic Ubuntu install with the default Nautilus browser -- Konqueror includes [font=courier]zeroconf:/[/font] protocol support.  Just typing this into the Konq address bar should show all Zeroconf-enabled devices that are actively broadcasting on your network.  If you do not have the full KDE install, the packages you'd need are Konqueror and kdnssd.  

Also note that, while pretty much all printers for the past few years have shipped with some kind of Zeroconf support by default, they don't all broadcast.  I have a Dell multifunction that doesn't broadcast, for instance.  If any of you out there have network printers, where the printers themselves have their own IP addresses, try setting up CUPS (accessible by typing in [font=courier]localhost:631[/font] in a browser) to use your printer.  I'm just adding mine again after a fresh re-install, and the basic setup is:
[list=1][*]Access [font=courier]localhost:631[/font] in browser
[*]Click "Add Printer"
[*]Type in printer name, click "Continue"
[*]Select printer from the "Device" dropdown, click "Continue"
[*]Copy the .ppd file from my printer driver CD to local Ubuntu hard disk
[*]Provide CUPS with the path to that file, click "Add Printer"
[*]Enter username and login, click "OK"
[*]Set up basic printer options (toner save, default paper size, etc.)[/list]

If your printer is network-enabled but doesn't show up in the list, do this instead:
[list=1][*]Access [font=courier]localhost:631[/font] in my browser
[*]Click "Add Printer"
[*]Type in printer name, click "Continue"
[*]Select "Internet Printing Protocol (http)" from the "Device" dropdown, click "Continue"
[*]Enter URL [font=courier]http://IP.ADD.RES.S:631/ipp/[/font] (replacing capital letters with the numbers of your printers IP address), click "Continue"
[*]Copy the .ppd file from my printer driver CD to local Ubuntu hard disk
[*]Provide CUPS with the path to that file, click "Add Printer"
[*]If desired, click the printer name, then "Set Printer Options" to set options[/list]

Hope this helps folks with their network printers.  :)

Cheers,

Eiríkr

---

