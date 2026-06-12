---
title: "Adding an HP network printer on an Windows XP system in Kubuntu"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by T1Oracle on 2007-10-26
I know there are instructions for Ubuntu, but the Kubuntu menu is different.

I have been able to access the shared folder on the XP system using smb but I cannot get the printer to connect.  I have the HPLIP Toolbox but I can't figure out how to use it either.

When I attempted to add the printer I went to System Settings > Printers > Add > Add Printer Class

I then clicked next.

Then I chose SMB and clicked next, since that worked for the shared folder stuff.

Then I chose Anonymous and clicked next. (I tried several combinations here, all with the same result)

Then I clicked Scan.

My workgroup showed up but when I clicked the + sign nothing was shown under it.

Then I just typed the name of the workgroup in the box above, entered the ip (the same ip that worked for the shared folder) as the server, and entered the same printer name that XP has.  After clicking next and choosing the correct printer I was able to chose to Print a Test page.  Nothing was printed.

I haven't the slightest clue what I am doing wrong here and nothing I see online is much help.

---

### Post by phidia on 2007-10-26
What is the actual physical connection of the printer e.g usb, ethernet ect?
You should be able to use the printer admininstration program to add your printer-that is if the printer is available the admin program should "see" it.

---

### Post by T1Oracle on 2007-10-26
I figured it out.

For the user name screen I chose guest, then I set the work group as the one that showed up after clicking Scan. For the server I entered the ip of the networked machine that had the printer attached (via USB).  For the printer name I entered the "shared" name of the printer which turned out to be the default which is "Share".

After that I selected the model of the printer and printed the test page successfully.

If I actually read the Test page printout from when I did a test print through the Windows system, I would have noticed that the share name was "Share."

Live and learn.

---

