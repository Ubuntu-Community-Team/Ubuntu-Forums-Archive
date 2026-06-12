---
title: "Starting in Terminal?"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Sgt Sc0rpi0n on 2009-02-02
When I start my computer it goes directly to a command line and not to my normal desktop. Any ideas? Any help is appreciated.

---

### Post by taurus on 2009-02-02
What happens when you run this command from a prompt, after you have logged in with your username and password?

```
startx
```

---

### Post by Sgt Sc0rpi0n on 2009-02-02
That is how I start my GUI but I want it to happen on boot.

---

### Post by Sgt Sc0rpi0n on 2009-02-02
Any ideas?

---

### Post by Crafty Kisses on 2009-02-02
Have you upgraded your kernel recently?

---

### Post by taurus on 2009-02-02
```
sudo /etc/init.d/gdm start
```

---

