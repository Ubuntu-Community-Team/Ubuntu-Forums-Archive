---
title: "Karmic msfonts problem"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by powel212 on 2009-11-02
I have now installed Karmic on several machines and am really enjoying a lot of the changes.

It seems that the mscorefonts package that was previously available in restricted-extras is no longer available, but when I install "ubuntu-restricted-extras" it is still trying to install these fonts from a remote directory that no longer exists.

2 questions

1. where can I get the mscorefonts to install manually?

2. Why not remove mscorefonts from the restricted-extras install process so it does not continue to give us this error and slow down installations?

I am also surprised there are not more posts regarding this. I have tried installing from several different servers on several different systems so I am sure this is not my problem alone.

Thanks

Powel

---

### Post by winotree on 2009-11-02
I believe this [http://corefonts.sourceforge.net/](http://corefonts.sourceforge.net/) may be what you're looking for but it seems to be an rpm install. 

This is from Debian [http://packages.debian.org/search?keywords=ttf-mscorefonts-installer](http://packages.debian.org/search?keywords=ttf-mscorefonts-installer) and may be a better bet.  I got it installed via *xubuntu restricted extras* which is another option for you.  

Hope this helps.  ;)

EDIT - grammar and sentence structure

---

### Post by stchman on 2009-11-02
The package msttcorefonts is available in Karmic.  It is in the Multiverse repository.

```
sudo apt-get install msttcorefonts
```

---

### Post by powel212 on 2009-11-02
> The package msttcorefonts is available in Karmic. It is in the Multiverse repository.

I have multiverse repository enabled and the problem persists.

Thanks though.

Powel

---

### Post by powel212 on 2009-11-02
> This is from Debian [http://packages.debian.org/search?ke...onts-installer](http://packages.debian.org/search?ke...onts-installer) and may be a better bet. I got it installed via xubuntu restricted extras which is another option for you. 

Thank you very much

That is exactly what I needed.

Powel

---

