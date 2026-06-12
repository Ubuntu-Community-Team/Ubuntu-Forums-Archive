---
title: "ctrl+alt+backspace doesn't work"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by Mr.Kuchinawa on 2009-05-09
How do I make ctrl+alt+backspace restart gnome in 9.04?

---

### Post by Elfy on 2009-05-09
[https://wiki.ubuntu.com/X/Config/DontZap](https://wiki.ubuntu.com/X/Config/DontZap)

works for me :)

---

### Post by RedSingularity on 2009-05-09
Great....that solved my problem as well:)

---

### Post by binbash on 2009-05-09
[http://www.ubuntu-inside.me/2009/05/howto-enable-ctrlaltbackspace-on-ubuntu.html](http://www.ubuntu-inside.me/2009/05/howto-enable-ctrlaltbackspace-on-ubuntu.html)

---

### Post by nhandler on 2009-05-09
As a note, this was mentioned in the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/904") for Jaunty.

To quote,

> Ctrl-Alt-Backspace disabled by default in Xorg

The Ctrl-Alt-Backspace key combination to force a restart of X is now disabled by default, to eliminate the problem of accidentally triggering the key combination. Users who do want this function can enable it in their xorg.conf, or by running the command dontzap --disable. 

The release notes contain important pieces of information that the developers want to ensure users are aware of before installing/upgrading. You should always read them when installing a new version of Ubuntu.

---

### Post by Bios Element on 2009-05-09
> **nhandler said:**
> As a note, this was mentioned in the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/904") for Jaunty.

To quote,



The release notes contain important pieces of information that the developers want to ensure users are aware of before installing/upgrading. You should always read them when installing a new version of Ubuntu.

Funny though how upstream randomly decided to change it...I don't mean to sound a TOTAL prick but it was a stupid stupid move. It's just making it harder for people.

---

