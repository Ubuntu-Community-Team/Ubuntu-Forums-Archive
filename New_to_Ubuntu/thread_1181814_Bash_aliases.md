---
title: "Bash aliases"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by leplen on 2009-06-08
Perhaps I'm just an idiot, but for some reason I can only get about half of my bash aliases to load.  .bashrc is sourced properly from .profile, the aliases are contained in my .bashrc file, but only about half of them are loaded.  I know that they're typed correctly because they work fine if I re-enter them each session, but bash absolutely refuses to load SOME of them.  The others work fine.  I also have a bash_alias file, which also contains all the aliases.  I've even placed some of them in .profile, all to no avail.  I'm running the most recent ubuntu release, though I can't see how that would matter.

If this has been addressed elsewhere I've been unable to locate it.

Any help would be greatly appreciated because typing out the full address for my ssh shell is getting really really old really really quickly.

---

### Post by Celauran on 2009-06-08
Are the aliases that are loading and those that aren't located in the same file? If so, can you post (some of) the ones that aren't working?

---

### Post by abhiroopb on 2009-06-08
open up a terminal and type in "alias" it should show you th list of aliases you have saved.

---

### Post by leplen on 2009-06-08
Yes they're both in the same file.

alias DFT='ssh [email]login@host.whatev[/email]er -X' 
That's the one that I care about the most.

If I copy and paste it into the command line and then type alias it will show up in my list, so it's not as if bash can't learn the command, but if I exit then it's gone and it doesn't reload with a new terminal.

---

### Post by leplen on 2009-06-08
> **abhiroopb said:**
> open up a terminal and type in "alias" it should show you th list of aliases you have saved.

Yes.  And that list and the one in my .bashrc file are not congruent.

---

### Post by abhiroopb on 2009-06-08
can you post your .bashrc and the output of "alias" please.

---

### Post by Meson on 2009-06-08
You'd be best off pasting at least one of your configuration files and pointing out which ones load and which don't. You might have something weird going on with quotes or other meta-characters

---

### Post by Celauran on 2009-06-08
That alias itself seems fine, which is confirmed by the fact that it works when entered at the command line. You mentioned having aliases entered in .bashrc, .bash_alias, and .profile; are the same aliases entered in multiple files and, if so, have you checked all three for typos? I once had a problem with conflicting aliases in .bashrc and .bash_aliases, so it may be worth a look.

---

### Post by taavikko on 2009-06-08
> **leplen said:**
> Yes they're both in the same file.

alias DFT='ssh [email]login@host.whatev[/email]er -X' 
That's the one that I care about the most.

If I copy and paste it into the command line and then type alias it will show up in my list, so it's not as if bash can't learn the command, but if I exit then it's gone and it doesn't reload with a new terminal.

I would use ssh_config for that
More info "man ssh_config"

```
taavikko@hp-dv5:~$ cat .ssh/config 
host "name_for_the_alias"
hostname "address_for_the_host"
user "account_name"

```

And the same without explanation

```
taavikko@hp-dv5:~$ cat .ssh/config 
host myserver
hostname myserver.com
port 8000
user servit

```

And using it on CLI is simply
```
ssh myserver
```


For the aliases, please uncomment the following from ".bashrc"
```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```
Then create ~/.bash_aliases and edit it to your needs
(add the aliases you want) and "source .bashrc"
and you're set.

---

### Post by leplen on 2009-06-10
I'm still not sure what was going on with my aliases, and I never did get the ssh one to work, but changing the config file worked fine.  

I retyped the .bashrc file pretty much from scratch and that seems to have fixed it so the only conclusion I can come to is it was just being stubborn about some blank spaces or something somewhere.

Anyway, thanks for the help

---

