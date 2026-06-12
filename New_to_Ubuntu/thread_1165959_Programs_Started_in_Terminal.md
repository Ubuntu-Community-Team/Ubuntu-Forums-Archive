---
title: "Programs Started in Terminal"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Helloes on 2009-05-21
The question I have is kinda pure noobish curiosity, but why do the programs started in the terminal close when the terminal is closed?

---

### Post by qjmoss on 2009-05-21
They're...


Dependent on the terminal.


That's like.. uhm.

hm..


Unplugging your desktop and expecting it to stay on.


=/


i'm sure someone else will give you a better explination. it's very early for me right now..


good luck!

---

### Post by baizon on 2009-05-21
Run the program like that: 
```
firefox&
```
Then if you close the Terminal the program will not terminate :)

---

### Post by mcduck on 2009-05-21
> **Helloes said:**
> The question I have is kinda pure noobish curiosity, but why do the programs started in the terminal close when the terminal is closed?

When you start the program in a terminal, you should actually think of the program running *inside* that terminal, even when it happens to create some extra window to give you a graphical interface.

In other words the program runs as a subprocess of the terminal process. Close the parent and the subprocess will close as well.

If you need to, you can detach the process from the terminal, for example by using *nohup*:
```

nohup firefox &
```
The program starts as it's own process separate from the terminal, and all output is directed to a text file in your homed directory instead of the terminal window.

Anyway, most of the time the best way to start programs is by pressing Alt-F2 and starting the program from the Run dialog instead of a terminal.

edit: Here's another way to think about it: each terminal you open actually counts as you logging in to the system as another user. If you log to desktop, start program, and then log out of the desktop your program will close as well. In the same way, if you log into a terminal, and then close the terminal, the programs running in the terminal will close as well.

Try opening a terminal and running "who". that will show you being logged in twice, once in the graphical desktop and once in the terminal. Open a second terminal and run "who" again and you'll see yourself being logged into the system as three users. If the user logs out,a ll programs started by that user will close.

---

### Post by mcduck on 2009-05-21
> **baizon said:**
> Run the program like that: 
```
firefox&
```
Then if you close the Terminal the program will not terminate :)

That won't always work. Adding "&" to the end simply tells the program to run in background, some programs might detach from the original terminal process, most won't. If you want a solution that *always* works, use *nohup*.

I can definitely tell you that at least on my system starting Firefox in background will not detach it from the terminal. Close the terminal and Firefox will close as well.

---

### Post by kpkeerthi on 2009-05-21
Or background the application, like this:
```
firefox&
```
... and then disconnect it from the shell it started off from, with this command:
```
disown
```
You should be able to close the terminal window now.

---

### Post by Helloes on 2009-05-21
Thanks you all for the fast responses, everything is clear now.

---

### Post by 3rdalbum on 2009-05-21
Just out of interest, if I started an SSH session to my remote server with X forwarding, and I started Firefox on the remote server with "nohup", could I close the ssh connection without killing Firefox?

EDIT: I just tried it; didn't work. Is there some other way I can do that? My server isn't running X - well, it does usually but I managed to crash it. I don't want to reboot the whole machine if I can help it!

---

