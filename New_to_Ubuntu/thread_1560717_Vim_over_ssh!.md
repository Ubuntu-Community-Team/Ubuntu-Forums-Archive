---
title: "Vim over ssh!"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by nebu on 2010-08-25
Hey,
I was using vim over two successive ssh connections and I cant seem to use the backsapce key!

It turns up as a ^?. 

How do I fix this? Google turns up lots of fixes for the MacOS but nothing for Ubuntu or any other linux distro! :(

---

### Post by Brandon Williams on 2010-08-26
First, determine what key is set as the erase key in the shell when you log in via ssh:
```
$ stty -a
speed 38400 baud; rows 58; columns 160; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>; eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R; werase = ^W;
lnext = ^V; flush = ^O; min = 1; time = 0;
etc
```
Here, you can see that '^?' (backspace) is treated as the erase key. Sometimes, this shows up as '^H' or something else instead. I expect that this will be the case in your setup.

Assuming that the erase key is not set to '^?', there are two approaches to the problem: 1) change the erase key used in your session on the server, or 2) change the code that your ssh client sends when you press backspace.

To change the erase key on the server, run this command:
```
stty erase '^?'
```
If that works to correct the behavior in vim, you can add this command to your ~/.bashrc file so that it takes effect every time you log in.

Alternatively, some ssh clients allow you to handle this in the client software by changing the value that is sent when you press the backspace key. You could try to configure the client to send whatever code is currently set as the erase key.

---

### Post by nebu on 2010-08-26
thanks... that worked!

---

### Post by th1980 on 2010-09-07
You can also make this global (all users) by adding this command to /etc/bash.bashrc

[http://lcorg.blogspot.com/2010/01/bashrc-vs-bashprofile.html](http://lcorg.blogspot.com/2010/01/bashrc-vs-bashprofile.html)

It worked for me in Ubuntu 10.04.

---

### Post by th1980 on 2010-09-07
I also just discovered that bash history was also not working (up/down arrow keys).  The shell defined in the /etc/passwd file was set to /bin/sh instead of /bin/bash.

By changing this it corrected both problems.

[http://ubuntuguide.net/enable-tabupdown-functional-key-in-new-users-terminal](http://ubuntuguide.net/enable-tabupdown-functional-key-in-new-users-terminal)

---

