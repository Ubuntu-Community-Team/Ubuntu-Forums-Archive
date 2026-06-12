---
title: "grub : Error 17: Cannot mount selected partition"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by choko on 2009-02-01
Hello,
While booting in the grab menu I am trying to find one of my partitions with the TAB completion key, and I get the
following error

Error 17: Cannot mount selected partition

Any ideas?

(that partition mounts fine from within ubuntu, only not
from grub)

---

### Post by caljohnsmith on 2009-02-01
I think at least part of the issue is that Grub's menu file is called "menu.[COLOR="Red"]l[/COLOR]st" and not "menu.[COLOR="Red"]1[/COLOR]st", i.e. it uses a lowercase L and not the numeral 1. It would help to get some more info about your setup related to booting in order to help you, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problems might be.

---

