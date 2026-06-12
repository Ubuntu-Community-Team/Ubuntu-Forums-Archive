---
title: "Clear recent documents in Unity"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by Kimm on 2010-10-17
The question is straight forward enough, how do I clear the recent documents in the Unity interface? I cant seem to find it anywhere, and google has turned up with nothing usefull

---

### Post by kerry_s on 2010-10-17
i have a line in ~/.profile that removes it at log in.

```
rm -f $HOME/.recently-used.xbel
```

---

### Post by Kimm on 2010-10-18
> **kerry_s said:**
> i have a line in ~/.profile that removes it at log in.

```
rm -f $HOME/.recently-used.xbel
```

Thanks! this seems to prevent Unity from saving any new recent files, but the ones I had in the list before I added this line are still there, and I am still not sure how to get rid of them... ideas?

---

### Post by SM666AT on 2010-10-29
Hello,

same with my unity here, i don't need those recently used item stuff and i want to delete the "old" recently used items. please let me know if there is already a nice command.

thanx

---

