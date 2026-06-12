---
title: "Launching Programs from Shell"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by dormouse on 2009-01-24
Hi -

I know how to launch a program like Rhythmbox from the shell.  
    rhythmbox

And I know how to use the & character to run in the background
    rhythmbox &

For both of these methods the shell remains open, and closing the shell also closes Rhythmbox.  

Is there a way to launch a program from the shell, and be able to close the shell without closing the program.  [Yes, I could just launch from desktop, but I am trying to understand the terminal and shell better.]

Thanks,

- dormouse

---

### Post by stoogiebuncho on 2009-01-24
This may not answer your question, but you can always press Alt+F2 and run it from the "Run Application" dialog.  You use the same commands as you would in the terminal (except you don't need the &).

---

### Post by kaibob on 2009-01-24
I haven't used it, but another thread recommended nohup is a somewhat similar situation:

[http://ubuntuforums.org/showthread.php?t=1047494](http://ubuntuforums.org/showthread.php?t=1047494)

---

### Post by dormouse on 2009-01-24
Thanks for both the suggestions!

   nohup rhythmbox

will start the program and then I can close the terminal window.  (It does leave behind a file nohup.out for any messages.)

Alt-F2 is another way to start from the GUI that I didn't know about.

I learned two new things - thanks!

- dormouse

---

