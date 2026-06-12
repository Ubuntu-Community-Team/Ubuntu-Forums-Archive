---
title: "PATH environment variable"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by dvdhaar on 2009-12-30
Hi there,

I'm currently messing with VirtualBox WebUI using this guide here:

[http://code.google.com/p/vboxweb/wiki/install](http://code.google.com/p/vboxweb/wiki/install)

I'm pretty much done except for the 

"To execute Python scripts everywhere on your system (and you need to for getting VBox Web Console to work later) you need to add you Python installation directory to your PATH environment variable."

part.
I understand what I need to do but don't know how :) I found another topic here: [http://ubuntuforums.org/showthread.php?t=429127](http://ubuntuforums.org/showthread.php?t=429127)

But there's no /etc/envoironments" on my machine..

Help is appreciated very much

---

### Post by phidia on 2009-12-30
Python should already be in your path open  the terminal app and enter > python -V To find out what is in your path enter > $PATH Hope that helps.

---

### Post by dvdhaar on 2009-12-30
> **phidia said:**
> Python should already be in your path open  the terminal app and enter  To find out what is in your path enter  Hope that helps.

Thx for your reply.
This is what I get:

```

daniel@daniel:~$ python -V
Python 2.6.2
daniel@daniel:~$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory

```

---

### Post by JKyleOKC on 2009-12-30
That first result shows that Python is already in your path. The error message in the second result is because you were told to enter an incomplete command. It should have been "cat $PATH" rather than just "$PATH" and that would have displayed the content of your PATH variable. Without the "cat" in front of it, your command shell tried to find a program with a name equal to that content. Of course it couldn't, so it displayed the error message, with the name it was looking for in front!

In other words, you don't have to do anything more.

---

### Post by dvdhaar on 2009-12-31
> **JKyleOKC said:**
> That first result shows that Python is already in your path. The error message in the second result is because you were told to enter an incomplete command. It should have been "cat $PATH" rather than just "$PATH" and that would have displayed the content of your PATH variable. Without the "cat" in front of it, your command shell tried to find a program with a name equal to that content. Of course it couldn't, so it displayed the error message, with the name it was looking for in front!

In other words, you don't have to do anything more.


Ok thanks for your time. The problems I currently have are apparently due to some other issue with virtualbox then. Thanks!

---

