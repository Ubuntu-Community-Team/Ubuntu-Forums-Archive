---
title: "got my dad to use linux. printer issue."
date: 2009-07-12
forum: New to Ubuntu
---

### Post by darksidedude on 2009-07-12
hey. we have a new linux user, my father. his computer griped with windows rot was faced with 2 options. a complete wipe of windows with the promase this will happen again in 2 years. or linux. going on his faith in me he opted for linux. ubuntu 9.04 to be exact. :p

just one issue. 

Lexmark x4270 the z42 driver is somewhat functional. but not good enough for my dad. here is what it does. it will print 1 page of a 4 page document and no more. this is frustrating I want to show him there is more to computers than just windows xp. 

if anyone can help it would be appreciated.

---

### Post by nynoah on 2009-07-12
Blame Lexmark............ they are a bunch of jerks who will not release drivers to us.  To my knowledge no one has been able to get lexmark to work on any linux distro.  Only way I know to make it work is to install windows in virtual box.  Or the best option....... sell your lexmark on Craigs list and buy an HP.

---

### Post by darksidedude on 2009-07-12
My Dad loves that printer unfortunately. won't buy anything until its broken. another angle would be is this thing a postscript printer? if it is does anyone have a PPD for it?

---

### Post by jerome1232 on 2009-07-12
> **nynoah said:**
> buy an HP.

Agreed, epson is also well supported, but I don't think you can buy an hp that won't work in linux.

---

### Post by darksidedude on 2009-07-12
I usually like the ubuntu forums people. but your not trying to do anything but say. lost cause buy something else. maybe in la la land the economy is ok. not here I don't have the money for a new printer. only other printer is A dell AIO i seriously doubt that will work at all

---

### Post by theozzlives on 2009-07-12
Uhum, when I had my Lexmark z600... I got it working fine. Granted it was a pain in the patooty, but it worked. All I can say is Google "lexmark+x4270+ubuntu+9.04" (without the quotes).

---

### Post by nynoah on 2009-07-12
We are being realistic.  Search the forums.  I just did for how to make Lexmark work a few days ago.  Common consensus is there is no way.  At one time Lexmark had some drivers (that were HORRIBLE).  They gave up and have not released any linux drivers in over 2 years now.  We are not being mean......... just being honest.

---

### Post by twright on 2009-07-12
Hi,
it seams some other people have been having similar problems:
[http://ubuntuforums.org/showthread.php?t=338811](http://ubuntuforums.org/showthread.php?t=338811)

If you cannot find anything useful in that thread I can only suggest you re-approach the subject of a new printer - considering how expensive lexmark cartridges are it would practically pay for itself!
(edit: quite a few posts came in while I was typing so just ignore this last bit...)

---

### Post by LowSky on 2009-07-12
[http://localhost:631/](http://localhost:631/)
go there add your printer, lexmark z42 driver (right?)


it should then work, as good as a horible lexmark product can.

OR

Take sledgehammer or other heavy tool and introduce it to the lexmark at a high velocity, and then claim it was an accident, and buy a device that actually supports more than just Windows.


OR

sell it on eBay and use the cash toward a nice new working printer

---

### Post by jerome1232 on 2009-07-12
@theozzlives

Did you use a Linux driver or Windows driver + ndiswrapper?

You might be able to download a windows driver, extract the .inf driver file out of it and use ndiswrapper to use the windows driver under linux, only way I see it maybe happening.

---

### Post by twright on 2009-07-12
> **LowSky said:**
> 
OR

Take sledgehammer or other heavy tool and introduce it to the lexmark at a high velocity, and then claim it was an accident, and buy a device that actually supports more than just Windows.
I didn't see espionage/sabotage training listed on the Ubuntu system requirements page... anyway others have got it working so not all hope is lost.

---

### Post by theozzlives on 2009-07-12
> **jerome1232 said:**
> @theozzlives

Did you use a Linux driver or Windows driver + ndiswrapper?

You might be able to download a windows driver, extract the .inf driver file out of it and use ndiswrapper to use the windows driver under linux, only way I see it maybe happening.

If I remember right I had to extract a tar.gz to get the .RPMs (there were 2), use alien to convert them to .DEB, and install both of them. Rough stuff considering I was a total Linux noob and didn't have a clue as to what I was doing.

---

### Post by nynoah on 2009-07-12
Which was how long ago that you had to go through the convolution of using alien and what not?

---

### Post by theozzlives on 2009-07-12
> **nynoah said:**
> Which was how long ago that you had to go through the convolution of using alien and what not?

Way before I got my Linux+

---

### Post by nynoah on 2009-07-12
That was the method that I alluded to that was 2 years old.  I doubt if that still works with Ubuntu 9.04.  I could be wrong. But I would not think a file from that long ago would work correctly.

---

### Post by twright on 2009-07-12
> **nynoah said:**
> That was the method that I alluded to that was 2 years old.  I doubt if that still works with Ubuntu 9.04.  I could be wrong. But I would not think a file from that long ago would work correctly.
No reason why it shouldn't - for alien to work on RPMs they need to be LSB compliant and the driver will just be basic postscript :-)

---

### Post by nynoah on 2009-07-12
Well it may work.  But I bet the printer is newer than 2 years.  So it is no guarantee.  I should have been more specific.

---

### Post by halitech on 2009-07-12
not sure how close the x4270 is to the x4250 but you could try the drivers listed here and see if it helps

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-X4250](http://openprinting.org/show_printer.cgi?recnum=Lexmark-X4250)

```
Lexmark X4250
Color inkjet printer, works Mostly
```
as opposed to this
```
Lexmark x4270
Color inkjet printer, max. 4800 x1200 dpi, works Partially
```

---

