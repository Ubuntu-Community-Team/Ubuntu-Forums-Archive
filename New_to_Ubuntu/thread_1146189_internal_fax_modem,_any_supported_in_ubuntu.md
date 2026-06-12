---
title: "internal fax modem, any supported in ubuntu?"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by gandaran on 2009-05-02
I need to buy a fax modem, which model and make should I buy that will work in ubuntu?
thanks.

---

### Post by jimmy the saint on 2009-05-02
I would recommend getting an external serial harware modem.  Much less of a hassle, as it should just work.  There are some internal modems that work as well but a) they are harder to find, b) it is such a small percentage that it is easier to mistakenly buy one that wont, and c) even some that will work require headache causing work.  I bough a zoom brand modem for 60 bucks at office depot for my grandmother's computer last year.  Worked like charm.  Just make sure that it does not way winmodem, softmodem or anything else.  It should also indicate support for linux (but not all do).

---

### Post by llamabr on 2009-05-02
add my support to an external zoom modem.  I used to use one back in college, and it just worked.  I'm sure it's still the same case.

With the internal ones, you have to be careful, because they'll put different things in the same box, and you won't know what you have until you plug it in.

---

### Post by ddnev45 on 2009-05-02
A shameless plug for US Robotics, but I know both will work in many distros of Linux:

[Internal Performance Pro]("http://www.usr.com/support/product-template.asp?prod=5610a")

[External]("http://www.usr.com/products/modem/modem-product.asp?sku=USR5686E")

As long as you stay away from Winmodems, softmodems and USB modems you should be ok -- I think Zoom also makes an internal modem compatable with Linux.

I'd also go with an external, but your computer will need a serial port.

---

### Post by lkraemer on 2009-05-03
If you don't have a serial port, or want to use a USB port check out
the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a N82E16812156008
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $8.99.

They will be /dev/ttyAMC0 or /dev/ttyUSB0, etc....

These work wonderful with wvdial, KPPP, Gnome-PPP, etc.
wvdial will find the correct /dev/ttyxxxy

lkraemer

---

### Post by AlexanderDGreat on 2009-11-12
So what fax program is good for Ubuntu? Is there a program that emails the fax to you?

---

