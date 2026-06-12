---
title: "simple ownership script"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by neurostu on 2010-03-01
I'm planning on changing the UID of my username for a variety of reasons.  When I chance the UID of my username in the /etc/passwd file I also have to update all my files to reflect the proper ownership.

I'm guessing that the easiest thing will be to write a script that will scan an entire file system and change the owndership ID from one UID to another that I can specify.

Does anybody know how to write a script like this?

---

### Post by undecim on 2010-03-01
```
sudo chown -R username /home/username
```
That will change all files in your home directory to your ownership.

---

### Post by neurostu on 2010-03-01
thanks...

What I was looking for was this:
```

sudo chown 1050.1050 `find -uid 1000`

```

---

### Post by DaithiF on 2010-03-01
> sudo chown 1050.1050 `find -uid 1000`
 
thats probably not going to work so well for files with spaces.  and you may run into issues with the length of the command itself exceeding the max # of characters (depending on how many files the find command expands to)
 
so maybe something like this instead:
```
 
sudo find somedir -uid 1000 -exec chown 1050.1050 {} \;

```
though personally I would agree with undecim's approach of chown'ing your home directory ... since all files there should be owned by you and there shouldn't be too many other places in a typical linux filesystem that have files owned by the user (shared data folders aside perhaps)

---

### Post by ayenack on 2010-03-01
> **undecim said:**
> ```
sudo chown -R username /home/username
```
That will change all files in your home directory to your ownership.

I'd add the group to that as well.

```
sudo chown -R username:username /home/username
```

---

### Post by neurostu on 2010-03-03
it seems as though the usermod command is what I want:
```

sudo usermod -u <new uid>

```

---

