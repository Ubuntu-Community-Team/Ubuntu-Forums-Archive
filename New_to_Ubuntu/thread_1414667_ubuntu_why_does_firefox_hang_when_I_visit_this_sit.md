---
title: "ubuntu why does firefox hang when I visit this site?"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by mvalviar on 2010-02-23
[http://www.oscommerce.com](http://www.oscommerce.com)

Chrome works fine when I open that page.

---

### Post by oldsoundguy on 2010-02-23
works fine for me .. check your FF plug ins.

---

### Post by v1ad on 2010-02-23
because your default browser needs to be chrome.

---

### Post by Didius Falco on 2010-02-23
works fine for me as well, using FF 3.6

---

### Post by n0dix on 2010-02-23
Not problem here. 
Run firefox in console and post the output.

---

### Post by lovinglinux on 2010-02-23
Works for me too, Firefox 3.6 with a clean profile and with my regular profile.

Try to start Firefox in safe mode, visit that page and check if it hangs.

```
firefox -safe-mode
```

Also try a clean profile:

```
firefox -P
```

---

### Post by mvalviar on 2010-02-24
I tried with firefox -P -safe-mode. It still drains my CPU, 80-100% usage.

```

 4325 mvalviar  20   0  185m  68m  22m S   95  6.9   1:09.50 firefox            
```
```
mvalviar@mumee:~$ firefox -safe-mode -P

(firefox:4325): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:4325): GLib-WARNING **: g_set_prgname() called multiple times

```

---

### Post by lovinglinux on 2010-02-24
> **mvalviar said:**
> I tried with firefox -P -safe-mode. It still drains my CPU, 80-100% usage.

```

 4325 mvalviar  20   0  185m  68m  22m S   95  6.9   1:09.50 firefox            
```
```
mvalviar@mumee:~$ firefox -safe-mode -P

(firefox:4325): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:4325): GLib-WARNING **: g_set_prgname() called multiple times

```

Have you created a new profile after running firefox -P, or did you use the available one?

---

### Post by mvalviar on 2010-02-24
I selected "default". Let me try that again.

---

### Post by mvalviar on 2010-02-24
You're right. It works fine on a clean profile. I'll just let it go. I don't visit that sight very often anyway. 

Thanks for your help.

---

