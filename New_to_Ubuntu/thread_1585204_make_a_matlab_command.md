---
title: "make a matlab command?"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by Biddlesby on 2010-09-30
Ok, so I have installed matlab, into ~/.MATLAB/ I can run matlab by typing 

```
bash ~/.MATLAB/bin/matlab
```Although I don't know why this works. What I want to do is to create a 'matlab' command that I can use. [This page]("http://www.freebsd.org/doc/handbook/linuxemu-matlab.html") says

>  
Place the following startup script in /usr/local/bin/matlab:

[LIST=1]
[*]   #!/bin/sh /compat/linux/bin/sh /compat/linux/usr/local/matlab/bin/matlab "$@"
[*] Then type the command chmod +x /usr/local/bin/matlab.
[/LIST]
But this doesn't quite work even after I changed /compat/linx/usr/local/matlab to ~/.MATLAB/. [This page]("http://en.kioskea.net/faq/2540-linux-create-your-own-command") is better but I don't know what to put in the script

```
#!/bin/bash

bash ~/.MATLAB/bin/matlab
```Didn't work. What am I doing wrong? :s

---

### Post by kleskjr on 2010-09-30
I got similar issue: I could open Matlab just when I go to the directory ../matlab/bin/.. and then type **matlab** to lunch it. I think that then you can use nautilus, just right click on the executable file and created a link, then copy the link file in /bin or /usr/bin and you can just call **matlab** in order to execute it. Hope that this answer you question!

---

### Post by Biddlesby on 2010-09-30
Works! Thank you.

---

