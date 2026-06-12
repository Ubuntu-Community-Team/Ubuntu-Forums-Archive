---
title: "Printing from Windows (98) to Ubuntu 6.06"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by bcollignon on 2006-10-20
I was finally (after some searching) able to get Windows 98 to print via Ubuntu running Samba and CUPS.  And, yes, I will post my smb.conf file.  I'm writing from work at the moment and don't have it available.  However, I will tell you what was the sticking point for me.  If you just want to set up a basic share, without security and buzzers and whistles, to see whether Windows will print to Ubuntu, then start with a couple of things.  In the [Global] section of smb.conf, use "share" instead of "user" where it applies.  There's also a setting for making the printer public; set this to "yes".  Then, and this is crucial, make sure the share name for the printer (at least where Windows 98 and ME are concerned) is less than 12 characters.  I couldn't see the printer share until I did that.  Then, stopping Windows from asking for a password (which I didn't have anyway) was near impossible until I went to "share" from "user" on security on smb.conf.  I haven't played with the smb.conf file yet to see what the ramifications are for some of the settings, but that's next.  Naturally set Printing to CUPS and Printcap as well.  I'm going from memory here, but I'll post the successfull smb.conf file later.  Thanks for all posts and guidance.

---

