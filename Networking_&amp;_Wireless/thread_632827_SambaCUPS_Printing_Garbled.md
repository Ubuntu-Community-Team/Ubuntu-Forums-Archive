---
title: "Samba/CUPS Printing Garbled"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by nighthawk98tj on 2007-12-05
Hi All,

I have successfully setup Samba and CUPS to share my HP Laserjet 1022 from my Ubuntu server, however, whenever I print something, the text and/or graphics are all garbled.  Either some lines are "ghosted" on top of the text on the page, or there are random characters, or there are a bunch of lines seemingly printed on top of each other.  I am using the "Recommended" driver in Ubuntu for the printer and I am printing from another Ubuntu box.  I have tried printing through Samba and also directly through CUPS (IPP).

Does anyone have any suggestions as to why this is not printing properly?  It sounds like a driver issue, but I've tried both that are available to select from.

Any suggestions are much appreciated.

Thanks,

Tim

---

### Post by nighthawk98tj on 2007-12-05
Some additional details:

The print server is running mythbuntu, so I had to install CUPS and the foo2zjs drivers as it is not packaged with them.

When I print a test page from the print server system, it is still garbled, faded, etc.

Whenever I print something, it causes the printer lights to go nuts and I have to power cycle it to be able to print again...

---

### Post by csat on 2007-12-06
I was having the same issue with my 1022.  Few minutes ago, after reading your post, I submitted a job for printing this query and got 1022 stucked.  I went to System, Administration, Printing (Ubuntu) and deleted printer installation and reinstalled again and it started printing again.  Well I don't know if my SAMBA setup was affected or not...

---

### Post by nighthawk98tj on 2007-12-06
Hmm, strange.

I seem to have narrowed down the problem.  The issue is generally only appearing with graphics now.

When I print a PDF file, for example, it will print about half the page, then end with an almost solid black bar horizontally across the page.  Sometimes it throws the printer into an error, too.

Generally, text seems fine...

Also, the part of the PDF that DOES print, is perfect, but it won't finish.

Any ideas?

---

### Post by nighthawk98tj on 2007-12-07
**UPDATE:**  OK, so graphics are not the only problem...

It appears as though anything I print that is longer than 2/3 of a page gets a 1/2" thick bar of garbled stuff across the page 2/3 of the way down.  I'm not sure why it is doing this.

It is doing it whether I print over IPP to the CUPS server from an Ubuntu box, print via Samba from an Ubuntu box or print via Samba from a Windows box.  Same issue all the way around.

If I print a doc that is 1/4 of a page, it turns out fine.  Also, if I connect it directly to my Windows PC or directly to my other Ubuntu box, it prints just fine...

However, if I print locally FROM the ubuntu server PC, the same thing happens.  Therefore, the problem is with THAT PC, but I'm just not sure what is wrong.  I am using the same driver, etc...

Any ideas?

Thank you!

Tim

---

