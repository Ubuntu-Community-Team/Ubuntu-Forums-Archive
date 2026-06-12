---
title: "editor for root crontab"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-08-15
Hi Ubuntu Community:

How do I change the default editor for root crontab?

THanks,
Phil Smith
Duluth, GA

---

### Post by Paqman on 2010-08-15
By changing the default text editor for the system:

```
sudo update-alternatives --config editor
```

---

### Post by MrWES on 2010-08-15
Correct, choose option 3 for nano :)

---

### Post by samarium on 2010-08-15
nano was the problem

update-alternatives was not providing the usual solution

seems like crontab -e uses sensible-editer as the editor and it saves the selected editor to $HOME/.selected_editor

rm $HOME/.selected_editor and I was again prompted for an editor to select

why we need another layer of editor selection inconsistent with update-alternatives I don't know, and would have appreciated not having to strace -f -t execve crontab -e 2>/tmp/a to find out

back to vim.tiny

---

### Post by Old Jimma on 2010-08-15
I should have been more specific.

I want gedit to be the default editor in root so when I say 

sudo -i
crontab -e

I get gedit there working on my crontab.

How do I get gedit to be my default editor under root?

Thanks!
Phil

---

