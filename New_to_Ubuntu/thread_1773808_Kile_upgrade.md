---
title: "Kile upgrade"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by mavenuparker on 2011-06-02
I've got Kile 2.0.85 installed in 11.04 and there are a few bugs in it. These bugs are said to be fixed in 2.0.86. Can someone help me in upgrading from 2.0.85 to 2.0.86

 Found these when I was searching 
 [http://ubuntuforums.org/archive/index.php/t-1728076.html](http://ubuntuforums.org/archive/index.php/t-1728076.html)
[https://launchpad.net/~yofel/+archive/backports/+build/2489577](https://launchpad.net/~yofel/+archive/backports/+build/2489577)

Thanks

---

### Post by duke.tim on 2011-06-02
I looks like there is only 1:2.1.0~svn1112278beta-4-2ubuntu2 in the synaptic (natty). That means if you want another version you are going to need to download the source

[http://kile.sourceforge.net/download.php](http://kile.sourceforge.net/download.php)

download the version you want then
read the readme file

```
sudo make install
```

---

### Post by iclestu on 2011-06-02
> **mavenuparker said:**
> I've got Kile 2.0.85 installed in 11.04 and there are a few bugs in it. These bugs are said to be fixed in 2.0.86. Can someone help me in upgrading from 2.0.85 to 2.0.86

 Found these when I was searching 
 [http://ubuntuforums.org/archive/index.php/t-1728076.html](http://ubuntuforums.org/archive/index.php/t-1728076.html)
[https://launchpad.net/~yofel/+archive/backports/+build/2489577]("https://launchpad.net/%7Eyofel/+archive/backports/+build/2489577")

Thanks

just out of interest - what bug are you refering to?

This:

[https://bugs.launchpad.net/ubuntu/+source/kile/+bug/772631](https://bugs.launchpad.net/ubuntu/+source/kile/+bug/772631)

is the only one that I have noticed and I use kile pretty much daily (maths student). 

Just curious really....

---

### Post by mavenuparker on 2011-06-03
Yeah the same one, inserting symbols by click, command for symbol doesn't show up and auto completion of commands.

---

### Post by mavenuparker on 2011-06-17
__For i386
_[https://launchpad.net/~yofel/+archive/backports/+build/2489577](https://launchpad.net/~yofel/+archive/backports/+build/2489577)_

For AMD
[https://launchpad.net/~yofel/+archive/backports/+build/2489576](https://launchpad.net/~yofel/+archive/backports/+build/2489576)
[]("http://ubuntuforums.org/showthread.php?t=1728076")

---

### Post by lethalfang on 2011-06-26
By the way, after all those years, Kile 2.1 is finally released, and has a PPA available:
[https://launchpad.net/~kile/+archive/stable](https://launchpad.net/~kile/+archive/stable)
Rejoice!

---

