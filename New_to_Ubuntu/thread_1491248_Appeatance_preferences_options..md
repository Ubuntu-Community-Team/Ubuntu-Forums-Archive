---
title: "Appeatance preferences options."
date: 2010-05-23
forum: New to Ubuntu
---

### Post by bob brazie on 2010-05-23
Two fresh instillations of 10.04 on two different machines..

One has a “custom” option in right click on a blank desktop area “change desktop background”
in the “visual effects” tab.

One has none, normal, extra and custom.

The other installation does not have the “custom option”

It's a cool option and I would like it to be on both machines is possible.

I did install the CompizConfig Settings manager in both installations and can't find anything there but maybe I am missing something.

Maybe a video card/driver difference that the installation detected?

Any ideas? Thanks in advance.

---

### Post by themusicalduck on 2010-05-23
You need to install the simple-ccsm package.

```
sudo apt-get install simple-ccsm
``` in a terminal, or search for it in synaptic.

---

### Post by bob brazie on 2010-05-23
Thanks, that did the trick. it seems I installed the simple-ccm on one machine and not the other.

I also see that if you install just the simple package it also installs the other full CompizConfig Settings Manager too. They both show up in system/preferences area.

Not sure why.

Thanks again for the help.

---

