---
title: "ubuntu 8.04 doesn't load in a GUI"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by neonathon on 2010-05-09
I have installed Ubuntu 8.04 on my gateway solo 2150 laptop, but it doesn't load in an GUI. how do i get it to do so?

---

### Post by howefield on 2010-05-09
What does it load to, login prompt or error and have you installed the server edition or desktop ?

---

### Post by sadaruwan12 on 2010-05-09
> **neonathon said:**
> I have installed Ubuntu 8.04 on my gateway solo 2150 laptop, but it doesn't load in an GUI. how do i get it to do so?

Could you please give us more details about your problem.

---

### Post by neonathon on 2010-05-09
It doesn't display an error message, and i log in in text. I have installed the server edition.

---

### Post by howefield on 2010-05-09
> **neonathon said:**
> It doesn't display an error message, and i log in in text. I have installed the server edition.

If you want the full gnome desktop..

```
sudo apt-get install ubuntu-desktop
```

But there are other desktop environments, some lighter than gnome, some not.

---

### Post by tekkidd on 2010-05-09
the server edition does not include a gui. to install a gui:

for gnome ```
sudo apt-get install ubuntu-desktop
```

for kde ```
sudo apt-get install kubuntu-desktop
```

for xfce ```
sudo apt-get install xubuntu-desktop
```

---

### Post by neonathon on 2010-05-09
I typed it in and it couldnt find the file to install

---

