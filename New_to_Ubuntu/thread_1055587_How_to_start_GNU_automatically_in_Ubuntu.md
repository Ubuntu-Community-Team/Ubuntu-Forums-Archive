---
title: "How to start GNU automatically in Ubuntu?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by lobo-tuerto on 2009-01-30
Hi guys, I would like the program GNU screen to be started automatically whenever I go into gnome-terminal.

I know only of this tutorial, but it's dated 2006.
[http://linuxwisdom.blogspot.com/2006/08/start-gnu-screen-automatically.html](http://linuxwisdom.blogspot.com/2006/08/start-gnu-screen-automatically.html)

Is it the correct way to do it in Ubuntu? or is there a better way? :popcorn:

---

### Post by jerome1232 on 2009-01-30
You could stick it at the bottom of your ~/.bashrc file, that should do the trick.

---

### Post by lobo-tuerto on 2009-02-05
After installing screen you can add this to the bottom of your .bashrc file:

if [ "$TERM" = "screen" ]; then
echo "[ screen is activated ]"
else
exec screen
fi

---

