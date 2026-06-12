---
title: "Gzip"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by Frogs Hair on 2010-04-19
Hi 

Do I need to install 7ZIP to extract a GZIP  file ?

---

### Post by mcduck on 2010-04-19
No, gzip is already installed by default. Just right-click a gzip archive and select "Extract", or use the gunzip command in a terminal.

---

### Post by e4uforums on 2010-04-19
You should be able to do it with built in tools.

Right click on the archive and choose "extract here" - this should do the trick.

Here is more information on gzip and Linux:

[http://lowfatlinux.com/linux-gzip-gunzip.html](http://lowfatlinux.com/linux-gzip-gunzip.html)

---

### Post by Frogs Hair on 2010-04-19
Thanks

The reason I asked is that I get an error when I try and extract the file . I will down load a new one and try again.

---

### Post by iponeverything on 2010-04-19
If you use gunzip from the command line, the error might be bit more verbose..

---

### Post by oldos2er on 2010-04-19
> **Frogs Hair said:**
> The reason I asked is that I get an error when I try and extract the file

It might help if you shared the error msg with us.

---

### Post by Frogs Hair on 2010-04-19
The file is a theme found at  Gnome Look.Org. I tried a different package but got the same error message.

---

### Post by atomizer on 2010-04-19
I think you can drag/drop the file directly into your "appereance preferences" window. It will be installed automaticly.

---

### Post by oldos2er on 2010-04-19
> **Frogs Hair said:**
> The file is a theme found at  Gnome Look.Org. I tried a different package but got the same error message.

That is one unhelpful error msg. Maybe atomizer's suggestion will work.

---

### Post by mcduck on 2010-04-19
> **Frogs Hair said:**
> The file is a theme found at  Gnome Look.Org. I tried a different package but got the same error message.

That message would indicate a corrupted package.

Could you give us a link to the theme you are trying to download, so that we can test if the problems is with the package on gnome-look.org or if it's something that's wrong with your system?

(and no, trying to just drag&drop the package into Appearance dialog is not likely to work, as it really just unzips the package into ~/.themes using the very same tools you already tried to use...)

---

### Post by Frogs Hair on 2010-04-19
> **mcduck said:**
> That message would indicate a corrupted package.

Could you give us a link to the theme you are trying to download, so that we can test if the problems is with the package on gnome-look.org or if it's something that's wrong with your system?

(and no, trying to just drag&drop the package into Appearance dialog is not likely to work, as it really just unzips the package into ~/.themes using the very same tools you already tried to use...)


[URL="http://dermamred.deviantart.com/IDoLikeIt2Much-154340271"]
[/URL]

---

### Post by Frogs Hair on 2010-04-19
My Link did not work I will check it again.

---

### Post by Frogs Hair on 2010-04-19
I just downloaded another theme that I like also, as a test, and extracted it without issue.
I think the first package is possible corrupt download, both are GZIP.

---

