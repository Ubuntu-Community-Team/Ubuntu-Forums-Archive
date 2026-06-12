---
title: "How to undo a command in terminal"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by anrom on 2010-10-06
I entered this command in terminal:

nautilus -q

I want to undo that command.  How do I do that?

I'm working on getting banshee to recognize my ipod, so I was trying out suggestions. The first part reads like this:
--------------

The easiest workaround I had found for this was to simply issue - nautilus -q on the command line...

Plug your iPod in, nautilus window opens... eject your iPod, open a terminal or Alt+F2 and type nautilus -q
--------------

Which is why I issued the command, but don't know how to reverse it.

---

### Post by throntax on 2010-10-06
if you type 'man nautilus' it gives you the manual page for this command. the command you typed, 'nautilus -q' is used to quit nautilus, so presumably, running the command 'nautilus' by itself would restart it, which may be what you mean by reversing the command...

---

### Post by NightwishFan on 2010-10-06
There is no way I know to reverse a command. I would do as the above posted advised and research a command before you run it.

---

### Post by anrom on 2010-10-06
Thanks, throntax. That worked.  Simple if I had known that I quit terminal. NightwishFan is right, it's always a good idea to research first and i do as much as I can. Curiously, I googled that command and came up with nothing. Being a total non-tech when it comes to terminal commands, I had no idea where to look, except here finally. 

Though everything is back to where it was before I issued the first command, I did get this and have no idea what it means:
-----------

Initializing nautilus-share extension
seahorse nautilus module initialized
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:10784): WARNING **: Unable to add monitor: Not supported
------------
I hope all is as well as it seems.  Thanks again.

---

### Post by throntax on 2010-10-06
incidentally have you got it working?

[http://old.nabble.com/ipod-recognition-td26661726.html]("http://old.nabble.com/ipod-recognition-td26661726.html")

---

### Post by mastablasta on 2010-10-06
> **anrom said:**
>  Curiously, I googled that command and came up with nothing. 
 
next time it's better to just type "man" in front of command and you will get the info you were looking for on google now.
 
"man" is sort of like /? or /h swtich in MS based systems.

---

### Post by anrom on 2010-10-06
> incidentally have you got it working?

[http://old.nabble.com/ipod-recognition-td26661726.html](http://old.nabble.com/ipod-recognition-td26661726.html)

throntax, Yes, I got podsleuth from synaptic package manager. Banshee now "sees" my ipod and all is well.

mastablast - I'll look into that.  Really appreciated your help.

---

### Post by themusicalduck on 2010-10-06
> **anrom said:**
> Curiously, I googled that command and came up with nothing. Being a total non-tech when it comes to terminal commands, I had no idea where to look, except here finally. 

Google wouldn't have come up with anything because using a - I think takes the term out of the search results. So it would have searched for nautilus excluding "q".

You need to use "nautilus -q" with the quote marks in Google then it comes up with more relevant stuff.

---

### Post by fatality_uk on 2010-10-06
For those that want a web version of bash man, look here:
[http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

---

### Post by Rubi1200 on 2010-10-06
Or here:
[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)

---

