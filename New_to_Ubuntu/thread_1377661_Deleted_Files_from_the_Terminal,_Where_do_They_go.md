---
title: "Deleted Files from the Terminal, Where do They go?"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Sugi on 2010-01-10
I just deleted files from the terminal and I need them. :/  Where did they go?  Not in my ".Trash-o".


```
sudo rm -r game\ folder
```

The deleting took p[ace on my external ext3 drive.


Thanks for the help,
Sugi

---

### Post by Tahakki on 2010-01-10
If you delete using a Terminal, they're gone forever. Sorry.

EDIT: Wait - check they're not in a .Trash-1000 or similar folder on the drive itself.

---

### Post by Sef on 2010-01-10
Read Ubuntu Doc's [Data Recovery]("https://help.ubuntu.com/community/DataRecovery").

---

### Post by Sugi on 2010-01-10
Tahakki: Nope, nothing in the .trash directory.

Sef:  Thanks for the insight sef.

I guess getting them back won't be the easiest thing to do.

EDIT:  Does changing the premission of the .trash in my external ext3 drive hurt anything?  Should I change it back?

Sugi

---

### Post by efflandt on 2010-01-10
If you delete files from gnome file viewers it puts them in your trash.

But if you **rm** files from the terminal they go to never never land.  So you should be very careful about doing that.  It would have been a good idea to have done **ls game/ folder** first to see a listing of what you were about to delete.

I am not familiar with any specific programs, but you could web search "linux file recovery".

---

### Post by Sugi on 2010-01-10
efflandt, Ya I feared that rm -r would do the trick... as in for good. :/  I actually wanted to give it permission, not delete it. XD But when I press up on my arrow keys the last command was rm -r not chown -R and well, I wasn't paying close attention (as you can see.)

Thanks for the help guys,
Lucky I have most of what I lost,
Sugi

---

