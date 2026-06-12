---
title: "Can you change backgound of login screen 10.10?"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by Ditchdoc7893 on 2011-06-03
Just a question of sheer curiosity.  I am wondering if there is a way to change the background of the ubuntu login screen, the screen that appears just after bootup when ubuntu starts up and asks you which user you are?  Is there a way to change or customize this?

---

### Post by dFlyer on 2011-06-03
Your answer is yes. Just search this forum and you will find your answer.

---

### Post by Ditchdoc7893 on 2011-06-03
Thank you.  I'm continuing to hunt and can't as yet find it.  I guess the question should have added how.  Again, I am continuing to look.

---

### Post by jtarin on 2011-06-03
You can use Ubuntu Tweak. You can find it in the Software sources.

---

### Post by vivek.pandey on 2011-06-04
check out this thread

[http://ubuntuforums.org/showthread.php?t=1731427](http://ubuntuforums.org/showthread.php?t=1731427)

---

### Post by Anuovis on 2011-06-04
There is another easy way I stumbled upon. Worked with 9.10 and 11.04, so I assume 10.10 would be fine.

Open terminal and type:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```Close the terminal window and logout.

When the login screen appears, the Appearance window pops up. You can change the background, pick a theme to decorate window elements, etc.

To prevent the Appearance Manager from opening when you login type this into the terminal:
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by nzjethro on 2011-06-04
Anuovis, that worked for me on Maverick, no problems. Ditchdoc, Anuovis' way is good because it lets you change the entire theme (wallpaper and the look of the login) which is nice.

---

### Post by Ditchdoc7893 on 2011-06-06
Thanks guys for the help.  Worked great!

---

