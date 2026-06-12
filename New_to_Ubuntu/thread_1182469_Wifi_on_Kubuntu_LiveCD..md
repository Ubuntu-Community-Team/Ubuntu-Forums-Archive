---
title: "Wifi on Kubuntu LiveCD."
date: 2009-06-09
forum: New to Ubuntu
---

### Post by Bios Element on 2009-06-09
So I've got working wifi on an Ubuntu install and Ubuntu/Linux Mint LiveCD's. Problem is when I load up Kubuntu it can see the Wifi network but never accepts my password.

My Wifi is WEP Key on Open System 1. Anything I should know about configuring it for Kubuntu? It makes it basically impossible to even see if I want to install it alongside ubuntu.

---

### Post by Bios Element on 2009-06-09
Hmm, No luck?

---

### Post by Bios Element on 2009-06-15
Hmm, I find it hard to believe I'm the only one who's had this problem. >.>

---

### Post by izizzle on 2009-06-15
I had this problem. the fix for me was a bad CD. Try checking your cd for defects or try an md5 comparison.

---

### Post by shifty_powers on 2009-06-15
frankly the network manager plasmoid in kde is crap. It has been nothing but a headache for me whenever i have used it.

My advice? Install gnome network manager, which will install itself and remove the kde version.

```
sudo apt-get install network-manager-gnome
```

Pretty much always sort my problems...

---

### Post by izizzle on 2009-06-15
If you don't want to install the gnome libs, WICD is always a great choice (it's what I use).

```
sudo apt-get install wicd
```

---

