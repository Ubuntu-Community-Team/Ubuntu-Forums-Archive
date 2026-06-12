---
title: "Gimp Malfunction"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by Ignotus Angelus on 2010-06-04
[B][FONT=Book Antiqua][COLOR=Navy]Hello,

I am having a bit of trouble with my Gimp program. I tried to install the Gimpshop extension, but since I had problems with the loading, I decided to uninstall it entirely and reinstall the original version.

But now, it seems that when I try to install it, it reverts back to Gimpshop by default. How can I fix this?

Thank you for your help![/COLOR][/FONT][/B]

---

### Post by sidzen on 2010-06-04
> **Ignotus Angelus said:**
> [B][FONT=Book Antiqua][COLOR=Navy]Hello,

I am having a bit of trouble with my Gimp program. I tried to install the Gimpshop extension, but since I had problems with the loading, I decided to uninstall it entirely and reinstall the original version.

But now, it seems that when I try to install it, it reverts back to Gimpshop by default. How can I fix this?

Thank you for your help![/COLOR][/FONT][/B]


I'm no expert, but here's more than I want to know about the GIMP:

[http://manpages.ubuntu.com/manpages/hardy/man1/gimp.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/gimp.1.html)

[https://help.ubuntu.com](https://help.ubuntu.com) is the place to go, my fellow linux enthusiast (ubuntu esp.).

---

### Post by Ignotus Angelus on 2010-06-14
[COLOR=Navy][B][FONT=Book Antiqua]I tried... This is not helping one bit. :(

I want to reinstall Gimp anew, but when I uninstall using the Software Centre, and then try to reinstall it, it just goes back to GimpShop.

I looked at the links you gave me, I didn't find the solution to my problem in there...

Can anyone just tell me what to do? Write something or other in the terminal to fix it??
[/FONT][/B][/COLOR]

---

### Post by jtarin on 2010-06-14
If your starting completly from scratch with your install, you can go into to your "HOME" folder and delete the hidden folder marked ".gimp-2.X". Then do your install.There could be one for "gimp-shop" also, so look around.

---

### Post by sandyd on 2010-06-14
```
sudo apt-get remove gimpshop
```

---

### Post by Ignotus Angelus on 2010-06-14
[B][FONT=Book Antiqua][COLOR=Navy]:) Thank you! This solved my issue *glomps everyone and offers cookies* :KS:KS:KS:KS:KS:KS
[/COLOR][/FONT][/B]

---

### Post by Phrea on 2010-06-14
Mark as solved. :)

---

