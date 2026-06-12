---
title: "Allowing permission"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by Wrathe on 2009-10-25
Hey,

I want to install Flash Player as a plug-in on Firefox.  On the flash website it says to copy the file to /usr/lib/firefox/plugins.  I try to copy the file but it comes up and says:

> There was an error copying the file to /usr/lib/firefox/plugins.  Error opening file 'usr/lib/mozilla/plugins/libflashplayer.so': Permission denied.Can anyone help me to allow permission and to copy it to the location.  I do not mind using terminal.

---

### Post by Soulcage on 2009-10-25
sudo cp -v (souce location & file name) (destination location & file name)

---

### Post by skbhat03 on 2009-10-25
In Ubuntu, you cannot execute commands by default. As you are not root.
 
As stated above you will have to use *sudo* at the beginning of the command line.

---

### Post by nothingspecial on 2009-10-25
You could just 

```
sudo apt-get install ubuntu-restricted-extras
```

Which will install the flash plugin and a whole bunch of other groovy stuff.

---

