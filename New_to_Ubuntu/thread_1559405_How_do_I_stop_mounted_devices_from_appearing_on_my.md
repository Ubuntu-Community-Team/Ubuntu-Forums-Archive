---
title: "How do I stop mounted devices from appearing on my desktop?"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Rushyang on 2010-08-23
Bonjour Guys! 

As we know when we mount device, it appears on desktop automatically. I kinda don't like it. as I like nothing on my desktop.

Please advice how do I change that settings so It don't appear?

---

### Post by Calash on 2010-08-23
You can change this using Ubuntu-Tween or the built in configuration editor.

In a terminal type

```

gconf-editor

```

On the left side navigate to the following

```

apps>nautilus>desktop

```

Uncheck the "volumes_visible" option.

---

### Post by Rushyang on 2010-08-23
What a Sweet Relief!! Thanks a lot man..  It worked..!!

---

