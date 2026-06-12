---
title: "find executable path"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by flylehe on 2009-09-02
Hi,
I want to know how to get the location of an executable, if I can run it directly in bash? For example, I can run emacs directly like this
```

$ emacs

```
How can I know where this executable is?

Thanks and regards!

---

### Post by st33med on 2009-09-02
Most of the binaries are stored in /usr/bin, /bin, or /usr/local/bin.

---

### Post by slakkie on 2009-09-02
man which
man whereis
man find
man locate

These are commands to find stuff. Beware that which and whereis work based on what you have set in your PATH env. variable. So if you don't have a PATH set, it will not find the binary.

---

### Post by Volt9000 on 2009-09-02
Use the whereis command.

```

whereis emacs

```

This will show you all paths relevant to emacs. As st33med said, the main executable will usually be located in some 'bin' directory.

---

