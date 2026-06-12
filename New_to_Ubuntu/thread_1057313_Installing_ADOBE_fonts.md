---
title: "Installing ADOBE fonts"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by accodata on 2009-02-01
Good Morning

I am using wine for some programs however, I need to install some adobe fonts, I am not sure where to find the ubuntu font folder, or do I need to put them else where?

Any help would be fantastic.

with thanks

---

### Post by Partyboi2 on 2009-02-01
Have a look in ```
/usr/share/fonts
```After adding new fonts you can update the cache with
```
 sudo fc-cache -f -v
``` from a terminal.

---

### Post by accodata on 2009-02-01
Partyboi2
thankyou for your help, But I found it, but it won't allow me to add my fonts....

Any more help????????????

many thanks

---

### Post by Partyboi2 on 2009-02-01
Are you having problems copying them over to /usr/share/fonts or is something else going wrong?

---

### Post by accodata on 2009-02-01
Hi Again,

I can't copy any of them over at all, I am not sure why... I have them in 2 folders on my c drive already however, I can't put them in /usr/share/fonts/

---

### Post by Partyboi2 on 2009-02-02
Press Alt+F2 and enter
```
gksu nautilus /usr/share/fonts
```
This will open /usr/share/fonts with admin rights. Copy your files over then close nautilus before doing anything else as you do not want to continue using nautilus as root as it can cause breakages if not careful. Then open a terminal (Applications>Accessories>Terminal) and update the cache
```
sudo fc-cache -f -v
```

---

