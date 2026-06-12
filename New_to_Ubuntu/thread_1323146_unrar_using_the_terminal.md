---
title: "unrar using the terminal"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Konbuntu on 2009-11-11
i downloaded a compressed file (rar)
i installed unrar using the terminal...
i would like to unrar my file through the terminal:
the file is located /Download and i want to unrar it at /Music

still learning! ;)

thanks in advance

---

### Post by syntr on 2009-11-11
unrar e /Download/archive.rar /Music

---

### Post by hictio on 2009-11-11
Open a Terminal, goto the directory that has the .rar file, and type:
```

unrar e someFile.rar ENTER

```

Then, to move what ever someFile.rar contains, for isntance, if it has a file called "file", then type:
```

mv file ~/Music ENTER

```

Be sure that there is not a file named exactly like file on ~/Music before executing the above.

---

