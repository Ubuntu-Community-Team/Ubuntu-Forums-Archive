---
title: "can't find app installed with synaptiic"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by rwarwarwa on 2009-05-16
HI there,

I just downloaded and installed Linux multimedia studio with synaptic. It doesn't appear in my applications drop down menu. I have searched for files with it's name.Can't find it.


thanks,

rwa

---

### Post by x33a on 2009-05-16
was the installation error free?

sometimes, newly installed apps don't show up in the menu.

try 
```
killall gnome-panel
```

and see if it appears in the menu.

---

### Post by chellrose on 2009-05-16
> **rwarwarwa said:**
> HI there,

I just downloaded and installed Linux multimedia studio with synaptic. It doesn't appear in my applications drop down menu. I have searched for files with it's name.Can't find it.


thanks,

rwa

In a terminal, type

```

sudo updatedb

```

This updates the search database.  You can then look for the file again using locate.  If it still isn't there, you might check Synaptic to verify that it thinks that's installed.

---

