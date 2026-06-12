---
title: "Error when starting Archive Manager"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by greenleaves123 on 2009-03-11
I finally got sound to work again on my Dell Mini 9 after reinstalling Ubuntu.

Now the problem is I still can't get the Windows key to be F11. I need it to be F11 because my netbook has a modified keyboard and doesn't have F11 or F12. I like using F11 to fullscreen on Firefox because my screen is tiny.

I found out that Dell has a BIOS download that will turn Fn+Z into F11 and Fn+x into F12.

I downloaded the A04 BIO thingie, but it won't open.

I get this error:

[/home/jenny/Desktop/910_A04.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/jenny/Desktop/910_A04.exe or
          /home/jenny/Desktop/910_A04.exe.zip, and cannot find /home/jenny/Desktop/910_A04.exe.ZIP, period.

How do I get it to work?

---

### Post by tarps87 on 2009-03-17
The bios update file is a binary file for windows and therefore won't run on GNU/Linux. Wine or some other compatibility layer may work but as this is a bios upgrade I wouldn't suggest it.
There should be a GNU/Linux version of the upgrade program or a bootable cd. I can not look on there website at the moment as it is blocked

---

### Post by oldos2er on 2009-03-17
If your Dell netbook came with Ubuntu preinstalled, Dell should provide a Linux-based BIOS upgrade program--at least they do for my XPS 410. You might want to ask this on the Dell Support subforum.

---

