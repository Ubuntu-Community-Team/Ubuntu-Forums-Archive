---
title: "Chromium and Flash"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by Dobbie03 on 2009-08-07
I have just installed Chromium and I am having a hard time getting Chromium to start with all the plugins.

Supposedly I need to add this "--enable-plugins" to the Chromium shortcut, how do I do that?

---

### Post by coolbrook on 2009-08-07
System > Preferences > Main Menu > Internet

Right click Chromium Browser

Select _P_roperties

and under Command

chromium-browser --enable-plugins %U

---

### Post by Dobbie03 on 2009-08-07
Thanks but still no bloody flash player.

---

### Post by coolbrook on 2009-08-07
I followed these steps:

[http://webupd8.blogspot.com/2009/07/how-to-enable-flash-support-for.html](http://webupd8.blogspot.com/2009/07/how-to-enable-flash-support-for.html)

Under **"To enable Flash support:"**

I had to choose a different source path for copying the libflashplayer.so file to the Chromium plug-in folder.

```

sudo cp /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/chromium-browser/plugins

```

---

### Post by Dobbie03 on 2009-08-07
Awesome! its working thanks for your help.

---

