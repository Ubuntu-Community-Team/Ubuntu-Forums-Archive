---
title: "How to uninstall vuze?"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by ltwinner on 2009-09-19
I downloaded and installed vuze from here - [http://www.vuze.com/](http://www.vuze.com/)

Can anyone tell me how to uninstall it? Thanks.

---

### Post by yabbadabbadont on 2009-09-19
How, **exactly**, did you install it?

---

### Post by Liolikas on 2009-09-19
Ah it was bad idea you you have to use Synaptic or apt-get to install things so then you can uninstall things with same ease.

But we can try just tell us what kind of file you downloaded maybe stup.exe on wine deb package source package? Something else?

---

### Post by yabbadabbadont on 2009-09-19
It looks like a linux installer in a tar.gz package.  I'm not going to download 13MB to figure it out though.  :D

---

### Post by Liolikas on 2009-09-19
>I'm not going to download 13MB to figure it out though
Actually I think you best hope is to redownload it and find something interesting in txt file.  Or sth like uninstaller.

Or more simple way just remove some shortcuts and forget it. You waste 10-100Mb space but who cares when you have hundreds Gb. Next time just command:
sudo apt-get install vuse
And do not mess with download from web pages this is old and annoying method.
apt-get remove <name> uninstalls.

---

### Post by pedro3005 on 2009-09-19
I downloaded it. It's not an installer, just already pre-compiled, you only run a script. So it is not installed. The max you should do is delete the extracted directory and search for a .vuze or .azureus on your home.
EDIT: Yeah, just checked, it's a .azureus on your home. To get rid of it just open a terminal and run:
```
rm -r .azureus
```

---

