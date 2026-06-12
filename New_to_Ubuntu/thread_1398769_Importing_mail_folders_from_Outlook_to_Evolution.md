---
title: "Importing mail folders from Outlook to Evolution"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by asharpham on 2010-02-04
I have a few email folders in Microsoft Outlook 2003 that i want to export to Evolution. I went into Outlook and selected the export option. I selected the folder I wanted to export and chose CSV (Windows) as the format. I did this for all 3 of the folders I wanted. Each exported file was placed on a USB drive that can be read by both Windows and Ubuntu.

Then i rebooted back into Ubuntu and opened Evolution. I selected the import function, then the single file option. I located one of the files from the USB drive that i wanted to import and selected Outlook csv as the type. It appeared to startt importing but after about a minute or so it just closed and nothing was imported.

Does anyone have another suggestion for how this should have been done? I successfully imported the address book and had no such dramas with it.

Regards,
Alan.

---

### Post by asharpham on 2010-02-05
I've just discovered that the email folder I tried to import imtegrated its contents into the address book. How do I import an email folder as a folder in Evolution?

Alan

---

### Post by Rowan_ on 2010-11-09
Marked as solved, but no solution.  Awesome.

---

### Post by Cheesehead on 2010-11-09
You might be making it too complicated.

Don't use Outlook's export function.
Instead, copy your entire .pst file across and let Evolution import *that*.
You can always prune the folder tree after import.

I imported a 1.3G .pst the easy way, and it kept everything - all the links to responses and threads and attachments. Beautiful.

---

### Post by mrsfixit on 2010-11-30
> **Cheesehead said:**
> You might be making it too complicated.

Don't use Outlook's export function.
Instead, copy your entire .pst file across and let Evolution import *that*.
You can always prune the folder tree after import.

I imported a 1.3G .pst the easy way, and it kept everything - all the links to responses and threads and attachments. Beautiful.

I just tried this and it worked. Thanks! :)

How do you import the contacts and the rest of the data from Outlook? I also need to import the email and contacts from Eudora 6.2 into Sylpheed.

I'm trying to get my husband to make the switch from XP, but he won't if I can't solve the email import problem.

---

