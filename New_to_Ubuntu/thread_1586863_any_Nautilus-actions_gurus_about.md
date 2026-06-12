---
title: "any Nautilus-actions gurus about?"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by 0004tom on 2010-10-02
I'm able to get mplayer to play from a set of rars using this code

```
unrar p -inul my_file.rar | mplayer -cache 2048 -
```

I've been trying now for a few hours, to have this in the right-click nautilus menu with nautilus-actions, I just can't get it to work.

Is anyone able to help?

---

### Post by xtremesupremacy3 on 2010-10-05
oh thats pretty simple...you save it as a script, then move the script to:

~/.gnome2/nautilus-scripts

then its available by right clicking, scripts

---

### Post by Vaphell on 2010-10-05
try sh - c "unrar p -inul %f | mplayer -cache 2048 -" (i assume %f is a proper symbol for a filename here)
maybe nautilus-actions doesn't like piping or something

---

### Post by 0004tom on 2010-10-05
Thanks for the responses guys, I was unable to get nautilus-actions, and have no idea how to go about troubleshooting it, as the documentation for it is sparse at best. So I took the advice of writing a script and have managed to pull it off. 

Here's the script for anyone else that whats this..

```
# Get current path
mypath="`pwd`"

# Get file name
for filename in "$@"
do

# Hand it over to unrar and mplayer
unrar p -inul "$mypath/$filename" | mplayer -cache 2048 -
done
```

---

