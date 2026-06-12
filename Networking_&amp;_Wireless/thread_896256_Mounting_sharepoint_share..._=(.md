---
title: "Mounting sharepoint share... =("
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by choey on 2008-08-21
At my company we use a sharepoint site to share documents. In particular, I need access to an excel spreadsheet. On Windows, if I use IE, it will ask whether I want to edit when I click on the document link (located at roughly [http://sharepoint/dev/docs/spreadsheet.xls](http://sharepoint/dev/docs/spreadsheet.xls)).

Now, I've seriously tried a dozen methods... I was hoping davfs2 would work, but apparently it doesn't for me. Here is what I get:

```
$ sudo mount -t davfs http://sharepoint/dev/docs /mnt/sharepoint/dev/docs
Please enter the username to authenticate with server http://sharepoint/dev/docs or hit enter for none.
Username: <my VALID username>
Please enter the password to authenticate user sukhyun.cho with server
http://sharepoint/dev/docs or hit enter for none.
Password: <my VALID password>
/sbin/mount.davfs: Mounting failed.
401 Unauthorized
```

I'm totally stumped. Is our sharepoint site not webdav or something...? I was about to mount box.net/dav this way, so it has to work, right?!

I even tried the console ftp client-looking thing for webdav... forgot its name, but it would not connect, either. I can download the file fine through the sharepoint site, but I just can't upload it. A way in open office to update a sharepoint file would be very nice, too...

Halp? :confused:

---

### Post by jimv on 2008-08-21
Try yourdomain\yourusername for the username.

---

### Post by choey on 2008-08-21
I've tried domain\username and domain/username... no luck. I've pretty much tried all permutations of credentials... hehe.

Thanks for the try tho. :cry:

---

### Post by jimv on 2008-08-21
Well, I'll try it at work tomorrow and let you know what happens.

---

### Post by choey on 2008-08-21
Ok, thank you for the help.

[In this post]("http://ubuntuforums.org/showpost.php?p=5635232&postcount=2"), the guy says you can join an active directory by joining the domain and adding the dns...

I didn't want to hijack the thread so didn't post there, but how would I go about doing what he said? Or does active directories not apply to sharepoint shares?

---

### Post by jimv on 2008-08-21
I tried and got the same error.  :(

---

### Post by choey on 2008-08-21
Dang... thanks for trying, tho. :sad:
I asked the corp ops to install me vmware with xp so that I can map the share to a drive, then share that drive between host/client OS's. I think that ought to work...

Until then, doze for me. :cry:

---

### Post by nirudha on 2008-11-24
I face the same scenario and the same error. And not just for sharepoint but for a plain IIS webdav share which I have been using in the past with older versions of Ubuntu as well as Windows.

Back to windows at work :)

> **choey said:**
> Dang... thanks for trying, tho. :sad:
I asked the corp ops to install me vmware with xp so that I can map the share to a drive, then share that drive between host/client OS's. I think that ought to work...

Until then, doze for me. :cry:

---

### Post by bfisk on 2009-03-25
I had to configure my sharepoint site to enable basic authentication.  I did this using IIS admin on my server, went to the sharepoint site, then authentication.  Just click on enable next to basic authentication.

Also, if you will be accessing a shared documents library, you should change the settings for your document library so that checkout is not required.  This will allow you to seemlessly copy and replace files.  It still does versioning!

One thing I am having problems with though is that I cannot see files/folders with spaces in them!  I have tried so many different things so if someone has a solution, please provide me with syntax and a sample.

I am about to implement sharepoint and this was one of my major stumbling blocks that was going to keep me from moving forward.  I got everything working on the mac side using the webdav client "cyberduck".  Now I just need to figure out this spaces in the file/folder problem!

---

