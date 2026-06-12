---
title: "Multiple Ubuntu options at start up"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by dpgriff on 2011-02-12
I installed the ubuntu netbook remix on netbook and dual boot with windows. After doing an update for ubuntu today I noticed that there even more start up options when I turn the computer on. It looks something like this if I remember correctly
linux 2.6.35-25
linux 2.6.35-25(recovery mode)
linux 2.6.35-24
linux 2.6.35-24(recovery mode)
linux 2.6.35-22
linux 2.6.35-22(recovery mode)
win 7

Does anyone know why this is and how I can fix it?

---

### Post by Foxheadz on 2011-02-12
There just old linux kernels you should probably run ```
sudo apt-get autoremove
``` There is a command for removing old menu entries from grub but I do not know it. TO GOOGLE!

---

### Post by zhogan85 on 2011-02-14
I think to remove the older entries from grub, you can simply go to synpatic, and search for linux-image, and then remove the older ones. I have also read that it is prudent to keep the most recent two, rather than only the most recent. I haven't done this before but I have the same amount of entries as you when I boot up and I think I will do this right now to see if I can clean it up too. Hope this was helpful. For more info, as the previous poster suggested, a google search will return heaps of results, many that go into way more detail.

---

### Post by Kirboosy on 2011-02-14
[COLOR=Red]**Welcome to the Forums! :D**[/COLOR]

Even easier. Download [Ubuntu Tweak]("http://ubuntu-tweak.com/")

It will allow you to clean up cache and old kernels easily. All through a simple, nice GUI. :)


Hope that helps

~Caboose

---

### Post by zhogan85 on 2011-02-14
Here was a particularly thorough and informative thread.

[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

---

### Post by presence1960 on 2011-02-14
> **zhogan85 said:**
> I think to remove the older entries from grub, you can simply go to synpatic, and search for linux-image, and then remove the older ones. I have also read that it is prudent to keep the most recent two, rather than only the most recent. I haven't done this before but I have the same amount of entries as you when I boot up and I think I will do this right now to see if I can clean it up too. Hope this was helpful. For more info, as the previous poster suggested, a google search will return heaps of results, many that go into way more detail.

Also remove linux-headers

Please note from Syanaptic if you mark them for Removal they will be uninstalled, but the packages will remain in cache. If you Mark For Complete Removal it will uninstall and remove the packages from cache- thus if you later want to reinstall them you will have to download them again.

---

### Post by hansolo4949 on 2011-02-14
+1 Ubuntu tweak. I have found that it is just about the easiest way to remove old Linux kernels. All you have ti di is mtyoe un your password after selecting the ones you want to remove and presto! All cleaned up.

---

