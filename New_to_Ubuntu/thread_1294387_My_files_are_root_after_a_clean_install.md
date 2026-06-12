---
title: "My files are root after a clean install"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by captgadget on 2009-10-18
is there someway I can unlock all of them? I saved my documents, videos, photos and stuff to another harddrive and now when I moved them to the home folder they are all locked.

---

### Post by falconindy on 2009-10-18
```
sudo chown -R `id -nu`:`id -nu` $HOME
```

---

### Post by OpenGuard on 2009-10-18
```
sudo chown user:group /directory/sub

```

---

### Post by SuperSonic4 on 2009-10-18
```
sudo chown -Rv username:group ~
```

Where username is your username and group is your group (in nearly all cases it's the same as your username)

---

### Post by lovinglinux on 2009-10-18
You can also run this without changing any word:

```
sudo chown -R $USER:$USER $HOME
```

---

### Post by captgadget on 2009-10-18
This is the error message I got here: /home/captgadget/.gvfs': Permission denied

---

### Post by captgadget on 2009-10-18
I got this error message: /home/captgadget/.gvfs': Permission denied

---

### Post by SuperSonic4 on 2009-10-18
Did you preface the command with sudo?

---

### Post by falconindy on 2009-10-18
You'll always get an error when trying to tinker with .gvfs's permissions. It's no big deal. Sounds like the rest of it went fine.

---

