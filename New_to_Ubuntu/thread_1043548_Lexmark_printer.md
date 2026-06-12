---
title: "Lexmark printer"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by aagavin on 2009-01-18
I am using Ubuntu 8.04 and I can't get my Lexmark X6170 printer working

When I plugin the USB it nothing happens

how do i get my printer to work

---

### Post by mike555 on 2009-01-18
[http://blog.k33bz.com/how-i-got-my-lexmark-x6170-working-on-ubuntu-804/](http://blog.k33bz.com/how-i-got-my-lexmark-x6170-working-on-ubuntu-804/)

---

### Post by aagavin on 2009-01-18
> **mike555 said:**
> [http://blog.k33bz.com/how-i-got-my-lexmark-x6170-working-on-ubuntu-804/](http://blog.k33bz.com/how-i-got-my-lexmark-x6170-working-on-ubuntu-804/)

ok I was tring that but when i type in the 

[PHP]sudo alien -t lexmarkz55-CUPS-1.0-1.i386.rpm[/PHP]

command it gives me this error:
> 
Warning: Skipping conversion of scripts in package lexmarkz55-CUPS: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
lexmarkz55-CUPS-1.0.tgz generated


---

### Post by diablo75 on 2009-01-18
All I can say is, from experience... you'll probably not get that thing to work right.  Lexmarks have poor linux support.  I arm wrestled with one for a week and got it to work half way...text would print, pictures wouldn't.  HP's on the other hand usually rock your socks in an snap with no pain.  If you're serious about using Linux, you might want to consider exchanging your lexmark for a different printer.

---

### Post by aagavin on 2009-01-18
alright thanks, the Ubuntu should do something about the lack of support, mabey then can write there own drivers or something...

---

### Post by beezap on 2009-02-23
If all you want is for the printing to work, then that's not a problem.  See post how to install x6170.

---

### Post by NewJack on 2009-02-23
> **aagavin said:**
> alright thanks, the Ubuntu should do something about the lack of support, mabey then can write there own drivers or something...

It is not Ubuntu or Linux's fault.  It is the Manufacturer (In this case, Lexmark) who fails to produce drivers.  HP and Epson provide excellent Linux driver support FYI.

Anyway, here is the listing for your printer on the OpenPrinting.org website:

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-X6170](http://openprinting.org/show_printer.cgi?recnum=Lexmark-X6170)

It states that printing works, but scanning isn't supported with the Z55 driver.  The author states that the driver is available for Linux on Lexmark's site.

Good Luck!

---

### Post by BDNiner on 2009-02-23
Yeah, good luck with the Lexmark. I have ordered a brother MFD to replace my Lexmark. It is connected to my windows machine and I could never get it to work at all with my ubuntu computer.

---

