---
title: "Need Help Installing Songbird"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by selittl on 2010-05-11
I just downloaded Songbird and (being a complete noob) I need someone to tell me how to install it.   (or any software not in the repositories for that matter.)

:confused:

Thanks

---

### Post by lrcaballero on 2010-05-11
Follow these step by step installation guide and enjoy the wonders of Songbird...

[http://www.getdeb.net/updates/Ubuntu/9.04/?q=songbird](http://www.getdeb.net/updates/Ubuntu/9.04/?q=songbird)

Luis Caballero

---

### Post by sandyd on 2010-05-11
```

wget -c http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb
sudo dpkg -i getdeb-repository_0.1-1~getdeb1_all.deb
sudo apt-get update
sudo apt-get install songbird
```

done.

The first line adds the getdeb repository (where songbird is situated)
the second one installs the repository.
the third line updates the repository.
the fourth line installs songbird.

cool huh?

---

### Post by selittl on 2010-05-11
Thanks guys.  I'm new to ubuntu and these tips help a lot.  :guitar:

---

