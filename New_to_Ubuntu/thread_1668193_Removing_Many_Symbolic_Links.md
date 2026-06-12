---
title: "Removing Many Symbolic Links"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by if4124l on 2011-01-16
HI, I have a lot of symbolic links(I think that's what they're called, I used ln -s dir/* . ) in one directory. I need to remove them. I there any way to do this using the terminal? It's in a server with no gui.

---

### Post by Perfect Storm on 2011-01-16
```
cd <path>
sudo rm -rf <symblink file>
```

Just be very careful using the second command.

---

### Post by if4124l on 2011-01-16
Yes, but is there something to find all links and delete them automatically? There are a lot of them.
EDIT: Never mind. I have removed them.

---

### Post by Perfect Storm on 2011-01-16
You can do a 
```
ls -a
```
In the directory all symblinks file are colored "Cyan".

Then;
```
sudo rm -rf <file> <file> <file>
```

---

