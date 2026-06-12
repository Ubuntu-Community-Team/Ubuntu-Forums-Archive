---
title: "A second bash to auto-run as non-root user"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-06
Hi,
These days I have to install a higher version of bash under my $HOME on my office server. I hope to make the new bash automatically run both when I ssh to my server and when I boot into my office computer which loads my $HOME on the server. So I added into ~/.bash_profile that:
```

SHELL='${HOME}/bin/my_new_bash/bin/bash'                                                                                                      
exec $SHELL

```

The new bash starts automatically if I ssh to the server, however, if I try to login into my office computer, I will not be able to with the following error:
> Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem.
I can login successfully if the line "exec $SHELL" in .bash_profile is commented. 

I was wondering if there is some way to make the new bash start automatically without the login error when login into my office computer?
Thanks!

---

### Post by blueridgedog on 2009-03-06
Have you tried specifying your shell in /etc/passwd?

```
joeuser:x:1000:1000:Joe User,,,:/home/joeuser:/bin/bash
```

---

### Post by flylehe on 2009-03-06
I don't think I could, because I am not the root to the server. Is that right?

---

### Post by blueridgedog on 2009-03-06
You have a system admin at your work place that asks you to run a different shell, but won't help you edit your shell setting in /etc/passwd?

---

### Post by flylehe on 2009-03-06
Not that he asks me to use a new shell, but my work requires me to. Asking him to change for me might probably get rejected. 
I was just wondering why change to a new shell in .bash_profile would cause the login error to my office computer?

---

### Post by blueridgedog on 2009-03-06
Sorry, I misunderstood.  I though you were being required to run a newer version of bash as a rule, not as a requirement.  Hmm....let me give it some thought.

---

