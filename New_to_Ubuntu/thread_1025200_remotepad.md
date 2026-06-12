---
title: "remotepad"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by lui22 on 2008-12-29
dose any one know what to do with the source file 
remote pad only works when used in unison with i pod touch or iphone it lets u use your device as a mouse :o

---

### Post by woosyrmomma on 2009-01-22
Just read the follow the direction here > 1. Open terminal emulator (xterm perhaps).
    2. Change your directory to where the downloaded file is.
               prompt% cd the_directory_where_the_downloaded_file_is
    3. Extract source files from the downloaded file.  This command
       outputs extracted file names.
               prompt% tar xvfz RemotePadServer-1.4-Source.tgz
    4. Change your directory to an extracted one.  You have to enter
       the command includes doublequotes.
               prompt% cd "RemotePad Server"
    5. Do compile with make command.  This command outputs compiling
       commands and its outputs.
               prompt% xmkmf
               prompt% make
    6. You have now get the RemotePad Server program named 'remotepad.'
    7. Run this server.
               prompt% ./remotepad
    8. You may install this program to /usr/local/bin with root privilege.
               prompt% su
               prompt# make install and if you get hung up at step six (i did) type > sudo apt-get install libxtst-dev libxtst6

---

### Post by bbrg548 on 2009-02-13
Ok, I'm trying to install this, but when I run "make" I get:

```
cc -g -O2 -Wall -Werror -I/usr/X11R6/include -I/usr/X11R7/include -I/usr/X11/include   -c -o remotepad.o remotepad.c
remotepad.c:48:22: error: X11/Xlib.h: No such file or directory
remotepad.c:49:23: error: X11/Xutil.h: No such file or directory
remotepad.c:50:24: error: X11/keysym.h: No such file or directory
remotepad.c:51:34: error: X11/extensions/XTest.h: No such file or directory
remotepad.c:74: error: ‘Button1’ undeclared here (not in a function)
remotepad.c:74: error: ‘Button3’ undeclared here (not in a function)
remotepad.c:74: error: ‘Button2’ undeclared here (not in a function)
remotepad.c:74: error: ‘Button4’ undeclared here (not in a function)
remotepad.c:74: error: ‘Button5’ undeclared here (not in a function)
remotepad.c:82: error: expected ‘)’ before ‘*’ token
remotepad.c: In function ‘main’:
remotepad.c:91: error: ‘Display’ undeclared (first use in this function)
remotepad.c:91: error: (Each undeclared identifier is reported only once
remotepad.c:91: error: for each function it appears in.)
remotepad.c:91: error: ‘dpy’ undeclared (first use in this function)
cc1: warnings being treated as errors
remotepad.c:112: warning: implicit declaration of function ‘XOpenDisplay’
remotepad.c:113: warning: implicit declaration of function ‘XDisplayName’
remotepad.c:113: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
remotepad.c:117: error: ‘Bool’ undeclared (first use in this function)
remotepad.c:117: error: expected ‘;’ before ‘success’
remotepad.c:119: error: ‘success’ undeclared (first use in this function)
remotepad.c:119: error: ‘False’ undeclared (first use in this function)
remotepad.c:217: warning: implicit declaration of function ‘XTestFakeRelativeMotionEvent’
remotepad.c:243: warning: implicit declaration of function ‘XTestFakeButtonEvent’
remotepad.c:273: warning: implicit declaration of function ‘handleKeyEvent’
remotepad.c:282: warning: implicit declaration of function ‘XFlush’
remotepad.c:94: warning: unused variable ‘dummy’
remotepad.c: At top level:
remotepad.c:320: error: expected ‘)’ before ‘*’ token
make: *** [remotepad.o] Error 1
```

Help?

-Jake

---

### Post by solong on 2009-02-22
I think that the problem may be that when I downloaded it from the website it is version 1.6 rather than 1.4. I ended up with a 'remotepad.c' file that I have no idea what to do with and couldn't go any further and get the server running. Anyone have any ideas or can provide a more concise walkthrough with this version? This is a cool toy and works well on my mac. I would love to be able to control the 42" with it instead of my wireless keyboard.

---

### Post by biketrials on 2009-02-24
Here is a binary that should work. Just run ifconfig to get your ipaddress and then add :5583



Example --> 192.168.0.101:5583

---

### Post by solong on 2009-02-25
Hmmmm.
So I ran ifconfig and got my address which is 192.168.1.100 on 'eth0'.

Then when I run the binary './remotepad' (from the directory where the binary is of course) I get the following:
[INDENT]
Remotepad server for X11 version 1.6
Application launched.
Failed to bind socket: Address already in use[/INDENT]

I am assuming that this means that the ip address is in use which it is. I'm not sure how you wanted me to use port 5583 either. I did run a port scan and 5583 came back as open though.

---

### Post by m3alnemer on 2009-09-27
> **solong said:**
> Hmmmm.
So I ran ifconfig and got my address which is 192.168.1.100 on 'eth0'.

Then when I run the binary './remotepad' (from the directory where the binary is of course) I get the following:
[INDENT]
Remotepad server for X11 version 1.6
Application launched.
Failed to bind socket: Address already in use[/INDENT]

I am assuming that this means that the ip address is in use which it is. I'm not sure how you wanted me to use port 5583 either. I did run a port scan and 5583 came back as open though.


I have the same problem. I wonder if we can do something by changing the IP or host name somehow.

---

### Post by Hozza on 2009-12-10
i got the same thing...

Failed to bind socket: Address already in use

can anyone help?

---

### Post by Hozza on 2009-12-10
just run it a "sudo"

```
sudo remotepad
```

---

