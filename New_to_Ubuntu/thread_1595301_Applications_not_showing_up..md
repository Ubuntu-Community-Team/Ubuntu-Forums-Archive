---
title: "Applications not showing up."
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Sexraider on 2010-10-13
I've attempted to install VBA-M and Gambatte using the .deb packages and after it installs I cannot find the application under "Applications" I'm trying to play some ROMs!

Why is this?

---

### Post by spikoley on 2010-10-13
The program probably isn't set up to add a menu item.  You can manually set it up.  The first thing is to find out where the program is located.

```
which program-name
```

This will return the location of the program.

1.  Right click on Applications
2.  Edit Menus
3.  Select the location you want it and click New Item
4.  Enter in the details and the complete path from the which command

Now it will show up in the menu.

---

### Post by Sexraider on 2010-10-13
Well, I tried using that command and I typed:

```

which gambatte
```

and

```

which gambatte-qt
```

Terminal didn't display anything.

What is the default path after installing using the deb?

---

### Post by dr_kabuto on 2010-10-13
You can check which files are installed with a package using synaptic. Executable are installed /usr/bin.

---

### Post by JustinR on 2010-10-13
> **Sexraider said:**
> I've attempted to install VBA-M and Gambatte using the .deb packages and after it installs I cannot find the application under "Applications" I'm trying to play some ROMs!

Why is this?

Restart your computer.

---

### Post by Sexraider on 2010-10-13
> **dr_kabuto said:**
> You can check which files are installed with a package using synaptic. Executable are installed /usr/bin.

Thank you very much.

Resolved.

---

