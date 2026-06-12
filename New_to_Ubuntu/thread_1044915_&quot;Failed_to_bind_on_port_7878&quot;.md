---
title: "&quot;Failed to bind on port 7878&quot;"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by blob1 on 2009-01-19
Hello,

I am very new to linux and I have been trying to get some code working on ubuntu. I have compiled the code with make, but when I try to run the executable file the message "Failed to bind on port 7878" comes up. Can someone please explain what this means and what I can do to fix it.

Thanks in advance

---

### Post by stderr on 2009-01-19
Hi

What exactly are you trying to compile? Is this some of your own code or is this source code you've downloaded (in which case what application is it?)

Also, how are you invoking the executable?

---

### Post by blob1 on 2009-01-20
Hi,

Sorry for not being very clear before.

The code is source code which I have downloaded and the application is a MTconnect adapter. It reads data from a data source and writes it out in a normalised format. The default port used is 7878.

I have built the code in Visual Studio in Windows XP and it worked without any problems. What I did in ubuntu was I typed make in the terminal and it compiled successfully. I tried double clicking the executable and nothing happened, so I tried dragging the executable to the terminal and pressing enter. This gave the message "Failed to bind on port 7878" in the terminal. I am guessing it is something in ubuntu which is the problem, since it worked fine in Visual Studio.

Thanks for the help (and sorry if I sound noob :P)

---

### Post by stderr on 2009-01-20
Maybe port 7878 is already in use for some reason? You could try doing something like this

```
sudo netstat -apn | grep 7878
```

to see if 7878 is in use. Also, do you need to invoke the application as superuser? The readme might say, one way or another. You could try with:

```
cd /to/the/correct/directory/
sudo ./theMTConnectApplication
```

---

### Post by blob1 on 2009-01-21
Thanks for the help, I've found that the port was actually being used by the adapter application itself from when I first opened it, lol my bad. Ok, now the application is working, but there is no window or any signs of it running. The only way I can tell it is running is by using the telnet command on port 7878. Is there a way to check what applications are running and to close the application?

---

