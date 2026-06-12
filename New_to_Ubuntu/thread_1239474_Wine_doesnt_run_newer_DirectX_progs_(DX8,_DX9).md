---
title: "Wine doesnt run newer DirectX progs (DX8, DX9)"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by Kaymeerah on 2009-08-13
Hello, Wine doesn't launch any newer directx progs, like directx 8 and directx 9 and spits out this:

```

err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1

```

Do u guys have any ideas?

---

### Post by coldReactive on 2009-08-13
The wine guys might know:

[http://forum.winehq.org/viewforum.php?f=2](http://forum.winehq.org/viewforum.php?f=2)

---

### Post by Kareeser on 2009-08-13
Could be stagnant development on porting D3D calls to OpenGL. Best bet is to raise it up as an issue on their forum, and check the AppDB for your program.

---

### Post by NightwishFan on 2009-08-13
You can install the latest version of Wine using this Ubuntu tutorial. I always use the development version.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

I play some DirectX 9 games, such as Battle For Middle Earth 2, and I get good performance. My card is an Integrated Nvidia 6150SE, which is terrible. Performance is about equal or greater than Windows Vista using Nvidia 185 drivers. :P

Currently using Wine 1.1.27

---

### Post by Kaymeerah on 2009-08-13
its all the progs, anyways i degraded to 1.1.26..works now

---

