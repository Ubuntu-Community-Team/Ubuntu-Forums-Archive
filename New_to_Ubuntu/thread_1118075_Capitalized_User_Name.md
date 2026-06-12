---
title: "Capitalized User Name"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by BslBryan on 2009-04-06
Hello, everyone.

I'm not much of a beginner anymore, but it seems that this was the only place this belongs.  It's beginning to be a cosmetic annoyance that every time I open up a terminal, my name is not capitalized, and the same goes for my GDM login.  I know this can be changed somehow, because this is a feature, and other Linux distros like Fedora don't mind one bit.  Please advise.

Thanks!  :p

---

### Post by metallicamike on 2009-04-06
In ubuntu, open System->Administration->Users and groups. Select your names and press properties. Then you can change your login name and password from there. :) Make sure you hit unlock and enter your pass first

---

### Post by BslBryan on 2009-04-06
Thanks for such a speedy reply.  Unfortunately, this doesn't help me change my User name.  This makes me think that I'll have to do something without a GUI.

I also tried to create a new user name with a capital letter, but it gave me an error.  I've attached two screenshots.

---

### Post by metallicamike on 2009-04-06
According to the error it sounds like you cant have a capitalized username. I wouldnt know because mine is also lowercase

EDIT: I just confirmed that you can't have a capitalized username.

---

### Post by BslBryan on 2009-04-06
Look here:

[https://bugs.launchpad.net/ubuntu/+source/adduser/+bug/127967](https://bugs.launchpad.net/ubuntu/+source/adduser/+bug/127967)

His or her bug report gives really vague instructions, so I know it can be done.

---

### Post by metallicamike on 2009-04-06
those instuctions are a little too vague. i tried
```
sed /etc/{passwd,passwd-,shadow,shadow-,group,group-}
``` but i dont think it worked.

---

### Post by LowSky on 2009-04-06
you should have read the thread on launchpad more carefully, then next post give you more information
> ...This is not a bug, this is a feature. Some systems like mail delivery systems won't deliver to such users because they lowercase the name before lookup.

The username must match the regular expression configured via the NAME_REGEX[_SYSTEM] configuration variable. The default is NAME_REGEX="^[a-z][-a-z0-9]*\$". You can use the `--force-badname' option to relax this check or reconfigure NAME_REGEX or NAME_REGEX_SYSTEM. You can change it in /etc/adduser.conf


here is more infor on /etc/adduser.conf
[http://www.annodex.net/cgi-bin/man/man2html?adduser.conf+5](http://www.annodex.net/cgi-bin/man/man2html?adduser.conf+5)

---

### Post by BslBryan on 2009-04-06
Can someone give me their adduser.conf?  

At least copy and paste the lines after 
```
# If ADD_EXTRA_GROUPS is set to something non-zero, the EXTRA_GROUPS
# option above will be default behavior for adding new, non-system users
#ADD_EXTRA_GROUPS=1

```

I deleted it out of stupidity.  Sorry for the inconvenience.  I'll try --force-badname. 

Thanks. :p

---

### Post by BslBryan on 2009-04-06
bump.

Sorry, but it's more than just capitalization now, I'm missing a piece of code. ;)

---

### Post by kanikilu on 2009-04-06
My unmodified adduser.conf (in .txt) is attached.

---

### Post by hessczoo on 2009-04-06
Capitalized usernames are very not linux friendly, I would suggest using lowercase and just not trying to modify them.

---

### Post by BslBryan on 2009-04-06
GNU and the Linux Kernel are both *very* case-sensitive.  However, in regards to user name, I've found that it is different.  I suppose Ubuntu developers just wanted to make certain that everything would work as smoothly as possible, but as pointed out in the website, it can be changed.  Thanks, also for the adduser file. It helped a lot. :D

---

