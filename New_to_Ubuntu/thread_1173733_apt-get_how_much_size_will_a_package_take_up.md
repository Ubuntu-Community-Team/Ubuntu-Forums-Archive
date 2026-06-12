---
title: "apt-get: how much size will a package take up?"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by PGScooter on 2009-05-30
For large installations, I get a message similar to the following:

```

Need to get 18.2MB of archives.
After this operation, 74.3MB of additional disk space will be used.

```

On small installations, I do not get this message before being asked if I would like to proceed.

I would like to receive this message for all installations with apt-get. I read the man page, but could not figure out how to do it. Simulation did not do it.

Thanks.

---

### Post by Didius Falco on 2009-05-30
Unutbu has just written a Python script that will do just that. Here is a link to the thread with the script and installation/use instructions:

[http://ubuntuforums.org/showthread.php?t=1154940&highlight=get_dependencies](http://ubuntuforums.org/showthread.php?t=1154940&highlight=get_dependencies)

Regards,

Didius

---

### Post by asmoore82 on 2009-05-30
`apt-get` asks for confirmation when it needs to install additional dependencies -
any other software that was not specifically requested.

to see size and other info, use `apt-cache show` - no sudo needed:
```
apt-cache show *<package_name>*
```
if you're not sure of the name, use `apt-cache search` - no sudo needed:
```
apt-cache search *<search_term>*
```

---

### Post by PGScooter on 2009-06-01
great, I will check out that script.

Thank you for the replies

---

