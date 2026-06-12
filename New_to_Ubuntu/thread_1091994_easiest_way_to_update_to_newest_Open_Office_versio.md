---
title: "easiest way to update to newest Open Office version?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by cptrohn on 2009-03-09
So what it the easiest way you have found to update to open office 3?

I have been snooping around some, I tried the way they did it on 10 things to do after you intall Ubuntu 8.10 but it didn't seem to work for me... 

Anything easy out there to do it with?

---

### Post by cptrohn on 2009-03-09
After I type in the information they give in that article here is what I get back in the terminal.
```
bash: /etc/apt/sources.list.d/openoffice.sources.list: Permission denied
```

Sorry I should have posted this in the OP.

---

### Post by sandyd on 2009-03-09
```

sudo gedit /etc/apt/sources.list

```

put this at the bottom of the file
```

deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main

```
```

sudo apt-get uppate
sudo aptitude safe-upgrade

```

---

### Post by tad1073 on 2009-03-09
post deleted

---

### Post by taurus on 2009-03-09
> **tad1073 said:**
> ```
/etc/apt/sources.list.d/openoffice.sources.list
```

needs to be 
```
sudo /etc/apt/sources.list.d/openoffice.sources.list
```

Actually, it needs to be 

```
gksudo gedit /etc/apt/sources.list.d/openoffice.sources.list
```
if you want to edit it.  

But if you only want to look at it, then 

```
cat /etc/apt/sources.list.d/openoffice.sources.list
```

---

### Post by cptrohn on 2009-03-09
Thank you carlee that did the trick!

---

### Post by sandyd on 2009-03-09
but still, i gotta question

why are ubuntu's resipostries not updated to openoffice 3.01 and instead still only at openoffice 2.XX?

---

### Post by starcannon on 2009-03-09
Carlee, as I understand it, packages are updated after they are tested; they are tested as time permits; there are a lot of packages.

That said, I do look forward to something as big as our office suite getting updated to latest or near latest version soon.

GL and have fun.

---

### Post by cptrohn on 2009-03-09
> **carlee said:**
> but still, i gotta question

why are ubuntu's resipostries not updated to openoffice 3.01 and instead still only at openoffice 2.XX?

Yeah, that doesn't make alot of sense really..  You would think they would be.

---

### Post by cptrohn on 2009-03-09
> **starcannon said:**
> Carlee, as I understand it, packages are updated after they are tested; they are tested as time permits; there are a lot of packages.

That said, I do look forward to something as big as our office suite getting updated to latest or near latest version soon.

GL and have fun.

Well I take back my "that doesn't make sense comment then"  Because that makes alot of sense.;)

---

