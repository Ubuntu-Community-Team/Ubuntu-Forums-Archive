---
title: "what ubuntu version I'm running?"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by sallam on 2010-10-09
Greetings

I'm exited that finally I will be able tomorrow to run the release version of 10.10, no more beta.
And I was wondering..
From where do I get to know what ubuntu version is running in my laptop right now?
Originally, I installed 10.10 Beta, and I made the update manager's setting to auto update (download all updates in the background).
It says that my sytem is up-to-date, but it doesn't show me the version I'm on now..

---

### Post by HermanAB on 2010-10-09
$uname -a

should give you some clue.

---

### Post by sallam on 2010-10-09
$uname -a
-a: command not found

---

### Post by wilbuzz2 on 2010-10-09
go on system monitor then its the first tab thats how i did it when the beta version of 9 was out

---

### Post by howefield on 2010-10-09
Try it with just

```
uname -a
```

or

```
lsb_release -a
```

If you have kept the Beta up to date, you'll most likely already the final version :)

---

### Post by sallam on 2010-10-09
It said:
> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

is maverick the beta version?

---

### Post by howefield on 2010-10-09
If I remember correctly, were you still running the Beta, the description would read - Ubuntu 10.10 development branch - (something like that).

The words "development branch" are dropped for final release.

I'm sure someone can correct me if I got that wrong.

---

