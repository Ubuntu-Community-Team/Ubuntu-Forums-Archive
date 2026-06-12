---
title: "Help - It's not so easy!"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by halsport on 2009-10-07
**[B][B]**[/B][/B]I have Ubuntu 9.04 loaded.

The 1st time I loaded Firefox it worked great.  I added items to the bookmark toolbar, and changed the homepage.  I specified that tabs should always be showing.

I closed Firefox and reopened it and nothing I did was saved!!!

I also tried to update and I get a message that I don't have enough room and I need to delete items.

What's going on.  I thought that the installation was "straight forward", but it seems to be confusing.

Help

---

### Post by wojox on 2009-10-07
Try cleaning somethings out:

```
sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove
```

```
sudo apt-get localepurge
```

```
sudo localpurge
```

```
sudo apt-get install deborphan gtkorphan
```

---

### Post by halsport on 2009-10-07
Tried them.  Command not found.

---

### Post by wojox on 2009-10-07
> **halsport said:**
> Tried them.  Command not found.

Which command?

---

### Post by halsport on 2009-10-07
All of them.

---

### Post by Chronon on 2009-10-07
If those commands can't be found then your system didn't get installed properly. 

What do you mean by having 9.04 loaded?  Are you running from the LiveCD?  If so, this would explain why bookmarks and such aren't saved between boots.  

Corruption can sometimes happen during download, so it might be a good idea to verify the integrity of the disk and reinstall if it checks out properly. 

Maybe someone can offer you clear advice on how to get your system working from this point, but I would personally backup my data and then do a fresh install.

---

