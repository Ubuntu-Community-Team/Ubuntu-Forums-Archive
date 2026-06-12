---
title: "newbe needs help with conky.."
date: 2011-08-23
forum: New to Ubuntu
---

### Post by werty2010 on 2011-08-23
i installed conky and followed these instructions [here]("http://helmuthdu.deviantart.com/art/CONKY-Colors-244793180") for installing conky-colors. 
after that i ran conky and i had only a small black "box" with some very basic info, on the top left of the screen, covering the icons...
i haven't made any changes except those on the link above.

some help to fix this?

---

### Post by Frogs Hair on 2011-08-23
What you are seeing is the default Conky theme , to remove it , use Alt+F2 or open the terminal and run the command below . ```
killall conky
```
I am not familiar with Conky Colors but I know there are users on the forum that are . If you have followed the instructions I don't know what could be wrong .

---

### Post by werty2010 on 2011-08-23
i managed to run it and put in "start up applications" but now im facing another problem:
when i boot up conky works fine but the weather forecast doen't seem to be updated/strarted.
maybe this is because i don't connect to internet automatically..

is there any way to get forecast working without having  to type :
> conky -c /home/sky/.conkycolors/conkyrc 
everytime i boot up?

---

### Post by hookitup on 2011-08-23
conky, issues ,, try the [GUI]("http://conkygui.sourceforge.net/") and see if that makes a little more scene then all the terminal talk..

---

