---
title: "&quot;Transmission cannot be started&quot; error"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by J003S3PH on 2011-07-07
Whenever I try downloading a torrent, I get a "Transmission cannot be started" error,

and get a message like

Couldn't open "/home/joe/.config/transmission/lock": Permission denied.

I was able to download a torrent before, but now I cant..

Any help would be appreciated, Thanks!

---

### Post by wojox on 2011-07-08
Remove the lock file:

```
rm /home/joe/.config/transmission/lock
```

---

### Post by J003S3PH on 2011-07-08
> **wojox said:**
> Remove the lock file:

```
rm /home/joe/.config/transmission/lock
```

I tried that but I get a message saying "cannot remove /home/joe/.config/transmission/lock" no such file or directory

---

### Post by wojox on 2011-07-08
Were you running Transmission as root? Try:

```
sudo chown -R "$USER:$USER" ~/.config/transmission
```

---

### Post by J003S3PH on 2011-07-09
> **wojox said:**
> Were you running Transmission as root? Try:

```
sudo chown -R "$USER:$USER" ~/.config/transmission
```

THANK YOU SO MUCH!!, That Fixed the Problem!

---

