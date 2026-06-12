---
title: "Problem with Sage Installation"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by banerjeerupak on 2009-02-14
Sage is a mathematical tool on similar lines as Matlab. I am trying to install it. 

The readme.txt file accompanying the package asked me to install it using the terminal as follows 

[I]"If you downloaded
a binary, you do not need to do anything, just execute

 ./sage 

from the command line and you are good to go."[/I]

I followed the instruction and did the following in my terminal
[I]
"rupak@blitzkreig:~/softies/sage-3.2.2-ubuntu32bit-intel-i686-Linux$ ./sage"[/I]

The response from the terminal was :-
[I]
"----------------------------------------------------------------------
| Sage Version 3.2.2, Release Date: 2008-12-18                       |
| Type notebook() for the GUI, and license() for information.        |
----------------------------------------------------------------------
The SAGE install tree may have moved.
Regenerating Python.pyo and .pyc files that hardcode the install PATH (please wait at
most a few minutes)...
Do not interrupt this.
Setting permissions of DOT_SAGE directory so only you can read and write it.
sage: "[/I]
:confused:
what do i do now??

---

### Post by therangemaster on 2009-02-23
Once you see the sage: prompt you can go ahead and enter any of the sage commands.

If you want to use the notebook interface on your browser, for example under Firefox, type notebook() at the prompt and press enter:

sage: notebook()
**************************************************
*                                                *
* Open your web browser to [http://localhost:8001](http://localhost:8001) *
*                                                *
**************************************************

This will usually open your browser to the main notebook page. You can then click "New Worksheet" to start working with sage.

When you are done you can close the browser window, and press Ctrl-C in the terminal window to get back to the sage: prompt and then type "exit" to close sage.

---

