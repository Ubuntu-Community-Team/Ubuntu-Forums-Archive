---
title: "Problem removing package"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by Goat Boy on 2010-06-02
Beginner here, ran into a roadblock.Donwloaded Geany off of their website and installed.  Don't like it, trying to remove.

Synaptic does not display Geany as installed, tried installing and uninstalling, no change.
Sudo apt-get remove geany doesn't work, says package isn't present.

Any other suggestions on how to get rid of this thing?  I'm on Lucid.

Not even going to start with the nightmare trying to get codeblocks to run, that'll be another day.

Thanks.

---

### Post by sandyd on 2010-06-02
> **Goat Boy said:**
> Beginner here, ran into a roadblock.Donwloaded Geany off of their website and installed.  Don't like it, trying to remove.

Synaptic does not display Geany as installed, tried installing and uninstalling, no change.
Sudo apt-get remove geany doesn't work, says package isn't present.

Any other suggestions on how to get rid of this thing?  I'm on Lucid.

Not even going to start with the nightmare trying to get codeblocks to run, that'll be another day.

Thanks.

You installed geany from their site, not from the repos. Therefore, you cannot remove it VIA the package manager.

how did you install it from their site?

---

### Post by Goat Boy on 2010-06-02
> **carlee said:**
> You installed geany from their site, not from the repos. Therefore, you cannot remove it VIA the package manager.

how did you install it from their site?

Downloaded and sudo dpkg -i *.deb I think it was if I've remembered correctly?

---

### Post by sandyd on 2010-06-02
> **Goat Boy said:**
> Downloaded and sudo dpkg -i *.deb I think it was if I've remembered correctly?
thats impossible because the geany site does not provide debs

in fact, the geany site does not provide any linux binaries.

if you downloaded it from the geany site, you would have had to compile the source code, and then install it.

---

### Post by Goat Boy on 2010-06-02
Woof.  That was one of 9,622 Code::blocks attempts.

[http://www.geany.org/Download/Releases](http://www.geany.org/Download/Releases)

[geany-0.18.1.tar.gz]("http://download.geany.org/geany-0.18.1.tar.gz")

$ ./configure
$ make
Then as root:
 % make install

Thanks  much for help.  :)

---

### Post by sandyd on 2010-06-02
> **Goat Boy said:**
> Woof.  That was one of 9,622 Code::blocks attempts.

[http://www.geany.org/Download/Releases](http://www.geany.org/Download/Releases)

[geany-0.18.1.tar.gz]("http://download.geany.org/geany-0.18.1.tar.gz")

$ ./configure
$ make
Then as root:
 % make install

Thanks  much for help.  :)
go back into the folder that you ran ./configure from (and this **might** work, and i might not depending on how geany writes some of its files)

```

sudo make uninstall

```

and yea... thats compiling from source code.

---

### Post by Goat Boy on 2010-06-02
Thank you thank you thank you.

Got codeblocks working too!  :P

---

### Post by marshmallow1304 on 2010-06-02
You might want to look into checkinstall in the future.  You use it in place of
```
make install
```

It creates a deb from compiled sources and installs it (by default) so you can then easily remove the program via the package manager.

---

