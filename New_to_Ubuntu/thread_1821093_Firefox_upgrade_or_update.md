---
title: "Firefox upgrade or update"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by DaveMcC on 2011-08-08
Have thought about upgrading or updating Firefox 3.6 to either ver 4 or 5

I know there is no "check for update" in this version that I am using, I also know that some thing in the back ground has stopped working as a web site I check my ####### on, the sliding bars are no longer taking effect on the filters, (lucky Google chrome still does)

Any and all advise is welcome

Dave

:guitar:

Should have said I am using ver 10, 64bit here of Ubuntu

---

### Post by dniMretsaM on 2011-08-08
If you want to upgrade (Which I would highly recommend. You'll get TONS of features and more speed.), run this in terminal and you'll be upgraded to Firefox 5:
```
sudo add-apt-repository ppa:mozillateam/firefox-stable sudo apt-get update sudo apt-get upgrade sudo apt-get install firefox
```

---

### Post by DaveMcC on 2011-08-08
Error: need a repository as argument

Thats all that happen

Sorry know nothing about command line prompts

Dave

---

### Post by Redblade20XX on 2011-08-08
> **dniMretsaM said:**
> If you want to upgrade (Which I would highly recommend. You'll get TONS of features and more speed.), run this in terminal and you'll be upgraded to Firefox 5:
```
sudo add-apt-repository ppa:mozillateam/firefox-stable sudo apt-get update sudo apt-get upgrade sudo apt-get install firefox
```

 I agree fox5 is extremely quick! :D

---

### Post by dniMretsaM on 2011-08-08
> **DaveMcC said:**
> Error: need a repository as argument

Thats all that happen

Sorry know nothing about command line prompts

Dave

That's odd. Try running each command individually:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install firefox
```

---

### Post by DaveMcC on 2011-08-08
That ! I think done the trick, it all looks different, as long as I have password exporter I will be happy

The rest I do not care about

Thanking you

---

### Post by dniMretsaM on 2011-08-08
No problem. Glad I could help!

---

### Post by mikodo on 2011-08-08
> **dniMretsaM said:**
> If you want to upgrade (Which I would highly recommend. You'll get TONS of features and more speed.), run this in terminal and you'll be upgraded to Firefox 5:
```
sudo add-apt-repository ppa:mozillateam/firefox-stable sudo apt-get update sudo apt-get upgrade sudo apt-get install firefox
```

I use "&&" in between each command. Would that have made a difference?

---

### Post by dniMretsaM on 2011-08-08
Yeah probably. I just copied it from someplace in this format:
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install firefox
```

It didn't copy in that format and I forgot to change it. But yes, && would work as well.

---

