---
title: "Computer Janitor / Adobe flashplayer problems"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by VinRo on 2009-11-22
Hi , this is my first post and would appreciate help with the following.
I'm a Linux virgin and appear to have deleted / corrupted adobe flashplayer files while in computer janitor:( I now have a no entry symbol at the top telling me" an error occured please run package manager/or apt get in a terminal to see the fault(E:The package adobe-flashplugin needs to be re-installed,but i can't find an archive for it)This usually means that your installed packages have unmet dependencies!!"and Update manager will not function HELP!
 
I have Linpus lite Linux /Ubuntu 9.10 Karmic Kernel linux 2.6,31-14 generic Gnome 2.28.1 
installed on my Acer AOA 150-AB

Look forward to any help thank you .VinRo

---

### Post by zkriesse on 2009-11-22
If you know how you could try to edit the sources.list.d file and try to get the repository list through there. Or you could try sticking in the Live CD and choosing the Repair System option through the Live CD boot menu. Hope this helps. Will research your problem further though.

---

### Post by slakkie on 2009-11-22
Check my sig on updating flash.

---

### Post by wojox on 2009-11-22
Or:

```

#Remove Flash
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way

```

---

### Post by sandyd on 2009-11-22
> **wojox said:**
> Or:

```

#Remove Flash
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way

```
isnt it called flashplugin-installer now?

---

### Post by sgosnell on 2009-11-22
The easy way is to just go to [http://www.adobe.com](http://www.adobe.com), click on the button that says Get Adobe Flash Player, and let it do the install.  You'll have the latest version, and it should work.

---

### Post by VinRo on 2009-11-24
Hi ,i seem to have cured my problems by following WOJOX,S! reply advice:D!
Thank you all for your responses .(It was looking like a system restore type solution or reinstall but i'm now sorted) Best regards from a very appreciative old limey to you across the pond. Cheers VinRo:lol:

---

### Post by [A]madeus on 2009-11-29
Thank you also :)

---

