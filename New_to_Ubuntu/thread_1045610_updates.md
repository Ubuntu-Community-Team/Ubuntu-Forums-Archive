---
title: "updates"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by ericgds on 2009-01-20
I just re downloaded ubuntu but was not prompted on the 200 or so security updates this time.  I wonder if I still have them. How can I tell?

---

### Post by gettinoriginal on 2009-01-20
Did you do a totally fresh install ??  What distribution ??

---

### Post by Dumbestcrayon on 2009-01-20
to see if you have any available updates do this..

System > Administration > Software Sources

Make sure everything under Downloadable from the internet is checked and I unchecked the Installable from CD-ROM

Then do

```
sudo apt-get update
```

then open synaptic and click "Check for Updates"

---

### Post by ericgds on 2009-01-20
> **Dumbestcrayon said:**
> to see if you have any available updates do this..

System > Administration > Software Sources

Make sure everything under Downloadable from the internet is checked and I unchecked the Installable from CD-ROM

Then do

```
sudo apt-get update
```

then open synaptic and click "Check for Updates"


Where do I write that code stuff?

---

### Post by donkyhotay on 2009-01-20
Go to applications, click on accessories, then click on terminal. This will bring up the terminal (also known as the CLI). This is where you type user commands. There are also other programs such as yakuake that make accessing the CLI easier but for just starting out the instructions given above are the easiest.

---

### Post by ericgds on 2009-01-20
> **donkyhotay said:**
> Go to applications, click on accessories, then click on terminal. This will bring up the terminal (also known as the CLI). This is where you type user commands. There are also other programs such as yakuake that make accessing the CLI easier but for just starting out the instructions given above are the easiest.


OK that seemed to work as it just did a bunch of stuff in the terminal.  now i need to open synaptic.  How do I do this, do I close the terminal first?

---

### Post by Temposs on 2009-01-20
To open Synaptic, go to System->Administration->Synaptic Package Manager

---

### Post by ericgds on 2009-01-20
> **ericgds said:**
> OK that seemed to work as it just did a bunch of stuff in the terminal.  now i need to open synaptic.  How do I do this, do I close the terminal first?

OK I just found the update manager and am downloading 224 updates so I got what I was needing. Thanks.  Speaking of security updates, should I now feel safe to do internet banking and stuff on ubuntu or do I need to install any other specific security.  I am so used to windows and having to install antispyware, anti malware, anti virus, etc.

---

### Post by ericgds on 2009-01-20
> **Temposs said:**
> To open Synaptic, go to System->Administration->Synaptic Package Manager

Oh I just got this reply.  I went to the package manager earlier but didn't see a check for updates button. Oh well, the problem is solved now anyway.

---

### Post by SunnyRabbiera on 2009-01-20
> **ericgds said:**
> OK I just found the update manager and am downloading 224 updates so I got what I was needing. Thanks.  Speaking of security updates, should I now feel safe to do internet banking and stuff on ubuntu or do I need to install any other specific security.  I am so used to windows and having to install antispyware, anti malware, anti virus, etc.

Nono, you will be fine after your update.
Ubuntu doesnt suffer from viruses, adware and the like.
Not saying that there are not security patches, what you are getting there with your update are probably all security patches and bugfixes...
But dont worry about the number, its actually a GOOD thing that Ubuntu has these updates.
It shows you that Ubuntu does care about security :D

---

### Post by donkyhotay on 2009-01-20
The only thing you really have to worry about with internet banking and online commerce is 'man in the middle' attacks which has nothing to do with viruses or even your computer (basically someone else pretends to be your banks website). Generally though so long as you pay attention to the URL that isn't a major problem.

---

