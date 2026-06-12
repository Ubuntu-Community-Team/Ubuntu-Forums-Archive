---
title: "Mouse cursor in Ubuntu 11.04"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by user_Abdullah on 2011-05-06
Hi guys :)

I used to change the color of the mouse cursor in Ubuntu 10.10 to Black


When I upgraded to 11.04 I changed the color as well

but the issue is, it becomes Black inside the windows only (i.e terminal, firefox ..etc) and if I move the cursor out to desktop space or to Ubuntu top bar, it becomes White!!


I don't know what is the problem? Any idea?


Thanks :)

---

### Post by user_Abdullah on 2011-05-06
up

---

### Post by user_Abdullah on 2011-05-06
up up :$

---

### Post by user_Abdullah on 2011-05-07
if anybody knows please help :)

---

### Post by Cenzontle on 2011-05-10
Hey, ....well i am new in this forum... and my english is not very well yet.... so .... ... ...

but...the thing is this.... I had the same problem in my laptop (with ubuntu 11.04)... and the way that i resolved the problem is...
                               
**1.- cd /var/lib/dpkg/alternatives**

2.- nano x-cursor-theme
.... in this file is some kind of list of all the themes you have installed 
.... and search just to confirm if there is the cursor theme you want, (if is not there, then i don't know what do... yet :) :))

example:
/etc/X11/cursors/ComixCursors-Green-Large.theme
50

[B]3. then exit and run 
sudo update-alternatives --config x-cursor-theme[/B]
this will present you  again a list of all the cursor theme, but this time, every item have a number on it...(in my case the ComixCursors-Green-Large.theme was 19) .... so the program ask you for that number... type 19 and enter

4.- ...but.... this will change only your "arrow" icon, so you will see that the rest of the icons for your mouse are not change yet, so you need to go change that yourself in the "theme configuration"....you can do it as you normally do

[B]5.- reboot your pc and that is...
[/B]
...look all i did was test and error, so maybe sometime later someone come here with a better answer

...and maybe in that time i will come here writing a better english :):)

---

### Post by Polymorphium on 2011-05-11
Hello to everybody and one big thanks @Cenzotle for the post.
I had this problem since alpha2 and I couldn't find any solution for it.Once again,thanks.

---

### Post by jdorenbush on 2012-03-21
Cenzontle's solution worked for me. Thanks

---

