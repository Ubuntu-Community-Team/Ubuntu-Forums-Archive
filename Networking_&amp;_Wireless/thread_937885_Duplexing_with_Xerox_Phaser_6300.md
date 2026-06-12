---
title: "Duplexing with Xerox Phaser 6300"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by legomind on 2008-10-04
Well, my problem is pretty simple. I installed the .ppd driver from the Xerox website in BOTH the printer gui and the Cups web interface (at different times of course). I set the duplex option to long (tried short too). But when I print anything, (.pdf, .ps, .doc) the pages are printed single sided. The in the print dialog, duplex is grayed out and says not installed. Any ideas? OH, forgot to mention, the windows driver prints duplex fine. ](*,)

---

### Post by legomind on 2008-10-04
Now I feel kinda stupid, but it was an easy thing to mess up. :D

When installing the printer, I at first used the automatic uri that was at the top of the option box when installing the printer. DONT USE IT!!! You must use the JetDirect option with this uri:
```
socket://<ip of printer>:9100
```

So, first step install the driver: 
copy the attached driver (I found it on the xerox website) to "/usr/share/cups/model/Xerox/" (assuming you are using cups)

Then install the printer using the JetDirect option with the correct uri, goto job options tab and set the duplex option.

Done!

---

### Post by bowsercake on 2009-03-23
I just searched and found this thread. Thanks for the info. I just got my Phaser 6300 installed here at work.

I finally have Ubuntu setup with full access to all of our websites with certificates and now the printer. Good times :D

---

