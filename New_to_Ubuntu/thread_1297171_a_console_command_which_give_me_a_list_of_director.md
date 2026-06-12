---
title: "a console command which give me a list of directories along with the directory size?"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by legolas_w on 2009-10-21
Hi
I am looking for a command to show me list of all directories in the current location along with each directory size.

Is there such a thing around?

thanks

---

### Post by sisco311 on 2009-10-21
> **legolas_w said:**
> Hi
I am looking for a command to show me list of all directories in the current location along with each directory size.

Is there such a thing around?

thanks

```
find ./ -type d -exec du -sh {} \;
```

```
man find
man du
```

---

### Post by Zulu-Zeffir on 2009-10-21
Why not just use:
 ls -alh

---

### Post by ajgreeny on 2009-10-21
> **Zulu-Zeffir said:**
> Why not just use:
 ls -alh
I suspect that is not quite what the OP wants, as it gives the size of the folders but not including the files in the folders, eg, I have a video folder with about 10GB of space used by files in it, but your command shows it as 4k, ie the folder but not its contents.

The first answer was correct, I think.

---

### Post by legolas_w on 2009-10-21
Thank you all, the first reply was what I needed.
However the command showed all folders recursively but I removed them manually.

Basically I needde the command to see what is the size of each TV series in my archive to decide about moving it to another hard disk or not.

Thanks again.

---

### Post by sisco311 on 2009-10-21
> **legolas_w said:**
> Thank you all, the first reply was what I needed.
However the command showed all folders recursively but I removed them manually.

Basically I needde the command to see what is the size of each TV series in my archive to decide about moving it to another hard disk or not.

Thanks again.

You are welcome!

If you don't want to list the folders recursively, you can set the maxdepth to 1:
```
find ./ -maxdepth 1 -type d -exec du -sh {} \;
```

---

