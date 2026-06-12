---
title: "Getting familiar with Commands"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by BunnyBear on 2011-02-16
[B]Fantastic I used the command line with mkdir 1 2 3 4 and made 4 directories under my user name!

Now without moving I want to make a file in 1 with information. What single command can I use?

I am in home/bunnybear and want to make a FILE in DIRECTORY 1

What single command would I use? :popcorn: Popcorn for everyone[/B]):P Thanks

---

### Post by Grenage on 2011-02-16
> Now without moving I want to make a file in 1 with information. What single command can I use?

```
echo Hello > 1/file
```

> I am in home/bunnybear and want to make a FILE in DIRECTORY 1

```
touch ../1/file
```

Alternatively, be explicit with your paths:

```
echo Hello > /home/*username*/1/file
touch /home/*username*/1/file
```

---

### Post by BunnyBear on 2011-02-16
Great I was able to do it and type in information to make the file complete. Thanks so much!!

---

