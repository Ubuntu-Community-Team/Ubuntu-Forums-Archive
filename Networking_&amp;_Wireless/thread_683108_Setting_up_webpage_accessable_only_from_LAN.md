---
title: "Setting up webpage accessable only from LAN"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by inoesomestuff on 2008-01-30
What is the best way to set up a website viewable only by LAN? Or separate a seperate website viewable from the internet. I saw another post about using apache and I will look more into that. Is there any forum type software that is free (other than phpBB) Im looking for something that will be supporting very few users but has is capable of logging whos has visited to host a private forum and blog. Does anyone know any good tutorials for this?

Thanks in advance

---

### Post by mpokrywka on 2008-01-30
You can restrict access to directories in apache configuration, for example:
```

<Directory /var/www/private_forum/>
    Order deny,allow
    deny from all
    allow from 192.168.1.0/255.255.255.0
</Directory>

```
then install forum in directory /var/www/private_forum/ and only hosts from LAN (192.168.1.*) will be able to access...

---

### Post by inoesomestuff on 2008-02-01
i just installed php and apache, is there a place where i can find a good beginners guide? ive tried googling ubuntu apache tutorial and no luck so far, either they detail the installation process (like apt-get stuff) or installing modules (im not that far yet).

---

