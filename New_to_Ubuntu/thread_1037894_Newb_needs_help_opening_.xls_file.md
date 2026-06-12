---
title: "Newb needs help opening .xls file"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Tighearna on 2009-01-12
This is my first post to the forums, so I would like to say hello and thank you for this wonderful OS and helpful and friendly attitude here.

Now on to the question:

We are looking at making the switch from Micro$haft to Unbuntu. The only issue so far is that one of our vendors supplies inventory feeds in what is labeledd as a .xls file but I believe is Excel XML. At least that is what I believe it is, see copy below.

At this point I have used excel to open the file with no problem. In Unbuntu however, I cannot seem to get the file open. I have tried, Open Office spreadsheet, Kspread, Gnumeric, even excel viewer running under wine. Nothing opens these files. I need them to open in a spreadsheet for data manipulation.

This is about the only thing preventing us from making a complete switch to Unbuntu. Any ideas how to open these files?

```

<?xml version="1.0"?>
<ss:Workbook xmlns:ss="urn:schemas-microsoft-com:office:spreadsheet">
```

Thank you,
Jim

---

### Post by kestrel1 on 2009-01-12
Try installing Open Office 3 I believe that supports the opening of XLS files.

---

### Post by Tighearna on 2009-01-12
Tried, No Joy

---

### Post by hyper_ch on 2009-01-12
sign up for a google docs account. You can import there the .xls file and then have it exported as openoffice file.

However most stuff should run - except if you use visual basic in it for programming.

---

### Post by kestrel1 on 2009-01-12
OO3 should have opened it as it supports XLS & then newer XLSX.
However if it has something that is only supported in Excel ie. VB as mentioned above, I dought if you will be able to.

---

### Post by Tighearna on 2009-01-12
Just tried uploading to google docs. That didn't work either. For what it's worth I don't think it is an OS issue. I had the same problem in XP. What I would do is open it with excel, save it as an .xls the open that with Open Office and save it as an .ods.

Will excel run under wine? I really don't want to have to keep a dual boot just to open a single file from one distributor.

Any other ideas?

Thank you for the quick replies I am uber imperessed so far. :)

---

### Post by achase79 on 2009-01-12
Depending on the version Excel will run in wine. Check the AppDB at Winehq.org to find out if the version you have will work

---

### Post by RobsterUK on 2009-01-12
If this is the only thing stopping you from switching, maybe you could you ask the supplier to provide the file in a format like CSV (comma separated values).

If they are editing it in Excel it should be about 5 seconds work for them to save it in this format, which can be opened in pretty much any spreadsheet software. If they value their customers they shouldn't have a problem with it.

---

### Post by Tighearna on 2009-01-12
I've got an email off to them asking about csv already. (Great minds and all, lol). I'm trying to get excel installed as we speak. Apparently there is a bug with the version I have. 03 Pro. So, I'll let everyone know. Thank you again for the help.

Jim

---

### Post by hyper_ch on 2009-01-12
depending on your machine you could install virtualbox or vmware to install a virtual windows xp and inside there Microsoft office...

---

### Post by ugm6hr on 2009-01-12
I think this is the format that is being supplied: [http://en.wikipedia.org/wiki/Microsoft_Office_XML_formats](http://en.wikipedia.org/wiki/Microsoft_Office_XML_formats)

I found this explanation on how Excel (2003) interprets / imports an xml file: [http://msdn.microsoft.com/en-gb/library/aa159889(office.11).aspx](http://msdn.microsoft.com/en-gb/library/aa159889(office.11).aspx)

Obviously, you are not the first person to ask the question:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=9&t=10534&st=0&sk=t&sd=a&sid=bb8e94b675cc032485fad8076aa2f0fe&start=10](http://user.services.openoffice.org/en/forum/viewtopic.php?f=9&t=10534&st=0&sk=t&sd=a&sid=bb8e94b675cc032485fad8076aa2f0fe&start=10)

Anyway, it appears you have to create a custom macro dependent on your specific xml files:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=45&t=3490](http://user.services.openoffice.org/en/forum/viewtopic.php?f=45&t=3490)

---

### Post by jrusso2 on 2009-01-12
I would say if you tried all those programs and can't open it there is something wrong with that file.  Maybe its corrupt.  Ask for a copy they have opened recently.

---

### Post by Tighearna on 2009-01-17
I'm afraid writing a macro is WAYYYYYYYY outside my skill level. I was able to get it running though. I was able to install excel 03 pro under wine. I just had to install the run time file in wine first. Then just point to the file and "open with" pointing to excel. (Just in case anyone else runs into this situation).

Thank you everyone for your help.
Jim

---

