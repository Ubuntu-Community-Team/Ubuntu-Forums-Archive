---
title: "Ubuntu and Canon dog fight"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by turboopugsleylx on 2010-01-09
Printer wont print!

Hey guys I have a Canon ip3600 and I have been having all sorts of issues.....lack of ppd driver files (fixed)....psotcanonij error (fixed I think after download)....

Now when I hit print it asks which printer and I select mine....and then hit print...I see the status bar go to 100%...and then....either nothing (and the printer says stopped in the status) or it pops up with an unable to print error...run troubleshoot and nothing happens....

[http://ubuntuforums.org/showthread.php?t=575779&highlight=virtualbox+recognizing+usb+device](http://ubuntuforums.org/showthread.php?t=575779&highlight=virtualbox+recognizing+usb+device)

This was an interesting thread...though not sure if it applies to me....guys I am about to chuck this printer out the window...can someone please help me get this fixed and working!?

---

### Post by marco123 on 2010-01-09
Make sure you open the window first.;)

Seriously though, Canon are notorious for their lack of Linux support.

---

### Post by marco123 on 2010-01-09
Is it a Pixma?  If so it reckons it "mostly" works on the Open Printing database, and that there's a commercial Linux driver available from Turboprint.

[http://www.openprinting.org/show_printer.cgi?recnum=Canon-Pixma_iP3600](http://www.openprinting.org/show_printer.cgi?recnum=Canon-Pixma_iP3600)

[http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_iP3600](http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_iP3600)

---

### Post by turboopugsleylx on 2010-01-09
how would I utilize that?

---

### Post by marco123 on 2010-01-09
[http://www.zedonet.com/en_p_turboprint_download_2.phtml](http://www.zedonet.com/en_p_turboprint_download_2.phtml)

Download the .deb version and install it.  It's not free (30 day trial), but then again how much would a new HP printer cost?

---

### Post by Duncan J Murray on 2010-01-09
This page helped me a lot...

[http://preview.tinyurl.com/yc9covd](http://preview.tinyurl.com/yc9covd)

The crucial bit was working out the 'new' bits, which the driver was missing because it was looking for some 'old' things.  I don't really have a clue what I'm talking about, but I did get my Pixma IP2500 working which was nice...

Duncan

---

### Post by turboopugsleylx on 2010-01-10
Dude your awesome...I spent 5 hours trying to fix it and u did it in 15 mins...on a side question....is there anyway for Ubuntu to "defrag" or go thru and clean up all the files and mess I made screwing around with things? I remember seeing a file "straightener" so to say when I booted in safe mode before...any suggestions on this...mainly for organizing and fixing things that could slow the OS down?

---

### Post by Duncan J Murray on 2010-01-16
You don't need to defrag linux filesystems.  Don't ask me why, but I haven't had any problems or performance issues yet...

Try system > administration > computer janitor

watch out though, it tries to de-install stuff that you actually need!  Like those canon printer drivers...

I'm sure there was a terminal command that used to clean up things that weren't used anymore... but I can't remember it.

---

### Post by Duncan J Murray on 2010-01-17
Just remembered : try apt-get autoremove in terminal

---

