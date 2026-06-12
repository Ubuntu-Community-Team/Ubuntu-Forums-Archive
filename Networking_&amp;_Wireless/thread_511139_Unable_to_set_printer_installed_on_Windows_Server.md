---
title: "Unable to set printer installed on Windows Server"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by frayalejandro on 2007-07-27
I have a small Windows 2000 Advanced Server network set up in my office. All stations have Windows XP, except mine. Everything is  fine in the files and internet sharing area, but I can no longer print with my Epson 5900L. When I select new printer, Network Printer, Windows Printer (SMB), Ubuntu detects the printer in the network, but when I send the print order, it says "stopped: job stopped" with the message "Ready: /usr/lib/cups/filter/foomatic-rip failed"

 Can someone tell me where I am going wrong please.:confused:

---

### Post by Soybean on 2007-07-27
Hmm... do you have appropriate Linux drivers for an Epson 5900L? Also, you may need to enter a valid username and password for the Windows box when setting up the printer. Even if you don't need to on the Windows based systems... sometimes they're transmitting your username and password without telling you.

---

### Post by frayalejandro on 2007-07-27
I allready installed the appropiate driver, and I do enter the correct username and password.

:confused:

---

### Post by Soybean on 2007-07-27
Bah. Windows networking is always such voodoo... have you tried chanting while walking counter-clockwise around the Windows server? ;)

Well, I did a bit of looking around, and apparently cups sometimes has more detailed information than it gives you there. If you point your web browser at [http://localhost:631](http://localhost:631) it'll take you to your cups interface... it seems that clicking on the "jobs" tab there might give more info about the error. Not that the extra info is likely to magically solve the problem, but it's a step in the right direction.

Oh, also... did you try printing a test page when you were setting up the printer? If not, you should try that too, just to rule out the possiblity that the problem is with the particular document you're trying to print. It's an *unlikely* possibility, but it's worth checking just in case.

---

### Post by frayalejandro on 2007-07-27
Yes, I´ve tried to print the test page, but i keep getting the same error message.

I also went to //localhost:631 but it keeps me asking the same "CUPS" username and password. I am using my box username. Is that correct?:confused:

---

### Post by Soybean on 2007-07-27
> **frayalejandro said:**
> I also went to //localhost:631 but it keeps me asking the same "CUPS" username and password. I am using my box username. Is that correct?:confused:

I... don't know. Mine just opens, without any password requirement. Is your username/password on the windows server different? If so, you could try that one. Maybe it didn't save the credentials you entered when you set up the printer, so it's looking for them now. I'm just guessing here, though... 

Oh, also, there's a command-line tool called "lppasswd" that seems to be related to setting CUPS-specific passwords. I just had time to skim the manpage, though, so I don't entirely understand what it does. If the windows user/password doesn't work, I'd recommend reading up on lppasswd.

---

### Post by frayalejandro on 2007-07-31
thanks.

---

