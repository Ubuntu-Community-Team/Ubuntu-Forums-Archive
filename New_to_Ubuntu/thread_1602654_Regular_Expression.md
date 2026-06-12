---
title: "Regular Expression"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by pokerkmx on 2010-10-21
How can I find in current directory records, satisfied to this conditions: 1) starts with R 2) is a directory 3) name less than 11 symbols 4) read-only for all users. How can I find the count? May I use this in gcc app? Thanks.

---

### Post by uRock on 2010-10-21
Is this a homework assignment? Doesn't sound like anything a new user would be asking.

---

### Post by Old *ix Geek on 2010-10-22
> **uRock said:**
> Is this a homework assignment? Doesn't sound like anything a new user would be asking.Maybe we're both just very skeptical, but that's EXACTLY what I was thinking. :)

---

### Post by pokerkmx on 2010-10-22
:D I don't ask to do my homework. It's a topic for questions, right?

---

### Post by nothingspecial on 2010-10-22
Still looks like homework to me.

So, I think we can give hints, if I remember the COC correctly.

The find command can search for directories only and has a -perm option to filter for permissions.

```
man find
```

^ signifies the start of a string in regex

You specify the amount of times to match a character between curly brackets.

That should get you started :)

---

### Post by utilitytrack on 2010-10-22
> **pokerkmx said:**
> How can I find the count?

The count of wich? How many records found?

---

### Post by uRock on 2010-10-22
Thread closed. Obviously homework.

---

