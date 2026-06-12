---
title: "Compiling Programs from source"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Tsurugi13 on 2008-12-10
Does anyone have a basic guide on this? I keep downloading programs and getting source code I don't know what to do with. Thanks in advance!

---

### Post by halitech on 2008-12-10
normally there should be a read me file with details on how to compile from source. What exactly are you trying to install? normally its best to install from the repos if at all possible.

---

### Post by Het Irv on 2008-12-10
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

This guide should cover most of what you need.

---

### Post by Michael.Godawski on 2008-12-10
Perhaps this sounds repetitive but:

[LIST=1]
[*]Use the Add/Remove application first
[*]use the Synaptic when add/remove was not enough
[*]then search for a deb file
[*]then ask on the forums
[*]finally try to compile
[/LIST]
The usual three-step-compile-magic-trick is:
read the readme file and then:

```
.configure
make 
sudo make install **or** sudo check install
```

---

### Post by oldos2er on 2008-12-10
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

 [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

 [https://help.ubuntu.com/community/OtherWaysToInstall](https://help.ubuntu.com/community/OtherWaysToInstall)

---

### Post by Tsurugi13 on 2008-12-10
I'm trying to install Songbird 1.0, but the readme is no help at all, just a list of improvements, and there's no configure or install files. I'm lost! :confused:

---

### Post by lykwydchykyn on 2008-12-10
Download the .deb file here:
[http://www.getdeb.net/release.php?id=3519](http://www.getdeb.net/release.php?id=3519)

You don't want to start compiling things at this point.  Unlike in other OS's, the place to download programs isn't usually the developer's website (though sometimes they offer packages).  You want to get it from the repository, or from a community site that offers prepackaged versions for your distro.  Developers usually just release source code because they have better things to do than cross-compile their work for 15 different distros.

---

### Post by Michael.Godawski on 2008-12-10
Perhaps there is no need to compile. Make sure there is no install script, which can be executed with
```

chmod a+x songbird
./songbird
```

Have tried out and the method above worked for me.

---

### Post by oldos2er on 2008-12-10
Songbird is precompiled binaries.

---

### Post by Tsurugi13 on 2008-12-10
> **Michael.Godawski said:**
> Perhaps there is no need to compile. Make sure there is no install script, which can be executed with
```

chmod a+x songbird
./songbird
```

Have tried out and the method above worked for me.

It worked! Thanks for the tip!

---

