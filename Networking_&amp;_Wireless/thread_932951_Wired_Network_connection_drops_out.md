---
title: "Wired Network connection drops out"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by dunskii on 2008-09-28
Hello all,
I'm fairly new to Linux/Ubuntu and with everything so far I have got working by trial and error and forums.  Though my latest problem has completely stumped me.  When I copy large files to or from one of my desktop PC's the network connection will drop out after 5-10 minutes.  Sometimes I will get the error, "Unable to resolve host name" or "Host name does not exist" and other times no errors at all.
Not sure where to start with this, so if you point me in the right direction that would be great.
Cheers
D
Oh FYI, all my PC's are running Hardy

Just found this thread, 
[http://ubuntuforums.org/showthread.php?t=278693](http://ubuntuforums.org/showthread.php?t=278693)
it could be the screensaver, so I'll let you know how I go, just strange that this didn't happen on the other PC (though it is a lot more powerful)

---

### Post by dunskii on 2008-09-29
Well disabling the screensaver didn't work, just wondering if there would be any other processes that run every 10 minutes
d
:confused:

---

### Post by Iowan on 2008-09-29
Does BIOS have any sort of power-saving "sleep" mode?

---

### Post by dunskii on 2008-09-29
yes it does.
Should the ACPI Suspend type be S1 or S3.
Will I need to edit the boot file, if so would it be better setting acpi=no, and if this is the case where do I add or edit this

---

### Post by dunskii on 2008-09-30
Ok, I've installed boot up manager and disabled acpi with out any luck.
i also added noapic acpi=off  to the menu.lst with no luck as well

---

