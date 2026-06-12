---
title: "Please Help:  Prompt missing upon terminal launch."
date: 2009-04-09
forum: New to Ubuntu
---

### Post by TheCoe on 2009-04-09
Hello All ):P,

I am having a bit of a problem.  When I launch a terminal window, the command prompt is missing.  However, I can hit [CTRL]+C to break whatever is running in the background and return a prompt.  

The problem is persistent after multiple restarts.

Also, the problem is user-specific, as I created a "test" user to see if the problem occurred there as well.  It did not.

Please help if you can.

Thanks in advance for your assistance.

Coe

---

### Post by snova on 2009-04-09
Have you modified your ~/.bashrc file? If so, please post it.

---

### Post by TheCoe on 2009-04-09
Thank you for your reply.

I have not modified it.  I did follow an "export" command that I found online to add a folder in my home directory to the PATH variable.  I tried to add two:  ~/bin/ and ~/bin/*.  Was it wrong to add the '~/bin/*'?    

Just in case here is the .bashrc file information:

> # ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

Thanks again.

---

### Post by snova on 2009-04-09
> **TheCoe said:**
> I have not modified it.  I did follow an "export" command that I found online to add a folder in my home directory to the PATH variable.  I tried to add two:  ~/bin/ and ~/bin/*.  Was it wrong to add the '~/bin/*'?

Yes. You only need ~/bin.

From the first line of that file I would say it looks a lot like a ~/.profile file. :)

```
# ~/.profile: executed by the command interpreter for login shells.
```

If you saved it as ~/.bashrc however, this would cause a problem:

```

if [ -f "$HOME/.bashrc" ]; then
. "$HOME/.bashrc"
fi

```

Because it's sourcing itself, which sources itself, which sources itself, which sources itself... it's an endlessly recursive .bashrc file.

Remove those three lines.

---

### Post by TheCoe on 2009-04-09
snova,

Thanks for your help.  Got in a little over my head, I'm afraid :rolleyes:.  Your suggestion worked like a charm.  Have a good week(end).

Regards,

Coe

---

