---
title: "how to remove gtk-1.2"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by flylehe on 2009-02-02
I think I might have accidentally installed gtk-1.2 myself and have two versions of gtk, with the other as gtk+-2.0. I want to uninstall the lower version.

How to check if it is not in used by other programs and safe to uninstall?

I find that I cannot uninstall them by "sudo apt-get remove gtk-1.2", or "sudo apt-get remove gtk+-1.2", or "sudo apt-get remove gtk1.2". It is hard for me to identify what exactly to uninstall. Even searching synaptics software manager in my ubuntu system, there will be so many software associated with "gtk 1.2", making me uncertain what to remove.

Thanks!

---

### Post by Vadi on 2009-02-02
*libgtk1.2-common* is the package you'd like to remove. If it doesn't want to remove any other programs that you use along with it, you're good to go.

---

### Post by flylehe on 2009-02-02
Thanks!

How do you locate the file to be libgtk1.2-common?

I noticed that once I check libgtk1.2-common for removal, the other two components of the library will also be marked for removal: libgtk1.2 and libgtk1.2-dev. Does it mean that checking any single component of a library always result in selecting its all components? Or I have to always to choose the one named with "-common"?

---

### Post by Vadi on 2009-02-02
Think of it as a tree structure. Common package is the root of the other packages, because they all depend on it. So if you remove that, it'll take all others with it. If you remove some other package though thats not at the root, it will only take packages that depend on it, and that's not necessarily all.

And I just read the package descriptions to find out which was the base one

---

### Post by flylehe on 2009-02-02
Thanks again!
So does single "sudo apt-get remove libgtk1.2-common" remove the other two dependencies too?

---

### Post by Vadi on 2009-02-02
Yeah.

---

