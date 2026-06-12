---
title: "Ubuntu 10.04 LTS Ignores Login Password"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by ViperSpec on 2011-02-28
I am running 10.04 LTS on an HP laptop. It was working with no issues last night. When I attempted to login today, after I enter my password, I get a black screen for 1-2 seconds, then the login screen reappears. It does not say anything about an "authentication failure", as it does when I enter a known bad password. I have rebooted several (15-20) times, with no change. I am able to boot into recovery mode, and when it asks for username and password, it allows me to the command line.  However, once at the command line, I have limited function.  For example, I am able to change directories using cd, but am unable to view the contents of those directories using ls. I receive the following error message:

Command 'ls' is available in '/bin/ls'
The command could not be located because '/bin' is not located in the PATH environment variable
ls: command not found

Am I screwed?

---

### Post by turtle153 on 2011-02-28
Not quite. Press Ctrl-Alt-F1 (note: press Ctrl-Alt-F7 to switch back) and login to the big terminal with your username and pass. Once you've done that, type
```

sudo stop gdm

```
and enter your password again.
You'll then need to restart x under root privileges so type
```

sudo startx

```

You'll then have to press Ctrl-Alt-F7 to switch into the GUI mode. Using this you can go to System > Administration > Users and Groups to create a new user I would assume.

---

### Post by ViperSpec on 2011-02-28
Thanks for the reply, but no luck.  I get a similar "command not found" error, except regarding the sudo command instead of the ls command.
I did find that I can get to the root shell by booting into the recovery mode, and everything seems to work from there.  But I have virtually no experience with the command line, so I don't even know where to start to try to fix this.

---

### Post by ViperSpec on 2011-03-01
OK, problem solved.  It turned out that I had managed (don't know how) to change the $PATH variable for my profile.  I was able to create an new user from the root shell in recovery mode, give that new user sudo rights, and access nautilus from the new profile.  Once in nautilus, I found the modified file (.profile in my home folder).  On the advice of a buddy, I changed the last lines of that file to read

if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

And now I'm able to login to the original profile, and everything is still there.  Hope this helps some one else if they run into a similar issue.

---

### Post by turtle153 on 2011-03-01
Good on you for fixing it! I should have guessed there was a path problem when you can't run commands :p

---

### Post by 3177 on 2011-03-01
just goes to show that beans are just for fun:KS

---

