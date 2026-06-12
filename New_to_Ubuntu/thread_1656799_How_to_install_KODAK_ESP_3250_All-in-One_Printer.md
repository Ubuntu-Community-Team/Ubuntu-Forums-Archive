---
title: "How to install KODAK ESP 3250 All-in-One Printer"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by Runckle on 2010-12-31
How to install KODAK ESP 3250 All-in-One Printer HELP!

---

### Post by Runckle on 2010-12-31
Craps!

---

### Post by Autodave on 2010-12-31
> **Runckle said:**
> How to install KODAK ESP 3250 All-in-One Printer HELP!


Have you tried simply hooking up the cable and seeing if Ubuntu recognizes the printer?  I have never had to do anything but plug the USB cable in and all my printers have been recognised instantly.

---

### Post by bkratz on 2010-12-31
Although specifically about a different printer this pretty much sums up Kodak.

[http://ubuntuforums.org/showpost.php?p=6499873&postcount=3](http://ubuntuforums.org/showpost.php?p=6499873&postcount=3)

---

### Post by Runckle on 2010-12-31
Kodak ain't interested. So I ain't interested in Kodak!:lolflag:

---

### Post by MartyBuntu on 2010-12-31
> **Runckle said:**
> Kodak ain't interested. So I ain't interested in Kodak!:lolflag:


Uhhh...*you* started the thread, remember?

---

### Post by bkratz on 2010-12-31
> **MartyBuntu said:**
> Uhhh...*you* started the thread, remember?

If you read the link you will see what he means!

---

### Post by Runckle on 2011-01-06
Decided to have one more crack at this. Someone in a previous thread I know not which one said he used Virtualbox to get it to work. Anyone have any Ideas if this is possible and how?):P

---

### Post by JKyleOKC on 2011-01-06
> **Runckle said:**
> Decided to have one more crack at this. Someone in a previous thread I know not which one said he used Virtualbox to get it to work. Anyone have any Ideas if this is possible and how?):PIf he used vbox to make it work, that means that he installed Windows in vbox, and then installed the printer in that Windows system, to be shared with others. Once this is done, you can use the "vboxtools" package to automatically run that vbox VM in background whenever you boot, and can install the "Windows shared" printer in your Ubuntu host where it will work just as if it had been installed direct into Ubuntu itself.

You do this through the CUPS interface; browse to [http://localhost:631](http://localhost:631) to get to CUPS, than add the printer. The first screen of the "add" process gives a list of possible places to find the printer, and "Windows shared" is at the bottom of that list. From there, follow the prompts and use "browse" when uncertain what to fill into a text box...

I had to do this for one of my printers; although it had a Linux driver (unlike Kodak), there was a USB conflict between my VMs (required so that I can support Win-only customers) and the host that made the Linux driver lock up in mid-job. By setting it up so that the Linux host accessed the printer as a "Windows share" rather than directly, the problem went away. Performance doesn't seem to be hurt by the change, either.

You'll need to have the Windows VM and the host system on the same network connections for this to work.

---

### Post by Runckle on 2011-01-06
> **JKyleOKC said:**
> 
You'll need to have the Windows VM and the host system on the same network connections for this to work.


Thanks Jim. I'll get on this right now. Cheers!

---

### Post by cjazz on 2011-01-06
Have you given [this]("http://sourceforge.net/projects/cupsdriverkodak/") a try? I have no idea if it works.

---

### Post by Runckle on 2011-01-07
Thanks for the help Cjazz but it doesn't seem to work for x64bit. I spent several hours on this last night looking for the correct cups driver that simply eludes us x64 bitters...

---

### Post by paulnewall on 2011-01-29
This may help with 64 bit
[https://sourceforge.net/projects/cupsdriverkodak/forums/forum/1107085/topic/3821012](https://sourceforge.net/projects/cupsdriverkodak/forums/forum/1107085/topic/3821012)

---

### Post by lproven on 2011-08-03
For 64-bit, you have to download and unpack the tarball (the file ending .tgz) and carefully follow the instructions in the README and INSTALL file. You need to compile the driver (with the command "make") and then install it (with the command "make install") and then it works fine - I am using it right now. 

Took me 5min but it's not complicated. If you're a complete newbie, though, I am afraid this is not the printer for you if you use only Linux.

The driver is print-only, doesn't scan, and it doesn't support choosing paper trays. Colour may be erratic but I only need B&W, which it does fine.

Ask or mail me if you need more guidance but I suspect it's too late now.

---

### Post by paulnewall on 2011-10-08
There is a driver here
[https://sourceforge.net/projects/cupsdriverkodak/](https://sourceforge.net/projects/cupsdriverkodak/)

---

### Post by OhioRon on 2011-10-11
This Form is Great been looking to use my kodak printer and could never find the correct driver,
Worked like a charm.
Thanks everyone:popcorn:

---

### Post by gmemo2 on 2011-10-13
driver worked like a treat thanks all.
:D

---

### Post by paulnewall on 2011-10-21
does anyone have experience of the kodak esp printer driver included in the ubuntu 11.10 release working?

---

### Post by satanselbow on 2011-10-21
Yep! Installed as a wifi printer out of the box under Gnome3 :popcorn:

ESP 5250 for the record ;)

---

