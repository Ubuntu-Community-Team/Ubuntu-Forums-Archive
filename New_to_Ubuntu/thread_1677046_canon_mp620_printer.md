---
title: "canon mp620 printer"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by malp on 2011-01-28
Hi
As i have mentioned before i am extremely new to ubuntu linux but i have followed the introduction document advised in my last post and i am really impressed with the desktop i have been able to change to. I was considering changing ubuntu to my first choice boot option until i tried to add my printer a canon mp620 all in one. there are no drivers for it but i have found a ppd which is 
ppdm620-630en-1.5
I used this and it installed but now complains of a missing file
pstocanonij
I have read other posts and forums about this and some i do not understand. please make it easy step by step as i do not understand the commands yet. Others mention getting files from canon australia which do not exist or mention connecting the printer wireless. I just want the printer to work over usb.
a computer without a scanner and printer is useless to me and i do want to use ubuntu.
please any suggestions
all the best
malc

---

### Post by anglican on 2011-01-28
> **malp said:**
> 
I used this and it installed but now complains of a missing file
pstocanonij
Try opening a terminal and typing:
```
mkdir canon
cd canon
wget http://de.software.canon-europe.com/files/soft31301/software/MP630_debian_drivers.tar
tar xvf MP630_debian_drivers.tar
wget http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.9_all.deb
sudo dpkg -i libcupsys2_1.3.9-17ubuntu3.9_all.deb
tar xvf MP630_debian_printer.tar
sudo dpkg -i cnijfilter-common_3.00-1_i386.deb         

```

Let us know how you get on.

H

---

### Post by fabricator4 on 2011-01-28
> **malp said:**
> Hi
boot option until i tried to add my printer a canon mp620 all in one. there are no drivers for it but i have found a ppd which is 
ppdm620-630en-1.5
I used this and it installed but now complains of a missing file
pstocanonij



Ah yes, Canon. The best technology - electronics, inks, innovative ideas...  and the absolute  worst approach to driver support on the planet.  They wouldn't make Windoze drivers available except they managed to figure out they wouldn't sell any product otherwise.

They've always been this way, since I've had anything to do with them - Prior to GUI's being the norm they actually expected the dealers and users themselves to sort out the driver issue - they saw themselves as solely suppliers of hardware - drivers were someone elses's problem. (Does anyone else remember the LBP-1 and Wordstar/Wordperfect ?

Times change, Canon does not.

The debian packages available on the Canon website do work. Just.  Follow the instructions for installing .deb packages and you will get a driver that just barely meets the minimum criteria for a printer driver.  If you want photo quality output under Linux, the Canon drivers may not (probably won't) do it.

There is however a good fix: [Turbo Print]("http://www.turboprint.info/printers.html") drivers.  They are not free, either as in "free speech" or "free beer", but they do work. The proprietary print manager allows a limited trial period after which it will stop working so you can well and truly test it before buying.

For the scanner, support is provided under Linux/Ubuntu by SANE and shouldn't be too troublesome especially if the scanner is TWAIN compliant.

The fax I have no knowledge or experience of. That's what email is for. ;-)

Chris.

---

### Post by malp on 2011-01-28
hi i tried typing the code you gave me into terminal and it seemed to go in ok but the printer still does not work. 
It goes through the motions but prints nothing. The system recognises that it switched on and if I choose a printer off of the canon list that is supplied with ubuntu such as the mp610 then the printer actualy changes status on its display to printing from pc but nothing comes out.
if i use the printer installed with the ppd mentioned above nothing happens at all.
The code you gave me runs but nothing is installed so thats why i tried the two versions of printer above after running the code.
Have you any other suggestions 
thanks
malc

---

### Post by anglican on 2011-01-28
> **malp said:**
> hi i tried typing the code you gave me into terminal and it seemed to go in ok but the printer still does not work. 
It goes through the motions but prints nothing. The system recognises that it switched on and if I choose a printer off of the canon list that is supplied with ubuntu such as the mp610 then the printer actualy changes status on its display to printing from pc but nothing comes out.
if i use the printer installed with the ppd mentioned above nothing happens at all.
The code you gave me runs but nothing is installed so thats why i tried the two versions of printer above after running the code.
Have you any other suggestions 
thanks
malcI'd also recommend that you try [turboprint]("http://www.turboprint.info/printers.html") there's a free 30 day trial so if it doesn't do what you want you lose nothing.

H

---

### Post by malp on 2011-01-28
hello again
Turbo Print indeed does the trick. Now I have 1 month to test it. 
thankyou all for your help

malc

ps now to try the scanner

---

### Post by cyncicle on 2011-02-08
I'll second that - Turbo Print seems to work perfectly.

SANE seems to work fine for scanning.

---

### Post by Opti_Rick on 2011-10-03
A third for Turbo Print.

I must have lost days trying to get my Canon ip3600 to print, followed all manner of instructions only to reach new hurdles.

Installed Turbo Print today and was printing in minutes. I wish i'd found it earlier, i'm still using it on trial but it  might be the best £30 I ever spend.

---

