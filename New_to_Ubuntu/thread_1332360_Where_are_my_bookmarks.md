---
title: "Where are my bookmarks?"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by vagelism on 2009-11-20
Hello to all.
I made an ordinary update in my Ubuntu and then I lost the firefox bookmarks. Every time I start the firefox , I got the message that is checking compatibility for my add ons. Then  I can browse the web but i do not have the bookmarks, and I can not apply any login screen like this one with my user  name and password.
Any Idea please?
I am new one so keep it simple.
THANK YOU FOR YOUR TIME.

---

### Post by danill2008 on 2009-11-20
What version of firefox and ubuntu are you using?

---

### Post by vagelism on 2009-11-20
> **danill2008 said:**
> What version of firefox and ubuntu are you using?

It is say that is the last one.
How can I watch this? is there any command?
thank you!!!

---

### Post by linux-hack on 2009-11-20
if you want to know your operating system try ```
uname
``` ...

---

### Post by HarrisonNapper on 2009-11-20
> **vagelism said:**
> It is say that is the last one.
How can I watch this? is there any command?
thank you!!!

To get the firefox version, go to Help>About Mozilla Firefox.

---

### Post by vagelism on 2009-11-20
I have the Mozilla 5.0 /3.0.15

---

### Post by lhb1142 on 2009-11-20
I hope I am interpreting your problem correctly. Evidently you have upgraded Ubuntu and in the process you have lost all your Firefox bookmarks.

If that is the case, and if you did not previously back up your bookmarks, then I am afraid they are indeed lost.

I regularly back up my bookmarks into a folder in Documents and I back ALL of my Documents, Music, Pictures, etc. to an external hard drive (actually THREE external hard drives!). That way there is no possibility of my losing my bookmarks.

To back up bookmarks go to Bookmarks -> Organize Bookmarks -> Import and Backup -> Backup. You will then see a file named < bookmarks-2009-11-20.json > (the date shown will be the current date). The destination folder will be the Desktop but you can change it to anything you wish. (I have a folder within Documents that I have labeled Mozilla Bookmarks and that is where I backup the .json file.)

Whenever I add new items to my bookmarks, I back it up; the .json file will contain the current date and I just delete the older one.

As I said, I also back this up to an external hard drive (along with everything else).

Then if, for some reason, I have to reinstall Firefox or I wish to transfer the bookmarks to Firefox on another computer, I merely plug in the external drive and import the .json file to Firefox; this will replace anything there (and if it is a new installation such as you have, there will be very little) with my desired bookmarks.

The process is actually quite simple and straightforward; it's far easier to actually accomplish than it is to read my instructions.

It appears to me that you may have irretrievably lost your Firefox bookmarks and will have to manually make them again. But if you follow my suggestions and instructions to back up your bookmarks, it won't ever happen again.

I hope this is of some help to you. ):P

Lawrence

---

### Post by philinux on 2009-11-20
> **vagelism said:**
> Hello to all.
I made an ordinary update in my Ubuntu and then I lost the firefox bookmarks. Every time I start the firefox , I got the message that is checking compatibility for my add ons. Then  I can browse the web but i do not have the bookmarks, and I can not apply any login screen like this one with my user  name and password.
Any Idea please?
I am new one so keep it simple.
THANK YOU FOR YOUR TIME.

Open a terminal Apps>access>terminal

```
find -name bookmarks-2009*
```

Post back the results.

---

### Post by vagelism on 2009-11-20
> **philinux said:**
> Open a terminal Apps>access>terminal

```
find -name bookmarks-2009*
```

Post back the results.

Thank you .
It works I found them....but when I try to import them i go the message Firefox could not complete the request.
any ideas?

---

### Post by silverglade00 on 2009-11-20
The posts above mine should help you either find your bookmarks or at least figure out that they are gone. To make sure this doesn't happen in the future, you could use XMarks plugin for Firefox. That's what I use and it is awesome! It will automatically sync your bookmarks to the Xmarks server and also sync them with any other computer you put Xmarks on with your login info.

---

### Post by 8isawesome on 2010-02-23
> **philinux said:**
> Open a terminal Apps>access>terminal

```
find -name bookmarks-2009*
```

Post back the results.
Thank you. The same thing happened to me and this found the backups that are thankfully set to store automatically.

---

