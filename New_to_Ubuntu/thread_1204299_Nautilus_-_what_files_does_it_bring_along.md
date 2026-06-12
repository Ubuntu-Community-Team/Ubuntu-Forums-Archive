---
title: "Nautilus - what files does it bring along?"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by marktebbutt on 2009-07-04
Hi,
I am running Xubuntu and the fact it is so lightweight is great for my laptop. However, while trying to sort out connection to a windows machine I installed Nautilus. I wasn't paying attention, and hit install, only to notice afterwards that it brings along a lot of other programs - a lot of the Gnome desktop I believe.
I would like to uninstall Nautilus, as I want to keep my system as light as possible, but I'm not sure what other programs it brings along - I'd like to uninstall those too.
Is there anybody out there who can provide a list of programs that Nautilus requires when it is installed in Xubuntu?
Thanks in advance.

---

### Post by scorp123 on 2009-07-04
```
apt-cache show nautilus
```

This should spit out all the info you need, especially the **"Depends: "** section. That's the list of extra-software that got installed along with Nautilus.

How to read that stuff ...

If it says something like ...
```
Suggests: evince | pdf-viewer ... 
```
then this means "evince OR pdf-viewer". So it could be you have one or the other.

And if it says something like ...
```
Depends: libc6 (>= 2.4) ...
``` That's clear I suppose? It wants that packge to be the same or bigger than version 2.4

Last but not least, you can simulate what would happen if you uninstalled Nautilus: ```
sudo apt-get --simulate remove nautilus
```

The "--simulate" parameter makes sure nothing happens, but it should give you a hint what else is going to be removed too.

Then there is a risky method .... Leave the "--simulate" away, trigger the command for real, but say "No" when it asks you if you are sure:

```
> sudo apt-get remove nautilus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nautilus nautilus-image-converter nautilus-share ubuntu-desktop
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 3707kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
```

This definitely will list what else it wants to remove in earnest. But _PLEASE_ make sure you know what you do and respond with "N" .... or "Y" if removing the program is really what you want.

I hope this posting helped.

---

### Post by Idefix82 on 2009-07-04
There is a program that shows which packages are not needed any more after you uninstall a package. It's precisely for those cases when installing one package fetches a lot of dependencies, then you uninstall a package and want to know what dependencies have become superfluous. Read Tips 4 and 5 in this tutorial:
[http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")

---

### Post by scorp123 on 2009-07-04
> **Idefix82 said:**
> There is a program that shows which packages are not needed any more  You don't need an extra program for that. "apt" can do that now by itself:  ```
sudo apt-get autoremove
```

"apt" will now even inform you about this when it detects redundant packages, e.g. you are actually installing something else, it could then be that "apt" will tell you something like:

```
Packages xyz were installed but are no longer required. Type
   apt-get autoremove
to automatically remove them.

```

---

### Post by Idefix82 on 2009-07-04
Can you remind me of whether xubuntu also uses Synaptic? Personally, I found it safer to use the Synaptic deborphan plugin and to check the properties (e.g. dependent packages) of the supposedly redundant packages before removing them. I have read many times on these forums that people blindly followed the suggestions of apt-get on these matters and ended up with a non-functioning system. But maybe that's also a matter of the past?

---

### Post by scorp123 on 2009-07-04
> **Idefix82 said:**
>  I have read many times on these forums that people blindly followed the suggestions of apt-get on these matters and ended up with a non-functioning system.  Good you mention that. I just had such a strange case 5 minutes ago ... :mad:

Let me put it this way: *usually* that "autoremove" thing should work as intended.... ;)

---

