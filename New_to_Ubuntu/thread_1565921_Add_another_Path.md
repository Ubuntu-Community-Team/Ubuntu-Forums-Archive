---
title: "Add another Path"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by saidbakr on 2010-09-01
Hello,
From terminal, echo $PATH gives something like the following:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```
I need to add another path to this path - /home/admin/www/cakephp/cake/console - to be able running cake bake from the terminal.

I read several posts on the form, but I need to a clear method to do that permanently beside it should keep the current path too. In other word, I'd like to have the following path:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/admin/www/cakephp/cake/console

```

---

### Post by andrewthomas on 2010-09-01
add 
```
PATH="$HOME/www/cakephp/cake/console:$PATH"
```to the bottom of the user named admin's .profile

---

### Post by saidbakr on 2010-09-01
This is not permanent modification or add to the Path. It gives the same old Path when closing the current session of the terminal and starting new one. I need a permanent modification to the Path.

---

### Post by scorp123 on 2010-09-01
> **saidbakr said:**
> This is not permanent modification  Of course it is ):P

> **saidbakr said:**
>  It gives the same old Path when closing the current session of the terminal and starting new one.   Then you edited the wrong file. If you put that PATH statement into the right place such as e.g. ~/.bashrc, ~/.profile, ~/.bash_profile (depends on your config) then this will remain in there. So it is permanent.

---

### Post by AlphaLexman on 2010-09-01
And to make it system-wide, add it to /etc/profile using sudo.

EDIT: You'll have to logout and login for it to take effect.

---

### Post by saidbakr on 2010-09-01
The following is a copy of /etc/profile, so where could I add the new addition to Path?
```

# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
    . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

```

---

### Post by AlphaLexman on 2010-09-01
Either right before or right after the 'umask 022' on a separate line of course!

---

### Post by saidbakr on 2010-09-01
I added the following to the end of /etc/profile - after unmask 002 -
```

PATH = '/home/admin/www/cakephp/cake/console:/opt/lampp/bin:$PATH'

```Does it need restarting the computer to be applied?

---

### Post by AlphaLexman on 2010-09-01
No, just logout and log back in.

---

### Post by saidbakr on 2010-09-01
I performed logout and restarting, but I only get the old Path
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

without any new Path added as described before.

Is there anything wrong in the line that I had added to /etc/profile ?

---

### Post by AlphaLexman on 2010-09-01
Are you adding it as described?
```
PATH="$HOME/www/cakephp/cake/console:$PATH"
```

---

### Post by saidbakr on 2010-09-01
I added it as:
PATH = '/home/admin/www/cakephp/cake/console:/opt/lampp/bin:$PATH'Without $HOME you regarded.

---

### Post by AlphaLexman on 2010-09-01
It appears from your post you have spaces on both sides of the equal (=) sign. Make sure there are no spaces before or after the equal sign such as:
```
PATH='/home/admin/www/cakephp/cake/console:/opt/lampp/bin':$PATH
```

---

### Post by saidbakr on 2010-09-01
Thank you. It may has two wrong:
1- spaces
2- I added :$PATH inside the single quote while it should be added outside it exactly as you regarded before:

PATH='/home/admin/cakephp/cake/condole':$PATH

Thank you again, it is working fine now.

---

### Post by Paddy Landau on 2010-09-02
[LIST]
[*]To change the path for one user in a single terminal session, change[FONT=Courier New] ~/.bashrc[/FONT].
[*]To change the path for one user in the entire session, including when you don't use the terminal (e.g. Ctrl-F2), change [FONT=Courier New]~/.profile[/FONT].
[*]To change the path for everyone (including when you don't use the terminal), change [FONT=Courier New]/etc/environment[/FONT].
[/LIST]
  > **saidbakr said:**
> ```
PATH = '/home/admin/www/cakephp/cake/console:/opt/lampp/bin:$PATH'
```
You mustn't have spaces, and you need double-quote marks, as:
```
PATH="/home/admin/www/cakephp/cake/console:/opt/lampp/bin:$PATH"
```Be aware that the order is important. The way you've put it, the computer will search [FONT=Courier New]cake/console[/FONT] and [FONT=Courier New]lampp/bin[/FONT] before it searches anywhere else. If that's what you intend, then OK.

---

### Post by saidbakr on 2010-09-02
> **Paddy Landau said:**
> 
... you need double-quote marks, as:
```
PATH="/home/admin/www/cakephp/cake/console:/opt/lampp/bin:$PATH"
```Be aware that the order is important. The way you've put it, the computer will search [FONT=Courier New]cake/console[/FONT] and [FONT=Courier New]lampp/bin[/FONT] before it searches anywhere else. If that's what you intend, then OK.
I used single quote, but :$PATH is cocatenated to the new value as follows:
```

#/etc/profile
PATH='/home/admin/www/cakephp/cake/console:/opt/lampp/bin':$PATH

```
:KSHowever, there is new information, could I understand that /etc/profile will affect only running in terminal, while /etc/environment will affect both terminal and any application need path?

---

### Post by AlphaLexman on 2010-09-02
I am glad you marked the thread as solved (and I believe it is), there are some technical items I want to point out.
> could I understand that /etc/profile will affect only running in  terminal, while /etc/environment will affect both terminal and any  application need path?/etc/profile is 'invoked' at login, before any interactive shells (those with a prompt) are executed.

I wouldn't change /etc/environment (just a gut feeling).
> Be aware that the order is important. The way you've put it, the computer will search [FONT=Courier New]cake/console[/FONT] and [FONT=Courier New]lampp/bin[/FONT] before it searches anywhere else.Paddy Landau makes an excellent point here, for ANY 'program' that is ran, the system will look in your /home/admin/www/... dierctory FIRST. And simple things like 'ls' (yes, ls is a program and not a built-in) will take just a little bit longer, not much, but in principle it matters. So a better option is:
```
PATH="$PATH":'/home/admin/www/cakephp/cake/console:/opt/lampp/bin'
```Note the double quotes around the variable $PATH, even though you know it doesn't have any 'spaces' in the value, imo it is still good practice to double quote your variables.

---

### Post by chaanakya_chiraag on 2010-09-02
I thought you have to use the export command e.g.
```
export PATH=$PATH:/home/admin/www/cakephp/cake/console:/opt/lampp/bin
```
Is that just a safety measure?

---

### Post by AlphaLexman on 2010-09-02
> **chaanakya_chiraag said:**
> Is that just a safety measure?
Short answer: yes.

Long answer:
>                                   **COMMAND EXECUTION**

 After a command has been split into words, if it results in a simple command and an optional list of arguments, the following actions are taken. If the command name contains no slashes, the shell attempts to locate it. If there exists a shell function by that name, that function is invoked as described above in [SIZE=2]**FUNCTIONS**[/SIZE][SIZE=2]. [/SIZE]If the name does not match a function, the shell searches for it in the list of shell builtins. If a match is found, that builtin is invoked. If the name is neither a shell function nor a builtin, and contains no slashes, **bash** searches each element of the [SIZE=2]**PATH **[/SIZE]for a directory containing an executable file by that name. **Bash** uses a hash table to remember the full pathnames of executable files (see **hash** under [SIZE=2]**SHELL BUILTIN COMMANDS **[/SIZE]below). A full search of the directories in [SIZE=2]**PATH **[/SIZE]is performed only if the command is not found in the hash table. If the search is unsuccessful, the shell searches for a defined shell function named **command_not_found_handle**. If that function exists, it is invoked with the original command and the original command's arguments as its arguments, and the function's exit status becomes the exit status of the shell. If that function is not defined, the shell prints an error message and returns an exit status of 127.  
 from man:bash

It seems $PATH gets special treatment and doesn't have to be exported.

---

### Post by saidbakr on 2010-09-02
**To complete the benefits of this post**, if you know a GUI application or Gnome Applet that able to make this in one single step, I think that it will be nice to inform us about it.

---

### Post by chaanakya_chiraag on 2010-09-07
> **AlphaLexman said:**
> Short answer: yes.

Long answer:
from man:bash

It seems $PATH gets special treatment and doesn't have to be exported.
Thank you very much for that! :)

---

### Post by chaanakya_chiraag on 2010-09-07
> **saidbakr said:**
> **To complete the benefits of this post**, if you know a GUI application or Gnome Applet that able to make this in one single step, I think that it will be nice to inform us about it.
I could try writing a gui script...if I do, I'll post a link on this thread...

---

### Post by saidbakr on 2010-09-07
> **chaanakya_chiraag said:**
> I could try writing a gui script...if I do, I'll post a link on this thread...
Thank you our dear friend and I hope that you will able to do it. I'm waiting your link :D

---

### Post by chaanakya_chiraag on 2010-09-07
My script will add the new addition to the path to .bashrc and can be found here:
[http://dl.dropbox.com/u/1238977/add_path.sh](http://dl.dropbox.com/u/1238977/add_path.sh)
To use it, simply create a launcher to it and double-click on the launcher.  An alternative would be to just double-click on the script itself and choose run.

---

### Post by saidbakr on 2010-09-07
Very nice and handy, however, I should mention to set permission to execute for owner by right click on the file, then, properties, then permissions.

---

### Post by chaanakya_chiraag on 2010-09-08
Oh right...the other option for those terminal-savvy people is a version of
```
chmod +x /path/to/add_path.sh
```
Both methods will work.

---

### Post by jackachan on 2011-05-11
Remember to source the file after modification.
i.e.

source .profile

After that, the modification (newly added paths) will be applied.

---

