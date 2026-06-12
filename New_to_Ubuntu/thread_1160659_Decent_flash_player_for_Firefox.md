---
title: "Decent flash player for Firefox?"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by chilimac02 on 2009-05-15
The default flash player for Firefox is giving me fits. I want to uninstall it and then install a good one, like the adobe one... How do I do such a thing?

-Justin

---

### Post by mikewhatever on 2009-05-15
There is no default flash player. You must explicitly install one first. Do provide more info on what is going on.

---

### Post by Ericyzfr1 on 2009-05-15
> **chilimac02 said:**
> The default flash player for Firefox is giving me fits. I want to uninstall it and then install a good one, like the adobe one... How do I do such a thing?

-Justin

Uninstall the one you have in Synaptic or Add/Remove. Then go on a site where flash player is required and follow the prompt.

---

### Post by Bölvaður on 2009-05-15
There is no one installed by default, but the one in ubuntu-restricted-extras, a package named flashplugin-nonfree is the adobe flash player.

if you have 64 bit ubuntu please google "adobe flash linux 64" it is the only 64 bit version for any os, and is still in beta. But it is very good even though it is "just" beta.
In the package on the flash site you'll get the plugin (the name ends with .so) which you'll have to place into /usr/lib/firefox/plugins

if you placed the .so file onto your desktop you can run this command
you can Alt+F2
```
gksu nautilus ~/Desktop
``` and cut it and paste into the correct folder.

or alternatively you can open the terminal and run this command (you'll have to place the .so file onto your desktop and write the name of that file here)
```
sudo mv ~/Desktop/NameOfFile.so /usr/lib/firefox/plugins
```

---

### Post by Bölvaður on 2009-05-15
which graphical card are you using?
I have a hunch


command to tell us exactly what you got:

```
lspci | grep vga
```

---

### Post by chilimac02 on 2009-05-17
vga card:
VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
I have version 180 installed (driver)

---

### Post by chilimac02 on 2009-05-17
I uninstalled (synaptic) swf codec for firefox. Everything works fine now... :) happy happy joy joy

---

