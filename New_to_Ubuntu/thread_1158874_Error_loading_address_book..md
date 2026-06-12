---
title: "Error loading address book."
date: 2009-05-14
forum: New to Ubuntu
---

### Post by TRANQU111TY on 2009-05-14
I get this error message after I installed 9.04, restored my backed up Evolution from 8.10 and tried to open contacts. 

"**Error loading address book.**"
"This address book cannot be opened.  Please check that the path /home/username/.evolution/addressbook/local/system exists and that permissions are set to access it."

Thanks for reading

---

### Post by nandemonai on 2009-05-14
> **TRANQU111TY said:**
> I get this error message after I installed 9.04, restored my backed up Evolution from 8.10 and tried to open contacts. 

"**Error loading address book.**"
"This address book cannot be opened.  Please check that the path /home/username/.evolution/addressbook/local/system exists and that permissions are set to access it."

Thanks for reading

Just a stab in the dark but have you checked to see if the dir exists in your home directory and you have the appropiate permissions on it?

```
ls -l ~/.evolution/addressbook/local/system/
```

Should return something like this..

```
-rw-r--r-- 1 nandemonai nandemonai 32768 2009-04-24 19:53 addressbook.db
-rw-r--r-- 1 nandemonai nandemonai   173 2009-04-24 19:53 addressbook.db.summary
```

---

### Post by TRANQU111TY on 2009-05-14
> **nandemonai said:**
> Just a stab in the dark but have you checked to see if the dir exists in your home directory and you have the appropiate permissions on it?

```
ls -l ~/.evolution/addressbook/local/system/
```

Should return something like this..

```
-rw-r--r-- 1 nandemonai nandemonai 32768 2009-04-24 19:53 addressbook.db
-rw-r--r-- 1 nandemonai nandemonai   173 2009-04-24 19:53 addressbook.db.summary
```

It came up with
```

-rw-r--r-- 1 t t 3624960 2009-04-24 21:05 addressbook.db
-rw-r--r-- 1 t t   18330 2009-04-24 21:05 addressbook.db.summary
```

---

### Post by nandemonai on 2009-05-14
Is 't' your username? If so it looks Ok to me.

---

### Post by TRANQU111TY on 2009-05-16
> **nandemonai said:**
> Is 't' your username? If so it looks Ok to me.

Yep t is the username/login.

---

### Post by nandemonai on 2009-05-16
> **TRANQU111TY said:**
> Yep t is the username/login.

Hmm, well I don't use Evolution myself so not too sure. Looks like it does here though so not sure what to tell you. Maybe someone else can chime in with some other suggestions?

---

### Post by TRANQU111TY on 2009-05-29
I figured out the problem.

This is the error message:

```
This address book cannot be opened.  Please check that the path /home/**tim**/.evolution/addressbook/local/system exists and that permissions are set to access it.
```

But the folder that contains the addressbook is in /home/**[COLOR="Red"]t[/COLOR]**/.evolution/addressbook/local/system

How can I fix this?

Thanks for reading!

---

### Post by TRANQU111TY on 2009-05-30
Bump

---

