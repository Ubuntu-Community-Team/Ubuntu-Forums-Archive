---
title: "e-mail server marks my e-mail as containing a virus"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by matyasfalvi on 2008-12-22
Hi all!

I need help and I am really freaking out! :confused:

I sent an e-mail to a teacher of mine at school. This e-mail had a zip attachment (about 6 MB) containing 4 different document types: a pdf, a doc, an rtf and an odt. And the e-mail server at my school did the following to my e-mail:
> 
From: "Gyorgy Matyasfalvi" 
Subject: Algoritmusok jegyzet
Date: Mon, 22 Dec 2008 05:10:47 +0100
This mail contains a VIRUS: Zip.ExceededFileSize!
File: /var/mail/spam/kiraly/new/1229919078.H909908P3776.konig.cs.elte.hu

i.e it marked my e-mail as a virus. I know it says Zip.ExceededFileSize, but I mean how can I be certain that it is only the file size and that I really don't have virus. I know this is gonna sound crazy but I am going to ask cause if I have a virus than these are about the only places I could have gotten them from. So is it possible to get a virus, from unsupported updates (hardy-backports) or anything like that, or is it possible to get maybe a virus, through msn I am using pidgin for that? 

Thanx a lot in advance!


(merry xmas to all)

---

### Post by night_fox on 2008-12-22
No, dont worry, there is no way that these files could contain a virus. Your mail server is filtering your message because it assumes everything in a .zip file over a certain size is a virus. You should split it up and resend it. Unless you have somehow installed a virus under wine or have installed software from a repository that you really don't trust, then there is no way that you can have a virus on ubuntu.

---

### Post by mkvnmtr on 2008-12-22
There are tools in the repositories to scan things like your attachments for viruses. Why not download them and check? While it would not affect you on Ubuntu it is possible to have a virus on something in  your system that could be passedn on to a Windows machine.

---

### Post by matyasfalvi on 2008-12-27
Hi All!

Thanx everybody for the response. I did send the files one by one. It turned out that the mail server didn't like the .odt file.

> 
From: "Gyorgy Matyasfalvi" 
Subject: algoritmusok odt
Date: Mon, 22 Dec 2008 22:52:55 +0100
This mail contains a VIRUS: Zip.ExceededFileSize!
File: /var/mail/spam/magpact/new/1229982802.H21216P8329.konig.cs.elte.hu


The funny thing is that I didn't zip them this time I just simply attached the odt file to the e-mail. 

So after this I checked my computer for viruses with f-prot, and I didn't have any. I only have one file with an error :). 

So what do you think, what is happening here?

Thanx

---

### Post by Dr Small on 2008-12-27
> **matyasfalvi said:**
> 
So what do you think, what is happening here?

I think the mailserver is running clamscan (perhaps) with a whitelist of supported (non-executable) filetypes. Anything that does not meet the criteria (example: odt, exe, zip, bin, xcf) gets flagged as a potential virus. So basically, you have to pick and choose to see what filetypes are supported by the mailserver that do not get flagged as a virus.

Here is a list of extensions that should be accepted:
(txt, rtf, doc, pdf(?))

You could try renaming the files you are attempting to send to one of these extensions (as it is most likely scanning extensions, not MIME types) and see if it gets through.

That's about all I would know to try, for now.

---

### Post by matyasfalvi on 2008-12-27
Hi Dr. Small!

Yes you are right the .doc and the .pdf file did go through. Well I guess I just have to avoid sending .odt-s and that's about it.

Thanx for the help!

---

