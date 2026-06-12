---
title: "sudo will not give me opportunity to enter password; normally works fine"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by dissembly on 2010-08-01
Hey all,

I'm trying to install a driver, and using "sudo" to do it.

Now i know that typing "sudo" means it will ask for your password; my terminal normally prints something like:

> sudo: unable to resolve host (myname)-laptop
[sudo] password for myname:

At which point i enter my password and everything works perfectly.

However, for some reason, with my current command, it will not give me any opportunity to enter my password; it says:

> sudo: unable to resolve host (myname)-laptop

...like normal, but then it just returns me to the regular command prompt! (in case it is relevant, the command i am trying to execute is:

> sudo cp -rf firmware/RTL8192SE /lib/firmware

...from this tutorial: [http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10)

Wherever i search for this problem, it only seems to bring up questions from users who aren't aware that sudo doesn't give you asterisks or bullet points as you type in your password, so i am having trouble finding any reference to this specific problem.

Any ideas?

---

### Post by Elfy on 2010-08-01
Have a look here = [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

### Post by dissembly on 2010-08-01
Thank-you for the pointer. That looks like what my problem is.

But my /etc/hosts file does not look exactly the same:

> # Do not remove the following line, or various programs# that require network functionality will fail.127.0.0.1             localhost.localdomain     localhost...nevertheless i added a line to it based on the advice in that thread:

> # Do not remove the following line, or various programs# that require network functionality will fail.127.0.0.1             localhost.localdomain     localhost
127.0.1.1      david-laptopNow when i repeat the command i was attempting before, it does not even give me the "unable to resolve host" message - it just goes straight back to the command prompt, without doing anything (that i can see) at all!

_______________________________

Edited to add: To clarify, that quoted block is *exactly* what my hosts file looks like; i.e. everything is on a single line. When i edited it, i added a new line.

Should i change the formatting so that the text "127.0.0.1             localhost.localdomain     localhost" appears on it's own line?

________________________________

I did the above, just to see what would happen, and it has no effect. I just go straight back to the command prompt, no "unable to resolve host", no asking for my password... :(

---

### Post by da burger on 2010-08-01
Has the file been copied? (Check with ls or nautilus). Sudo will not ask you for a password if it has been authenticated in the last 15 minutes (I think that's the default time).

---

### Post by Elfy on 2010-08-01
If there is no error message then that has dealt with that. If it returns to the prompt it usually means it has done, if there is a proble you would get an error - as an example

```
cp: cannot stat `firmware/RTL8192SE': No such file or directory
```

Have you checked to see if the file copied?

```
ls /lib/firmware/RTL8192*
```

---

### Post by dissembly on 2010-08-01
Oh wow, it has! Thank-you both so much, i appreciate that. Sorry for being a bit dense!

---

### Post by Elfy on 2010-08-01
Dense? I thought you needed help :) I remember wondering how to bump a thread and asking ... 

Can you check that sudo is infact working properly now - if so can you mark thread as solved

---

### Post by dissembly on 2010-08-01
All working perfectly now, thank-you again :) :) :)

Marked as "solved".

---

