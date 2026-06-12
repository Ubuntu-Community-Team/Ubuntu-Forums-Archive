---
title: "navigating directories"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Fika on 2010-01-10
Ok I am unable to figure how to navigate to 

/var/log/rkhunter.log

I've tried the cd command doesn't work

---

### Post by halitech on 2010-01-10
rkhunter.log is a file so you would only use cd to get to /var/log then you would need to open the file with gedit or nano or some other text editor.

---

### Post by NoaHall on 2010-01-10
```
cd /var/log
less rkhunter.log
```
or just simply
```
less /var/log/rkhunter.log
```
or if you don't want to view in the terminal
```
gedit /var/log/rkhunter.log
```

---

### Post by Fika on 2010-01-10
It says permission denied

---

### Post by NoaHall on 2010-01-10
> **Fika said:**
> It says permission denied

```
gksudo gedit /var/log/rkhunter.log
```

Just don't edit anything.

---

