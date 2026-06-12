---
title: "Ubuntu 10.10 BETA Software Center"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by Toshley on 2010-10-01
I noticed that when you download anything now, it's redirected to the Ubuntu Software Center, I was wondering if there was a way to revert it back to the old way (aside from downgrading to 10.04 LTS) where I can install the file via the Package Manager?

Thank you in advance.

---

### Post by andrewthomas on 2010-10-01
Can't you just save the file,then right-click on it and choose what you want to do?

---

### Post by Toshley on 2010-10-01
I was looking around for the "Open with" option but Ubuntu Software Center is the only option, am I missing something? I'm sorry if this is a stupid question.

---

### Post by ankspo71 on 2010-10-01
hi,
Gdebi is the name of the package you need to accomplish installing deb packages graphically without using the Software Center. You might need to install it though, if it is not already installed. I don't know how to make it the default/permanent package handler though, except for maybe right clicking on the file and choose open with, etc.
> 
In Ubuntu 10.10 Maverick Meercat Gdebi is replaced by the Ubuntu Software Center. The Ubuntu Software Center can download the required packages.
[http://en.wikipedia.org/wiki/Gdebi](http://en.wikipedia.org/wiki/Gdebi)

---

### Post by Toshley on 2010-10-01
Thank you both so much!

---

### Post by theozzlives on 2010-10-01
> **Toshley said:**
> Thank you both so much!

I ran into that problem also, I just dropped to the CLI and did:
```
sudo dpkg -i <nameoffile.deb>
```

Worked like a charm!

---

### Post by coffeecat on 2010-10-01
> **Toshley said:**
> I noticed that when you download anything now, it's redirected to the Ubuntu Software Center

I have to ask: is there a problem with that? As others have said, installing gDebi gives you the old way of doing it, but Software Centre does a good job of installing downloaded debs.

---

### Post by Dyegov on 2010-10-01
> **coffeecat said:**
> I have to ask: is there a problem with that? As others have said, installing gDebi gives you the old way of doing it, but Software Centre does a good job of installing downloaded debs.

I completely agree with this comment. Some people may be too purist and want to do it the old way, but I don't see anything wrong with the SC.

---

### Post by qamelian on 2010-10-01
> **coffeecat said:**
> I have to ask: is there a problem with that? As others have said, installing gDebi gives you the old way of doing it, but Software Centre does a good job of installing downloaded debs.
For one thing, gdebi is a heck of a lot faster than USC. In the time it takes USC to open, I can have the same app commpletely installed in gdebi and be using it. I've actually time the two methods on the same laptop and USC sometimes takes as much as 4 times longer to install the same app.

---

