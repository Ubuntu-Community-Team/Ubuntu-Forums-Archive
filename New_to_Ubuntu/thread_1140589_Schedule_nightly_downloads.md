---
title: "Schedule nightly downloads"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-04-27
My friend (from around the world) regularly updates a server we share with files. The files are very big and I'd like them to download over night as soon as they appear.

The website basically lists all the various files on an http page.

So, what I would like to do is have a script that checks the page (at intervals), grabs the file and downloads it. However, I will not know the name of the EXACT name of the file, so it may be called: "TestData.28.04.2009.first", and I only know that it is called "TestData". Anyway to do this?

Thanks.

---

### Post by jimmy the saint on 2009-04-27
Maybe something like rsync?  I don't know how hard that would be to implement as I don't use it myself.  It is setup to sync files both locally and remotely though.

---

### Post by abhiroopb on 2009-04-27
I use rsync for backups but how would this work?

---

### Post by Didius Falco on 2009-04-27
I'd suggest using Wget. Here is some info about doing exactly the task you are after:

[http://lifehacker.com/software/downloads/geek-to-live-mastering-wget-161202.php](http://lifehacker.com/software/downloads/geek-to-live-mastering-wget-161202.php)

Alternatively, you could use Cron and script a task, but I think Wget would be easier to use - especially with the head start you'll get from the above info.

I hope this helps...

---

### Post by llamabr on 2009-04-27
Likewise, this is just what podcasts do.  the friend could set up an xml server, and you could get it with your favorite podcast software.

---

### Post by blueridgedog on 2009-04-27
+1 on wget.  Just put it in as a cron job and pull everything.

---

### Post by abhiroopb on 2009-04-27
Thanks for the advice, and while it seems promising, I think it would take a LOT of effort for me to read all the relevant information and figure out how to do this. I was looking for a simple gui tool. Something like specto ([http://code.google.com/p/specto/](http://code.google.com/p/specto/)) is what I had in mind.

---

### Post by llamabr on 2009-04-27
Using wget isn't going to be nearly as difficult as you think.  And once you've got this tool in your belt (so to speak), you'll find tons of uses for it.  It's an extremely powerful little app.

---

### Post by abhiroopb on 2009-04-27
Fair enough, I've been reading the man page and I've gotten ideas but I'd like some advice.

1. The http website has a long list of .doc files that I need to download. How do I select one file from the page? E.g. if the file is called test.doc on page [www.test.com](www.test.com)

2. There is a username and password associated with the page, how do you integrate that into the command?

3. What if I want to download files that are called test2.doc and test3.doc, but I only know that it will be called test*.doc (i.e. don't know what the number will be).

Any suggestions?

Thanks

---

### Post by Didius Falco on 2009-04-27
> **abhiroopb said:**
> Fair enough, I've been reading the man page and I've gotten ideas but I'd like some advice.

1. The http website has a long list of .doc files that I need to download. How do I select one file from the page? E.g. if the file is called test.doc on page [www.test.com]("http://www.test.com")

2. There is a username and password associated with the page, how do you integrate that into the command?

3. What if I want to download files that are called test2.doc and test3.doc, but I only know that it will be called test*.doc (i.e. don't know what the number will be).

Any suggestions?

Thanks

Download the PDF manual from here:

[http://www.gnu.org/software/wget/manual/wget.pdf](http://www.gnu.org/software/wget/manual/wget.pdf)

1. wget [http://www.files4me/shh/myporn.zip](http://www.files4me/shh/myporn.zip)

2. [http://user:password@host/path](http://user:password@host/path)

3. it supports the use of wildcards in several ways.

You can even use a timestamp, so it will check the file and only download it if it's newer or the filesize has changed.

I gleaned all the above in about 10 minutes of perusing the PDF manual.

---

### Post by Didius Falco on 2009-04-27
> **abhiroopb said:**
> Fair enough, I've been reading the man page and I've gotten ideas but I'd like some advice.

1. The http website has a long list of .doc files that I need to download. How do I select one file from the page? E.g. if the file is called test.doc on page [www.test.com]("http://www.test.com")

2. There is a username and password associated with the page, how do you integrate that into the command?

3. What if I want to download files that are called test2.doc and test3.doc, but I only know that it will be called test*.doc (i.e. don't know what the number will be).

Any suggestions?

Thanks

Download the PDF manual from here:

[http://www.gnu.org/software/wget/manual/wget.pdf](http://www.gnu.org/software/wget/manual/wget.pdf)

1. wget [http://www.files4me/shh/myporn.zip](http://www.files4me/shh/myporn.zip)

2. ```
http://user:password@host/path
```

3. it supports the use of wildcards in several ways.

You can even use a timestamp, so it will check the file and only download it if it's newer or the filesize has changed.

I gleaned all the above in about 10 minutes of perusing the PDF manual.

---

### Post by llamabr on 2009-04-27
from the manpage:

```
--user=user
       --password=password
           Specify the username user and password password for both FTP and HTTP file retrieval.  These
           parameters can be overridden using the --ftp-user and --ftp-password options for FTP connections and
           the --http-user and --http-password options for HTTP connections.

```

To your next question, how do you get doc2.doc and doc3.doc if you don't know the title?  I'm not sure how you get a file if you don't know what the title is.  If you want to run it every day, you could just tell it to read the time stamp, and get only the ones that are less than 25 hours old, say.  With the -N flag:

```
 -N
       --timestamping
           Turn on time-stamping.


```

As I say, wget is an extremely powerful little app, once you know your way around it.

---

