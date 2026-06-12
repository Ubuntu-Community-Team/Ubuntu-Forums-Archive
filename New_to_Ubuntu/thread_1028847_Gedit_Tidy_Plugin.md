---
title: "Gedit Tidy Plugin"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by animeshb on 2009-01-02
Hi,

I am having trouble using the Tidy Plugin in Gedit. Tidy is installed. HTML-Tidy is in the gedit plugins directory. It appears in the plugins list in gedit preferences, but it is grayed out as soon as I try to select it. I have tried searching the forums but a solution could not be found for the problem.

Please Help.
Thanks.

---

### Post by blueridgedog on 2009-01-02
What version of Ubuntu are you running?  Here is a conversation about 18 months ago about your problem:

[http://ubuntuforums.org/archive/index.php/t-460063.html](http://ubuntuforums.org/archive/index.php/t-460063.html)

Perhaps you have an oder version of Tidy?

---

### Post by animeshb on 2009-01-02
> **blueridgedog said:**
> What version of Ubuntu are you running?  Here is a conversation about 18 months ago about your problem:

[http://ubuntuforums.org/archive/index.php/t-460063.html](http://ubuntuforums.org/archive/index.php/t-460063.html)

Perhaps you have an oder version of Tidy?

I am using Intrepid and installed Tidy from Synaptics and the plugin from the site today. I have read that conversation and there seemed to be no solution provided in that thread.

When I was extracting the plugin into gedit-plugins folder, I did not allow me to do so. So I used ```
gksudo nautilus
``` command to browse the directories as root and extracted the plugin into the requisite folder. After doing this:
1) the html-tidy plugin showed up in the gedit plugins and but was disabled.
2) when I navigate to the plugins folder, the html-tidy folder has the emblem X on it, saying it is not possible to display the contents when clicked.

---

### Post by blueridgedog on 2009-01-02
I am just guessing...

Perhasp the plugin has the wrong permission?  perhaps running ls -al in the plugins folder will reveal that either the owner of the plugin or the permission are off?

---

### Post by animeshb on 2009-01-03
> **blueridgedog said:**
> I am just guessing...

Perhasp the plugin has the wrong permission?  perhaps running ls -al in the plugins folder will reveal that either the owner of the plugin or the permission are off?

it is like this:

drwx------ 4 root    root      4096 2009-01-02 20:06 **html-tidy**
-rw-r--r-- 1 animesh animesh    225 2007-04-28 06:11 html-tidy.gedit-plugin

**html-tidy** is the directory.

---

### Post by blueridgedog on 2009-01-03
Still just guessing mind you, but you may want to try taking ownership of the directory or setting the permissions so everyone can read it.  Right now root owns it and it is private.

Try going to the parent directory and changing the permission on the html-tidy directory with:

```
sudo chmod 777 ./html-tidy
```

---

### Post by jruberto on 2012-12-27
It's an old thread but still a relevant topic, hopefully this saves someone some troubleshooting time.

You gotta save your file as an HTML document before Tidy will allow itself to run -- otherwise it is on the menu, but disabled.

Also in the plugin's preferences, you can specify which MIME types or file extensions Tidy should be active on.

---

### Post by oldos2er on 2012-12-27
Old thread closed, please don't bump old threads.

---

