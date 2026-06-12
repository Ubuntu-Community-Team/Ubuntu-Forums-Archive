---
title: "PHP5 is no-show, though installed"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by qajaq on 2009-12-18
I'm running Apache2.2 on Kubuntu 9.04, and I'm able to open my [FONT="Courier New"]index.html[/FONT] page which includes plain text, images, and links with no problem. However, PHP5 does not seem to be recognized by my set-up. I installed it with ```
apt-get install php5
``` and I saw all the usual installation lines I expect, but when I add
```
<?php

echo "Hello ... Is this thing on?";
phpinfo();

?>
```
to the [FONT="Courier New"]index.html[/FONT] file, it is completely ignored. All the text, images, links, etc., show up as usual, but absolutely nothing appears in the space where the PHP coding is written.

The [FONT="Courier New"]php5.conf[/FONT] and [FONT="Courier New"]php5.load[/FONT] files exist in the [FONT="Courier New"]...apache2/mods-available[/FONT] directory, and they are linked from the [FONT="Courier New"]...apache2/mods-enabled[/FONT] directory, and the [FONT="Courier New"]apache2.conf[/FONT] file has lines to include the contents of the [FONT="Courier New"]mods-enabled[/FONT] directory.

I'm at a loss to know where to look next. Any ideas?

---

### Post by halitech on 2009-12-18
did you restart apache after installing php?

---

### Post by travmanx on 2009-12-18
> **qajaq said:**
> I'm running Apache2.2 on Kubuntu 9.04, and I'm able to open my [FONT="Courier New"]index.html[/FONT] page which includes plain text, images, and links with no problem. However, PHP5 does not seem to be recognized by my set-up. I installed it with ```
apt-get install php5
``` and I saw all the usual installation lines I expect, but when I add
```
<?php

echo "Hello ... Is this thing on?";
phpinfo();

?>
```
to the [FONT="Courier New"]index.html[/FONT] file, it is completely ignored. All the text, images, links, etc., show up as usual, but absolutely nothing appears in the space where the PHP coding is written.

The [FONT="Courier New"]php5.conf[/FONT] and [FONT="Courier New"]php5.load[/FONT] files exist in the [FONT="Courier New"]...apache2/mods-available[/FONT] directory, and they are linked from the [FONT="Courier New"]...apache2/mods-enabled[/FONT] directory, and the [FONT="Courier New"]apache2.conf[/FONT] file has lines to include the contents of the [FONT="Courier New"]mods-enabled[/FONT] directory.

I'm at a loss to know where to look next. Any ideas?

Because you need php code to go inside a .php file :)

---

### Post by halitech on 2009-12-18
> **travmanx said:**
> Because you need php code to go inside a .php file :)

D'oh! didn't even clue into that, so used to using php for my pages I didn't even think about the OP using .html pages :redface:

---

### Post by Hospadar on 2009-12-18
You might also need to
```
sudo a2enmod php5
``` I don't thing the php5 apache module gets enabled by default (for security reasons most likely).

---

### Post by Agent ME on 2009-12-18
Did you install the [libapache2-mod-php5](apt:libapache2-mod-php5) package? You need it for PHP to work in Apache.

EDIT: Nevermind, it seems it comes with the main php5 package, so you probably already have it.

---

### Post by qajaq on 2009-12-18
Yep, it was the [FONT="Courier New"]**.php**[/FONT] extension that I needed. Many thanks!

---

