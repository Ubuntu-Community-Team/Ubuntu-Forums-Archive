---
title: "Firefox Constantly Closes"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by Michael Kaiser on 2010-03-15
So, besides my problem with Freezing and Crashing found in [this thread]("http://ubuntuforums.org/showthread.php?t=1430602"), and inadvertently deleting my Google Chrome tab from the Applications menu - Firefox won't stay open from more than a minute before crashing and closing out. Its done it 2 times while typing this, as a matter of fact.

How can I find out why its doing that?

---

### Post by mike555 on 2010-03-15
usually it's a flash problem or an add-on ....... you might want to start Firefox in "safe mode" to see if it's an addon ..... if not uninstall all flash and try it (you can always reinstall flash from their site , just download the right one ,close Firefox then install flash )

---

### Post by LordSmight on 2010-03-15
Start firefox from terminal and post the contents here.

---

### Post by wojox on 2010-03-15
You could also open a terminal and run **firefox**

Leave the terminal open and see what errors it gives you.

---

### Post by Michael Kaiser on 2010-03-15
Unfortunately, I still haven't learned how to run things from the Terminal unless someone posts the commands.

Would someone be so kind as to tell me how, please?

---

### Post by cerealtx on 2010-03-15
> **Michael Kaiser said:**
> Unfortunately, I still haven't learned how to run things from the Terminal unless someone posts the commands.

Would someone be so kind as to tell me how, please?

open terminal type in firefox hit enter thats all there is to it, all the GUI does is link to terminal to do the exact same thing, when u click on the firefox symbol its just sending "firefox" to the terminal


^^ i like to repeat my self :/

---

### Post by Michael Kaiser on 2010-03-15
> **cerealtx said:**
> open terminal type in firefox hit enter thats all there is to it, all the GUI does is link to terminal to do the exact same thing, when u click on the firefox symbol its just sending "firefox" to the terminal


^^ i like to repeat my self :/

Well, that was rediculously simple! Haha

---

### Post by cerealtx on 2010-03-15
a common misconception is that linux is hard, but many things are acctually simpler, you just have to know where to look and what your doing which can take time, trial and error, run firefox, when it crashes post what terminal says

---

### Post by lovinglinux on 2010-03-15
See the [COLOR="Sienna"]**troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by rexxxlo on 2010-03-30
i dont mean to threa jack but in my search i found this thread

this is what i get when i run firefox and it crashes randomly

GLib-GObject-WARNING **: invalid uninstantiatable type `<unknown>' in cast to `GtkObject' Segmentation fault

its random times too sometimes its immediately when i open firefox sometimes its after a long time

---

### Post by dianemeeks on 2010-04-02
I am having the same problem.  Here is the terminal output.

(firefox:2907): GLib-WARNING **: g_set_prgname() called multiple times
The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 561563 error_code 160 request_code 149 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault

---

