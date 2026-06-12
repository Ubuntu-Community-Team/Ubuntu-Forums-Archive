---
title: "Adobe Air"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by loyaleagle on 2009-02-02
Hey just a question

I went to the Adobe AIR site and installed the AIR bin file. It shows in my menu and stated it installed correctly. I run Ubuntu 64 8.10. When I try to install an air app... nothing happens. Same when I try to install it using the AIR installer. 

Now my question. It was my understanding that AIR now worked well with 64 or am I wrong and I have to install it using the 32 bit method with the extra libs and changes.

Thanks...

---

### Post by 2hot6ft2 on 2009-02-02
I don't know the answer to your question but here's the fix for what you'll find it did later.
Add/Remove Program List Empty?
Applications>Add/Remove

Did you just install Adobe Air and/or the new BBC iPlayer Desktop? Seems to be happening a lot lately. To fix it go to

Applications>Accessories>Terminal
and use
```
sudo apt-get --reinstall install gnome-app-install
```

---

### Post by loyaleagle on 2009-02-03
No I just used the Air 1.5 installer from Adobe. Then once it stated it installed correctly, I tried to install several AIR applications, but had no luck. They just would not install through AIR.

Thanks.

---

### Post by binbash on 2009-02-03
open the page you want to install the air application.Press ctru +u (show to source code) then search for .air then copy the url and paste it to your browser.Download it and open it.

---

