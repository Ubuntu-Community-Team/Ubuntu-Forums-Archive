---
title: "How list the currently employed DISPLAYs ?"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by honeybear on 2011-08-23
Hi,

How know the currently employed DISPLAYs on a given machine :0, :1, ... by an SH command or SH script?
And eventually, the remaining ones ? 

Thank you

---

### Post by papibe on 2011-08-23
In Bash:
```
$ echo $DISPLAY
```
Regards.

---

### Post by honeybear on 2011-08-23
> **papibe said:**
> In Bash:
```
$ echo $DISPLAY
```
Regards.

But you cannot run this into crontab? 

I would like to list them using a script.

---

### Post by papibe on 2011-08-23
> **honeybear said:**
> But you cannot run this into crontab? 
I would like to list them using a script.
Interesting. Could you explain a little more what you are trying to do?

Regards.

---

### Post by bodhi.zazen on 2011-08-24
```
ps aux | grep -v awk | awk '/Xorg/ , gsub(".*Xorg", "") {print $1}'
```

If you are running on chron, use the full path to ps, grep, and awk

---

### Post by papibe on 2011-08-24
I think Xorg runs as just plain X (at least on 10.04). With that in mind, just making a few tweaks to bodhi.zazen's code, and this works on my system:
```
$ ps aux | grep -v awk | awk '/\/usr\/bin\/X/ , gsub(".*/usr/bin/X", "") {print $1}'
```

Regards.

EDIT: I have a dual head system running 2 separate X Screens.

---

### Post by honeybear on 2011-08-24
> **papibe said:**
> I think Xorg runs as just plain X (at least on 10.04). With that in mind, just making a few tweaks to bodhi.zazen's code, and this works on my system:
```
$ ps aux | grep -v awk | awk '/\/usr\/bin\/X/ , gsub(".*/usr/bin/X", "") {print $1}'
```

Regards.

EDIT: I have a dual head system running 2 separate X Screens.


Wow. Cool. 

```
 ps aux | grep -v awk | awk '/\/usr\/bin\/X/ , gsub(".*/usr/bin/X", "") {print $1}'
:0
:6
:6

```

Since I have several users, only one can be using Xdm, so the others might startx with startx but it shall be onto empty DISPLAY... so script?

---

### Post by bodhi.zazen on 2011-08-24
> **honeybear said:**
> Wow. Cool. 

You are welcome :twisted:

> Since I have several users, only one can be using Xdm, so the others might startx with startx but it shall be onto empty DISPLAY... so script?

Not sure what you are asking. You can test it out yourself, start X and then run the command.

You can also add sort and uniq to that command

ps aux ..... | sort | uniq

---

