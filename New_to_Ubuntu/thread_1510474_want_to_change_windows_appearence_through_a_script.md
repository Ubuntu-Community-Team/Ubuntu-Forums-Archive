---
title: "want to change windows appearence through a script"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by johnrcomeau on 2010-06-15
I have a theme that I've selected from the System->Preferences->Appearance menu.  I'd like to make the changes in appearance through a script instead of interactively choosing this theme.  Is there some command-line tool that says "load a certain theme" where you'd point it to the .xml files that describe the theme?

Or are these settings done by command line either with the 'gconf-editor' or 'gconftool' program?  I am not able to see how the key/value pairs correspond to the settings I find in my .xml file.  And I can't find a good example of using either of these programs to set a key/value pair.

Thanks,
John

---

### Post by Diabolis on 2010-06-21
Check this:
```
man gconftool-2
```
and this: [http://www.packtpub.com/article/ubuntu-user-interface-tweaks](http://www.packtpub.com/article/ubuntu-user-interface-tweaks)

---

