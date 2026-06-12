---
title: "GPG key"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by t4ggs on 2008-12-27
Hi,I'm installing a package and the instruction here:
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

said that after adding the repository to /etc/apt/sources.list, the signed GPG key for identification of the repository is: wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -

what should I do with that?? I don't know... how do I add it??

---

### Post by ercferret18 on 2008-12-27
just paste that command into the terminal...

---

### Post by HotShotDJ on 2008-12-27
> **t4ggs said:**
> what should I do with that?? I don't know... how do I add it??Open Applications --> Accessories --> Terminal and then paste that line in.  When it asks for your password, enter it and press enter.  Barring any error messages, just type exit when it is finished.  Voila!

---

### Post by Michael.Godawski on 2008-12-27
```
wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -
```
Copy this command into the terminal and hit enter.

---

### Post by t4ggs on 2008-12-27
Thanks to all of u

---

