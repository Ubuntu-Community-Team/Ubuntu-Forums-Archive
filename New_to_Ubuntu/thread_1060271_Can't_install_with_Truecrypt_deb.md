---
title: "Can't install with Truecrypt deb"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by imagia on 2009-02-04
I'm trying to install Truecrypt using the deb file from their site, but the file doesn't show as a .deb. Once I've extracted it from the tarball, I can't get the deb manager to do anything with it.

I managed this without any trouble a few weeks ago on Intrepid, but I've since moved back to Hardy. Other .deb downloads (like Skype) have worked fine, so any ideas what is going wrong here?

---

### Post by petervk on 2009-02-04
I think you need to run the included file.

Extract the "truecrypt-6.1a-setup-ubuntu-x86" file to a known directory.
open a terminal
```
cd /path/to/directory/
chmod +x truecrypt-6.1a-setup-ubuntu-x86
./truecrypt-6.1a-setup-ubuntu-x86
```

chmod +x makes the file executable.
./ runs the file.

Follow the prompts to extract the deb file. Then try launching the deb file to install it.

---

### Post by binbash on 2009-02-04
run the downloaded package, it will extract a deb to /tmp

---

### Post by imagia on 2009-02-04
Awesome, managed to install it now.

Thanks so much to both of you!

---

