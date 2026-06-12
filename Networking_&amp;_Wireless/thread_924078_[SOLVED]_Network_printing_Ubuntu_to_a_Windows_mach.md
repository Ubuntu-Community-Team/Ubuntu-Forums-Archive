---
title: "[SOLVED] Network printing: Ubuntu to a Windows machine."
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by juwain on 2008-09-19
Hi! I'm trying to set up network printing from my Ubuntu Hardy machine to a server running Win2003 Server. Printer is Canon PIXMA iP2200. It does work from any Windows machine around. I'm trying to access the printer via SAMBA. I've read lots of manuals and done everything right. But the symptoms are unlike anything i read about. I've added the printer to the system. It seems to be ok. When I try to print the job is added to the queue and it says the printer is actually working. Then in some  6-8 seconds the job disappears from the queue just as if printing was finished! The printer itself shows no reaction at all. To led-blinking, no sounds - nothing!

There are no drivers for 2200 model, so i tried to use iP2000 drivers and some generic. I can see the printer in shares via SAMBA. When i clicked "Verify" in the connection dialog the verification passed. But if turn off the printer, the behavior is exactly the same! It acts as if everything is going right! Can anybody help? If you need more information, please ask! I will gladly provide it.

---

### Post by wodenx on 2008-09-29
hi
i am having a very similar problem.  i see you've marked the thread as solved - if you did, in fact, figure it out, could you please let me know how?
by the way - there are in fact drivers for your printer - more info at [here]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon")
and also
[here]("http://arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html").
i have installed the correct drivers, and can print when the printer is attached directly to the linux box.  i can also see it and install it using samba from the "Printing" control panel.  but when i print, the job appears in the windows box print queue for a second or two, then disappears without a trace.
any solution you found would be very much appreciated.
thanks

---

### Post by Another Monkey on 2008-09-29
I'd like to know too - may give me a clue as to my own networking frustrations.

---

### Post by wodenx on 2008-09-29
I FINALLY got my pixma ip1600 to print as a samba share.  Posting here in case it helps anyone.

Configuration:  
Windows box running XP-SP2 with attached Canon Pixma ip1600 via USB
Linux box running Ubuntu Hardy

Mostly I followed the instructions [here]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200"), but with the following modification. For some reason i didn't have libxml installed, so i downloaded the package libxml2 using synaptic.

then checking the library links (step 7 in the referenced article) - just have to make sure that the following 3 libraries are linked to the most recent version of your system

/usr/lib/libtiff.so.3 
/usr/lib/libxml2.so.2
/usr/lib/libpng.so.3

in my case, that means
/usr/lib/libtiff.so.3 -> 
      /usr/lib/libtiff.so.4 ->
           /usr/lib/libtiff.so.4.2.1

/usr/lib/libxml2.so.2 -> /usr/lib/libxml2.so.2.1

/usr/lib/libpng.so.3 -> /usr/lib/libpng12.so.0 ->
       /usr/lib/libpng12.so.0.15

then install the printer using the "Printing" control panel - add printer, windows printer via samba, browse, find the printer, choose driver Canon and "IP2200 Ver 2.60" (which is listed towards the end, not with the rest of the pixmas), finish up, and it printed a test page.

Cheers!

---

