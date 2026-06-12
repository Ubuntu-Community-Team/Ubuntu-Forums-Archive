---
title: "how to take a hold off of a package update"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by thegoat001 on 2009-06-14
sudo echo bluez-compat **hold** | sudo dpkg --set-selections

This command put a hold on my bluez-compat package which was rolled back to a later version, I now realize this is not necessary for what I wanted to do.  I would like to take the hold off so that I can  update it with the rest of my packages through the synaptec package manager.  At the moment the bluez-compat package appears greyed out and will not update.  Any one know the terminal command to remove the hold?

---

### Post by zvacet on 2009-06-14
```
sudo aptitude unhold package_name
```

---

