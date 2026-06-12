---
title: "installing application"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by jimbo160 on 2009-10-30
I search for things my grandkids can play with, and find something withen the education area called "eToys". i go thru the process of installing, and after conferming installation, everything looks good. I open applications, it is there, but, when i click open, it does nothing. Can someone tell me where to go now to find out why it does NOTHING?

---

### Post by KIAaze on 2009-11-09
Run the following from a terminal:
```
/usr/games/etoys
```

Hopefully, it will give some useful error output.

P.S.: You might also be interested in this:
[Children's Games]("http://ubuntuforums.org/showthread.php?t=699338")

edit:
I got the following error message when trying to run it:
```
$/usr/games/etoys
/usr/bin/squeakvm -encoding UTF-8 -vm-display-x11 -xshm /usr/share/etoys/etoys.image 
unknown option: -xshm
```
The easy solution is to remove the "-xshm" option.
You can either launch it by command-line via:
```
/usr/bin/squeakvm -encoding UTF-8 -vm-display-x11 /usr/share/etoys/etoys.image

```
or edit "/usr/games/etoys" by replacing the line:
```
VMOPTIONS="-encoding UTF-8 -vm-display-x11 -xshm"
```
with
```
VMOPTIONS="-encoding UTF-8 -vm-display-x11"
```

The menu shortcut should then work correctly.

This should probably be reported as a bug to the etoys packagers or developers.
re-edit:
Bug already reported at [https://bugs.launchpad.net/ubuntu/+source/etoys/+bug/301190](https://bugs.launchpad.net/ubuntu/+source/etoys/+bug/301190)

---

