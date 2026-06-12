---
title: "Cant install Pidgin?"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by Shadowgamon on 2010-12-05
When ever I I try to install pidgin , be it by .deb, Software center, or terminal , I get this
[CENTER]```
**Package dependencies cannot be resolved **
[LEFT] This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.
[/LEFT]
 
```[/CENTER]

---

### Post by wojox on 2010-12-06
Run

```
sudo apt-get -f install pidgin
```

See what the dependencies are.

---

### Post by karthick87 on 2010-12-06
Add this repository if you use Lucid or above,
```
sudo add-apt-repository ppa:pidgin-developers/ppa
```Update your repository,
```
sudo apt-get update
```Install Pidgin,
```
sudo apt-get install pidgin
```

---

### Post by sp-1070 on 2010-12-06
Forget pidgin

Install mercury
Works better highly editable looks really cool after youre done with it

---

### Post by Sef on 2010-12-06
What version of Ubuntu are you using?  (Note: just because someone says they are running a certain version, does not mean they are. Sometimes they forget to change it.)

---

### Post by karthick87 on 2010-12-06
Is that in repository?(Mercury)

---

### Post by sp-1070 on 2010-12-06
no mercury is to be downloaded from 
[http://mercury.im/](http://mercury.im/)
Just go download page install the thing and watch the magic happen

---

### Post by karthick87 on 2010-12-06
It is under develoopment i guess.

---

### Post by sp-1070 on 2010-12-06
Yeah they are working on it 
Its a great program already and to correct my other post.
You have to put it in youre sources.list yourself or use the core release.

---

### Post by Shadowgamon on 2010-12-07
I run 10.04 because I had a host of problems with 10.10 (I was using 10.04 for about two weeks before it was released) I would use mercury I I used msn exclusively, but I need multi- protocol, and empathy isnt doing it for me. Thanks for the help

---

