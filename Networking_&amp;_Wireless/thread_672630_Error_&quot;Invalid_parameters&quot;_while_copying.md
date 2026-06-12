---
title: "Error &quot;Invalid parameters&quot; while copying"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by SchneiderIS on 2008-01-19
I am trying to write from Ubuntu to a hard drive share on an AirPort Extreme Base Station (just think of it as a Windows share as it basically is) and am getting the error [COLOR="Blue"]Error "Invalid parameters" while copying ..[/COLOR].  I have tried renaming files but to no avail.  From my Mac I can shuttle files without difficulty so I don't think it is a file naming problem.  The process does start and creates the folders and even the first part of the file so I have write permissions working.  

Can anyone tell me why I keep getting this error?

---

### Post by philidox on 2008-02-25
Yes and its an easy fix.  I was having the same issue until it hit me that the file I was trying to transfer had Quotation marks in it.  I simply remove Quotation marks and I could transfer the file.  For example the file name was**[SIZE="5"] Howto - fix "no sound" issue.ogg[/SIZE]** I had to change it to **[SIZE="5"]Howto - fix no sound issue.ogg[/SIZE]**,and then the file would transfer.  Post back here and let me know if it worked.  Keep in mind its not only Quotation Marks that will cause this error.  Odd characters such as backlash, colons, semicolon is enough to set off this error.

---

### Post by SchneiderIS on 2008-02-25
That isn't my problem.  I have even stripped the file names down to a single character, the letter "A" (without quotation marks) and yet the same problem.  This is not an issue of special characters.  This appears to be a continuing issue of writing to FAT32 disks.

---

