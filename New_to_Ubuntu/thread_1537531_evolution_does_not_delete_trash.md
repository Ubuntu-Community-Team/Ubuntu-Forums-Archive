---
title: "evolution does not delete trash"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by libihero on 2010-07-23
i've been trying to delete my trash in evolution, and every time i try the trash still remains :S

---

### Post by Zeike on 2010-07-23
Can you be more specific?

Are you using IMAP or POP?

If you're using IMAP dig around in the settings and make sure 'expunge on quit' or something like that is checked.  I think this will do what you want.

---

### Post by libihero on 2010-07-23
it's a POP :S

---

### Post by libihero on 2010-07-25
bump :(

---

### Post by libihero on 2010-07-28
bump :(

---

### Post by libihero on 2010-07-30
bump :(

---

### Post by Jazzy_Jeff on 2010-07-30
Sorry you are having this issue. I personally use IMAP and everything works great. Hopefully someone will have an answer for you here. Sorry I could not be of more help.

---

### Post by Michl on 2010-11-24
Well somewhere here there is a SOLVED thread for this
problem, But I cannot find it anymore.  But I just did
it and it worked.  

Close Evolution and Go to your home folder -> View ->
SHow hidden files.  Go to .evolution/mail/local and
delete all the files with these suffixes:

.index
.ev-summary
.cmeta

DO NOT DELETE and .data files.

I also went into the #evolution.sbd folder and
deleted the TRASH.cmeta file.

Reopen Evolution ... it will take some time now
because all the indexes will have to be redone.
But once it is open, everything will be there
but now you will be able to expunde Trash.

It worked for me, and that;s all I can say.  You
might want to back-up Evolution before you do it
in case you make any mistakes, but I didn't do
that.  Just be careful in what you delete.

Michael

---

### Post by Michl on 2010-11-24
Well somewhere here there is a SOLVED thread for this
problem, But I cannot find it anymore.  But I just did
it and it worked.  

Close Evolution and Go to your home folder -> View ->
SHow hidden files.  Go to .evolution/mail/local and
delete all the files with these suffixes:

.index
.ev-summary
.cmeta

DO NOT DELETE and .data files.

I also went into the #evolution.sbd folder and
deleted the TRASH.cmeta file.

Reopen Evolution ... it will take some time now
because all the indexes will have to be redone.
But once it is open, everything will be there
but now you will be able to expunde Trash.

It worked for me, and that;s all I can say.  You
might want to back-up Evolution before you do it
in case you make any mistakes, but I didn't do
that.  Just be careful in what you delete.

Michael

---

### Post by Michl on 2010-11-24
Well somewhere here there is a SOLVED thread for this
problem, But I cannot find it anymore.  But I just did
it and it worked.  

Close Evolution and Go to your home folder -> View ->
SHow hidden files.  Go to .evolution/mail/local and
delete all the files with these suffixes:

.index
.ev-summary
.cmeta

DO NOT DELETE and .data files.

I also went into the #evolution.sbd folder and
deleted the TRASH.cmeta file.

Reopen Evolution ... it will take some time now
because all the indexes will have to be redone.
But once it is open, everything will be there
but now you will be able to expunde Trash.

It worked for me, and that;s all I can say.  You
might want to back-up Evolution before you do it
in case you make any mistakes, but I didn't do
that.  Just be careful in what you delete.

Michael

---

### Post by Michl on 2010-11-24
Well somewhere here there is a SOLVED thread for this
problem, But I cannot find it anymore.  But I just did
it and it worked.  

Close Evolution and Go to your home folder -> View ->
SHow hidden files.  Go to .evolution/mail/local and
delete all the files with these suffixes:

.index
.ev-summary
.cmeta

DO NOT DELETE and .data files.

I also went into the #evolution.sbd folder and
deleted the TRASH.cmeta file.

Reopen Evolution ... it will take some time now
because all the indexes will have to be redone.
But once it is open, everything will be there
but now you will be able to expunde Trash.

It worked for me, and that;s all I can say.  You
might want to back-up Evolution before you do it
in case you make any mistakes, but I didn't do
that.  Just be careful in what you delete.

Michael

---

### Post by libihero on 2010-11-25
i should mark this as solved, i went back to lucid and recently reinstalled maverick to see if there was any updates and it works now :)

---

