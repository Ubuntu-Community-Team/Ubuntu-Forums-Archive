---
title: "Sudo broken?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Bogdanovist on 2009-03-22
Hi All, I have a strange problem with sudo. It simply won't do anything. I haven't (at least not intentionally) altered the default sudo behavior, but for some reason sudo now simply doesn't run? For instance:

sudo ls

returns

usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

Of course there is no reason to use sudo to run ls, but this demonstrates that the problem doesn't lie in the actual command (I first found this problem trying to install a new apt with apt-get, I've done this plenty of times before so something has changed, somehow). Any ideas what could be going wrong?

---

### Post by kansasnoob on 2009-03-22
Have you edited sudoers for any reason, like to launch a program at start up?

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by Bogdanovist on 2009-03-23
Ah oops, I found the error. I haven't changed the sudoers file however I forgot that I had aliased sudo to sudo -k in my .bashrc file. What I was trying to do was get sudo to never remember the authorisation, so that it would always ask for a password (as for the usual sudo behaviour I am used to from other linux distributions). I thought sudo -k {command} did this but it looks like sudo -k just kills the existing authorisation.

Can anyone tell me then how I do correctly get sudo to never remember the authorisation, and always ask for a password everytime? I guess I need to change the sudoers file in someway in order to do this, but I'm not sure what needs to be added?

---

### Post by sisco311 on 2009-03-23
Append the *Defaults* line with timestamp_timeout=0

> ...
Defaults env_editor, insults, **timestamp_timeout=0**
...

---

### Post by lisati on 2009-03-23
I think there's the germ of an idea here (not necessarily serious): a project that lets you do something like ```
sudo fix-system
```

---

### Post by drs305 on 2009-03-23
Just to expand on cisco's post:

You can edit the sudoers file to set the timeout to 0. Caution: You can mess up your system if you break sudoers.

Open sudoers for editing:
```
sudo visudo
```
Add this line:
> Defaults:*username* timestamp_timeout=0
Example: Defaults:john timestamp_timeout=0

Edit: This portion removed for clarity following HymnToLife's input that nano is now the default editor.

---

### Post by Bachstelze on 2009-03-23
> **drs305 said:**
> 
Editing visudo with the default editor is a bit different if you aren't used to it.


In Ubuntu, the default editor is [font="monospace"]nano[/font], IIRC.

---

### Post by drs305 on 2009-03-23
I must have changed my settings since mine comes up with vi. I've verified nano is the default in Intrepid. Nano is certainly better as it gives new users some help in editing, saving, etc.

You can also use the text editor of your choice to edit visudo by typing the following:
```

export EDITOR=gedit  # replace *gedit* if desired with your text app
sudo -E visudo

```

---

### Post by Bogdanovist on 2009-03-23
Thanks all, sudo is now asking for password every time. Cheers!

---

