---
title: "Start a program using init.d"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by love to learn on 2010-02-19
Hi guys
I need to bow and ask for help here,as i am getting cross-eyed already:}

I have a program which i wrote using sdl and i am trying to start it on boot using init.d.
The prog runs fine if run from the terminal but i cant get it to run on startup.

I first created a file in init.d called myprog which looks like this:
```

#! /bin/sh

su myuser -c  /home/myuser/myprogs/./myprog

exit 0

```Then i did      sudo update-rc.d -f myprog defaults
followed by sudo shutdown -r now
and myprog doesnt start after startup.

file permissions on the myprog file in init.d is 644.

The program does require the x server to be running.

Please help!

---

### Post by love to learn on 2010-02-19
I just tried chmodding the file in init.d to 755 and that did not help,although i think that was one of my errors.

---

### Post by love to learn on 2010-02-19
had to run the program from my ~.bash_profile

---

### Post by lavinog on 2010-02-19
system>prefs>startup applications would be a better place.

---

