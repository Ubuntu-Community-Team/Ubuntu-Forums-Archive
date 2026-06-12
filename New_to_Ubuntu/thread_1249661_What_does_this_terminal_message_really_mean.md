---
title: "What does this terminal message really mean?"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by listerdl on 2009-08-25
Hi - I was following a tutorial that said open terminal and enter:

```
$ sudo apt-get install tor privoxy
```

When I do that I get this message:

```
Command 'sudo' is available in '/usr/bin/sudo'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
bash: sudo: command not found
```

What is this telling me to do please?

Thanks

---

### Post by LowSky on 2009-08-25
your sudo profile seems to be messed up. did you activate your root account by any chance?

---

### Post by Bachstelze on 2009-08-25
Please apste the output of 

```
echo $PATH
```

---

### Post by renkinjutsu on 2009-08-25
give the output of this:

`echo $PATH`

if /usr/bin isn't in there, you should add it with
export PATH=$PATH:/usr/bin

you can also add that line to your .bashrc file so the change is permanent.

---

### Post by brunogirin on 2009-08-25
All command line shells find where executables are located through an environment variable called PATH. This variable contains a colon delimited list of directories that the shell looks into in order to find whatever executable it needs to run.

You can check the value of this variable by typing:
```
echo $PATH
```

If I do that on my machine, I get:
```
bruno@nuuk:~$ echo $PATH
/home/bruno/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:**/usr/bin**:/sbin:/bin:/usr/games:/home/bruno/devkitPro/devkitARM/bin

```

Note that it contains /usr/bin, which is what this error message is complaining about. To correct this, you can manually add /usr/bin to the path:
```
export PATH=$PATH:/usr/bin
```

You should then be able to follow the tutorial. However, this is rather odd because on a default install, /usr/bin should always be in the PATH variable.

---

### Post by Bachstelze on 2009-08-25
> **renkinjutsu said:**
> 
if /usr/bin isn't in there, you should add it with
export PATH=$PATH:/usr/bin

you can also add that line to your .bashrc file so the change is permanent.

No, no, no, *no*.

If /usr/bin is not in the PATH, it is *not* normal, and the issue should be investigated further, not solved with a dirty fix like that.

---

### Post by listerdl on 2009-08-26
Thanks - this is what happenend when I entered echo $PATH 

--
PATH:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/bin/
--

Does that look ok to you - ..what do I do next - sorry im still learning!!!

---

### Post by brunogirin on 2009-08-26
No, that's not normal. Looking at the value of the PATH variable, it looks like some script, some command you've run or something in your .bashrc file was meant to append ':/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/bin/' at the end of your path but did so incorrectly and instead clobbered the variable.

Try to start a new terminal window, type the following in it and post the output to this thread:
```
echo $PATH
```

If you still have the same result as above then type the following and post the output:
```
grep -n PATH ~/.bashrc ~/.profile ~/.bash_profile ~/.bash_login /etc/bash.bashrc /etc/profile
```

This will look for the string PATH in all profile initialisation files that bash reads at startup and will print out the lines prefixed with file name and line number. So if any of those files modifies the PATH variable in a funny way, this should find it.

---

### Post by listerdl on 2009-08-26
> **brunogirin said:**
> No, that's not normal. Looking at the value of the PATH variable, it looks like some script, some command you've run or something in your .bashrc file was meant to append ':/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/bin/' at the end of your path but did so incorrectly and instead clobbered the variable.

Try to start a new terminal window, type the following in it and post the output to this thread:
```
echo $PATH
```

If you still have the same result as above then type the following and post the output:
```
grep -n PATH ~/.bashrc ~/.profile ~/.bash_profile ~/.bash_login /etc/bash.bashrc /etc/profile
```

This will look for the string PATH in all profile initialisation files that bash reads at startup and will print out the lines prefixed with file name and line number. So if any of those files modifies the PATH variable in a funny way, this should find it.

The results was this:

-------------

Command 'grep' is available in '/bin/grep'
The command could not be located because '/bin' is not included in the PATH environment variable.
bash: grep: command not found


-------------

Any ideas on what do to next?:( thanks!!

---

### Post by unutbu on 2009-08-26
Try running
```

. /etc/environment
grep -n PATH ~/.bashrc ~/.profile ~/.bash_profile ~/.bash_login /etc/bash.bashrc /etc/profile
```

The ". /etc/environment" command should reset your PATH to 
"/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games".

---

### Post by brunogirin on 2009-08-27
Ah yes, sorry, if you don't have PATH set correctly, it won't find grep. Do what unutbu suggests and post the output here.

---

### Post by listerdl on 2009-08-27
Hi thanks guys....following from unutbu's advice to post this:

-----------------

. /etc/environment
grep -n PATH ~/.bashrc ~/.profile ~/.bash_profile ~/.bash_login /etc/bash.bashrc /etc/profile

-----------------

The output was the following.....what do I do with this - do i edit a file somewhere? THANKS GUYS

-----------------

/home/henry/.bashrc:101:export PATH=PATH:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/bin/
/home/henry/.profile:19:# set PATH so it includes user's private bin if it exists
/home/henry/.profile:21:    PATH="$HOME/bin:$PATH"
grep: /home/henry/.bash_profile: No such file or directory
grep: /home/henry/.bash_login: No such file or directory


-----------------

---

### Post by unutbu on 2009-08-27
In the terminal run:
```
/usr/bin/gedit ~/.bashrc
```
Change
```

export PATH=PATH:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/bin/

```
to
```

export PATH=[COLOR="Red"]$[/COLOR]PATH:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/bin/

```
Save and exit the text editor.
Log out, then log back in. You should then be good to go.

---

