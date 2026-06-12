---
title: "Problems with &quot;Open Office Writer&quot;"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by BSG Fan on 2010-05-31
Hello people
long time since my last time here.

Yesterday installed the new Ubuntu 10, wonderful.

I have problems with the "Open Office Writer".
Every time I open it (a document already saved in "ODF" (I thought was ODT?)
the document comes in "Read-only" format!
I don't know how to write or work in it more.

All started because my pc often get frozen and I have to re-start it.
When I did that yesterday my 500 something kb doc did not open and a window told me that is had macros, bla blah and it deleted the file + I did not have permission (I am the owner) to open it.  So I lost the entire document after one year of work!  :(  and there were not back-up.

1- How can I restore the 'writable' status to Open Office Writer?

2- How can I modify/restore/fix/open/etc etc my own documents when I have not the privileges of the creator?

Help, please

Thanks in advance!

:confused:

---

### Post by yeats on 2010-05-31
> (a document already saved in "ODF" (I thought was ODT?)

ODF = open document format, the more generic term for the OO.org format
ODT = open document text - there's also ODS (spreadsheet), ODP (presentation) and ODG (graphics)

This may help you with the read-only issue:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=9&t=967](http://user.services.openoffice.org/en/forum/viewtopic.php?f=9&t=967)

---

### Post by HereInOz on 2010-05-31
Is it every document, or just this one document?  If it is just this one document, try saving it as a different file name (you have probably already tried this, but it is worth a mention).  

If it is all of them which open read only, then it may be a permissions issue within Ubuntu, and I can't think of anything else which may be causing this.

---

### Post by drs305 on 2010-05-31
Are these documents on another partition? As HereInOz said, it could be a permission problem if they are on another partition and you haven't given yourself access to the files since your new installation.

If you don't understand permissions or need help, post the following, substituting the actual path and folder in which the files are located:
```
ls -la /*path*/*folder*
```

---

### Post by BSG Fan on 2010-05-31
Hello everybody.
Thanks a lot for your replies.

Ok, as HereInOz said: yes, I did that and the problem was solved the first time but the problem came back.  Weird.  So, I copied all the document (400 pages) and pasted it in a new "openoffice writer" with a different name.
and it worked.  It was awful because the doc I used was the one used 3 days ago.

As I said everything was because my pc freezes often and it "converted" my document in one "corrupted" and unsaved to be opened.  Damn, it said macros.
Was the macros the drawings I created in it?  How they can be harm for me?

The doc with the "write-only" problem was only one doc in specific.

I want to thanks **HereInOz**, **drs305** and **chrissharp123** for all the help. You guys rock!

ur Ubuntu fellow,
BSG fan
:guitar:

---

### Post by edmonds on 2010-06-04
Since upgrading  to Lucid Lynx my Openoffice documents saved as .doc appear blank when sent to clients and friends and opened in  MS Word.
Any ideas?
tom

---

