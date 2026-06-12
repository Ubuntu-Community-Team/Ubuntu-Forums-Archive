---
title: "Aircrack-ng - buddy-ng and easside-ng missing"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by morpheus063 on 2009-09-28
Hi All,

I have installed aircrack-ng using 

```
sudo apt-get install aircrack-ng
```However, i cannot find buddy-ng and easside-ng.

Any clue?

---

### Post by kambrik on 2009-09-28
Are those included in that distro package?  I would suggest downloading the source and compiling yourself.  Some of the features may not be included in the distro package due to the programs not yet being tested fully on the distro.

Do a apt-cache search aircrack-ng and see what version its using.  Then compare it to the version on their site.  From experience though I would download the source and compile it.

---

### Post by northern lights on 2009-09-28
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
Not in the repos.

What do you want to use the app for anyhow?
...

---

### Post by morpheus063 on 2009-09-28
Thanks, issue resolved, compiled from source.

---

