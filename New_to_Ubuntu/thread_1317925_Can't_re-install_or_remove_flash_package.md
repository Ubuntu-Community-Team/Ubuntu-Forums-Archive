---
title: "Can't re-install or remove flash package"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by OllieGab on 2009-11-07
Had some problems when trying to install flash player. It tells me I need to remove it manually but Synaptic won't open because of the "inconsistency" in the package, ie Synaptic won't open at all because of it.

The system also recommends me to re-install the flash player - but it won't because of the problem. So I can't remove it and I can't re-install it 
 
I seem to be stuck in a loop....I've just done a fresh install of 9.10 so the system should be nice and 'clean'!

Does anyone know how to remove/re-install from the command line?

---

### Post by The Funkbomb on 2009-11-07
```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper*flash*so
```

That should wipe out every flash package you have.

---

### Post by laidback on 2009-11-07
You're not alone:-

[http://ubuntuforums.org/showthread.php?t=1312126](http://ubuntuforums.org/showthread.php?t=1312126)

---

### Post by OllieGab on 2009-11-07
> **The Funkbomb said:**
> ```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper*flash*so
```

That should wipe out every flash package you have.

None of the above sorted the problem. When trying to open the Synaptic I get this error message:
"E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it."

When I tried to install the Ubuntu Add/Remove application from the Software Centre I got the message:
"E:I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.:

---

### Post by OllieGab on 2009-11-07
There may something more serious going on....?

When I opened the Update Manager I got this error message:
"Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

So how do I fix that??? I did the "sudo apt-get...." but just got the same message abut not finding an archive.

---

### Post by oldos2er on 2009-11-07
Do you have all repositories enabled?

---

### Post by mac9416 on 2009-11-07
Hey, OllieGab,

I have seen several people with this problem, and in each case these commands have solved it:

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree # Installs flashplayer the easy way 
```

Hope that helps!

---

### Post by phillw on 2009-11-07
> **mac9416 said:**
> Hey, OllieGab,

I have seen several people with this problem, and in each case these commands have solved it:

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree # Installs flashplayer the easy way 
```Hope that helps!


So do I, coz the other method is scary. :lolflag:

It's hiding over here  -->>>>   [http://ubuntuforums.org/showthread.php?t=1305829](http://ubuntuforums.org/showthread.php?t=1305829)

I'm hoping the above method sorts it out, because that one is pretty darn serious stuff, and could really break your computer. If you think it is something that you HAVE to do, please get a hold of me first and I'll check your problem out against that solution.

Phill.

---

### Post by OllieGab on 2009-11-08
The problem is now solved...partly because of my own "inability" to check various things.
As mentioned in an earlier message I had a "Software index broken...." problem and started to look around in various Administration areas. For some reason the Software source was set to 'local server'. After changing that to 'main' the Add/Remove application managed to find all the necessary packages and re-installed flash player without any hitches.

---

### Post by mabtifro2 on 2011-12-10
> **mac9416 said:**
> Hey, OllieGab,

I have seen several people with this problem, and in each case these commands have solved it:

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree # Installs flashplayer the easy way 
```

Hope that helps!

brilliant!!!! thank you so much, worked magic on my lubuntu 11.10!!!

---

### Post by oldos2er on 2011-12-10
Closed, necromancy.

---

