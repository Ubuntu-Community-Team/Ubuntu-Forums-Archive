---
title: "Can't restore gpg key from backup"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by carloslosgrande on 2010-07-09
I have my encryption keys backed up. Have done for quite a while now.
Since doing a fresh install of Lucid I find my gpg key files aren't recognised, by that I mean when I go thru the steps to import the key files, at the folder where they are stored, "all key files" is the default setting and they do not show up. I reset it to "all files" and select the key file but it doesn't get loaded.

It all worked fine on my last install - 9.10

Obviously I'm missing something obvious here.

The seahorse site doesn't have anything.

All info appreciated.

Carl.

---

### Post by gandaran on 2010-07-09
had the same problem before and I don't know how to fix it, what I do now is just backup the home/user/.gnupg folder in a zip file then restore it every time I reinstall Ubuntu.

---

### Post by carloslosgrande on 2010-07-09
G'day Gandaran.
I had the keys backed up in a zip file but had already extracted them and I was trying to restore from that, as previously done.

Tried extracting from zip direct into .gnupg.

That did it!

Thanks a lot.
Good thing I hadn't deleted the zip file.

---

