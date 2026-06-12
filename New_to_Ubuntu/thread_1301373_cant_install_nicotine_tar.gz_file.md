---
title: "cant install nicotine tar.gz file"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by houserparker on 2009-10-26
Hi people,

Im trying to install nicotine+-1.2.12.tar.gz as the version included in repos is buggy.

The problem is that all most all information on the web relating to installing packages and tar.gz/tar.bz2 files says that you need to use the script ./configure but the nicotine+-1.2.12.tar.gz file doesn't contain this file.

Does anybody know what script is needed to install nicotine+-1.2.12.tar.gz.

Any help would be appreciated.

---

### Post by fancypiper on 2009-10-26
[Check out this answer]("https://answers.launchpad.net/ubuntu/+source/nicotine/+question/84939")

Did you read the README?

---

### Post by houserparker on 2009-10-26
Yes i read the install readme but it has been written assuming the reader has good knowledge of script and the terminal.

Does anybody else have anything. There must be someone that has done this or knows something about it.

Thanks

---

### Post by Paqman on 2009-10-26
You could try installing the .deb of 1.2.12 from the Karmic repos: [click here to pick a location to download from]("http://packages.ubuntu.com/karmic/all/nicotine/download").

---

### Post by houserparker on 2009-10-26
I just tried installing the deb package with gdebi but it said the package had unsatisfiable dependencies. Anyone?

---

### Post by Paqman on 2009-10-26
The dependencies are listed [here]("http://packages.ubuntu.com/karmic/nicotine"). I did have a look at the dependencies before I recommended it, but I missed one. You'll need to install [this version]("http://packages.ubuntu.com/karmic/all/python-support/download") of python support first.

Normally this kind of thing is what your package manager does automatically, but we're cheating a bit by using the Karmic repo so we have to manage the dependencies by hand.

---

### Post by houserparker on 2009-10-26
You are a legend. It worked. Thanks for your time and help!

---

### Post by Paqman on 2009-10-26
No problem! :P

---

### Post by houserparker on 2009-10-26
Just one other thing. I want to do the same with gtk-gnutella. How did you find that deb file within ubuntu's website?

---

### Post by Paqman on 2009-10-27
Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/), you can search for any package, or you can browse the entire list (looooong).

---

