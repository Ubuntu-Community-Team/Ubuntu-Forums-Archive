---
title: "Need help remapping keys"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by malangbaba on 2009-05-03
Peace,

still new to Linux\Ubuntu....

My **/?** key went dead. I want to switch the **Alt_R** key with the **/?** key, since i never use the **Alt_R** key anyway...

So i created an .Xmodmap file...and put in:
keysym Alt_R = slash

that worked and now the former **Alt_r** key produces a **/**

But I cant produce a **?**

I tried:
keysym Alt_R = slash question

but that didnt work either...

ideas?

I also tried xkeycaps...but i cant figure out how to find my keyboard on there (its an 85-key-laptop)...ideally i'd be able to do this from command line, but am open to xkeycaps suggestions as well...

Ubuntu 8.10
Toshiba Satellite M105-S3041

---

### Post by x22 on 2009-05-03
did you try with quotes "slash question"?

---

### Post by malangbaba on 2009-05-03
actually
keysym Alt_R = slash question
ending up working in Jacky...

thanks!

---

