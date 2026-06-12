---
title: "Connecting DOS to Ubuntu"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by Patrick K on 2007-03-29
I have a situation that I'm not sure how to handle. I have a two computer network. One computer, named Little, runs on Windows 98/DOS exclusively. The other, named Big, is dual boot: Edgy (Gnome) and W98. I have an HP 1100 printer on a D-Link DI-704P router/printserver. Little can access the printer directly on the printserver in Windows. Big can access it from both Win and Ubuntu. Little cannot access it directly from DOS, it must go through Big.

On Little I have a DOS accounting program for my business. Right now, when I need a printout I must boot Big to Windows and use "Net" (on Little) to access Big and the printer. Changing accounting programs isn't going to happen. There are 15 years of data in it.  

What I'd like to do is access the printer from DOS on Little through Ubuntu on Big. That way I wouldn't need to boot Big to Windows just to print something from the DOS accounting program on Little. 

At this point I have not attempted networking the two computers using Linux. They are networked with Windows. Note that I want to keep the windows network working. 

I guess my question is, can a computer running DOS access a printer on a Linux box.

---

### Post by Ambimom on 2007-03-29
You can put logmein server on your windows machine at work and access it through your web browser on your linux machine.  

Logmein is free, though file sharing is only free for the first 14 days.  No problem really. When I want to share files  I  send myself gmail from which both linux and windows can download and upload.

[https://secure.logmein.com/go.asp?page=support_faq#basics-05](https://secure.logmein.com/go.asp?page=support_faq#basics-05)

---

### Post by koenn on 2007-03-29
So, you are sharing this printer on Big:Windows so you can print to it from Win98 / DOS. You can so the same on Big:Ubuntu if you install Samba on it so it can function as a (file- and) printer server. 

You'll need to find a howto - 
I found these but there might be others.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

You're mainly interested in a samba server and printer sharing - disregard stuff about file sharing and domain controllers. There's plenty people here who have set up samba so you can always come back with specific questions.

---

### Post by Patrick K on 2007-03-30
Thanks for the leads. I'll check them out. 

Just to clarify, the app I want to print from is a DOS app. It cannot access W98's file and print sharing whatsoever. The app has no networking ability of it's own. Right now the DOS "net use" command provides the link to the printerserver through Windows running on Big. Win98 on Little can access the printersever directly so printing from Windows on Little works fine. 

The two computers are in the same room using ethernet cable and the aforementioned D-Link router (I have to keep them separated for tax and business purposes).

"Net use" is mentioned only once in the links. Will "Net Use" and Samba connect?

---

### Post by koenn on 2007-03-30
DOS has no networking capabilities - what your doing now already  (I assume; correct me if I'm wrong)  is using Win98 network protocols (smb) to provide network access to the printerserver. The DOS application is not aware of any networking, it just prints to lpt1 (or something) which (in "real" DOS) would be a printerport on the PC itself - but you 've mapped lpt1 to a shared printer, using a ("DOS") command from Win98  - 'net use lpt1 \\Big\thePrinter" - so that's where the printjobs arrive.   The application is unaware of this - it has succesfully send its printjob to lpt1 and that's all that it cares about. 

For samba, all that matters is that you can create the share \\Big\thePrinter, and that it can process whatever is send to that share - i.e. that you're printer on Big:Ubuntu is set up correctly (driver, ...) and shared correctly. 

So, all in all, this should be do-able.

---

### Post by Patrick K on 2007-03-30
Yes, that is how "net use" is setup. I'll get started on setting this up. I'll read the pages you linked plus I ran across one specifically on Dos/Linux connectivity (if I can find it again). Thanks for your help. Hopefully, I can handle it from here.

---

