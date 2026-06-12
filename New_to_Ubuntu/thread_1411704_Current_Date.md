---
title: "Current Date"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by iggy pop on 2010-02-20
I am trying to learn a little about Ubuntu's CLI and notice that when i open a terminal a prompt appears: iggy@iggy-desktop:~$ is there anyway that i could include the current date into the prompt?

---

### Post by bluelamp999 on 2010-02-20
Not really a CLI expert but a quick Google turned this up - [http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

So if you type in a terminal ```
PS1="\d: \u@\h:\w $ "
```

This gives you a prompt like ```
Sat Feb 20: mike@LATITUDE:~ $ 
```

To make it permanent you have to mess around with .profile files, but I haven't fully explored this yet.:D

---

### Post by prismpirate on 2010-02-20
Hi iggy,

First, press alt - f2 and enter:

```
gedit .bashrc
```

Now, a text browser will open. Try to find this in the document:

> # If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)

Notice underneath this block of text is a line with some text

```
PS1="some random text"
```

Change everything within that bracket into:

```
$ PS1="[\d \t \u@\h:\w ] $ "
```

Save and close the text editor. Now, go to:
```
Applications > Accessories > Terminal
```

Launch the terminal. A command prompt will pop out. It should read something like: 

```
Day Date Hour:Min:Sec hostname@computer
```

You can change the output by adding / removing more stuff. Follow this link to what kind of stuff you can add. You can even change the color of the prompt.:

```
http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html
```

---

### Post by iggy pop on 2010-02-20
Would just like to say a great big thanks to you both for trying to help an old noob.

---

