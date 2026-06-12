---
title: "code::blocks not working!"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by Sandeepkumar on 2010-01-14
I had installed the code::blocks IDE and it was working great! but now it isn't working. When i ran it from the terminal it said this: 

scarletpimpernel@PC-HOME:~$ codeblocks
Exception: An exception has been raised!

The application encountered an error at configmanager.cpp, on line 211.
The error message is:

TinyXML error: Error document empty.
In file: /home/scarletpimpernel/.codeblocks/default.conf
At row 0, column: 0.

Code::Blocks Version revision 0 (gcc 4.4.1, build: Sep 13 2009 19:31:56)
scarletpimpernel@PC-HOME:~$ 

i need immediate help pls!:(

---

### Post by KIAaze on 2010-02-03
I think you somehow messed up the codeblocks settings.
~/.codeblocks/default.conf is probably empty (you should be able to open it with a text editor to verify this).

Try renaming the problematic file:
```
mv ~/.codeblocks/default.conf{,.bak}
```

If it still doesn't work, try renaming the whole settings directory:
```
mv ~/.codeblocks{,.bak}
```
WARNING: You will loose all your codeblocks settings this way.

---

### Post by vsbp on 2012-05-13
> **Sandeepkumar said:**
> I had installed the code::blocks IDE and it was working great! but now it isn't working. When i ran it from the terminal it said this: 

scarletpimpernel@PC-HOME:~$ codeblocks
Exception: An exception has been raised!

The application encountered an error at configmanager.cpp, on line 211.
The error message is:

TinyXML error: Error document empty.
In file: /home/scarletpimpernel/.codeblocks/default.conf
At row 0, column: 0.

Code::Blocks Version revision 0 (gcc 4.4.1, build: Sep 13 2009 19:31:56)
scarletpimpernel@PC-HOME:~$ 

i need immediate help pls!:(

please reply how to solve this

---

### Post by vsbp on 2012-05-13
[QUOTE=vsbp;11933673]please reply how to solve this[/QUO
The error message is:
codeblocks
Exception: An exception has been raised!

The application encountered an error at configmanager.cpp, on line 211.
The error message is:

TinyXML error: Error document empty.
In file: /home/administrator/.codeblocks/default.conf
At row 0, column: 0.

Code::Blocks Version revision 0 (gcc 4.4.1, build: Sep 13 2009 19:31:56)
how to solve this error in codebloxcks if i open codeblocks

---

### Post by vsbp on 2012-05-14
> **vsbp said:**
> [QUOTE=vsbp;11933673]please reply how to solve this[/QUO
The error message is:
codeblocks
Exception: An exception has been raised!

The application encountered an error at configmanager.cpp, on line 211.
The error message is:

TinyXML error: Error document empty.
In file: /home/administrator/.codeblocks/default.conf
At row 0, column: 0.

Code::Blocks Version revision 0 (gcc 4.4.1, build: Sep 13 2009 19:31:56)
how to solve this error in codebloxcks if i open codeblocks
please reply as early as possible.

---

### Post by vsbp on 2012-05-14
:)> **vsbp said:**
> please reply how to solve this

---

### Post by anzaksonn on 2012-05-14
Hello!
             This thread is too old. I suggest you start a new thread to attract attention
and include the basic info about your computer as suggested in the sticky as to 
what to think about before posting. I'm a newbie myself so I can't help you with this
problem. Good luck!

---

### Post by KIAaze on 2012-05-14
I'm still subscribed to this thread, so I got notified, but if you create a new thread, let me know and I'll help if I can.
For starters, it would be useful to post the contents of "/home/administrator/.codeblocks/default.conf" (I suspect it is empty if it says "At row 0, column: 0."), as well as trying what I suggested in my last post here:
```
mv ~/.codeblocks/default.conf{,.bak}
```
```
mv ~/.codeblocks{,.bak}
```
Then try restarting codeblocks.

Another possibility is installing the latest version from the official website instead of the version in the repositories.

---

### Post by ibollodi on 2013-04-08
It works!!!
Thank you so much!!

---

