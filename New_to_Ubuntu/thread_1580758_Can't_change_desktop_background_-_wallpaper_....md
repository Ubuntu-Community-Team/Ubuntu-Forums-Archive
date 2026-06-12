---
title: "Can't change desktop background - wallpaper ..."
date: 2010-09-23
forum: New to Ubuntu
---

### Post by cwmoser on 2010-09-23
Ubuntu 10.04
Cannot change the desktop background - i.e. wallpaper.

Tried several ways.  When I right click on the desktop and select Change Background, the wallpaper I select will not display on my monitor.

Any ideas?

Thanks

Carl

---

### Post by jtarin on 2010-09-23
What is the file extension of your image and where is it located?

I notice your signature about antique radios....I used to collect....had several pre-1936 and one 1922 all cabinet models.

---

### Post by cwmoser on 2010-09-23
I tried the stock images and some others.  The one that I want is located in a folder named ~/wallpaper.  The file is a JPG - i.e. Rak.jpg

Carl

---

### Post by cwmoser on 2010-09-23
Seems like my desktop is locked to the mauve colored standard background in Lucid Lynx.

Carl

---

### Post by jtarin on 2010-09-23
Try adding another user and login and see if you can do it from that account. You might have some glitch in permissions. Right-click on the directory and the image and see if you have permissions.

---

### Post by cwmoser on 2010-09-24
Jtarin, you solved the problem.  I took your advice and created a new user.  Logged in as the new user and was able to change the background.  Then I logged out and went back to my primary account and the wallpaper was changed to the same background as the new account.  But, then I was able to change background as I wanted.

Thanks

Carl

---

### Post by jtarin on 2010-09-24
Good. You can either remove that account or leave it unused for such purpose as this when you have problems with the initial account.As long as you don't use it,the space taken is negligble.

---

### Post by jcoles on 2010-09-26
I created a new user who can change their desktop background, but it had no effect on my existing account. 

I found my solution in the Configuration Editor. (This item might not be enabled in your Gnome menu by default.)

1. Go to Application > System Tools > Configuration Editor.
2. In the left pane, select desktop > gnome > background.
3. In the right pane, make sure that draw_background is enabled.

In my account, draw_background had been disabled. (might have been my fault).

---

