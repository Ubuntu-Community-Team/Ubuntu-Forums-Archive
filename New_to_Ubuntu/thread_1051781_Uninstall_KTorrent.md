---
title: "Uninstall KTorrent"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by meddyliol on 2009-01-27
Could someone please let me know how to remove KTorrent? I think it has to be done from the terminal but do not know how.

Thanks

Brian :)

---

### Post by shifty_powers on 2009-01-27
```
sudo apt-get remove ktorrent
```

will do the trick

---

### Post by meddyliol on 2009-01-27
Thanks for that. Is sudo apt-get remove a general term with the application simply added to the end?

:popcorn:

---

### Post by Thanoulis on 2009-01-27
Yes, it is. For more information just type into a terminal:
```
man apt-get
```

---

### Post by meddyliol on 2009-01-27
Thanks Thanoulis, that really is a great help.

Cheers

Brian :D

---

### Post by talsemgeest on 2009-01-27
> **meddyliol said:**
> Thanks for that. Is sudo apt-get remove a general term with the application simply added to the end?

:popcorn:
Indeed it is. Just like ```
sudo apt-get install <app-name>
``` will install an application. :)

---

### Post by rafaelsousa on 2009-01-27
Ktorrent is one (if it's not _the_ one) of the best bittorrent clients I've ever used. Why do you want uninstall it???

Well... People told you how to do so... But if you want to eliminate configuration files as well you shoud try:

```
apt-get remove ktorrent --purge
```

---

### Post by talsemgeest on 2009-01-27
No, ```

apt-get remove ktorrent --purge
``` would not work. On the other hand, ```
sudo apt-get remove ktorrent --purge
``` would. :)

---

