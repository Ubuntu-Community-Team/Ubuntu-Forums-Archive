---
title: "How do I sftp on a port other than 22?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by doctapeppa on 2009-05-10
My ubuntu server at home runs ssh on port 443 (so I can go through a very resctrictive firewall at work.)

It works great with graphical clients but now I need to connect via command line. 

```
sftp user@address -p 443
``` 

doesn't work, and neither does 

```
 sftp user@address:443
```

what's the magic command to tell it to use another port? The man page for sftp does not mention this.

---

### Post by uncannybuzzard on 2009-05-10
please read your man pages.

```
-o ssh_option
             Can be used to pass options to ssh in the format
 used in ssh_config(5).  This is useful for specifying options
 for which there is no separate sftp command-line flag.  For
 example, to specify an alternate port use: sftp -oPort=24.
 For full details of the options listed below, and their 
 possible values, see ssh_config(5).

```

---

### Post by doctapeppa on 2009-05-10
You are a god among men, with eye sight more keen than an eagle. Thank you.

---

### Post by The Cog on 2009-05-10
according to man ssh, the -p option should come before the address. Anything after the address is used as a remote command. So try this:
**sftp -p 443 user@address**

---

