---
title: "Keyboard CTRL pressed after update to Lucid"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by madu on 2010-04-30
So I upgraded to Lucid from 9.10 and everything seemed to go smooth. Until I realized that when I use mouse wheel in browser, it  changed the font sizes. i thought it was something wrong with BTNX mouse button mappings. Then I realized that I cannot type anything and its because the CTRL key is pressed. When I type h in FF, it opens the history. I cannot type anything anywhere. Sometimes I cant even log in. 

Sometime the keyboard works fine and after like couple of minutes it has CTRL pressed. I tried two keyboards, wireless and wired, withsame problem.

Really appreciate if anybody has any ideas to try out.

Cheers

---

### Post by _0R10N on 2010-04-30
> **madu said:**
> So I upgraded to Lucid from 9.10 and everything seemed to go smooth. Until I realized that when I use mouse wheel in browser, it  changed the font sizes. i thought it was something wrong with BTNX mouse button mappings. Then I realized that I cannot type anything and its because the CTRL key is pressed. When I type h in FF, it opens the history. I cannot type anything anywhere. Sometimes I cant even log in. 

Sometime the keyboard works fine and after like couple of minutes it has CTRL pressed. I tried two keyboards, wireless and wired, withsame problem.

Really appreciate if anybody has any ideas to try out.

Cheers

Did you tried disabling compiz?

---

### Post by madu on 2010-04-30
> **_0R10N said:**
> Did you tried disabling compiz?

No... I will try that.. thanks for the tip mate...

---

### Post by P4man on 2010-04-30
if you can, open a terminal and run

```
xev
```

it will show all key/mouse inputs (mouse only when over that white square). try using the control keys and see it registers both key up and down events

---

### Post by madu on 2010-04-30
> **P4man said:**
> if you can, open a terminal and run

```
xev
```

it will show all key/mouse inputs (mouse only when over that white square). try using the control keys and see it registers both key up and down events


Thank you p4man.
Actually it registers mouse events (terminal displays lots of messages) but when I type, the terminal just displays the keys I type... doesnt show anything else.. I suppose thats not good?

---

### Post by madu on 2010-04-30
I tried it after disabling Compiz too but still same result.
I am supposed to get some key mapping output from Xev everytime I press a key right?

Thank you.

---

### Post by P4man on 2010-04-30
click on the white square, then type

---

### Post by madu on 2010-04-30
> **P4man said:**
> click on the white square, then type

Thank you very much. Didnt know I had to click on the sqaure first.
Now it actually registers the keys. And so far I havent had the CTRL pressed problem. I am using the wired USB kb now.. for some reason Ubuntu doesnt detect my wireless kb (which was working fine before the upgrade)... the mouse, which is also connected to the same wireless USB receiver is working fine. But not the kb..

Thank you very much for the help guys.

---

### Post by johnycage on 2011-07-09
I'm having exact problem as you described. it's 11.04 updated version. & my user login always ctrl-pressed issue. I can login as another user & work. But I cant type well when I'm logged in to my regular userid. 
So I cannot type 'xev' in terminal.

Help. I can access via another PC using SSH. & make changes in required. 

thanks

---

