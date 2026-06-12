---
title: "Jailing a user to a folder"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by OneLine on 2010-09-30
Hi, I've given folders to my friends at /var/www/their-name-here/ but I would like to lock them into their folders so they can't read eachothers directories or my files using a clever php script, can anyone help please, thank you :popcorn:.

p.s. is it possible to do it without being in root (sudo su), using the command line, i ask as I would like to make a nice little script. Thank You.

---

### Post by OneLine on 2010-10-06
Anyone, Please?

Thank You.:KS

---

### Post by eakron on 2010-10-06
How do they access the folders? SMB, FTP or SSH?

Since you want to put it in a script I assume you want the command line way of doing it. Just clarifying to help.

---

### Post by OneLine on 2010-10-06
> **eakron said:**
> How do they access the folders? SMB, FTP or SSH?

They access by FTP,

> **eakron said:**
> Since you want to put it in a script I assume you want the command line way of doing it. Just clarifying to help.

Yes please,

Thank You :KS

---

### Post by OneLine on 2010-10-07
SFTP is what I meant to say.

Thank You :KS

---

### Post by bluefrog on 2010-10-07
[http://groups.gandi.net/en/topic/gandi.en.hosting.expert/22659](http://groups.gandi.net/en/topic/gandi.en.hosting.expert/22659)

---

### Post by OneLine on 2010-10-07
> **bluefrog said:**
> [http://groups.gandi.net/en/topic/gandi.en.hosting.expert/22659](http://groups.gandi.net/en/topic/gandi.en.hosting.expert/22659)

This isn't a step by step on how to set it up though, it looks like someone having the problem of setting it up :confused: :(

---

### Post by psusi on 2010-10-07
Set permissions on the files the way you want them to be.  By default normal users can not write anywhere outside their home folder.  If you don't want other users reading your personal files, then change the permissions on your home folder.

---

### Post by OneLine on 2010-10-07
> **psusi said:**
> Set permissions on the files the way you want them to be.  By default normal users can not write anywhere outside their home folder.  If you don't want other users reading your personal files, then change the permissions on your home folder.

Hi, I can't see how setting permissions would solve this 'problem' :confused:.

---

### Post by Locke_99GS on 2010-10-07
Removing rwx permission recursively for g and o on all user folders would prevent other users from getting directory listings, as well as from reading or writing files inside those folders.

---

### Post by psusi on 2010-10-07
> **OneLine said:**
> Hi, I can't see how setting permissions would solve this 'problem' :confused:.

Ummm... because if they don't have permission to access your files, then... they can't access your files.

---

### Post by redmk2 on 2010-10-08
> **OneLine said:**
> This isn't a step by step on how to set it up though, it looks like someone having the problem of setting it up :confused: :(
But it does lead you to [**_[COLOR="Green"]this article[/COLOR]_**]("http://blogs.techrepublic.com.com/opensource/?p=229") which explains it pretty well.

---

### Post by OneLine on 2010-10-08
> **redmk2 said:**
> But it does lead you to [**_[COLOR=Green]this article[/COLOR]_**]("http://blogs.techrepublic.com.com/opensource/?p=229") which explains it pretty well.

Hi, I didn't see that before, sorry, Thank You.

One thing, please correct me if i'm wrong, usermod, chown & chmod all need to be run as root?

---

### Post by da burger on 2010-10-08
> **OneLine said:**
> Hi, I didn't see that before, sorry, Thank You.
 
One thing, please correct me if i'm wrong, usermod, chown & chmod all need to be run as root?
 
Depends. On your own files you can run it without sudo. However to run it on someone elses files you will need root. When you think about it this makes sense. Otherwise anyone could stop you reading your own files just by changing the permissions.

---

### Post by OneLine on 2010-10-08
> **da burger said:**
> Depends. On your own files you can run it without sudo. However to run it on someone elses files you will need root. When you think about it this makes sense. Otherwise anyone could stop you reading your own files just by changing the permissions.

Thank You.

I wonder if there is a way to virtualise the user's instead.

---

