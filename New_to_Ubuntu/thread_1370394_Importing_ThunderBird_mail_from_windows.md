---
title: "Importing ThunderBird mail from windows"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by GreggC on 2010-01-02
I have a duel boot system Vista and karmic (9.10).:)
(My wife uses Vista)
I would like to import the thunderbird mail and address book from Vista to thunderbird running under karmic.  I can read new mail messages in both systems - I just leave the mail on the server for a few days. I would like to import my old mail and address books from Vista. Any help would be appreciated...

---

### Post by starcraft.man on 2010-01-02
Contacts can easily be exported and imported from the Address Book area, under tools.

Mail is stored in the mbox format. Simply find the folder you set to store the mail and copy it to the linux partition. Under the main menu Tools > Import. You can bring those mail into the main program.

As to leaving mail on server, be sure to configure imap instead of standard pop if you want that. See google for steps how, it varies by what service gives ya mail.

---

### Post by GreggC on 2010-01-02
Thanks!
The tools>import was only showing communicator mail.
I downloaded the importExport tool extension, followed your advice and it worked w/o any problems.

---

### Post by starcraft.man on 2010-01-02
> **GreggC said:**
> Thanks!
The tools>import was only showing communicator mail.
I downloaded the importExport tool extension, followed your advice and it worked w/o any problems.

No problem, I'll keep that extension in mind in future. Though I grown fond of just leaving it in the cloud with imap.

---

### Post by 73ckn797 on 2010-01-02
In Windows look at 

C:\Documents and Settings\Your Name\Application Data\Thunderbird\Profiles


Copy the directory that has a similar name to "6cdx09df.default" and also the "profiles.ini".

Go to /home/Your Name/.mozilla-thunderbird and paste into that directory.

That should work. 

You can just copy the "Mail" folder from the Windows directory referred to above and paste that into the .mozilla-thunderbird/*.default directory. The folder name will have it's own numerical/text name.

---

