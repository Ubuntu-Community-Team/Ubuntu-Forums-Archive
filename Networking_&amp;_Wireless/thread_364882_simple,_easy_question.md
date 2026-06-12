---
title: "simple, easy question"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by SuperTeece on 2007-02-18
I have a laptop and a desktop. The laptop is running Dapper Desktop and the desktop is running Edgy Server. I have them communicating via SSH. I want to copy a folder (about 24GB) from the laptop to the desktop. I am looking at the desktop's terminal and am at a loss for what to type. I know the standard syntax is ```
cp (source)  (destination)
```
But how do I tell it that the source is one PC while the destination is the other?

---

### Post by SuperTeece on 2007-02-18
Never mind. I just had a brain storm. I did the reverse, connecting to the terminal only desktop through the GUI laptop. After a little chmod magic the files are copying after a bit of drag-and-drop action.

Tough, if anyone reads this, I would still like to know the syntax for future use.

Thanks.

---

### Post by Reedbeta on 2007-02-18
For future reference, you can use 'scp' (secure copy).  The synax is like
```

scp username@sourcemachine:sourcefile username@destmachine:destfile

```
You can leave off the username@machine part if it's a local file, and you can use ~ for the home directory in the path.

---

