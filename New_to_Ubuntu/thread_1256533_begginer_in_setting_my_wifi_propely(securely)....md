---
title: "begginer in setting my wifi propely(securely)..."
date: 2009-09-02
forum: New to Ubuntu
---

### Post by heyyy on 2009-09-02
speaking of wireless security if i "hide" my wifi would that be any good?
also could you recommend me a link or two to set up my wireless properly(securely)?

---

### Post by gn2 on 2009-09-02
> **heyyy said:**
> speaking of wireless security if i "hide" my wifi would that be any good?

No, it makes no difference.

> **heyyy said:**
> also could you recommend me a link or two to set up my wireless properly(securely)?

That depends on what router you have.
You need to enter the configuration pages, set it to WPA2 (if possible) and set a strong password.
Then enter the password in Network Manager.

---

### Post by Bachstelze on 2009-09-02
> **gn2 said:**
> 
You need to enter the configuration pages, set it to WPA2 (if possible)

And if it is not, get another router. Really. When people say WEP and WPA1 are now compromized, it's true. You don't need to be a genius hacker to crack them, just know how to use Google and paste a few commands in a terminal.

---

### Post by heyyy on 2009-09-02
> **gn2 said:**
> No, it makes no difference.



That depends on what router you have.
You need to enter the configuration pages, set it to WPA2 (if possible) and set a strong password.
Then enter the password in Network Manager.

ok thanks
and how many characters makes a good password?

---

### Post by Bachstelze on 2009-09-02
> **heyyy said:**
> ok thanks
and how many characters makes a good password?

```
sudo apt-get install makepasswd
makepasswd --crypt-md5
```

and use the one given in the second field. It should be good. ;)

If you need to remember the password, use makepasswd --chars 16. It will create a password with 16 characters containing only alphanumerics.

---

