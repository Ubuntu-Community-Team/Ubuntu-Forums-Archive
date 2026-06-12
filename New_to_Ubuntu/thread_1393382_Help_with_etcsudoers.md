---
title: "Help with /etc/sudoers"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by patchwork on 2010-01-29
I have allowed a user sudoer access to all the files in a directory in my sudoers file, however the user is still prompted for a password when a file from the directory is executed.  If I open sudoers and then close it without changing anything, reset the sudo timestamp using sudo -k, and retry the command, I am not prompted for a password.  The appropriate line from sudoers is as follows:    =(root)NOPASSWD:  After opening sudoers, the NOPASSWD option is operating as expected for the duration of the session, but resets on restart.  Anybody know what I'm doing wrong?

---

### Post by falconindy on 2010-01-29
2 mistakes:

1) File permissions aren't done through /etc/sudoers. The octal permission bits on the directories and files are what controls this.
2) You're directly editing the /etc/sudoers file directory. Bad idea. Thanks to Ubuntu's security model, you'll find yourself in a world of trouble if you make a mistake in that file. Use 'sudo visudo' to edit it.

---

### Post by patchwork on 2010-01-29
Let me clarify:  I edited sudoers using visudo, and the user has the necessary permissions to run the files.  The main hangup here is that the NOPASSWD option does not seem to take effect unless I open sudoers through visudo, even if I make no changes to the settings.  I reset the sudo timestamp afterwards, so it does not seem to be an issue of the default 15min sudo command allowance.

---

### Post by falconindy on 2010-01-29
Sure, you run a command with sudo, and for some period you're allowed to continue running commands with sudo without being prompted for a password. You obviously understand this since you've mentioned the -k flag of sudo.

You still haven't mentioned:

1) **exactly** what your sudoers file looks like
2) **exactly** what you're trying to do that prompts you for a password

The above information would go a long way.

---

### Post by patchwork on 2010-01-29
Exactly what I am trying to accomplish is to execute a script that uses the cpufreq-set command to change my frequency scaling governor option.  I have two scripts tied to keyboard commands, for quick freq scaling when I am on the go with my laptop, ondemand to help battery life, and performance for when I am on ac power.  Each of these scripts invoke sudo cpufreq-set (with associated arguments for proc core and governor setting).  The keyboard commands then execute the scripts.  Normal operation of this (before editing the sudoers file) causes a terminal window to open prompting for the sudo password.  Entering the password then changes the scaling to the desired level.  What I am trying to accomplish is a matter of convenience.  I wish to not be prompted for the password when executing these two scripts.  From my sudoers file:

```
# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=NOPASSWD: /home/kevin/Desktop/ShellScripts/*, /usr/bin/cpufreq-set
kevin crystalpepsi = (root)NOPASSWD: /home/kevin/Desktop/ShellScripts/*, /usr/bin/cpufreq-set
```This is the current state of my sudoers (when I originally posted it was slightly different.  Currently, I am prompted for a password whenever I try to scale the proc now, where this morning I was not).  This is not crippling, but it would be convenient to have.  Any help would be appreciated.


EDIT:  I seem to have gotten it the way I wanted.  My updated sudoers entry is as follows:
# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=NOPASSWD: /home/kevin/Desktop/ShellScripts/*, /usr/bin/cpufreq-set
kevin crystalpepsi = NOPASSWD: /home/kevin/Desktop/ShellScripts/*, /usr/bin/cpufreq-set

Upon restart, I was in fact able to use the keyboard shortcuts without entering my password.   Thanks.

---

