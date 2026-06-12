---
title: "how to change dir of /var/cache/apt/archives???"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by nooor7772000 on 2009-04-03
[SIZE="4"]hi guys...

can i change the dir of synaptic manger from normal dir   /var/cache/apt/archives to another dir on my harddisk???

i want download software in another dir and also install it via synaptic manger from new dir.........how plz[/SIZE]

---

### Post by logic++ on 2009-04-03
Even though it seems to be very tricky, you could try creating a symbolic link of your desired folder pointing to /var/cache/apt/archives

```
sudo ln -s /your/desired/folder /var/cache/apt/archives
```

Before doing this you must delete the already existing /var/cache/apt/archives folder.

---

### Post by snova on 2009-04-03
> **nooor7772000 said:**
> i want download software in another dir and also install it via synaptic manger from new dir.........how plz

If you're trying to install .deb files, I believe you need only right-click on them, there is an item on the menu.

---

### Post by nooor7772000 on 2009-04-03
> **logic++ said:**
> Even though it seems to be very tricky, you could try creating a symbolic link of your desired folder pointing to /var/cache/apt/archives

```
sudo ln -s /your/desired/folder /var/cache/apt/archives
```

Before doing this you must delete the already existing /var/cache/apt/archives folder.

you are so sweaty and thanks for that):P

---

### Post by nooor7772000 on 2009-04-03
> **snova said:**
> If you're trying to install .deb files, I believe you need only right-click on them, there is an item on the menu.

thanks ;)so much and you are so sweaty too

---

### Post by asmoore82 on 2009-04-03
and you could move the old to the new location first...
```
sudo mv /var/cache/apt /new/location/apt-cache
sudo ln -s /new/location/apt-cache /var/cache/apt
```

BTW - I would recommend relocating the whole "apt" folder and not just "archives"

---

