---
title: "firefox so slow"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by satipera on 2009-06-03
Why is firefox so slow after updating to jaunty. Really it takes ages to load and run plus wait time for pages is terrible.

---

### Post by gettinoriginal on 2009-06-03
This is a good place to start to fix it:  :p
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)
Really does speed things up.

---

### Post by satipera on 2009-06-03
Thanks for the reply, I have bookmarked and will be looking closely at it tomorrow. I would like to know why do we need to do this? What is going wrong in the first place?

---

### Post by gettinoriginal on 2009-06-03
Nothing is really wrong.  Firefox is a browser that works with many OS's, therefore, it must have the settings to allow it to do so.  The link I sent you is just to tweak those settings for the Ubuntu family  :p

---

### Post by lovinglinux on 2009-06-03
Just for curiosity, could you post the result of [Peacekeeper](http://service.futuremark.com/peacekeeper/index.action) benchmark?

Extensions can slow it down considerably. In my case, if I have all my extensions loaded, performance drops about 20-30%.

You could also try to optimize Firefrox databases. There is a tutorial somewhere about this with an optimization script, but I can't find it. You can try my own script, which is not elegant. Follow instructions below:

1 ) install [sqlite3](apt:sqlite3)
2) create an empty file where you save your personal scripts (usually ~/bin) and name it *firefox-databases*, then right-click on it, select *Preferences*, then *Permissions* tab, then select the option "*Allow to execute as program*".
3) Create a new empty file in the same folder and name it *firefox-optimize*, then add the code below to it and save it. 

```

#!/bin/bash

killall firefox

echo "#!/bin/bash" > $HOME/bin/firefox-databases

echo "" >> $HOME/bin/firefox-databases

find $HOME/.mozilla -type f \( -name "*.sqlite" \) | sed 's/.*/sqlite3 &/g' | sed 's/.*/& "vacuum"/g' >> $HOME/bin/firefox-databases

$HOME/bin/firefox-databases
```

Then make it also executable and run it from the terminal.

```
firefox-optimize
```

The script above will basically search for all sqlite databases on the ~/.mozilla folder, create a new script to optimize these databases, save it as *firefox-databases* in your script directory and will execute it.


*UKeywords: 649167 2009 june sqlite sqlite3 optimization firefox script performance vacuum*

---

### Post by powel212 on 2009-06-03
Give epiphany browser a try.

It is very similar to Firefox but is super lightweight.

It is in the repos.

Powel

Also for the purpose of testing the integrity of your Firefox install you could create a new user, log out, log in as new user and try firefox as new user and see if it improves at all. 

P.

---

### Post by cogs10 on 2009-06-03
hi, i was having a slowdown on firefox for winxp, when i updated to firefox3, so i downgraded to firefox2, and the speed returned. but yes, the slowdown may have to do with addons.

---

