---
title: "Skype aborted in Natty"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by Peter09 on 2011-05-26
Had skype running for weeks in Natty - suddenly I am getting a 'skype aborted' message and nothing else. Anyone know what this is about?

---

### Post by ceverett on 2011-05-26
Same thing for me here.  I've had this install running for months without trouble.  I used it yesterday morning without issues.  This morning it fails about 5 seconds after I start the program, saying nothing except "Aborted".

---

### Post by matborda on 2011-05-26
same here!

---

### Post by sergioroa on 2011-05-26
I can confirm this in maverick using Skype 2.2. I downgraded to 2.1 and it works.

---

### Post by luisloboborobia on 2011-05-26
Same here!

---

### Post by tim73 on 2011-05-26
It seems the problem is global and you can restart your Skype by going to ~/.Skype and removing the shared.xml (and probably also the lock file shared.lck)

It worked for me with Ubuntu 10.04

---

### Post by luisloboborobia on 2011-05-26
Thanks Tim, it worked for me too: removed shared.xml and shared.lck, Ubuntu 11.04

Regards,
Luis

---

### Post by Peter09 on 2011-05-26
> It seems the problem is global and you can restart your Skype by going  to ~/.Skype and removing the shared.xml (and probably also the lock file  shared.lck)

Yep - worked for me

---

### Post by ajgreeny on 2011-05-26
Anything to do with the M$ purchase of skype, or just a coincidence?

---

### Post by gradinaruvasile on 2011-05-26
> **ajgreeny said:**
> Anything to do with the M$ purchase of skype, or just a coincidence?

Lol. It probably wants to fall in line with the rest of M$ products. BTW i have seen it happening on Windows too recently.

Start looking for alternatives.

---

### Post by f_padia on 2011-05-26
> **tim73 said:**
> It seems the problem is global and you can restart your Skype by going to ~/.Skype and removing the shared.xml (and probably also the lock file shared.lck)

It worked for me with Ubuntu 10.04

Cool that worked for me too. Thanks!

---

### Post by Sergio.G on 2011-05-26
This also happened to me using Lucid 64 bit

Confirmed solution as Tim73(post #6) wrote:

> **tim73 said:**
> It seems the problem is global and you can restart your Skype by going to ~/.Skype and removing the shared.xml (and probably also the lock file shared.lck)

It worked for me with Ubuntu 10.04

or using the terminal:

mv ~/.Skype/shared.xml ~/.Skype/shared~.xml

Then start Skype, it'll pop up the licence agreement window, click ok and then everything should work as usual

---

### Post by alanchambers on 2011-05-27
> **tim73 said:**
> It seems the problem is global and you can restart your Skype by going to ~/.Skype and removing the shared.xml (and probably also the lock file shared.lck)

I've just suffered the same problem, after months of problem free use, and confirm that deleting those two files has cured it for me too.

---

### Post by alphacrucis2 on 2011-05-27
This was reported on omgubuntu:

[http://www.omgubuntu.co.uk/2011/05/skype-crashed-today-heres-a-fix/]("http://www.omgubuntu.co.uk/2011/05/skype-crashed-today-heres-a-fix/")

---

