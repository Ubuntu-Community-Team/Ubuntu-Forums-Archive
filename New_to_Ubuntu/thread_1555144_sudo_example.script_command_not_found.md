---
title: "sudo: example.script: command not found"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by TheCraneMan on 2010-08-17
I'm having a problem with the Terminal, I have a script called sys_info.script that I'm trying to run in the Terminal. I set the permissions, 755, and edited the path by adding

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

to the .profile file. Everything works fine but I need to run sys_info.script in Root user-mode so I use the command sudo sys_info.script and it gives me the error: sudo: sys_info.script: command not found
I even ran it in Root terminal, i.e. logged in as Root. Same error.

Someone please help, thanks in advance!

---

### Post by earthpigg on 2010-08-17
> **TheCraneMan said:**
> I need to run sys_info.script in Root user-mode so I use the command sudo sys_info.script and it gives me the error: sudo: sys_info.script: command not found
I even ran it in Root terminal, i.e. logged in as Root. Same error.


hi,

if you are already in the directory where the script is located:

```
sudo ./sys_info.script
```

if not:

```
sudo /path/to/sys_info.script
```

if you want root's profile to be the same as your user profile, you would need to edit /root/.profile similarly.

---

### Post by wojox on 2010-08-17
What does this return:

```
echo $PATH
```

---

### Post by TheCraneMan on 2010-08-17
Ah that's better. Your right the path for root wasn't set to my other home directory. I fixed up the root profile to point to the right point, appreciate it, kinda a dumb mistake. Another question though, in my sys_info.script I have this set up to check if the user is Root, but it always says "You are not Root" even when I use the sudo command or log in with Root terminal (now that they work :p )

if [ "$user_id" != "0" ]; then
    echo "You are not Root." >&2
    echo "Program finished with result code -1"
fi

Help please, thank you!

---

### Post by earthpigg on 2010-08-17
well, ubuntu doesn't use a 'traditional' root account.

even when you 'sudo su', typing users still doesn't show root as being logged in:

```
[chris: ~]$ users
chris chris
[chris: ~]$ sudo su
root@chris-desktop:/home/chris# users
chris chris
```

root still isn't listed, even though i am clearly looking at a root terminal.

maybe you could do something with 'touch', though, to see if you currently have root permissions?

using /root/.profile in this example just because it's on the top of my head as something you cannot touch as a user, but can with root permissions.

```

[chris: ~]$ touch /root/.profile
touch: cannot touch `/root/.profile': Permission denied
[chris: ~]$ sudo su
root@chris-desktop:/home/chris# touch /root/.profile
root@chris-desktop:/home/chris# 
```

if the script can touch /root/.profile, then it has root permissions. if not, it then it doesn't.

my kung fu is weak when it comes to scripting, so i can't demonstrate exactly what the script needs to say. but, something like that ought to do it: tell the script to do something trivial and harmless that only root can do. if it can, cool. if not, display an error message.

---

### Post by TheCraneMan on 2010-08-17
Hmm well thank you, I appreciate all the answers I'm kinda just goin through a tutorial on scripting and the Shell so when I reach that point in time I'll apply your advice and I understand what you mean so thank you very much and I think I understand but the $PATH for Root still won't work but it's alright because the ./ method still works fine. Bye!

---

