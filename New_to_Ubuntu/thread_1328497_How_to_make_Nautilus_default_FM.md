---
title: "How to make Nautilus default FM?"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by ovroniil on 2009-11-16
I've installed the Karmic and I've also installed the LXDE in Karmic. But when I run the PC in GNOME environment, I don't get Nautilus as my default File Manager. Instead I am getting PCman everytime. 

Can anyone please tell me, How can I restore Nautilus in GNOME environment?

---

### Post by philinux on 2009-11-16
Open gconf-editor.

Locate the key:-

/desktop/gnome/applications/component_viewer/exec

Change to nautilis %s

---

### Post by ovroniil on 2009-11-16
> **philinux said:**
> Open gconf-editor.

Locate the key:-

/desktop/gnome/applications/component_viewer/exec

Change to nautilis %s

Well... in my case that value is already **nautilis %s**

---

### Post by ibuclaw on 2009-11-16
> **philinux said:**
> Open gconf-editor.

Locate the key:-

/desktop/gnome/applications/component_viewer/exec

Change to nautilis %s

It is actually gnome-session that controls which is the default file manager now.

The actual location of the key is here:
```
/desktop/gnome/session/required_components/filemanager
```
Just setting that to "nautilus" will do.

Regards
Iain

---

### Post by ovroniil on 2009-11-16
> **tinivole said:**
> It is actually gnome-session that controls which is the default file manager now.

The actual location of the key is here:
```
/desktop/gnome/session/required_components/filemanager
```Just setting that to "nautilus" will do.

Regards
Iain

But in my case the filemanager is set to **nautilus** too! And I still have the PCman as my default FM. :(

---

### Post by ovroniil on 2009-11-22
Never mind... just removed the PCman, so Nautilus is back! I didnot find any other way to make Nautilus default over PCman.

---

### Post by zahnac on 2009-11-26
How do you un-install PC Man?

 I am having the same problem after installing LXDE, (suggestions above don't work). I tried to un-install PC man via Software Centre, but it claims its Not installed.

Thanks

:confused:

---

### Post by Bölvaður on 2009-11-26
System &#8594; Administration &#8594; Synaptic Package Manager

use the edit box to filter out the packages you are looking for (pcman), it's pretty straight forward after that.

---

### Post by LoREZ on 2009-11-28
I've had the same problem, only my solution can't be as simple as removing pcman, because I use it for Openbox.  I use both Openbox and Gnome, depending on the need of the moment.  Just like the op, those settings all already say nautilus, but when I execute a file it opens pcman.  Anyone have another solution?

---

### Post by ovroniil on 2009-11-28
I used the apt-get command
```
sudo apt-get remove pcman
```

---

### Post by LoREZ on 2009-11-28
I already know how to manage packages; that's not my problem.  I use PCman for Openbox, and I can't use Nautilus there because it screws with my background and makes my gnome desktop icons appear.  I suppose I could use an alternative to PCman, but it really is the best low-resource file manager for my purposes.  Somewhere PCman is overriding the settings in gnome and placing itself as default, which is a new behavior.  It should be fixable somehow.  Plus, I don't like it when software wins... ;)

---

