---
title: "Password with bash scripting"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by Mauler5858 on 2010-08-31
i need to automatically pass my password into a prompt for a bash script(which is running a mysqldump).  I dont want to store the password on the script, i was thinking to store it into a file that i could lockddown and pass it into the script that way.  ive heard this is possible, but dont really know how.

---

### Post by bodhi.zazen on 2010-08-31
Try "expect"

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

You could possibly pass the password on the command line as well, depending on your script.

If you are using sudo, make the script owned by root and run it with sudo.

---

### Post by nothingspecial on 2010-08-31
Sorry Mauler5858 

Thanks bodhi.zazen, I`ll play with expect later, it looks great!

[SIZE=1][ASIDE]   improvement on the sith btw, I still like the serene teddy bear better  [/ASIDE][/SIZE]

---

