---
title: "Nautilus Search Issue."
date: 2010-05-12
forum: New to Ubuntu
---

### Post by SKhan on 2010-05-12
I am new linux user and i must say i am loving ubuntu/kubuntu. But still there is a bunch of annoying issues i have to come over. One such issue is:
1. How to make Nautilus show the search results with complete path of found files.

2. What's the keyboard shortcut for searching files? I vaguely remember that some days ago Ctrl+S was working but now it's not.

3. I am unable to decrease the width of "Name" column below certain extent. It's still too wide to be acceptable.

4. If i change View of search results (icon view/ list view/ compact view), It auto-starts the search.

5. Search is slow so i have to wait double time as compared to windows 7.

---

### Post by ubunterooster on 2010-05-12
2. cntrl+f 

[think "find"] don't know the rest

---

### Post by Sealbhach on 2010-05-12
I like to use the locate command to give me a hint of where to find what I'm looking for.

e.g.

```
locate *.mp3
```

or

```
locate *.mp3 | grep GaGa


```

---

### Post by SKhan on 2010-05-12
> **Sealbhach said:**
> I like to use the locate command to give me a hint of where to find what I'm looking for.

e.g.

```
locate *.mp3
```

or

```
locate *.mp3 | grep GaGa


```
thanks. pretty fast search method. but the first code showed the results only from /home and /usr it didn't showed any result from NTFS partitions. Between it only showed the path and didn't show any other properties of the file. Can't i do that in nautilus?

second code didn't do anything

---

### Post by SKhan on 2010-05-12
> **ubunterooster said:**
> 2. cntrl+f 

[think "find"] don't know the rest
thanks for reminding me the shortcut. that's was it.

---

### Post by Sealbhach on 2010-05-12
> **SKhan said:**
> thanks. pretty fast search method. but the first code showed the results only from /home and /usr it didn't showed any result from NTFS partitions. Between it only showed the path and didn't show any other properties of the file. Can't i do that in nautilus?

Yeah, I guess it wouldn't have a record of what's on your NTFS partition, it searches a database of Linux filenames. It's quick way of finding where your stuff might be though. You can then go to that location using Nautilus and find out more. You can also search your NTFS partition with Nautilus.


> **SKhan said:**
> 
second code didn't do anything

I didn't really expect it to, unless you were a fan of Lady GaGa.

The | is called a "pipe" and the "grep" searches for keywords, so the command finds all mp3s, pipes those results to the grep filter and tries to narrow down the results to lines containing "GaGa".

I'm not a big fan of the command line, but I do use the locate command a lot.

.

---

### Post by SKhan on 2010-05-13
> **Sealbhach said:**
> I didn't really expect it to, unless you were a fan of Lady GaGa.

The | is called a "pipe" and the "grep" searches for keywords, so the command finds all mp3s, pipes those results to the grep filter and tries to narrow down the results to lines containing "GaGa".

I'm not a big fan of the command line, but I do use the locate command a lot.

.
he he! before reading this post i never heard of Lady GaGa. After reading your post i visited wikipedia to know something about her.
Most popular western singers/bands here in my place are Michael Jackson, Madonna, Mariah Carey, Britney Spears, Enigma etc. But really never heard of Lady GaGa.
I though GaGa was some linux command. :)

---

