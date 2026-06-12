---
title: "Remapping keys"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by malangbaba on 2009-11-03
Peace,

I just upgraded to 9.10.  I fixed this problem in Jacky, but cannot remember how I fixed it.....



My /? key is dead. I want to switch the Alt_R key with the /? key, since i never use the Alt_R key anyway...

So i created an .Xmodmap file...and put in:

keysym Alt_R = slash

that worked and now the former Alt_r key produces a /

But I cant produce a ?

I tried:
keysym Alt_R = slash question

but that didnt work either...

ideas?

I also tried xkeycaps...but i cant figure out how to find my keyboard on there (its an 85-key-laptop)...ideally i'd be able to do this from command line, but am open to xkeycaps suggestions as well...

Ubuntu 9.10
Toshiba Satellite M105-S3041

---

### Post by malangbaba on 2009-11-06
^^^

---

### Post by falconindy on 2009-11-06
I think you'll need to remove Alt_R from the list of modifiers. Add a line prior to yours:
```
remove mod1 = Alt_R
```

---

### Post by malangbaba on 2009-11-06
no, theres no modifiers for Alt_R

any other suggestions/ (<- thats supposed to be a question mark)

---

### Post by malangbaba on 2009-11-09
^^^

---

### Post by malangbaba on 2009-11-09
Well, I dont fully understand how I fixed it, but for some reason the Alt_R key was set to be the same regardless of using Shift or not.  I went into Keyboard preferences -> Layouts -> Layout Options and selected these two options:
- Alt/Win key behavior - Selected "Alt and Meta are on Alt keys"
- Key to choose 3rd level - Selected "Right Alt key never chooses 3rd level"

Then I did Xmodmap as above, and it worked.

---

