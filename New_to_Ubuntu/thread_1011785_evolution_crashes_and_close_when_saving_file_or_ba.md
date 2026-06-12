---
title: "evolution crashes and close when saving file or backup"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-12-15
evolution crashes and close when saving file or backup. What can i do to fix it ? how can i save my mail?
i am running evolution 2.12.1 and ubuntu 7.10. would anyone help me please? thanks!
here 's what i got when starting evolution from terminal 
> wong@wong-desktop:~$ evolution
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
wong@wong-desktop:~$ 


edit: firefox also crashes when saving / exporting the bookmarks. oh i just want to do a back up and everything crashes and close!!

---

### Post by Michael.Godawski on 2008-12-15
hi afeasfaerw23231233, 

make sure you have all updates installed for the package 
 evolution-data-server.

There seems to be a conflict between older versions of Evolutions.
Run in terminal:
```
sudo apt-get update
sudo apt-get upgrade
```

Also enable the proposed and backports update sources and check if there are any updates available.

---

### Post by afeasfaerw23231233 on 2008-12-15
i've just done the following but still doesn't work
> sudo apt-get update
sudo apt-get upgrade
please help! my mobo has problem and i have to replace it (i already bought a new one) i just want to back up my mail. many thanks!

---

### Post by howefield on 2008-12-15
Try running these command in terminal

```
cd Desktop
```

```
tar cvfz mybackup.tgz ~/.evolution
```

That should produce an archive on you desktop, change "mybackup" to whatever you want it to be. You can then copy/move the backtp to a safe place.

Edit :
Sorry just noticed you are running 7.10, the above works in 8.10. You might need other folders backed up as well as this one. I'll take a look and post back.

---

### Post by afeasfaerw23231233 on 2008-12-15
i've already run your command . does that .tgz contain all my mail archives? After a reinstallation of my system how can i import them? thanks so much for your help
that .tgz is about 80MB in size

---

### Post by afeasfaerw23231233 on 2008-12-15
bump

---

### Post by howefield on 2008-12-16
> **afeasfaerw23231233 said:**
> does that .tgz contain all my mail archives? After a reinstallation of my system how can i import them?

Yes, it is simply an archive of your evolution folder which contains your emails, accounts settings etc. Double click the file to open check you have everything you need.

As I said, I wrote my reply based on Intrepid, then noticed you are on Gutsy, so it might be slightly different. A google search would probably tell you.

To pack the file, open a terminal and navigate to where you have placed the .tgz file and type (change mybackup to whatever you named the file).

```
tar xvfz mybackup.tgz
```

Then move to it's rightful place.

---

