---
title: "Java 5 - error 9"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Xoanan on 2009-02-14
Hi All

This error I encountered is new, but fortunately (or unfortunately) it does not appear to generate a crash report

```
Setting up sun-java5-doc (1.5.0-16-3) ...
[/tmp/jdk-1_5_0-doc.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /tmp/jdk-1_5_0-doc.zip or
        /tmp/jdk-1_5_0-doc.zip.zip, and cannot find /tmp/jdk-1_5_0-doc.zip.ZIP, period.
dpkg: error processing sun-java5-doc (--configure):
 subprocess post-installation script returned error exit status 9

```

Any ideas?

:popcorn:

---

### Post by zvacet on 2009-02-14
How did you try to install it? Is there any special reason to install sun-java5 when you have sun-java6 in synaptic?You have to accept user agreement.

---

### Post by Xoanan on 2009-02-14
Actually, I'm not trying to install java5, I already have it. I was trying to get around the java update bug that has plagued more than a few people.  

So, I made sure the doc was owned by root.root and I copied it to the temp folder.

Now that that bug is gone, I have run into this one.:popcorn:

---

### Post by Xoanan on 2009-02-15
Well, now the original error returned..bummer

---

### Post by Xoanan on 2009-02-15
Errors all fixed now!  thanks!

---

