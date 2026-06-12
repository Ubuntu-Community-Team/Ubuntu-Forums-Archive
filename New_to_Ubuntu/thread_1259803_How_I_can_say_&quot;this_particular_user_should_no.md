---
title: "How I can say: &quot;this particular user should not be able to access a directory&quot; usign"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by legolas_w on 2009-09-06
Hi,

Thank you for reading my post
is there any way to prevent a user from accessing a particular directory?
say we have a user named sec and a directory named /opt/noop and we want to prevent sec from accessing the directory or its sub directories

Thanks.

---

### Post by k33bz on 2009-09-06
you want to jsut prevent that user from accessing this file or everyone but himn?

---

### Post by legolas_w on 2009-09-07
Hi,
I want to prevent only that user from accessing the directory. later on I may add other users to the blocked list.

Thanks

---

### Post by Bodsda on 2009-09-07
> **legolas_w said:**
> Hi,
I want to prevent only that user from accessing the directory. later on I may add other users to the blocked list.

Thanks

Removing his read write and execute permissions recursively should work
```
sudo chmod -R sec-rwx /opt/noop/
```
That command removes sec's read write and execute permissions from /opt/noop/
Syntax is
```
sudo chmod [COLOR="SeaGreen"]<arguments> <user><action><permissions> <directory>[/COLOR]
```
[COLOR="SeaGreen"]Arguments:[/COLOR] [COLOR="Blue"]-R[/COLOR], for recursive
[COLOR="SeaGreen"]User:[/COLOR] [COLOR="Blue"]sec[/COLOR], the user who we want to remove permissions form
[COLOR="SeaGreen"]action:[/COLOR] [COLOR="Blue"]-[/COLOR], + or - depending on giving or removing permissions
[COLOR="SeaGreen"]permissions:[/COLOR] [COLOR="Blue"]rwx[/COLOR], r = read w = write x = execute
[COLOR="SeaGreen"]directory:[/COLOR] [COLOR="Blue"]/opt/noop/[/COLOR], The parent directory we want to remove permissions from

Hope this helps,
Bodsda

---

### Post by longtom on 2009-09-07
> **Bodsda said:**
> Removing his read write and execute permissions recursively should work
```
sudo chmod -R sec-rwx /opt/noop/
```
That command removes sec's read write and execute permissions from /opt/noop/
Syntax is
```
sudo chmod [COLOR="SeaGreen"]<arguments> <user><action><permissions> <directory>[/COLOR]
```
[COLOR="SeaGreen"]Arguments:[/COLOR] [COLOR="Blue"]-R[/COLOR], for recursive
[COLOR="SeaGreen"]User:[/COLOR] [COLOR="Blue"]sec[/COLOR], the user who we want to remove permissions form
[COLOR="SeaGreen"]action:[/COLOR] [COLOR="Blue"]-[/COLOR], + or - depending on giving or removing permissions
[COLOR="SeaGreen"]permissions:[/COLOR] [COLOR="Blue"]rwx[/COLOR], r = read w = write x = execute
[COLOR="SeaGreen"]directory:[/COLOR] [COLOR="Blue"]/opt/noop/[/COLOR], The parent directory we want to remove permissions from

Hope this helps,
Bodsda

Love this.  Another bookmark....getting a bit cramped right now.

Hey - is this a squirrel in your avatar?  You must be careful - there appears to be an invasion doing it's rounds....

---

