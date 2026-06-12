---
title: "ClamAV"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-05-13
I thought I installed it. But I can't find it anywhere. I did a command to install it, that I found off a website. And it seemed to work in the terminal, but I don't see the program anywhere. Did I skip a step? The command was something like sudo get-update install clamav .

---

### Post by theozzlives on 2009-05-13
```
sudo apt-get install clamav
```
```
mkdir /tmp/virus
```
```
clamscan -ri --move=/tmp/virus /home/username/
```

---

### Post by qamelian on 2009-05-13
By default, ClamAV is a command line tool and therefore, doesn't appear in you menus. If you want a GUI for it, you'll need to install clamtk.

---

### Post by HermanAB on 2009-05-13
Howdy,

ClamAV consists of programs like clamd and freshclam.  To find it, use the find command or heaven forbid, read the documentation.

This will find it for you:
$ find / -name clamd

However... Why do you want to install clamav?  The normal use for clamav is as part of an email server.  If you are not serving email, then you probably don't need it.

---

### Post by Ericyzfr1 on 2009-05-13
You can also look at Avast, it is free and comes with a GUI. I used Clamav a couple of years ago, it was ok. I think Avast is more convenient.

---

### Post by kakashi_12 on 2009-05-14
Email server? I was told it was an anti-virus. And my teacher told me it was the best anti-vrus for linux. I had him as my teacher in my Linux class.

---

### Post by aimpau on 2009-05-14
Yes, if you are running an email server that scans emails for malware and viruses.

---

### Post by NHArticleTen on 2009-05-14
> **kakashi_12 said:**
> Email server? I was told it was an anti-virus. And my teacher told me it was the best anti-vrus for linux. I had him as my teacher in my Linux class.

yes, it's probably a good idea not to pass those buggers on...

I like clamav

---

### Post by 3rdalbum on 2009-05-14
I'd just like to clarify something:

You only need an anti-virus program on Linux if you want to scan for Windows viruses. There are no Linux viruses; at least, there haven't been any for years.

That's why Clam AV is an anti-virus designed for use on an e-mail server; because having an anti-virus program on an e-mail server should stop Windows viruses from getting to Windows machines over e-mail.

You can install the "clamtk" package if you want to run a scan of your own system or a local hard drive; but there's absolutely no chance at all that you have any Linux viruses. I've been on Linux for nearly 4 years without malware. My father's Windows machine hasn't fared so well.

---

### Post by cneil on 2009-05-14
I think that you should clarify.  In Linux, unlike Windows, you won't get a virus from doing innocent things like surfing websites or viewing jpegs. Also if you are getting your software from reliable sources, you don't have to worry about rootkits, weird commercial driver software, and the like.... Windows users face these problems all of the time.  

However, it is entirely possible for someone to write some script or program that does things that you don't really like. But unless you're running as the system administrator/root/super user the worst thing they can do is corrupt data in your home directory.  It's not like windows where it could damage everything on your system.

The lesson: always know what you are clicking when selecting "Yes" or "Grant Permission" or putting in your root password.

---

### Post by kakashi_12 on 2009-05-14
not never a virus for linux, just hardly ever.

---

### Post by XCan on 2009-05-14
To keep on topic, there is a very handy plugin for nautilus called 'nautilus-clamscan'. Basically it lets you right click on, for example, a directory and select "Scan for viruses". Very handy for me when I'm about to run something through Wine.

---

### Post by kakashi_12 on 2009-05-14
cool, what's the cmd to dwnld that one?

---

### Post by XCan on 2009-05-14
sudo apt-get install nautilus-clamscan

---

### Post by JEBB on 2009-05-17
With Linux or Mac OSX you don't have to worry about viruses; with Windows you do.  That is a major reason why you don't want to do Windows.

---

### Post by kakashi_12 on 2009-05-26
with an  anti-virus in linux, will it scan ONLY for linux viruses, or does it scan for windows viruses too. it would make sense to only do for linux, but if you want to share your files with windows then, ya know.

---

### Post by Paqman on 2009-05-26
> **kakashi_12 said:**
> with an  anti-virus in linux, will it scan ONLY for linux viruses, or does it scan for windows viruses too. it would make sense to only do for linux, but if you want to share your files with windows then, ya know.

It'll only scan for Windows ones, that's what it's for. 

All known vulnerabilities to Linux viruses are patched in the kernel or the apps that those viruses would exploit, so there's no need for the antivirus package to protect against them.

---

### Post by Kevbert on 2009-05-26
You only need antivirus software if you're either emulating Windows/DOS with something like DOSBox or if you're sharing data files with Windows. Any viruses will be Windows ones at present as there are no Linux viruses out in the wild. If you have clamav you may want to install the graphical front end clamtk (see [COLOR="Red"][this]("http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html")[/COLOR]).

---

### Post by egalvan on 2009-05-26
> **XCan said:**
> , there is a very handy **plugin for nautilus called 'nautilus-clamscan'**.
 it lets you right click on a directory and select "Scan for viruses".
 Very handy

> **XCan said:**
> **sudo apt-get install nautilus-clamscan**

Under **Hardy 8.04.2** I get this error.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nautilus-clamscan

```


Is this perhaps for a newer version (8.10 or 9.04) ?

---

### Post by Kevbert on 2009-05-26
You can get nautilus-clamscan from [COLOR="Red"][here]("https://launchpad.net/nautilus-clamscan/+download")[/COLOR].

---

### Post by Saghaulor on 2009-05-26
> **Paqman said:**
> It'll only scan for Windows ones, that's what it's for. 

All known vulnerabilities to Linux viruses are patched in the kernel or the apps that those viruses would exploit, so there's no need for the antivirus package to protect against them.

There is a paradigm shift involved here.

The OP is accustomed to a world in which developers are okay with vulnerabilities and broken code. So more developers write code that works to blanket the aforementioned shoddy code from bad guys. 

We're accustomed to a world in which the craftsman takes pride in his/her product. S/He builds it to last.

This is not to say that Linux developers are without mistake, but generally speaking, when the mistake is pointed out, they handle their business instead of waiting for another developer to make a buck on producing a product that is a band-aid on a shotgun wound.

kakashi_12, we're working in a different model. It's not about kill or be kill, it's about helping each other as best we can.

Consequently, if we're going to be doing file sharing with any Windows users, we should use and antivirus product to ensure their safety.

---

### Post by wizard10000 on 2009-05-26
Mod parent up!

:)

---

### Post by XCan on 2009-05-26
> **egalvan said:**
> Under **Hardy 8.04.2** I get this error.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nautilus-clamscan

```


Is this perhaps for a newer version (8.10 or 9.04) ?

I am using 9.04 which might explain it. But it isn't hard to install it manually through the link Kevbert provided either. :)

---

### Post by kakashi_12 on 2009-05-27
yes i understand the helping each other out part. that's what linux is all about, open source. i know that, i had a linux class. anyway... that's cool that linux takes care of its virus's through their updates/patches when there is one, since it rarely happens. that makes sense. cool, thanks guys.

---

