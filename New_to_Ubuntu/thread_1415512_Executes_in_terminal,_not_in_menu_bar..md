---
title: "Executes in terminal, not in menu bar."
date: 2010-02-24
forum: New to Ubuntu
---

### Post by pteri498 on 2010-02-24
I placed my eclipse galileo executable in /usr/local/bin/eclipse and added that to my PATH variable.

running eclipse from the terminal is fine, but doing the same from an entry I added to the menu bar produces the following error:

Could not launch 'Eclipse Galileo'

Failed to execute child process "eclipse" (Permission denied)

What does this mean? Why is it I can do this in terminal but not from the menu bar?

---

### Post by ubudog on 2010-02-25
You will need to edit your menu entry command to say "gksu /usr/local/bin/eclipse" (without the quotes) 
It will ask for a password, enter it, and you are on your way!

---

