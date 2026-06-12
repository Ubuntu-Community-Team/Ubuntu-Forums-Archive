---
title: "wget syntax help"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by walrus_t on 2007-12-20
Hi,
I would like to retrieve some files:

[http://www.some_site.com/file0.gif](http://www.some_site.com/file0.gif)
[http://www.some_site.com/file1.gif](http://www.some_site.com/file1.gif)
[http://www.some_site.com/file2.gif](http://www.some_site.com/file2.gif)

...

[http://www.some_site.com/file200.gif](http://www.some_site.com/file200.gif)

with wget. Can someone help me with the syntax please?
Thanks!

---

### Post by yabbadabbadont on 2007-12-20
```
for i in $(seq 0 200)
do
    echo "http://www.some_site.com/file$i.gif" >> files
done

```
Then
```
wget -i files
```
Or install curl and read the section of its man page on using sequences in URL patterns.  (my posted solution is quicker)

---

### Post by walrus_t on 2007-12-20
Where do i type these commands?
I tried in Terminal, but no file named "files" is created and i get an error when i type wget -i files...
Thanks anyway!

---

### Post by yabbadabbadont on 2007-12-20
Ok, here is a cut and paste set of commands for you, since I'm sure that you must have typed something incorrectly when you followed my original instructions.

This will create a subdirectory called, "stuff", in your home directory and then download all the files into that directory.

```
mkdir stuff
cd stuff
for i in $(seq 0 200); do echo "http://www.some_site.com/file$i.gif" >> files; done
wget -i files

```

You will, of course, have to change the URL to the correct value.  (smart of you not to share with everyone which pr0n gallery you are going to download...  ;))

---

### Post by nfergusson on 2007-12-21
Just open a terminal and type:
for i in $(seq 0 200); do wget www.some_site.com/file$i.gif;done

---

