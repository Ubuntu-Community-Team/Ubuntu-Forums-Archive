---
title: "Installing MS Access in wine"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by longtom on 2009-02-10
Hi,

before I throw myself into the huge adventure of installing wine and than install something else through wine, I'll knock on the door of those, who might have done it all before.

Now - here's the plan:

I have a somewhat dusty, but still functional MS Office 2000 installation set.  Since I'm struggling to read or work with excisting mdb files (and there is no way I sit for weeks to start at 0 again) and in my desire to find out, to what extend I'll be able to migrate to Ubuntu, I have the following question:

Has somebody successfully installed Access (or any other MS Office aplication for that matter) through wine?

If yes, a description of the process for a keen but wet Ubuntu greenhorn will be highly appreciated.

Thank you and greetings

longtom

---

### Post by yeats on 2009-02-10
Here's the Wine AppDB page for Access

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=12]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=12")

It would be my assumption that Access (or any MS Office product) will NOT work, because MS Office is so integrated with the Windows platform and makes so many system calls that Wine simply can't emulate.  That said, have you tried OpenOffice Base?  I have not used either Access or OO Base enough to recommend either over the other, but Base might be enough for you to at least get work done.

---

### Post by yeats on 2009-02-10
> before I throw myself into the huge adventure of installing wine and than install something else through wine, I'll knock on the door of those, who might have done it all before.

Oh - and installing Wine is VERY easy.  The best way to do it is here:

[http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

Have fun :-)

---

### Post by longtom on 2009-02-10
Hi chris

yes, I considered the other programs you are mentioning.  None of them can do anything meaningful with an MS Access file, neither read, convert or anything else in that direction.

What you said about the MS Office applications doesn't fill me with a great amount of hope.  But I'll have a go anyway.  

If that doesn't work I guess I'm doublebooting forever....

greetings

lt

---

### Post by jloveless on 2009-08-07
Praytell, what success or lack thereof have you had with Access under Wine?
Appreciated.

Jon

> **longtom said:**
> Hi chris

yes, I considered the other programs you are mentioning.  None of them can do anything meaningful with an MS Access file, neither read, convert or anything else in that direction.

What you said about the MS Office applications doesn't fill me with a great amount of hope.  But I'll have a go anyway.  

If that doesn't work I guess I'm doublebooting forever....

greetings

lt

---

### Post by joris1977 on 2009-08-07
Yes it is possible to run MS access 2000 with wine, but it is not very easy.

I am not a smart geek and gave up after a couple of hours and bought a license of crossover-office. It is based on wine and basically a front end of wine that handles difficult tricks that wine need to get some windows applications running. It is not very expensive and they gave me very good support, when i ran into trouble with a pretty advanced database file in MS Access 2000.

more info here:

[http://www.codeweavers.com/](http://www.codeweavers.com/)

Installing access with crossover office  made it possible for a small shop where  I work as a volunteer to migrate to ubuntu. Access 2000 is used on a daily basis for over a year. If it is the last thing standing in the way of migrating to ubuntu, it is money well spent... 

Openoffice base is an interesting project, but feature wise it is not even a bad look alike of MS Access.

I remember it has some very limited support of reading MS Access files. The only way i know was to export access files and import them in openoffice base.

I renember Kexi has some further MS access support. [http://www.kexi-project.org/](http://www.kexi-project.org/)  

But if you want to work with your old database file in one hour crossoveroffice really is the way to go.

---

### Post by Jerry N on 2009-08-07
I found that Word 97 and Excel 97 worked much better under Crossover than Wine but I didn't play with Access.  The Crossover web site indicates that Access should work.  Unfortunately, my copy of Crossover is a couple of versions back and won't even install Office 97 in Ubuntu 9.04 although it worked quite well with Ubuntu 7.10.  I haven't been willing to pay the price for an updated version of Crossover yet.

Jerry

---

### Post by longtom on 2009-08-08
> **jloveless said:**
> Praytell, what success or lack thereof have you had with Access under Wine?
Appreciated.

Jon

As anticipated I didn't succeed in installing MS Access under wine.  I therefore installed my WinXP copy as a virtual system with VirtualBox and installed Access there.

This worked as a work arround.

@joris1977

Thank you for that tip.  It is certainly high up on the list of considerations.  Just making overseas calls for support, which appears to be needed, sounds a bit....a well, if you are really desperate I guess anything goes.

---

