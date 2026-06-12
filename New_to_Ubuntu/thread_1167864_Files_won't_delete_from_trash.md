---
title: "Files won't delete from trash"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by LinuxFox on 2009-05-23
I was trying to install Quake 3 with my CD and made a mistake.  Now when I try to delete the files I keep getting a delete error permission denied.  When I move it out of the trash, it just makes another copy.

Can someone please help me delete the game so I re-install it correctly?  I was looking at this, [http://zerowing.idsoftware.com/linux/q3a/]("http://zerowing.idsoftware.com/linux/q3a/").  I found it while browsing Ubuntu's support documents ([found here]("https://help.ubuntu.com/community/Games/Native/QuakeIIIArena")).

---

### Post by mike555 on 2009-05-23
Try logging out and back in ........

---

### Post by LinuxFox on 2009-05-23
> **mike555 said:**
> Try logging out and back in ........I just tried it, it did nothing.  It didn't delete and I can't delete it.

---

### Post by gandaran on 2009-05-23
run 'gksu nautilus' in terminal then navigate with the root nautilus window to /home/user/.local/share/Trash, this is where trash files are kept and just delete them with the keyboard delete key

---

### Post by LinuxFox on 2009-05-23
> **gandaran said:**
> run 'gksu nautilus' in terminal then navigate with the root nautilus window to /home/user/.local/share/Trash, this is where trash files are kept and just delete them with the keyboard delete keyThanks this worked, but I ran into another problem.  My folder's memory didn't go back up.  It's staying the same as it was when the files were on the computer.

---

### Post by mcduck on 2009-05-23
> **LinuxFox said:**
> Thanks this worked, but I ran into another problem.  My folder's memory didn't go back up.  It's staying the same as it was when the files were on the computer.

Probably should have used shift+delete to immediately remove the files. Simply pressing delete in the file manager just moved the files into root's trash.. ;)

You'll find the files in /root/.local/share/Trash, remove them in similar way as before. And next time you remove files as root in graphical programs use shift+delete to avoid having to empty rot's trash afterwards.

---

### Post by LinuxFox on 2009-05-23
> **mcduck said:**
> Probably should have used shift+delete to immediately remove the files. Simply pressing delete in the file manager just moved the files into root's trash.. ;)

You'll find the files in /root/.local/share/Trash, remove them in similar way as before. And next time you remove files as root in graphical programs use shift+delete to avoid having to empty rot's trash afterwards.Thanks, but now I'm getting another problem.  It can't find the root's trash.  I'll attach a screenshot, I used the same terminal command as before.

---

### Post by mcduck on 2009-05-23
> **LinuxFox said:**
> Thanks, but now I'm getting another problem.  It can't find the root's trash.  I'll attach a screenshot, I used the same terminal command as before.

That's interesting, as it would meant the files didn't go to root's trash at all (the directory doesn't exist until you delete something as root).

If the files you deleted were on local filesystem (not on any removable drive, for example) I can't really imagine any other place where the files could now be besides your trash or root's trash. Try checking the available space again, perhaps the space just didn't refresh when you removed those files..

---

### Post by lukjad on 2009-05-23
Open the Terminal (Application->Accessories->Terminal) and copy/paste EXACTLY:
```
sudo rm -rf ~/.local/share/Trash/*
```

---

### Post by LinuxFox on 2009-05-23
> **mcduck said:**
> That's interesting, as it would meant the files didn't go to root's trash at all (the directory doesn't exist until you delete something as root).

If the files you deleted were on local filesystem (not on any removable drive, for example) I can't really imagine any other place where the files could now be besides your trash or root's trash. Try checking the available space again, perhaps the space just didn't refresh when you removed those files..Actually, it did go to the root's trash.  Out of curiosity, I logged onto root and I was able to empty the trash there.  I try not to use root as much because of the risks I read about.

Thanks, now my hd space is back.  I'm going to do more research into playing Quake III on Ubuntu seeing how it's a native game.

Ludjak007, thanks for the command, I'll refer to it next time this happens since I don't like needing to access root (I prefer sudo anyway)

---

### Post by lukjad on 2009-05-23
LinuxFox, I'm not sure if that command would have worked, but I do know that it deletes your regular user trash.

Let me try something in VirtualBox and I'll get back to you.

---

### Post by LinuxFox on 2009-05-23
> **lukjad007 said:**
> LinuxFox, I'm not sure if that command would have worked, but I do know that it deletes your regular user trash.

Let me try something in VirtualBox and I'll get back to you.Thanks, if you're not sure, then I won't try it.

---

### Post by kathalee777 on 2009-06-11
I put a cd in my dell-ubuntu system that had pictures on it.  It is now in my trash bin as cdrom1; and when I try to empty the trash I get a message saying permission denied.  Does anyone know how I can get this out of my trash bin.  

Thanks for any help!

---

