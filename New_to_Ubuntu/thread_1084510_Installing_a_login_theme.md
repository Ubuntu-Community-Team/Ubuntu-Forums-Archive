---
title: "Installing a login theme"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by exicer on 2009-03-02
Hi,

I am trying to install a login theme (Equilibrium USPLASH _update for intrepid 2.0). I downloaded the .tar.gz archive, then dragged it into the Login Window Preferences window. However I got the following error message:

Not a theme archive
File not a tar.gz or tar archive

Could anyone explain why this is? 

Thanks!

---

### Post by theozzlives on 2009-03-02
If it's a usplash, you'll need startup manager to install it:
```
sudo apt-get install startup-manager
```

---

### Post by exicer on 2009-03-02
When I run that, I get a message:

E: Couldn't find package startup-manager


Any ideas?

---

### Post by Sirron on 2009-03-02
As theozzlives rightly pointed out, that's a USPLASH theme by the looks of it, not a login theme.

Usplash themes are for the boot screen, the one that shows when you boot up ubuntu, before the login window shows. You can still use it, but it won't show when you get to the login. Often the theme artists will create a login theme to match their usplash themes, so look at their other work and you may find one.

---

### Post by exicer on 2009-03-02
I found the corresponding login (a GDM, right?), however I get the same error when trying to install it. I am at a bit of a loss - I don't yet know enough about ubuntu to try and fix anything on my own!

---

### Post by theozzlives on 2009-03-02
K, go to Applications > Add/Remove, when that loads type "startup" in the text box. Make sure "All Applications" is selected. Put a check in the box and apply/apply.

Startup Manager will be in System > Administration, right above Synaptic. Go to the Apperance tab and click "Manage usplash", then add and navigate to your usplash (it should be a *.so file).

---

### Post by exicer on 2009-03-02
Thanks very much!

In case anyone was interested in why I could'nt install the gdm, it was because there were further .tar.gz inside the initial archive.

---

