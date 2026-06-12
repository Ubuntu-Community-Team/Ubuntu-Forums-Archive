---
title: "How do I see the exact byte size of files, directories"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by Chewable on 2009-11-28
I'm not sure if this has been asked before but I can't seem to find anything on it. My question is this:  How do I find the *exact* bytesize of a 1) directory and all of its contents, and 2) one or more selected files and/or subdirectories? 

Viewing properties within Nautilus just shows me a rounded off total like 1.2GB or 354.8MB which isn't the accuracy I'm looking for. Is there a plugin for Nautilus I should be installing? Should I switch over to another file manager? Is there somewhere I can edit the type of units used in Unbuntu?

---

### Post by rudy.b on 2009-11-30
You could try the terminal command du:
```
du -b /home/username
```

---

