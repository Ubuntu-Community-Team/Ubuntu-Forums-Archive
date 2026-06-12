---
title: "How can I extract this .bin file?"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by suomalainen on 2009-12-14
Ubunteros,

At the following HP website:

[http://h20180.www2.hp.com/apps/Lookup?h_lang=en&h_cc=us&cc=us&h_page=hpcom&lang=en&h_client=S-A-R163-1&h_pagetype=s-002&h_query=dvd840&submit=Go+%BB](http://h20180.www2.hp.com/apps/Lookup?h_lang=en&h_cc=us&cc=us&h_page=hpcom&lang=en&h_client=S-A-R163-1&h_pagetype=s-002&h_query=dvd840&submit=Go+%BB)

I"m trying to download various firmware packages. What I need to do is to be able to extract the .bin file from any of the files that I choose to download.

I was told that a program called WinRar can do this for me but after some time trying.... I got totally lost.

Is there any other way to achieve the same results???

Thank You!

---

### Post by ankspo71 on 2009-12-14
Hi,
To see if I could help in any way, I clicked on the first file, then selected the download for windows xp, the saved the exe to my desktop.

When it was downloaded to my desktop, I right clicked on the exe file and slected to "open with archive manager"

I saw the bin file right away, so I dragged the bin file out of the archive manager window and onto my desktop. It extracted with no problem when using drag and drop.

Note: I am testing an alpha release of Ubuntu 10.04, but I assume this should work as easily in Ubuntu 9.04 and 9.10.

**[COLOR=Red]EDITED[/COLOR]**: I just noticed that I have unrar installed. This might have something to do with it. If you need it too, use this code in the terminal:

**sudo apt-get install unrar**

Hope this helps,
James

---

### Post by fancypiper on 2009-12-14
I hope these links will be worth a read.

[How To Install Software in Linux](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

[How to install ANYTHING in Ubuntu!](http://amitech.50webs.com/installing/index.php.html)

---

### Post by Physical Hook on 2009-12-14
Can you show us the link from where you downloaded it ? I can't seem to find a Linux version in the link you posted previously.

---

### Post by fancypiper on 2009-12-14
Browsing the Hewlett Packard site you posted a bit further, I discovered this link: [Print, Scan and Fax Drivers for Linux ]("http://hplipopensource.com/hplip-web/index.html")

When in Linux, look for Linux programs and drivers, When using Windows, look for Windows or Microsoft drivers and programs.

---

### Post by lavinog on 2009-12-14
open it with the archive manager.
if it doesn't work, then install unrar. then try again.

---

### Post by suomalainen on 2009-12-14
ankspo71,

Thank you very much for the advice. I'm red with embarrassment that this procedure was so easy to perform in Ubuntu.

I had received instructions how to do this in XP using WinRar but the program is overwhelming. YOur procedure was easy and few steps to get desired results.

Now I can flash my DVD burner to "something else"..... Found at:

[http://italianjob.ifrance.com/](http://italianjob.ifrance.com/)

is a link to a file called "1.01 (14/11/2005 - 2nd version): in this zip file is a program called "HBLoader.exe" that when opened can take any .bin file and flash the firmware to your burner. No questions asked.

OBVIOUSLY, you need to research what you are doing and RISK breaking your burner if you ATTEMPT/TRY/Do install a bad f/w release onto a non-supported burner. Thus, you don't take firmware releases and try as many as you can to see which one will work as this will definately ruin your day.

Thanks again!!!!

---

