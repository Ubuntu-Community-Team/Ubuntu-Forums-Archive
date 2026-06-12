---
title: "How do I convert Outlook Express mail to Evolution mail?"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by bwallum on 2010-10-07
Hi

I have found the .dbx files that Outlook Express (version 6) uses for storing email messages and contacts. I have used the export function in Outlook Express to generate a text file for the contacts.

However, the messages export function fails. Evolution doesn't appear to be able to import .dbx files. How can I extract messages from Outlook Express and put them into Evolution?

---

### Post by P4man on 2010-10-07
Try this:
[http://www.softpedia.com/get/Internet/E-mail/Mail-Utilities/DbxConv.shtml](http://www.softpedia.com/get/Internet/E-mail/Mail-Utilities/DbxConv.shtml)

If that doesnt work, I think KMail can import dbx. You may not like KMail on gnome, but once in KMail you can export it to evolution and remove it again. Warning: Kmail is a KDE application, so installing it will cause it to install a LOT of KDE dependencies.

---

### Post by bwallum on 2010-10-11
DbxConv.exe worked for me, thanks for the steer. I had to run it in a M$ box and translate/parse the dbx files to mbox format, which, via a usb stick, could then be imported by Evolution on a Ubuntu box.

The advice to put the dbx files in the same folder as the DbxConv.exe file was useful. It took away the complication of specifying different paths.

It would be good to have a linux utility do the same thing or perhaps enable Evolution to import dbx files directly. ??

Thanks again!

---

### Post by michael.kyritsis on 2010-12-28
I used DbxConv.exe (which I ran in Wine, by "winconsole cmd" and then "dbxconv -eml *.dbx"

the -eml switch produces one eml file for each email it finds in the dbx file.  eml files preserve font information and attachments, but I found that going directly to mbox format (the default for dbxconv) caused the emails to be reduced to plain text.

Then I loaded the eml files into Thunderbird (with a Thunderbird plug-in called import/export), and from there moved the emails to Evolution.

.

---

### Post by loadbongsnotguns on 2012-09-04
Just a quick tip - if you don't have Wine, or much space or internet connectivity to get it (I spend most of my time in Tanzania) download Sylpheed, a very lightweight email client (its about 6mb) - this can read .dbx and convert the to .mbx for you, without messing around with the windows command line.

Hope this helps

---

### Post by howefield on 2012-09-04
Thank you for the information.

Old thread closed.

---

