---
title: "Installing old printer driver Canon LBP 800"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Plus+ on 2009-01-11
I got this old computer connected to Windows network and the only printer in the room, Canon LBP 800.

I installed recent Ubuntu release 8.10, Kernel 2.6.27-9 generic

It detects the printer via smb protocol but the only driver I could locate for it comes from

[http://www.veneto.com/lbp800/lbp800.html](http://www.veneto.com/lbp800/lbp800.html)

When I try to install it gives a whole bunch of errors starting with:

karen@karen-desktop:~/lbp800-0.1.2$ sudo make
[sudo] password for karen: 
gcc  -O2 -s -Wall \
	errcapt.c bmcapt.c lbp800.c \
	-l cups -o bin/Release/lbp800
bmcapt.c: In function ‘Bitmap_Skip’:
bmcapt.c:50: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
bmcapt.c:53: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result

and then it goes on and on

>>>

I've been on any LInux platform for only few hours, I believe there are problems with my environment - "cups" package is apparently not doing its job, but have no idea what it is or how to fix it. Do I need some sort of -dev package to compile this non-standard driver? Should I move it to some "executable" place and "make" it there? Should I change permissions or something?

What am I doing wrong?

Thanks in advance.

Plus+

---

### Post by RobsterUK on 2009-01-12
I think you may well have got uneccessarily technical on this one.

Try this:
Click on System > Administration > Printing

Click New to add a new printer. If its not detected automatically you'll get to a screen where you have to select the model, there is an option "Search for a printer driver to download" where typing Canon LBP 800 should get what you need

Hope this helps

---

### Post by Plus+ on 2009-01-13
>>>"Search for a printer driver to download"

I tried that first.

The button grays out for a minute or two and than comes back to the original state with no results in the drop down menu below.

Installing that driver manually seems to be the only option, there's no .deb for it.

---

### Post by itsols on 2010-06-27
Hi,

Your post is a little old but I'd like to know if you've got around the problem.

I have an old lbp-800 printer but never got it working on the LAN. So I'd like to see if you have any solution to YOUR problem as at now.

In case you're interested in reading my printer experience on Ubuntu, I've posted it on my site since it's not relevant here. The link to it is: [http://www.marhaonline.com/empress/?p=16](http://www.marhaonline.com/empress/?p=16)

Happy Computing!

---

### Post by Sixberlyx on 2010-11-25
Hi,

@Plus+,

> When I try to install it gives a whole bunch of errors starting with:

karen@karen-desktop:~/lbp800-0.1.2$ sudo make
[sudo] password for karen: 
gcc  -O2 -s -Wall \
    errcapt.c bmcapt.c lbp800.c \
    -l cups -o bin/Release/lbp800
bmcapt.c: In function ‘Bitmap_Skip’:
bmcapt.c:50: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
bmcapt.c:53: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
This kind of error is due to the version of gcc you use to compile the driver with the "make" command.
You must use an earlier version of gcc : I successfully installed the lbp800 driver with gcc-3.4.

1) install gcc-3.4 on your system. (I founded it in the repositories of Ubuntu Hardy, but if you can use synaptic, it might be safer). 

2) using a text editor, modify the very beginning of the Makefile file you'll find in the folder lbp-800-0.1.* of your driver : 
replace the line
```
CC=gcc
```by
```
CC=gcc-3.4
```3) proceed to the installation as described in the Readme file.

Since this thread is a little bit old, I hope it might help someone else (including me if I become amnesic).

Good Luck.

---

