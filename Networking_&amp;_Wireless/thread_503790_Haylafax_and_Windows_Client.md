---
title: "Haylafax and Windows Client"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by CHFFriday on 2007-07-18
I have setup a Fax Server running Feisty Fawn and Hylafax fax server.  I can send and receive faxes. This server is running in a Windows 2000 Server Domain.

Now I&#8217;m trying to setup a Windows XP workstation using WHFC. This is working as I can see all the Queues. 

Hers is my problem: I can not read the received Faxes. I have gone to the WHFC Web site and followed all of the suggestions but NO progress with this problem. I have tried several other Tif Viewers but they run and there is no picture. WHFC seams not to be grabbing the Fax file (TIF).

If I used a client called JHYLAFAX , it&#8217;s a Java client, I can view the faxes using the Windows XP default TIF Viewer. I want to use the WHFC Client because of the Fax to printer option.

I hope some one on this form has had the same problem and can help.

CHFFriday

---

### Post by kevdog on 2007-07-18
Try converting the files to pdf -- I cant remember where I found it but I think there is a tiff2pdf executable somewhere.  If you cant find it, you will have to do it in two steps tiff2ps ps2pdf.  Im using cygwin to help me.

---

