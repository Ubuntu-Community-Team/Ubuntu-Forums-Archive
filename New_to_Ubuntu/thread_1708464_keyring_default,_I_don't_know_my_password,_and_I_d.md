---
title: "keyring default, I don't know my password, and I don't think I ever set one"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by spaz33g on 2011-03-16
so i have begun mostly settling in with 10.10 on my laptop, and most of my beginners questions have been answered, except for one. i did a few searches and i could find a solution. Every once in a while, sometimes at random and sometime wen launching applications, a window will pop up asking me for my default keyring password. I orriginally assumed that it would be the same as my login password seeing as that's the only password I set up. So the long and short of it is, i have no idea what the password is so i ant enter it to change it:confused:. Any help would be greatly appreciated.

---

### Post by kerry_s on 2011-03-16
did you try your login password?

---

### Post by spaz33g on 2011-03-16
yeah i tried my login password and it tells me that the password is incorrect. It's pretty weird,I mean I know i didnt choose any other passwords during setup. It really didn't bother me all that much but now tweetdeck refuses to open without it so i' worried about it affecing other applications.

---

### Post by spaz33g on 2011-03-16
ok this is easily the fifth or sixth time ubuntu has made a total fool of me in the last two days. out the default keyring password was one character different than my login password. I really don't think i set it up that way but at this point i guess anything is possible, thank you for the quick reply.

---

### Post by kerry_s on 2011-03-16
> **spaz33g said:**
> ok this is easily the fifth or sixth time ubuntu has made a total fool of me in the last two days. out the default keyring password was one character different than my login password. I really don't think i set it up that way but at this point i guess anything is possible, thank you for the quick reply.

make sure you go to system-> passwords & encryption keys
right click on passwords:default-> change password

there you can set it to what you really want or just leave blank & have no password.

---

### Post by beew on 2011-03-16
> **kerry_s said:**
> make sure you go to system-> passwords & encryption keys
right click on passwords:default-> change password

there you can set it to what you really want or just leave blank & have no password.

Or just open /home/uesrname, click "show hidden file" go to .gnome2 , open it and delete the folder "keyring". Clean and simple. :)

---

### Post by spaz33g on 2011-03-16
ya that was the first thing i did when i figured out what it was actually set to. thanks again.

---

