---
title: "Open the results of find in nautilus"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by gidra on 2011-03-17
-run find command
-results are outputted as a "hyperlink"
-when I click the on a hyperlink, the folder contents of that particular file directory are show in nautilus

I'm a newbie to terminal so please bear with me. Thanks

---

### Post by nothingspecial on 2011-03-17
Don't know how you do the hyperlink bit but

```
find -type d -name "searchterm" -exec nautilus '{}' \;
```

will open a nautilus window for each directory it finds with the name searchterm.

---

### Post by gidra on 2011-03-17
Thankse nothingspecial, actually the hyperlink bit was idea (the reason why I wrote in double quotes) Gonna try it now, get back to you later.

---

### Post by gidra on 2011-03-17
Well that actually opened a nautilus windows for each folder it found, which is not what I want. I it to open the folder contents of a particular file from the results (hence why I came up with the idea of a hyperlink)

---

### Post by nothingspecial on 2011-03-17
Assuming that all the folders have different names make a folder to contain your links.

cd into that folder then do this

```
find <search path> -type d <search options> -exec ln -s '{}' \;
```

That will create a link to each folder in your new directory that you can click.

---

### Post by vanadium on 2011-03-17
Places - Search for files may pretty much do what you want.

---

### Post by nothingspecial on 2011-03-17
> **vanadium said:**
> Places - Search for files may pretty much do what you want.

Good point :p

---

### Post by gidra on 2011-03-17
Actually places-search ain't finding nothing (maybe because I got indexing turned off ?). Beside it isn't half as powerful as find

---

### Post by nothingspecial on 2011-03-17
> **gidra said:**
> . Beside it isn't half as powerful as find

Another good point.:p

---

### Post by gidra on 2011-03-17
While we're at it, can someone please point out how to sort my results by filetype in asc/desc order. Thanks for your assistance

---

### Post by gidra on 2011-03-17
Started a new thread about the latter issue [http://ubuntuforums.org/showthread.php?t=1708918](http://ubuntuforums.org/showthread.php?t=1708918)

---

