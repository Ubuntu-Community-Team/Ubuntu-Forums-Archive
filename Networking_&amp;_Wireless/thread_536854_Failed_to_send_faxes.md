---
title: "Failed to send faxes"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by iulian on 2007-08-28
Hi,

I try to send faxes using Efax-gtk but it fails:
```
Socket running on port 9900
efax-0.9a: 15:30:34 opened /dev/ttyS1
efax-0.9a: 15:30:34 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 15:30:34 failed page /home/iulian/test-fax.pdf.001
efax-0.9a: 15:30:34 Error: fax device write: Input/output error
efax-0.9a: 15:30:36 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 15:30:38 Error: fax device write: Input/output error
efax-0.9a: 15:30:40 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 15:30:40 sync: dropping DTR
efax-0.9a: 15:30:40 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 15:30:41 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 15:30:43 Error: fax device write: Input/output error
efax-0.9a: 15:30:45 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 15:30:45 Error: fax device write: Input/output error
efax-0.9a: 15:30:45 Error: fax device write: Input/output error
efax-0.9a: 15:30:45 sync: sending escapes
efax-0.9a: 15:30:45 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 15:30:45 Error: fax device write: Input/output error
efax-0.9a: 15:30:45 Error: fax device write: Input/output error
efax-0.9a: 15:30:46 Error: fax device write: Input/output error
efax-0.9a: 15:30:48 Error: fax device write: Input/output error
efax-0.9a: 15:30:50 Error: sync: modem not responding
efax-0.9a: 15:30:50 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 15:30:50 finished - unrecoverable error
```

You have idea why? How can I check if my modem is installed correctly? I have a Dell laptop, Inspiron 1300.

---

### Post by leonidas666 on 2007-08-31
Did you already check dialup-Modem-Howto ? see [https://help.ubuntu.com/community/DialupAndFax](https://help.ubuntu.com/community/DialupAndFax)

Do you have a external Modem? Because the input/output errors somehow look similar to the problem in this thread:
[http://ubuntuforums.org/showthread.php?t=504492](http://ubuntuforums.org/showthread.php?t=504492)

---

### Post by goofy_barney on 2008-04-01
Error: tcgetattr on fd=3 failed: Input/output error

The above is part of the error I received when using my external modem which is known to be working.  So of course my fax didn't transmit.

I changed my /etc/efax.rc file, specifically this line:

#DEV=ttyS1

to read:

DEV=ttyS0

That's a zero, not an uppercase o.
That fixed it for me.

It may not be your problem, but I'm sure many folks getting the same message have this problem.

Hope this helps someone.

Goofy_Barney

---

### Post by raypsi on 2008-05-09
I got my efax working took awhile to figure it out.
I had to set the fax to see the modem at ttyS0, It took forever to figure out where the modem was.

Then the file has to be postscript or .ps not pdf for some reason pdf wont work. Took forever again to find out how to make a .ps file. At the time open office was the only way to make any file to a .ps file. Now that I has hardy heron text editor makes ps files also.

It's really quirky how they do it. It's a print to file, you chose the file name and they converts it to a .ps file, and stores it where ever they like or your choice. So it has to be done under the print option. I have print to file, HP deskjet printer and PDF. Print to file, I have to choose the postscript option, because it defaults to PDF

Then you have to get efax to go to that .ps file and go from there.

---

