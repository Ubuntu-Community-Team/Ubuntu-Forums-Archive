---
title: "firefox problem"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-23
i run shiretoko with ppa repos
when i use google earth i want it to launch the links i click with shiretoko but that doesnt happen
i tried the "preferred application" window and although it works with all the other apps ,it "doesnt" with google earth.
after that i went to shiretoko->edit->preferences->advanced->check now but now matter how many times i click on the check now button no pop up window appears.. so my question:can i still do this with another way? maybe with a command inside shiretoko?

---

### Post by philinux on 2009-07-23
[http://sidux.com/PNphpBB2-viewtopic-t-15076.html](http://sidux.com/PNphpBB2-viewtopic-t-15076.html)

From next to last post. Example.

export BROWSER='opera' && googleearth

---

### Post by heyyy on 2009-07-23
> **philinux said:**
> [http://sidux.com/PNphpBB2-viewtopic-t-15076.html](http://sidux.com/PNphpBB2-viewtopic-t-15076.html)

From next to last post. Example.

export BROWSER='opera' && googleearth

i want googleearth to launch the links with shiretoko
so i repeat myself in order not to do any mistakes ,i type to the terminal:

```
export Browser='firefox-3.5' && googleearth
```

right?

---

### Post by heyyy on 2009-07-23
i typed it and gave me:

bash: googleearth: command not found
i also tried it with the path of googleearth but didnt work either
any ideas?

---

