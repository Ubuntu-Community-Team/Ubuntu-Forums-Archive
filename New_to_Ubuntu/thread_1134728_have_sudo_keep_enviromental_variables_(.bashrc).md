---
title: "have sudo keep enviromental variables (.bashrc)"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by pspsampsp on 2009-04-23
my question is in the title , i think i know how but i just want to check: 

if this is my sudo file below 

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password


```
would i remove: Defaults        env_reset  ?

---

### Post by Hospadar on 2009-04-23
Well, just for peace of mind, I would comment it out with a #
But yeah, I think you can remove it and sudo should work fine, if not, livecd and change it back.

That said, there might I suppose be some security concern if a program run as sudo sets an environment variable thinking that it is private since it's running as root, and then that value getting out into non-root land (or the other way around)

If you just have a couple specific environment variables you need to have set (or aliases, or whatever), you can put those into /root/.bashrc and that should work fine.

---

### Post by pspsampsp on 2009-04-23
ive put them in /root/.bashrc but they only work when using su not sudo any one else got ideas?

---

### Post by duanedesign on 2009-04-23
One of sudo&#8217;s security features makes sure your parent environment is cleaned before dropping down to root. Generally you want this! But if you do not.

You can instruct sudo to keep specific environmental variables (in /etc/sudoers):

Defaults env_keep=&#8221;variables&#8221;

Defaults env_reset

---

### Post by pspsampsp on 2009-04-23
quick question just to be sure , would i add multiple variables like : 
Defaults env_keep=&#8221;variable1&#8221;
Defaults env_keep=&#8221;variable2&#8221;
Defaults env_reset

if not how?

---

### Post by duanedesign on 2009-04-23
If I were passing Var_1 and Var_2

```
Defaults env_keep=”Var_1 Var_2”
Defaults env_reset
```


Good Luck

---

### Post by pspsampsp on 2009-04-23
ok thanks

---

### Post by ULeeC on 2011-09-14
> **duanedesign said:**
> One of sudo’s security features makes sure your parent environment is cleaned before dropping down to root. Generally you want this! But if you do not.

You can instruct sudo to keep specific environmental variables (in /etc/sudoers):

Defaults env_keep=”variables”

Defaults env_reset

Thanks a lot. that's what i'm looking for :)

---

### Post by oldos2er on 2011-09-14
Back to sleep, poor tired thread. Closed.

---

