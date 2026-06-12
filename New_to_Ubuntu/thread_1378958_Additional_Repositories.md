---
title: "Additional Repositories"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by iggy pop on 2010-01-12
Is it possible to add additional repositories like 'medibunu' for instance? If so, would someone point me towards a tutorial which covers this subject please.

---

### Post by mocoloco on 2010-01-12
[Guide here]("https://help.ubuntu.com/community/Medibuntu").  I highly recommend adding this repository, and installing [non-free-codecs]("apt:non-free-codecs").

---

### Post by konqueror7 on 2010-01-12
you may want to read [here]("https://help.ubuntu.com/community/Repositories/Ubuntu") for more info relating repositories...:o

---

### Post by iggy pop on 2010-01-12
I added the medibuntu repository but i still didn't find what i wanted .........Opera 10.10.

Although when i added the non-free-codecs any problems i had been having with Songbird and missing codecs simply vanished. Thanks guys!

---

### Post by HappyFeet on 2010-01-12
[Download Opera Here]("http://www.opera.com/download/"). Just click to install it.

---

### Post by iggy pop on 2010-01-12
Clicked the link and it appeared to have downloaded but could locate it even after doing a search of the file system? Suppose i'll have to try and work out how to unpack and install a .tar.gz file by the look of it

---

### Post by konqueror7 on 2010-01-12
by default ubuntu downloads it in your /home/<yourusername>/Downloads...

---

### Post by ThePinkWitch on 2010-01-12
> **iggy pop said:**
> Clicked the link and it appeared to have downloaded but could locate it even after doing a search of the file system? Suppose i'll have to try and work out how to unpack and install a .tar.gz file by the look of it

well good luck! I've been trying to find out how to do that for days :)

---

### Post by jamesbannon on 2010-01-12
> **iggy pop said:**
> Clicked the link and it appeared to have downloaded but could locate it even after doing a search of the file system? Suppose i'll have to try and work out how to unpack and install a .tar.gz file by the look of it

If it uses the GNU build system, it should be easy enough provided you have the appropriate developer tools installed (automake, autoconf, libtool & intltool along with the appropriate compiler support). That will require a little investigation, but all the tools are available via apt form the standard repositories from what I've seen so far.

A (very) rough guide is as follows:

[LIST]
[*]Download the appropriate tarball (by default it will download to $HOME/Downloads if you're using firefox).
[*]Create a build directory (I usually have one called Packages).
[*]Move / Copy the tarball into the directory.
[*]Extract the files with the command ```
tar -xvzf <name of the tarball file>.
```. This will extract the files to the build directory.
[*]Read the files called INSTALL and README (every GNU build should have these).
[*]Issue the command ```
./configure --help
``` and read the flags help. There will be a set of standard flags for setting the location. Usually just /usr will do, or you might want to use /opt to keep the app out of the way of the Ubuntu stuff.
[*]Issue the command ```
./configure --prefix=<install location>
```
[*]Once configure has run, type the command ```
make
```.
[*]If you are happy that the build succeeded and have tested the stuff locally, then you can install it by issuing the command ```
sudo make install
```.
[/LIST]
As I say, this is very, very rough. It would be preferable to make a debian package and install it from a local repository, but I don't know how to do that (yet).

Hope this helps.

---

### Post by mocoloco on 2010-01-12
Wait, why did you download the .tar.gz file?  Just download the "Default package" version of opera, which is a .deb.  Then double-click it to install.

---

### Post by mkvnmtr on 2010-01-12
Sounds like you might wish to go to the Getdeb page. Follow their instructions and then get Ubuntu Tweek. Getdeb and Ubuntu Tweek will give you some options that yoou might like and they are very easy to use.

---

### Post by Soul-Sing on 2010-01-12
opera comes with a .deb package from its downloadmirrors/site: double click..., or open with gdebi.

---

### Post by studmf on 2010-01-12
First simply edit your Source.list using [[COLOR=#d90d19]http://repogen.simplylinux.ch/[/COLOR]]("http://repogen.simplylinux.ch/") to create a list of wanted repositories
 
Also get
Ailurus and/or Ubuntu-Tweak
These programs make it a cinch to add additional repositories

---

### Post by jamesbannon on 2010-01-15
Thanks for all the links, guys. Appropriately bookmarked and installed.

---

