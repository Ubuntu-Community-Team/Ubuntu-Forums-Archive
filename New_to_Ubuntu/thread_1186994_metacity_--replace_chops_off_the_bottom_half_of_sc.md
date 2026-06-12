---
title: "metacity --replace chops off the bottom half of screen"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by earthpigg on 2009-06-14
ubuntu 9.04, fairly fresh install.

one of the first things i generally do on a clean install is enable compiz.

this is what my display normally looks like:

[IMG]http://i109.photobucket.com/albums/n59/earthpiglite/compizon.jpg

but if i enter 'metacity --replace' (or use the compiz icon to switch), this is what my display ends up looking like:

[IMG]http://i109.photobucket.com/albums/n59/earthpiglite/compizoff.jpg

as you can see, there is a black void at the bottom that eats up parts of windows.

anyone have any ideas?

---

### Post by earthpigg on 2009-06-14
bump

---

### Post by overdrank on 2009-06-14
The black box around AWN is because it need compiz. So when you use the command metcity --replace this disables compiz and the result is the black box.

---

### Post by earthpigg on 2009-06-14
that did it, thanks!

---

### Post by glennric on 2009-06-14
AWN will work with metacity if you enable compositing for metacity.  You can do this with the gconf-editor.  However, once you have enabled compositing for metacity you will not be able to restart compiz until you disable compositing for metacity again.

---

