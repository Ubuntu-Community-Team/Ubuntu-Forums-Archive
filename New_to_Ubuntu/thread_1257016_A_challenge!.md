---
title: "A challenge!"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by filifunk on 2009-09-03
So I just downloaded this file that is supposedly a .zip file, but when I try to open it it says this:

[/home/petem/Desktop/clipse - EAF. DCtoBC.com.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/petemondejar/Desktop/clipse - EAF. DCtoBC.com.zip or
          /home/petem/Desktop/clipse - EAF. DCtoBC.com.zip.zip, and cannot find /home/petem/Desktop/clipse - EAF. DCtoBC.com.zip.ZIP, period.


I was just going to trash it, but I figured that someone on this forum would know how to get around this or even get a kick out of it?

---

### Post by geirha on 2009-09-03
See what the file command says about it. 
```
file '/home/petem/Desktop/clipse - EAF. DCtoBC.com.zip'
```

Most likely it's corrupt, or a html page (if you used the wrong url to download it with wget).

---

### Post by filifunk on 2009-09-03
> **geirha said:**
> See what the file command says about it. 
```
file '/home/petem/Desktop/clipse - EAF. DCtoBC.com.zip'
```Most likely it's corrupt, or a html page (if you used the wrong url to download it with wget).


I get this

```

/home/petemondejar/Desktop/clipse - EAF. DCtoBC.com.zip: Zip archive data, at least v1.0 to extract

```


So I have to update my unzipper to atleast v1.0?

---

### Post by Volt9000 on 2009-09-03
Since 'file' can ID this as a zip file, I would say that error means it's corrupt.

---

