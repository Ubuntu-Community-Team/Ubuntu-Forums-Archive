---
title: "img file to usb flash drive MAC terminal HELP!"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by bubbleoffplumb on 2009-09-05
the plan:
download the img file for ubuntu netbook remix and trying to put it on a usb flash drive using my imac (10.5.7). 

the flash drive will then be used to boot ubuntu on to my asus eee pc
BIOS version: 0607
BIOS date: 09/24/2008
Softwasre version:
Eee PC 1.6.1.3
Build Info: 2008-08-06 05:53
CPU type: Intel (R) Mobile Processor
Memory size 1024 MB

I feel like I'm getting closer.
wanted to check with something that is not clear to me.

the issue:
can someone help me make my argument valid ;) ?

following this:
sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img, /dev/rdiskN is faster than /dev/diskN). If you see the error dd: Invalid number `1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.

from here:
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

I think I'm doing something wrong with the sudo ?string??
what is invalid argument?
am I incorrect to drag the path location?

this is copied from my terminal window:
[B][I]Unmount of all volumes on disk1 was successful
[/I][/B]*adminnameshere**** sudo dd if=/****pathtoIMGfiledraggedhere*[B][I] of=/dev/rdisk1 bs=1m
Password:
dd: /dev/rdisk1: Invalid argument
657+1 records in
657+0 records out
688914432 bytes transferred in 94.918481 secs (7257959 bytes/sec)
[/I][/B]
I plugged the usb into my asus anyway, just to see-
and got "boot error"


tried with capitol M  

[B][I]sudo dd if=/pathtoIMGfiledraggedhere of=/dev/rdisk1 bs=1M
dd: bs: illegal numeric value[/I][/B]

I assume the illegal numeric value is 1M??

I also stumbled on this info (below)- still unclear what the string should contain.
I suspect this may be where my problem lies, but I haven't a clue what to put in place of the /path/to/downloaded.img ? (as mentioned above, I tried dragging the file here.)


Type : sudo dd if=/path/to/downloaded.img of=/dev/diskN bs=1m in the Terminal and hit Enter. But there are several things that you have to change here before you hit Enter:
- first the /path/to/downloaded.img is the location of the downloaded UNR installer file.

??>>>>> As we’ve already taken care of this before, all you’ve got to do is to change the string into /unr.img   <<<<<<??????

from here:
[http://www.makeuseof.com/tag/how-to-create-an-ubuntu-installation-usb-on-the-mac/](http://www.makeuseof.com/tag/how-to-create-an-ubuntu-installation-usb-on-the-mac/)

I'm hoping a fresh set of eyes will see what I'm missing.
 any help would be greatly appreciated - thanks!

---

### Post by woedend on 2009-09-05
try - sudo dd bs=8M if=/path/to/imagefile of=/device/location

obviously replacing the if and of with your proper locations
make sure the of device is unmounted.
Also, assuming you know this will wipe out any/all data on the flash drive, i never specify a partition when doing img copies.  for example my of=/dev/sdb instead of /dev/sdb1

---

### Post by bubbleoffplumb on 2009-09-05
tried this -
got 
"illegal numeric value"
so tried again with lower case m.
oddly, didn't ask for my password this time.

took a bit - 
but I got this:
[B]118+1 records in
118+1 records out
992837632 bytes transferred in 505.959234 secs (1962288 bytes/sec)

[/B]gonna eject it and see if it works
here's hoping

thanks for the suggestion

---

### Post by bubbleoffplumb on 2009-09-05
[SIZE=6]O.M.G!!!
[SIZE=3]I can barely type - there are tears in my eyes....
[SIZE=2]
it just sorta set up itself - didn't ask any partitioning questions or anything that I expected.

now I have to figure out what I do next..

thank you!

I wish I could understand what the difference in the two commands were,
but I am okay being clueless - 
as long as we've got 
boot-age!!

thanks again!
[/SIZE][/SIZE][/SIZE]

---

### Post by LoneSage on 2012-08-12
Still confused... could you post the command you used?

---

### Post by nothingspecial on 2012-08-12
This is an old thread and rather mouldy. It needs re-burying to help with the smell.

Start a new one if you want help.

Closed

---

