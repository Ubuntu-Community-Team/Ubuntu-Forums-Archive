---
title: "Ubuntu and terminal."
date: 2010-06-17
forum: New to Ubuntu
---

### Post by SKYDOS on 2010-06-17
I want to do such a thing: run a program using terminal and after that close terminal window.
But when I close terminal window my app is also closing.
How can i avoid that?

Thanks! :popcorn:

---

### Post by sisco311 on 2010-06-17
Start the application in the background by appending its command with an & symbol, then run disown before you close the terminal:
```
command &
disown
```

---

### Post by philinux on 2010-06-17
```
gcalctool &exit
```

---

### Post by SKYDOS on 2010-06-17
> **sisco311 said:**
> Start the application in the background by appending its command with an & symbol, then run disown before you close the terminal:
```
command &
disown
```

Thanks a lot dude! I Like Ubuntu))) ):P

---

### Post by SKYDOS on 2010-06-17
> **philinux said:**
> ```
gcalctool &exit
```

Uh! Fantastic)) Thank you too!

---

### Post by bodhi.zazen on 2010-06-17
You can use other tools as well.

screen is helpful, often used with ssh sessions.

[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

There are many additional tutorials on screen on the net.

A "light weight" application similar to screen is dtach

[http://linux.die.net/man/1/dtach](http://linux.die.net/man/1/dtach)

The advantage of both screen and dtach, you can re associate the application with the terminal again (useful for command line applications).

In addition to disown, you can use nohup . nohup is one step :

```
nohup command &
```

Try it with xeyes:

```
nohup xeyes &
```

---

