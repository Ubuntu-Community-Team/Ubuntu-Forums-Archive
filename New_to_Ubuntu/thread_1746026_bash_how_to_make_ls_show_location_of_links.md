---
title: "bash how to make ls show location of links"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by edpatterson on 2011-05-01
I might be nuts but I swear when I used to do
ls -l
symbolic links would show in green with a -> pointing to the linked file
Now I see a green name with an asterisk next to it

This is a very humbling experience.

Ed

Answering my own question for the possible benefit of others:
ln <sourec> <name of link>
is not the same as
ln -s <source> <name of link>

I was looking in man ls instead of man ln for the answer

---

### Post by LuisGMarine on 2011-05-01
I found I had the same problem, I was able to simply fix it by installing the symlinks application.

```
sudo apt-get install symlinks
```

then the command would be something like this ..

```
symlinks -v /
```

shows all the locations of links in the "/" folder.

You can just type in symlinks by itself in a terminal window to see other options, hope this helps =)

---

