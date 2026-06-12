---
title: "Can't check source code in software sources"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by Vexiphne on 2010-12-30
I tried to install GIMP today and I got the message "Requires installation of untrusted packages". So I checked software sources and for some reason source code was suddenly not marked and when I tried to mark it, it wouldn't let me.

Does anyone know why and how I can fix this?

---

### Post by Wobblybob on 2011-01-02
you could try installing or re installing the ubuntu-keyring and ubuntu-extras-keyring packages in synaptic.

---

### Post by oldos2er on 2011-01-02
You can enable the source code repos manually, run ```
gksu gedit /etc/apt/sources.list
``` and remove the comment mark # from the deb-src repos you want.

The "untrusted packages" warning means you're missing a gpg key for one of your repos. See [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

### Post by Vexiphne on 2011-01-04
> **oldos2er said:**
> You can enable the source code repos manually, run ```
gksu gedit /etc/apt/sources.list
``` and remove the comment mark # from the deb-src repos you want.

The "untrusted packages" warning means you're missing a gpg key for one of your repos. See [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

Thank you. That helped :)

---

### Post by Add1cken on 2011-04-08
> **oldos2er said:**
> You can enable the source code repos manually, run ```
gksu gedit /etc/apt/sources.list
``` and remove the comment mark # from the deb-src repos you want.

The "untrusted packages" warning means you're missing a gpg key for one of your repos. See [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

thanks mate, did the trick for me to.

---

### Post by AndrewC312 on 2012-01-23
Hello, I'm sorry if this is something obvious that I'm missing but I am not very knowledgeable with this sort of thing. I'm having the same problem with being unable to check source code, but I'm not really sure what you did to fix it. I ran that line of code and the "sources.list" file opened. Is there to supposed to be a # mark to the left to the deb-src that I want to enable?

---

### Post by oldos2er on 2012-01-24
Comment mark # in place, repository is disabled. Remove the comment mark to enable the repository.

---

