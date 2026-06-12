---
title: "gnome 3 serious problem"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Sleven7 on 2010-08-23
I was trying to install gnome 3.0 from the article I was reading at 

[http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html](http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html)

The article said

Launch it by hitting Alt+F2 to open the "Run Applicatoin" dialog and  enter "gnome-shell --replace". Switch back by doing the same thing but  enter "metacity --replace" instead. 

I made a mistake and ran it from the bash terminal.  now the only thing on the desk top are the three icon shortcuts that I put there, everything else is missing, I can't even shut the computer off.  How do I fix this problem?

---

### Post by Darkness Des on 2010-08-23
Press Alt+F2 and you can still use the metacity --replace command. As an alternative, if you just want to reboot and not bother doing cleanup here, press Alt+F2, make sure the box for running in a terminal is checked, and type in
```
sudo shutdown -r now
```
and enter your password when prompted. Stars (or any other censored character) won't show up, it's a security thing.

---

### Post by Sleven7 on 2010-08-23
Thank you,  I have the old desk top back.

---

### Post by Darkness Des on 2010-08-23
Any time.

---

