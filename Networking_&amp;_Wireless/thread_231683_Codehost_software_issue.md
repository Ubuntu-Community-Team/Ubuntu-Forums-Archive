---
title: "Codehost software issue"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by scottie4442 on 2006-08-07
I am using codehost software to connect directly to a networked canon copier/printer.  The software is called BrightQ. I had it working fine in breezy and it was working in dapper but when I tried to upgrade to the newest version, 2.3, it give me the following two error when I start up the codehost-config with sudo:

CUPS_BackEnd: get-printers failed: client-error-not-found
CUPS_BackEnd: get-classes failed: client-error-not-found

Any help here would be appreciated. I have contacted the codehost people but no response as of this posting. Not sure if this is an updated cupsd problem or something else.  Also I did try to go back to the last version of BrightQ, had the same results.

---

### Post by Worsin on 2006-09-14
I am getting same thing and would love a fix for this.

---

### Post by scottie4442 on 2006-09-14
I did an upgrade on the cups system and it is working fine now. I went into the System>Administration>Printing screen and created a printer, use the imagerunner 330s driver and the HP JetDirect connection and then I did the Codehost configuration from the console, make sure you use sudo, and it works fine.  I know that the canon version of codehost work, the Kyocera/Mita one you have to pay for the drivers, not sure about any of the others.

---

### Post by Worsin on 2006-09-14
Well this has cleared up that error but now I get another when I go to the last step to add printer it gives me this error...

add-printer failed: client-error-not-authorized

seems strange because i was able to do this easy on SuSE 10.1

Any ideas?

---

### Post by tbonius on 2006-09-14
Are you performing this action as sudo or root?

T

---

### Post by scottie4442 on 2006-09-14
I remember, you must go and edit the cupsd.conf under /etc/cups, do this as sudo: sudo gedit /etc/cups/cupsd.conf.  When you are in the file go down and locate the lines that say Order deny,allow and put a # in front of the lines right by each of these, there were 4 sets of these right at the end of this file for me.  After this save the file and try to run the command: 
sudo codehost-config  again and it should work, the denies were the permission issue, sorry I forgot to post this.

Scott Adams

---

