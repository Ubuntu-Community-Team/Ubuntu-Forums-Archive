---
title: "Anyone here using burg?"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by JerichoKru on 2010-02-17
[http://code.google.com/p/burg/](http://code.google.com/p/burg/)

For those of you who don't know what it is:  It allows a graphical grub menu in grub2.


The only problem I have with it is that I'm not sure how to change the themes.  I did google searches and got conflicting results.  
The [https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg) page shows a way, but the main burg install page [http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu) says to keep those certain options the way they are.

---

### Post by 7th on 2010-02-17
Hi JerichoKru

As long as you haven't changed the burg configuration file in /etc/default/burg, you had installed the latest version using the ppa repositories ([https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)) then you can change the themes as you boot by pressing 't' and select from the list. 
If the burg config file is still default then it should remember the theme you selected last time.
Enjoy

Current commands seem to be (thanks to the help window in burg)
e - edit current command
t - edit current title (also seems to select theme)
c - open terminal
2 - open two terminals
h - show help window
i - show theme info
f6 - next anchor
f8 - toggle mode
f9 - shutdown
f10 - restart
f5/crtl-x - return (save after editing)
f7/f - fold/unfold similar entry's into one icon (ie ubuntu/ubuntu recovery...)
esc - exit without editing

---

### Post by Yvan300 on 2010-02-17
Yeah i heard about this before and was wondering if it is really stable enough for use. I don't want grub to die on me.

---

### Post by JerichoKru on 2010-02-17
> **Yvan300 said:**
> Yeah i heard about this before and was wondering if it is really stable enough for use. I don't want grub to die on me.

Seems stable to me...and even adds more functionality to the actual menu.

@ 7th: thanks I'll try that.

EDIT:  Yep, that worked.   I feel stupid since it was so simple...oh well.

---

