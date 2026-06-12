---
title: "I need to access my trash"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by airyk on 2010-12-03
Hello I run Ubuntu 10.01 Netbook remix. I need to access my trash because i deleted a very very important file for my job. I don't think i need to undelete the file because normally when i press delete the files end up in my trash.
I believe this because last time i 'emptied trash' 28 gigs became free.

The problem is that I have no clue how to access my trash.
Nautilus does not work, when i click on trash it says that its not supported.
There is no .trash folder anywhere
Please help.

---

### Post by Verbeck on 2010-12-03
this might or might not work
open nautilus > press ctrl+L > enter *trash:///* in the location bar

---

### Post by byStanderone on 2010-12-03
...hello, not sure if it's a typo...can't seem to find ubuntu 10.01 on the list of ubuntu versions: [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by amjjawad on 2010-12-03
> **byStanderone said:**
> ...hello, not sure if it's a typo...can't seem to find ubuntu 10.01 on the list of ubuntu versions: [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

I guess he meant 10.10.

---

### Post by wojox on 2010-12-03
Trash is in Nautilus. Open it and press Ctrl+H 

```
.local/share/Trash
```

---

### Post by amjjawad on 2010-12-03
> **airyk said:**
> Hello I run Ubuntu 10.01 Netbook remix. I need to access my trash because i deleted a very very important file for my job. I don't think i need to undelete the file because normally when i press delete the files end up in my trash.
I believe this because last time i 'emptied trash' 28 gigs became free.

The problem is that I have no clue how to access my trash.
Nautilus does not work, when i click on trash it says that its not supported.
There is no .trash folder anywhere
Please help.


> **forestpiskie said:**
> Do Alt+F2 and then run gconf-editor

Navigate to apps/nautilus/desktop - enable trash_icon_visible

[http://ubuntuforums.org/showthread.php?t=1056316](http://ubuntuforums.org/showthread.php?t=1056316)

---

### Post by stacych on 2012-04-01
Found this thread and didn't understand much as a total n00b, what is Nautilis? I have no idea... I eventually found it but it was empty as far as I could see.

This might be useful to fellow n00bs also searching for files accidentally deleted, who then must find trash un Ubuntu NBR

Go to your file system

Click VIEW

Select SIDE PANE

The trash is now visible in the list of files in the side paine. Yo ucan click on it and retrieve your files.

---

