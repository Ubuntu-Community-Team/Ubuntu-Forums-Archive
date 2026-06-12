---
title: "Installing Opera in Jaunty"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Orographic on 2009-07-22
> **Sarai the Geek said:**
> You should install Opera from a repository so that you can easily get updates for it.

Add this to your software sources:
```
deb http://deb.opera.com/opera/ stable non-free
```

Then add the GPG key:
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```

Finally...
```
sudo apt-get install opera
```


I followed that exactly in Jaunty and this is what I got. Opera wouldn't install...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate

---

### Post by cardpogi on 2009-07-22
the opera repo seems dead...

---

### Post by cardpogi on 2009-07-22
and sorry for double post but just checked the webpage and there a version for jaunty now..

---

### Post by Orographic on 2009-07-22
Thanks for that guys, appreciate it. We have a new puppy in the household so couldn't get back to this last night.

I might just try the deb approach now.

---

### Post by meeples on 2009-07-22
the opera deb added the repo for me btw. just thiought you should know

---

### Post by Orographic on 2009-07-22
Thanks for that. So does that mean it will just update as per other programs in synaptic?

---

### Post by LookTJ on 2009-07-22
> **Sarai the Geek said:**
> You should install Opera from a repository so that you can easily get updates for it.

Add this to your software sources:
```
deb http://deb.opera.com/opera/ stable non-free
```Then add the GPG key:
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```**Update/reload repository: ```
sudo apt-get update
```**Finally...
```
sudo apt-get install opera
```
This guide is missing one little part :)

---

### Post by aysiu on 2009-07-22
> **Sarai the Geek said:**
> Repo installs are also significantly easier to uninstall...
Not really.

If you manually install a .deb, it shows up in Synaptic, and you can just uninstall it the same way you would a .deb from a repository.

To the OP: download the .deb file from the Opera website and double-click it.

---

### Post by Orographic on 2009-07-22
I downloaded the deb and double clicked on it and all is running fine now although its not showing up in synaptic or add/remove.

Do I need to do anything in Software Sources etc?

I have just created a Clonezilla image of my whole system prior to Opera being installed, so there is no major problem. I will mostly only use Opera for viewing my router settings page which ordinarily needs Internet Explorer to open it but Opera will also open this settings page.

---

