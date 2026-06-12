---
title: "General X11 Questions"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by gsingh2011 on 2011-04-21
I was just reading about X11 and I thought it was cool so I decided to try it out. I connected to a remote UNIX computer using putty with ssh and xming on windows. 

My first question is that it didn't work when I didn't use SSH, but most guides say it is better to use SSH, which means using it without SSH should be an option, right? How would I do this?

So far I've run applications like xterm and kate to see what it was like, but can I run any application? If I connect to a linux machine, can I run any application on the machine as an X client? Or is it limited to specific applications?

---

### Post by The Cog on 2011-04-23
It is limited to X11 applications of course, but on Linux, any GUI application is an X11 application. 

X11 applications use an environment variable called DISPLAY to find out where to connect to to write their window. You can see this in a command prompt with the command:
```
echo $DISPLAY
```
When you do SSH tunneling of X, this is set up automatically for you as SSH connects. Otherwise, the GUI program must connect directly back to your desktop PC, and several things are needed for this.

Firstly, the GUI program must know where to connect to. So when you are starting the GUI program, you must set the DISPLAY variable first to tell it which display to connect to, and then launch the application. Something like these two commands, but you would have to use the proper IP address of course:
```
export DISPLAY=1.2.3.4:0.0
xeyes
```

Secondly, your PC's X server must accept incoming connections from the application. You need to deal with any firewall rules that prevent the connection of course. You need to configure the X server to accept connections. 

In Ubuntu, X isn't even listening on TCP for connections. I found this line in another forum:
> If you want to make X11 listen on a TCP socket nonetheless you have to edit the file /etc/X11/xinit/xserverrc and remove the '-nolisten tcp' option from it. Here's the link: [http://ubuntuforums.org/archive/index.php/t-85582.html](http://ubuntuforums.org/archive/index.php/t-85582.html)
Then you have to tell the X server which other hosts are OK to accept connections from. Giving the command ```
xhost +
```on the command line says to accept connections from any other host.

---

