---
title: "How do i: serve applications"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by TechDragon on 2009-01-27
I am using Ubuntu and have a few windows applications that I still utilize.  I want to start a vm and then serve the application to my desktop.  How do I do this?

---

### Post by XanTrax on 2009-01-27
> **TechDragon said:**
> I am using Ubuntu and have a few windows applications that I still utilize.  I want to start a vm and then serve the application to my desktop.  How do I do this?

I am guessing you mean wine?  I dont exactly what you mean but...

[www.winehq.com](www.winehq.com)

for developmental releaes (I use them, still very stable)

or

```
sudo apt-get install wine
```

for Ubuntu supported version

That application will allow you to run most Windows applications in linux.  Some might not work so check in [http://appdb.winehq.com](http://appdb.winehq.com) so see which applications you might be porting.

If wine doesnt work for you, you can always try virtualbox

[www.virtualbox.org](www.virtualbox.org) 

for latest

or

```
sudo apt-get install virtualbox-ose
```

I belive the command is, downloads and installs Ubuntu's supported version.

---

### Post by TechDragon on 2009-01-27
I am using vmware and want to call programs to be used from the windows vm and displayed on the linux desktop.  So I dont have to flip from vm to linux over and over.

Kinda like citrix

---

### Post by XanTrax on 2009-01-27
> **TechDragon said:**
> I am using vmware and want to call programs to be used from the windows vm and displayed on the linux desktop.  So I dont have to flip from vm to linux over and over.

Kinda like citrix

Understandable.  I think it would be much easier and less intensive if you gave wine a try.  By intensive I mean wine does not virtualize or emulate the environment of windows rather than utilizing Linux APIs to create their own communication pipes between the software.

Have you tried Wine or checked the AppDB for your applications to see if you can even give it a try?

Im not trying to steer you from your any of your objectives, just providing my opinionated solutions that I think are good alternatives. Dont want my posts to come off as snotty or anything :p.

---

