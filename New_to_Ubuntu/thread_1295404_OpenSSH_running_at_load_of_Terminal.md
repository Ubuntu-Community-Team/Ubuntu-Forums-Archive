---
title: "OpenSSH running at load of Terminal"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by Gripp on 2009-10-19
this is using CAELinux which is Ubuntu Hardy 64-bit with some extra apps included...

for whatever reason when i open a terminal it starts off saying this:

```
Adding known_hosts entries for host USER-desktop
# USER-desktop SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
Read from socket failed: Connection reset by peer
# USER-desktop SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
Read from socket failed: Connection reset by peer
Adding known_hosts entries for host localhost
# localhost SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
Read from socket failed: Connection reset by peer
# localhost SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
Read from socket failed: Connection reset by peer

```

then allows me to go on with my life...
i've never seen anything like this.
is it something that i should be concerned with (anything that wants to auto-load SSH worries me) and if so, how to fix it?

---

### Post by -Zeus- on 2009-10-19
Could you post your .profile file?

---

### Post by Gripp on 2009-10-19
```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
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
```

---

### Post by -Zeus- on 2009-10-19
OK, first one thing.  How do you start the shell?  Do you do it through the menus?

Now try this:  Open a new terminal, then after you get those messages, type 'bash' and press enter.  Then see if you still get the same messages.

---

### Post by Gripp on 2009-10-19
I use a short i created that is on the main tool bar (next the help icon, firefox, etc.) the command is simply "gnome-terminal"
and yes, typing "bash" into the started terminal results in the same message.

---

### Post by -Zeus- on 2009-10-19
Can you also paste the files ~/.bash_profile and ~/.bash_login?

---

### Post by Gripp on 2009-10-19
okay, found it

followed a code path to a file called ".bashrc-CAE" and in it was a line

```
/opt/caelinux/ssh-setup.sh
```

I just pounded it out and problem solved

thanks for your help (really, i wouldn't have even looked there..)

---

### Post by -Zeus- on 2009-10-19
Glad you figured it out.  Nice sleuthing skills! :P

---

### Post by Yannick Le Saint kyncani on 2009-10-19
Hi Gripp, could you post this file /opt/caelinux/ssh-setup.sh (just curious) ?

---

