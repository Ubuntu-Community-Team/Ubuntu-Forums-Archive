---
title: "creating md5 password"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by N-t-F on 2010-06-28
Hello all,

I know my question may look silly but how do you create md5 passwords in Ubuntu? With my old Slackware, I just used to type:

```
crypt password_in_clear_text
```

and it returned me the md5 encoded version that I could simply copy-paste to /etc/passwd if I wished so (or feed it to other scripts or even an ldif file to use with ldapadd, for instance). I think it was a perl script, but wouldn't bet on it.

But I've tried this on my new Ubuntu (10.04) and got an error message explaining that crypt was not present on the system and that I should install the mcrypt package. Alas! This package is deemed buggy and unmaintained, by its very description in the repository. O^o

Google search left me in the impression that each tool (slapd, grub, perl...) had its own function to do this. But I didn't find anything generic to the system, which I find quite disturbing and awkward.

So, please, is there an official way to get md5 passwords from clear-text ones in command line? :confused:

---

### Post by Bachstelze on 2010-06-28
There is no "official" way, whatever that means. You can use [font=monospace]makepasswd[/font]:

```
firas@tsukino ~ % echo "foo" | makepasswd --clearfrom - --crypt-md5
foo          $1$STwTCV9d$KoEL8Fj/r.a2aqQRoBlZz1

```

Also, such passwords should be copied in /etc/shadow, not /etc/passwd, and MD5 is not really considered secure anymore.

---

### Post by N-t-F on 2010-07-08
> **Bachstelze said:**
> Also, such passwords should be copied in /etc/shadow, not /etc/passwd
Doesn't work on a NIS server, as far as I know. Not that NIS could be considered secure, of course.

Anyway, merci beaucoup.

---

### Post by pabloab777 on 2011-03-02
An alternative:
```
echo "mypass" |md5sum
```

---

