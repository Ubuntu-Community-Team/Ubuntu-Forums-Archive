---
title: "print jobs won't get past processing stage"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by jennifermq on 2010-03-07
I have a HP Photosmart C4680 printer that worked fine when I first installed it. Now, every time I try to print, the job stays in the print queue as "processing" . Here are the steps I've already taken to try and fix the issue:

1) deleted the driver and reinstalled the driver that came with Ububtu
2) got hplip and installed it via command line
3) went through the package manager and reinstalled hplip and it's associated packages

And none of it has worked. I restated the system, check to make sure my printer (which Ubuntu sees) is the default printer, no dice. What am I missing?

---

### Post by paydaydaddy on 2010-03-07
Is the printer local or on network? Have you looked at the wiki pages:

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)

[https://help.ubuntu.com/9.10/printing/C/printing.html#local](https://help.ubuntu.com/9.10/printing/C/printing.html#local)

---

### Post by lyall on 2010-03-07
Have you check to see printer properties for in enable

if if does not have a check in the box it is not enable

open you Printer window
right click on the print and see what it says 

another way to check is right click on the printer and click on Properties
On the Print Properties click on Policies and check the State
is Enabled checked

good luck and have fun learning

---

### Post by Pithikos on 2011-02-24
That solved it for me! I went to the printer properties and it seems that the printer software was pointing to an IP that doesn't exist. For example it was like this:

```
DEVICE URI:socket://192.168.1.3:9100
```So I just changed that to

```
DEVICE URI:socket://192.168.1.4:9100
``` where 192.168.1.4 is the ip of my printer in the local network. It worked beautifully

---

### Post by ejames82 on 2012-12-04
hello,

thanks for all suggestions, but special thanks to PitkinOS for his suggestion.  his suggestion made it possible for me to print.

my problem was the same as many on here.  the printer was connected, drivers installed successfully and I was attempting to print a test page and the window said the printer was 'processing'.  but the printer was doing nothing and the printer didn't seem to know a thing.  there was no indication on the printers readout that any data was received.

my device URI was listed as dev/lp0 which my investigation later determined to be the parallel port.  nothing was plugged into the parallel port.  my printer was plugged into the usb.  I clicked on the 'change' button next to 'Device URI' and a new window popped up.  then I  selected the first choice in the list which happened to have 'usb' in the name.  even if a newbie didn't know what these terms mean, they could still write down the choice that was originally selected, then choose each one and try to print, and if it didn't work, return to the original selection with no damage done.  they would be where they were to begin with.

when I licked 'OK' after making the change, the window did not immediately change the letters in the box either.  however, the printer immediately started to work, so don't be discouraged if the letters don't change right away.  after closing the window and reopening it, the letters will be changed, or at least they had for me.

---

### Post by wildmanne39 on 2012-12-04
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

