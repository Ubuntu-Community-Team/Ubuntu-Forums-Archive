---
title: "Permisions rebelion"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by nnjond on 2010-04-30
Hi,

I need to back up some Directories, but this happens:

ubuntu@ubuntu:/media/03b6fba4-4e4f-471e-9766-481d932075c1$ chmod 777 *
chmod: changing permissions of `13 of Stravinsky': Operation not permitted
chmod: changing permissions of `1 of Stravinsky': Operation not permitted
chmod: changing permissions of `Arditti Quartet': Operation not permitted


Can you think of a solution please?

---

### Post by HermanAB on 2010-04-30
Use sudo to do things with elevated privileges:
$ sudo chmod 777 /media/whatever

---

### Post by Paqman on 2010-04-30
If you don't own those files, then you'll need to prefix you command with sudo to change the permissions:
```
sudo chmod 777 *
```

Be seriously careful that you're in the right folder before using that command. It would be safer to use:
```
sudo chmod 777 /media/03b6fba4-4e4f-471e-9766-481d932075c1/*
```
You can hit TAB to autocomplete long paths like that one, btw.

---

### Post by nnjond on 2010-04-30
Thanks That works but not for daugther dir.

---

### Post by K.Mandla on 2010-04-30
> **nnjond said:**
> Thanks That works but not for daugther dir.
```
sudo chmod -R 777 /media/03b6fba4-4e4f-471e-9766-481d932075c1/*
```
That should recurse through the directories.

---

