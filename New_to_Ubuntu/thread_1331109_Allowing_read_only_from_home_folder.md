---
title: "Allowing read only from home folder"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by chimere on 2009-11-19
Hey all,

I want to set up my Xubuntu machine so that other users can use it as an sftp for files. However, I don't want those users to be able to snoop around through the rest of my machine outside of their home folder, even if they can't change anything. Is this a reasonable thing to want? What's the easiest way to set it up?

Thanks!

---

### Post by emigrant on 2009-11-19
they can't do damage to the other folders.
if you wan't your folder to be made inaccessible to others give:

```
sudo chown -R yourname:yourname ~/.
```

```
sudo chmod -R 700 ~/. 
```

---

