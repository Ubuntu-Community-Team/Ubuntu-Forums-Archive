---
title: "Automatic Samba permissions"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by Pas_sa on 2011-01-25
Hi guys,

I have a "dropbox" share on my Ubuntu powered server. When Windows copies a file to the share, the permissions are set so only that Windows user can edit or delete the file.

How can I set up the share so any files copied automatically have permissions allowing any unauthenticated user to do anything? (ie fully open).

---

### Post by Pas_sa on 2011-01-26
Bump.. seems to be even more arbitrary than I thought - I copied over a whole bunch of movies to the server today (through Ubuntu itself, off a removable HDD), a small handful of them had permissions locked after copying.

Is there a way to automatically change any rogue permissions within a directory I choose so that it and its contents are always open? Short of doing it manually myself all the time (not ideal).

---

### Post by Morbius1 on 2011-01-26
>  How can I set up the share so any files copied automatically have  permissions allowing any unauthenticated user to do anything? (ie fully  open).Instead of changing permission force every user to look the same. It sounds like you set up a guest accessible share so just add the following to the share definition:
```
force user = nobody
```[COLOR=Blue][I]I'm assuming you're using the default guest account of "nobody".

[/I][COLOR=Black]Then restart samba:[COLOR=Blue][/COLOR][/COLOR][/COLOR]```
 sudo service smbd restart*
```*[COLOR=Blue][COLOR=Black][COLOR=Blue][/COLOR][/COLOR][/COLOR]

---

