---
title: "open a program from terminal"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by ave2 on 2009-03-09
Iv created a menu item to a program, but instead of just executing the program, I first want it to open a terminal and then execute it from there- how do I go about doing this? 

I pasted the command gnome-terminal -e before the address, but it doesnt work

---

### Post by karlr42 on 2009-03-09
That probably did work, but the thing is, the terminal will close as soon as that program ends, which may have been quite quickly? Also try
gnome-terminal --COMMAND=<program>

---

