---
title: "Messed up my desktop - Compiz"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by Garrote2010r on 2011-07-12
Hello all,

I was playing around with Compiz and just to experiment, I unchecked Desktop Wall.  Little did I realize was it was going to cause graphics problems.  Now I have no top tool bar and my unity dock doesn't show.  

Please help!  I am an Ubuntu newb.  I am using 11.04 Unity.

---

### Post by Garrote2010r on 2011-07-12
Some added info:

If it wasn't for my internet hot key, I wouldn't have been able to post this.  I don't know how to manually start programs.

I can't seem to drag, drop, or resize this current browser. (chromium).

All I can see (besides the browser) is my desktop background pic.  None of my keyboard shortcuts work.  

I am stuck.

---

### Post by Peter09 on 2011-07-12
Try

```
unity --reset
```

in a terminal

---

### Post by wildmanne39 on 2011-07-12
Hi, after you reset unity if you want to change settings have a look at this guide it was written for the cube and effects but it shows the safe way to edit compiz.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by Garrote2010r on 2011-07-12
> **Peter09 said:**
> Try

```
unity --reset
```

in a terminal

Peter09,

I am unable to load a terminal, is there any other way to load the terminal?  It seems none of my keyboard shortcuts no longer work.  The only applications I am able to run seems like ones that are linked to the hot keys of my keyboard (internet, calculator, email, etc)

---

### Post by wildmanne39 on 2011-07-12
Open a terminal by hitting ctrl+alt+t or alt+f2, if  one of those key combination does not open the terminal try ctrl+alt+f1 thru f6. Then type this command in terminal to reset unity. 
Unity --reset

---

### Post by Garrote2010r on 2011-07-12
> **wildmanne39 said:**
> Hi, after you reset unity if you want to change settings have a look at this guide it was written for the cube and effects but it shows the safe way to edit compiz.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

Wildmann,

I have bookmarked your blog, I'll be sure to take a look once I figure this out!

---

### Post by tekkidd on 2011-07-12
Press CTRL+F1 and log in with your account. Note you will not get a response for the password. Then enter these commands:

```
sudo service gdm stop
```

```
cd
```

```
rm -rf .compiz
```

```
sudo gdm start
```

Make sure you save your work before doing this as it will log you out.

---

### Post by wildmanne39 on 2011-07-12
> **Garrote2010r said:**
> Wildmann,

I have bookmarked your blog, I'll be sure to take a look once I figure this out!Hi, ok and in my signature you can click on reset unity or compiz for instructions but it does not tell you another way to get a terminal to open.

---

### Post by Garrote2010r on 2011-07-12
> **wildmanne39 said:**
> Open a terminal by hitting ctrl+alt+t or alt+f2, if  one of those key combination does not open the terminal try ctrl+alt+f1 thru f6. Then type this command in terminal to reset unity. 
Unity --reset

Ctrl+alt+f1 worked perfectly.  Thanks again.

---

### Post by wildmanne39 on 2011-07-12
> **Garrote2010r said:**
> Ctrl+alt+f1 worked perfectly.  Thanks again.
Hi,you are welcome! Enjoy ubuntu,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

