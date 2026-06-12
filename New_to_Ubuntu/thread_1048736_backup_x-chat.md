---
title: "backup x-chat?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Vicfred on 2009-01-23
I'm going to format my HDD but I love my x-chat as it is now, I have lots of networks configured and I'd don't like to lose it, it is possible to backup my networks and preferences?

---

### Post by yeats on 2009-01-23
If you open up your terminal and do 
```
cd
cp -r .xchat2 xchat-backup
```

that should preserve your settings.  Then you could move that backup file back into place with 

```
mv xchat-backup .xchat2
```

---

### Post by snova on 2009-01-23
Or, you could also say, just copy the hidden .xchat2 folder (in your home directory) somewhere safe, along with the rest of your backup. :)

---

### Post by yeats on 2009-01-23
or that. :-) 

A separate home directory is probably the best idea.

---

### Post by MDSmith2 on 2009-01-23
I would also suggest taring it to save space and make it one file
```

cp .xchat2 xchat2_backup
tar -cvf xchat_backup.tar.gz xchat2_backup

```then when you need to extract it
```

tar -xvf xchat_backup.tar.gz
mv xchat2_backup .xchat2

```

---

