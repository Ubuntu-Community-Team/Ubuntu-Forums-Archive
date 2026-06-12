---
title: "AWN 0.3.2.1 installed, can't run"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by marlin9800 on 2009-08-27
I just finished installing Avant Window Navigator 0.3.2.1, a long and somewhat painful process (much less so using google). All looks good, icons are in the menu (Applications - Accessories - Avant Window Navigator and System - Preferences - Awn Manager) but they don't open anything. When I run **avant-window-navigator** from terminal I get

```
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_vfs_init

```

Did I not get it installed correctly? I followed the INSTALL instructions to the tee, adding the packages every time I got a 'package not found'. Thank you

---

### Post by NoaHall on 2009-08-27
Why not install the one from synaptic? It will work better. (sudo apt-get install avant-window-navigator)
Are you using compiz? If not, then you need it.

---

### Post by marlin9800 on 2009-08-27
> **NoaHall said:**
> Why not install the one from synaptic? It will work better. (sudo apt-get install avant-window-navigator)
Are you using compiz? If not, then you need it.

I wanted 0.3.2.x specifically. I want to move the bar to the bottom right corner and read that they included that feature post 0.3.x.

---

### Post by NoaHall on 2009-08-27
Ah, I see. Well, are you compiling it yourself? That version is unstable - I wouldn't suggest using it.

---

### Post by marlin9800 on 2009-08-27
> **NoaHall said:**
> Ah, I see. Well, are you compiling it yourself?

Yes, I believe.:confused: I ran ./configure, make, make install installing many dev packages along the way.

---

### Post by NoaHall on 2009-08-27
Ah, well, your problem might be due to incorrect linking - run "sudo ldconfig"

---

### Post by marlin9800 on 2009-08-27
I read that in another post on another site, I get 'command not found'.

---

### Post by NoaHall on 2009-08-27
sorry, my mistake - typo - run "sudo ldconfig"

---

### Post by marlin9800 on 2009-08-27
Running with 'sudo' displays nothing, just enters to another line. Without 'sudo' displays 

/sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied

---

### Post by NoaHall on 2009-08-27
now try running awn, and if that fails, do 
"ldconfig -P"

---

### Post by marlin9800 on 2009-08-27
> **NoaHall said:**
> sorry, my mistake - typo - run "sudo ldconfig"

> **NoaHall said:**
> now try running awn

That did it! If you don't mind can you explain what that command did? Thank you for the fast help!:guitar:

---

### Post by marlin9800 on 2009-08-27
I can't for the life of me find where to mark this thread "SOLVED".

---

### Post by NoaHall on 2009-08-27
It connected everything up! sudo does work, the blank "result" just shows it worked ;) or else errors would have come up. Your problem was there was a file needed to run which wasn't linked up correctly. But that connected it all up.


Click edit on original post.

---

### Post by marlin9800 on 2009-08-27
Well that explains it! lol

> **NoaHall said:**
> Click edit on original post.

I was looking for a drop down or something that I thought I could edit the original post title, oh well. 

And wouldn't you know, after all that I don't see any option for changing it's place on the screen. Maybe it is there and I am just ready for bed. Thanks again.

---

### Post by NoaHall on 2009-08-27
No, haven't tested it myself - but I'm guessing there will be something which lets you change it by changing a number somewhere

---

### Post by marlin9800 on 2009-08-27
That would be nice... I don't need a GUI to possision on the screen. Just the posts that I found said that it was real easy, just use the Manager.

---

### Post by marlin9800 on 2009-08-28
I have managed to place the bar in the bottom right like I wanted (see attached). Pretty simple, just edit the /home/%username%/.gconf/apps/avant-window-navigator/bar/%gconf.xml file. Change this line's value

```
        <entry name="bar_pos" mtime="1251418471" type="float" value="1.0">
```

0.0 = left bottom
0.5 = center bottom (default)
1.0 = right bottom

Hope this helps someone else.

---

