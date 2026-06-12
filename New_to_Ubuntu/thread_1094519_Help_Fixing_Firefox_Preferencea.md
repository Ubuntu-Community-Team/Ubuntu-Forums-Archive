---
title: "Help Fixing Firefox Preferencea"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by saxonjf on 2009-03-12
I was fiddling around with the shell with a guy who knows more about linux than me, and I entered in
> 
sudo firefox

and that opened up a stripepd down version of firefox with no features, appearance formatting, or add-ons.  Then I closed it, but when I opened it from the Ubuntu GUI, the homepage went back to the Ubuntu 8.10 screen, and when I change the homepage, it changes back to the Ubuntu 8.10 screen.

Can someone give me hint on a command I could enter to allow my preferences back?

---

### Post by stchman on 2009-03-12
> **saxonjf said:**
> I was fiddling around with the shell with a guy who knows more about linux than me, and I entered in


and that opened up a stripepd down version of firefox with no features, appearance formatting, or add-ons.  Then I closed it, but when I opened it from the Ubuntu GUI, the homepage went back to the Ubuntu 8.10 screen, and when I change the homepage, it changes back to the Ubuntu 8.10 screen.

Can someone give me hint on a command I could enter to allow my preferences back?

NEVER use sudo and Firefox together.  This will allow scripts to run.  Part of Linux security is permissions.  The sudo command elevates any command to root privileges.

---

