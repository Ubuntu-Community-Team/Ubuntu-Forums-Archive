---
title: "Documents"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by rmsmith87 on 2010-04-17
Hey,

I wasn't sure where to post this.  But my problem is this.  Occasionally I have to do document work where I talked a list of names, dates, companies, and locations and then copy and paste them into 10 different 1-2 page documents.  If there was a way I could make some sort of template that is linked to those documents so that when I insert the the information into the template it ripples through all the other documents it would save me lots of time in the long run.  Is there a way I can set this up?  I dual boot ubuntu and 7 so if it can only be done in one or the other that fine.

Thanks.

---

### Post by kg87 on 2010-04-17
I think it could be worked both in either OS. What i think your looking for is mail merge. It allows a database/spreadsheet to be used as a data source for the document, so you can set fields in the document to match those of the database. 

I'm not really good at describing the process, but i've done it numerous times. if i had the pc infront of me, i'd show you what i mean. 

Basically, you need to enter all your data (the addresses, peoples names 
etc) before, but it's time saving in the long run!

I've placed two links below, which should set you on your way. 

[Mail Merge for Open Office]("http://wiki.services.openoffice.org/wiki/Documentation/OOoAuthors_User_Manual/Writer_Guide/Using_Mail_Merge")

[Mail Merge for MS Office]("http://office.microsoft.com/en-us/help/ha010349201033.aspx")

Hope that sets you in the right direction.

---

### Post by quadproc on 2010-04-17
> **rmsmith87 said:**
> Hey,

I wasn't sure where to post this.  But my problem is this.  Occasionally I have to do document work where I talked a list of names, dates, companies, and locations and then copy and paste them into 10 different 1-2 page documents...
Thanks.
I assume that you are starting with a single file that contains all of the relevant data in some known format.  If so, this would be a good application for a shell script to generate your reports.  Have you looked into awk?  You could implement one script that generates 10 different reports, or you could write 10 scripts that each produce a single report.  I think that the key issue is "how does the data get into the computer system in the first place".

quadproc

---

