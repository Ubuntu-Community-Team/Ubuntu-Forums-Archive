---
title: "ifconfig through SSH"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by Chrissd on 2011-07-03
Hi all,

On my server machine, if I go upstairs to the keyboard and type ifconfig, all is well, however, 9/10 of the time I use SSH for obvious reasons. If through SSH I type ifconfig I get this come up:
```

Command 'ifconfig' is available in '/sbin/ifconfig'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
ifconfig: command not found

```

If I type /sbin/ifconfig all is well. What causes this and how do I fix it?

Thanks

---

### Post by frankbooth on 2011-07-03
I'll try to explain this, so if I'm wrong, please correct me...

The bash command 'ifconfig' is searched for when you type it in the terminal. It seems your PATH isn't set as it should since it can't find the command.

Look at your users profile in /etc/profile and see what PATH is being set to.

Should look something like this:
```

PATH=/bin:/sbin:/usr/bin
export PATH

```

Folders are separated with colon: and it will search in the same order as it appears in the PATH.

---

### Post by The Cog on 2011-07-03
frankbooth is pointing in the right direction. 

The PATH variable lists the directories that should be searched for an executable when the command is entered. You can see your current path setting with this command:
> echo $PATH
Mine looks like this:
> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
I haven't been able to work out where this is set though. You could always put a line in ~/.bashrc to set it to what you want.

---

### Post by Chrissd on 2011-07-03
I'm a little confused why it works when I'm at the computer but not remotely.

---

### Post by nothingspecial on 2011-07-03
Are you logging in as the same user?

---

### Post by Chrissd on 2011-07-03
Aye. Both Chriss

---

### Post by wmatthews on 2011-08-26
I am having this exact same problem ChrissD..  Did you ever get it fixed?

---

### Post by bodhi.zazen on 2011-08-26
How did you configure your path ?

Check .bashrc , .bash_profile for a PATH variable.

here is a nice explanation :

[http://stackoverflow.com/questions/216202/why-does-an-ssh-remote-command-get-fewer-environment-variables-then-when-run-manu](http://stackoverflow.com/questions/216202/why-does-an-ssh-remote-command-get-fewer-environment-variables-then-when-run-manu)

If it is not in your .bashrc or .bash_profile, check sshd_config for 

PermitUserEnvironment no

change it to yes ;)

---

### Post by decoherence on 2011-08-26
> **Chrissd said:**
> I'm a little confused why it works when I'm at the computer but not remotely.

I am also confused by this. Please run the 'echo $PATH' command both locally and remotely and see if they are different (they shouldn't be if you're logging in as the same user.)

---

### Post by bodhi.zazen on 2011-08-26
> **decoherence said:**
> I am also confused by this. Please run the 'echo $PATH' command both locally and remotely and see if they are different (they shouldn't be if you're logging in as the same user.)

The short answer is ssh logins use .bash_profile and not .bashrc

I have this (and some other things) to .bash_profile

```
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi
```

---

### Post by Chrissd on 2011-08-29
Hi, never got it resolved, I just actually just bodged it and created an alias for it.

With regards to .bash_profile, I don't have that file in my home directory, so should I just create it with in it, or did you mean add it to .profile

```
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi
```

Thanks for the clarification.

---

### Post by bodhi.zazen on 2011-08-29
> **Chrissd said:**
> Hi, never got it resolved, I just actually just bodged it and created an alias for it.

With regards to .bash_profile, I don't have that file in my home directory, so should I just create it with in it, or did you mean add it to .profile

```
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi
```

Thanks for the clarification.

You can create a file .bash_profile ;)

---

### Post by Chrissd on 2011-08-29
Hi, 

I removed the alias, and then literally just created a file called .bash_profile with ```
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi
``` in, rebooted for good measure, ssh'd into the machine and it still creates the error.

---

### Post by HarrisonNapper on 2011-08-29
When remoting in, run

```
bash ~/.bashrc
```

then try

```
/sbin/ifconfig
```

and see if it works. If it does, .bash_profile is not running .bashrc

If it doesn't, let us know output; maybe something preventing PATH variable from being set?

---

### Post by Chrissd on 2011-09-01
It's working now! All I've done since starting this thread is add a file in my home directory called .bash_profile with ```
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi
``` in it.

I'm not sure what I did differently to when I last tested it, but it definitely works now, tried it several times after several reboots too. Must have been doing something wrong.

Thanks guys! :)

's what I love about these forums, loads of people willing to help!

---

