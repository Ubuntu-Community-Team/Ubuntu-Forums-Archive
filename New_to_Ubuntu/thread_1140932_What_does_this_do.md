---
title: "What does this do?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by tacomodo on 2009-04-28
MY_BASE=${MY_BASE:-/opt/mybase}; export MY_BASE

I can't really figure out what this does. I've tried to change the path there from /opt/mybase to /pot/lalala, but can't see any difference at all.

Could someone please explain the details about what this does?

---

### Post by luctor on 2009-04-28
All I know is that ALL YOUR BASE ARE BELONG TO US

---

### Post by ananth.gouri on 2009-04-28
That particular line would get the path you give and make that path in your classpath -- Something like the Java Classpath. 

It might be not working for you due to the following reasons:

1. You might have not closed your terminal. 
2. You might have added the export to your bashrc file. 

Solutions:

1. Close your terminal and relogin again. Or you can still edit the same command by giving the proper path once again. 
2. Edit your bashrc file. 

You can check if it has worked for you or not by giving the 'set' command in a konsole. 

Hope this should be your solution.

---

### Post by tacomodo on 2009-04-29
Thanks for the replies!
This is from the man for bash:
> ${parameter:-word}
Use Default Values. If parameter is unset or null, the expansion of word
is substituted. Otherwise, the value of parameter is substituted.
Could anyone be so kind as to rephrase that into understandable English?

---

