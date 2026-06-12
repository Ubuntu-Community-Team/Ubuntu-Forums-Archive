---
title: "FTP and File Upload Hang"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by lenny8088 on 2007-05-21
Hopefully I describe this well enough...

I've recently set up a test intranet server (LAMP) on an antique piece of machinery. From the beginning I noticed that ftp connections would hang if I used a graphical client (FireFTP, Filezilla are the two I generally install). But command line (from windows) ftp worked fine - if slow and tedious. 

Now I am trying to create a simple PHP to upload a file which will then go thru x and y manipulations and generally make my life easier. However I can't upload the darn thing (currently 382k). I can upload smaller files (< 30K easily enough) but anything else and the browse just spins away and never comes back. Every other PHP function-a-ma-jig has worked fine. 

The two seem related to me but I can't figure out what the issue is or how to fix/alleviate/avoid it. 

For the PHP side I checked the PHP ini settings (both file and post max sizes are fine - 5 and 8 meg respectively), I've checked permissions on the /tmp dir - wide open. 

Thoughts, ideas, voodoo. Hopefully it's something painfully obviously that I've missed. 

Thanks,
-Lenny

---

