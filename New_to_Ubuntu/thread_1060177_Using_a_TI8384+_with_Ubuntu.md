---
title: "Using a TI83/84+ with Ubuntu?"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-02-04
Right now I am simply using my XpPro Virtual box to add apps to my TI84plus but I was wondering if there was an easy way to do this using just Ubuntu?...

~Jeff

---

### Post by petervk on 2009-02-04
Looks like the "tilp2" package can do some/all of this.

```
sudo apt-get install tilp2
```

---

### Post by beastrace91 on 2009-02-04
Yea I found that online and installed it... how ever how do I use it?... It did not add anything to my applications menu and running tilp2 in console yields an unknown command.

~Jeff

---

### Post by petervk on 2009-02-04
[http://packages.ubuntu.com/intrepid/i386/tilp2/filelist](http://packages.ubuntu.com/intrepid/i386/tilp2/filelist)

I think the executable is called "tilp" not "tilp2"

---

### Post by bwang on 2009-02-05
If you are using a USB DirectLink (USB on both ends), you will need to run tilp as root:

```
sudo tilp
```

---

