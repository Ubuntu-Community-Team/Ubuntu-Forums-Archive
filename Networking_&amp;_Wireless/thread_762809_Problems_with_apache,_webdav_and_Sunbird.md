---
title: "Problems with apache, webdav and Sunbird"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by leillo1975 on 2008-04-22
First: I have no idea if this is the forum where I can post this questión

Two: I post a reply with my problems in other forum (Tutorials), but I don't have response ( [http://forums.mozillazine.org/viewtopic.php?p=3347833#3347833](http://forums.mozillazine.org/viewtopic.php?p=3347833#3347833) ).

The problem is the following: 

I have a apache server running with webdav in a computer with ubuntu (192.168.0.221), and, with my computer (Ubuntu 7.10), I tried to create an .ics calendar with sunbird. When I create a remote calendar in this server ([http://192.168.0.221:999/davhome/](http://192.168.0.221:999/davhome/)), it shows a message that the calendar was created succesfully.

When I create the first event, Sunbird shows in the calendar, but, when I create the second or more, Sunbird don't show it, and the calendar in the /var/www/davhome/ is not created in the server. I try to make It with the commands:

Ahhh, the error in the Sunbird's Error Console is the following:

```
Error: [Exception... "Component returned failure code: 0x80040111 (NS_ERROR_NOT_AVAILABLE) [nsIHttpChannel.requestSucceeded]" nsresult: "0x80040111 (NS_ERROR_NOT_AVAILABLE)" location: "JS frame :: file:///home/leo/Escritorio/sunbird/js/calICSCalendar.js :: anonymous :: line 363" data: no]
Archivo de origen: file:///home/leo/Escritorio/sunbird/js/calICSCalendar.js
Línea: 363
```

Someone can Help me please (my ugly boss wants kill me)

Note: Sorry, my English is very bad, I'm from Spain

---

### Post by Webdemic on 2008-05-06
I have run into this problem on my own server. It has been a while, but as I recall, it was an issue with my .htaccess file. Have you set up your DAV lock file?

Honestly, I have run into nothing but problems with this sort of setup. My recommendation, if you can get away with it, is to use ftp instead. 

Simply place the calendar file in a folder that is readable/writable via ftp. Then add the calendar in Sunbird using the following connection URL:

ftp://username:password@ServerAddressOrDomainName/CalendarName.ics

A simple example in case the cryptic example above doesn't make sence:

ftp://me:mysecretpassword@192.168.0.1/MySchedule.ics

I know this doesn't really answer your question, but hopefully it helps. If I find my old .htaccess file, I will be sure to post it.

---

