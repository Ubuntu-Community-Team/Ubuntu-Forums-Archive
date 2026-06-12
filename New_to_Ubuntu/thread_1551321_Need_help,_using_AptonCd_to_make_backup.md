---
title: "Need help, using AptonCd to make backup"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by brotherlouie on 2010-08-12
hi! 
i've customized my ubuntu 10.04 just the way i like it. 
im using aptoncd to make an .iso file.
i plan to use this file to update other pc's that ill install ubuntu on. (so i don't have to re-download everything)
i used the ubuntu start script, and i want to include everything that script installed in my aptoncd .iso file. (like chrome,google earth, fonts, themes etc.)
**my question is...where do i find these folders/packages?**

im lost.
tnx alot!

---

### Post by plucky on 2010-08-12
> **brotherlouie said:**
> hi! 
i've customized my ubuntu 10.04 just the way i like it. 
im using aptoncd to make an .iso file.
i plan to use this file to update other pc's that ill install ubuntu on. (so i don't have to re-download everything)
i used the ubuntu start script, and i want to include everything that script installed in my aptoncd .iso file. (like chrome,google earth, fonts, themes etc.)
**my question is...where do i find these folders/packages?**

im lost.
tnx alot!


AptonCD copies the .deb files from **/var/cache/apt/archives**

> i used the ubuntu start script,

What is the **ubuntu start script?**

---

### Post by elliotn on 2010-08-12
Check out this post. This is better than AptonCd
 [ubuntuforums.org/showthread.php?t=819396]("ubuntuforums.org/showthread.php?t=819396")

---

### Post by mapes12 on 2010-08-13
> Check out this post. This is better than AptonCd
ubuntuforums.org/showthread.php?t=819396I have also had problems with AptonCD. An even easier GUI method is to make an installable .iso of Ubu using [Remastersy]("http://www.geekconnection.org/remastersys/ubuntu.html"). I use the "dist" option. Works like a dream.

---

