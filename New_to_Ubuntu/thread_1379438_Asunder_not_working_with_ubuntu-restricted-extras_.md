---
title: "Asunder not working with ubuntu-restricted-extras package?"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by Noded on 2010-01-12
First post, first eager and ignorant foray into Linux/Ubuntu, and apparently the first problem :) Sorry if this is a common one; did a quick search with didn't show much, but that may be due to my ineptitude...

I installed Asunder CD Ripper and the ubuntu-restricted-extras packages with the Synaptic Package Manager, pretty much first thing I did after installing. Now I want to rip some of my music CDs but despite the ubuntbu-restricted-extras install, Asunder still says **'lame was not found in your path'** when I try to select encoding as mp3.

Again it could (very likely) be my ineptitude but all the help documentation I've seen for dealing with mp3s in Ubuntu seem to say 'install the ubuntu-restricted-extras' package...'. The Flash elements of the install seem to work fine, judging by how I can see youtube videos and play flash games so I'm not convinced the package install didn't work, but it doesn't seem to have got me encoding mp3s. If anyone can help out and excruciatingly new user it would be hugely appreciated.

Many thanks

---

### Post by sedition on 2010-04-10
casting thread necromancy...

If it's still an issue, this should take care of it.
```
sudo apt-get install lame
```

---

