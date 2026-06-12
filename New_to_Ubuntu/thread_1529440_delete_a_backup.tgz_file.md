---
title: "delete a backup.tgz file"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by Whatrymes on 2010-07-12
Hey:

I ran a backup of my Ubuntu system, terminal said done but with errors, I would like to delete the tgz file, stored at /, but can't see how.

Thanks

---

### Post by wojox on 2010-07-12
You used **sudo rm**?

---

### Post by audiomick on 2010-07-12
If you would rather use the file manager instead of the terminal, start it with

```
gksu nautilus
```

and you should be able to do what you want.

Be careful doing this; with nautilus open in this way, you are in a position to erase system files and kill your system. (Same as with an incorrect sudo rm command)

---

### Post by Whatrymes on 2010-07-12
> **wojox said:**
> You used **sudo rm**?

Sorry absolute beginner here, I don't know what you mean.

---

### Post by wojox on 2010-07-12
In that case follow audiomick's advice ,but be careful. Just delete that file.

---

### Post by gandaran on 2010-07-12
> **wojox said:**
> In that case follow audiomick's advice ,but be careful. Just delete that file.
correct, but make sure to delete not send it to trash, highlight the file and use the delete key or enable the delete command in root nautilus.

---

### Post by Whatrymes on 2010-07-12
Got all, thank you.

Ps: I do i change this to say "solved" ??

---

### Post by wojox on 2010-07-12
> **Whatrymes said:**
> Got all, thank you.

Ps: I do i change this to say "solved" ??

Should be up top under thread tools. ;)

---

### Post by masque7 on 2010-07-12
> **Whatrymes said:**
> Got all, thank you.

Ps: I do i change this to say "solved" ??
'Thread tools'
Top right of the posts.

---

### Post by kinueakachi on 2010-07-14
So what do I do if I was, say, stupid enough to move it to the Trash-Bin? It won't appear there...how do I get rid of it now? And I'm a beginner so please do explain...XD.

---

### Post by gandaran on 2010-07-14
> **kinueakachi said:**
> So what do I do if I was, say, stupid enough to move it to the Trash-Bin? It won't appear there...how do I get rid of it now? And I'm a beginner so please do explain...XD.
which ubuntu version do you have, I ask because I haven't found the root trash in 10.04 so I don't yet know if theres one but there used to be one in older versions, well to remove the files  you open root nautilus, find the root trash folder and open it then delete the contents with the delete key.

---

