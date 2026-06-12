---
title: "Apache question(s)"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-03-24
I am new to Ubuntu

When I install Apache, is there a way to tell if it is running or not?  How do I actually start it? Does it start automatically?

Also, where do the html files go?

---

### Post by cipherboy_loc on 2011-03-24
First of all, to check if it is running:
```

ps aux | grep -i 'apache'
# Or
nmap localhost

```

How to start it:
```

sudo /etc/init.d/apache2 start

```

How to get it to start at boot:
```

sudo update-rc.d apache2 defaults

```


Where to put the HTML files? The default is /var/www/ (you can create sub directories as needed), but some people change that to /srv/www/example.com, or just /srv/www. If needed, I could post an example on how to move it.


Cipherboy

---

### Post by alphacrucis2 on 2011-03-24
> **Learning Linux 2011 said:**
> I am new to Ubuntu

When I install Apache, is there a way to tell if it is running or not?

```
service apache2 status
```

> How do I actually start it?


```
sudo service apache2 start
```

> Does it start automatically?

Should do.

> Also, where do the html files go?

/var/www/

---

### Post by Learning Linux 2011 on 2011-03-25
Wow, thanks, that was exactly what I was looking for!

---

